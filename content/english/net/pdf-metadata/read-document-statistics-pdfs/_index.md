---
title: Read Document Statistics from PDFs in .NET
linktitle: Read Document Statistics from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/pdf-metadata/read-document-statistics-pdfs/
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
    ///  This code sample demonstrates how to obtain the text statistics for a PDF document.
    /// </summary>
    public static class PdfReadDocumentStatistics
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfReadDocumentStatistics : How to obtain the text statistics for a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                Console.WriteLine(root.DocumentStatistics.CharacterCount);
                Console.WriteLine(root.DocumentStatistics.PageCount);
                Console.WriteLine(root.DocumentStatistics.WordCount);
            }
        }
    }
}

```
