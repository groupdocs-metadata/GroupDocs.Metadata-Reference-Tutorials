---
title: Обновление встроенных свойств в PDF-файлах с помощью .NET
linktitle: Обновление встроенных свойств в PDF-файлах с помощью .NET
second_title: GroupDocs.Метаданные .NET API
description: Узнайте, как обновить свойства PDF-документа с помощью C# и GroupDocs.Metadata для .NET. Измените автора, заголовок, ключевые слова и многое другое программно.
weight: 15
url: /ru/net/pdf-metadata/update-built-in-properties-pdfs/
---

# Обновление встроенных свойств в PDF-файлах с помощью .NET

## Введение
В этом руководстве мы узнаем, как использовать GroupDocs.Metadata для .NET для обновления встроенных свойств PDF-документов. Эта библиотека предоставляет мощный набор инструментов для управления метаданными в различных форматах документов. Мы выполним необходимые шаги для изменения таких свойств, как автор, название, дата создания, ключевые слова, создатель и производитель, в файле PDF с использованием C#.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
-  GroupDocs.Метаданные для библиотеки .NET: загрузите библиотеку с сайта[здесь](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: установите Visual Studio для написания и выполнения кода C#.
- Базовое понимание C#: рекомендуется знание языка программирования C#.

## Импортировать пространства имен
Начните с включения необходимых пространств имен в проект C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Шаг 1. Инициализация объекта метаданных
 Начните с инициализации`Metadata`объект с путем к вашему PDF-файлу:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Ваш код будет здесь
}
```
## Шаг 2. Доступ к корневому пакету PDF
 Затем извлеките корневой пакет специально для PDF, используя`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Шаг 3. Обновите свойства документа
 Теперь обновите нужные свойства PDF-документа в`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Шаг 4. Сохраните изменения.
После изменения свойств сохраните изменения обратно в PDF-файл:
```csharp
metadata.Save("Your Output File Path");
```
## Шаг 5. Получите обновленные свойства
Чтобы проверить изменения, перезагрузите метаданные и получите обновленные свойства:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Заключение
В этом руководстве мы рассмотрели, как использовать GroupDocs.Metadata для .NET для программного обновления встроенных свойств PDF-документов. Следуя описанным шагам, вы сможете эффективно управлять метаданными в файлах PDF и изменять их с помощью C#. Не стесняйтесь изучить дополнительные функции и возможности, предлагаемые GroupDocs.Metadata для комплексного управления метаданными.

## Часто задаваемые вопросы
### Вопрос: Что такое GroupDocs.Metadata для .NET?
Ответ: GroupDocs.Metadata для .NET — это библиотека, которая позволяет разработчикам программно читать, редактировать, удалять и манипулировать метаданными в различных форматах документов.
### Вопрос: Где я могу найти документацию по GroupDocs.Metadata для .NET?
 О: Вы можете получить доступ к документации[здесь](https://tutorials.groupdocs.com/metadata/net/).
### Вопрос: Как загрузить GroupDocs.Metadata для .NET?
 О: Вы можете скачать GroupDocs.Metadata для .NET с сайта[эта ссылка](https://releases.groupdocs.com/metadata/net/).
### Вопрос: Доступна ли бесплатная пробная версия?
 О: Да, вы можете получить бесплатную пробную версию.[здесь](https://releases.groupdocs.com/).
### Вопрос: Где я могу получить поддержку GroupDocs.Metadata для .NET?
 О: Для получения поддержки посетите форум GroupDocs.Metadata.[здесь](https://forum.groupdocs.com/c/metadata/14).