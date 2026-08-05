---
date: '2026-08-05'
description: Узнайте, как обнаружить версию PDF в Java и обновить PDF metadata с помощью
  GroupDocs.Metadata для Java. Включает обнаружение версии, чтение свойств и редактирование
  metadata.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Обнаружьте версию PDF в Java и обновите PDF metadata с помощью GroupDocs.Metadata.
  Пошаговое руководство по Java показывает обнаружение версии, чтение свойств и редактирование
  metadata.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: Обнаружить версию PDF в Java и обновить PDF metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: Обнаружить версию PDF в Java и обновить PDF metadata
type: docs
url: /ru/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Обнаружение версии PDF java и обновление метаданных PDF

Managing PDF files programmatically often means you need to **detect PDF version java** and **update PDF metadata** — author, title, creation date, or even the PDF version itself. Inconsistent metadata can cause rendering glitches or make it harder to locate documents in a large repository. This tutorial walks you through detecting the PDF version and updating PDF metadata using **GroupDocs.Metadata** for Java, giving you a reliable way to keep your PDFs tidy, searchable, and compatible with any viewer.

## Быстрые ответы
- **What does “update PDF metadata” mean?** Adding, modifying, or removing information stored inside a PDF file. → Добавление, изменение или удаление информации, хранящейся внутри PDF‑файла.  
- **Which library helps with this in Java?** GroupDocs.Metadata. → GroupDocs.Metadata.  
- **Can I also detect the PDF version?** Yes, the same API provides version detection. → Да, тот же API предоставляет определение версии.  
- **Do I need a license?** A free trial works for evaluation; a paid license is required for production. → Бесплатная пробная версия подходит для оценки; платная лицензия требуется для продакшн.  
- **What Java version is required?** JDK 8 or newer. → JDK 8 или новее.

## Что такое обновление метаданных PDF?

Updating PDF metadata means programmatically reading and writing the descriptive information embedded in a PDF file—such as author, title, subject, and custom properties. Proper metadata improves searchability, compliance, and version control in document management systems. Accurate metadata also enables automated indexing, compliance reporting, and version tracking across document management systems. → Обновление метаданных PDF означает программное чтение и запись описательной информации, встроенной в PDF‑файл — такой как автор, название, тема и пользовательские свойства. Корректные метаданные повышают возможность поиска, соответствие требованиям и контроль версий в системах управления документами. Точные метаданные также позволяют автоматическое индексирование, отчётность по соответствию и отслеживание версий в системах управления документами.

## Почему важно определять версию PDF в Java?

Detecting the PDF version lets you verify that a file will render correctly on the target viewer and that it meets downstream processing requirements. Knowing whether a PDF is version 1.4, 1.7, or newer helps you enforce compatibility rules before archiving, publishing, or converting the document. → Определение версии PDF позволяет убедиться, что файл будет корректно отображаться в целевом просмотрщике и соответствует требованиям последующей обработки. Знание того, является ли PDF версией 1.4, 1.7 или более новой, помогает применять правила совместимости перед архивированием, публикацией или конвертацией документа.

## Предварительные требования

- **Java Development Kit (JDK)** 8 или новее.  
- **Maven** для управления зависимостями (или можно скачать JAR напрямую).  
- Базовое знакомство с вводом‑выводом файлов в Java.  

## Настройка GroupDocs.Metadata для Java

### Настройка Maven

Add the repository and dependency to your `pom.xml`: → Добавьте репозиторий и зависимость в ваш `pom.xml`:

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

### Прямое скачивание

Alternatively, download the latest JAR from the official release page: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Шаги получения лицензии
- **Free trial** – start experimenting without cost. → **Free trial** – начните экспериментировать бесплатно.  
- **Temporary license** – extend the trial if needed. → **Temporary license** – продлите пробный период при необходимости.  
- **Purchase** – obtain a full‑feature license for production use. → **Purchase** – получите полную лицензию для использования в продакшн.

## Базовая инициализация и настройка

The `Metadata` class is the entry point for working with PDF files in GroupDocs.Metadata. It represents a container that gives you read/write access to document properties, version information, and custom XMP data. → Класс `Metadata` является точкой входа для работы с PDF‑файлами в GroupDocs.Metadata. Он представляет контейнер, предоставляющий доступ к чтению/записи свойств документа, информации о версии и пользовательским данным XMP.

