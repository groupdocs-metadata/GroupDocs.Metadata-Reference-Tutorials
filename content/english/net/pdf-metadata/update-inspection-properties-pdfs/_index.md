---
title: Update Inspection Properties in PDFs using .NET
linktitle: Update Inspection Properties in PDFs using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 17
url: /net/pdf-metadata/update-inspection-properties-pdfs/
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
    /// This code sample demonstrates how to remove the inspection properties in a PDF document.
    /// </summary>
    public static class PdfUpdateInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfUpdateInspectionProperties : How to remove the inspection properties in a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                root.InspectionPackage.ClearAnnotations();
                root.InspectionPackage.ClearAttachments();
                root.InspectionPackage.ClearFields();
                root.InspectionPackage.ClearBookmarks();
                root.InspectionPackage.ClearDigitalSignatures();

                metadata.Save("Your Input File");
            }
        }
    }
}
```
