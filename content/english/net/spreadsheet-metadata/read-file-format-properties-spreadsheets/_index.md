---
title: Read File Format Properties from Spreadsheets in .NET
linktitle: Read File Format Properties from Spreadsheets in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/spreadsheet-metadata/read-file-format-properties-spreadsheets/
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
    /// This example shows how to detect the exact type of a loaded spreadsheet and extract some additional file format information.
    /// </summary>
    public static class SpreadsheetReadFileFormatProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SpreadsheetReadFileFormatProperties : How to detect the exact type of a loaded spreadsheet and extract some additional file format information.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<SpreadsheetRootPackage>();

                Console.WriteLine(root.FileType.FileFormat);
                Console.WriteLine(root.FileType.SpreadsheetFormat);
                Console.WriteLine(root.FileType.MimeType);
                Console.WriteLine(root.FileType.Extension);
            }
        }
    }
}

```
