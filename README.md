#### Домашнее задание к занятию «Базы данных, их типы» "Сергей Шульга"

### Задание 1. СУБД
Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.

Реляционная база данных – это набор данных с предопределенными связями между ними. Эти данные организованны в виде набора таблиц, состоящих из столбцов и строк. В таблицах хранится информация об объектах, представленных в базе данных. В каждом столбце таблицы хранится определенный тип данных, в каждой ячейке – значение атрибута. Каждая стока таблицы представляет собой набор связанных значений, относящихся к одному объекту или сущности.
Документно-ориентированные СУБД хранят документы — структурированные тексты, имеющие конкретный синтаксис. Это популярная разновидность NoSQL СУБД, которая подходит для проектов, где в таблицах хранят объекты с разной структурой (списки, словари). Нельзя сказать, что это база для систем документооборота, хотя Документные СУБД сохраняют состояние, а не поведение. Зато они поддерживают проверку схему и сейчас активно развиваются. Среди популярных СУБД этого типа — CouchDB, MongoDB, Amazon DocumentDB.
Реляционные базы данных, или базы данных SQL Основная особенность — надежность и неизменяемость данных, низкий риск потери информации. При обновлении данных их целостность гарантирована, они заменяются в одной таблице. Подойдут Oracle, Microsoft SQL, PostgreSQL, MySQL

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?

СУБД типа ключ-значение Чаще всего такие СУБД используют для кэширования, т.к. они очень быстро работают, а это и не сложно, когда есть уникальный ключ, и запрос возвращает только одно значение. подойдут Redis, Memcached. md5 - это быстрый хэш. То есть он предназначен для использования больших объемов данных и вывода хэша очень, очень быстро.

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.

MySQL Данная СУБД работает с реляционными данными и имеет свободное программное обеспечение, считается одной из самых гибких и быстродействующих, поэтому ее предлагают использовать для проектов малых и средних объемов.


1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?
PostgreSQL — поддержка большого количества типов записи информации. Это не только стандартные целочисленные значения, числа с плавающей точкой, строки и булевы значения («да/нет»), но и денежный, геометрический, перечисляемый, бинарный и другие типы. PostgreSQL «из коробки» поддерживает битовые строки и сетевые адреса, массивы данных, в том числе многомерные, композитные типы и другие сложные структуры. В ней есть поддержка XML, JSON и NoSQL-баз.

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

MongoDB рассчитана на работу с данными иерархической структуры. По сути, это хранилище документов без использования схематичного или табличного форматов, поэтому ее еще называют документоориентированной. MongoDB базы данных подключаются к приложениям через драйверы баз данных. Несколько типов данных обрабатываются одновременно и для этой цели используется внутренний кэш. Плюсы MongoDB:
- простой доступ к данным;
- их хранение;
- ввод и извлечение.
Одним из преимуществ MongoDB, вытекающих из его природы NoSQL, является быстрая и простая обработка данных. СУБД MongoDB рекомендуют использовать там, где отсутствуют потребности в сложных выборках.
Вместо таблиц в MongoDB используются коллекции. Это наборы из документов. В одном наборе могут храниться документы с разнообразными данными — это главное отличие от таблиц. Коллекция разнородна, документы внутри нее могут различаться структурой, размером, значениями и связями. Поэтому MongoDB считается отличным выбором для хранения слабо структурированной информации.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?

У MongoDB открытый исходный код. С помощью идентификатора можно осуществлять манипуляции над объектом с высокой скоростью. При сложных операциях СУБД тоже демонстрирует весьма хорошие показатели. Это связано с тем, что ПО относится к типу NoSQL и использует объектный язык запросов, который намного легче SQL.

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.

Графовые СУБД - специфичный тип, предназначены для работы с графами, с их узлами, свойствами, и произвольными отношениями между узлами. Очень простой пример, это организация связей в различного типа социальных сетях, где нужно хранить связи между пользователями (узлами) по разным критериям (родственные связи, коллеги, общие интересы). Известные представители этого типа субд - Neo4j, Amazon Neptune, InfiniteGraph, InfoGrid.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?
Лучше создать свою СУБД.
1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

Приведите ответ в свободной форме.

### Задание 2. Транзакции
2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.
#### проверка баланса на счету в банке, ввести номер телефона счет которого нужно пополнить, ввести сумму на которую нужно пополнить, подтвердить перевод денежных средств со счета в банке (происходит уменьшение баланса на счету, сохраняется новое значение), проверка баланса на счету телефона (происходит уведичение баланса на счету телефона, сохраняется новое значение), проверить пополнение счета.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?
- мобильный оператор отслеживает баланс телефона;
- при падении баланса ниже определеной суммы оператор отправляет запрос в банк;
- создается автоматический запрос на пополнение балпнса со счета клиента на баланс телефона;
- банк перечисляет заранее установленную сумму со счета клиента на счет указанного номера;
- автоматическая транзакция и подтверждение поступления денежных средств на номер телефона.

