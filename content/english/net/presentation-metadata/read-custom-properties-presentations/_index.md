---
title: Read Custom Properties from Presentations in .NET
linktitle: Read Custom Properties from Presentations in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to read custom properties from presentations in .NET using GroupDocs.Metadata. Access and retrieve metadata efficiently.
weight: 11
url: /net/presentation-metadata/read-custom-properties-presentations/
---
## Introduction
In this tutorial, we will explore how to read custom properties from presentations in .NET using GroupDocs.Metadata. Custom properties contain additional information embedded within the presentation file, which can be useful for organizing, categorizing, or describing the content. By leveraging the GroupDocs.Metadata library, developers can efficiently access and extract these custom properties for various purposes.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites set up:
- Visual Studio: Install Visual Studio on your system.
- GroupDocs.Metadata for .NET: Download and install GroupDocs.Metadata for .NET from the [website](https://releases.groupdocs.com/metadata/net/).
- Presentation File: Prepare a sample presentation file (e.g., PowerPoint) containing custom properties for testing.

## Import Namespaces
Start by importing the necessary namespaces into your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
using GroupDocs.Tagging;
```
## Step 1: Load Presentation and Access Custom Properties
First, instantiate a `Metadata` object with your input presentation file path:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Step 2: Retrieve Custom Properties
Next, retrieve custom properties from the presentation excluding built-in properties:
```csharp
    var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));
    foreach (var property in customProperties)
    {
        Console.WriteLine("{0} = {1}", property.Name, property.Value);
    }
}
```

## Conclusion
In this tutorial, we've demonstrated how to use GroupDocs.Metadata for .NET to read custom properties from presentations. Leveraging the library's capabilities, developers can easily access, retrieve, and manipulate metadata embedded within various document formats, enhancing their applications' functionality and flexibility.

## FAQ's
### What are custom properties in presentations?
Custom properties are user-defined metadata fields that store additional information within a presentation file, such as author details, keywords, or custom descriptions.
### Can GroupDocs.Metadata handle other file formats besides presentations?
Yes, GroupDocs.Metadata supports a wide range of file formats, including documents, spreadsheets, images, videos, and more.
### How do I install GroupDocs.Metadata for .NET?
You can download and install GroupDocs.Metadata for .NET from the releases page [here](https://releases.groupdocs.com/metadata/net/).
### Is there a free trial available for GroupDocs.Metadata?
Yes, you can get a free trial of GroupDocs.Metadata to explore its features before making a purchase [here](https://releases.groupdocs.com/).
### Where can I get support for GroupDocs.Metadata?
For technical assistance and discussions related to GroupDocs.Metadata, visit the support forum [here](https://forum.groupdocs.com/c/metadata/14).
