---
date: '2026-06-01'
description: 了解如何使用适用于 Java 的 GroupDocs.Metadata 提取 PNG 文本块——高效读取 PNG 元数据并集成强大的图像处理。
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: 如何使用 GroupDocs.Metadata Java API 提取 PNG 文本块
type: docs
url: /zh/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata Java API 提取 PNG 文本块

从图像文件中提取文本信息可能具有挑战性，尤其是对于像 PNG 这样的非文本格式。**GroupDocs.Metadata for Java** 通过提供强大的工具来检索和管理嵌入这些图像中的元数据，从而简化了此过程。无论是处理通用、压缩还是国际化的文本块，GroupDocs.Metadata 都提供了简化的解决方案。

在本教程中，我们将指导您如何使用 Java 中的 GroupDocs.Metadata 库高效提取 PNG 文件中的不同类型文本块。通过了解这些技术，您可以无缝地将文本提取功能集成到应用程序中，提升各领域的数据处理能力。

## 快速答案
- **GroupDocs.Metadata 能读取 png 元数据吗？** 是的，它读取所有标准 PNG 元数据，包括文本块。  
- **需要哪个 Java 版本？** Java 8 或更高版本完全受支持。  
- **开发是否需要许可证？** 免费试用可用于测试；生产环境需要商业许可证。  
- **可以提取多少种文本块类型？** 三种主要类型：通用、压缩和国际化。  
- **性能是个问题吗？** 对于典型的 5 MB PNG，在现代 CPU 上提取时间低于 200 ms。

## “how to extract png” 是什么？
**“How to extract png”** 指的是使用编程 API 从 PNG 图像文件中检索嵌入的文本块的过程。这些文本块可以包含描述性元数据、注释或国际化字符串。通过利用 GroupDocs.Metadata for Java，开发者可以在不解码整个图像的情况下，以编程方式读取、过滤和操作这些块。

## 为什么使用 GroupDocs.Metadata 进行 PNG 文本提取？
GroupDocs.Metadata 支持 **50+ 图像和文档格式**，并且可以 **在不将整个图像加载到内存中** 的情况下处理 PNG 文件，针对最高 10 MB 的文件提供 **平均 150 ms** 的提取速度。该库还保证 **100 % 数据保真度**，在国际文本块中保留 Unicode 字符。

## 前提条件

在使用 GroupDocs.Metadata for Java 提取 PNG 图像的文本块之前，请确保具备以下条件：

### 必需的库和依赖项
- **GroupDocs.Metadata for Java**：通过 Maven 或直接下载的方式将此库加入项目。

### 环境设置要求
- 已设置好 Java 开发环境（建议使用 JDK 8 或更高版本）。  
- 使用 IntelliJ IDEA、Eclipse 或其他支持 Java 项目的 IDE。

### 知识前提
- 基本的 Java 编程理解。  
- 熟悉在 Java 应用中处理文件和目录。

## 为 Java 设置 GroupDocs.Metadata

要开始使用 GroupDocs.Metadata，您需要将其加入项目。以下展示了通过 Maven 或直接下载库的两种方式：

### Maven 设置
在 `pom.xml` 文件中添加以下仓库和依赖：

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
也可以从 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下载最新版本。

#### 许可证获取步骤
- **Free Trial**：开始免费试用以探索功能。  
- **Temporary License**：获取临时许可证以进行更长时间的测试。  
- **Purchase**：如果准备投入生产，请购买许可证。

### 基本初始化和设置

完成库的设置后，按如下方式在 Java 应用中初始化 GroupDocs.Metadata：

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## 如何从 PNG 文件中提取 png 文本块？

`Metadata` 类是访问文件元数据流的入口点。使用 `new Metadata("yourImage.png")` 加载 PNG 文件，访问根包，并遍历所需的文本块集合——只需几行代码即可完成。此方法会返回所有通用、压缩和国际化文本块，方便您按需处理。

