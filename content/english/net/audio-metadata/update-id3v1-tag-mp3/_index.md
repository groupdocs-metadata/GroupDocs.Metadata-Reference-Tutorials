---
title: Update ID3V1 Tag in MP3 Files using .NET
linktitle: Update ID3V1 Tag in MP3 Files using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 19
url: /net/audio-metadata/update-id3v1-tag-mp3/
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
    /// This code sample shows how to update the ID3v1 tag in an MP3 file.
    /// </summary>
    public static class MP3UpdateID3V1Tag
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # MP3UpdateID3V1Tag : How to update the ID3v1 tag in an MP3 file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<MP3RootPackage>();

                if (root.ID3V1 == null)
                {
                    root.ID3V1 = new ID3V1Tag();
                }

                root.ID3V1.Album = "test album";
                root.ID3V1.Artist = "test artist";
                root.ID3V1.Title = "test title";
                root.ID3V1.Comment = "test comment";
                root.ID3V1.Year = "2019";

                // ...

                metadata.Save("Your Input File");
            }
        }
    }
}

```
