// TODO: 29.09.2024 Initial commit

# 1. Обзор микросервисной архитектуры

Микросервисная архитектура (МСА) – это современный подход к разработке программного обеспечения, который стал популярным
благодаря своей способности улучшать гибкость, масштабируемость и поддержку сложных систем. В отличие от монолитной
архитектуры, где все компоненты приложения связаны в единую структуру, микросервисы разбивают приложения на набор малых,
независимых сервисов, каждый из которых отвечает за конкретную бизнес-функцию. Эти сервисы взаимодействуют между собой
через API, что позволяет командам разрабатывать, тестировать и разворачивать их независимо друг от друга.

![sctructureMicroserviceSchema.png](attach%2FsctructureMicroserviceSchema.png)

_Рисунок – 1. Структурная схема архитектуры монолита и микросервисов._

## 1.1 Значение микросервисной архитектуры

Микросервисная архитектура (МСА) зарекомендовала себя как один из наиболее эффективных подходов к проектированию и
разработке программного обеспечения в условиях быстро изменяющегося бизнес-окружения. В отличие от традиционных
монолитных приложений, где весь код объединен в единую систему, микросервисы представляют собой набор независимых, малых
сервисов, каждый из которых может быть развернут, изменён и масштабирован отдельно. Эта концепция изменила не только
технологический ландшафт, но и подходы к ведению бизнеса, позволяя организациям быстрее реагировать на потребности
клиентов и условия рынка.

Значение микросервисной архитектуры в современном мире программного обеспечения трудно переоценить. Она предоставляет
организациям подходы к разработке, которые отвечают требованиям быстрого времени выхода на рынок, устойчивости к сбоям и
управления сложностью. Хотя переход на микросервисы может быть сопряжен с определенными вызовами, преимущества, которые
они предлагают, делают их привлекательным выбором для многих компаний. В конечном итоге, успешная реализация
микросервисной архитектуры требует не только технических знаний, но и изменений в организации процессов разработки, что
позволяет компаниям эффективно адаптироваться к условиям современного бизнеса и поддерживать конкурентоспособность.

## 1.2 Исторический контекст и эволюция архитектур

Исторический контекст и эволюция архитектур программного обеспечения представляет собой путь от монолитных приложений к
современным микросервисам, отражая изменения в технологиях и подходах к разработке.

В начальный период, когда программное обеспечение только начинало развиваться, приложения создавались как монолиты. Все
компоненты и функции находились в одном большом коде, что упрощало развертывание и управление. Однако такая архитектура
имела значительные недостатки: изменения в одной части приложения затрагивали другие, что усложняло тестирование и
обновление. Повышенная сложность модификации монолитов привела к созданию клиент-серверной архитектуры, которая
разделила логику приложения. Это позволило легче масштабировать и обновлять различные части системы, хотя управление
состоянием между клиентами и серверами оставалось сложной задачей.

С формированием сервисно-ориентированной архитектуры (SOA) в начале 2000-х годов разработка сделала шаг к более
модульному подходу. В SOA приложения делились на независимые сервисы, взаимодействующие через стандартизированные
интерфейсы, что способствовало повторному использованию компонентов. Однако эта модель требовала сложной инфраструктуры
и сталкивалась с проблемами производительности из-за многоуровневых взаимодействий.

Следующим этапом стала виртуализация и облачные технологии, которые значительно упростили разработку и тестирование
приложений. Облачные платформы, такие как AWS и Azure, позволили динамически масштабировать ресурсы и эффективно
управлять ими.

В результате, к 2010-м годам стала набирать популярность микросервисная архитектура. Этот подход предполагает создание
приложений как набора маленьких, независимых сервисов, отвечающих за конкретные функции. Микросервисы взаимодействуют
через легковесные механизмы, такие как REST API, что позволяет использовать разные технологии для разных сервисов.

Таким образом, эволюция архитектур от монолитов к микросервисам демонстрирует стремление к более гибким, масштабируемым
и независимым решениям. Микросервисная архитектура продолжает развиваться, интегрируя новые технологии и подходы, что
делает её ключевой парадигмой в разработке современных приложений. Понимание этой эволюции помогает осознать
преимущества и недостатки актуальных архитектурных моделей.

![architectureEvolution.jpg](attach%2FarchitectureEvolution.jpg)

_Рисунок - 1. Эволюция архитектуры._

