---
title: Update Custom Properties in Diagrams using .NET
linktitle: Update Custom Properties in Diagrams using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to update custom properties in diagrams using .NET with GroupDocs.Metadata for .NET. Enhance metadata with ease.
weight: 15
url: /net/diagram-metadata/update-custom-properties-diagrams/
---

# Update Custom Properties in Diagrams using .NET

## Introduction
In this tutorial, we will explore how to update custom properties in diagrams using .NET with the help of GroupDocs.Metadata for .NET. Custom properties in diagrams can be essential for adding metadata or additional information to your files, enhancing their usability and organization. GroupDocs.Metadata for .NET provides a robust set of tools to manipulate and update metadata within various document formats, including diagrams.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
- Visual Studio: Install Visual Studio IDE on your machine.
- GroupDocs.Metadata for .NET: Download and install GroupDocs.Metadata for .NET from the [download page](https://releases.groupdocs.com/metadata/net/).
- Basic Knowledge of C#: Familiarity with C# programming language and .NET framework.

## Import Namespaces
Start by including the necessary namespaces in your C# project:
```csharp
using GroupDocs.Metadata.Formats.Document;
using System;
using GroupDocs.Metadata;
```
## Step 1: Load the Document
Begin by loading the diagram file from the specified input path using GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile"))
{
    var root = metadata.GetRootPackage<DiagramRootPackage>();
```
## Step 2: Set Custom Properties
Now, you can set custom properties within the document. Use the `DocumentProperties` object to add or update custom properties:
```csharp
    root.DocumentProperties.Set("customProperty1", "some value");
    root.DocumentProperties.Set("customProperty2", true);
```
Here, `"customProperty1"` and `"customProperty2"` are examples of custom property names that you can define based on your requirements. You can assign different types of values like strings, integers, booleans, etc., to these properties.
## Step 3: Save Changes
After setting the custom properties, save the changes back to the original file:
```csharp
    metadata.Save("YourInputFile");
}
```
This completes the process of updating custom properties in diagrams using .NET with GroupDocs.Metadata.

## Conclusion
In this tutorial, we learned how to leverage GroupDocs.Metadata for .NET to update custom properties in diagrams efficiently. Custom properties play a vital role in enriching the metadata associated with diagrams, making them more descriptive and structured.

## FAQ's
### What types of diagrams are supported by GroupDocs.Metadata for .NET?
GroupDocs.Metadata for .NET supports various diagram formats, including Microsoft Visio diagrams (VSD, VSDX), Drawings (VDX), and other common diagram formats.
### Can I retrieve existing custom properties from a diagram using this library?
Yes, you can easily retrieve existing custom properties from diagrams using GroupDocs.Metadata for .NET.
### Does GroupDocs.Metadata for .NET support batch processing of diagram files?
Yes, you can batch process multiple diagram files to update or retrieve metadata using GroupDocs.Metadata for .NET.
### Is there a trial version available for GroupDocs.Metadata for .NET?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### Where can I get support or ask questions related to GroupDocs.Metadata for .NET?
For any queries or support related to GroupDocs.Metadata for .NET, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
