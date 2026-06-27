---
date: '2026-06-27'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 获取文件创建时间戳并提取 PowerPoint 演示文稿的其他文档属性。非常适合文档管理和合规性。
keywords:
- java get file creation timestamp
- java extract document properties
- GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  headline: How to java get file creation timestamp from Presentation Files Using
    GroupDocs.Metadata
  type: TechArticle
- description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  name: How to java get file creation timestamp from Presentation Files Using GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
    text: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
  - name: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
    text: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
  - name: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
    text: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
  - name: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
    text: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
  type: HowTo
- questions:
  - answer: 'The API returns `null` for unset fields. Use a conditional expression
      like `(author != null ? author : "N/A")` to provide a fallback value.'
    question: How do I handle missing metadata properties?
  - answer: Yes, beyond the built‑in properties you can read and write custom key/value
      pairs using the same API.
    question: Can GroupDocs.Metadata extract custom metadata fields?
  - answer: GroupDocs.Metadata works with PowerPoint (`.ppt`, `.pptx`) and also supports
      PDF, Word, Excel, and many image formats.
    question: Is there support for other presentation formats?
  - answer: A compatible JDK (8 or higher) and sufficient heap memory for the size
      of the documents you process (e.g., 1 GB heap for 500‑page presentations).
    question: What are the system requirements for GroupDocs.Metadata Java?
  - answer: 'Visit the official support forum for assistance: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)'
    question: Where can I get help if I run into problems?
  type: FAQPage
title: 如何在 Java 中使用 GroupDocs.Metadata 获取演示文件的创建时间戳
type: docs
url: /zh/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 从演示文件中获取文件创建时间戳（Java）

管理元数据是现代文档工作流的基石，而 **java get file creation timestamp** 通常是验证文件来源的第一条信息。在本分步指南中，您将学习如何读取 PowerPoint 演示文稿的创建时间戳，提取作者、公司、关键字等附加属性，并将结果集成到任何基于 Java 的解决方案中——无论是文档管理系统、审计轨迹生成器，还是合规仪表盘。

## 快速答案
- **“java get file creation timestamp” 是什么意思？** 通过 Java 代码使用元数据 API 检索文件的原始创建日期。  
- **哪个库负责此功能？** GroupDocs.Metadata for Java 提供了干净、与格式无关的 API 用于读取时间戳和其他内置属性。  
- **生产环境需要许可证吗？** 是的，生产环境必须使用永久许可证；免费试用版足以用于开发和测试。  
- **可以一次提取其他元数据吗？** 当然——作者、公司、类别、关键字以及自定义字段都可以通过同一 API 访问。  
- **支持的 Java 版本是什么？** JDK 8 或更高（兼容 Java 11、 17 及以后版本）。

## 什么是 “java get file creation timestamp”？
`java get file creation timestamp` 指的是访问文档内部存储的 **Created** 元数据字段的操作，该字段记录文件首次生成的确切时刻。此时间戳对版本控制、审计轨迹和合规性至关重要，因为它提供了内容产生时间的不可变记录。

## 为什么使用 GroupDocs.Metadata for Java 提取文档属性？
GroupDocs.Metadata 抽象了数十种文件格式的底层解析，让您专注于业务逻辑。它支持 **超过 50 种输入和输出格式**——包括 .pptx、 .ppt、 .pdf、 .docx、 .xlsx 以及多种图像类型，并且能够在不将整个文件加载到内存的情况下处理数百页的演示文稿，为大规模环境提供内存高效的解决方案。

## 前置条件
- **GroupDocs.Metadata for Java** 版本 24.12 或更高。  
- Java Development Kit (JDK 8 或更新)。  
- IntelliJ IDEA 或 Eclipse 等 IDE。  
- 对 Java 文件 I/O 与异常处理有基本了解。

## 设置 GroupDocs.Metadata for Java

### Maven 设置
如果使用 Maven 管理依赖，请在 `pom.xml` 中添加仓库和依赖：

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

