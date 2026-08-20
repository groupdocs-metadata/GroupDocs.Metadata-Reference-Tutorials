---
date: '2026-08-20'
description: Узнайте, как извлекать XMP metadata в Java с использованием GroupDocs.Metadata.
  Это руководство показывает, как извлекать базовые, Dublin Core и Photoshop XMP metadata.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Узнайте, как извлекать XMP metadata в Java с помощью GroupDocs.Metadata.
  Этот учебник охватывает извлечение базовых, Dublin Core и Photoshop XMP с практическими
  примерами кода.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Как извлечь XMP metadata с помощью GroupDocs.Metadata для Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Как извлечь XMP metadata с помощью GroupDocs.Metadata для Java
type: docs
url: /ru/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как извлечь XMP‑метаданные с помощью GroupDocs.Metadata для Java

## Быстрые ответы
- **Какая библиотека обрабатывает XMP в Java?** GroupDocs.Metadata for Java.
- **Минимальная версия Java?** JDK 8 или новее.
- **Можно ли читать PNG и JPEG файлы?** Да, оба поддерживаются из коробки.
- **Требуется ли лицензия для продакшн?** Да, нужна полная или временная лицензия.
- **Где найти справочник API?** На официальном сайте документации GroupDocs.Metadata.

## Что такое XMP‑метаданные?
XMP (Extensible Metadata Platform) — это формат стандарта ISO для встраивания структурированных метаданных непосредственно в медиа‑файлы. Он обеспечивает межпрограммную совместимость и постоянное хранение данных без изменения оригинального контента. Сохраняя такие сведения, как создатель, авторские права, настройки камеры и пользовательские теги внутри файла, XMP гарантирует, что метаданные перемещаются вместе с ресурсом, упрощая каталогизацию и поиск в разных системах.

## Почему использовать GroupDocs.Metadata для Java?
GroupDocs.Metadata поддерживает **30+ форматов файлов** (включая PNG, JPEG, TIFF и PSD) и может обрабатывать файлы размером до **2 GB**, не загружая весь документ в память, обеспечивая **30 % снижение нагрузки на CPU** по сравнению с обычными парсерами. Это делает её идеальной для масштабных систем управления цифровыми активами (DAM).

## Предварительные требования

- **Java Development Kit (JDK) 8+** установлен.
- **Maven** для управления зависимостями.
- Базовое знакомство с Java I/O и объектно‑ориентированным программированием.

## Как настроить GroupDocs.Metadata для Java?
Чтобы начать, добавьте репозиторий GroupDocs и зависимость библиотеки в ваш `pom.xml`. Это позволит Maven автоматически разрешать артефакты и поддерживать их в актуальном состоянии, упрощая будущие обновления и исправления безопасности. После обновления `pom.xml` выполните `mvn clean install` для загрузки необходимых JAR‑файлов и проверки успешности установки.

```xml
<!-- ```xml
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
``` -->
```

Если вы предпочитаете ручной подход, скачайте последний JAR‑файл со страницы официальных релизов:

