---
date: '2026-08-20'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 XMP metadata。本指南展示了如何提取 basic、Dublin
  Core 和 Photoshop XMP metadata。
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 XMP metadata。本教程涵盖 basic、Dublin
  Core 和 Photoshop XMP 的提取，并提供实用代码示例。
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: 如何使用 GroupDocs.Metadata for Java 提取 XMP metadata
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
title: 如何使用 GroupDocs.Metadata for Java 提取 XMP metadata
type: docs
url: /zh/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 GroupDocs.Metadata for Java 提取 XMP 元数据

在现代数字工作流中，快速可靠地 **提取 XMP** 元数据可以决定是拥有可搜索的资产库还是混乱的文件堆。本教程将逐步演示——设置库、加载文件以及提取基本、Dublin Core 和 Photoshop 特定的 XMP 包——帮助您今天就在 Java 应用中集成丰富的元数据。

## 快速答案
- **哪个库在 Java 中处理 XMP？** GroupDocs.Metadata for Java.
- **最低 Java 版本？** JDK 8 or later.
- **我可以读取 PNG 和 JPEG 文件吗？** Yes, both are supported out of the box.
- **生产环境是否需要许可证？** Yes, a full or temporary license is needed.
- **在哪里可以找到 API 参考？** On the official GroupDocs.Metadata documentation site.

## 什么是 XMP 元数据？
XMP（Extensible Metadata Platform）是一种 ISO 标准格式，用于将结构化元数据直接嵌入媒体文件内部。它实现了跨应用的互操作性和持久化数据存储，而无需更改原始内容。通过在文件中存储创作者、版权、相机设置和自定义标签等信息，XMP 确保元数据随资产一起移动，简化了跨系统的目录编制和搜索。

## 为什么使用 GroupDocs.Metadata for Java？
GroupDocs.Metadata 支持 **30+ 文件格式**（包括 PNG、JPEG、TIFF 和 PSD），并且能够在 **2 GB** 以内处理文件而无需将整个文档加载到内存中，相比通用解析器可实现 **30 % 的 CPU 使用率降低**。这使其非常适合大规模数字资产管理（DAM）系统。

## 前提条件

- **Java Development Kit (JDK) 8+** 已安装。
- **Maven** 用于依赖管理。
- 对 Java I/O 和面向对象编程有基本了解。

## 如何设置 GroupDocs.Metadata for Java？
首先，将 GroupDocs 仓库和库依赖添加到 Maven `pom.xml` 中。这可确保 Maven 能自动解析构件并保持最新，从而简化后续升级和安全补丁。更新 `pom.xml` 后，运行 `mvn clean install` 下载所需 JAR 并验证设置是否成功。

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

如果您更倾向于手动方式，可从官方发布页面下载最新的 JAR：

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### 许可证获取
- **Free trial** – evaluate all features for 30 days.
- **Temporary license** – use during development without restrictions.
- **Full license** – required for production deployments.

## 基本初始化

`Metadata` 是所有操作的入口点。它代表单个文件并提供对其嵌入的 XMP 包的访问。

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## 如何提取基本 XMP 元数据？

加载图像，打开其 XMP 包，并读取常见属性，如创建工具和时间戳。

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

## 如何提取 Dublin Core XMP 元数据？

Dublin Core 架构存储标准化的描述性元素，如标题、创作者和主题。通过 `DublinCorePackage` 类访问它。

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

## 如何提取 Photoshop 特定的 XMP 元数据？

Photoshop 会嵌入额外信息，如颜色模式、分辨率和图层计数。通过 `PhotoshopPackage` 检索这些值。

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

## 实际应用

- **Digital asset management** – tag and search images by creator, copyright, or camera settings.
- **Automated publishing pipelines** – inject or modify XMP before publishing to web galleries.
- **Analytics** – aggregate metadata across thousands of files to discover usage trends.

## 性能考虑

`Metadata` 类提供对文件元数据和 XMP 包的访问。读取完毕后尽快释放 `Metadata` 对象以释放本地资源。`LoadOptions.LAZY` 让库惰性加载元数据，降低内存占用。使用 `Metadata.load(InputStream)` 流式处理大文件以保持堆内存低。读取大量小文件时复用单个 `Metadata` 实例，可减少对象创建开销。

## 常见问题及排查

| 症状 | 可能原因 | 解决方法 |
|---|---|---|
| `NullPointerException` 在访问 XMP 时 | 文件没有 XMP 包 | 调用 `metadata.getXmpPackage()` 并在读取前检查是否为 `null`。`getXmpPackage()` 方法返回 XMP 包对象，若不存在则返回 null。 |
| 处理 500 MB 图像时速度慢 | 将整个文件加载到内存 | 使用 `metadata.load(InputStream)` 并启用 `metadata.setLoadOptions(LoadOptions.LAZY)`。 |
| 缺少 Photoshop 字段 | 图像未保存 Photoshop 图层信息 | 确认源文件是从 Photoshop 导出且勾选了 “Save XMP”。 |

## 常见问答

**Q:** 我可以从 PDF 文件中提取 XMP 吗？  
**A:** 可以，GroupDocs.Metadata 通过相同的 `Metadata` API 支持 PDF XMP 包。

**Q:** 如果文件格式不受支持会怎样？  
**A:** 库会抛出 `UnsupportedFormatException`；请捕获该异常并回退到通用处理器。

**Q:** 是否可以修改 XMP 元数据并保存回去？  
**A:** 完全可以。修改属性后，调用 `metadata.save("output.png")` 将更新持久化。

**Q:** 该库能在 Android 上使用吗？  
**A:** 核心 Java 库兼容 Android API 24+，但需引入 `android`‑specific 构件。

**Q:** 如何处理加密的图像？  
**A:** 在 `Metadata` 构造函数中提供解密密码，例如 `new Metadata(filePath, "password")`。

## 结论

您现在拥有一份完整的、可直接用于生产的 **提取 XMP** 元数据指南，使用 GroupDocs.Metadata for Java。按照上述步骤操作，即可为您的应用注入可搜索、符合标准的元数据，释放强大的资产管理能力。

## 下一步

深入阅读官方文档，探索完整功能集，并尝试其他元数据标准，如 IPTC 和 EXIF。

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

## 相关教程

- [Extract Dublin Core Metadata Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extract EXIF Software Tag in Java: A Complete Guide Using GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [How to Extract Metadata with GroupDocs.Metadata for Java – Tutorials & Examples](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}