---
title: Read Built-In Properties in .NET Project Management Documents
linktitle: Read Built-In Properties in .NET Project Management Documents
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 10
url: /net/project-management-metadata/read-built-in-properties-project-management-documents/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.ProjectManagement
{
    using System;
    using Formats.Document;

    /// <summary>
    /// This code sample demonstrates how to extract built-in properties of a ProjectManagement document.
    /// </summary>
    public static class ProjectManagementReadBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # ProjectManagementReadBuiltInProperties : How to extract built-in properties of a ProjectManagement document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<ProjectManagementRootPackage>();

                Console.WriteLine(root.DocumentProperties.Author);
                Console.WriteLine(root.DocumentProperties.CreationDate);
                Console.WriteLine(root.DocumentProperties.Company);
                Console.WriteLine(root.DocumentProperties.Category);
                Console.WriteLine(root.DocumentProperties.Keywords);
                Console.WriteLine(root.DocumentProperties.Revision);
                Console.WriteLine(root.DocumentProperties.Subject);

                // ... 
            }
        }
    }
}

```
