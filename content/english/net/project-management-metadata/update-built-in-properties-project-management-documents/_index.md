---
title: Update Built-In Properties in .NET Project Management Documents
linktitle: Update Built-In Properties in .NET Project Management Documents
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 12
url: /net/project-management-metadata/update-built-in-properties-project-management-documents/
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
    /// This code sample demonstrates how to update built-in properties in a ProjectManagement document.
    /// </summary>
    public static class ProjectManagementUpdateBuiltInProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # ProjectManagementUpdateBuiltInProperties : How to update built-in properties in a ProjectManagement document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<ProjectManagementRootPackage>();

                root.DocumentProperties.Author = "test author";
                root.DocumentProperties.CreationDate = DateTime.Now;
                root.DocumentProperties.Company = "GroupDocs";
                root.DocumentProperties.Comments = "test comment";
                root.DocumentProperties.Keywords = "metadata, built-in, update";

                // ... 

                metadata.Save("Your Input File");
            }
        }
    }
}

```