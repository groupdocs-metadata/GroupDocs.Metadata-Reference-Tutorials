---
title: Update Custom Properties in Spreadsheets using .NET
linktitle: Update Custom Properties in Spreadsheets using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 15
url: /net/spreadsheet-metadata/update-custom-properties-spreadsheets/
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
    /// This code snippet demonstrates how to update custom metadata properties in a spreadsheet.
    /// </summary>
    public static class SpreadsheetUpdateCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetUpdateCustomProperties : How to update custom metadata properties in a spreadsheet.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                root.DocumentProperties.Set("customProperty1", "some value");
                root.DocumentProperties.Set("customProperty2", 7);

                // Set a content type property
                root.DocumentProperties.ContentTypeProperties.Set("customContentTypeProperty", "custom value");

                metadata.Save("Your Input File");
            }
        }
    }
}

```
