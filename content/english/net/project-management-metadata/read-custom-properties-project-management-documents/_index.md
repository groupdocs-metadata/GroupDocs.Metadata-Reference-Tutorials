---
title: Read Custom Properties in .NET Project Management Documents
linktitle: Read Custom Properties in .NET Project Management Documents
second_title: GroupDocs.Metadata .NET API
description: 
type: docs
weight: 11
url: /net/project-management-metadata/read-custom-properties-project-management-documents/
---

## Complete Source Code
```csharp
// <copyright company="Aspose Pty Ltd">
//   Copyright (C) 2011-2024 GroupDocs. All Rights Reserved.
// </copyright>

namespace GroupDocs.Metadata.Examples.CSharp.AdvancedUsage.ManagingMetadataForSpecificFormats.Document.ProjectManagement
{
    using System;
    using GroupDocs.Metadata.Formats.Document;
    using GroupDocs.Metadata.Tagging;

    /// <summary>
    /// This example demonstrates how to read custom metadata properties of a ProjectManagement document.
    /// </summary>
    public static class ProjectManagementReadCustomProperties
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # ProjectManagementReadCustomProperties : How to read custom metadata properties of a ProjectManagement document.\n");
            using (Metadata metadata = new Metadata("Your Input File"))
            {
                var root = metadata.GetRootPackage<ProjectManagementRootPackage>();

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
