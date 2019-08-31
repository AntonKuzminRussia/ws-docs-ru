# Модули DafsDict, DafsMask и DafsCombine

### Общее описание 

Используются для поиска файлов и директорий на целевых веб-сайтах \(DAFS — аббревиатура от Directories and Files Search\). Поиск производится по шаблону URL, в который на место маркировочного символа подставляется искомое имя.

В качестве признаков отрицательных ответов \(аналог кода 404\) можно использовать регулярные выражения \(совпадения ищутся в заголовках и телах ответов сервера\), размер тела ответа, коды статуса. Также можно указать регулярное выражение для определения положительного ответа \(аналог кода 200\).

Если вы указываете сразу несколько признаков отрицательных/положительных ответов, то у них будет следующий приоритет:

1. Регулярное выражение для определения положительного ответа \(аналог кода 200\)
2. Размер отрицательного ответа
3. Регулярное выражение для определения отрицательного ответа \(аналог кода 404\)
4. Код статуса HTTP

Если какой-либо из признаков показывает что запрошенный элемент существует, дальнейшие проверки не производятся. Например. Вы указали что признаком положительного ответа является фраза «found» в ответе сервера. WS делает запрос элемента X и получает ответ с кодом 404, в теле которого содержится фраза «found». Такой ответ будет считаться положительным и WS сообщит о нахождении элемента Х. Причиной является то, что наличие в ответе фразы определяющей положительный ответ приоритетнее проверки по коду статуса.

Поиск производится по маске, словарю и в комбинированном режиме \(маска + словарь\).

Работа модулей осуществляется как в режиме «сырого» http, так и средствами selenium.

### Опции \(\* - обязательно\)

| Имя | По умолчанию | raw | selenium | Описание |
| :--- | :--- | :--- | :--- | :--- |
| --template \* |  | Да | Да | Шаблон перебора. Маркировочным символом \(@ по умолчанию\) в нём отмечается то место, куда будет помещена проверяемая фраза. Примеры: «[http://site.com/@»](http://site.com/@»), «[https://site.com/@.php»](https://site.com/@.php»). |
| --dict \* |  | Да | Да | Для DafsDict. Путь к словарю для перебора. |
| --mask \* |  | Да | Да | Для DafsMask. Маска для перебора. |
| --combine-template \* |  | Да | Да | Для DafsCombine. Шаблон для комбинированного поиска. Строка с вхождениям маркеров «%m%» и «%d%» на чьё место подставляются слова из маски и словаря соответственно. |
| --found-re |  | Да | Да | Регулярное выражение \(python.re\) для определения положительного ответа веб-сервера \(аналог кода 200\) |
| --not-found-re |  | Да | Да | Регулярное выражение \(python.re\) для определения отрицательного ответа веб-сервера \(аналог кода 404\) |
| --not-found-size |  | Да | Да | Размер отрицательного ответа \(аналог кода 404\). Помните что он может отличаться у разных утилит. Пользуйтесь тестовым режимом чтоб узнать нужное вам значение. |
| --not-found-codes |  | Да | Нет | Набор кодов статуса \(через запятую\) которые будут считаться аналогами 404. |
| --method | GET | Да | Нет | HTTP-метод которым будет запрошен искомый URL: HEAD, POST, GET. |
| --proxies |  | Да | Да | Файл со списком http-proxy. |
| --retest-re |  | Да | Да | Регулярное выражение \(python.re\) для поиска в ответе сервера признака необходимости переотправить запрос. Например «Service Temporarily Unavailable». |
| --retest-codes |  | Да | Нет | Набор кодов \(через запятую\) указывающих на то, что запрос нужно отправить заново. Например «502,503». |
| --headers-file |  | Да | Нет | Файл с http заголовками для включения в заголовки запроса. |
| --ignore-words-re |  | Да | Да | Регулярное выражение \(python.re\) для игнорирования проверяемых фраз. Пригодится в случаях когда вам не нужно проверять слова из словаря/маски содержащие какой-либо фрагмент, например начинающиеся на «.ht». |
| --msymbol | @ | Да | Да | Маркировочный символ для шаблона поиска. |
| --delay | 0 | Да | Да | Задержка между запросами \(в секундах\). Касается не всех рабочих потоков в целом, а каждого потока в частности. |
| --threads | 10 | Да | Да | Количество рабочих потоков |
| --parts | 0 | Да | Да | На сколько частей разбить проверяемый список \(словарь, маску\) |
| --part | 0 | Да | Да | С какой из частей проверяемого списка работаем. |
| --test | 0 | Да | Да | Включение тестового режима |
| --xml-report | 0 | Да | Да | Путь к xml-отчёту |
| --selenium | 0 | Нет | Да | Включение selenium-режима |
| --browser-recreate-re |  | Нет | Да | Регулярное выражение \(python.re\). При совпадении в ответе веб-сервера бразер будет закрыт и запущен заново. При этом будет сменён прокси, если они используются. |
| --browser-wait-re |  | Нет | Да | Регулярное выражение \(python.re\). При совпадении в ответе веб-сервера браузер остановит работу и будет ждать пока совпадение не исчезнет. Может использоваться для ручного ввода captcha или обхода anti-ddos защит \(«wait 5 secs, we check your browser»\). |
