---
title: Read Inspection Properties from PDFs in .NET
linktitle: Read Inspection Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/pdf-metadata/read-inspection-properties-pdfs/
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
    /// This example demonstrates how to inspect a PDF document.
    /// </summary>
    public static class PdfReadInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PdfReadInspectionProperties : How to inspect a PDF document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PdfRootPackage>();

                if (root.InspectionPackage.Annotations != null)
                {
                    foreach (var annotation in root.InspectionPackage.Annotations)
                    {
                        Console.WriteLine(annotation.Name);
                        Console.WriteLine(annotation.Text);
                        Console.WriteLine(annotation.PageNumber);
                    }
                }

                if (root.InspectionPackage.Attachments != null)
                {
                    foreach (var attachment in root.InspectionPackage.Attachments)
                    {
                        Console.WriteLine(attachment.Name);
                        Console.WriteLine(attachment.MimeType);
                        Console.WriteLine(attachment.Description);
                    }
                }

                if (root.InspectionPackage.Bookmarks != null)
                {
                    foreach (var bookmark in root.InspectionPackage.Bookmarks)
                    {
                        Console.WriteLine(bookmark.Title);
                    }
                }

                if (root.InspectionPackage.DigitalSignatures != null)
                {
                    foreach (var signature in root.InspectionPackage.DigitalSignatures)
                    {
                        Console.WriteLine(signature.CertificateSubject);
                        Console.WriteLine(signature.Comments);
                        Console.WriteLine(signature.SignTime);

                        // ...
                    }
                }

                if (root.InspectionPackage.Fields != null)
                {
                    foreach (var field in root.InspectionPackage.Fields)
                    {
                        Console.WriteLine(field.Name);
                        Console.WriteLine(field.Value);

                        // ...
                    }
                }
            }
        }
    }
}
```