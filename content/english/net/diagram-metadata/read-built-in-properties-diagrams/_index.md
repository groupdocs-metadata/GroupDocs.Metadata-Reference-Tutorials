---
title: Read Built-In Properties from Diagrams in .NET
linktitle: Read Built-In Properties from Diagrams in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 10
url: /net/diagram-metadata/read-built-in-properties-diagrams/
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
    /// This code sample demonstrates how to extract built-in metadata properties from a diagram.
    /// </summary>
    public static class DiagramReadBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # DiagramReadBuiltInProperties : How to extract built-in metadata properties from a diagram.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<DiagramRootPackage>();

                Console.WriteLine(root.DocumentProperties.Creator);
                Console.WriteLine(root.DocumentProperties.Company);
                Console.WriteLine(root.DocumentProperties.Keywords);
                Console.WriteLine(root.DocumentProperties.Language);
                Console.WriteLine(root.DocumentProperties.TimeCreated);
                Console.WriteLine(root.DocumentProperties.Category);

                // ... 
            }
        }
    }
}

```
