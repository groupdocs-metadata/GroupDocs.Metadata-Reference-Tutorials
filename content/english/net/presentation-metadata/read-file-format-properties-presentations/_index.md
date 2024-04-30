---
title: Read File Format Properties from Presentations in .NET
linktitle: Read File Format Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 13
url: /net/presentation-metadata/read-file-format-properties-presentations/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Presentation
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This example demonstrates how to detect the exact type of a presentation and extract some additional file format information.
    /// </summary>
    public static class PresentationReadFileFormatProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationReadFileFormatProperties : How to detect the exact type of a presentation and extract some additional file format information.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                Console.WriteLine(root.FileType.FileFormat);
                Console.WriteLine(root.FileType.PresentationFormat);
                Console.WriteLine(root.FileType.MimeType);
                Console.WriteLine(root.FileType.Extension);
            }
        }
    }
}

```
