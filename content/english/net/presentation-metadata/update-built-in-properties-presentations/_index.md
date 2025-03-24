---
title: Update Built-In Properties in Presentations using .NET
linktitle: Update Built-In Properties in Presentations using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to update built-in properties in presentations using .NET with GroupDocs.Metadata, a versatile metadata manipulation library.
weight: 15
url: /net/presentation-metadata/update-built-in-properties-presentations/
---

# Update Built-In Properties in Presentations using .NET

## Introduction
In this tutorial, we'll delve into the powerful capabilities of GroupDocs.Metadata for .NET, a comprehensive library designed to manipulate metadata within documents using the .NET framework. Specifically, we'll focus on updating built-in properties in presentations (.PPT and .PPTX files) programmatically using C#.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio: Installed on your system.
- GroupDocs.Metadata for .NET: Downloaded and installed from [here](https://releases.groupdocs.com/metadata/net/).
- Basic C# Knowledge: Familiarity with C# programming language.

## Import Namespaces
Start by importing the necessary namespaces into your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Load the Presentation File
First, create a new instance of `Metadata` by loading your presentation file:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Step 2: Update Built-In Properties
Now, update the desired built-in properties of the presentation. For example, you can modify the author, creation date, company, category, keywords, etc. Here's how you can do it:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Step 3: Save Changes
After updating the properties, save the changes back to the presentation file:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Conclusion
In this tutorial, we explored how to use GroupDocs.Metadata for .NET to update built-in properties in presentation files programmatically. By following these steps, you can efficiently manage and modify metadata within your .NET applications.

## FAQ's
### Q: What is GroupDocs.Metadata for .NET?
A: GroupDocs.Metadata for .NET is a powerful metadata manipulation library for the .NET framework, allowing developers to read, write, and edit metadata in various document formats.
### Q: Where can I find documentation for GroupDocs.Metadata?
A: You can access the detailed documentation [here](https://tutorials.groupdocs.com/metadata/net/).
### Q: How can I obtain a temporary license for GroupDocs.Metadata?
A: You can acquire a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### Q: Does GroupDocs.Metadata support other file formats besides presentations?
A: Yes, GroupDocs.Metadata supports a wide range of formats including documents, spreadsheets, images, videos, and more.
### Q: Where can I get support or ask questions about GroupDocs.Metadata?
A: For support and discussions, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
