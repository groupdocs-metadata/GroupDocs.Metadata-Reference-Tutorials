---
title: Read File Format Properties from Diagrams in .NET
linktitle: Read File Format Properties from Diagrams in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 13
url: /net/diagram-metadata/read-file-format-properties-diagrams/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Diagram
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This code sample shows how to detect the exact type of a loaded diagram and extract some additional file format information.
    /// </summary>
    public static class DiagramReadFileFormatProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # DiagramReadFileFormatProperties : How to detect the exact type of a loaded diagram and extract some additional file format information.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<DiagramRootPackage>();

                Console.WriteLine(root.FileType.FileFormat);
                Console.WriteLine(root.FileType.DiagramFormat);
                Console.WriteLine(root.FileType.MimeType);
                Console.WriteLine(root.FileType.Extension);
            }
        }
    }
}

```
