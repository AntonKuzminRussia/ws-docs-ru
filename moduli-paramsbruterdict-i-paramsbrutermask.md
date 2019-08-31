# Модули ParamsBruterDict и ParamsBruterMask

### Общее описание 

Модули занимаются поиском параметров с которыми можно обращаться к URL. Логика работы основана на том, что обращение к URL с определёнными параметрами изменяет контент возвращаемый им.

Возможно 4 варианта поиска — методами GET, POST, в cookies и загружаемых файлах. Поиск методом GET выглядит как запрос URL с большим количеством параметров. У метода POST параметры передаются в теле запроса. В поиске через cookies параметры передаются как множество cookies с различными именами. А в поиске через загружаемые файлы на сервер отправляются запросы загрузки нескольких файлов с мизерным содержимым.

Важный момент. Количество одновременно передаваемых в запросах параметров регулируется опцией «--max-params-length». Она имеет двойное значение. Для GET и POST это максимальная длина строки параметров вместе с их значением и амперсандами \(a=1&b=1&c=1...\). Для cookies и файлов это количество самих имён проверяемых за один запрос. Рекомендуемые значения параметра «--max-params-length» для GET и POST составляют 1000. Для cookies и файлов — 20.

Значение, помещаемое в искомые параметры по умолчанию «1» и может меняться через указание опции «--value».

Работа модулей осуществляется как в режиме «сырого» http, так и средствами selenium.
