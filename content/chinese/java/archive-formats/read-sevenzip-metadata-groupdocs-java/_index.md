---
date: '2026-02-19'
description: 学习如何使用 GroupDocs.Metadata for Java 读取 7z 元数据，包括如何获取压缩大小以及其他归档属性。
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: 如何在 Java 中使用 GroupDocs.Metadata 读取 SevenZip 元数据
type: docs
url: /zh/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 在 Java 中读取 SevenZip 元数据

如果您需要在 Java 应用程序中 **read sevenzip metadata java**，您来对地方了。在本教程中，我们将演示如何使用 **GroupDocs.Metadata** 提取文件名、压缩大小、未压缩大小、修改日期等——正是您进行备份验证、同步或存储优化任务所需的数据。

## 介绍

在使用 Java 访问和读取 SevenZip 存档文件的元数据属性时遇到困难吗？本教程将指导您使用 **GroupDocs.Metadata** 的过程。这个强大的库简化了直接从存档中提取文件名、大小和修改日期等关键信息的操作。

## 快速答案

- **我应该使用哪个库？** GroupDocs.Metadata for Java  
- **我可以列出 SevenZip 存档中的文件吗？** 是的 – 使用 `getSevenZipPackage().getFiles()`  
- **我需要许可证吗？** 免费试用可用于评估；生产环境需要完整许可证  
- **支持哪个 Java 版本？** JDK 8 或更高  
- **是否必须使用 Maven？** 不是强制的，但 Maven 能简化依赖管理  

## 在 Java 中 “how to read sevenzip” 是什么？

读取 SevenZip 元数据意味着打开 `.7z` 容器，枚举每个条目，并获取 **compressed size**、**uncompressed size**、**file name** 和 **modification date** 等属性，而无需提取实际文件。

## read sevenzip metadata java

在专用标题中使用主要关键词有助于读者和搜索引擎了解本指南的重点。下面我们将深入探讨您需要高效 **read sevenzip metadata java** 的具体步骤。

## 为什么在元数据提取中使用 GroupDocs.Metadata Java？

- **Unified API** – 可跨数十种存档和文档格式工作  
- **No external tools** – 所有操作都在您的 Java 进程内完成  
- **Performance‑focused** – 仅读取元数据提取 java 任务所需的头部信息  
- **Robust licensing** – 提供试用版，商业使用需完整许可证  

## 前提条件

在深入了解 **GroupDocs.Metadata for Java** 之前，请确保您的开发环境已正确配置。您需要以下内容：

- **Java Development Kit (JDK)：** 版本 8 或更高。  
- **Maven：** 推荐用于依赖管理，当然也可以手动添加 JAR。  
- **Basic Java Knowledge：** 熟悉类、方法和异常处理。  

## 为 Java 设置 GroupDocs.Metadata

要使用 GroupDocs.Metadata，请通过 Maven 或直接下载库将其包含在项目中。

### 使用 Maven

在您的 `pom.xml` 文件中添加以下配置：

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

或者，从 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下载最新版本。

#### 获取许可证

1. **Free Trial：** 先使用免费试用以测试 GroupDocs.Metadata 的功能。  
2. **Temporary License：** 如需延长评估访问，可申请临时许可证。  
3. **Purchase：** 长期使用时，考虑购买完整许可证。  

完成设置后，让我们继续实现元数据读取功能。

## 实施指南

### 从 SevenZip 存档访问元数据

在本节中，我们将从 SevenZip 存档中提取并打印文件名和大小等元数据属性。

#### 步骤 1：初始化 Metadata 对象

首先使用指向 SevenZip 文件的路径初始化 `Metadata` 对象。这告诉 GroupDocs 要处理哪个文件。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 步骤 2：获取根包

接下来，访问存档的根包，以便作为所有文件及其属性的入口点。

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **为什么使用 `getRootPackageGeneric()`？** 它提供了存档内容的通用视图，使遍历条目更容易，而无需关心特定文件格式。

#### 步骤 3：遍历存档条目

通过访问存档的根包，遍历每个条目以提取元数据属性。这包括获取名称、压缩大小和修改日期等细节。

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **为什么提取这些属性？** 了解文件大小有助于存储管理，而修改日期对同步任务至关重要。`getCompressedSize()` 调用是 Java 获取每个条目 **get compressed size java** 的方式。

#### 步骤 4：清理资源

最后，确保释放 metadata 对象，以释放 GroupDocs.Metadata 占用的任何资源。

```java
} finally {
    metadata.dispose();
}
```

- **为什么要释放？** 正确释放对象有助于防止长期运行的应用程序出现内存泄漏。

## 实际应用

了解如何 **read sevenzip metadata java** 具有许多实际优势：

1. **Data Backup Management：** 快速验证备份存档的完整性和一致性。  
2. **File Synchronization Tools：** 使用修改日期决定哪些文件需要更新。  
3. **Storage Optimization：** 比较压缩和未压缩大小以规划容量。  

可以与其他系统集成，实现作为更大数据管理工作流一部分的自动化元数据提取。

## 性能考虑

在使用 GroupDocs.Metadata 处理大型存档时，请记住以下提示：

- **Batch Processing：** 分批处理文件，以有效管理内存使用。  
- **Efficient Exception Handling：** 使用 try‑with‑resources 实现自动资源管理。  
- **Asynchronous Processing：** 对于繁重的工作负载，实施异步技术。  

## 常见问题及解决方案

| 问题 | 解决方案 |
|------|----------|
| **访问文件时的 `NullPointerException`** | 确认存档路径正确且文件未损坏。 |
| **大型存档导致内存激增** | 启用批处理或增大 JVM 堆大小 (`-Xmx`)。 |
| **许可证未被识别** | 确保许可证文件放置在应用程序的工作目录中，或通过 `License.setLicense(path)` 设置。 |

## 常见问答

**Q:** 什么是 GroupDocs.Metadata？  
**A:** 它是一个用于处理不同文件格式元数据的 Java 库，包括 SevenZip 存档。

**Q:** 我可以在不使用 Maven 的情况下使用 GroupDocs.Metadata 吗？  
**A:** 可以，您可以从官方网站下载 JAR 并将其添加到项目的类路径中。

**Q:** 如何高效处理大型存档？  
**A:** 实施批处理或使用异步流以限制内存消耗。

**Q:** 我在哪里可以找到更详细的指南？  
**A:** 请参阅 [official documentation](https://docs.groupdocs.com/metadata/java/) 获取完整的 API 参考。

**Q:** 如果我遇到库的问题怎么办？  
**A:** 在 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 社区提问。

## 资源

- **文档：** Explore more at [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **API 参考：** Check detailed API information at [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **下载：** Get the latest version from [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub 仓库：** Access code samples on [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **免费支持论坛：** Join discussions or ask questions at [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**最后更新：** 2026-02-19  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs