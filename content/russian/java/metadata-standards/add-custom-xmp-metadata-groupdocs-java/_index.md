---
date: '2026-06-12'
description: Узнайте, как создавать пользовательские пакеты XMP, управлять метаданными
  файлов и добавлять пользовательские метаданные в PDF с помощью GroupDocs.Metadata
  для Java.
keywords:
- create custom xmp package
- manage file metadata
- add custom metadata pdf
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  headline: Create Custom XMP Package with GroupDocs.Metadata for Java
  type: TechArticle
- description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  name: Create Custom XMP Package with GroupDocs.Metadata for Java
  steps:
  - name: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
    text: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
  - name: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
    text: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
  - name: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
    text: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
  type: HowTo
- questions:
  - answer: Over 50 formats—including JPEG, PNG, PDF, DOCX, and TIFF—support XMP packet
      injection. See the full list in the [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).
    question: What file formats support custom XMP packages?
  - answer: Yes, the library lets you read, modify, and delete any XMP property using
      the `IXmp` interface.
    question: Can I edit existing XMP metadata with GroupDocs.Metadata?
  - answer: For unsupported formats, consider wrapping the file in a container that
      does support XMP (e.g., converting to PDF) or using an alternative metadata
      store.
    question: How do I handle files that don’t natively support XMP?
  - answer: Absolutely—GroupDocs.Metadata is tested against Java 8 through Java 21,
      including all LTS releases.
    question: Is the library compatible with Java 17 LTS?
  - answer: Common pitfalls include using an incorrect namespace URI, exceeding the
      maximum packet size (≈ 2 MB), or attempting to write to a read‑only file. Ensure
      proper permissions and validate your XML schema before saving.
    question: What are typical errors when adding XMP packages?
  type: FAQPage
title: Создайте пользовательский пакет XMP с GroupDocs.Metadata для Java
type: docs
url: /ru/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# Создать пользовательский XMP‑пакет с GroupDocs.Metadata для Java

В современных цифровых рабочих процессах **создание пользовательских XMP‑пакетов** является необходимым для внедрения богатых, поисковых метаданных непосредственно в файлы. Независимо от того, работаете ли вы с изображениями, PDF или мультимедийными ресурсами, GroupDocs.Metadata для Java предоставляет надёжный способ **управлять метаданными файлов** и **добавлять пользовательские метаданные в PDF** без внешних баз данных. В этом руководстве мы пройдём весь процесс — от настройки библиотеки до внедрения полностью функционального XMP‑пакета — чтобы вы могли начать обогащать свои документы уже сегодня.

## Быстрые ответы
- **Какой первый шаг?** Добавьте GroupDocs.Metadata как зависимость Maven или скачайте JAR.  
- **Сколько строк кода?** Для создания и присоединения пользовательского XMP‑пакета требуется всего три лаконичных оператора.  
- **Какие форматы файлов поддерживаются?** Более 50 форматов, включая JPEG, PNG, PDF, DOCX и TIFF.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для разработки; для продакшн‑использования требуется постоянная лицензия.  
- **Можно ли использовать это с Java 11+?** Да, библиотека совместима с Java 8 до Java 21.

## Что такое «создание пользовательского XMP‑пакета»?
*Создание пользовательского XMP‑пакета* означает построение XMP‑пакета, содержащего определяемые пользователем поля метаданных, и внедрение его в поддерживаемый файл. Этот пакет хранится внутри XMP‑раздела файла, делая метаданные переносимыми и доступными для поиска любой XMP‑совместимой программой.

## Почему использовать GroupDocs.Metadata для Java для управления метаданными файлов?
GroupDocs.Metadata поддерживает **более 50 форматов ввода и вывода** и может обрабатывать файлы размером до **2 ГБ** без загрузки всего документа в память, что снижает потребление ОЗУ до **80 %** на больших ресурсах. API также предоставляет потокобезопасные операции, позволяя выполнять высокопроизводительную пакетную обработку в корпоративных средах.

## Предварительные требования
- **Java Development Kit** 8 или новее (рекомендовано Java 11+).  
- IDE, например **IntelliJ IDEA** или **Eclipse**.  
- Установленный Maven для управления зависимостями.  
- Базовое понимание классов Java и концепций метаданных.

## Настройка GroupDocs.Metadata для Java
### Настройка Maven
Добавьте следующую зависимость в ваш файл `pom.xml`, чтобы включить GroupDocs.Metadata:

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

