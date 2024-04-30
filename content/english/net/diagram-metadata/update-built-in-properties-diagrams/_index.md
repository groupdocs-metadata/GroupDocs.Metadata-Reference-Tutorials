---
title: Update Built-In Properties in Diagrams using .NET
linktitle: Update Built-In Properties in Diagrams using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/diagram-metadata/update-built-in-properties-diagrams/
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
    /// The following code sample demonstrates how to update built-in metadata properties in a diagram document.
    /// </summary>
    public static class DiagramUpdateBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # DiagramUpdateBuiltInProperties : How to update built-in metadata properties in a diagram document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<DiagramRootPackage>();

                root.DocumentProperties.Creator = "test author";
                root.DocumentProperties.TimeCreated = DateTime.Now;
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
