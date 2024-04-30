---
title: Update Inspection Properties in Presentations using .NET
linktitle: Update Inspection Properties in Presentations using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 17
url: /net/presentation-metadata/update-inspection-properties-presentations/
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
    /// This code sample demonstrates how to clean inspection properties in a presentation.
    /// </summary>
    public static class PresentationUpdateInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationUpdateInspectionProperties : How to clean inspection properties in a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                root.InspectionPackage.ClearComments();
                root.InspectionPackage.ClearHiddenSlides();

                metadata.Save("Your Input File");
            }
        }
    }
}

```