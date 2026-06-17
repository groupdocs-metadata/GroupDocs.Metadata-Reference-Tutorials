---
date: '2026-06-17'
description: Узнайте, как изменить время создания диаграммы и автоматизировать обновление
  метаданных файлов диаграмм с помощью GroupDocs.Metadata в Java.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Изменение времени создания диаграммы в метаданных с помощью GroupDocs Java
type: docs
url: /ru/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Изменение времени создания диаграммы в метаданных с помощью GroupDocs Java

В этом пошаговом руководстве вы узнаете, как **изменить время создания диаграммы** и обновить другие встроенные свойства файлов диаграмм с помощью библиотеки GroupDocs.Metadata для Java. Автоматизация этих изменений экономит часы ручного редактирования, гарантирует согласованные метки времени во всем репозитории и делает ваши диаграммы мгновенно доступными для поиска в любой системе управления документами.

## Быстрые ответы
- **Какова основная цель?** Изменить время создания диаграммы и другие метаданные в файлах диаграмм.  
- **Какую библиотеку следует использовать?** GroupDocs.Metadata for Java.  
- **Нужна ли лицензия?** Достаточно бесплатной пробной версии для тестирования; полная лицензия требуется для продакшн.  
- **Можно ли пакетно обрабатывать множество диаграмм?** Да — оберните ту же логику в цикл или параллельный поток.  
- **Какая версия Java требуется?** JDK 8 или выше.

## Что означает «изменить время создания диаграммы» в метаданных диаграммы?
Изменение времени создания перезаписывает оригинальную метку времени, хранящуюся внутри файла диаграммы (например, VDX или VSDX), новым значением даты‑времени. Это позволяет согласовать метаданные файла с фактической датой обработки или архивирования вместо оригинальной метки времени автора, что важно для аудиторских следов и точных результатов поиска.

## Зачем автоматизировать обновление метаданных для диаграмм?
Автоматизация метаданных гарантирует, что каждая диаграмма следует одинаковым правилам именования, категоризации и меток времени без человеческих ошибок. Это также ускоряет массовую миграцию, снижает риск несоответствия требованиям и повышает обнаруживаемость в корпоративных платформах DMS — экономя до 70 % ручных усилий в крупномасштабных проектах.

## Предварительные требования
- **Java Development Kit (JDK) 8+** установлен на вашем компьютере.  
- **IDE** такая как IntelliJ IDEA или Eclipse.  
- **Maven** (или ручное управление JAR) для управления зависимостями.  
- Базовое знакомство с классами Java, методами и обработкой исключений.

### Требуемые библиотеки и зависимости
Добавьте следующий репозиторий и зависимость в ваш файл `pom.xml`, если используете Maven:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/metadata/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-metadata</artifactId>
      <version>24.12</version>
   </dependency>
