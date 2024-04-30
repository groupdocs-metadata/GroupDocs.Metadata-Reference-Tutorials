---
title: Read MPEG Audio Metadata from MP3 Files in .NET
linktitle: Read MPEG Audio Metadata from MP3 Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/audio-metadata/read-mpeg-audio-metadata-mp3/
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
    /// This example demonstrates how to read MPEG audio metadata from an MP3 file.
    /// </summary>
    public class MP3ReadMpegAudioMetadata
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # MP3ReadMpegAudioMetadata : How to read MPEG audio metadata from an MP3 file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<MP3RootPackage>();

                Console.WriteLine(root.MpegAudioPackage.Bitrate);
                Console.WriteLine(root.MpegAudioPackage.ChannelMode);
                Console.WriteLine(root.MpegAudioPackage.Emphasis);
                Console.WriteLine(root.MpegAudioPackage.Frequency);
                Console.WriteLine(root.MpegAudioPackage.HeaderPosition);
                Console.WriteLine(root.MpegAudioPackage.Layer);

                // ...
            }
        }
    }
}

```