# 2. Основы микросервисов

## 2.1 Определение микросервисов

Микросервисы — это архитектурный стиль, который структурирует приложение как набор небольших, независимых сервисов,
каждое из которых выполняет свою конкретную функцию и взаимодействует с другими сервисами через четко определенные
интерфейсы, обычно через API. Основная идея заключается в разделении большой и сложной системы на более мелкие,
управляемые и легко изменяемые компоненты.

## 2.2 Принципы микросервисной архитектуры

### 2.2.1 Независимость

Каждый микросервис должен быть независимым компонентом, который может разрабатываться, тестироваться, развертываться и
масштабироваться отдельно. Это позволяет командам работать параллельно, не мешая друг другу. При необходимости изменения
в одном микросервисе, другие сервисы могут продолжать функционировать без прерываний.

### 2.2.2 Автономность

Микросервисы должны иметь собственные базы данных и зависимостями, чтобы избежать взаимозависимости с другими сервисами.
Это сокращает риски, связанные с изменениями, и упрощает процесс развертывания.

### 2.2.3 Стандарты взаимодействия

Микросервисы должны взаимодействовать друг с другом по стандартным протоколам, таким как HTTP/REST, gRPC или message
queues. Использование стандартных интерфейсов для обмена данными упрощает интеграцию и повышает совместимость.

### 2.2.4 Управление данными

Каждый микросервис должен самостоятельно управлять своими данными. Это позволяет избежать проблем с согласованностью
данных и упрощает процесс миграции и обновления микросервисов.

### 2.2.5 Обработка ошибок

Микросервисы должны быть спроектированы так, чтобы устойчиво реагировать на сбои. Возможно использование паттернов,
таких как Circuit Breaker для предотвращения cascade failures и обработки ошибок без воздействия на общее приложение.

### 2.2.6 Масштабируемость

Микросервисы должны быть легкими для масштабирования как вертикально (увеличение ресурсов), так и горизонтально (
добавление новых инстансов). Это позволяет гибко реагировать на изменения нагрузки.

### 2.2.7 Технологическое разнообразие

Разные микросервисы могут использовать разные технологии и языки программирования. Это позволяет командам выбирать
наилучшие инструменты для каждой конкретной задачи и позволяет внедрять новые технологии по мере их появления.

### 2.2.8 Непрерывная интеграция и доставка (CI/CD)

Принципы CI/CD позволяют автоматизировать процессы сборки, тестирования и развертывания микросервисов, что повышает
скорость и качество разработки.

### 2.2.9 Мониторинг и логирование

Каждый микросервис должен иметь систему мониторинга и логирования, чтобы отслеживать его состояние и производительность.
Это помогает быстро обнаруживать и устранять проблемы.

### 2.2.9 Безопасность

Микросервисы должны быть спроектированы с учетом безопасности. Это включает авторизацию и аутентификацию, использование
шифрования и регулярные обновления компонентов.

# 3. Архитектурные паттерны микросервисов

Выбор архитектурного паттерна зависит от требований конкретной системы, сложности приложения и архитектурных
предпочтений. Каждый из паттернов имеет свои сильные и слабые стороны, и важно хорошо понимать их, чтобы принимать
обоснованные решения при проектировании микросервисной архитектуры.

## 3.1 REST (Representational State Transfer)

REST — это архитектурный стиль, который использует HTTP-протокол для взаимодействия между клиентом и сервером.

Принципы:

+ Статусные коды HTTP для обозначения состояния (200, 404, 500 и т.д.);
+ Использование URL для идентификации ресурсов;
+ Поддержка различных форматов (JSON, XML).

![trivialArchDisREST.png](attach%2FtrivialArchDisREST.png)

_Рисунок - 3. Тривиальный архитектурный дизайн REST API._

### 3.1.1 Преимущества REST API

REST API имеет множество преимуществ, включая простоту и понятность, так как использует стандартные HTTP-методы (GET,
POST, PUT, DELETE), что делает его интуитивно понятным для разработчиков. Он не зависит от платформы, позволяя
интегрировать его с любыми клиентами, будь то веб или мобильные приложения. REST API является безсостоянием (stateless),
что упрощает обработку запросов и увеличивает масштабируемость, так как сервер не хранит состояние сессий. Кроме того,
поддержка кэширования улучшает производительность, так как ответы могут сохраняться и ускорять время отклика. Легкость
интеграции с другими системами и поддержка различных форматов данных, таких как JSON и XML, делают его универсальным
решением. Масштабируемость позволяет легко увеличивать ресурсы по мере роста нагрузки, а независимость клиента и сервера
дает возможность развивать их отдельно друг от друга. В целом, преимущества REST API делают его идеальным выбором для
создания высокопроизводительных приложений.

