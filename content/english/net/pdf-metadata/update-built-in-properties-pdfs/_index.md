---
title: Update Built-In Properties in PDFs using .NET
linktitle: Update Built-In Properties in PDFs using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 15
url: /net/pdf-metadata/update-built-in-properties-pdfs/
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
    /// This code snippet demonstrates how to update built-in metadata properties in a PDF document.
    /// </summary>
    public static class PdfUpdateBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfUpdateBuiltInProperties : How to update built-in metadata properties in a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                root.DocumentProperties.Author = "test author";
                root.DocumentProperties.CreatedDate = DateTime.Now;
                root.DocumentProperties.Title = "test title";
                root.DocumentProperties.Keywords = "metadata, built-in, update";
                root.DocumentProperties.Creator = "test creator";
                root.DocumentProperties.Producer = "test producer";

                // ... 

                metadata.Save("Your Input File");
            }

            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();
                Console.WriteLine(root.DocumentProperties.Author);
                Console.WriteLine(root.DocumentProperties.CreatedDate);
                Console.WriteLine(root.DocumentProperties.Title);
                Console.WriteLine(root.DocumentProperties.Keywords);
                Console.WriteLine(root.DocumentProperties.Creator);
                Console.WriteLine(root.DocumentProperties.Producer);

            }
        }
    }
}

```