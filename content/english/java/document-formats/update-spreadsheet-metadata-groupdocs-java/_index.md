---
title: "Change Excel Creation Date Using GroupDocs.Metadata in Java"
description: "Learn how to change Excel creation date and update Excel metadata using GroupDocs.Metadata for Java. Follow this step‑by‑step guide to add keywords to Excel and modify document properties."
date: "2026-03-22"
weight: 1
url: "/java/document-formats/update-spreadsheet-metadata-groupdocs-java/"
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
type: docs
---

# Change Excel Creation Date Using GroupDocs.Metadata in Java

In modern data‑driven environments, **changing the Excel creation date** and keeping other metadata up‑to‑date can dramatically improve document organization, searchability, and compliance. Whether you’re handling financial reports, project trackers, or archival data, accurate metadata ensures that the right people find the right files at the right time. This tutorial walks you through using the GroupDocs.Metadata library to **change Excel creation date**, **add keywords to Excel**, and **modify Excel document properties** in a Java application.

## Quick Answers
- **Can I change the creation date of an Excel file?** Yes, using `setCreatedTime` from GroupDocs.Metadata.  
- **Which library supports updating Excel metadata in Java?** GroupDocs.Metadata for Java.  
- **Do I need a license?** A free trial works for evaluation; a permanent license is required for production.  
- **What Java version is required?** JDK 8 or higher.  
- **Can I add custom keywords to an Excel workbook?** Absolutely—use `setKeywords` on the document properties.

## What is “change Excel creation date”?
Changing the Excel creation date means updating the built‑in *Created* property stored inside the workbook file. This property is part of the standard Office Open XML metadata and can be edited programmatically without altering the actual worksheet content.

## Why use GroupDocs.Metadata for Excel metadata?
GroupDocs.Metadata offers a high‑level, type‑safe API that abstracts the low‑level XML handling required by the Office Open XML format. It lets you:

- **Update core properties** such as author, company, and creation date in a single call.  
- **Add keywords to Excel** to improve search results in SharePoint, OneDrive, or local file systems.  
- **Modify Excel document properties** without opening the workbook in Excel, which saves time and resources.  

## Prerequisites
- Java Development Kit (JDK) 8 or newer.  
- An IDE like IntelliJ IDEA or Eclipse.  
- Basic familiarity with Java file I/O.  

## Setting Up GroupDocs.Metadata for Java

### Installation

Add the GroupDocs.Metadata Maven repository and dependency to your `pom.xml`:

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

Alternatively, you can [download the latest version directly](https://releases.groupdocs.com/metadata/java/) if you prefer a manual setup.

### License Acquisition

GroupDocs offers a free trial for evaluation. For production use, obtain a temporary or permanent license from the vendor. Visit [GroupDocs' purchase page](https://purchase.groupdocs.com/temporary-license/) for details.

#### Basic Initialization

Import the necessary classes in your Java source file:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Step‑by‑Step Implementation

### Step 1: Open the Excel Workbook

Provide the path to the source workbook and create a `Metadata` instance. The `try‑with‑resources` block ensures the file handle is closed automatically.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Step 2: Update Built‑In Metadata Properties

Now you can **change the Excel creation date**, set the author, company, category, and **add keywords to Excel**. The `new Date()` call captures the current timestamp, but you can supply any `java.util.Date` you need.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Pro tip:** Use a consistent naming convention for keywords (e.g., `project:Q2, finance, confidential`) to make future searches more effective.

### Step 3: Save the Updated Workbook

Specify an output path and persist the changes. The original file remains untouched, which is useful for audit trails.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Common Issues and Solutions

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **File path errors** | Incorrect relative/absolute paths | Double‑check the `inputFilePath` and `outputFilePath`. Use `Paths.get(...)` for platform‑independent paths. |
| **Incompatible library version** | Using an older GroupDocs.Metadata that doesn’t support the `setCreatedTime` method | Upgrade to the latest version (as shown in the Maven snippet). |
| **Missing license** | Trial period expired | Apply a temporary license or purchase a full license via the purchase page. |
| **Large workbook memory usage** | Loading massive Excel files consumes heap space | Process files in batches and increase JVM heap (`-Xmx`) if necessary. |

## Frequently Asked Questions

**Q: What Java versions are supported by GroupDocs.Metadata?**  
A: Java 8 and newer are fully supported.

**Q: How should I handle exceptions when updating metadata?**  
A: Wrap the code in a `try‑catch` block and log `MetadataException` to capture any I/O or format errors.

**Q: Can I update multiple Excel files in one run?**  
A: Yes, iterate over a collection of file paths, but monitor memory usage for large batches.

**Q: Is it possible to revert the changes made to metadata?**  
A: Keep a backup of the original workbook before applying updates, then restore it if needed.

**Q: Where can I find more detailed documentation?**  
A: See the official guide at [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Practical Applications

1. **Financial Audits** – Record who modified a workbook and when, providing an audit trail.  
2. **Project Management** – Tag spreadsheets with project‑specific keywords for quick retrieval.  
3. **Data Archiving** – Preserve original creation dates and company information for compliance.

## Performance Tips

- Limit metadata operations per run to avoid excessive memory consumption.  
- Close the `Metadata` object promptly (the `try‑with‑resources` pattern does this automatically).  
- For very large workbooks, consider processing them on a background thread to keep the UI responsive.

## Conclusion

You now know how to **change Excel creation date**, **add keywords to Excel**, and **modify Excel document properties** using GroupDocs.Metadata in Java. This capability empowers you to keep your spreadsheets well‑organized, searchable, and compliant with internal governance policies. As a next step, explore other metadata features such as custom properties or batch processing to further streamline your document management workflow.

---

**Last Updated:** 2026-03-22  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

**Resources**
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)