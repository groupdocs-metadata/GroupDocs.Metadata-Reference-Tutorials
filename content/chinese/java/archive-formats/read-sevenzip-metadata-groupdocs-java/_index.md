---
date: '2025-12-20'
description: 学习如何使用 GroupDocs.Metadata for Java 读取 SevenZip 档案的元数据，这是元数据提取 Java 项目中的关键步骤。
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

如果您需要在 Java 应用程序中 **how to read sevenzip** 存档信息，您来对地方了。在本教程中，我们将演示如何使用 **GroupDocs.Metadata** 提取文件名、大小、日期等——正是您进行备份验证、同步或存储优化任务所需的数据。

## 介绍

在使用 Java 访问和读取 SevenZip 存档文件的元数据属性时遇到困难吗？本教程将指导您使用 **GroupDocs.Metadata** 的过程。这个强大的库简化了直接从存档中提取文件名、大小和修改日期等重要信息。

在本文中，我们将演示如何利用 **GroupDocs.Metadata for Java** 高效访问 SevenZip 文件中的元数据属性。

### 您将学习
- 在 Java 项目中设置 GroupDocs.Metadata  
- 使用特定方法和类读取 SevenZip 存档的元数据  
- 提取关键文件属性（如名称、压缩大小和修改日期）的实际示例  

## 快速答案
- **我应该使用哪个库？** GroupDocs.Metadata for Java  
- **我可以列出 SevenZip 存档中的文件吗？** 可以 – 使用 `getSevenZipPackage().getFiles()`  
- **我需要许可证吗？** 免费试用可用于评估；生产环境需要完整许可证  
- **支持哪个 Java 版本？** JDK 8 或更高  
- **是否必须使用 Maven？** 不是强制的，但 Maven 能简化依赖管理  

## 在 Java 中 “how to read sevenzip” 是什么？
读取 SevenZip 元数据意味着打开 `.7z` 容器，枚举每个条目，并获取 **compressed size**、**uncompressed size**、**file name** 和 **modification date** 等属性，而无需提取实际文件。

## 为什么使用 GroupDocs.Metadata Java 进行元数据提取？
- **统一的 API** – 可跨数十种存档和文档格式工作  
- **无需外部工具** – 所有操作都在您的 Java 进程内部完成  
- **性能导向** – 仅读取元数据提取任务所需的头部信息  
- **稳健的授权** – 提供试用，商业使用需完整许可证  

## 前提条件
在深入了解 **GroupDocs.Metadata for Java** 之前，请确保您的开发环境已正确设置。您需要以下内容：

- **Java Development Kit (JDK)：** 版本 8 或更高。  
- **Maven：** 推荐用于依赖管理，当然也可以手动添加 JAR。  
- **基础 Java 知识：** 熟悉类、方法和异常处理。  

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
1. **免费试用：** 首先使用免费试用来测试 GroupDocs.Metadata 的功能。  
2. **临时许可证：** 如需延长评估访问，可申请临时许可证。  
3. **购买：** 长期使用时，建议购买完整许可证。  

完成设置后，让我们继续实现元数据读取功能。

## 实施指南

### 从 SevenZip 存档访问元数据
在本节中，我们将从 SevenZip 存档中提取并打印文件名和大小等元数据属性。

#### 步骤 1：初始化 Metadata 对象
首先使用 SevenZip 文件的路径初始化 `Metadata` 对象。这告诉 GroupDocs 要处理哪个文件。

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

- **为什么提取这些属性？** 了解文件大小有助于存储管理，而修改日期对同步任务至关重要。

#### 步骤 4：清理资源
最后，确保释放 metadata 对象，以释放 GroupDocs.Metadata 占用的任何资源。

```java
} finally {
    metadata.dispose();
}
```

- **为什么要释放？** 正确释放对象有助于防止长时间运行的应用程序出现内存泄漏。

## 实际应用
了解如何读取 SevenZip 元数据具有许多实际优势：

1. **数据备份管理：** 快速验证备份存档的完整性和一致性。  
2. **文件同步工具：** 使用修改日期决定哪些文件需要更新。  
3. **存储优化：** 比较压缩后和未压缩的大小以规划容量。  

可以与其他系统集成，实现作为更大数据管理工作流一部分的自动化元数据提取。

## 性能考虑
在使用 GroupDocs.Metadata 处理大型存档时，请记住以下提示：

- **批处理：** 将文件分批处理，以有效管理内存使用。  
- **高效的异常处理：** 使用 try‑with‑resources 实现自动资源管理。  
- **异步处理：** 对于繁重的工作负载，实施异步技术。  

## 常见问题及解决方案
| 问题 | 解决方案 |
|-------|----------|
| **`NullPointerException` when accessing a file** | 验证存档路径是否正确且文件未损坏。 |
| **Memory spikes on huge archives** | 启用批处理或增加 JVM 堆大小 (`-Xmx`)。 |
| **License not recognized** | 确保许可证文件放置在应用程序的工作目录中，或通过 `License.setLicense(path)` 设置。 |

## 常见问答

**问：** 什么是 GroupDocs.Metadata？  
**答：** 它是一个用于处理不同文件格式元数据的 Java 库，包括 SevenZip 存档。

**问：** 我可以在不使用 Maven 的情况下使用 GroupDocs.Metadata 吗？  
**答：** 可以，您可以从官方网站下载 JAR 并将其添加到项目的类路径中。

**问：** 如何高效处理大型存档？  
**答：** 实施批处理或使用异步流以限制内存消耗。

**问：** 在哪里可以找到更详细的指南？  
**答：** 请参阅 [official documentation](https://docs.groupdocs.com/metadata/java/) 获取全面的 API 参考。

**问：** 如果遇到库的问题该怎么办？  
**答：** 在 [GroupDocs support forum](https://forum.groupdocs.com/c/metadata/) 向社区提问。

## 资源
- **文档：** 在 [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/) 查看更多信息  
- **API 参考：** 在 [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/) 查看详细的 API 信息  
- **下载：** 从 [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/) 获取最新版本  
- **GitHub 仓库：** 在 [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) 获取代码示例  
- **免费支持论坛：** 在 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 加入讨论或提问  

---

**最后更新：** 2025-12-20  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

---