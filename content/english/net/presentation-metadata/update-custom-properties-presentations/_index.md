---
title: Update Custom Properties in Presentations using .NET
linktitle: Update Custom Properties in Presentations using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to manage presentation metadata using GroupDocs.Metadata for .NET. Update custom properties efficiently in PowerPoint files.
weight: 16
url: /net/presentation-metadata/update-custom-properties-presentations/
---
## Introduction
In this tutorial, we will explore how to leverage GroupDocs.Metadata for .NET to update custom properties within presentations. GroupDocs.Metadata is a powerful API that allows developers to manipulate metadata in various file formats programmatically. Specifically, we'll focus on presentations (such as PowerPoint files) and demonstrate how to add or modify custom properties using C#.
## Prerequisites
Before diving into the tutorial, ensure you have the following:
- Basic knowledge of C# programming language.
- Visual Studio installed on your machine.
- GroupDocs.Metadata for .NET library. You can download it from [here](https://releases.groupdocs.com/metadata/net/).
- An input presentation file (e.g., a PowerPoint file) to work with.

## Import Namespaces
First, start by importing the necessary namespaces in your C# project.
```csharp
using GroupDocs.Metadata.Formats.Document;
using System;
using GroupDocs.Metadata;
```
## Step 1: Initialize Metadata and Access Root Package
Begin by initializing a `Metadata` object with your input presentation file path. Then, access the root package of the presentation file.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Step 2: Update Custom Properties
Next, update or add custom properties to the presentation file.
```csharp
    root.DocumentProperties.Set("customProperty1", "some value");
    root.DocumentProperties.Set("customProperty2", 123.1);
```
In the above code snippet:
- `Set("customProperty1", "some value")` sets a custom property named "customProperty1" with the value "some value".
- `Set("customProperty2", 123.1)` sets another custom property named "customProperty2" with a numeric value.
## Step 3: Save the Updated Presentation
After modifying the custom properties, save the changes back to the input presentation file.
```csharp
    metadata.Save("YourInputFile.pptx");
}
```

## Conclusion
In this tutorial, we've demonstrated how to use GroupDocs.Metadata for .NET to update custom properties in presentations programmatically. By following these simple steps, you can seamlessly integrate metadata manipulation capabilities into your .NET applications, enhancing the flexibility and functionality of your presentation processing tasks.

## FAQ's
### Can I retrieve existing custom properties from a presentation file using GroupDocs.Metadata for .NET?
Yes, you can retrieve existing custom properties using methods provided by the API. Refer to the documentation for more details.
### Does GroupDocs.Metadata support other file formats besides presentations?
Yes, GroupDocs.Metadata supports a wide range of file formats including Word documents, Excel spreadsheets, PDFs, images, and more.
### Is GroupDocs.Metadata for .NET suitable for both personal and commercial projects?
Yes, GroupDocs.Metadata can be used in both personal and commercial projects. Different licensing options are available for various project needs.
### How can I get technical support or assistance with GroupDocs.Metadata?
You can seek technical assistance and support via the GroupDocs.Metadata forum [here](https://forum.groupdocs.com/c/metadata/14).
### Can I try GroupDocs.Metadata for .NET before purchasing?
Yes, you can obtain a free trial of GroupDocs.Metadata from [here](https://releases.groupdocs.com/).
