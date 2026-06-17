---
date: '2026-05-27'
description: Узнайте, как установить CreatedTime в PPTX на Java с помощью зависимости
  GroupDocs Maven для обновления метаданных PowerPoint, включая изменение даты создания
  PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Установить CreatedTime в PPTX на Java с зависимостью GroupDocs Maven
type: docs
url: /ru/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Установить CreatedTime PPTX в Java с помощью GroupDocs.Metadata

Точные метаданные имеют решающее значение для соответствия требованиям и возможности поиска в современных рабочих процессах с документами. С помощью **GroupDocs.Metadata** вы можете программно **установить CreatedTime PPTX в Java**, позволяя **изменять дату создания PPTX** вместе с другими встроенными свойствами, такими как автор или компания. Этот учебник проведёт вас через настройку Maven, инициализацию API, обновление метаданных и сохранение изменённой презентации — всё с понятным, готовым к использованию в продакшене кодом.

## Быстрые ответы
- **Какой библиотекой обновляются метаданные PowerPoint в Java?** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **Могу ли я установить свойство PPTX CreatedTime?** Да — используйте `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Требуется ли лицензия для продакшена?** Пробная версия подходит для оценки; коммерческая лицензия обязательна для развертывания в продакшене.  
- **Какой инструмент сборки используется в примере?** Maven (вы также можете скачать JAR вручную).  
- **Поддерживает ли API Java 8 и новее?** Абсолютно — GroupDocs.Metadata targets Java 8+.

## Что такое зависимость GroupDocs Maven?

**GroupDocs Maven dependency** — это запись репозитория, совместимая с Maven, которая подтягивает последнюю библиотеку GroupDocs.Metadata в ваш Java‑проект. Она упрощает управление зависимостями, автоматически разрешая транзитивные библиотеки, гарантирует, что вы всегда используете самую новую и безопасную версию, и устраняет необходимость ручной загрузки JAR‑файлов или отслеживания версий.

## Почему использовать GroupDocs.Metadata для изменения даты создания PPTX?

GroupDocs.Metadata позволяет выполнять автоматические, готовые к пакетной обработке обновления меток времени создания PPTX, обеспечивая соответствие каждой презентации корпоративным политикам или юридическим требованиям. Программно устанавливая свойство CreatedTime, вы избегаете ручного редактирования, снижаете риск человеческих ошибок и можете интегрировать изменение в конвейеры CI/CD или скрипты миграции для бесшовного управления документами.

## Предварительные требования
- Java 8 или выше установлен.  
- IDE, например IntelliJ IDEA или Eclipse.  
- Maven для управления зависимостями.  
- Доступ к пробной версии GroupDocs или приобретённой лицензии.

## Как установить PPTX CreatedTime в Java?

Класс `Metadata` представляет документ и предоставляет доступ к его свойствам метаданных.

Загрузите ваш PowerPoint файл с помощью `new Metadata("presentation.pptx")`, получите корневой пакет, вызовите `setCreatedTime` с желаемым объектом `java.util.Date` и, наконец, вызовите `save` для записи изменений. Этот сквозной процесс изменяет дату создания, сохраняя всё содержимое слайдов и другие свойства.

### Настройка Maven
Add the GroupDocs repository and the metadata dependency to your `pom.xml`:

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

> **Совет:** Своевременное обновление номера версии гарантирует, что вы получаете последние исправления ошибок и улучшения производительности.

### Прямое скачивание (если вы предпочитаете не использовать Maven)

В качестве альтернативы скачайте последнюю JAR‑файл с [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Приобретение лицензии

Начните с бесплатной пробной версии или запросите временную лицензию для оценки GroupDocs.Metadata. Для использования в продакшене приобретите лицензию через [официальный сайт GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Базовая инициализация и настройка

После того как библиотека добавлена в classpath, вы можете создать экземпляр `Metadata`, указывающий на ваш PowerPoint файл:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Этот код открывает презентацию в блоке try‑with‑resources, гарантируя автоматическое освобождение дескриптора файла.

## Пошаговое руководство по обновлению встроенных метаданных

### Шаг 1: Загрузить документ презентации

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Загрузка файла устанавливает соединение, позволяющее читать или записывать метаданные.

### Шаг 2: Доступ к корневому пакету презентации

Объект `root` предоставляет доступ к корневому пакету презентации и её встроенным свойствам.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Объект `root` предоставляет доступ ко всем встроенным свойствам документа.

### Шаг 3: Обновить встроенные свойства документа (включая дату создания)

`setCreatedTime` присваивает документу новый временной штамп создания.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Здесь мы демонстрируем, как **установить PPTX CreatedTime**, присваивая новое объект `Date` свойству `CreatedTime`. Замените `new Date()` на любой нужный вам конкретный временной штамп.

### Шаг 4: Сохранить обновлённую презентацию

`save` записывает изменённые метаданные в файл.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Вызов `save` записывает изменённые метаданные в новый PowerPoint файл, оставляя оригинал нетронутым.

## Советы по устранению неполадок
- **Файл не найден:** Проверьте путь к входному файлу и права доступа.  
- **Несоответствие версии:** Убедитесь, что версия `groupdocs-metadata` соответствует вашей среде Java.  
- **Свойство не обновляется:** Убедитесь, что вы вызываете `setCreatedTime` (или соответствующий сеттер) перед вызовом `save`.

## Практические применения

1. **Корпоративный брендинг:** Автоматически вставлять правильное название компании и категорию во все наборы слайдов перед распространением.  
2. **Системы управления документами:** Обогащать файлы PPTX поисковыми метаданными для более быстрого поиска.  
3. **Образовательные ресурсы:** Поддерживать актуальность информации об авторе и учебной программе во всех слайдах лекций.  
4. **Отслеживание сотрудничества:** Записывать имена участников для обеспечения ответственности.  
5. **Интеграция с CMS:** Синхронизировать изменения метаданных с вашей платформой управления контентом в реальном времени.

## Соображения по производительности
- **Пакетная обработка:** Проходить по списку файлов и по возможности переиспользовать один экземпляр `Metadata`.  
- **Управление памятью:** Всегда используйте try‑with‑resources (как показано), чтобы своевременно освобождать нативные ресурсы.  
- **Эффективные структуры данных:** Сохраняйте обновления метаданных в карте перед их применением, чтобы уменьшить количество повторных вызовов.

## Часто задаваемые вопросы

**В: Какова основная цель зависимости GroupDocs Maven?**  
A: Она предоставляет удобный способ включить последнюю библиотеку GroupDocs.Metadata в Maven‑проекты на Java.

**В: Как установить дату создания PPTX, не затрагивая другие свойства?**  
A: Используйте `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` перед вызовом `metadata.save()`.

**В: Нужна ли лицензия для запуска этого кода в разработке?**  
A: Временная пробная лицензия достаточна для разработки и тестирования; полная лицензия требуется для продакшена.

**В: Могу ли я также обновлять пользовательские поля метаданных?**  
A: Да — GroupDocs.Metadata поддерживает как встроенные, так и пользовательские свойства через свой API.

**В: Есть ли способ откатить изменения, если я ошибся?**  
A: Сохраните копию оригинального файла или прочитайте существующие значения свойств перед их перезаписью, затем при необходимости восстановите их.

## Ресурсы

- [Документация](https://docs.groupdocs.com/metadata/java/)
- [Справочник API](https://apireference.groupdocs.com/metadata/java/)

---

**Последнее обновление:** 2026-05-27  
**Тестировано с:** GroupDocs.Metadata 24.12 for Java  
**Автор:** GroupDocs  

## Связанные учебники

- [Обновить пользовательские метаданные в PowerPoint с помощью GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Как обновить метаданные Word‑документа с помощью GroupDocs.Metadata Java: Полное руководство](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Эффективно обновить PDF‑метаданные с помощью GroupDocs.Metadata в Java для управления документами](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)