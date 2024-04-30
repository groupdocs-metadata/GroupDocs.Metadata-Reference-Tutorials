---
title: Loading Metadata from Stream in .NET Tutorial
linktitle: Loading Metadata from Stream in .NET Tutorial
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 11
url: /net/metadata-loading/load-metadata-stream/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.LoadingFiles
{
    using System;
    using System.IO;

    /// <summary>
    /// This example demonstrates how to load a file from a stream.
    /// </summary>
    public static class LoadFromStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadFromStream : How to load a file from a stream\n");
            // "Your Input File" is an absolute or relative path to your document. Ex: @"C:\Docs\source.doc"
            using (Stream stream = File.Open("Your Input File", FileMode.Open, FileAccess.ReadWrite))
            using (Metadata metadata = new Metadata(stream))
            {
                // Extract, edit or remove metadata here
            }
        }
    }
}

```