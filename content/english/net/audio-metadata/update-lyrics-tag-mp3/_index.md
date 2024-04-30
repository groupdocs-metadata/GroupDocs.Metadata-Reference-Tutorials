---
title: Update Lyrics Tag in MP3 Files using .NET
linktitle: Update Lyrics Tag in MP3 Files using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 21
url: /net/audio-metadata/update-lyrics-tag-mp3/
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
    /// This example shows how to update the Lyrics tag in an MP3 file
    /// </summary>
    public static class MP3UpdateLyricsTag
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # MP3UpdateLyricsTag : How to update the Lyrics tag in an MP3 file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<MP3RootPackage>();

                if (root.Lyrics3V2 == null)
                {
                    root.Lyrics3V2 = new LyricsTag();
                }

                root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
                root.Lyrics3V2.Artist = "test artist";
                root.Lyrics3V2.Album = "test album";
                root.Lyrics3V2.Track = "test track";

                // You can add a fully custom field to the tag
                root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));

                // ...

                metadata.Save("Your Input File");
            }
        }
    }
}

```