### 直接下载
或者，您可以从官方发布页面下载库：  
[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

#### 许可证获取步骤
- **免费试用：** 首先使用免费试用以探索 API。  
- **临时许可证：** 获取临时密钥以进行无限制测试。  
- **购买：** 为生产部署获取完整许可证。

### 基本初始化和设置
`Metadata` 是 GroupDocs.Metadata for Java 的主要入口类，提供对文档元数据的访问。依赖就位后，创建一个 `Metadata` 对象并指向您的演示文件：

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## 如何 java get file creation timestamp 并从演示文稿中提取其他属性？
使用 `new Metadata("sample.pptx")` 加载演示文稿，然后调用相应的 getter 方法——`getCreatedTime()`、`getAuthor()`、`getCompany()` 等——即可获取每项信息。这种单对象方式让您只需几行代码即可拉取所有内置属性，免去格式特定解析器的需求。

### 提取作者信息
`getAuthor()` 返回文档元数据中存储的作者名称，如果字段为空则返回 `null`。

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*该方法返回普通的 `String`，您可以将其记录、显示或存入数据库。*

### 提取创建时间（java get file creation timestamp）
`getCreatedTime()` 提供一个 `java.util.Date` 对象，表示文件首次创建的确切时刻——正是 “java get file creation timestamp” 所描述的内容。

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*您可以使用 `SimpleDateFormat` 或更现代的 `java.time` API 对该 `Date` 进行格式化，以便显示或比较。*

### 提取公司信息
`getCompany()` 返回与演示文稿关联的组织名称，如果字段未设置则返回 `null`。

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*该值对于将文档关联到企业记录或 CRM 实体非常有用。*

### 其他可提取的元数据
您同样可以使用 `getCategory()`、`getKeywords()`、`getLastPrinted()`、`getApplicationName()` 等方法检索 **Category**、**Keywords**、**Last Printed Date**、**Application Name** 等内置字段。每个 getter 都遵循相同模式：返回简洁、空安全的值，随时可用。

## 实际应用场景
1. **文档管理系统：** 按作者、公司或创建日期对演示文稿建立索引，实现快速搜索与检索。  
2. **合规审计：** 确保每个归档的幻灯片文件在存入法律保留库前都包含创建时间戳。  
3. **自动化报告：** 生成每日摘要，列出每个演示文稿的创建者和创建时间，并将数据推送至 BI 仪表盘。  
4. **CRM 集成：** 将 `Company` 元数据与现有客户记录匹配，实现演示文稿与客户档案的无缝关联。

## 性能考虑
- **并行处理：** 在成千上万的文件上提取元数据时，可为每个提取任务启动独立线程或使用线程池，以最大化 CPU 利用率。  
- **资源管理：** 如示例所示使用 try‑with‑resources 自动关闭 `Metadata` 对象并释放本机资源。  
- **批量提取：** GroupDocs.Metadata 支持批量操作；遍历文件路径集合时尽可能复用单个 `Metadata` 实例，以降低开销。

## 常见问题及解决方案
- **元数据缺失：** 如果 getter 返回 `null`，说明源文件根本没有该属性。请使用条件检查或默认回退来防止空指针。  
- **不支持的格式：** 确认文件是受支持的 PowerPoint 格式（`.pptx` 或 `.ppt`）。加载不受支持的类型会抛出 `UnsupportedFormatException`。  
- **许可证错误：** 确保许可证文件已正确放置在类路径上，或试用期未过期；否则 API 会抛出 `LicenseException`。

## 常见问答

**Q: 如何处理缺失的元数据属性？**  
A: API 对未设置的字段返回 `null`。可使用类似 `(author != null ? author : "N/A")` 的条件表达式提供回退值。

**Q: GroupDocs.Metadata 能提取自定义元数据字段吗？**  
A: 可以，除了内置属性外，您还可以使用相同的 API 读取和写入自定义键/值对。

**Q: 是否支持其他演示文稿格式？**  
A: GroupDocs.Metadata 支持 PowerPoint（`.ppt`、`.pptx`），同时也兼容 PDF、Word、Excel 以及多种图像格式。

**Q: GroupDocs.Metadata Java 的系统要求是什么？**  
A: 兼容的 JDK（8 或更高）以及足够的堆内存以处理文档大小（例如，处理 500 页演示文稿时建议 1 GB 堆）。

**Q: 遇到问题时可以在哪里获取帮助？**  
A: 访问官方支持论坛获取帮助：[GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## 资源

- **文档：** https://docs.groupdocs.com/metadata/java/
- **API 参考：** https://reference.groupdocs.com/metadata/java/
- **下载：** https://releases.groupdocs.com/metadata/java/
- **GitHub：** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
- **免费支持：** https://forum.groupdocs.com/c/metadata/
- **临时许可证：** https://purchase.groupdocs.com/temporary-license/

通过本指南，您现在了解了如何 **java get file creation timestamp** 并 **java extract document properties**，从 PowerPoint 演示文稿中使用 GroupDocs.Metadata 提取元数据。将这些代码片段集成到项目中，可提升文档智能、简化合规工作流，并为下游分析提供支持。

---

**最后更新：** 2026-06-27  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

## 相关教程

- [How to Extract Metadata from PowerPoint Presentations Using GroupDocs.Metadata in Java](/metadata/java/working-with-metadata/extract-presentation-metadata-groupdocs-java/)
- [Automate Java Metadata Updates by Date Using GroupDocs.Metadata for Efficient File Management](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)
- [Master Metadata Management: Detect Document Properties & Encryption Status with GroupDocs.Metadata for Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)