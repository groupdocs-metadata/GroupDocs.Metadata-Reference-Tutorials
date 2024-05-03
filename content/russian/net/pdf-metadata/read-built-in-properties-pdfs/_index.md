---
title: Чтение встроенных свойств из PDF-файлов в .NET
linktitle: Чтение встроенных свойств из PDF-файлов в .NET
second_title: GroupDocs.Метаданные .NET API
description: Узнайте, как читать метаданные PDF в .NET с помощью GroupDocs.Metadata. Получите доступ к именам авторов, датам создания, темам и т. д. с помощью кода C#.
type: docs
weight: 10
url: /ru/net/pdf-metadata/read-built-in-properties-pdfs/
---
## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Metadata для .NET для чтения встроенных свойств из файлов PDF. GroupDocs.Metadata — это мощная библиотека, которая позволяет разработчикам работать с метаданными, связанными с различными форматами документов, включая PDF-файлы, документы Microsoft Office, изображения и многое другое. Используя эту библиотеку, вы можете легко получать доступ и манипулировать атрибутами метаданных, встроенными в файлы PDF, такими как имена авторов, даты создания, темы и т. д.
## Предварительные условия
Прежде чем приступить к изучению этого руководства, убедитесь, что у вас есть следующие предварительные условия:
- Visual Studio: убедитесь, что на вашем компьютере установлена Visual Studio.
-  GroupDocs.Metadata для .NET: загрузите и установите GroupDocs.Metadata для .NET с сайта[здесь](https://releases.groupdocs.com/metadata/net/).
- Базовые знания C#: Знакомство с языком программирования C# и платформой .NET.

## Импортировать пространства имен
Начните с добавления необходимых пространств имен в проект C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Шаг 1. Загрузите метаданные PDF
Сначала загрузите PDF-файл и извлеките его метаданные с помощью GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Доступ к корневому пакету файла PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Получение и отображение встроенных свойств
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Доступ к дополнительным свойствам можно получить аналогичным образом.
    // ...
}
```
Помимо чтения метаданных, GroupDocs.Metadata позволяет программно выполнять расширенные операции, такие как редактирование, удаление или добавление новых свойств метаданных в файлы PDF. Эта гибкость обеспечивает комплексное управление метаданными документов в ваших приложениях .NET.
## Заключение
В этом руководстве мы рассмотрели, как использовать GroupDocs.Metadata для .NET для извлечения встроенных свойств из файлов PDF с помощью C#. Интегрировав эту библиотеку в свои проекты, вы сможете беспрепятственно выполнять операции с метаданными документов, предоставляя расширенные возможности управления документами.

## Часто задаваемые вопросы
### Может ли GroupDocs.Метаданные работать с другими форматами документов?
Да, GroupDocs.Metadata поддерживает различные форматы документов, такие как DOCX, XLSX, PPTX, PDF, JPG, PNG и другие.
### Доступна ли бесплатная пробная версия для GroupDocs.Metadata?
Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Metadata на сайте[здесь](https://releases.groupdocs.com/).
### Как изменить свойства метаданных с помощью GroupDocs.Metadata?
Вы можете изменить свойства метаданных программным путем, получив доступ к соответствующему пакету документов и установив новые значения.
### Поддерживает ли GroupDocs.Metadata .NET Core?
Да, GroupDocs.Metadata совместим как с .NET Framework, так и с .NET Core.
### Где я могу найти поддержку или задать вопросы, связанные с GroupDocs.Metadata?
 Для поддержки и обсуждения посетите[Форум GroupDocs.Метаданные](https://forum.groupdocs.com/c/metadata/14).