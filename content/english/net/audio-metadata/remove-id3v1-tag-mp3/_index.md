---
title: Remove ID3V1 Tag from MP3 Files in .NET
linktitle: Remove ID3V1 Tag from MP3 Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 16
url: /net/audio-metadata/remove-id3v1-tag-mp3/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright> 

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Audio.MP3
{
    using Formats.Audio;
    using System;

    /// <summary>
    /// This code sample shows how to remove the ID3v1 tag from an MP3 file.
    /// </summary>
    public static class MP3RemoveID3V1Tag
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # MP3RemoveID3V1Tag : How to remove the ID3v1 tag from an MP3 file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<MP3RootPackage>();

                root.ID3V1 = null;

                metadata.Save("Your Input File");
            }
        }
    }
}

```