[GroupDocs.Metadata для Java релизы](https://releases.groupdocs.com/metadata/java/)

### Приобретение лицензии
- **Free trial** – оценить все функции в течение 30 дней.
- **Temporary license** – использовать во время разработки без ограничений.
- **Full license** – требуется для продакшн‑развертываний.

## Базовая инициализация

`Metadata` — точка входа для всех операций. Она представляет один файл и предоставляет доступ к встроенным XMP‑пакетам.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Как извлечь базовые XMP‑метаданные?

Загрузите изображение, откройте его XMP‑пакет и прочитайте общие свойства, такие как инструмент создания и метки времени.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Как извлечь XMP‑метаданные Dublin Core?

Схема Dublin Core хранит стандартизированные описательные элементы, такие как заголовок, создатель и тема. Доступ к ней осуществляется через класс `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Как извлечь Photoshop‑специфичные XMP‑метаданные?

Photoshop встраивает дополнительную информацию, такую как режим цвета, разрешение и количество слоёв. Получить эти значения можно через `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Практические применения

- **Digital asset management** – помечать и искать изображения по создателю, авторским правам или настройкам камеры.
- **Automated publishing pipelines** – внедрять или изменять XMP перед публикацией в веб‑галереи.
- **Analytics** – агрегировать метаданные из тысяч файлов для выявления тенденций использования.

## Соображения по производительности

Класс `Metadata` предоставляет доступ к метаданным файла и XMP‑пакетам. Освобождайте объекты `Metadata`, как только закончите чтение, чтобы освободить нативные ресурсы. `LoadOptions.LAZY` заставляет библиотеку загружать метаданные лениво, снижая потребление памяти. Для больших файлов используйте `Metadata.load(InputStream)`, чтобы держать использование кучи низким. При чтении множества небольших файлов переиспользуйте один экземпляр `Metadata`, чтобы уменьшить накладные расходы на создание объектов.

## Распространённые ошибки и устранение неполадок

| Симптом | Вероятная причина | Решение |
|---|---|---|
| `NullPointerException` при доступе к XMP | Файл не содержит XMP‑пакет | Вызовите `metadata.getXmpPackage()` и проверьте `null` перед чтением. Метод `getXmpPackage()` возвращает объект XMP‑пакета или `null`, если он отсутствует. |
| Медленная обработка 500 МБ изображений | Загрузка всего файла в память | Используйте `metadata.load(InputStream)` и включите `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Отсутствуют поля Photoshop | Изображение сохранено без информации о слоях Photoshop | Убедитесь, что исходный файл был экспортирован из Photoshop с включённой опцией «Save XMP». |

## Часто задаваемые вопросы

**Q: Можно ли извлечь XMP из PDF файлов?**  
A: Да, GroupDocs.Metadata поддерживает PDF‑XMP‑пакеты через тот же API `Metadata`.

**Q: Что происходит, если формат файла не поддерживается?**  
A: Библиотека бросает `UnsupportedFormatException`; перехватите её и переключитесь на универсальный обработчик.

**Q: Можно ли изменить XMP‑метаданные и сохранить их?**  
A: Абсолютно. После изменения свойств вызовите `metadata.save("output.png")`, чтобы сохранить обновления.

**Q: Работает ли библиотека на Android?**  
A: Ядро Java‑библиотеки совместимо с Android API 24+, но необходимо добавить артефакт, специфичный для `android`.

**Q: Как обрабатывать зашифрованные изображения?**  
A: Передайте пароль расшифровки в конструктор `Metadata`: `new Metadata(filePath, "password")`.

## Заключение

Теперь у вас есть полное, готовое к продакшн руководствo **как извлечь XMP‑метаданные** с помощью GroupDocs.Metadata для Java. Следуя описанным шагам, вы сможете обогатить свои приложения поисковыми, стандартизированными метаданными и открыть мощные возможности управления активами.

## Следующие шаги

Углубитесь в полный набор функций, изучив официальную документацию и поэкспериментировав с другими стандартами метаданных, такими как IPTC и EXIF.

[документация](https://docs.groupdocs.com/metadata/java/)

---

**Последнее обновление:** 2026-08-20  
**Тестировано с:** GroupDocs.Metadata for Java 23.11  
**Автор:** GroupDocs  

- [Документация](https://docs.groupdocs.com/metadata/java/)
- [Справочник API](https://reference.groupdocs.com/metadata/java/)
- [Скачать](https://releases.groupdocs.com/metadata/java/)
- [Репозиторий GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Бесплатный форум поддержки](https://forum.groupdocs.com/c/metadata/)
- [Временная лицензия](https://purchase.groupdocs.com/temporary-license/)

## Похожие руководства

- [Извлечь Dublin Core метаданные из Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Извлечь EXIF Software Tag в Java: Полное руководство с использованием GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Как извлечь метаданные с помощью GroupDocs.Metadata для Java – Руководства и примеры](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}