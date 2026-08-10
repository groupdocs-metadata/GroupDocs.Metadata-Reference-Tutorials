---
date: '2026-08-10'
description: Узнайте, как извлекать EXIF‑метаданные из файлов PSD с помощью GroupDocs.Metadata
  для Java. Это руководство охватывает базовое извлечение, пакеты IFD, данные GPS
  и реальные примеры использования.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Узнайте, как извлекать EXIF‑метаданные из файлов PSD с помощью GroupDocs.Metadata
  для Java. Пошаговое руководство, примеры кода и советы по устранению неполадок для
  разработчиков.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Как извлечь EXIF‑метаданные из файлов PSD с помощью GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: Как извлечь EXIF‑метаданные из файлов PSD с помощью GroupDocs.Metadata
type: docs
url: /ru/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Как извлечь EXIF‑метаданные из файлов PSD с помощью GroupDocs.Metadata

Извлечение **EXIF‑метаданных** из файлов PSD — это обычный, но мощный шаг, когда необходимо проверять происхождение изображений, автоматизировать маркировку ресурсов или создавать поисковые медиа‑библиотеки. В этом руководстве вы быстро узнаете, **как извлекать EXIF** с помощью GroupDocs.Metadata для Java, увидите точные вызовы API и научитесь работать с расширенными пакетами IFD и GPS‑координатами. К концу вы будете готовы интегрировать извлечение метаданных в любой Java‑ориентированный рабочий процесс.

## Быстрые ответы

Класс `Metadata` представляет файл и предоставляет доступ к его метаданным.

- **Как выглядит первая строка кода?** `Metadata metadata = new Metadata("sample.psd");`
- **Какой метод возвращает имя автора?** `metadata.getExif().getArtist();`
- **Можно ли прочитать GPS‑данные?** Да — используйте `metadata.getExif().getGpsInfo();`
- **Нужна ли лицензия для продакшн?** Требуется действующая лицензия GroupDocs.Metadata после окончания пробного периода.
- **Поддерживаемая версия Java?** Java 8 или новее (до Java 21).

## Что такое EXIF‑метаданные?

Метаданные EXIF (Exchangeable Image File Format) хранят настройки камеры, временные метки создания и данные о местоположении внутри файлов изображений. GroupDocs.Metadata считывает эту информацию непосредственно из бинарной структуры файлов PSD, предоставляя её через чистый Java‑API. Это позволяет разработчикам программно получать такие детали, как модель камеры, время экспозиции и GPS‑координаты, без ручного осмотра.

## Почему стоит использовать GroupDocs.Metadata для Java?

GroupDocs.Metadata поддерживает **более 30 форматов файлов** (включая PSD, JPEG, PNG, TIFF) и может обрабатывать файлы размером до **2 ГБ**, не загружая весь документ в память. Библиотека извлекает **более 150 различных EXIF‑тегов**, гарантируя наличие полного набора атрибутов камеры и GPS, необходимых для аналитики или соответствия требованиям.

## Требования

- **Java Development Kit (JDK) 8** или новее, установленный на вашем компьютере.  
- **Maven** для управления зависимостями.  
- **GroupDocs.Metadata для Java версии 24.12** (или новее).  
- Базовое знакомство с классами Java, объектами и обработкой исключений.

### Требуемые библиотеки и зависимости

| Зависимость | Maven координаты |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Настройка окружения

У вас должна быть IDE, совместимая с Maven, например IntelliJ IDEA или Eclipse. Создайте новый Maven‑проект или добавьте зависимость в существующий.

## Как настроить GroupDocs.Metadata для Java

GroupDocs.Metadata можно добавить в Maven‑проект несколькими строками конфигурации. Ниже приведены шаги, показывающие, как включить репозиторий и зависимость, чтобы библиотека была доступна в classpath.

### Настройка Maven

Добавьте следующий фрагмент в ваш `pom.xml` внутри раздела `<dependencies>`:

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

