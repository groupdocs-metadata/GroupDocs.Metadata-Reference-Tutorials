---
title: "Set PPTX CreatedTime in Java with GroupDocs Maven Dependency"
description: "Learn how to set pptx CreatedTime in Java using the GroupDocs Maven dependency to update PowerPoint metadata, including how to change PPTX creation date."
date: "2026-05-27"
weight: 1
url: "/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/"
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
type: docs
schemas:
- type: TechArticle
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  dateModified: '2026-05-27'
  author: GroupDocs
- type: HowTo
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
- type: FAQPage
  questions:
  - question: What is the primary purpose of the GroupDocs Maven dependency?
    answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
  - question: How can I set the PPTX creation date without affecting other properties?
    answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
  - question: Do I need a license to run this code in development?
    answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
  - question: Can I update custom metadata fields as well?
    answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
  - question: Is there a way to revert changes if I make a mistake?
    answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
---

# Set PPTX CreatedTime in Java with GroupDocs.Metadata

Accurate metadata is essential for compliance and discoverability in modern document workflows. With **GroupDocs.Metadata** you can programmatically **set PPTX CreatedTime in Java**, allowing you to **change PPTX creation date** alongside other built‑in properties such as author or company. This tutorial walks you through Maven setup, initializing the API, updating metadata, and saving the modified presentation—all with clear, production‑ready code.

## Quick Answers
- **Which library updates PowerPoint metadata in Java?** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **Can I set the PPTX CreatedTime property?** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Is a license required for production?** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **What build tool does the example use?** Maven (you can also download the JAR manually).  
- **Does the API support Java 8 and newer?** Absolutely—GroupDocs.Metadata targets Java 8+.

## What is the GroupDocs Maven Dependency?
The **GroupDocs Maven dependency** is a Maven‑compatible repository entry that pulls the latest GroupDocs.Metadata library into your Java project. It simplifies dependency management by automatically resolving transitive libraries, guarantees you always use the most recent and secure version, and eliminates the need for manual JAR downloads or version tracking.

## Why Use GroupDocs.Metadata to Change PPTX Creation Date?
GroupDocs.Metadata enables automated, batch‑ready updates of PPTX creation timestamps, ensuring every presentation complies with corporate policies or legal requirements. By programmatically setting the CreatedTime property you avoid manual editing, reduce human error, and can integrate the change into CI/CD pipelines or migration scripts for seamless document management.

## Prerequisites
- Java 8 or higher installed.  
- An IDE such as IntelliJ IDEA or Eclipse.  
- Maven for dependency handling.  
- Access to a GroupDocs trial or purchased license.

## How to set PPTX CreatedTime in Java?

The `Metadata` class represents a document and provides access to its metadata properties.

Load your PowerPoint file with `new Metadata("presentation.pptx")`, retrieve the root package, call `setCreatedTime` with the desired `java.util.Date`, and finally invoke `save` to write the changes. This end‑to‑end flow modifies the creation date while preserving all slide content and other properties.

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

The `root` object gives access to the presentation's core package and its built‑in properties.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

The `root` object exposes all the built‑in document properties.

### Step 3: Update Built‑In Document Properties (including creation date)

`setCreatedTime` assigns a new creation timestamp to the document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Here we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.

### Step 4: Save the Updated Presentation

`save` writes the modified metadata back to a file.

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

**Q: What is the primary purpose of the GroupDocs Maven dependency?**  
A: It provides a convenient way to include the latest GroupDocs.Metadata library in Maven‑based Java projects.

**Q: How can I set the PPTX creation date without affecting other properties?**  
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

**Last Updated:** 2026-05-27  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

---

## Related Tutorials

- [Update Custom Metadata in PowerPoint Using GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [How to Update Word Document Metadata Using GroupDocs.Metadata Java: A Complete Guide](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Efficiently Update PDF Metadata with GroupDocs.Metadata in Java for Document Management](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
