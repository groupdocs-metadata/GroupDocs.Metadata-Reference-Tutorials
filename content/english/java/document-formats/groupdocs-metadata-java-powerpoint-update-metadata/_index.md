---
title: "Update PowerPoint Metadata with GroupDocs Maven Dependency"
description: "Learn how to use the GroupDocs Maven dependency to update PowerPoint metadata, including how to change PPTX creation date, with Java."
date: "2026-02-03"
weight: 1
url: "/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/"
keywords:
- update PowerPoint metadata Java
- GroupDocs.Metadata Java library
- presentation metadata management
type: docs
---

# How to Update Presentation Metadata with GroupDocs.Metadata Java

In modern document workflows, keeping metadata accurate is a must‑have. By leveraging the **groupdocs Maven dependency**, you can programmatically update built‑in properties of a PowerPoint file—such as author, company, and even the **change PPTX creation date**—directly from Java. This tutorial walks you through the entire process, from Maven setup to saving the updated presentation.

## Quick Answers
- **What library lets me edit PowerPoint metadata in Java?** GroupDocs.Metadata Java via the groupdocs Maven dependency.  
- **Can I change the PPTX creation date?** Yes—simply set the `CreatedTime` property.  
- **Do I need a license?** A free trial works for evaluation; a commercial license is required for production.  
- **Which build tool is supported?** Maven (shown below) or manual JAR download.  
- **Is the code compatible with Java 8+?** Absolutely—GroupDocs.Metadata targets Java 8 and newer.

## What is the GroupDocs Maven Dependency?
The **groupdocs Maven dependency** is a Maven‑compatible repository entry that pulls the latest GroupDocs.Metadata library into your Java project. It simplifies dependency management and ensures you always have the most recent, secure version.

## Why Use GroupDocs.Metadata to Change PPTX Creation Date?
- **Centralized control:** Update many presentations in a batch job.  
- **Compliance:** Keep creation timestamps aligned with your document‑management policies.  
- **No UI required:** Automate metadata changes during CI/CD pipelines or content migrations.

## Prerequisites
- Java 8 or higher installed.  
- An IDE such as IntelliJ IDEA or Eclipse.  
- Maven for dependency handling.  
- Access to a GroupDocs trial or purchased license.

## Using the GroupDocs Maven Dependency in Your Java Project

### Maven Setup
Add the GroupDocs repository and the metadata dependency to your `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/metadata/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-metadata</artifactId>
      <version>24.12</version>
   </dependency>
</dependencies>
```

> **Pro tip:** Keeping the version number up‑to‑date ensures you benefit from the latest bug fixes and performance improvements.

### Direct Download (if you prefer not to use Maven)

Alternatively, download the latest JAR from [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### License Acquisition

Start with a free trial or request a temporary license to evaluate GroupDocs.Metadata. For production use, purchase a license through [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/).

## Basic Initialization and Setup

Once the library is on the classpath, you can create a `Metadata` instance that points to your PowerPoint file:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

This code opens the presentation in a try‑with‑resources block, guaranteeing that the file handle is released automatically.

## Step‑by‑Step Guide to Update Built‑In Metadata

### Step 1: Load the Presentation Document

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Loading the file establishes a connection that lets you read or write metadata.

### Step 2: Access the Root Package of the Presentation

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

The `root` object exposes all the built‑in document properties.

### Step 3: Update Built‑In Document Properties (including creation date)

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Here we demonstrate how to **change PPTX creation date** by assigning a new `Date` object to `CreatedTime`. You can replace `new Date()` with any specific timestamp you need.

### Step 4: Save the Updated Presentation

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

The `save` call writes the modified metadata back to a new PowerPoint file, leaving the original untouched.

## Troubleshooting Tips
- **File Not Found:** Double‑check the input path and file permissions.  
- **Version Mismatch:** Ensure the `groupdocs-metadata` version matches your Java runtime.  
- **Property Not Updating:** Verify that you are calling `setCreatedTime` (or the relevant setter) before invoking `save`.

## Practical Applications

1. **Corporate Branding:** Automatically inject the correct company name and category into all slide decks before distribution.  
2. **Document Management Systems:** Enrich PPTX files with searchable metadata for faster retrieval.  
3. **Educational Resources:** Keep author and curriculum information up‑to‑date across lecture slides.  
4. **Collaboration Tracking:** Record contributors’ names to maintain accountability.  
5. **CMS Integration:** Sync metadata changes with your content management platform in real time.

## Performance Considerations
- **Batch Processing:** Loop over a list of files and reuse a single `Metadata` instance where possible.  
- **Memory Management:** Always use try‑with‑resources (as shown) to free native resources promptly.  
- **Efficient Data Structures:** Store metadata updates in a map before applying them to reduce repetitive calls.

## Frequently Asked Questions

**Q: What is the primary purpose of the groupdocs Maven dependency?**  
A: It provides a convenient way to include the latest GroupDocs.Metadata library in Maven‑based Java projects.

**Q: How can I change the PPTX creation date without affecting other properties?**  
A: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before calling `metadata.save()`.

**Q: Do I need a license to run this code in development?**  
A: A temporary trial license is sufficient for development and testing; a full license is required for production.

**Q: Can I update custom metadata fields as well?**  
A: Yes—GroupDocs.Metadata supports both built‑in and custom properties through its API.

**Q: Is there a way to revert changes if I make a mistake?**  
A: Keep a copy of the original file or read the existing property values before overwriting them, then restore if needed.

## Resources

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**Last Updated:** 2026-02-03  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

---