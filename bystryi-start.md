# Быстрый старт

### Поиск URL

Простой поиск по словарю:

```text
./ws.py UrlsDict --template http://simple.polygon.web-scout.online/@ --dict bases/demo/dict.txt
```

Простой поиск по маске:

```text
./ws.py UrlsMask --template http://simple.polygon.web-scout.online/@ --mask ?l,1,4
```

Простой поиск по словарю в selenium-режиме:

```text
./ws.py UrlsDict --template http://selenium.polygon.web-scout.online/@ --dict bases/demo/dict.txt --selenium 1 --browser-wait-re "checking" --not-found-re "Not Found"
```

## Раскрытие контента

Простой запуск для поиска новых URL:

```text
./ws.py ContentDiscovery --template http://simple.polygon.web-scout.online/@ --urls-file bases/demo/cd-urls.txt 
```

## Поиск поддоменов

Простой поиск поддоменов:

```text
./ws.py DnsDict --template @.standart-zone.polygon.web-scout.online --dict bases/demo/dict.txt
```

Простой поиск поддоменов по маске:

```text
./ws.py DnsMask --template @.standart-zone.polygon.web-scout.online --mask ?l,1,4
```

## Поиск виртуальных хостов

Поиск виртуального хоста на веб-сервере по словарю:

```text
./ws.py HostsDict --ip 82.146.56.21 --dict bases/demo/dict.txt --template @.hostsbrute.polygon.web-scout.online --false-re "Ubuntu Default Page"
```

Поиск виртуального хоста на веб-сервере по маске:

```text
./ws.py HostsMask --ip 82.146.56.21 --mask ?l,1,4 --template @.hostsbrute.polygon.web-scout.online --false-re "Ubuntu Default Page"
```

## Поиск параметров URL

Поиск параметров скрипта методом GET по словарю:

```text
./ws.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-get.php --dict bases/demo/dict.txt --max-params-length 1000 --params-method GET --not-found-re NOT
```

Поиск параметров скрипта методом GET по маске:

```text
./ws.py ParamsMask --url http://simple.polygon.web-scout.online/params-bruter-dict-get.php --mask ?l,1,2 --max-params-length 1000 --params-method GET --not-found-re NOT
```

Поиск параметров скрипта принимающего файлы на загрузку:

```text
./ws.py ParamsDict --url http://simple.polygon.web-scout.online/params-bruter-dict-files.php --dict bases/demo/dict.txt --max-params-length 10 --params-method FILES --not-found-re NOT
```

## Брутфорс формы

Простой брут POST формы:

```text
./ws.py Forms --url http://simple.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-str "login=^USER^&password=^PASS^" --false-re "User: " --login admin
```

Брут формы в selenium-режиме:

```text
./ws.py Forms --url http://selenium.polygon.web-scout.online/admin.php --dict bases/demo/dict.txt --conf-file bases/demo/form-brute.conf --false-re "User: " --login admin --selenium 1 --browser-wait-re "checking"
```

## Фаззинг

Фаззинг параметров URL

```text
./ws.py FuzzerUrls --urls-file bases/demo/fuzzer-urls.txt
```

Фаззинг заголовков URL:

```text
./ws.py FuzzerHeaders --urls-file bases/demo/fuzzer-headers.txt
```