### 3.1.2 Недостатки REST API

REST API имеет несколько недостатков, которые стоит учитывать. Во-первых, его безсостояние (stateless) может привести к
необходимости повторной передачи идентификационных и авторизационных данных с каждым запросом, что может увеличить объем
трафика и снизить производительность. Также это может усложнить управление сессиями для приложений, требующих сохранения
состояния.

Во-вторых, REST API может иметь ограниченные возможности в сравнении с более сложными протоколами, такими как GraphQL,
которые позволяют более гибко запрашивать данные. Это может привести к множественным запросам для получения сложных
данных, что негативно сказывается на производительности.

Еще одним недостатком является отсутствие строгой схемы данных, что может привести к неоднозначностям и проблемам с
согласованностью данных. Кроме того, REST API не поддерживает форматирование запросов и ответов в реальном времени, что
может быть критично для приложений, требующих мгновенной синхронизации.

Также REST API может быть подвержен проблемам с безопасностью, если не реализованы надлежащие механизмы аутентификации и
авторизации. Наконец, для больших проектов с высоким трафиком управление версионированием может стать сложной задачей,
требующей внимательного планирования.

## 3.2 GraphQL

GraphQL — это язык запросов для API, который позволяет клиентам запрашивать только те данные, которые им нужны.

Принципы:

+ Запросы формируются в виде единого запроса к серверу;
+ Возможность объединения нескольких ресурсов в одном запросе.

![trivialArchGraphQL.png](attach%2FtrivialArchGraphQL.png)

_Рисунок – 4. Тривиальный архитектурный дизайн GraphQL._

### 3.2.1 Преимущества GraphQL

GraphQL — это мощный инструмент для работы с API, который предлагает множество преимуществ по сравнению с традиционными
REST API. Во-первых, одним из ключевых преимуществ GraphQL является возможность получать точно те данные, которые нужны
клиенту, без излишних запросов. Клиенты формируют запросы, указывая, какие именно поля им необходимы, что минимизирует
объем передаваемых данных и оптимизирует производительность. Это особенно полезно для мобильных и веб-приложений, где
ограничены ресурсы и пропускная способность сети.

Во-вторых, GraphQL обеспечивает единый эндпоинт для всех запросов, тогда как в REST API каждому ресурсу соответствует
отдельный URL. Это упрощает структуру и делает управление API более удобным, так как все запросы попадают в одно место.
Разработчики могут быстрее и проще тестировать и документировать свои API, что ускоряет процесс разработки.

Еще одним важным аспектом является возможность версии API. В GraphQL версии не нужно создавать, так как клиенты просто
запрашивают нужные им поля. Если новое поле добавлено, старые запросы всё равно продолжают работать, что значительно
уменьшает вероятность столкновений и проблем с совместимостью.

Кроме того, GraphQL предоставляет мощные средства для получения связанных данных. Вместо того чтобы делать несколько
запросов для получения информации от разных ресурсов, можно получить все необходимые данные в одном запросе, что
упрощает логику клиентского приложения и снижает количество сетевых операций. Это особенно эффективно в сложных
приложениях, где связь между данными может быть глубокой и многоуровневой.

Наконец, GraphQL поддерживает типизацию и схемы, что позволяет клиентам и серверам заранее знать, какие данные доступны
и какие ошибки могут возникнуть. Это делает разработку более предсказуемой и снижает риск ошибок, которые могут
возникнуть на этапе выполнения.

Таким образом, использование GraphQL позволяет разработчикам создавать более гибкие, эффективные и масштабируемые API,
что делает его всё более популярным выбором среди современных технологий разработки.

### 3.2.2 Недостатки GraphQL

Несмотря на множество преимуществ, GraphQL имеет и свои недостатки, которые стоит учитывать. Во-первых, одной из
основных проблем является сложность освоения. Для разработчиков, привыкших работать с REST API, переход на GraphQL может
потребовать значительного времени и усилий на изучение новой концепции, синтаксиса запросов и управления схемами.

