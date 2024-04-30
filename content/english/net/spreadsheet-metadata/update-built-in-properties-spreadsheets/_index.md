---
title: Update Built-In Properties in Spreadsheets using .NET
linktitle: Update Built-In Properties in Spreadsheets using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
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
    /// This example shows how to update built-in metadata properties in a spreadsheet.
    /// </summary>
    public static class SpreadsheetUpdateBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetUpdateBuiltInProperties : How to update built-in metadata properties in a spreadsheet.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                root.DocumentProperties.Author = "test author";
                root.DocumentProperties.CreatedTime = DateTime.Now;
                root.DocumentProperties.Company = "GroupDocs";
                root.DocumentProperties.Category = "test category";
                root.DocumentProperties.Keywords = "metadata, built-in, update";

                // ... 

                metadata.Save("Your Input File");
            }
        }
    }
}

```