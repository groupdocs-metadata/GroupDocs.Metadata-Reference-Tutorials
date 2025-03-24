---
title: Read Built-In Properties from Spreadsheets in .NET
linktitle: Read Built-In Properties from Spreadsheets in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract metadata from spreadsheets in .NET using GroupDocs.Metadata, enhancing document management and organization in your applications.
weight: 10
url: /net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
---
## Introduction
In this tutorial, we will delve into how to utilize GroupDocs.Metadata for .NET to efficiently manage and extract metadata from spreadsheets. GroupDocs.Metadata for .NET is a powerful API that enables developers to work with metadata embedded in various file formats, including spreadsheets, presentations, documents, images, and more. This guide focuses specifically on extracting built-in properties from spreadsheet files using C#.
## Prerequisites
Before getting started, ensure you have the following prerequisites in place:
- Development Environment: Visual Studio or any C# compatible IDE.
- GroupDocs.Metadata for .NET Library: Download and install the library from the [website](https://releases.groupdocs.com/metadata/net/).
- Input File: Prepare a sample spreadsheet file (e.g., Excel) from which you want to extract metadata.

## Import Namespaces
Start by importing the necessary namespaces to access GroupDocs.Metadata functionalities within your C# project.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Step 1: Initialize Metadata and Retrieve Spreadsheet Root Package
Begin by initializing the `Metadata` object with your input file path. Then, obtain the root package specific to spreadsheets.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    // Access and retrieve built-in properties
}
```
## Step 2: Access Built-In Properties
Once you have the root package, you can access various built-in properties of the spreadsheet file using `DocumentProperties`.
### Step 2.1: Access Author Property
Retrieve the author (creator) of the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### Step 2.2: Access Created Time Property
Get the creation timestamp of the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### Step 2.3: Access Company Property
Fetch the company name associated with the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### Step 2.4: Access Category Property
Obtain the category information of the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### Step 2.5: Access Keywords Property
Retrieve the keywords associated with the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### Step 2.6: Access Language Property
Retrieve the language used in the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### Step 2.7: Access Content Type Property
Get the content type or MIME type of the spreadsheet.
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## Conclusion
In this tutorial, we explored how to use GroupDocs.Metadata for .NET to extract built-in properties from spreadsheet files using C#. By following these steps, you can seamlessly integrate metadata management into your .NET applications, enhancing file organization and retrieval capabilities.

## FAQ's
### Is GroupDocs.Metadata for .NET compatible with various file formats?
Yes, GroupDocs.Metadata supports a wide range of file formats including spreadsheets, documents, presentations, images, and more.
### Can I modify metadata using GroupDocs.Metadata for .NET?
Yes, you can not only read but also edit, update, and remove metadata using this API.
### Where can I find detailed documentation for GroupDocs.Metadata for .NET?
Detailed documentation is available at [GroupDocs.Metadata for .NET Documentation](https://tutorials.groupdocs.com/metadata/net/).
### How can I obtain a temporary license for testing purposes?
You can request a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Is there a community forum for GroupDocs.Metadata support?
Yes, you can visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14) for community support and discussions.