### Задание 3. SQL vs NoSQL
3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.
различия между SQL и NoSQL заключаются в:
- Базы данных SQL являются реляционными, а базы данных NoSQL - нереляционными.
- Базы данных SQL используют язык структурированных запросов (SQL) и имеют предопределенную схему. Базы данных NoSQL имеют динамические  схемы для неструктурированных данных.
- Базы данных SQL масштабируются по вертикали, в то время как базы данных NoSQL масштабируются по горизонтали.
- Базы данных SQL основаны на таблицах, в то время как базы данных NoSQL представляют собой хранилища документов, значений-ключей, графиков или больших столбцов.
- Базы данных SQL лучше подходят для многорядных транзакций, в то время как NoSQL лучше подходит для неструктурированных данных, таких как документы или JSON.

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

Технические характеристики решений NewSQL:
- SQL как основной механизм для взаимодействия;
- ACID поддержка транзакций;
- Механизм управления без применения блокировок, таким образом считывающие данные в реальном времени не будут находится в противоречии с записывающими, что исключает конфликт;
- Архитектура, обеспечивающая намного выше производительность узла;
- Удобное масштабирование, способное управлять большим количеством узлов, не перенося узкие места.
NewSQL - идеальный выбор. NewSQL улучшает SQL, обеспечивая горизонтальную масштабируемость при сохранении свойств ACID. Это облегчает работу с большими данными за счет реализации параллелизма. Он также хорошо справляется с соблюдением требований ACID. Таким образом, NewSQL, похоже, нашел оптимальное соотношение между скоростью, масштабируемостью, согласованностью и доступностью. Несмотря на то, что NewSQL все еще находится на стадии зарождения, у него есть все необходимые параметры, чтобы стать идеальной базой данных для приложений Big Data и OLTP. 

### Задание 4. Кластеры
Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.
На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?
Приведите ответ в свободной форме.
Критерии выбора:
- Тип проекта (Под типом проекта подразумевается сфера, в которой этот проект будет применяться: персональная или коммерческая. Тип проекта определяет критерии для сравнения СУБД);
- Что будем хранить (В разных системах используются разные движки. Одни лучше работают с текстом, а другие с медиаконтентом. Поэтому желательно заранее знать, какой контент будет храниться в БД);
- Объем (У каждой системы управления базами данных есть документация, в которой отражены ограничения на объем одного файла, таблицы и т.д. Если планируете хранить большие объемы, то не все решения подойдут);
- Нагрузка (Желательно заранее представлять, какое количество людей или компьютеров будет обращаться к БД в один момент);
- Масштабируемость; 
- Безопасность;
- Отказоустойчивость ( Отказоустойчивость системы определяется её способностью сохранить информацию и работоспособность в случае сбоя: отключения электричества, человеческая или программная ошибка. Если проект — это небольшой блог и при сбое будет потеряна статья, то это неприятно, но всё же некритично. А вот в случае банковской системы потеря информации скорее всего приведет к потере денежных средств);

Я думаю использовать колоночные СУБД, они похожи на реляционные, однако в них информация хранится не построчно, а по столбцам. 

Для получения значения атрибута одного из объектов в таблице в реляционных базах придется прочитать всю строку до нужной колонки. В колоночных СУБД будет прочитан сразу необходимый атрибут. На практике это позволяет ускорить чтение при больших (сто миллионов записей и больше) объемах. Колоночные БД используются в качестве хранилищ данных с большим объемом информации. При обработке маленьких объемов преимущество чтения не будет заметно. 
Самая популярная колоночная СУБД — Cassandra.
Можно использовать Hadoop — это программная платформа для сбора, хранения и обработки очень больших объемов данных. Проще говоря, это база данных (database), предназначенная для работы с большими данными (Big Data).Набор утилит, библиотек и фреймворк для разработки и выполнения распределенных программ, работающих на кластерах из сотен и тысяч узлов. Из преимуществ поисковые и контекстные механизмы высоконагруженных веб-сайтов и интернет-магазинов в том числе аналитики поисковых запросов и пользовательских логов,хранение, сортировка огромных объемов данных и разбор содержимого чрезвычайно больших файлов,быстрая обработка графических данных.