В качестве альтернативы скачайте последнюю JAR‑файл со страницы официальных выпусков: [GroupDocs.Metadata для Java (выпуски)](https://releases.groupdocs.com/metadata/java/).

### Приобретение лицензии

Чтобы использовать библиотеку после 30‑дневного пробного периода, получите временную или полную лицензию:

1. Перейдите на страницу [Страницы покупки лицензии](https://purchase.groupdocs.com/temporary-license).  
2. Выберите **temporary** для тестирования или **full** для продакшна.  
3. Следуйте инструкциям на экране, чтобы встроить файл лицензии (`metadata.lic`) в ваш Java‑classpath.

### Базовая инициализация и настройка

После того как библиотека добавлена в classpath, инициализируйте её, как показано ниже:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Как извлечь базовые свойства EXIF‑метаданных из изображения PSD

В этом разделе объясняется, как загрузить файл PSD, получить доступ к контейнеру EXIF и прочитать наиболее распространённые теги, такие как **artist**, **copyright** и **software**. Процесс включает создание экземпляра `Metadata`, вызов `getExif()` и последующее получение отдельных свойств с помощью простых методов‑геттеров.

### Пошаговая реализация

1. **Создайте экземпляр `Metadata`**, указывающий на ваш файл PSD.  
2. **Вызовите `getExif()`**, чтобы получить контейнер EXIF.  
3. **Прочитайте отдельные свойства** такие как `getArtist()`, `getCopyright()` и `getSoftware()`.  
4. **Выведите или сохраните** значения в соответствии с логикой вашего приложения.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Совет:** Объект `Metadata` автоматически определяет формат файла, поэтому вы можете повторно использовать тот же код для файлов JPEG или TIFF без изменений.

## Как извлечь свойства пакета EXIF IFD из изображения PSD

Раздел IFD (Image File Directory) содержит более глубокие технические детали, такие как **camera serial number**, **lens model** и **user comments**. `Ifd0` представляет основной каталог файлов изображений, содержащий базовую информацию о камере. Извлечение этих полей полезно для судебного анализа или высокоточного каталогизирования.

### Шаги реализации

1. **Повторно используйте экземпляр `Metadata`** из предыдущего раздела.  
2. **Перейдите к контейнеру IFD** через `metadata.getExif().getIfd0()`.  
3. **Прочитайте свойства** такие как `getBodySerialNumber()` и `getUserComment()`.  
4. **Выведите данные** или сопоставьте их с вашей доменной моделью.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Как получить GPS‑данные (широта, долгота) из файла PSD

Во многих современных камерах GPS‑координаты встраиваются в блок EXIF. `GpsInfo` хранит географические координаты, извлечённые из EXIF‑данных. Вызовите `metadata.getExif().getGpsInfo()`, а затем используйте `getLatitude()`, `getLongitude()` и `getAltitude()`, чтобы получить точные данные о местоположении — дополнительный разбор не требуется.

### Подробные шаги

1. **Получите объект GPS‑информации**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Прочитайте широту и долготу**: `gps.getLatitude()` возвращает `double` в десятичных градусах.  
3. **Обработайте отсутствие данных**: API возвращает `null`, если тег отсутствует, поэтому необходимо проверять на `NullPointerException`.  

> **Распространённая ошибка:** Некоторые файлы PSD хранят GPS‑координаты в виде рациональных чисел; библиотека автоматически нормализует их, но в старых файлах может потребоваться ручное преобразование.

## Распространённые проблемы и их устранение

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| `Unsupported format` exception | Использование более старой версии GroupDocs.Metadata, которая не распознаёт PSD | Обновите до версии 24.12 или новее |
| `NullPointerException` when calling `getArtist()` | Тег EXIF отсутствует в исходном файле | Проверьте `metadata.getExif().hasArtist()` перед чтением |
| License error after 30 days | Файл лицензии не найден в classpath | Поместите `metadata.lic` в `src/main/resources` или задайте `Metadata.setLicense("path/to/license")` |

## Часто задаваемые вопросы

**В: Можно ли извлечь EXIF‑метаданные из защищённого паролем файла PSD?**  
О: Да. Загрузите файл с помощью `new Metadata("file.psd", "password")` и затем получайте EXIF‑данные как обычно.

**В: Поддерживает ли GroupDocs.Metadata пакетную обработку множества файлов PSD?**  
О: Абсолютно. Создавайте объект `Metadata` внутри цикла или используйте вспомогательный класс `MetadataCollection` для эффективной обработки каталогов.

**В: Какие версии Java официально поддерживаются?**  
О: Java 8‑21 полностью протестированы. Библиотека использует только стандартные API, поэтому работает на любой совместимой JVM.

**В: Можно ли записать EXIF‑данные обратно в файл PSD?**  
О: Да. После изменения свойств через объект `Exif` вызовите `metadata.save("output.psd")`, чтобы сохранить изменения.

**В: Какой максимальный размер файла PSD может обработать библиотека без исчерпания памяти?**  
О: GroupDocs.Metadata потоково обрабатывает данные и может работать с файлами до **2 ГБ** на типичной машине с 8 ГБ ОЗУ благодаря своей низкопамятной архитектуре.

## Заключение

Теперь вы знаете, **как извлекать EXIF‑метаданные** из файлов PSD с помощью GroupDocs.Metadata для Java, от базовых тегов до расширенных IFD и GPS‑информации. Интегрируйте эти фрагменты кода в ваш конвейер обработки изображений, чтобы автоматизировать каталогизацию, проверки соответствия или сервисы, основанные на местоположении. Для более глубокого изучения попробуйте извлекать метаданные из других поддерживаемых форматов (JPEG, TIFF, PNG) или поэкспериментировать с возможностями записи, чтобы внедрять пользовательские теги.

---

**Последнее обновление:** 2026-08-10  
**Тестировано с:** GroupDocs.Metadata 24.12 for Java  
**Автор:** GroupDocs

## Связанные руководства

- [Извлечение ресурсов изображения из файлов PSD с помощью GroupDocs.Metadata в Java: Полное руководство](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Извлечение заголовка PSD и информации о слоях с помощью GroupDocs.Metadata для Java: Полное руководство](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Извлечение свойств MakerNote как тегов TIFF/EXIF с помощью GroupDocs.Metadata в Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)