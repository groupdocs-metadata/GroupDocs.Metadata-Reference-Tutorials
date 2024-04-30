---
title: Update Inspection Properties in Spreadsheets using .NET
linktitle: Update Inspection Properties in Spreadsheets using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 16
url: /net/spreadsheet-metadata/update-inspection-properties-spreadsheets/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Spreadsheet
{
    using Formats.Document;
    using System;

    /// <summary>
    /// This code sample shows how to remove inspection properties from a spreadsheet.
    /// </summary>
    public static class SpreadsheetUpdateInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetUpdateInspectionProperties : How to remove inspection properties from a spreadsheet.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                root.InspectionPackage.ClearComments();
                root.InspectionPackage.ClearDigitalSignatures();
                root.InspectionPackage.ClearHiddenSheets();

                metadata.Save("Your Input File");
            }
        }
    }
}

```
