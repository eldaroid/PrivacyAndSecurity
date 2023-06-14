# Privacy

### Как изучать?

1. - [x] [Лекция 05. Security and Privacy](https://www.youtube.com/watch?v=PlL44J5OOWQ&ab_channel=%D0%A4%D0%9A%D0%9D%D0%92%D0%A8%D0%AD%E2%80%94%D0%B4%D0%B8%D1%81%D1%82%D0%B0%D0%BD%D1%86%D0%B8%D0%BE%D0%BD%D0%BD%D1%8B%D0%B5%D0%B7%D0%B0%D0%BD%D1%8F%D1%82%D0%B8%D1%8F)
2. - [x] [Какой пароль защитит от взлома](http://samag.ru/uart/more/53)
3. - [x] [The New Oil](https://thenewoil.xyz/)
4. - [x] [КАК ЗА НАМИ СЛЕДЯТ? — ТОПЛЕС](https://www.youtube.com/watch?v=qBDbO_bAdFM&ab_channel=%D0%A2%D0%9E%D0%9F%D0%9B%D0%95%D0%A1)
5. - [x] [КАК ВЗЛОМАТЬ СИСТЕМУ? — ТОПЛЕС](https://www.youtube.com/watch?v=l9d1HXE7SH0&t=609s&ab_channel=%D0%A2%D0%9E%D0%9F%D0%9B%D0%95%D0%A1)
6. - [x] [КИБЕРОГРАБЛЕНИЕ ВЕКА — ТОПЛЕС](https://www.youtube.com/watch?v=uYpBIrhW114&ab_channel=%D0%A2%D0%9E%D0%9F%D0%9B%D0%95%D0%A1)
7. - [x] [НА ЧТО СПОСОБНО КИБЕРОРУЖИЕ? — ТОПЛЕС](https://www.youtube.com/watch?v=pBSGl2uq3_4&ab_channel=%D0%A2%D0%9E%D0%9F%D0%9B%D0%95%D0%A1)

## Security and Privacy

**Privacy** - насколько вы можете контролировать какими данными вы делитесь (защиты личности пользователя). В целом есть ощущение, что мир всё менее приватен, так как даже по Вашим запросам в Google можно достаточно точно описать, кто Вы как личность.

**Security** - насколько вы можете не бояться за сохранность ваших данных (защита данных). А вот безопасность растёт и возможна. Хранить секреты текущие технологии умеют достаточно хорошо.

## Пароли

Если рассматривать односторонние пароли, то самое важное понятие, которым надо руководствоваться — сколько злоумышленнику потребуется времени, чтобы его перебрать. Математическое понятие — энтропия. Фактически, логарифм количества вариантов. На этот счёт есть хороший комикс (энтропия в нем приведена для примера):

![](https://camo.githubusercontent.com/a426969729d7cb92c2fd86080bb567fed31f61908bf323873d7ce50af30ba1db/68747470733a2f2f696d67732e786b63642e636f6d2f636f6d6963732f70617373776f72645f737472656e6774682e706e67)

### Энтропия

Энтропия пароля - сложность пароля, измеряемая в битах. С точки зрения взлома методом полного перебора (brute-force attack) устойчивость пароля к хакерским атакам сильно зависит как от его длины, так и от используемого набора знаков. 

### Подсчет энтропии

`H(пароль) = L*(lnN/ln2)`

где:

* L – длина символов в пароле - [можно посмотреть длину (Length) здесь](http://rumkin.com/tools/password/passchk.php);
* N – количество используемых символов - [можно посмотреть количество вариаций символов (Charset Size)](http://rumkin.com/tools/password/passchk.php);
* ln – натуральный логарифм, т.е. логарифм по основанию е = 2,71828

В частности, энтропия самого легкого для взлома пароля 123456 находится следующим образом:

`H(123456) = 6*(ln10/ln2) = 19,9` Таким образом, хакеру нужно 2^19,9 = 524288 вариантов перебрать все пароли с заданными параметрами ~ 0.05 секунды, - пароль слишком легкий.

**!!! Стремитесь как минимум к 70 битам !!!**

Подсчет [энтропии онлайн](https://www.antivirus.promo/password-strength-checker).

Почти любой может перебрать пароли с энтропией 25-30. Это всего какие-то жалкие миллиарды операций. Уже намного сложнее с энтропией 50-60, для этого потребуется много мощностей. Представим, что злоумышленник может перебирать 100 миллиардов в секунду — это где-то 30-50 мощных комп станций или 10-20 приличных серверов. Пароли из больших и маленьких букв + цифр, алфавит 62 символа:
  
  * 6 символов - энтропия 35, 0.5 секунд
  * 8 символов - энтропия 47, 37 минут;
  * 9 символов - энтропия 53, 1.5 дня;
  * 10 символов - энтропия 59, 3.25 месяцев;
  * 11 символов - энтропия 65, 17 лет;
  * 12 символов - энтропия 71, 10.5 столетий;

Дальше экспоненциально, понятное дело. Де факто даже энтропию 40-50 уже сложно перебирать, особенно в онлайне, но оно находится на грани текущих возможностей, желаний и эффективности. Если не рассматривать квантовые компьютеры (с их суперпозицией), перебор пароля с энтропией 60-70 занимает огромное количество ресурсов и практически невозможен, если не задействует десятки миллионы долларов вычислений.

## Анонимность

Есть VPN, Tor, первый пытается использовать proxy, чтобы Ваш IP адрес невозможно было отследить, но Вы должны сильно доверять VPN провайдеру. Tor создаёт отдельную сеть, где через каждого участника можно "прыгать" и тем самым путать свои пути к точке выхода. Оба увеличивают Вашу анонимность, но даже они уязвимы к атакам sniff: когда отслеживают выход и вход и пытаются провести корреляцию. Такие атаки вполне успешны и с ними фундаментально ничего не поделать.

## Двух-факторная аутентификация

Основная суть двухфакторной аутентификации — спросить другой ресурс, а точно ли это Вы. Самый простой пример: "Вы говорите маме, что гуляете с друзьями, она просит дать телефон другу, чтобы подтвердить, что это так".

Используйте 2Auth только с Auth apps, которые перегенерируют коды раз в несколько секунд и достаточно сложны для взламывания. SMS и телефоны менее безопасны и вполне могут подделываться.

[YubiKey](https://ru.wikipedia.org/wiki/YubiKey) предотвращает вход на определенные сети (по факту, любые действия, даже заход по ssh или чтение файла можно настроить) без подтверждения, что Вы дотронулись до нужного ключа. Протокол открыт и всем понятен, подделать реальное нажатие на ключ крайне сложно. Например, количество фишинговых атак на Google после перевода всех сотрудников на YubiKey снизилось до нуля.

## Для предотвращения взлома: 

* Для хранения паролей можно использовать password manager: [KeePassXC](https://keepassxc.org/download/), LastPass, 1Password. Можно к ним подсоединяться и с телефона, для этого всего лишь базу данных сохранить в облаке и скачать в телефон -> импортировать в приложение.

  Я использую **KeePassXC**: 

  1.  Переходим по [ссылке](https://keepassxc.org/download/)
  2.  Скачиваем на мак с помощью `brew install --cask keepassxc` и устанавливаем без каких-либо изменений
  3.  Создаем базу данных и вписываем пароли
  4.  Сохраняем полученную базу данных -> сохранить как `*.kdbx`
  5.  Отправляем себе на почту или в облако
  6.  Скачиваем на любом другом устройстве (в том числе на телефоне) и импортируем нашу базу данных
  7.  ✅ Пользуемся 

### Чему надо придерживаться?

  * Лучший бесплатный **VPN** - nordVPN.
  * !!! Старайтесь не подключаться к публичным точкам WiFi, они сделаны так, что запоминание идёт по именам точек и их легко подделать. Приватные WiFi точки достаточно безопасны.
  * [KeePass](https://keepassxc.org/) для хранения паролей
  * [UBlock Origin](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=en) (антифишинг) - расширение для Chrome для блокирования рекламы и блокирования входа на сайты c плохой репутацией.
  * [Yubikey](https://www.yubico.com/) для предотвращения фишинговых атак на себя
  * Протокол для wi-fi, который безопасный - VPA2
  * Двух-факторная аутентификация только вместе с Authentificator App, никаких SMS

Если Вы хотите ультимативный гайд, то можете прочитать [эту заметку](https://techsolidarity.org/resources/basic_security.htm) для журналистов в США, которые ездят в ближний восток для репортажей. Если кратко: `всё выше перечисленное + Chromebook + Signal/WhatsApp, Windows Defender и никаких антивирусов + только IPhone и закленные веб камеры.`


## Популярные личности и безопасность

**Эдвард Сноуден** - в начале июня 2013 года Сноуден передал газетам The Guardian и The Washington Post секретную информацию [АНБ](https://ru.wikipedia.org/wiki/%D0%90%D0%B3%D0%B5%D0%BD%D1%82%D1%81%D1%82%D0%B2%D0%BE_%D0%BD%D0%B0%D1%86%D0%B8%D0%BE%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9_%D0%B1%D0%B5%D0%B7%D0%BE%D0%BF%D0%B0%D1%81%D0%BD%D0%BE%D1%81%D1%82%D0%B8), касающуюся тотальной слежки американскими спецслужбами за информационными коммуникациями между гражданами многих государств по всему миру. Раскрыл факт всеобъемлющего слежения в 60 странах за более чем миллиардом человек правительствами 35 стран

```
Я готов пожертвовать всем этим, потому что не могу со спокойной совестью
позволить правительству США нарушать приватность, свободу Интернета и основные свободы людей во всём мире
с помощью этой громадной системы слежки, которую они втайне разрабатывают.

У любых стен в США есть уши.
```
Объявлен американскими властями в международный розыск и в США ему грозит до 30 лет тюрьмы. Сноуден направил запросы на предоставление убежище во многие страны, но положительно ответила только страна Эквадор. При транзите через Москву, Эдварда не пропустили, потому что его паспорт аннулирован. По словам В. Путина в июле 2013, американцы знали, что делали, когда аннулировали удостоверение личности Сноудена: «Как только он, находясь в воздухе, заявил о том, что летит транзитом, это стало всем известно, и американская сторона, по сути, заблокировала его дальнейший перелёт». Сейчас имеет бессрочный вид на жительство в РФ.

**Кевин Митник** - "самое слабое звено в системе безопасности не технологии, а человек". Его книга "Искусство обмана" - в ней он подробно описал насколько уязвимы системы безопасности крупнейших компаний, несмотря на их степень защиты.
