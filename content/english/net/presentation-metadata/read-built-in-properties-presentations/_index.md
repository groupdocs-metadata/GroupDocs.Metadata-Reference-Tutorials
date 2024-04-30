---
title: Read Built-In Properties from Presentations in .NET
linktitle: Read Built-In Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 10
url: /net/presentation-metadata/read-built-in-properties-presentations/
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
    /// This example shows how to extract built-in metadata properties from a presentation.
    /// </summary>
    public static class PresentationReadBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationReadBuiltInProperties : How to extract built-in metadata properties from a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                Console.WriteLine(root.DocumentProperties.Author);
                Console.WriteLine(root.DocumentProperties.CreatedTime);
                Console.WriteLine(root.DocumentProperties.Company);
                Console.WriteLine(root.DocumentProperties.Category);
                Console.WriteLine(root.DocumentProperties.Keywords);
                Console.WriteLine(root.DocumentProperties.LastPrintedDate);
                Console.WriteLine(root.DocumentProperties.NameOfApplication);

                // ... 
            }
        }
    }
}

```