Во-вторых, из-за гибкости запросов есть риск излишней нагрузки на сервер. Поскольку клиенты могут запрашивать
произвольные данные, это может привести к созданию запросов, которые затрачивают много ресурсов и времени на обработку.
Это создает необходимость в сложной оптимизации и ограничениях на стороне сервера, чтобы избежать мощных и ресурсоемких
запросов.

Третьим недостатком является сложность кэширования. В REST API легко кэшировать данные, так как каждый URL соответствует
определенному ресурсу. В GraphQL же запросы динамические, и данные могут изменяться в зависимости от запрашиваемых
полей, что усложняет процесс кэширования и требует разработки более продвинутых механизмов для эффективного хранения и
извлечения данных.

Также стоит отметить, что GraphQL может стать неэффективным при работе с очень большими объемами данных.
Структурированные запросы могут усложнить процесс пагинации и ограничение результата, что может привести к избыточной
передаче данных.

Кроме того, управление безопасностью и авторизацией может стать более запутанным в GraphQL. Поскольку запросы могут
запрашивать произвольные поля, это требует тщательной настройки разрешений и проверки данных, чтобы избежать утечек
информации и несанкционированного доступа.

Наконец, у GraphQL может быть ограниченная поддержка некоторых инструментов и фреймворков, особенно в сравнении с REST,
который имеет обширные экосистемы библиотек и инструментов. Это может усложнить интеграцию и использование GraphQL в
старых проектах или в тех случаях, когда требуется совместимость с существующими системами.

Таким образом, хотя GraphQL предлагает множество преимуществ, важно учитывать и его недостатки, чтобы сделать
обоснованный выбор при разработке API.

## 3.3 gRPC (gRPC Remote Procedure Calls)

gRPC — это фреймворк для удаленных вызовов процедур, который работает по протоколу HTTP/2 и поддерживает множество
языков программирования.

Принципы:

+ Поддержка бинарного формата передачи данных (Protocol Buffers);
+ Поддержка потокового взаимодействия.

![trivialArchgRPC.png](attach%2FtrivialArchgRPC.png)

_Рисунок – 5. Тривиальный архитектурный дизайн gRPC._

### 3.3.1 Преимущества gRPC

Один из ключевых аспектов gRPC — это его производительность. Протокол использует HTTP/2, что позволяет осуществлять
мультиплексирование запросов и уменьшает задержку передачи данных. Это особенно важно для приложений, требующих высокой
скорости и быстрого ответа от серверов.

Преимуществом gRPC также является поддержка различных языков программирования, что позволяет разработчикам создавать
приложения на разных языках, сохраняя единый интерфейс для взаимодействия. Это даёт возможность использовать gRPC как
связующее звено между компонентами системы, написанными на разных языках.

Кроме того, gRPC использует Protocol Buffers (protobuf) для сериализации данных, что делает обмен сообщениями между
клиентом и сервером более эффективным по сравнению с форматами, такими как JSON или XML. Protocol Buffers обеспечивают
компактность и скорость сериализации, что снижает объем передаваемых данных и ускоряет их обработку.

Также стоит отметить, что gRPC предоставляет встроенные механизмы для аутентификации и авторизации, что упрощает
создание безопасных распределенных приложений. При этом gRPC поддерживает поточные вызовы, позволяя клиентам и серверам
обмениваться данными в реальном времени, что делает его идеальным для приложений с постоянным обновлением данных, таких
как мессенджеры или системы мониторинга.

Таким образом, gRPC обеспечивает высокую производительность, поддержку множества языков, эффективную сериализацию
данных, безопасность и возможности потоковой передачи, что делает его привлекательным выбором для современных
распределенных систем и микросервисной архитектуры.

### 3.3.2 Недостатки gRPC

Несмотря на множество преимуществ, gRPC имеет и некоторые недостатки, которые стоит учитывать при его использовании.
Во-первых, gRPC требует поддержки HTTP/2, что может создать проблемы совместимости с некоторыми старыми клиентами и
серверами, которые работают только с HTTP/1.1. Это может ограничивать выбор технологий или усложнять интеграцию с
существующей инфраструктурой.

Во-вторых, использование Protocol Buffers для сериализации данных требует предварительного определения схемы и
дополнительных шагов в процессе разработки, что может увеличить сложность работы с системой. Это также означает, что
разработчики должны иметь представление о protobuf и быть готовы к изменениям в схемах, что может быть сложно в больших
командах.

