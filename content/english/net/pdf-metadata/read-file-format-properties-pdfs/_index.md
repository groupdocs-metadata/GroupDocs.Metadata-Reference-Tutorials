---
title: Read File Format Properties from PDFs in .NET
linktitle: Read File Format Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 13
url: /net/pdf-metadata/read-file-format-properties-pdfs/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Pdf
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This code snippet shows how to detect the PDF version a loaded document and extract some additional file format information.
    /// </summary>
    public static class PdfReadFileFormatProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfReadFileFormatProperties : How to detect the PDF version a loaded document and extract some additional file format information.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                Console.WriteLine(root.FileType.FileFormat);
                Console.WriteLine(root.FileType.Version);
                Console.WriteLine(root.FileType.MimeType);
                Console.WriteLine(root.FileType.Extension);
            }
        }
    }
}

```
