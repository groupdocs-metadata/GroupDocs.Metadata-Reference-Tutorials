---
date: '2026-06-22'
description: Узнайте, как читать sevenzip metadata java с использованием GroupDocs.Metadata
  для Java, включая то, как получить compressed size java и другие archive properties.
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: Как читать метаданные SevenZip в Java с помощью GroupDocs.Metadata
type: docs
url: /ru/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Как читать метаданные SevenZip в Java с GroupDocs.Metadata

Если вам нужно **read sevenzip metadata java** из Java‑приложения, вы попали по адресу. В этом руководстве мы покажем, как использовать **GroupDocs.Metadata** для получения имён файлов, сжатых размеров, несжатых размеров, дат изменения и многого другого — именно тех данных, которые нужны для проверки резервных копий, синхронизации или оптимизации хранения.

## Введение

Трудно получить доступ к свойствам метаданных из архивов SevenZip с помощью Java? Это руководство проведёт вас через процесс использования **GroupDocs.Metadata**. Мощная библиотека упрощает извлечение важной информации, такой как имена файлов, размеры и даты изменения, непосредственно из ваших архивов.

## Быстрые ответы
- **Какую библиотеку следует использовать?** GroupDocs.Metadata для Java — решение с единым API для более чем 70 форматов архивов и документов.  
- **Можно ли перечислить файлы внутри архива SevenZip?** Да — вызовите `getSevenZipPackage().getFiles()` после инициализации объекта `Metadata`.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для оценки; для продакшна требуется полная лицензия.  
- **Какая версия Java поддерживается?** JDK 8 или выше (совместима с Java 17 LTS).  
- **Обязательно ли использовать Maven?** Не обязательно, но Maven автоматически обрабатывает транзитивные зависимости.  

## Что означает «как читать sevenzip» в Java?

Чтение метаданных SevenZip означает открытие контейнера `.7z`, перечисление каждой записи и получение свойств, таких как **compressed size**, **uncompressed size**, **file name** и **modification date**, без извлечения самих файлов. Этот процесс даёт представление о составе архива, позволяет проверять целостность резервных копий и принимать решения о ёмкости хранилища без затрат на полное извлечение.

## Чтение метаданных sevenzip java

Использование основного ключевого слова в отдельном заголовке помогает как читателям, так и поисковым системам понять фокус данного руководства. Ниже мы подробно разберём шаги, необходимые для **read sevenzip metadata java** эффективно.

## Почему использовать GroupDocs.Metadata Java для извлечения метаданных?

GroupDocs.Metadata читает только заголовочную информацию, необходимую для извлечения метаданных, поэтому операция завершается за миллисекунды даже для архивов мног gigabyte. Поддерживает **70+** форматов архивов и документов, обрабатывает архивы до **2 GB** без загрузки всего файла в память и предоставляет единый API для всех поддерживаемых типов.

## Требования

Прежде чем приступить к работе с **GroupDocs.Metadata для Java**, убедитесь, что ваша среда разработки правильно настроена. Вам понадобится:

- **Java Development Kit (JDK):** версия 8 или выше.  
- **Maven:** рекомендуется для управления зависимостями, хотя можно добавить JAR вручную.  
- **Базовые знания Java:** знакомство с классами, методами и обработкой исключений.  

## Настройка GroupDocs.Metadata для Java

Чтобы использовать GroupDocs.Metadata, добавьте её в проект через Maven или загрузив библиотеку напрямую.

### Использование Maven

Добавьте следующую конфигурацию в ваш файл `pom.xml`:

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

### Прямая загрузка

