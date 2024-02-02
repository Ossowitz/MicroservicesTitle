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

### 3.1 REST (Representational State Transfer)

REST — это архитектурный стиль, который использует HTTP-протокол для взаимодействия между клиентом и сервером.

Принципы:

+ Статусные коды HTTP для обозначения состояния (200, 404, 500 и т.д.);
+ Использование URL для идентификации ресурсов;
+ Поддержка различных форматов (JSON, XML).

![trivialArchDisREST.png](attach%2FtrivialArchDisREST.png)

_Рисунок - 3. Тривиальный архитектурный дизайн REST API._