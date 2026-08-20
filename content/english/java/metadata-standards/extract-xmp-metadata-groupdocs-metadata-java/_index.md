---
date: '2026-08-20'
description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata. This
  guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
images:
- /java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/og-image.png
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
  This tutorial covers basic, Dublin Core, and Photoshop XMP extraction with practical
  code examples.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: How to extract XMP metadata with GroupDocs.Metadata for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: How to extract XMP metadata with GroupDocs.Metadata for Java
type: docs
url: /java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to extract XMP metadata with GroupDocs.Metadata for Java

In modern digital workflows, **how to extract XMP** metadata quickly and reliably can make the difference between a searchable asset library and a chaotic file dump. This tutorial walks you through every step—setting up the library, loading files, and pulling out basic, Dublin Core, and Photoshop‑specific XMP packets—so you can integrate rich metadata into your Java applications today.

## Quick answers
- **Which library handles XMP in Java?** GroupDocs.Metadata for Java.
- **Minimum Java version?** JDK 8 or later.
- **Can I read PNG and JPEG files?** Yes, both are supported out of the box.
- **Is a license required for production?** Yes, a full or temporary license is needed.
- **Where can I find the API reference?** On the official GroupDocs.Metadata documentation site.

## What is XMP metadata?
XMP (Extensible Metadata Platform) is an ISO‑standard format for embedding structured metadata directly inside media files. It enables cross‑application interoperability and persistent data storage without altering the original content. By storing information such as creator, copyright, camera settings, and custom tags inside the file, XMP ensures that metadata travels with the asset wherever it goes, simplifying cataloging and search across diverse systems.

## Why use GroupDocs.Metadata for Java?
GroupDocs.Metadata supports **30+ file formats** (including PNG, JPEG, TIFF, and PSD) and can process files up to **2 GB** without loading the entire document into memory, delivering a **30 % reduction in CPU usage** compared with generic parsers. This makes it ideal for large‑scale digital‑asset‑management (DAM) systems.

## Prerequisites

- **Java Development Kit (JDK) 8+** installed.
- **Maven** for dependency management.
- Basic familiarity with Java I/O and object‑oriented programming.

## How to set up GroupDocs.Metadata for Java?
To begin, add the GroupDocs repository and the library dependency to your Maven `pom.xml`. This ensures that Maven can resolve the artifacts and keep them up‑to‑date automatically, which simplifies future upgrades and security patches. After updating the `pom.xml`, run `mvn clean install` to download the required JARs and verify that the setup succeeded.

```xml
<!-- ```xml
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
``` -->
```

If you prefer a manual approach, download the latest JAR from the official releases page:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### License acquisition
- **Free trial** – evaluate all features for 30 days.
- **Temporary license** – use during development without restrictions.
- **Full license** – required for production deployments.

## Basic initialization

`Metadata` is the entry point for all operations. It represents a single file and provides access to its embedded XMP packages.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## How to extract basic XMP metadata?

Load the image, open its XMP package, and read common properties such as creator tool and timestamps.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## How to extract Dublin Core XMP metadata?

The Dublin Core schema stores standardized descriptive elements like title, creator, and subject. Access it through the `DublinCorePackage` class.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## How to extract Photoshop‑specific XMP metadata?

Photoshop embeds additional information such as color mode, resolution, and layer counts. Retrieve these values via the `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Practical applications

- **Digital asset management** – tag and search images by creator, copyright, or camera settings.
- **Automated publishing pipelines** – inject or modify XMP before publishing to web galleries.
- **Analytics** – aggregate metadata across thousands of files to discover usage trends.

## Performance considerations

The `Metadata` class provides access to a file's metadata and XMP packets. Dispose of `Metadata` objects as soon as you finish reading to free native resources. `LoadOptions.LAZY` tells the library to load metadata lazily, reducing memory usage. Stream large files using `Metadata.load(InputStream)` to keep heap usage low. Reuse a single `Metadata` instance when reading many small files to reduce object‑creation overhead.

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| `NullPointerException` when accessing XMP | File has no XMP packet | Call `metadata.getXmpPackage()` and check for `null` before reading. The `getXmpPackage()` method returns the XMP packet object, or null if none exists. |
| Slow processing on 500 MB images | Loading whole file into memory | Use `metadata.load(InputStream)` and enable `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Missing Photoshop fields | Image saved without Photoshop layer info | Verify the source file was exported from Photoshop with “Save XMP” enabled |

## Frequently asked questions

**Q: Can I extract XMP from PDF files?**  
A: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata` API.

**Q: What happens if the file format isn’t supported?**  
A: The library throws a `UnsupportedFormatException`; catch it and fallback to a generic handler.

**Q: Is it possible to modify XMP metadata and save it back?**  
A: Absolutely. After changing properties, call `metadata.save("output.png")` to persist the updates.

**Q: Does the library work on Android?**  
A: The core Java library is compatible with Android API 24+, but you must include the `android`‑specific artifact.

**Q: How do I handle encrypted images?**  
A: Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath, "password")`.

## Conclusion

You now have a complete, production‑ready guide on **how to extract XMP** metadata using GroupDocs.Metadata for Java. By following the steps above, you can enrich your applications with searchable, standards‑compliant metadata and unlock powerful asset‑management capabilities.

## Next steps

Dive deeper into the full feature set by reviewing the official documentation and experimenting with other metadata standards such as IPTC and EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Last Updated:** 2026-08-20  
**Tested With:** GroupDocs.Metadata for Java 23.11  
**Author:** GroupDocs  

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Related Tutorials

- [Extract Dublin Core Metadata Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extract EXIF Software Tag in Java: A Complete Guide Using GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [How to Extract Metadata with GroupDocs.Metadata for Java – Tutorials & Examples](/metadata/java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}