Другой недостаток — это необходимость знания и понимания подхода RPC, который может отличаться от более привычных
RESTful API. Это может потребовать от команды адаптации и повышения квалификации для эффективной работы с gRPC.

К тому же, хотя gRPC поддерживает аутентификацию, его конфигурация может быть более сложной по сравнению с некоторыми
другими технологиями. Для реализации безопасного обмена данными может потребоваться больше времени и усилий.

Наконец, gRPC не вполне подходит для публичных API, так как его использование может значительно усложнить процесс
интеграции с клиентами, которые ожидают простоты и удобства взаимодействия, характерного для RESTful API с
использованием JSON.

Таким образом, недостатки gRPC заключаются в ограничениях совместимости, сложности работы с Protocol Buffers,
необходимости изучения RPC-подхода, сложности конфигурации безопасности и менее удобном использовании для публичных API.

## 3.4 Event-driven Architecture (Событийная архитектура)

В этом паттерне взаимодействие между сервисами осуществляется на основе событий, которые генерируются и обрабатываются
асинхронно.

Принципы:

+ Использование систем обмена сообщениями (например, RabbitMQ, Apache Kafka);
+ Сервис реагирует на события, а не делает непосредственные вызовы другим сервисам.

![trivialArchEDA.png](attach%2FtrivialArchEDA.png)

_Рисунок – 6. Тривиальный архитектурный дизайн Event-driven Architecture._

### 3.4.1 Преимущества Event-driven Architecture

Event-driven architecture (EDA) предоставляет ряд значительных преимуществ, благодаря которым она становится всё более
популярной в разработке современных информационных систем. Во-первых, EDA обеспечивает высокую степень масштабируемости.
Системы, основанные на событиях, могут легко адаптироваться к увеличению нагрузки, так как новые компоненты могут
добавляться или удаляться без необходимости изменения существующих. Это делает EDA идеальной для динамично развивающихся
бизнес-приложений.

Во-вторых, архитектура, ориентированная на события, способствует повышенной гибкости и реактивности систем. В EDA
инициируются события, на которые различные компоненты системы могут реагировать независимо. Это позволяет приложениям
быстрее адаптироваться к изменениям в бизнес-логике и требованиям пользователей, что является ключевым фактором в
условиях быстро меняющегося рынка.

Третьим значительным преимуществом является улучшенная обработка данных в реальном времени. EDA позволяет обрабатывать и
анализировать данные по мере их поступления, что даёт возможность принимать оперативные решения и усиливает возможность
аналитики данных. Это особенно полезно для таких областей, как финансовые сервисы или интернет-торговля, где задержки
могут привести к упущенным возможностям.

Кроме того, EDA способствует лучшей изолированности компонентов системы. Каждый компонент в EDA выполняет свою задачу и
взаимодействует с другими через событийные сообщения, что минимизирует зависимость между ними. Это упрощает тестирование
и обслуживание системы, так как изменения в одном компоненте не влияют на другие.

Наконец, архитектура, ориентированная на события, улучшает общее восприятие пользователями. За счёт быстрой обработки
событий и гибкости приложения, пользователи могут получать более качественное взаимодействие и увеличенную
производительность. В результате, EDA не только повышает эффективность разработки и сопровождения приложений, но и
способствует созданию более удобных и отзывчивых решений для конечных пользователей.

### 3.4.2 Недостатки Event-driven Architecture

Event-driven architecture (EDA), несмотря на свои преимущества, имеет ряд недостатков, которые стоит учитывать при её
внедрении. Во-первых, одним из основных минусов является повышенная сложность системы. Архитектура, основанная на
событиях, требует тщательного проектирования взаимодействий и обработки событий, что может привести к сложным механизмам
управления и координации между компонентами.

Во-вторых, отладка и мониторинг таких систем может быть значительно сложнее. Поскольку компоненты взаимодействуют через
асинхронные события, отслеживание потока исполнения и выявление причин проблем требуют дополнительных инструментов и
методик. Это может увеличить время на диагностику и решение проблем.

Третьим недостатком является потенциальная потеря данных. В случае сбоя в системе, особенно в распределенных системах,
могут возникнуть ситуации, когда события не обрабатываются или теряются. Это требует создания надежных механизмов
гарантирования доставки и обработки событий, что, в свою очередь, добавляет дополнительную сложность.

