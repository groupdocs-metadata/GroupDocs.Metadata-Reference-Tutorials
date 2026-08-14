---
date: '2026-05-27'
description: 了解如何在 Java 中使用 GroupDocs Maven 依赖设置 PPTX CreatedTime，以更新 PowerPoint 元数据，包括如何更改
  PPTX 创建日期。
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
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
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: 在 Java 中使用 GroupDocs Maven 依赖设置 PPTX CreatedTime
type: docs
url: /zh/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# 在 Java 中使用 GroupDocs.Metadata 设置 PPTX CreatedTime

准确的元数据对于现代文档工作流中的合规性和可检索性至关重要。使用 **GroupDocs.Metadata**，您可以以编程方式 **在 Java 中设置 PPTX CreatedTime**，从而能够 **更改 PPTX 创建日期**，以及作者或公司等其他内置属性。本教程将引导您完成 Maven 设置、API 初始化、元数据更新以及保存修改后的演示文稿的全过程——全部使用清晰、可用于生产的代码。

## 快速答复
- **哪个库在 Java 中更新 PowerPoint 元数据？** GroupDocs.Metadata 通过 GroupDocs Maven 依赖。  
- **我可以设置 PPTX CreatedTime 属性吗？** 可以——使用 `root.getDocumentProperties().setCreatedTime(yourDate)`。  
- **生产环境是否需要许可证？** 试用版可用于评估；商业许可证是生产部署的必需。  
- **示例使用的构建工具是什么？** Maven（您也可以手动下载 JAR）。  
- **API 是否支持 Java 8 及更高版本？** 当然——GroupDocs.Metadata 目标是 Java 8+。

## 什么是 GroupDocs Maven 依赖？

**GroupDocs Maven 依赖** 是一个兼容 Maven 的仓库条目，可将最新的 GroupDocs.Metadata 库拉入您的 Java 项目。它通过自动解析传递依赖简化了依赖管理，确保您始终使用最新且安全的版本，并消除手动下载 JAR 或版本跟踪的需求。

## 为什么使用 GroupDocs.Metadata 更改 PPTX 创建日期？

GroupDocs.Metadata 能够实现自动化、批量就绪的 PPTX 创建时间戳更新，确保每个演示文稿符合公司政策或法律要求。通过以编程方式设置 CreatedTime 属性，您可以避免手动编辑、降低人为错误，并且可以将此更改集成到 CI/CD 流水线或迁移脚本中，实现无缝的文档管理。

## 前提条件
- 已安装 Java 8 或更高版本。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 用于依赖管理的 Maven。  
- 可使用 GroupDocs 试用版或已购买的许可证。

## 如何在 Java 中设置 PPTX CreatedTime？

`Metadata` 类表示一个文档并提供对其元数据属性的访问。

使用 `new Metadata("presentation.pptx")` 加载 PowerPoint 文件，获取根包，使用所需的 `java.util.Date` 调用 `setCreatedTime`，最后调用 `save` 写入更改。此端到端流程在保留所有幻灯片内容和其他属性的同时修改创建日期。

### Maven 设置
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

> **技巧提示：** 保持版本号为最新可确保您受益于最新的错误修复和性能改进。

### 直接下载（如果您不想使用 Maven）

或者，从 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下载最新的 JAR。

#### 许可证获取

先使用免费试用或请求临时许可证来评估 GroupDocs.Metadata。生产使用时，请通过 [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/) 购买许可证。

## 基本初始化和设置

一旦库位于类路径上，您即可创建指向 PowerPoint 文件的 `Metadata` 实例：

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

此代码在 try‑with‑resources 块中打开演示文稿，确保文件句柄自动释放。

## 步骤指南：更新内置元数据

### 步骤 1：加载演示文稿

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

加载文件会建立一个连接，使您能够读取或写入元数据。

### 步骤 2：访问演示文稿的根包

The `root` object gives access to the presentation's core package and its built‑in properties.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` 对象公开所有内置的文档属性。

### 步骤 3：更新内置文档属性（包括创建日期）

`setCreatedTime` assigns a new creation timestamp to the document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

这里演示如何通过将新的 `Date` 对象赋给 `CreatedTime` 来 **设置 PPTX CreatedTime**。将 `new Date()` 替换为您需要的任何特定时间戳。

### 步骤 4：保存更新后的演示文稿

`save` writes the modified metadata back to a file.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` 调用将修改后的元数据写回新的 PowerPoint 文件，原文件保持不变。

## 故障排除技巧
- **文件未找到：** 仔细检查输入路径和文件权限。  
- **版本不匹配：** 确保 `groupdocs-metadata` 版本与您的 Java 运行时匹配。  
- **属性未更新：** 确认在调用 `save` 之前已调用 `setCreatedTime`（或相应的 setter）。

## 实际应用
1. **企业品牌化：** 在分发前自动将正确的公司名称和类别注入所有幻灯片。  
2. **文档管理系统：** 为 PPTX 文件添加可搜索的元数据，以加快检索。  
3. **教育资源：** 在讲义幻灯片中保持作者和课程信息的最新。  
4. **协作追踪：** 记录贡献者姓名以保持问责。  
5. **CMS 集成：** 实时将元数据更改同步到您的内容管理平台。

## 性能考虑因素
- **批处理：** 循环处理文件列表，并在可能的情况下重用单个 `Metadata` 实例。  
- **内存管理：** 始终使用 try‑with‑resources（如示例所示）及时释放本机资源。  
- **高效数据结构：** 在应用之前将元数据更新存储在映射中，以减少重复调用。

## 常见问题

**Q: GroupDocs Maven 依赖的主要目的是什么？**  
A: 它提供了一种便捷方式，将最新的 GroupDocs.Metadata 库包含在基于 Maven 的 Java 项目中。

**Q: 如何在不影响其他属性的情况下设置 PPTX 创建日期？**  
A: 在调用 `metadata.save()` 之前使用 `root.getDocumentProperties().setCreatedTime(yourDesiredDate)`。

**Q: 在开发中运行此代码是否需要许可证？**  
A: 临时试用许可证足以用于开发和测试；生产环境需要完整许可证。

**Q: 我还能更新自定义元数据字段吗？**  
A: 可以——GroupDocs.Metadata 通过其 API 支持内置和自定义属性。

**Q: 如果出现错误，有办法恢复更改吗？**  
A: 保留原文件的副本或在覆盖之前读取现有属性值，然后在需要时恢复。

## 资源

- [文档](https://docs.groupdocs.com/metadata/java/)
- [API 参考](https://apireference.groupdocs.com/metadata/java/)

---

**最后更新：** 2026-05-27  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

## 相关教程

- [使用 GroupDocs.Metadata Java API 更新 PowerPoint 自定义元数据](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [使用 GroupDocs.Metadata Java 更新 Word 文档元数据：完整指南](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [在 Java 中使用 GroupDocs.Metadata 高效更新 PDF 元数据以进行文档管理](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)