---
title: Read Inspection Properties from Spreadsheets in .NET
linktitle: Read Inspection Properties from Spreadsheets in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 13
url: /net/spreadsheet-metadata/read-inspection-properties-spreadsheets/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Spreadsheet
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This code snippet shows how to inspect a spreadsheet document.
    /// </summary>
    public static class SpreadsheetReadInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetReadInspectionProperties : How to inspect a spreadsheet document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                if (root.InspectionPackage.Comments != null)
                {
                    foreach (var comment in root.InspectionPackage.Comments)
                    {
                        Console.WriteLine(comment.Author);
                        Console.WriteLine(comment.Text);
                        Console.WriteLine(comment.SheetNumber);
                        Console.WriteLine(comment.Row);
                        Console.WriteLine(comment.Column);
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

                if (root.InspectionPackage.HiddenSheets != null)
                {
                    foreach (var sheet in root.InspectionPackage.HiddenSheets)
                    {
                        Console.WriteLine(sheet.Name);
                        Console.WriteLine(sheet.Number);
                    }
                }
            }
        }
    }
}

```