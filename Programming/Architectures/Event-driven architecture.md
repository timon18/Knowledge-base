14-03-2023
22:13
Authors: Roman Barannik 
***
Tags: #stub #programming #architecture
***
# Event-driven архитектура

## Что это

Шаблон распределенной асинхронной архитектуры, используемый для создания масштабируемых приложений. EDA состоит из разделенных одноцелевых компонентов, которые асинхронно получают и обрабатывают события.

---

### Пример

Сайт электронной коммерции. Такая архитектура позволяет сайту реагировать на изменения в различных источниках во время пикового спроса без сбоев приложения или избыточного выделения ресурсов.

![[Pasted image 20230314221900.png]]

(1) — Продюсеры событий; (2) — Начальные события; (3) — Маршрутизаторы событий; (4) — События обработки; (5) — Потребители событий

---
### Компоненты

Управляемые событиями архитектуры включают пять ключевых компонентов: продюсеры (производитель) событий, начальные события и события обработки, маршрутизаторы событий и потребители событий. Продюсер публикует начальное событие в маршрутизаторе, который фильтрует и передает событие обработки потребителям. Сервисы продюсера и потребителя разделены, что позволяет масштабировать, обновлять и развертывать их независимо

---

### Продюсеры мероприятий

В этом примере производители событий представлены eCommerce сайтом, мобильным приложением и торговым терминалом. В принципе, все, что регистрирует факт и представляет факт как сообщение о событии, может быть продюсером.

---

### Событие

Первоначальное событие — это исходное событие, сгенерированное продюсером и полученное маршрутизатором, тогда как события обработки — это события, которые генерируются маршрутизатором событий и принимаются компонентами потребителя событий.
События могут содержать либо состояние (приобретенный товар, его цена и адрес доставки), либо события могут быть идентификаторами (уведомление о том, что заказ был отправлен).
Событие обычно состоит из двух частей: 1) заголовок события включает такую ​​информацию, как имя события, отметка времени и тип события; 2) тело события предоставляет подробную информацию об обнаруженном изменении состояния.

----

### Каналы

И начальные, и события обработки доставляются по каналам событий.
Первоначальные каналы событий могут быть TCP/IP-соединением или файлом (XML, JSON, электронная почта и т.д). Одновременно можно открыть несколько исходных каналов событий. Они читаются асинхронно, что позволяет обрабатывать события почти в реальном времени. События хранятся в очереди, ожидая последующей обработки маршрутизатором событий.
Каналы обработки событий обычно представлены очередями сообщений и брокерами сообщений. Брокеры сообщений наиболее широко используются, так что события могут обрабатываться несколькими потребителями событий (каждый из которых выполняет свою задачу в зависимости от полученного события обработки).

---

### Маршрутизатор событий

Маршрутизатор событий отвечает за идентификацию начального события, а затем за выбор и выполнение шагов, содержащихся в событии. Для каждого шага в начальном событии маршрутизатор событий асинхронно отправляет событие обработки в канал событий, которое затем принимается и обрабатывается потребителем событий.
Маршрутизатор событий также может запускать ряд утверждений. Например, если событие, которое поступает в механизм обработки событий, является идентификатором продукта, запас которого на складе ограничен, это может вызвать такие реакции, как «Заказать продукт» и «Уведомить персонал».
Важно отметить, что маршрутизатор событий не выполняет бизнес-логику, необходимую для обработки исходного события — он распределяет соответствующие инструкции (= события обработки) среди потребителей событий.

---

### Потребители событий

В этом примере потребители событий представлены управленческой базой данных, финансовой системой и отделом по работе с клиентами.
Эти компоненты содержат бизнес-логику приложения, необходимую для обработки события обработки. Потребители событий — это автономные, независимые, сильно разделенные компоненты архитектуры, которые выполняют определенную задачу в приложении или системе. Хотя степень детализации потребителей событий может варьироваться от точечной (например, расчет налога с продаж по заказу) до крупной (например, обработка страхового возмещения), важно помнить, что в целом каждый потребитель события должен выполнять одну бизнес-задачу и не полагаться на других потребителей в выполнении своей конкретной задачи.

---

## Анализ шаблона

### Масштабируемость: высокая

Каждый потребитель событий может масштабироваться отдельно, что обеспечивает точную масштабируемость.

---

### Сложность разработки: высокая

Сложно из-за асинхронного характера шаблона, а также из-за создания контракта и необходимости более сложных условий обработки ошибок в коде для не отвечающих обработчиков событий и отказавших брокеров.

---

### Производительность: высокая

Высокая производительность за счет асинхронных возможностей: возможность выполнять разделенные, параллельные асинхронные операции перевешивают затраты на постановку в очередь и удаление сообщений из очереди.

---

### Тестируемость: низкая

Хотя индивидуальное юнит-тестирование не слишком сложно, для генерации событий требуется какой-то специализированный клиент или инструмент тестирования. Тестирование также осложняется асинхронным характером этого шаблона.

---

### Модифицируемость: высокая

Поскольку компоненты-потребители событий являются одноцелевыми и полностью отделены от других компонентов-потребителей событий, изменения, как правило, ограничиваются одним или несколькими потребителями событий и могут быть выполнены быстро, не затрагивая другие компоненты.

## Выводы

1.  Событийная архитектура использует события для запуска и обмена данными между разделенными службами и является обычным явлением в современных приложениях, созданных с использованием микросервисов.
2.  Событийная архитектура имеет следующие ключевые компоненты: генераторы событий, каналы событий, начальные события и события обработки, маршрутизаторы событий и потребители событий.
3.  Событийная архитектура хорошо масштабируется, легко модифицируется и обладает высокой производительностью благодаря своей асинхронной природе, но шаблон имеет высокую сложность разработки и его непросто тестировать.
4.  Варианты использования событийной архитектуры включают репликацию данных между учетными записями и между регионами; разветвление и параллельная обработка; мониторинг состояния ресурсов и оповещение; интеграция разнородных систем.