Обратитесь к [API Documentation](https://reference.groupdocs.com/metadata/java/) для полного списка сигнатур методов.  
Для подробного справочника API см. [GroupDocs.Metadata Java Docs](https://docs.groupdocs.com/metadata/java/).

**Прямая загрузка** – Если вы предпочитаете ручную настройку, получите последнюю JAR‑файл с [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/). Вы также можете просмотреть страницу [Latest Releases](https://releases.groupdocs.com/metadata/java/) для деталей журнала изменений.

### Приобретение лицензии
- **Free Trial** – Оценить все функции бесплатно.  
- **Temporary License** – Получить ограниченный по времени ключ для тестирования разработки. ([Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/))  
- **Purchase** – Приобрести постоянную лицензию для использования в продакшн.

Исходный код и примеры доступны на [GroupDocs Metadata on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## Руководство по реализации
Ниже представлено пошаговое руководство, показывающее точно, как **создать пользовательский XMP‑пакет** и внедрить его в файл.

### Как создать пользовательский XMP‑пакет и присоединить его к файлу?
Загрузите целевой файл с помощью класса `Metadata`, создайте `XmpPacketWrapper`, определите свои пользовательские XMP‑поля и, наконец, сохраните изменения. Этот сквозной процесс требует только три вызова методов после инициализации. Процесс гарантирует корректное внедрение XMP‑пакета, а файл остаётся полностью функциональным во всех поддерживаемых приложениях.

### Инициализация объекта Metadata
`Metadata` — основной класс, представляющий файл и предоставляющий методы для чтения и записи его метаданных.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### Создание нового XmpPacketWrapper
`XmpPacketWrapper` служит контейнером для одного или нескольких XMP‑пакетов, позволяя выполнять пакетные обновления перед сохранением.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### Определение и настройка пользовательского XMP‑пакета
Интерфейс `IXmp` позволяет определять пользовательские XMP‑схемы и задавать значения свойств внутри пакета.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### Сохранение обновлённых метаданных
`Metadata.save()` записывает изменённые метаданные обратно в оригинальный файл, сохраняет любые добавленные XMP‑пакеты.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### Объяснение ключевых компонентов
- **Metadata Object** – Центральный узел для доступа к метаданным файла.  
- **IXmp Interface** – Предоставляет методы для чтения/записи XMP‑специфических полей.  
- **XmpPacketWrapper** – Содержит один или несколько XMP‑пакетов, позволяя выполнять пакетные обновления.  
- **Custom XMP Package** – Пользовательская схема, которая хранит дополнительную информацию.

## Распространённые проблемы и решения
- **Неподдерживаемый формат файла** – Убедитесь, что тип целевого файла присутствует в официальном списке форматов (поддерживается более 50 форматов).  
- **License Not Found** – Убедитесь, что файл лицензии размещён в корневом каталоге приложения или установлен через `License.setLicense("license_path")`.  
- **Memory Exhaustion on Large Files** – Используйте `metadata.setLoadOptions(LoadOptions.lazyLoad())` для ленивой обработки метаданных и снижения использования памяти.

Для дополнительной помощи посетите форум [GroupDocs Support](https://forum.groupdocs.com/c/metadata/).

## Практические применения
1. **Digital Asset Management** – Внедрить лицензирование и права использования непосредственно в изображения и PDF.  
2. **Content Personalization** – Прикрепить идентификаторы, специфичные для пользователя, к документам для целевой доставки.  
3. **Regulatory Compliance** – Хранить аудиторские следы и политики удержания внутри самого файла, упрощая аудиты управления.

## Соображения по производительности
- **Resource Optimization** – Обрабатывать метаданные в режиме потоковой передачи, чтобы поддерживать использование ОЗУ ниже **100 МБ** для файлов размером более **1 ГБ**.  
- **Version Updates** – Держите библиотеку актуальной; каждый крупный релиз добавляет поддержку новых форматов и повышает скорость обработки до **30 %**.

## Заключение
Следуя этому руководству, вы теперь знаете, как **создавать пользовательские XMP‑пакеты** с помощью GroupDocs.Metadata для Java, что позволяет эффективно **управлять метаданными файлов** и **добавлять пользовательские метаданные в PDF** и многие другие форматы. Экспериментируйте с дополнительными XMP‑схемами, интегрируйте процесс в ваш CI‑конвейер или комбинируйте его с GroupDocs.Viewer для сквозной обработки документов.

## Часто задаваемые вопросы

**Q: Какие форматы файлов поддерживают пользовательские XMP‑пакеты?**  
A: Более 50 форматов — включая JPEG, PNG, PDF, DOCX и TIFF — поддерживают внедрение XMP‑пакетов. Смотрите полный список в [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).

**Q: Можно ли редактировать существующие XMP‑метаданные с помощью GroupDocs.Metadata?**  
A: Да, библиотека позволяет читать, изменять и удалять любые XMP‑свойства с помощью интерфейса `IXmp`.

**Q: Как обрабатывать файлы, которые изначально не поддерживают XMP?**  
A: Для неподдерживаемых форматов рассмотрите возможность обернуть файл в контейнер, поддерживающий XMP (например, конвертировать в PDF) или использовать альтернативное хранилище метаданных.

**Q: Совместима ли библиотека с Java 17 LTS?**  
A: Абсолютно — GroupDocs.Metadata протестирована с Java 8 до Java 21, включая все LTS‑версии.

**Q: Какие типичные ошибки возникают при добавлении XMP‑пакетов?**  
A: Распространённые проблемы включают использование неверного URI пространства имён, превышение максимального размера пакета (≈ 2 МБ) или попытку записи в файл только для чтения. Обеспечьте правильные разрешения и проверьте вашу XML‑схему перед сохранением.

**Последнее обновление:** 2026-06-12  
**Тестировано с:** GroupDocs.Metadata 23.12 for Java  
**Автор:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with operations on metadata
}
```

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Get the root XMP package from the metadata
    IXmp root = (IXmp) metadata.getRootPackage();
```

```java
import com.groupdocs.metadata.core.XmpPacketWrapper;

// Create a new XmpPacketWrapper to hold custom packages
XmpPacketWrapper packet = new XmpPacketWrapper();
```

```java
import com.groupdocs.metadata.core.XmpPackage;
import com.groupdocs.metadata.core.XmpArray;
import com.groupdocs.metadata.core.XmpArrayType;

// Define and configure the custom XMP package
custom = new XmpPackage("gd", "GroupDocs Custom Package");
custom.set("CustomProperty", "CustomValue");

// Add it to the packet
packet.addPackage(custom);
```

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```

## Связанные руководства

- [Добавить пользовательские XMP‑метаданные в файлы с GroupDocs.Metadata Java: Полное руководство](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [Как добавить метаданные в PDF с помощью GroupDocs.Metadata для Java – Руководство разработчика](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [Как извлечь пользовательские метаданные из PDF с использованием GroupDocs.Metadata в Java: Полное руководство](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)