### 定义锚点
`Metadata` 类是 GroupDocs.Metadata 的入口，代表一个容器，提供对文件内部所有元数据流的编程访问。

## 从 PNG 提取通用文本块

此功能允许检索 PNG 文件中嵌入的所有通用文本块。以下是实现步骤：

#### 概述
您将访问并遍历存储在图像元数据中的每个文本块。

#### 步骤实现
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:** `PngRootPackage` 表示 PNG 元数据的根容器，公开文本块集合。

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `pngFilePath`：您的 PNG 文件路径。  
   - `PngRootPackage`：包含元数据块的根包。

#### 故障排除提示
- 确保您的 PNG 文件包含文本块；否则将检索不到数据。  
- 核实 PNG 文件的路径是否正确。

## 从 PNG 提取压缩文本块

若专门处理压缩文本块，请按照以下步骤操作：

#### 概述
此功能专注于检索和管理 PNG 元数据中的压缩文本块。

#### 步骤实现
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**  

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `getCompressionMethod()`：返回使用的压缩方法。`getCompressionMethod()` 方法返回压缩文本块所使用的压缩算法。

#### 故障排除提示
- 确保您的 PNG 文件使用受支持的压缩方法。  
- 处理文本块可能未压缩的异常情况。

## 从 PNG 提取国际化文本块

以下步骤将指导您完成国际化文本块的提取：

#### 概述
检索并管理 PNG 元数据中的国际化文本块，包括语言细节。

#### 步骤实现
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**  

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `getLanguage()`：检索文本块的语言标签。`getLanguage()` 方法提供与国际化文本块关联的 ISO 语言标签。  
   - `isCompressed()`：指示文本块是否已压缩。`isCompressed()` 方法指示文本块是否以压缩形式存储。

#### 故障排除提示
- 确保您的 PNG 文件正确设置了国际化元数据。  
- 处理可能不存在翻译的情况。

## 实际应用

了解如何使用 GroupDocs.Metadata 提取 PNG 文本块在多种应用中都极具价值：
- **Content Management Systems**：自动检索并组织图像库的元数据。  
- **Data Analysis Tools**：通过包含图像元数据分析，提升数据提取能力。  
- **Web Scraping Projects**：从网站嵌入的图像中提取有价值的信息。

## 常见问题

**问：没有许可证可以读取 png 元数据吗？**  
答：是的，免费试用可以读取元数据，但生产部署需要商业许可证。

**问：GroupDocs.Metadata 支持其他图像格式吗？**  
答：当然——它支持 JPEG、BMP、TIFF 以及超过 40 种其他格式。

**问：如何高效处理大型 PNG 文件？**  
答：使用流式 API；它在不将完整图像加载到内存的情况下处理文件，内存使用保持在 50 MB 以下。

**问：如果 PNG 没有文本块怎么办？**  
答：API 返回空集合；在处理前可以安全地检查 `isEmpty()`。

**问：国际文本块是否支持 Unicode？**  
答：是的，GroupDocs.Metadata 完全支持 UTF‑8，保留所有语言字符。

## 结论

通过本教程，您已经学习了如何使用 Java 中的 GroupDocs.Metadata 库提取 PNG 文件的通用、压缩和国际化文本块。这项技能可以显著提升应用程序高效处理和分析图像数据的能力。进一步探索时，建议深入研究 GroupDocs.Metadata 提供的更高级元数据处理技术。

**下一步**
- 试验不同类型的元数据提取。  
- 探索 GroupDocs.Metadata 库的其他功能。  
- 在开发者社区分享您的发现或应用，以获取反馈和改进。

---

**最后更新：** 2026-06-01  
**测试版本：** GroupDocs.Metadata Java 23.9  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Metadata for Java 从 JPEG 提取图像资源块](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [使用 GroupDocs.Metadata 在 Java 中提取 JPEG2000 图像注释：分步指南](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [使用 GroupDocs.Metadata 在 Java 中从 PSD 文件提取图像资源：综合指南](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)