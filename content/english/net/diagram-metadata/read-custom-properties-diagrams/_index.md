---
title: Read Custom Properties from Diagrams in .NET
linktitle: Read Custom Properties from Diagrams in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 11
url: /net/diagram-metadata/read-custom-properties-diagrams/
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
    using Tagging;

    /// <summary>
    /// This code sample demonstrates how to extract custom metadata properties from a diagram.
    /// </summary>
    public static class DiagramReadCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # DiagramReadCustomProperties : How to extract custom metadata properties from a diagram.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<DiagramRootPackage>();

                var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));

                foreach (var property in customProperties)
                {
                    Console.WriteLine("{0} = {1}", property.Name, property.Value);
                }
            }
        }
    }
}

```
