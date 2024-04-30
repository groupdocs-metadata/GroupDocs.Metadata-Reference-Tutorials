---
title: Read Custom Properties from PDFs in .NET
linktitle: Read Custom Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 11
url: /net/pdf-metadata/read-custom-properties-pdfs/
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
    using Tagging;

    /// <summary>
    /// This code sample shows how to extract custom metadata properties from a PDF document.
    /// </summary>
    public static class PdfReadCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfReadCustomProperties : How to extract custom metadata properties from a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));

                foreach (var property in customProperties)
                {
                    Console.WriteLine("{0} = {1}", property.Name, property.Value);
                }
            }
        }
    }
}

```
