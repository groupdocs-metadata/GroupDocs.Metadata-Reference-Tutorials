---
title: Update Custom Properties in Presentations using .NET
linktitle: Update Custom Properties in Presentations using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 16
url: /net/presentation-metadata/update-custom-properties-presentations/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.Presentation
{
    using Formats.Document;
    using System;

    /// <summary>
    /// This code sample demonstrates how to add or update custom metadata properties in a presentation.
    /// </summary>
    public static class PresentationUpdateCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationUpdateCustomProperties : How to add or update custom metadata properties in a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                root.DocumentProperties.Set("customProperty1", "some value");
                root.DocumentProperties.Set("customProperty2", 123.1);

                metadata.Save("Your Input File");
            }
        }
    }
}

```