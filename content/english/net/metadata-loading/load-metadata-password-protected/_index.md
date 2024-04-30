---
title: How to Load Metadata from Password Protected Document in .NET
linktitle: How to Load Metadata from Password Protected Document in .NET
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 13
url: /net/metadata-loading/load-metadata-password-protected/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.LoadingFiles
{
    using Options;
    using System;

    /// <summary>
    /// This example demonstrates how to load a password-protected document.
    /// </summary>
    public static class LoadPasswordProtectedDocument
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadPasswordProtectedDocument : How to load a password-protected document.\n");
            // Specify the password
            var loadOptions = new LoadOptions
            {
                Password = "123"
            };

            // "Your Input File" is an absolute or relative path to your document. Ex: @"C:\Docs\source.docx"
            using (var metadata = new Metadata("Your Input File", loadOptions))
            {
                // Extract, edit or remove metadata here
            }
        }
    }
}

```