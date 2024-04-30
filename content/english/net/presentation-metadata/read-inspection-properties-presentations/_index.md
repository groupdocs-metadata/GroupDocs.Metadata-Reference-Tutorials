---
title: Read Inspection Properties from Presentations in .NET
linktitle: Read Inspection Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/presentation-metadata/read-inspection-properties-presentations/
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
    /// This code sample demonstrates how to inspect a presentation.
    /// </summary>
    public static class PresentationReadInspectionProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationReadInspectionProperties : How to inspect a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                if (root.InspectionPackage.Comments != null)
                {
                    foreach (var comment in root.InspectionPackage.Comments)
                    {
                        Console.WriteLine(comment.Author);
                        Console.WriteLine(comment.Text);
                        Console.WriteLine(comment.CreatedTime);
                        Console.WriteLine(comment.SlideNumber);
                    }
                }

                if (root.InspectionPackage.HiddenSlides != null)
                {
                    foreach (var slide in root.InspectionPackage.HiddenSlides)
                    {
                        Console.WriteLine(slide.Name);
                        Console.WriteLine(slide.Number);
                        Console.WriteLine(slide.SlideId);
                    }
                }
            }
        }
    }
}

```
