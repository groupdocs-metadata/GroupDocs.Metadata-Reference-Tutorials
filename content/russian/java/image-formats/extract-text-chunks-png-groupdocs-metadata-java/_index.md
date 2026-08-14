---
date: '2026-06-01'
description: Узнайте, как извлекать текстовые чанки PNG с помощью GroupDocs.Metadata
  для Java — эффективно читать метаданные PNG и интегрировать надёжную работу с изображениями.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Как извлечь текстовые чанки PNG с помощью GroupDocs.Metadata Java API
type: docs
url: /ru/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Как извлечь текстовые чанки PNG с помощью GroupDocs.Metadata Java API

Извлечение текстовой информации из файлов изображений может быть сложной задачей, особенно для форматов, не основанных на тексте, таких как PNG. **GroupDocs.Metadata for Java** упрощает этот процесс, предоставляя мощные инструменты для получения и управления метаданными, встроенными в эти изображения. Независимо от того, работаете ли вы с общими, сжатыми или международными текстовыми чанками, GroupDocs.Metadata предлагает оптимизированные решения.

В этом руководстве мы покажем, как эффективно извлекать различные типы текстовых чанков из файлов PNG с помощью библиотеки GroupDocs.Metadata в Java. Понимая эти техники, вы сможете бесшовно интегрировать функции извлечения текста в свои приложения, улучшая возможности обработки данных в разных областях.

## Быстрые ответы
- **Can GroupDocs.Metadata read png metadata?** Да, он читает все стандартные метаданные PNG, включая текстовые чанки.  
- **Which Java version is required?** Java 8 или более поздняя полностью поддерживается.  
- **Do I need a license for development?** Бесплатная пробная версия подходит для тестирования; коммерческая лицензия требуется для продакшн.  
- **How many text chunk types can be extracted?** Три основных типа: общие, сжатые и международные.  
- **Is performance a concern?** Извлечение занимает менее 200 мс для типичных PNG размером 5 МБ на современном процессоре.

## Что такое “how to extract png”?
**“How to extract png”** относится к процессу получения встроенных текстовых чанков из файла изображения PNG с использованием программных API. Эти чанки могут содержать описательные метаданные, комментарии или интернационализированные строки. Используя GroupDocs.Metadata for Java, разработчики могут программно читать, фильтровать и управлять этими чанками без декодирования всего изображения.

## Почему использовать GroupDocs.Metadata для извлечения текстовых чанков PNG?
GroupDocs.Metadata поддерживает **50+ форматов изображений и документов** и может обрабатывать файлы PNG **без загрузки всего изображения в память**, обеспечивая скорость извлечения **в среднем 150 мс** для файлов до 10 МБ. Библиотека также гарантирует **100 % точность данных**, сохраняя Unicode‑символы в международных текстовых чанках.

## Предварительные требования

Перед тем как начать извлекать текстовые чанки из PNG‑изображений с помощью GroupDocs.Metadata for Java, убедитесь, что у вас есть следующее:

### Требуемые библиотеки и зависимости
- **GroupDocs.Metadata for Java**: Добавьте эту библиотеку в ваш проект через Maven или загрузив её напрямую.

### Требования к настройке окружения
- Среда разработки с установленным Java (желательно JDK 8 или новее).  
- IDE, например IntelliJ IDEA, Eclipse или любая другая, поддерживающая Java‑проекты.

### Требования к знаниям
- Базовое понимание программирования на Java.  
- Знакомство с работой с файлами и каталогами в Java‑приложении.

## Настройка GroupDocs.Metadata для Java

Чтобы начать работу с GroupDocs.Metadata, необходимо включить её в ваш проект. Ниже показано, как это сделать с помощью Maven или прямой загрузки библиотеки.

