---
title: Update Built-In Properties in Diagrams using .NET
linktitle: Update Built-In Properties in Diagrams using .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to update built-in properties in diagrams using GroupDocs.Metadata for .NET. Modify metadata seamlessly with code examples.
weight: 14
url: /net/diagram-metadata/update-built-in-properties-diagrams/
---
## Introduction
In this tutorial, we'll explore how to update built-in properties in diagrams using GroupDocs.Metadata for .NET. This library allows you to manipulate metadata within various document formats, including diagrams. We'll cover the prerequisites, necessary namespaces, and provide a step-by-step guide with code examples to update these properties effectively.

## Prerequisites

Before you begin, ensure you have the following:

- Visual Studio: Installed on your machine.
- GroupDocs.Metadata for .NET: Downloaded and added as a tutorials to your project.
- Basic knowledge of C#: Understanding of C# programming language.

## Import Namespaces

Start by importing the necessary namespaces to access the GroupDocs.Metadata library functionalities:

```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```

Let's break down the process of updating built-in properties in diagrams using GroupDocs.Metadata into multiple steps:

## Step 1: Initialize Metadata Object

Begin by initializing a `Metadata` object with the path to your input diagram file:

```csharp
using (Metadata metadata = new Metadata("Your Input File"))
{
    var root = metadata.GetRootPackage<DiagramRootPackage>();
```

## Step 2: Update Document Properties

Now, access and modify the desired built-in properties of the diagram:

```csharp
root.DocumentProperties.Creator = "test author";
root.DocumentProperties.TimeCreated = DateTime.Now;
root.DocumentProperties.Company = "GroupDocs";
root.DocumentProperties.Category = "test category";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```

You can set properties like `Creator`, `TimeCreated`, `Company`, `Category`, `Keywords`, etc., based on your requirements.

## Step 3: Save Changes

Finally, save the updated metadata back to the diagram file:

```csharp
metadata.Save("Your Input File");
```

## Conclusion

By following these steps, you can efficiently update built-in properties within diagrams using GroupDocs.Metadata for .NET. This approach enables you to manage metadata seamlessly, ensuring accurate and relevant information is associated with your diagram files.


## FAQ's

### Q: Can I modify other metadata properties apart from built-in ones?
A: Yes, GroupDocs.Metadata for .NET supports editing various metadata properties like EXIF, IPTC, XMP, and custom properties.

### Q: Is there a trial version available to test before purchasing?
A: Yes, you can download a free trial from [here](https://releases.groupdocs.com/).

### Q: How can I get technical support for GroupDocs.Metadata for .NET?
A: You can visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14) for assistance.

### Q: Where can I find detailed documentation for GroupDocs.Metadata for .NET?
A: Refer to the comprehensive [documentation](https://tutorials.groupdocs.com/metadata/net/) for in-depth guidance.

### Q: Can I purchase a temporary license for short-term usage?
A: Yes, you can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
