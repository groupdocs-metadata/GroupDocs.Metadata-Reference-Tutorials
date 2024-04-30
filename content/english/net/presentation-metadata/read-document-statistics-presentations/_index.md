---
title: Read Document Statistics from Presentations in .NET
linktitle: Read Document Statistics from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/presentation-metadata/read-document-statistics-presentations/
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
    /// This code sample demonstrates how to obtain simple text statistics for a presentation.
    /// </summary>
    public static class PresentationReadDocumentStatistics
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # PresentationReadDocumentStatistics : How to obtain simple text statistics for a presentation.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<PresentationRootPackage>();

                Console.WriteLine(root.DocumentStatistics.CharacterCount);
                Console.WriteLine(root.DocumentStatistics.PageCount);
                Console.WriteLine(root.DocumentStatistics.WordCount);
            }
        }
    }
}

```