Четвёртым аспектом является сложность обеспечения согласованности данных. В распределенных системах, работающих на
основе событий, поддержание консистентности данных может стать реализационным вызовом, особенно при наличии нескольких
источников данных и асинхронной природы обработки событий.

Наконец, EDA может потребовать значительных затрат на инфраструктуру и обучение команды. Переход на архитектуру,
ориентированную на события, часто связан с необходимостью внедрения новых технологий и инструментов, что может
потребовать времени и ресурсов для адаптации. Эти факторы могут ограничивать применение EDA для небольших или простых
приложений, где более традиционные подходы могут быть более целесообразными.

## 3.5 Saga Pattern

Паттерн саги используется для управления распределенными транзакциями с помощью организации последовательности локальных
транзакций.

Принципы:

+ Оркестрация
    + Центральный координатор (менеджер саги) контролирует процесс выполнения с учетом последовательности транзакций;
    + Он отвечает за запуск локальных транзакций и обработку их результатов, инициируя компенсирующие операции при
      необходимости;
    + Пример: бизнес-логика реализована в центральном сервисе, который управляет последовательностью шагов.
+ Хореография
    + Каждый сервис, участвующий в саге, самостоятельно сообщает об успешном выполнении своей транзакции, инициируя
      следующую;
    + Сервисы обрабатывают события, что позволяет им взаимодействовать без центрального координатора;
    + Пример: каждый сервис излучает события, на которые подписываются другие сервисы для выполнения своих действий.

![trivialArchSaga.png](attach%2FtrivialArchSaga.png)

_Рисунок – 6. Тривиальный архитектурный дизайн Saga Pattern._

### 3.5.1 Преимущества Saga Pattern

Основные преимущества заключаются в том, что он обеспечивает высокую степень надежности и согласованности данных без
необходимости использовать блокировки, как в традиционных транзакциях. Saga разбивает длинные операции на более мелкие,
независимые шаги, что позволяет каждой службе обрабатывать свои части транзакции автономно. Это не только снижает риск
блокировок и повышает производительность системы, но и увеличивает ее масштабируемость, так как каждый сервис можно
независимо развивать и разворачивать.

Кроме того, Saga допускает асинхронные взаимодействия, что позволяет избежать долгих ожиданий между сервисами и сделать
систему более отзывчивой. В случае возникновения ошибок механизм компенсационных действий позволяет откатить изменения,
обеспечивая тем самым согласованность данных. Это делает паттерн Saga особенно полезным для бизнес-процессов, где
требуются надежные обновления состояния, такие как заказы, бронирования и финансовые транзакции. Такой подход также
упрощает тестирование и отладку, так как каждый шаг Saga можно проверить отдельно. В целом, использование Saga Pattern
способствует улучшению устойчивости системы, её гибкости и возможности обработки сложных бизнес-логик в распределенной
архитектуре.

### 3.5.2 Недостатки Saga Pattern

Несмотря на множество преимуществ, паттерн Saga также имеет свои недостатки. Во-первых, его реализация может быть
довольно сложной, особенно в случае больших и многоуровневых саг, требующих тщательного управления состоянием и логикой
каждого шага. Это может привести к увеличению сложности кода и затрат на его поддержку.

Во-вторых, асинхронная природа взаимодействий может усложнить отладку и мониторинг процессов. Ошибки могут возникать на
любом этапе, и отследить их источник может быть непросто. Это требует дополнительных инструментов для логирования и
анализа, чтобы обеспечить видимость в выполнении саги.

Также, в случае использования механизмов компенсации в случае ошибок, управление состоянием может стать запутанным.
Сложные сценарии компенсации могут привести к несогласованности данных, если не учитывать все возможные пути и
зависимости.

Кроме того, паттерн Saga может не всегда подходить для задач, где требуется строгая атомарность транзакций. В случаях,
когда операции должны быть выполнены точно или не выполнены вовсе, Saga может не обеспечить нужный уровень гарантии.

Наконец, если в системе много микросервисов с различными сагами, это может привести к увеличению сетевых вызовов и
задержек, что в итоге негативно скажется на производительности системы. Поэтому, несмотря на свои преимущества,
внедрение Saga Pattern требует тщательного анализа и проектирования, чтобы минимизировать потенциальные недостатки.