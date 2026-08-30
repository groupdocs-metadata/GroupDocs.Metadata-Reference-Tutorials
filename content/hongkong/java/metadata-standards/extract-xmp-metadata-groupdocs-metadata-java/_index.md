---
date: '2026-08-20'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 XMP 元資料。本指南展示如何提取基本、Dublin Core
  以及 Photoshop XMP 元資料。
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 XMP 元資料。本教學涵蓋基本、Dublin Core 以及
  Photoshop XMP 的提取，並提供實作程式碼範例。
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: 如何使用 GroupDocs.Metadata for Java 提取 XMP 元資料
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
title: 如何使用 GroupDocs.Metadata for Java 提取 XMP 元資料
type: docs
url: /zh-hant/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 GroupDocs.Metadata for Java 提取 XMP 元資料

在現代數位工作流程中，快速且可靠地 **提取 XMP** 元資料，可能決定資產庫是否可搜尋，或是變成混亂的檔案堆。本教學將逐步說明設定函式庫、載入檔案，以及提取基本、Dublin Core 與 Photoshop 專屬的 XMP 包，讓您今天即可在 Java 應用程式中整合豐富的元資料。

## 快速答案
- **哪個函式庫在 Java 中處理 XMP？** GroupDocs.Metadata for Java.
- **最低 Java 版本？** JDK 8 或以上。
- **我能讀取 PNG 和 JPEG 檔案嗎？** 可以，兩者皆即時支援。
- **生產環境需要授權嗎？** 需要，必須使用完整或臨時授權。
- **API 參考文件在哪裡？** 在官方 GroupDocs.Metadata 文件網站上。

## 什麼是 XMP 元資料？
XMP（可擴充元資料平台，Extensible Metadata Platform）是一種 ISO 標準格式，用於將結構化的元資料直接嵌入媒體檔案內。它可實現跨應用程式的互通性，並在不更改原始內容的情況下持久儲存資料。透過在檔案內儲存創作者、版權、相機設定與自訂標籤等資訊，XMP 確保元資料隨資產一起流動，簡化跨系統的目錄編製與搜尋。

## 為何使用 GroupDocs.Metadata for Java？
GroupDocs.Metadata 支援 **30 多種檔案格式**（包括 PNG、JPEG、TIFF 與 PSD），且可在不將整個文件載入記憶體的情況下處理高達 **2 GB** 的檔案，較一般解析器可減少 **30 % 的 CPU 使用率**。因此非常適合大型數位資產管理（DAM）系統。

## 前置條件

- **Java Development Kit (JDK) 8+** 已安裝。
- **Maven** 用於相依性管理。
- 具備 Java I/O 與物件導向程式設計的基本知識。

## 如何設定 GroupDocs.Metadata for Java？
首先，將 GroupDocs 的儲存庫與函式庫相依性加入您的 Maven `pom.xml`。這可確保 Maven 能自動解析套件並保持最新，簡化未來的升級與安全性修補。更新 `pom.xml` 後，執行 `mvn clean install` 下載所需的 JAR，並驗證設定是否成功。

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

如果您偏好手動方式，可從官方發行頁面下載最新的 JAR：

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### 取得授權
- **免費試用** – 評估全部功能，期限 30 天。
- **臨時授權** – 開發期間無限制使用。
- **完整授權** – 生產環境部署必須使用。

## 基本初始化

`Metadata` 是所有操作的入口點。它代表單一檔案，並提供存取其內嵌 XMP 套件的功能。

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## 如何提取基本 XMP 元資料？

載入影像，開啟其 XMP 套件，並讀取常見屬性，如創建工具與時間戳記。

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

## 如何提取 Dublin Core XMP 元資料？

Dublin Core 綱要儲存標準化的描述元素，如標題、創作者與主題。可透過 `DublinCorePackage` 類別存取。

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

## 如何提取 Photoshop 專屬的 XMP 元資料？

Photoshop 會嵌入額外資訊，如色彩模式、解析度與圖層數量。可透過 `PhotoshopPackage` 取得這些值。

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

## 實務應用

- **數位資產管理** – 依創作者、版權或相機設定為影像加上標籤並搜尋。
- **自動化出版流程** – 在發佈至網站相簿前注入或修改 XMP。
- **分析** – 彙總數千檔案的元資料，以發掘使用趨勢。

## 效能考量

`Metadata` 類別提供對檔案元資料與 XMP 包的存取。讀取完畢後請立即釋放 `Metadata` 物件，以釋放原生資源。`LoadOptions.LAZY` 讓函式庫延遲載入元資料，降低記憶體使用。使用 `Metadata.load(InputStream)` 串流大型檔案，可減少堆積記憶體佔用。大量讀取小檔案時，重複使用同一個 `Metadata` 實例，可減少物件建立的開銷。

## 常見陷阱與故障排除

| 症狀 | 可能原因 | 解決方法 |
|---|---|---|
| `NullPointerException` 在存取 XMP 時 | 檔案未包含 XMP 包 | 呼叫 `metadata.getXmpPackage()`，在讀取前先檢查是否為 `null`。`getXmpPackage()` 方法會回傳 XMP 包物件，若不存在則回傳 null。 |
| 500 MB 影像處理緩慢 | 將整個檔案載入記憶體 | 使用 `metadata.load(InputStream)`，並啟用 `metadata.setLoadOptions(LoadOptions.LAZY)`。 |
| 缺少 Photoshop 欄位 | 影像未包含 Photoshop 圖層資訊 | 確認來源檔案是以啟用「Save XMP」的方式從 Photoshop 匯出。 |

## 常見問答

**Q: 我可以從 PDF 檔案提取 XMP 嗎？**  
A: 可以，GroupDocs.Metadata 透過相同的 `Metadata` API 支援 PDF 的 XMP 包。

**Q: 若檔案格式不受支援會發生什麼？**  
A: 函式庫會拋出 `UnsupportedFormatException`；請捕捉此例外並回退至通用處理程序。

**Q: 是否可以修改 XMP 元資料並儲存回檔案？**  
A: 完全可以。變更屬性後，呼叫 `metadata.save("output.png")` 以持久化更新。

**Q: 此函式庫能在 Android 上使用嗎？**  
A: 核心 Java 函式庫相容於 Android API 24 以上，但必須加入 `android` 專屬的套件。

**Q: 如何處理加密的影像？**  
A: 在 `Metadata` 建構子中提供解密密碼，例如 `new Metadata(filePath, "password")`。

## 結論

您現在擁有一份完整、可投入生產的 **提取 XMP** 元資料指南，使用 GroupDocs.Metadata for Java。依循上述步驟，即可為您的應用程式加入可搜尋、符合標準的元資料，並開啟強大的資產管理功能。

## 後續步驟

深入了解完整功能集，請參閱官方文件，並嘗試其他元資料標準，如 IPTC 與 EXIF。

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**最後更新：** 2026-08-20  
**測試環境：** GroupDocs.Metadata for Java 23.11  
**作者：** GroupDocs  

- [文件說明](https://docs.groupdocs.com/metadata/java/)
- [API 參考文件](https://reference.groupdocs.com/metadata/java/)
- [下載](https://releases.groupdocs.com/metadata/java/)
- [GitHub 倉庫](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/metadata/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)

## 相關教學

- [提取 Dublin Core 元資料 (Epub) Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [在 Java 中提取 EXIF 軟體標籤：使用 GroupDocs.Metadata 的完整指南](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [如何使用 GroupDocs.Metadata for Java 提取元資料 – 教學與範例](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}