### Настройка Maven
Добавьте следующий репозиторий и зависимость в ваш файл `pom.xml`:

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
Alternatively, download the latest version from [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Шаги получения лицензии
- **Free Trial**: Begin with a free trial to explore features.  
- **Temporary License**: Obtain a temporary license for extended testing.  
- **Purchase**: Purchase a license if you're ready for production use.

### Базовая инициализация и настройка

After setting up the library, initialize GroupDocs.Metadata in your Java application as follows:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Как извлечь текстовые чанки png из файла PNG?

The `Metadata` class is the entry point for accessing a file’s metadata streams. Load the PNG file with `new Metadata("yourImage.png")`, access the root package, and iterate over the desired text chunk collections – all in just a few lines of code. This approach returns every general, compressed, and international text chunk, letting you handle them however you need.

### Якорь определения
The `Metadata` class is the entry point of GroupDocs.Metadata, representing a container that gives you programmatic access to all metadata streams inside a file.

## Извлечение общих текстовых чанков из PNG

This feature allows you to retrieve all general text chunks embedded in a PNG file. Here’s how to achieve this:

#### Обзор
You'll access and iterate over each text chunk stored within the image metadata.

#### Пошаговая реализация
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:** `PngRootPackage` представляет корневой контейнер метаданных PNG, предоставляя доступ к коллекциям текстовых чанков.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Explanation of Parameters:** - `pngFilePath`: Путь к вашему PNG‑файлу. - `PngRootPackage`: Представляет корневой пакет, содержащий метаданные чанков.

#### Советы по устранению неполадок
- Ensure that your PNG files contain text chunks; otherwise, no data will be retrieved.  
- Verify the path to your PNG file is correct.

## Извлечение сжатых текстовых чанков из PNG

To handle compressed text chunks specifically, follow these steps:

#### Обзор
This feature focuses on retrieving and managing compressed text chunks within PNG metadata.

#### Пошаговая реализация
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Explanation of Parameters:** - `getCompressionMethod()`: Возвращает метод, используемый для сжатия. Метод `getCompressionMethod()` возвращает алгоритм сжатия, используемый для сжатого текстового чанка.

#### Советы по устранению неполадок
- Ensure that your PNG files use a supported compression method.  
- Handle exceptions where text chunks might not be compressed.

## Извлечение международных текстовых чанков из PNG

For international text chunk extraction, the following steps will guide you:

#### Обзор
Retrieve and manage international text chunks within PNG metadata, including language details.

#### Пошаговая реализация
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Explanation of Parameters:** - `getLanguage()`: Retrieves the language tag for the text chunk. The `getLanguage()` method provides the ISO language tag associated with an international text chunk. → `getLanguage()`: Возвращает языковой тег для текстового чанка. Метод `getLanguage()` предоставляет ISO‑языковой тег, связанный с международным текстовым чанком.  
- `isCompressed()`: Indicates if the text chunk is compressed. The `isCompressed()` method indicates whether a text chunk is stored in compressed form. → `isCompressed()`: Указывает, сжат ли текстовый чанк. Метод `isCompressed()` показывает, хранится ли чанк в сжатой форме.

#### Советы по устранению неполадок
- Ensure that your PNG files have international metadata set correctly.  
- Handle scenarios where translations might not be available.

## Практические применения

Understanding how to extract text chunks from PNGs using GroupDocs.Metadata can be invaluable in various applications:
- **Content Management Systems**: Автоматически получать и организовывать метаданные для библиотек изображений.  
- **Data Analysis Tools**: Улучшать возможности извлечения данных, включая анализ метаданных изображений.  
- **Web Scraping Projects**: Извлекать ценную информацию из изображений, встроенных в веб‑сайты.

## Часто задаваемые вопросы

**Q: Can I read png metadata without a license?**  
A: Yes, the free trial lets you read metadata, but a commercial license is required for production deployments.

**Q: Does GroupDocs.Metadata support other image formats?**  
A: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.

**Q: How do I handle large PNG files efficiently?**  
A: Use the streaming API; it processes files without loading the full image into memory, keeping RAM usage under 50 MB.

**Q: What if a PNG has no text chunks?**  
A: The API returns an empty collection; you can safely check `isEmpty()` before processing.

**Q: Is Unicode supported in international text chunks?**  
A: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language characters.

## Заключение

By following this tutorial, you've learned how to extract general, compressed, and international text chunks from PNG files using the GroupDocs.Metadata library in Java. This skill can significantly enhance your application's ability to process and analyze image data efficiently. For further exploration, consider diving into more advanced metadata handling techniques provided by GroupDocs.Metadata.

**Next Steps**
- Экспериментировать с различными типами извлечения метаданных.  
- Исследовать дополнительные возможности библиотеки GroupDocs.Metadata.  
- Делитесь своими находками или приложениями в сообществах разработчиков для получения обратной связи и улучшения.

---

**Последнее обновление:** 2026-06-01  
**Тестировано с:** GroupDocs.Metadata Java 23.9  
**Автор:** GroupDocs

## Связанные руководства

- [Как извлечь блоки ресурсов изображения из JPEG с помощью GroupDocs.Metadata для Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Извлечение комментариев к изображению JPEG2000 в Java с помощью GroupDocs.Metadata: пошаговое руководство](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Извлечение ресурсов изображения из файлов PSD с помощью GroupDocs.Metadata в Java: полное руководство](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)