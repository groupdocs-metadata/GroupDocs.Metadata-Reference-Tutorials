---
title: Read Lyrics Tag from MP3 Files in .NET
linktitle: Read Lyrics Tag from MP3 Files in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to extract lyrics tags from MP3 files using GroupDocs.Metadata for .NET. Follow our step-by-step tutorial.
weight: 13
url: /net/audio-metadata/read-lyrics-tag-mp3/
---

# Read Lyrics Tag from MP3 Files in .NET

## Introduction
In this tutorial, we will learn how to extract and read lyrics tags from MP3 files using the GroupDocs.Metadata API in .NET. GroupDocs.Metadata is a powerful library that allows developers to work with metadata associated with various file formats, including MP3 files. By following these steps, you'll be able to efficiently retrieve lyrics-related information embedded within MP3 files.
## Prerequisites
Before we begin, ensure you have the following prerequisites set up:
- Visual Studio installed on your machine.
- Basic knowledge of C# programming language.
- GroupDocs.Metadata library for .NET. You can download it [here](https://releases.groupdocs.com/metadata/net/).
- Access to an MP3 file containing lyrics tags for testing.

## Import Namespaces
First, include the necessary namespaces in your C# project:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## Step 1: Load the MP3 File
Begin by initializing a `Metadata` object with your input MP3 file path:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // Retrieve the root package for MP3 format
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## Step 2: Access Lyrics Tags
Check if the MP3 file contains Lyrics3V2 tags and retrieve the associated information:
```csharp
    if (root.Lyrics3V2 != null)
    {
        // Output specific tag fields
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## Step 3: Loop Through All Tag Fields
Alternatively, you can loop through all available tag fields within Lyrics3V2:
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## Conclusion
In this tutorial, we explored how to extract and read Lyrics tags from MP3 files using GroupDocs.Metadata for .NET. By following these steps, you can effectively retrieve lyrics-related metadata embedded within your MP3 files for further processing or display in your applications.

## FAQ's
### Can I modify or update the lyrics tags using GroupDocs.Metadata?
Yes, GroupDocs.Metadata allows you to update and modify metadata within MP3 files, including lyrics tags.
### Does GroupDocs.Metadata support other audio formats besides MP3?
Yes, GroupDocs.Metadata supports a wide range of audio and video formats for metadata extraction and manipulation.
### Where can I find more detailed documentation for GroupDocs.Metadata?
You can access the full documentation [here](https://tutorials.groupdocs.com/metadata/net/).
### Is there a free trial available for GroupDocs.Metadata?
Yes, you can get a free trial version [here](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Metadata?
For technical assistance, you can visit the GroupDocs.Metadata support forum [here](https://forum.groupdocs.com/c/metadata/14).
