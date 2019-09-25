# Быстрый старт

### Поиск URL

Простой поиск по словарю:

```text
./main.py UrlsDict --template http://simple.polygon.web-scout.online/@ --dict bases/demo/dict.txt
```

Простой поиск по словарю в selenium-режиме:

```text
./main.py UrlsDict --template http://selenium.polygon.web-scout.online/@ --dict bases/demo/dict.txt --selenium 1 --browser-wait-re "checking" --not-found-re "Not Found"
```

Поиск на сайте, который отвечает 200 на запрос несуществующих страниц:

```text
./main.py UrlsDict --template http://always-200.polygon.web-scout.online/@ --dict bases/demo/dict.txt --not-found-re "Page not found"
```

Поиск с восприятием кода 500 как 404:

```text
./main.py UrlsDict --template http://always-500.polygon.web-scout.online/@ --dict bases/demo/dict.txt --not-found-codes 500
```

Поиск с повторением запроса при получении кода 503:

```text
./main.py UrlsDict --template http://sometimes-503.polygon.web-scout.online/@ --dict bases/demo/dict.txt --retest-codes 503
```

Поиск с повторением запроса при наличии фразы "Too big load" в ответе сервера:

```text
./main.py UrlsDict --template http://sometimes-503.polygon.web-scout.online/@ --dict bases/demo/dict.txt --retest-re "Too big load"
```

## Раскрытие контента

Простой запуск для поиска новых URL:

```text
./main.py ContentDiscovery --template http://simple.polygon.web-scout.online/@ --urls-file bases/demo/cd-urls.txt 
```

## Поиск поддоменов

Простой поиск поддоменов:

```text
./main.py DnsDict --template @.standart-zone.polygon.web-scout.online --dict bases/demo/dict.txt
```

Поиск поддоменов в wildcard-зоне с игнорированием IP по умолчанию:

```text
./main.py DnsDict --template @.wildcard-ip.polygon.web-scout.online --dict bases/demo/dict.txt --ignore-ip 8.8.8.8
```

Поиск поддоменов в wildcard-зоне методом запроса найденных имён на веб-сервере:

```text
./main.py DnsDict --template @.wildcard-web.polygon.web-scout.online --dict bases/demo/dict.txt --http-not-found-re "Ubuntu Default Page"
```

## Поиск виртуальных хостов

Поиск виртуального хоста на веб-сервере:

```text
./main.py HostsDict --ip 82.146.56.21 --dict bases/demo/dict.txt --template @.hostsbrute.polygon.web-scout.online --false-re "Ubuntu Default Page"
```


## Поиск параметров URL

Поиск параметров скрипта методом GET:

```text
./main.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-get.php --dict bases/demo/dict.txt --max-params-length 1000 --params-method GET --not-found-re NOT
```

Поиск параметров скрипта принимающего файлы на загрузку:

```text
./main.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-files.php --dict bases/demo/dict.txt --max-params-length 10 --params-method FILES --not-found-re NOT
```

## Брутфорс формы

Простой брут POST формы:

```text
./main.py Forms --url http://simple.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-str "login=^USER^&password=^PASS^" --false-re "User: " --login admin
```

Брут формы в selenium-режиме:

```text
./main.py Forms --url http://selenium.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-file bases/demo/form-brute.conf --false-re "User: " --login admin --selenium 1 --browser-wait-re "checking"
```

## Фаззинг

Фаззинг параметров URL

```text
./main.py FuzzerUrls --urls-file bases/demo/fuzzer-urls.txt
```

Фаззинг заголовков URL:

```text
./main.py FuzzerHeaders --urls-file bases/demo/fuzzer-headers.txt
```