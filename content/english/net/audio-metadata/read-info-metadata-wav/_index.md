---
title: Read Info Metadata from WAV Files in .NET
linktitle: Read Info Metadata from WAV Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 22
url: /net/audio-metadata/read-info-metadata-wav/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Audio.Wav
{
    using System;
    using Formats.Audio;

    /// <summary>
    /// This code sample shows how to extract INFO chunk metadata from a WAV file.
    /// </summary>
    public static class WavReadInfoMetadata
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # WavReadInfoMetadata : How to extract INFO chunk metadata from a WAV file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<WavRootPackage>();
                if (root.RiffInfoPackage != null)
                {
                    Console.WriteLine(root.RiffInfoPackage.Artist);
                    Console.WriteLine(root.RiffInfoPackage.Comment);
                    Console.WriteLine(root.RiffInfoPackage.Copyright);
                    Console.WriteLine(root.RiffInfoPackage.CreationDate);
                    Console.WriteLine(root.RiffInfoPackage.Software);
                    Console.WriteLine(root.RiffInfoPackage.Engineer);
                    Console.WriteLine(root.RiffInfoPackage.Genre);

                    // ...
                }
            }
        }
    }
}

```
