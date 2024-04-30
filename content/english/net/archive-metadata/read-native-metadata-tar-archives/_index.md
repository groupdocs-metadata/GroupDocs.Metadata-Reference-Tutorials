---
title: Read Native Metadata Properties from TAR Archives in .NET
linktitle: Read Native Metadata Properties from TAR Archives in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/archive-metadata/read-native-metadata-tar-archives/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Archive
{
    using Formats.Archive;
    using System;
    using System.Text;

    /// <summary>
    /// The following code snippet shows how to get metadata from a Tar archive.
    /// </summary>
    public static class TarReadNativeMetadataProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # TarReadNativeMetadataProperties : How to get metadata from a Tar archive.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<TarRootPackage>();

                Console.WriteLine(root.TarPackage.TotalEntries);

                foreach (var file in root.TarPackage.Files)
                {
                    Console.WriteLine(file.Name);
                    Console.WriteLine(file.Size);

                }
            }
        }
    }
}

```