Или скачайте последнюю версию с [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Приобретение лицензии

1. **Free Trial:** Начните с бесплатной пробной версии, чтобы оценить возможности GroupDocs.Metadata.  
2. **Temporary License:** Запросите временную лицензию, если нужен расширенный доступ для оценки.  
3. **Purchase:** Для длительного использования рассмотрите покупку полной лицензии.  

После завершения настройки перейдём к реализации функции чтения метаданных.

## Руководство по реализации

### Доступ к метаданным из архивов SevenZip

В этом разделе мы извлечём и выведем свойства метаданных, такие как имена файлов и размеры, из архива SevenZip.

#### Шаг 1: Инициализация объекта Metadata

Класс `Metadata` представляет точку входа для загрузки и взаимодействия с архивными файлами.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### Шаг 2: Получение корневого пакета

Метод `getRootPackageGeneric()` возвращает обобщённый вид корневого пакета архива, позволяя работать с записями без необходимости писать код, специфичный для формата.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Почему использовать `getRootPackageGeneric()`?** Он предоставляет обобщённый взгляд на содержимое архива, упрощая итерацию по записям без учёта конкретных форматов файлов.

#### Шаг 3: Итерация по записям архива

Класс `SevenZipPackage` представляет контейнер SevenZip, а каждая запись представлена объектом `SevenZipFileInfo`. Класс `SevenZipFileInfo` даёт прямой доступ к таким свойствам, как имя, сжатый размер и дата изменения.

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **Зачем извлекать эти свойства?** Знание размеров файлов помогает управлять хранилищем, а дата изменения может быть критичной для задач синхронизации. Вызов `getCompressedSize()` — это Java‑способ **get compressed size java** для каждой записи.

#### Шаг 4: Очистка ресурсов

Вызов `close()` у экземпляра `Metadata` освобождает нативные ресурсы и предотвращает утечки памяти в длительно работающих сервисах.

```java
} finally {
    metadata.dispose();
}
```

- **Зачем освобождать ресурсы?** Правильное освобождение объектов помогает избежать утечек памяти в долгоживущих приложениях.

## Как эффективно извлекать метаданные?

Загрузите архив SevenZip одним экземпляром `Metadata`, один раз вызовите `getRootPackageGeneric()` и затем пройдитесь по записям в цикле `for‑each`. Такой подход избегает повторных операций ввода‑вывода, снижает нагрузку на сборщик мусора и завершает работу за O(n), где *n* — количество записей.

## Практические применения

Понимание того, как **read sevenzip metadata java**, приносит множество реальных преимуществ:

1. **Управление резервными копиями:** Быстро проверяйте целостность и полноту архивов резервных копий.  
2. **Инструменты синхронизации файлов:** Используйте даты изменения для определения, какие файлы нуждаются в обновлении.  
3. **Оптимизация хранилища:** Сравнивайте сжатые и несжатые размеры для планирования ёмкости.  

Интеграция с другими системами возможна, позволяя автоматизировать извлечение метаданных в рамках более крупных процессов управления данными.

## Соображения по производительности

Работая с GroupDocs.Metadata и большими архивами, учитывайте следующие рекомендации:

- **Пакетная обработка:** Обрабатывайте файлы пакетами, чтобы эффективно управлять использованием памяти.  
- **Эффективная обработка исключений:** Используйте `try‑with‑resources` для автоматического управления ресурсами.  
- **Асинхронная обработка:** Реализуйте асинхронные техники для тяжёлых нагрузок.  

## Распространённые проблемы и решения

| Проблема | Решение |
|----------|---------|
| **`NullPointerException` при доступе к файлу** | Убедитесь, что путь к архиву указан правильно и файл не повреждён. |
| **Пики памяти при работе с огромными архивами** | Включите пакетную обработку или увеличьте размер кучи JVM (`-Xmx`). |
| **Лицензия не распознаётся** | Убедитесь, что файл лицензии находится в рабочем каталоге приложения или установлен через `License.setLicense(path)`. |

## Часто задаваемые вопросы

**Q:** Что такое GroupDocs.Metadata?  
**A:** Это Java‑библиотека для работы с метаданными различных форматов файлов, включая архивы SevenZip.

**Q:** Можно ли использовать GroupDocs.Metadata без Maven?  
**A:** Да, вы можете скачать JAR с официального сайта и добавить его в classpath проекта.

**Q:** Как эффективно обрабатывать большие архивы?  
**A:** Реализуйте пакетную обработку или используйте асинхронные потоки, чтобы ограничить потребление памяти.

**Q:** Где найти более подробные рекомендации?  
**A:** См. [official documentation](https://docs.groupdocs.com/metadata/java/) для полного справочника по API.

**Q:** Что делать, если возникнут проблемы с библиотекой?  
**A:** Обратитесь к сообществу на [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/).

## Ресурсы

- **Документация:** Подробнее на [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **Официальная документация:** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **Справочник API:** Подробная информация о API доступна по адресу [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Скачать:** Получите последнюю версию с [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub репозиторий:** Примеры кода доступны на [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Форум бесплатной поддержки:** Присоединяйтесь к обсуждениям или задавайте вопросы на [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Last Updated:** 2026-06-22  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs

## Связанные руководства

- [How to Read TAR Files and Extract Metadata with GroupDocs.Metadata for Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)
- [Update ZIP Comment Java – How to Update ZIP Archive Comments Using GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Extract Video Metadata Java: How to Read AVI Files with GroupDocs.Metadata](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)