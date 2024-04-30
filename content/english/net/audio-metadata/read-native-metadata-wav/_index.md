---
title: Read Native Metadata Properties from WAV Files in .NET
linktitle: Read Native Metadata Properties from WAV Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 23
url: /net/audio-metadata/read-native-metadata-wav/
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
    /// This code sample shows how to extract technical audio information from a WAV file.
    /// </summary>
    public static class WavReadNativeMetadataProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # WavReadNativeMetadataProperties : How to extract technical audio information from a WAV file.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<WavRootPackage>();
                if (root.WavPackage != null)
                {
                    Console.WriteLine(root.WavPackage.AudioFormat);
                    Console.WriteLine(root.WavPackage.BitsPerSample);
                    Console.WriteLine(root.WavPackage.BlockAlign);
                    Console.WriteLine(root.WavPackage.ByteRate);
                    Console.WriteLine(root.WavPackage.NumberOfChannels);
                    Console.WriteLine(root.WavPackage.SampleRate);
                }
            }
        }
    }
}

```
