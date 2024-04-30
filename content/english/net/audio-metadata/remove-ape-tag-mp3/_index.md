---
title: Remove APE Tag from MP3 Files in .NET
linktitle: Remove APE Tag from MP3 Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 15
url: /net/audio-metadata/remove-ape-tag-mp3/
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
    /// This example shows how to remove the APEv2 tag from an MP3 file.
    /// </summary>
    public static class MP3RemoveApeTag
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # MP3RemoveApeTag : How to remove the APEv2 tag from an MP3 file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<MP3RootPackage>();

                root.RemoveApeV2();

                metadata.Save("Your Input File");
            }
        }
    }
}

```
