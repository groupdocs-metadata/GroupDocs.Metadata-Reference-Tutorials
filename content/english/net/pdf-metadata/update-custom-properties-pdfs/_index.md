---
title: Update Custom Properties in PDFs using .NET
linktitle: Update Custom Properties in PDFs using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 16
url: /net/pdf-metadata/update-custom-properties-pdfs/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Pdf
{
    using Formats.Document;
    using System;

    /// <summary>
    /// This code snippet demonstrates how to update custom metadata properties in a PDF document.
    /// </summary>
    public static class PdfUpdateCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfUpdateCustomProperties : How to update custom metadata properties in a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                root.DocumentProperties.Set("customProperty1", "some value");

                metadata.Save("Your Input File");
            }
        }
    }
}

```
