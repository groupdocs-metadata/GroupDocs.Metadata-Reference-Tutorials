---
title: Remove Archive Comment from ZIP Files in .NET
linktitle: Remove Archive Comment from ZIP Files in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 14
url: /net/archive-metadata/remove-archive-comment-zip-files/
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
    /// The following code snippet shows how to remove the user comment from a ZIP archive.
    /// </summary>
    public static class ZipRemoveArchiveComment
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # ZipRemoveArchiveComment : How to remove the user comment from a ZIP archive.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<ZipRootPackage>();

                root.ZipPackage.Comment = null;

                metadata.Save("Your Input File");
            }
        }
    }
}

```
