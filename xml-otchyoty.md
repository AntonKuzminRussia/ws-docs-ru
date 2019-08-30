# XML-отчёты

Данная возможность пригодится для автоматизации сканирований. У всех модулей есть опция «--xml-report» в которой нужно указать путь к отчёту без расширения. Например «--xml-report /tmp/test». Тогда WS создаст файлы /tmp/test-result.xml, /tmp/test-errors.xml и /tmp/test-progress.xml. Они отвечают за результаты сканирования, ошибки и прогресс соответственно.

```text
<root>
    <results>
        <item>
..
        </item>
        <item>
...
        </item>
</root>
```

Для разных модулей содержимое тега разное. Его формат вы можете увидеть запустив нужный модуль с данной опцией.

Формат -errors.xml:

```text
<root>
    <errors>
        <error>
            <text>some error</text>
            <trace>...</trace>
            <timestamp>1557102331</timestamp>
        </error>
        ...
    </errors>
</root>
```

Ошибки перестают заноситься в отчёт после того как их количество превышает 1000.

Формат -progress.xml:

```text
<root>
    <progress>
        <count_now>9000</count_now>
        <full_count>71746</full_count>
        <percent_done>12.54</percent_done>
        <time_now>35s</time_now>
        <time_left>3m 54s</time_left>
        <speed>272.45</speed>
    </progress>
</root>
```

Файл обновляется каждый раз когда в консоли отображается строка прогресса. Здесь:

* count\_now — сколько объектов проверено на данный момент 
* full\_count — сколько объектов всего 
* percent\_done — процент завершенности 
* time\_now — время которое работает WS 
* time\_left — сколько осталось работать 
* speed — скорость работы, объектов в секунду