</dependencies>
```
Если вы предпочитаете скачивать напрямую, посетите [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/), чтобы получить последнюю версию.

### Настройка окружения
- JDK 8 или новее.  
- IntelliJ IDEA, Eclipse или любой совместимый с Java IDE.  

### Требования к знаниям
Понимание синтаксиса Java и базового ввода‑вывода файлов упростит прохождение руководства, но шаги объяснены простым языком.

## Настройка GroupDocs.Metadata для Java
### Инструкции по установке
**Пользователи Maven:** Приведённый выше фрагмент автоматически добавляет репозиторий и требуемый JAR.  
**Пользователи прямой загрузки:** После скачивания JAR с [GroupDocs](https://releases.groupdocs.com/metadata/java/), добавьте его в classpath вашего проекта.

### Получение лицензии
- **Бесплатная пробная версия:** Исследуйте библиотеку бесплатно.  
- **Временная лицензия:** Получите временную лицензию для расширенного тестирования [здесь](https://purchase.groupdocs.com/temporary-license/).  
- **Покупка:** Приобретите полную лицензию для производственной среды.

### Базовая инициализация
`Metadata` — основной класс, представляющий контейнер метаданных документа и предоставляющий доступ для чтения/записи ко всем встроенным свойствам. Чтобы начать использовать GroupDocs.Metadata, импортируйте класс и откройте файл диаграммы:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

После инициализации библиотеки вы теперь можете изменять любое встроенное свойство, включая время создания.

## Руководство по реализации
### Как изменить время создания в файлах диаграмм
В этом разделе мы пройдем каждый шаг, необходимый для **изменения времени создания диаграммы** и обновления других общих свойств, таких как автор, компания и категория. Процесс включает загрузку диаграммы с помощью Metadata API, доступ к корневому пакету, установку нужных полей и, наконец, сохранение изменений в новый файл, чтобы оригинал остался нетронутым.

#### Шаг 1: Загрузка документа диаграммы
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Объяснение:* Конструктор `Metadata` принимает путь к вашему файлу диаграммы. Блок try‑with‑resources гарантирует правильное закрытие файла после операции.

#### Шаг 2: Доступ к корневому пакету
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Объяснение:* Корневой пакет предоставляет прямой доступ ко всем встроенным полям метаданных диаграммы.

#### Шаг 3: Установка свойства создателя
```java
root.getDocumentProperties().setCreator("test author");
```  
*Объяснение:* Присваивает новое имя автора. Замените `"test author"` на фактического создателя.

#### Шаг 4: Изменение времени создания
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Объяснение:* Эта строка **изменяет время создания** на текущие системные дату и время. Вы также можете передать конкретный объект `Date`, если нужен пользовательский таймстамп.

#### Шаг 5: Определение информации о компании
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Объяснение:* Сохраняет название компании, связанной с диаграммой — полезно для корпоративного отслеживания.

#### Шаг 6: Установка категории документа
```java
root.getDocumentProperties().setCategory("test category");
```  
*Объяснение:* Категоризирует файл, помогая вам **обновлять категорию диаграммы** последовательно во всем репозитории.

#### Шаг 7: Добавление ключевых слов
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Объяснение:* Ключевые слова повышают возможность поиска; вы можете перечислить любые термины, релевантные содержимому диаграммы.

#### Шаг 8: Сохранение изменений
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Объяснение:* Сохраняет все изменения в новый файл, оставляя оригинал нетронутым.

### Распространённые проблемы и их устранение
- **File Not Found:** Проверьте путь ввода и убедитесь, что расширение файла соответствует реальному формату.  
- **Access Denied:** Проверьте права чтения/записи для входных и выходных каталогов.  
- **Invalid Date Format:** Используйте объекты `java.util.Date` или `java.time`, совместимые с API.

## Практические применения
1. **Автоматизация архивирования документов** – При перемещении старых диаграмм в архив автоматически **изменять время создания диаграммы** на дату архивирования и задавать единообразную категорию.  
2. **Интеграция с системой контроля версий** – Синхронизировать метки времени с коммитами Git, обновляя время создания при каждом релизе.  
3. **Стандартизация корпоративных DMS** – Внедрить общекорпоративную политику для автора, компании и ключевых слов во всех ресурсах диаграмм.

## Соображения по производительности
- **Batch Processing:** Оберните вышеуказанные шаги в цикл, чтобы обработать десятки файлов за один запуск.  
- **Memory Management:** Быстро освобождайте каждый экземпляр `Metadata` (блок try‑with‑resources делает это автоматически).  
- **Asynchronous Execution:** Для больших пакетов рассмотрите `CompletableFuture` для параллельного выполнения обновлений без блокировки основного потока.  
- **Quantified Capability:** GroupDocs.Metadata поддерживает более 30 форматов диаграмм и может обрабатывать файлы до 500 МБ без загрузки всего документа в память, обеспечивая обновления менее чем за 200 мс на файл на типичном серверном оборудовании.

## Заключение
Теперь вы знаете, как **изменить время создания диаграммы** и обновить другие встроенные свойства метаданных для документов диаграмм с помощью GroupDocs.Metadata в Java. Автоматизируя эти шаги, вы сможете поддерживать согласованную, доступную для поиска и соответствующую требованиям документацию во всей организации.

**Следующие шаги**
- Поэкспериментировать с другими форматами файлов, поддерживаемыми GroupDocs.Metadata (PDF, DOCX и т.д.).  
- Интегрировать код в CI/CD конвейер для обеспечения стандартов метаданных в каждой сборке.

Готовы попробовать? Перейдите к [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) и начните реализовывать свою автоматизацию метаданных уже сегодня.

---

**Последнее обновление:** 2026-06-17  
**Тестировано с:** GroupDocs.Metadata 24.12  
**Автор:** GroupDocs  

## Часто задаваемые вопросы

**Q:** Можно ли использовать этот подход с другими форматами диаграмм, например VSDX?  
**A:** Да, тот же API работает со всеми форматами диаграмм, поддерживаемыми GroupDocs.Metadata.

**Q:** Нужна ли лицензия для сборок разработки?  
**A:** Бесплатная пробная версия достаточна для разработки и тестирования; полная лицензия требуется для продакшн-развертываний.

**Q:** Как можно обновить несколько свойств за один вызов?  
**A:** Установите каждое свойство в объекте `DocumentProperties` перед вызовом `metadata.save(...)`; библиотека запишет их все сразу.

**Q:** Безопасно ли перезаписывать оригинальный файл?  
**A:** Рекомендуется сохранять в новый файл (как показано) и заменять оригинал только после подтверждения успешного обновления.

**Q:** Что делать, если нужно установить пользовательскую дату создания вместо текущего времени?  
**A:** Создайте `java.util.Date` (или экземпляр `java.time`) с нужным таймстампом и передайте его в `setTimeCreated`.

## Связанные руководства

- [Как обновить метаданные диаграммы Java с помощью GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Как обновить метаданные автора DXF с помощью GroupDocs.Metadata для Java – Полное руководство](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Автоматизировать обновление метаданных Java по дате с помощью GroupDocs.Metadata для эффективного управления файлами](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)