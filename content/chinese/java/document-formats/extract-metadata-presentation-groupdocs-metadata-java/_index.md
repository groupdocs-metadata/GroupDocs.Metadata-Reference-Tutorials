---
date: '2026-01-26'
description: 了解如何使用 GroupDocs.Metadata for Java 读取 PowerPoint 演示文稿的创建时间并提取其他文档属性。非常适合文档管理和合规。
keywords:
- read created time java
- java extract document properties
- presentation metadata
title: 使用 GroupDocs.Metadata 从演示文件读取创建时间（Java）——一步步指南
type: docs
url: /zh/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 从演示文件读取创建时间（java）

管理元数据是现代文档工作流的基石。在本教程中，您将学习 **如何读取创建时间（java）** 并从 PowerPoint 演示文稿中提取其他有用属性——如作者、公司和关键字——使用 **GroupDocs.Metadata for Java**。完成后，您即可将这些细节集成到文档管理系统、合规报告或任何需要了解文件来源的基于 Java 的应用程序中。

## 快速答案
- **“read created time java” 是什么意思？** 通过 Java 代码检索文件的创建时间戳的过程。  
- **哪个库支持此功能？** GroupDocs.Metadata for Java 提供了简洁的 API 来访问所有内置的演示属性。  
- **需要许可证吗？** 免费试用可用于开发；生产环境需要正式许可证。  
- **可以同时提取其他属性吗？** 可以——作者、公司、类别等都可以通过同一 API 获取。  
- **需要哪个 Java 版本？** JDK 8 或更高。

## 什么是 “read created time java”？
在 Java 中读取文档的创建时间是指访问存储文件最初生成时间的元数据字段。该时间戳对于版本控制、审计追踪和合规验证至关重要。

## 为什么使用 GroupDocs.Metadata for Java 提取文档属性？
GroupDocs.Metadata 抽象了不同文件格式的复杂性，让您专注于业务逻辑，而不是底层解析。它支持 PowerPoint、PDF、Word 以及多种图像格式，是任何需要 **java extract document properties** 的 Java 项目的多功能选择。

## 前置条件
- **GroupDocs.Metadata for Java** 版本 24.12 或更高。  
- Java Development Kit (JDK 8 或更新)。  
- IntelliJ IDEA 或 Eclipse 等 IDE。  
- 基本的 Java 文件处理知识。

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
- **免费试用：** 开始免费试用以探索 API。  
- **临时许可证：** 获取临时密钥以进行无限制测试。  
- **购买：** 为生产部署获取完整许可证。

### 基本初始化和设置
依赖配置完成后，创建一个 `Metadata` 对象并指向您的演示文件：

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## 如何 java extract document properties from a presentation
下面我们逐步演示最常用的内置属性，展示如何读取它们。

### 提取作者信息
**概述：** 获取创建演示文稿的人的姓名。

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*`getAuthor()` 方法返回作者字符串，如果字段为空则返回 `null`。*

### 提取创建时间（read created time java）
**概述：** 获取指示文件首次创建时间的时间戳。

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*`getCreatedTime()` 提供一个 `java.util.Date` 对象，表示创建时刻——这正是 “read created time java” 所指的内容。*

### 提取公司信息
**概述：** 获取与演示文稿关联的组织名称。

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*`getCompany()` 方法返回公司元数据，如果未设置则返回 `null`。*

### 其他可提取的元数据
您同样可以使用 `getCategory()`、`getKeywords()` 等方法检索 **Category**、**Keywords**、**Last Printed Date**、**Application Name** 等内置字段。

## 实际应用场景
1. **文档管理系统：** 按作者、公司或创建日期为演示文稿建立索引，以实现快速检索。  
2. **合规审计：** 在归档前验证必需的元数据（例如创建时间戳）是否存在。  
3. **自动化报告：** 生成汇总报告，列出每个幻灯片文稿的创建者及创建时间。  
4. **CRM 集成：** 使用公司元数据字段将演示文稿关联到客户记录。

## 性能考虑
- **并行处理：** 处理大批量文件时，可在独立线程中并行处理以提升吞吐量。  
- **资源管理：** 如示例所示使用 try‑with‑resources 自动关闭流，防止内存泄漏。  
- **批量提取：** GroupDocs.Metadata 支持批量操作；考虑在单个循环中读取多个文件以提高效率。

## 常见问题与解决方案
- **元数据缺失：** 若属性返回 `null`，说明源文件未包含该信息。请按示例对 `null` 值进行防护。  
- **不支持的格式：** 确保文件为受支持的 PowerPoint 格式（`.pptx`、`.ppt`）。  
- **许可证错误：** 检查许可证文件是否放置正确，或试用期是否已过。

## 常见问答

**Q: 如何处理缺失的元数据属性？**  
A: API 对未设置的字段返回 `null`。可使用类似 `(author != null ? author : "N/A")` 的条件表达式提供默认值。

**Q: GroupDocs.Metadata 能提取自定义元数据字段吗？**  
A: 能，除了内置属性外，您还可以使用相同的 API 读取和写入自定义键/值对。

**Q: 是否支持其他演示文稿格式？**  
A: GroupDocs.Metadata 支持 PowerPoint（`.ppt`、`.pptx`）以及 PDF、Word 和多种图像格式。

**Q: GroupDocs.Metadata Java 的系统要求是什么？**  
A: 兼容的 JDK（8 或更高）以及足够的堆内存以容纳要处理的文档大小。

**Q: 遇到问题时在哪里获取帮助？**  
A: 访问官方支持论坛获取帮助：[GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## 资源

- **文档：** https://docs.groupdocs.com/metadata/java/  
- **API 参考：** https://reference.groupdocs.com/metadata/java/  
- **下载：** https://releases.groupdocs.com/metadata/java/  
- **GitHub：** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java  
- **免费支持：** https://forum.groupdocs.com/c/metadata/  
- **临时许可证：** https://purchase.groupdocs.com/temporary-license/

通过本指南，您已经掌握了如何 **read created time java** 并 **java extract document properties** 从 PowerPoint 演示文稿中使用 GroupDocs.Metadata。将这些代码片段集成到项目中，可提升文档智能水平并简化合规工作流。

---

**最后更新：** 2026-01-26  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs