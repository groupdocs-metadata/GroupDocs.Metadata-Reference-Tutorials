---
date: '2026-08-10'
description: 了解如何使用适用于 Java 的 GroupDocs.Metadata 从 PSD 文件中提取 EXIF 元数据。本指南涵盖基础提取、IFD
  包、GPS 数据以及实际案例。
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: 了解如何使用适用于 Java 的 GroupDocs.Metadata 从 PSD 文件中提取 EXIF 元数据。提供逐步指南、代码片段以及针对开发者的故障排除技巧。
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: 如何使用 GroupDocs.Metadata 从 PSD 文件中提取 EXIF 元数据
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: 如何使用 GroupDocs.Metadata 从 PSD 文件中提取 EXIF 元数据
type: docs
url: /zh/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 从 PSD 文件中提取 EXIF 元数据

从 PSD 文件中提取 **EXIF 元数据** 是在需要审计图像来源、自动化资产标记或构建可搜索媒体库时的常规但强大的步骤。在本教程中，您将快速了解如何使用 GroupDocs.Metadata for Java **提取 EXIF**，查看确切的 API 调用，并学习如何处理高级 IFD 包和 GPS 坐标。完成后，您将能够将元数据提取集成到任何基于 Java 的工作流中。

## 快速答案

`Metadata` 类表示一个文件并提供对其元数据的访问。

- **第一行代码是什么？** `Metadata metadata = new Metadata("sample.psd");`
- **哪个方法返回艺术家名称？** `metadata.getExif().getArtist();`
- **我可以读取 GPS 数据吗？** 是的 – 使用 `metadata.getExif().getGpsInfo();`
- **生产环境是否需要许可证？** 在试用期结束后需要有效的 GroupDocs.Metadata 许可证。
- **支持的 Java 版本？** Java 8 或更高（最高至 Java 21）。

## 什么是 EXIF 元数据？

EXIF（可交换图像文件格式）元数据在图像文件中存储相机设置、创建时间戳和位置信息。GroupDocs.Metadata 直接从 PSD 文件的二进制结构读取这些信息，并通过简洁的 Java API 公开。它使开发者能够以编程方式检索相机型号、曝光时间和 GPS 坐标等细节，而无需手动检查。

## 为什么在 Java 中使用 GroupDocs.Metadata？

GroupDocs.Metadata 支持 **30+ 种文件格式**（包括 PSD、JPEG、PNG、TIFF），并且可以在不将整个文档加载到内存中的情况下处理高达 **2 GB** 的文件。该库提取 **150 多个不同的 EXIF 标签**，确保您拥有进行分析或合规所需的完整相机和 GPS 属性集。

## 前置条件

- **Java Development Kit (JDK) 8** 或更高版本已安装在您的机器上。  
- **Maven** 用于依赖管理。  
- **GroupDocs.Metadata for Java 版本 24.12**（或更高）。  
- 基本熟悉 Java 类、对象和异常处理。

### 必需的库和依赖项

| 依赖项 | Maven 坐标 |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### 环境设置

您应该拥有一个兼容 Maven 的 IDE，例如 IntelliJ IDEA 或 Eclipse。创建一个新的 Maven 项目或将依赖项添加到现有项目中。

## 如何为 Java 设置 GroupDocs.Metadata

可以通过几行配置将 GroupDocs.Metadata 添加到 Maven 项目中。以下步骤展示了如何包含仓库和依赖，以便库在类路径上可用。

### Maven 设置

在 `<dependencies>` 部分的 `pom.xml` 中添加以下代码片段：

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

或者，从官方发布页面下载最新的 JAR： [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)。

### 许可证获取

要在 30 天试用期后运行库，需要获取临时或完整许可证：

1. 访问 [License Purchase Page](https://purchase.groupdocs.com/temporary-license)。  
2. 选择 **temporary** 进行测试或 **full** 用于生产。  
3. 按照屏幕指示将许可证文件 (`metadata.lic`) 嵌入到 Java 类路径中。

### 基本初始化和设置

库在类路径上后，按如下方式初始化：

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## 如何从 PSD 图像中提取基本 EXIF 元数据属性

本节说明如何加载 PSD 文件、访问 EXIF 容器并读取最常见的标签，如 **artist**、**copyright** 和 **software**。该过程包括创建 `Metadata` 实例，调用 `getExif()`，然后使用简单的 getter 方法检索各个属性。

### 步骤实现

1. **创建指向 PSD 文件的 `Metadata` 实例**。  
2. **调用 `getExif()`** 以获取 EXIF 容器。  
3. **读取各个属性**，如 `getArtist()`、`getCopyright()` 和 `getSoftware()`。  
4. **打印或存储** 根据您的应用逻辑的值。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **技巧提示：** `Metadata` 对象会自动检测文件格式，因此您可以在不修改代码的情况下将相同代码复用于 JPEG 或 TIFF 文件。

## 如何从 PSD 图像中提取 EXIF IFD 包属性

IFD（图像文件目录）部分包含更深入的技术细节，如 **camera serial number**、**lens model** 和 **user comments**。`Ifd0` 表示包含基本相机信息的主图像文件目录。提取这些字段对取证分析或高精度目录编制很有帮助。

### 实现步骤

1. **复用前一节的 `Metadata` 实例**。  
2. **通过 `metadata.getExif().getIfd0()`** 导航到 IFD 容器。  
3. **读取属性**，如 `getBodySerialNumber()` 和 `getUserComment()`。  
4. **输出数据** 或将其映射到您的领域模型。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## 如何从 PSD 文件中检索 GPS 数据（纬度、经度）

许多现代相机在 EXIF 块中嵌入 GPS 坐标。`GpsInfo` 保存从 EXIF 数据提取的地理坐标。调用 `metadata.getExif().getGpsInfo()`，然后使用 `getLatitude()`、`getLongitude()` 和 `getAltitude()` 获取精确的位置信息——无需额外解析。

### 详细步骤

1. **获取 GPS 信息对象**：`GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **读取纬度和经度**：`gps.getLatitude()` 返回十进制度的 `double`。  
3. **处理缺失数据**：如果标签不存在，API 返回 `null`，因此需防止 `NullPointerException`。

> **常见陷阱：** 某些 PSD 文件以有理数存储 GPS 坐标；库会自动归一化，但旧文件可能需要手动转换。

## 常见问题与故障排除

| 症状 | 可能原因 | 解决方案 |
|---------|--------------|-----|
| `Unsupported format` 异常 | 使用不识别 PSD 的旧版 GroupDocs.Metadata | 升级到 version 24.12 或更高 |
| 调用 `getArtist()` 时的 `NullPointerException` | 源文件中不存在 EXIF 标签 | 在读取前检查 `metadata.getExif().hasArtist()` |
| 30 天后许可证错误 | 类路径上未找到许可证文件 | 将 `metadata.lic` 放在 `src/main/resources` 或使用 `Metadata.setLicense("path/to/license")` |

## 常见问题

**Q: 我可以从受密码保护的 PSD 文件中提取 EXIF 元数据吗？**  
A: 可以。使用 `new Metadata("file.psd", "password")` 加载文件，然后像往常一样访问 EXIF 数据。

**Q: GroupDocs.Metadata 是否支持批量处理多个 PSD 文件？**  
A: 当然。可以在循环中实例化 `Metadata` 对象，或使用 `MetadataCollection` 辅助类高效处理目录。

**Q: 官方支持哪些 Java 版本？**  
A: 完全测试了 Java 8 到 Java 21。该库仅使用标准 API，因此在任何符合规范的 JVM 上都能运行。

**Q: 能否将 EXIF 数据写回 PSD 文件？**  
A: 可以。通过 `Exif` 对象修改属性后，调用 `metadata.save("output.psd")` 保存更改。

**Q: 库能够处理多大的 PSD 文件而不会耗尽内存？**  
A: 由于低内存架构，GroupDocs.Metadata 采用流式处理，在典型的 8 GB RAM 机器上可处理高达 **2 GB** 的文件。

## 结论

您现在已经了解了使用 GroupDocs.Metadata for Java 从 PSD 文件中 **提取 EXIF** 元数据的方法，包括基本标签、先进的 IFD 和 GPS 信息。将这些代码片段集成到图像处理流水线中，以实现自动目录编制、合规检查或基于位置的服务。想进一步探索，可尝试从其他受支持的格式（JPEG、TIFF、PNG）提取元数据，或实验写回功能以嵌入自定义标签。

---

**最后更新：** 2026-08-10  
**测试环境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

## 相关教程

- [使用 GroupDocs.Metadata 在 Java 中提取 PSD 文件的图像资源：综合指南](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [使用 GroupDocs.Metadata for Java 提取 PSD 标头和图层信息：综合指南](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [使用 GroupDocs.Metadata 在 Java 中将 MakerNote 属性提取为 TIFF/EXIF 标签](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)