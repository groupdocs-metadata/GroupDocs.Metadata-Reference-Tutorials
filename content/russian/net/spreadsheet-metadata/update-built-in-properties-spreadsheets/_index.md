---
title: Обновление встроенных свойств в электронных таблицах с помощью .NET
linktitle: Обновление встроенных свойств в электронных таблицах с помощью .NET
second_title: GroupDocs.Метаданные .NET API
description: Узнайте, как обновить встроенные свойства метаданных в файлах Excel с помощью GroupDocs.Metadata для .NET. Измените автора, время создания, компанию и т. д. с помощью C#.
weight: 14
url: /ru/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---

# Обновление встроенных свойств в электронных таблицах с помощью .NET

## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Metadata для .NET для обновления встроенных свойств в файлах электронных таблиц с помощью C#. GroupDocs.Metadata — это мощный API, который позволяет разработчикам читать, редактировать и удалять свойства метаданных из файлов различных форматов, включая электронные таблицы. Мы сосредоточимся конкретно на изменении таких свойств, как автор, время создания, компания, категория и ключевые слова в файлах Excel.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Visual Studio: установите последнюю версию Visual Studio.
-  GroupDocs.Metadata для .NET: загрузите и установите GroupDocs.Metadata для .NET с сайта[страница загрузки](https://releases.groupdocs.com/metadata/net/).
- Базовые знания C#: понимание языка программирования C# и платформы .NET.

## Импортировать пространства имен
Начните с импорта необходимых пространств имен в проект C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Шаг 1. Загрузите файл электронной таблицы
 Сначала инициализируйте`Metadata` объект, загрузив входной файл электронной таблицы:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Доступ к свойствам документа в корне
}
```
## Шаг 2. Обновите встроенные свойства
 Доступ к встроенным свойствам документа осуществляется через`SpreadsheetRootPackage` и измените их по мере необходимости:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Обязательно замените заполнители (`YourAuthorName`, `YourCompany`, `YourCategory`с фактическими значениями, которые вы хотите установить для свойств.
## Шаг 3. Сохраните изменения
После обновления свойств сохраните изменения обратно в файл электронной таблицы:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Заключение
В этом руководстве мы продемонстрировали, как использовать GroupDocs.Metadata для .NET для программного обновления встроенных свойств файлов электронных таблиц. Используя этот API, разработчики могут эффективно управлять метаданными в документах Excel, улучшая организацию и доступность данных.

## Часто задаваемые вопросы
### Какие форматы файлов поддерживает GroupDocs.Метаданные?
GroupDocs.Metadata поддерживает широкий спектр форматов файлов, включая документы Microsoft Office, PDF-файлы, изображения, аудиофайлы и многое другое.
### Могу ли я получить существующие свойства метаданных из файлов?
Да, вы можете извлекать и читать свойства метаданных, такие как автор, дата создания, ключевые слова и пользовательские свойства, с помощью GroupDocs.Metadata.
### Совместимы ли GroupDocs.Metadata с .NET Core?
Да, GroupDocs.Metadata совместим как с .NET Framework, так и с .NET Core.
### Предоставляет ли GroupDocs.Metadata бесплатную пробную версию?
 Да, вы можете загрузить бесплатную пробную версию GroupDocs.Metadata с сайта[здесь](https://releases.groupdocs.com/).
### Где я могу найти поддержку GroupDocs.Metadata?
 Для поддержки и обсуждения посетите[Форум GroupDocs.Метаданные](https://forum.groupdocs.com/c/metadata/14).