Create a `Metadata` instance that points to your PDF file: → Создайте экземпляр `Metadata`, указывающий на ваш PDF‑файл:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Now you’re ready to read properties, detect the version, and update metadata. → Теперь вы готовы читать свойства, определять версию и обновлять метаданные.

## Как определить версию PDF java

Load your PDF with `new Metadata("sample.pdf")` and call `getRootPackage().getVersion()` — the method returns the exact PDF version (e.g., 1.4, 1.7) in a single call. This direct answer lets you quickly validate compatibility before any further processing. The version string reflects the PDF specification level the file adheres to, which is crucial for compatibility checks.  
`getVersion()` returns the PDF version as a string, e.g., "1.4" or "1.7". → Загрузите ваш PDF с помощью `new Metadata("sample.pdf")` и вызовите `getRootPackage().getVersion()` — метод возвращает точную версию PDF (например, 1.4, 1.7) одним вызовом. Этот прямой ответ позволяет быстро проверить совместимость перед любой дальнейшей обработкой. Строка версии отражает уровень спецификации PDF, которому соответствует файл, что критично для проверок совместимости.  
`getVersion()` возвращает версию PDF в виде строки, например, "1.4" или "1.7".

### Пошаговое руководство

1. **Open the PDF** – instantiate the `Metadata` object (see initialization above). → 1. **Open the PDF** – создайте объект `Metadata` (см. инициализацию выше).  
2. **Access the PDF‑specific root package** – call `metadata.getRootPackage()`. → 2. **Access the PDF‑specific root package** – вызовите `metadata.getRootPackage()`.  
3. **Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned string contains the version number. → 3. **Retrieve the version** – вызовите `pdfRoot.getVersion()`; возвращаемая строка содержит номер версии.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Pro tip:** Use the `version` value to enforce compatibility checks before processing a batch of PDFs. → **Pro tip:** Используйте значение `version` для применения проверок совместимости перед обработкой пакета PDF‑файлов.

#### Устранение неполадок
- Verify the file path; an incorrect path throws `FileNotFoundException`. → - Проверьте путь к файлу; неверный путь вызывает `FileNotFoundException`.  
- Ensure the GroupDocs.Metadata version matches your JDK (the example uses 24.12). → - Убедитесь, что версия GroupDocs.Metadata соответствует вашей JDK (в примере используется 24.12).

## Как читать свойства PDF в Java

`DocumentInfo` provides access to standard PDF metadata fields without loading the full document. The `DocumentInfo` class provides access to standard PDF properties such as author, title, and creation date. It is a lightweight wrapper that reads metadata without loading the entire document into memory. → `DocumentInfo` предоставляет доступ к стандартным полям метаданных PDF без загрузки полного документа. Класс `DocumentInfo` дает доступ к стандартным свойствам PDF, таким как автор, название и дата создания. Это лёгкая обёртка, читающая метаданные без загрузки всего документа в память.

Create a `DocumentInfo` instance from the opened `Metadata` object: → Создайте экземпляр `DocumentInfo` из открытого объекта `Metadata`:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

You can then call getters like `getAuthor()`, `getTitle()`, and `getCreationDate()` to retrieve values. → Затем вы можете вызвать геттеры, такие как `getAuthor()`, `getTitle()` и `getCreationDate()`, чтобы получить значения.

## Как обновить метаданные PDF в Java

Load the PDF (same as above), obtain the `DocumentInfo` package, modify the desired fields, and save the changes. The operation overwrites the existing metadata block while preserving the rest of the document. After modifying the fields, calling `save()` writes the changes back to the file while preserving content streams. → Загрузите PDF (как выше), получите пакет `DocumentInfo`, измените нужные поля и сохраните изменения. Операция перезаписывает существующий блок метаданных, сохраняя остальную часть документа. После изменения полей вызов `save()` записывает изменения обратно в файл, сохраняя потоки содержимого.

The `DocumentInfo` class is GroupDocs.Metadata’s object for editing PDF‑level properties such as author, title, subject, and custom XMP fields. → Класс `DocumentInfo` в GroupDocs.Metadata используется для редактирования свойств PDF‑уровня, таких как автор, название, тема и пользовательские поля XMP.

