---
title: Обновить тег текста в файлах MP3 с помощью .NET
linktitle: Обновить тег текста в файлах MP3 с помощью .NET
second_title: GroupDocs.Метаданные .NET API
description: Узнайте, как программно обновить метаданные файла MP3, включая тексты песен, исполнителя и сведения об альбоме, с помощью GroupDocs.Metadata для .NET.
weight: 21
url: /ru/net/audio-metadata/update-lyrics-tag-mp3/
type: docs
---
# Обновить тег текста в файлах MP3 с помощью .NET

## Введение
В этом руководстве мы покажем, как использовать библиотеку GroupDocs.Metadata for .NET для программного обновления тега текста песни в файлах MP3. Этот процесс включает в себя доступ и изменение метаданных файлов MP3, в частности, информации о текстах песен.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующее:
- Базовые знания программирования на C#.
- Visual Studio установлена на вашем компьютере.
-  Установлена библиотека GroupDocs.Метаданные для .NET (см.[ссылка для скачивания](https://releases.groupdocs.com/metadata/net/)).
- Файл MP3 для целей тестирования.

## Импортировать пространства имен
Начните с импорта необходимых пространств имен в проект C#:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## Шаг 1. Загрузите файл MP3
 Сначала загрузите файл MP3 в`Metadata` объект с использованием GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Доступ к тегу Lyrics3V2
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## Шаг 2. Обновите информацию о текстах песен
Затем обновите информацию о тексте песни, а также другие важные сведения, такие как исполнитель, альбом и трек:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## Шаг 3. Добавьте настраиваемые поля (необязательно)
При желании вы можете добавить в тег дополнительные поля:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## Шаг 4. Сохраните изменения
Наконец, сохраните измененные метаданные обратно в файл MP3:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## Заключение
В этом руководстве мы рассмотрели, как обновить тег текста песни в файлах MP3 с помощью GroupDocs.Metadata для .NET. Следуя описанным шагам, вы сможете эффективно управлять метаданными в файлах MP3 и изменять их программными средствами.

## Часто задаваемые вопросы
### Могу ли я обновить другие метаданные, помимо текстов песен, с помощью GroupDocs.Metadata для .NET?
Да, GroupDocs.Metadata для .NET позволяет работать с различными типами метаданных в разных форматах файлов.
### Совместимы ли GroupDocs.Metadata для .NET с .NET Core?
Да, библиотека поддерживает как .NET Framework, так и .NET Core.
### Требует ли GroupDocs.Metadata для .NET лицензию для коммерческого использования?
 Да, вы можете получить лицензию от[ГруппаДокументы](https://purchase.groupdocs.com/buy) для коммерческого использования.
### Как я могу получить поддержку или задать вопросы, связанные с GroupDocs.Metadata для .NET?
 Вы можете посетить[Форум GroupDocs.Метаданные](https://forum.groupdocs.com/c/metadata/14) за поддержку и обсуждения.
### Могу ли я попробовать GroupDocs.Metadata для .NET бесплатно?
 Да, вы можете получить[бесплатная пробная версия](https://releases.groupdocs.com/) изучить его особенности.