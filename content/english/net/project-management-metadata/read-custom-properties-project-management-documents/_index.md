---
title: Read Custom Properties in .NET Project Management Documents
linktitle: Read Custom Properties in .NET Project Management Documents
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract custom properties from .NET project management documents using GroupDocs.Metadata for .NET. Enhance your metadata management.
type: docs
weight: 11
url: /net/project-management-metadata/read-custom-properties-project-management-documents/
---
## Introduction
In the world of .NET development, managing metadata within project management documents is a crucial aspect of data organization and retrieval. GroupDocs.Metadata for .NET offers powerful capabilities to read custom properties from various project management file formats like Microsoft Project (MPP) files. This tutorial will guide you through the process of utilizing GroupDocs.Metadata to extract custom properties from .NET project management documents step by step.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites in place:
- Visual Studio: Install Visual Studio IDE on your machine.
- GroupDocs.Metadata for .NET: Download and install GroupDocs.Metadata for .NET from the [download page](https://releases.groupdocs.com/metadata/net/).
- .NET Framework: Have a basic understanding of the .NET framework and C# programming language.
- Project Management Document: Prepare a sample .NET project management document (e.g., Microsoft Project file) to work with in this tutorial.

## Import Namespaces
To begin, you'll need to import the necessary namespaces to access GroupDocs.Metadata features within your C# project:
```csharp
using System;
using GroupDocs.Metadata.Formats.Document;
using GroupDocs.Metadata.Tagging;
```
## Step 1: Load the Project Management Document
First, initialize a `Metadata` object by loading your project management document:
```csharp
using (Metadata metadata = new Metadata("YourInputFile"))
{
    // Access the root package specific to project management documents
    var root = metadata.GetRootPackage<ProjectManagementRootPackage>();
```
## Step 2: Retrieve Custom Properties
Next, extract custom properties from the project management document:
```csharp
    // Retrieve custom properties excluding built-in properties
    var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));
```
## Step 3: Display Custom Properties
Iterate through the retrieved custom properties and display their names and values:
```csharp
    // Display custom property names and values
    foreach (var property in customProperties)
    {
        Console.WriteLine("{0} = {1}", property.Name, property.Value);
    }
}
```

## Conclusion
In this tutorial, you've learned how to use GroupDocs.Metadata for .NET to read custom properties from .NET project management documents efficiently. Leveraging the library's capabilities, you can manage metadata effectively within your applications, enhancing data retrieval and organization.

## FAQ's
### Can GroupDocs.Metadata extract properties from all types of project management documents?
GroupDocs.Metadata supports a wide range of project management formats, including Microsoft Project (MPP) files and others.
### Is a license required to use GroupDocs.Metadata for .NET?
Yes, a license is required for commercial use. You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### How can I access further documentation for GroupDocs.Metadata?
Explore detailed documentation at the [reference page](https://reference.groupdocs.com/metadata/net/).
### Where can I get support for GroupDocs.Metadata related queries?
Join the community at the [GroupDocs Metadata forum](https://forum.groupdocs.com/c/metadata/14) for support and discussions.
### Can I try GroupDocs.Metadata for free before purchasing?
Yes, you can access a free trial from [here](https://releases.groupdocs.com/).
