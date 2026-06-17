---
date: '2026-03-22'
description: 了解如何使用 GroupDocs.Metadata for Java 更改 Excel 创建日期并更新 Excel 元数据。请按照本分步指南向
  Excel 添加关键字并修改文档属性。
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: 使用 GroupDocs.Metadata 在 Java 中更改 Excel 创建日期
type: docs
url: /zh/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# 使用 GroupDocs.Metadata 在 Java 中更改 Excel 创建日期

在现代数据驱动的环境中，**更改 Excel 创建日期** 并保持其他元数据最新可以显著提升文档组织、可搜索性和合规性。无论您处理的是财务报告、项目跟踪器还是归档数据，准确的元数据都能确保相关人员在适当的时间找到正确的文件。本教程将指导您在 Java 应用程序中使用 GroupDocs.Metadata 库来**更改 Excel 创建日期**、**向 Excel 添加关键字**以及**修改 Excel 文档属性**。

## 快速回答
- **我可以更改 Excel 文件的创建日期吗？** 是的，可使用 GroupDocs.Metadata 的 `setCreatedTime`。  
- **哪个库支持在 Java 中更新 Excel 元数据？** GroupDocs.Metadata for Java。  
- **我需要许可证吗？** 免费试用可用于评估；生产环境需要永久许可证。  
- **需要哪个 Java 版本？** JDK 8 或更高。  
- **我可以向 Excel 工作簿添加自定义关键字吗？** 当然——在文档属性上使用 `setKeywords`。  

## 什么是“更改 Excel 创建日期”？
更改 Excel 创建日期是指更新工作簿文件内部存储的内置 *Created* 属性。该属性是标准 Office Open XML 元数据的一部分，可通过编程方式编辑，而不会更改实际的工作表内容。

## 为什么使用 GroupDocs.Metadata 处理 Excel 元数据？
GroupDocs.Metadata 提供了高级、类型安全的 API，抽象了 Office Open XML 格式所需的低层 XML 处理。它让您能够：

- **更新核心属性**，如作者、公司和创建日期，一次调用即可。  
- **向 Excel 添加关键字**，以提升在 SharePoint、OneDrive 或本地文件系统中的搜索结果。  
- **修改 Excel 文档属性**，无需在 Excel 中打开工作簿，从而节省时间和资源。  

## 前置条件
- Java Development Kit (JDK) 8 或更高。  
- IntelliJ IDEA 或 Eclipse 等 IDE。  
- 对 Java 文件 I/O 有基本了解。  

## 为 Java 设置 GroupDocs.Metadata

### 安装

在您的 `pom.xml` 中添加 GroupDocs.Metadata Maven 仓库和依赖：

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

或者，您也可以[直接下载最新版本](https://releases.groupdocs.com/metadata/java/)，如果您更喜欢手动设置的话。

### 获取许可证

GroupDocs 提供免费试用供评估。生产使用时，请从供应商处获取临时或永久许可证。详情请访问[GroupDocs 购买页面](https://purchase.groupdocs.com/temporary-license/)。

#### 基本初始化

在 Java 源文件中导入必要的类：

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## 步骤实现

### 步骤 1：打开 Excel 工作簿

提供源工作簿的路径并创建 `Metadata` 实例。`try‑with‑resources` 块可确保文件句柄自动关闭。

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### 步骤 2：更新内置元数据属性

现在您可以**更改 Excel 创建日期**，设置作者、公司、类别，并**向 Excel 添加关键字**。`new Date()` 调用会获取当前时间戳，但您也可以提供任意所需的 `java.util.Date`。

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **技巧提示：** 使用一致的关键字命名约定（例如 `project:Q2, finance, confidential`），以提升未来的搜索效果。

### 步骤 3：保存更新后的工作簿

指定输出路径并持久化更改。原始文件保持不变，这对审计追踪非常有用。

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## 常见问题及解决方案

| 问题 | 产生原因 | 解决方案 |
|------|----------|----------|
| **文件路径错误** | 相对/绝对路径不正确 | 仔细检查 `inputFilePath` 和 `outputFilePath`。使用 `Paths.get(...)` 以获得平台无关的路径。 |
| **库版本不兼容** | 使用了不支持 `setCreatedTime` 方法的旧版 GroupDocs.Metadata | 升级到最新版本（如 Maven 代码片段所示）。 |
| **缺少许可证** | 试用期已过 | 通过购买页面申请临时许可证或购买完整许可证。 |
| **大型工作簿内存占用** | 加载巨大的 Excel 文件会消耗堆内存 | 分批处理文件，并在必要时增加 JVM 堆内存 (`-Xmx`)。 |

## 常见问题

**问：GroupDocs.Metadata 支持哪些 Java 版本？**  
答：完全支持 Java 8 及更高版本。

**问：更新元数据时应如何处理异常？**  
答：将代码放在 `try‑catch` 块中，并记录 `MetadataException` 以捕获任何 I/O 或格式错误。

**问：我可以在一次运行中更新多个 Excel 文件吗？**  
答：可以，遍历文件路径集合，但对大批量时要监控内存使用情况。

**问：是否可以恢复对元数据所做的更改？**  
答：在应用更新前保留原始工作簿的备份，必要时可恢复。

**问：在哪里可以找到更详细的文档？**  
答：请参阅官方指南 [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/)。

## 实际应用

1. **财务审计** – 记录谁在何时修改了工作簿，提供审计追踪。  
2. **项目管理** – 使用项目特定的关键字标记电子表格，以便快速检索。  
3. **数据归档** – 保留原始创建日期和公司信息，以满足合规要求。  

## 性能提示

- 将每次运行的元数据操作限制在一定范围，以避免过度的内存消耗。  
- 及时关闭 `Metadata` 对象（`try‑with‑resources` 模式会自动完成）。  
- 对于非常大的工作簿，考虑在后台线程中处理，以保持 UI 响应。  

## 结论

现在，您已经了解如何使用 GroupDocs.Metadata 在 Java 中**更改 Excel 创建日期**、**向 Excel 添加关键字**以及**修改 Excel 文档属性**。此功能使您能够保持电子表格的良好组织、可搜索性，并符合内部治理政策的合规要求。下一步，您可以探索其他元数据功能，如自定义属性或批处理，以进一步简化文档管理工作流。

---

**最后更新：** 2026-03-22  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

**资源**
- [文档](https://docs.groupdocs.com/metadata/java/)
- [API 参考](https://reference.groupdocs.com/metadata/java/)
- [下载 GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [GitHub 仓库](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [免费支持论坛](https://forum.groupdocs.com/c/metadata/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)