# TOR

WS способен работать с .onion-доменами. Для этого вам необходимо указать IP и порт socks-сервера TOR в config.ini в секции “\[tor\]”. По умолчанию это 127.0.0.1:9050. Там же есть параметр “http\_timeout” который в несколько раз больше своего аналога из секции “\[main\]”. Это связано с медленной работой TOR-узлов. Повышайте его если сканирование не может завершиться из-за большого количества ошибок.

Если вы зададите список прокси-серверов \(--proxies-list\) работая с .onion-доменом, то он будет проигнорирован.
