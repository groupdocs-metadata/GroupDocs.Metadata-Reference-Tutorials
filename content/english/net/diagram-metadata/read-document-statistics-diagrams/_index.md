---
title: Read Document Statistics from Diagrams in .NET
linktitle: Read Document Statistics from Diagrams in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/diagram-metadata/read-document-statistics-diagrams/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Diagram
{
    using System;
    using Formats.Document;

    /// <summary>
    /// The following code sample demonstrates how to obtain the text statistics for a diagram.
    /// </summary>
    public static class DiagramReadDocumentStatistics
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # DiagramReadDocumentStatistics : How to obtain the text statistics for a diagram.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<DiagramRootPackage>();
                Console.WriteLine(root.DocumentStatistics.PageCount);
            }
        }
    }
}

```
