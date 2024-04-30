---
title: Update Archive Comment in ZIP Files using .NET
linktitle: Update Archive Comment in ZIP Files using .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 15
url: /net/archive-metadata/update-archive-comment-zip-files/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Archive
{
    using Formats.Archive;
    using System;

    /// <summary>
    /// The following code snippet shows how to update the user comment in a ZIP archive.
    /// </summary>
    public static class ZipUpdateArchiveComment
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # ZipUpdateArchiveComment : How to update the user comment in a ZIP archive.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<ZipRootPackage>();

                root.ZipPackage.Comment = "updated comment";

                metadata.Save("Your Input File");
            }
        }
    }
}

```