Update the metadata fields: → Обновите поля метаданных:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Note:** The setter calls follow the same pattern as the getters shown earlier, making the API intuitive and consistent. → **Note:** Вызовы сеттеров следуют той же схеме, что и геттеры, показанные ранее, делая API интуитивным и последовательным.

#### Распространённые подводные камни
- Attempting to modify metadata on a PDF that lacks the target property returns `null`—always check for `null` before setting a new value. → - Попытка изменить метаданные в PDF, у которого отсутствует целевое свойство, возвращает `null` — всегда проверяйте `null` перед установкой нового значения.  
- Large PDFs may require increased JVM heap; monitor memory usage during batch updates. → - Большие PDF‑файлы могут требовать увеличения кучи JVM; контролируйте использование памяти при пакетных обновлениях.

## Практические сценарии применения

1. **Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7) before legal filing. → 1. **Compliance audits** – Убедитесь, что все PDF соответствуют минимальной версии (например, 1.7) перед юридической подачей.  
2. **Automated archiving** – Tag PDFs with author, department, and creation date for easier retrieval. → 2. **Automated archiving** – Помечайте PDF авторами, отделом и датой создания для упрощённого поиска.  
3. **Document management integration** – Enrich PDFs with custom properties that DMS platforms can index. → 3. **Document management integration** – Обогащайте PDF пользовательскими свойствами, которые могут индексировать платформы DMS.  
4. **Report generation** – Insert version information into automatically generated reports. → 4. **Report generation** – Вставляйте информацию о версии в автоматически генерируемые отчёты.  
5. **Cross‑platform testing** – Detect version mismatches that could cause rendering issues on older viewers. → 5. **Cross‑platform testing** – Обнаруживайте несоответствия версий, которые могут вызвать проблемы отображения в старых просмотрщиках.

## Советы по производительности

- **Use try‑with‑resources** (as shown) to automatically close `Metadata` objects. → - **Use try‑with‑resources** (as shown) для автоматического закрытия объектов `Metadata`.  
- **Batch process** multiple files in a loop to reduce overhead. → - **Batch process** несколько файлов в цикле для снижения накладных расходов.  
- **Monitor heap** for very large PDFs; consider processing them in chunks if you hit memory limits. → - **Monitor heap** для очень больших PDF; рассмотрите обработку их частями при достижении предела памяти.  
- **GroupDocs.Metadata supports 50+ input and output formats** and can read metadata from multi‑hundred‑page PDFs without loading the entire file into memory, delivering fast performance on standard server hardware. → - **GroupDocs.Metadata supports 50+ input and output formats** и может читать метаданные из PDF‑файлов со сотнями страниц без загрузки всего файла в память, обеспечивая быструю работу на стандартном серверном оборудовании.

## Часто задаваемые вопросы

**Q: Можно ли обновлять метаданные в PDF, защищённых паролем?**  
A: Да, но необходимо предоставить пароль при создании объекта `Metadata`.

**Q: Поддерживает ли GroupDocs.Metadata пользовательские свойства XMP?**  
A: Абсолютно. Вы можете читать и записывать пользовательские поля XMP через тот же API.

**Q: Можно ли изменить саму версию PDF?**  
A: Библиотека может сообщать версию; изменение требует сохранения документа с другим профилем версии, что поддерживается через дополнительные параметры сохранения.

**Q: Что происходит, если у PDF нет существующих метаданных?**  
A: Геттеры вернут `null`. Вы можете безопасно вызвать сеттеры для создания новых записей метаданных.

**Q: Существуют ли ограничения лицензирования для коммерческого использования?**  
A: Для продакшн‑развёртываний требуется коммерческая лицензия; пробная версия ограничена только оценкой.

---

**Последнее обновление:** 2026-08-05  
**Тестировано с:** GroupDocs.Metadata 24.12 for Java  
**Автор:** GroupDocs

## Связанные руководства

- [Efficiently Update PDF Metadata with GroupDocs.Metadata in Java for Document Management](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Master Metadata Management: Detect Document Properties & Encryption Status with GroupDocs.Metadata for Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Create Document Preview Java – GroupDocs.Metadata Tutorials](/metadata/java/document-formats/)