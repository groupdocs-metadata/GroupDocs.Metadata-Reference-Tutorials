---
title: Read Built-In Properties from Spreadsheets in .NET
linktitle: Read Built-In Properties from Spreadsheets in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 10
url: /net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
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
    /// This code snippet demonstrates how to extract built-in metadata properties from a spreadsheet.
    /// </summary>
    public static class SpreadsheetReadBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetReadBuiltInProperties : How to extract built-in metadata properties from a spreadsheet.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                Console.WriteLine(root.DocumentProperties.Author);
                Console.WriteLine(root.DocumentProperties.CreatedTime);
                Console.WriteLine(root.DocumentProperties.Company);
                Console.WriteLine(root.DocumentProperties.Category);
                Console.WriteLine(root.DocumentProperties.Keywords);
                Console.WriteLine(root.DocumentProperties.Language);
                Console.WriteLine(root.DocumentProperties.ContentType);

                // ... 
            }
        }
    }
}

```
