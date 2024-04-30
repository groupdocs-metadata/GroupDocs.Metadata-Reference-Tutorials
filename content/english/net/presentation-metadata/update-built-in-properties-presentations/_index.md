---
title: Update Built-In Properties in Presentations using .NET
linktitle: Update Built-In Properties in Presentations using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 15
url: /net/presentation-metadata/update-built-in-properties-presentations/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Presentation
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This example demonstrates how to update built-in metadata properties in a presentation.
    /// </summary>
    public static class PresentationUpdateBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationUpdateBuiltInProperties : How to update built-in metadata properties in a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

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
