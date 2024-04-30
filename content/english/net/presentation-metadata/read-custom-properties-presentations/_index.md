---
title: Read Custom Properties from Presentations in .NET
linktitle: Read Custom Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 11
url: /net/presentation-metadata/read-custom-properties-presentations/
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
    using Tagging;

    /// <summary>
    /// This example shows how to extract custom metadata properties from a presentation.
    /// </summary>
    public static class PresentationReadCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationReadCustomProperties : How to extract custom metadata properties from a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

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
