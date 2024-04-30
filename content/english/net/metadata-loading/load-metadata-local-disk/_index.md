---
title: How to Load Metadata from Local Disk in .NET
linktitle: How to Load Metadata from Local Disk in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 10
url: /net/metadata-loading/load-metadata-local-disk/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

using System;

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.LoadingFiles
{
    /// <summary>
    /// This example demonstrates how to load a file from a local disk.
    /// </summary>
    public static class LoadFromLocalDisk
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadFromLocalDisk : How to load a file from a local disk\n");
            // "Your Input File" is an absolute or relative path to your document. Ex: @"C:\Docs\source.one"
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                // Extract, edit or remove metadata here
            }
        }
    }
}

```