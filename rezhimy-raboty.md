# Режимы работы

WS осуществляет работу в двух глобальных режимах. Первый — режим «сырого» http. Ниже он будет обозначаться как «raw». Это самый быстрый и гибкий режим работы и, как правило, его достаточно для большинства случаев. В нём WS шлёт целевому серверу http запросы напрямую, после чего анализирует полученный ответ.

Второй — работа с использованием Selenium \(ниже будет обозначаться как «selenium»\). В данном режиме работа с целевым сервером происходит через браузер Firefox. Скорость такой работы очень низкая и имеются существенные ограничения по анализу ответов сервера. Зато на стороне сервера создаётся впечатление работы с ним реального пользователя. Подробнее об этом вы можете почитать в соответствующем разделе документации.

Не всегда один и тот же параметр модуля может быть использован в обоих режимах. Для таких случаев в таблицах параметров имеются соответствующие колонки.

