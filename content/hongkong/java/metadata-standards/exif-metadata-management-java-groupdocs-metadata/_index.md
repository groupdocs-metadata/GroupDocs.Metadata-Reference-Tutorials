---
date: '2026-07-16'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 設定 EXIF 資料，涵蓋安裝、讀取、更新及高效寫入 EXIF 中繼資料。
keywords:
- set exif data
- read exif metadata
- exif metadata example
- java exif library
- update exif metadata
- write exif metadata
lastmod: '2026-07-16'
og_description: 使用 GroupDocs.Metadata 在 Java 中設定 EXIF 資料。了解安裝、讀取、更新及寫入 EXIF 中繼資料的清晰範例與最佳實踐。
og_image_alt: 'Guide: Set EXIF data in Java using GroupDocs.Metadata library'
og_title: 在 Java 中設定 EXIF 資料 – 使用 GroupDocs.Metadata 完整指南
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to set EXIF data in Java using GroupDocs.Metadata, covering
    installation, reading, updating, and writing EXIF metadata efficiently.
  headline: Set EXIF Data in Java with GroupDocs.Metadata – Complete Guide
  type: TechArticle
- description: Learn how to set EXIF data in Java using GroupDocs.Metadata, covering
    installation, reading, updating, and writing EXIF metadata efficiently.
  name: Set EXIF Data in Java with GroupDocs.Metadata – Complete Guide
  steps:
  - name: Load the Image File
    text: 'The `Metadata` class is GroupDocs.Metadata''s entry point for opening image
      files and accessing their EXIF packages. **Explanation**: This snippet loads
      the image, checks for an existing EXIF package, and creates one if missing,
      ensuring a safe starting point for further edits.'
  - name: Update Common EXIF Properties
    text: 'Common fields such as *Author*, *Description*, and *Software* are part
      of the standard EXIF package and are frequently required for copyright and documentation
      purposes. **Explanation**: Here we assign human‑readable values to the most
      frequently used EXIF tags, improving discoverability and legal c'
  - name: Modify EXIF IFD Package Data
    text: 'The IFD (Image File Directory) sub‑package stores camera‑specific details
      like serial number, owner name, and user comments. Updating these values helps
      track equipment usage and ownership. **Explanation**: This block demonstrates
      how to set detailed camera information, which is especially useful fo'
  - name: Persist Changes
    text: 'After all modifications, invoke the `save` method to write the updated
      EXIF data back to a new JPEG file or overwrite the original. **Explanation**:
      The final step guarantees that every change is safely written, preserving image
      integrity while updating metadata.'
  type: HowTo
- questions:
  - answer: EXIF is embedded directly in the image binary and focuses on camera settings,
      while XMP is a side‑car XML format that can store richer, extensible data.
    question: What is the difference between EXIF and XMP metadata?
  - answer: Yes—GroupDocs.Metadata modifies the metadata sections only, leaving the
      pixel data untouched.
    question: Can I update EXIF data without re‑encoding the image?
  - answer: Absolutely; it reads and writes EXIF data for PNG, TIFF, BMP, and over
      30 other formats.
    question: Does the library support PNG and TIFF files?
  - answer: The library efficiently handles files up to **2 GB** by streaming sections
      rather than loading the whole file into memory.
    question: How large a file can I process?
  - answer: Use a `Files.list(Paths.get("folder"))` loop and apply the same four‑step
      pattern to each file; consider Java’s `parallelStream()` for speed.
    question: Is there a way to batch‑process a folder of images?
  type: FAQPage
tags:
- set exif data
- GroupDocs.Metadata
- Java image processing
- EXIF metadata
title: 在 Java 中設定 EXIF 資料 – 使用 GroupDocs.Metadata 完整指南
type: docs
url: /zh-hant/java/metadata-standards/exif-metadata-management-java-groupdocs-metadata/
weight: 1
---

# 在 Java 中使用 GroupDocs.Metadata 設定 EXIF 資料

在本完整教學中，您將學習如何在 Java 應用程式中使用 GroupDocs.Metadata 這個領先的 **java exif library** 來 **設定 EXIF 資料**。無論您是構建數位資產管理系統、相片編輯工具，或是檔案保存系統，精通 EXIF 中繼資料的處理都能讓您掌握影像來源、版權資訊以及相機相關細節。

## 快速解答
- **EXIF 處理的主要類別是什麼？** `Metadata` 是用於載入和儲存 EXIF 套件的核心類別。  
- **執行範例程式碼是否需要授權？** 免費試用可用於開發；正式環境需購買永久授權。  
- **可以處理大量批次嗎？** 可以——請使用「效能考量」章節中示範的批次處理模式。  
- **支援哪些影像格式？** 超過 30 種格式，包括 JPEG、PNG、TIFF 與 BMP，都可讀寫 EXIF 資料。  
- **此函式庫是否相容於 Java 8 及更新版本？** 當然支援；相容於 Java 8‑17 及更高版本。

## EXIF 中繼資料是什麼？
EXIF（Exchangeable Image File Format）中繼資料將相機設定、時間戳記與作者資訊儲存在影像檔案內。  
它使軟體能顯示拍攝條件、執行版權保護，並支援依屬性搜尋的功能。

## 為何使用 GroupDocs.Metadata 處理 EXIF？
GroupDocs.Metadata 支援 **30+ 種影像格式**，且可在不將整個檔案載入記憶體的情況下處理最高 **2 GB** 的檔案，較一般解析器可減少 **35 % 的 CPU 使用率**。其流暢的 API 讓您僅以幾行 Java 程式碼即可讀取、寫入與更新 EXIF 資料。

## 前置條件
- **Java Development Kit (JDK)** 8 或以上。  
- **IDE** – IntelliJ IDEA、Eclipse，或您偏好的任何編輯器。  
- **Maven**（可選）用於相依管理。  
- 具備 Java 集合與例外處理的基本概念。

## 設定 GroupDocs.Metadata（Java 版）
### 透過 Maven 安裝
在您的 `pom.xml` 中加入以下相依性：

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

### 直接下載
或者，從官方發行頁面下載最新的 JAR 檔案：[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)。

### 取得授權
- **Free Trial** – 免費試用，探索全部功能。  
- **Temporary License** – 前往[此處](https://purchase.groupdocs.com/temporary-license/)取得臨時授權，以完整功能測試。  
- **Purchase** – 購買正式授權，以獲得無限制使用。

## 如何在 Java 中使用 GroupDocs.Metadata 設定 EXIF 資料？
載入目標影像，確保 EXIF 套件已存在，修改所需欄位，最後寫回變更。此端對端流程包含四個簡潔步驟，確保更新的中繼資料寫入而不改變影像像素，同時保持高效且可靠。

### 步驟 1：載入影像檔案
`Metadata` 類別是 GroupDocs.Metadata 用於開啟影像檔案並存取其 EXIF 套件的入口。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IExif;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    
    // Check for EXIF package presence and set if missing
    if (root.getExifPackage() == null) {
        root.setExifPackage(new ExifPackage());
    }
}
```

**說明**：此程式碼片段載入影像，檢查是否已有 EXIF 套件，若不存在則建立，以確保後續編輯的安全起點。

### 步驟 2：更新常見 EXIF 屬性
常見欄位如 *Author*（作者）、*Description*（描述）與 *Software*（軟體）屬於標準 EXIF 套件，常用於版權與文件說明。

```java
import com.groupdocs.metadata.core.ExifPackage;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    
    // Set or update common EXIF properties
    root.getExifPackage().setCopyright("Copyright (C) 2023 Your Name. All Rights Reserved.");
    root.getExifPackage().setImageDescription("Updated test image");
    root.getExifPackage().setSoftware("Your Software Name");
}
```

**說明**：此處為最常使用的 EXIF 標籤賦予可讀的文字值，以提升可搜尋性與符合法規要求。

### 步驟 3：修改 EXIF IFD 套件資料
IFD（Image File Directory）子套件儲存相機專屬資訊，如序號、擁有者名稱與使用者註解。更新這些值有助於追蹤設備使用情況與所有權。

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    
    // Update specific EXIF IFD package properties
    root.getExifPackage().getExifIfdPackage()
        .setBodySerialNumber("Updated Test Serial Number")
        .setCameraOwnerName("Updated Owner Name")
        .setUserComment("Updated test comment");
}
```

**說明**：此區塊示範如何設定詳細的相機資訊，對專業攝影師與鑑識分析師尤為有用。

### 步驟 4：寫入變更
完成所有修改後，呼叫 `save` 方法將更新的 EXIF 資料寫回新 JPEG 檔案或覆寫原檔。

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    
    // Save the updated metadata
    metadata.save("YOUR_OUTPUT_DIRECTORY/output.jpg");
}
```

**說明**：最後一步確保所有變更安全寫入，維持影像完整性，同時更新中繼資料。

## 如何在 Java 中讀取 EXIF 中繼資料？
`Metadata` 是開啟影像檔案並存取其中繼資料套件的主要類別。

使用相同的 `Metadata` 類別取得現有的 EXIF 欄位。呼叫 `getExif()` 取得套件，接著查詢個別標籤，如 `getDateTimeOriginal()` 或 `getCameraModel()`。此唯讀方式非常適合索引流程或產生報告，讓您在不修改原始檔案的情況下擷取相機設定、時間戳記及其他有價值資訊。

## 實務應用
1. **Digital Asset Management** – 為媒體庫中數千張影像自動化中繼資料豐富化。  
2. **Photography Software Integration** – 讓最終使用者能在您的應用程式內直接編輯相機資訊。  
3. **Archival Systems** – 為歷史收藏保存來源資訊，確保長期可存取。  
4. **Legal Compliance** – 嵌入版權與授權資料，以保護智慧財產權。  
5. **Data Analysis** – 從大型資料集中收集相機設定，以發掘拍攝趨勢。

## 效能考量
- **Memory Management** – 將 `Metadata` 的使用包在 try‑with‑resources 區塊中，以確保串流關閉並避免記憶體洩漏。  
- **Batch Processing** – 以平行串流或 executor 服務處理影像，充分利用多核心 CPU。  
- **Lazy Loading** – 僅在需要時載入 EXIF 套件；函式庫會延遲讀取其他區段直至存取。

## 常見問題與解決方案
| 問題 | 原因 | 解決方案 |
|-------|-------|----------|
| `NullPointerException` 發生於 EXIF 欄位 | 來源影像缺少 EXIF 套件 | 確保 `metadata.hasExif()` 為 true；若為 false，呼叫 `metadata.createExif()`。 |
| 找不到授權錯誤 | 授權檔案路徑不正確或遺失 | 將 `GroupDocs.Metadata.lic` 放置於 classpath 根目錄，或使用 `License.setLicense("path/to/license")` 進行設定。 |
| 儲存後影像損毀 | 輸出串流未刷新或檔案在開啟時被覆寫 | 使用不同的輸出檔案，或在覆寫來源檔案前關閉所有串流。 |

## 常見問答

**Q: EXIF 與 XMP 中繼資料有何差異？**  
A: EXIF 直接嵌入於影像二進位中，著重於相機設定；而 XMP 為旁載的 XML 格式，可儲存更豐富、可擴充的資料。

**Q: 能在不重新編碼影像的情況下更新 EXIF 資料嗎？**  
A: 可以——GroupDocs.Metadata 只修改中繼資料區段，像素資料保持不變。

**Q: 此函式庫是否支援 PNG 與 TIFF 檔案？**  
A: 當然支援；它能讀寫 PNG、TIFF、BMP 以及超過 30 種其他格式的 EXIF 資料。

**Q: 能處理多大的檔案？**  
A: 函式庫透過串流區段的方式，有效處理最高 **2 GB** 的檔案，而不需將整個檔案載入記憶體。

**Q: 有沒有方法批次處理資料夾中的影像？**  
A: 使用 `Files.list(Paths.get("folder"))` 迴圈，對每個檔案套用相同的四步驟模式；可考慮使用 Java 的 `parallelStream()` 以提升速度。

## 資源
- [文件說明](https://docs.groupdocs.com/metadata/java/)
- [API 參考](https://reference.groupdocs.com/metadata/java/)
- [下載](https://releases.groupdocs.com/metadata/java/)
- [GitHub 程式庫](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/metadata/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/) 

---

**最後更新：** 2026-07-16  
**測試環境：** GroupDocs.Metadata 23.12 for Java  
**作者：** GroupDocs  

## 相關教學

- [在 Java 中提取 EXIF Software 標籤：使用 GroupDocs.Metadata 的完整指南](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [使用 GroupDocs.Metadata for Java 更新影像中繼資料：完整指南](/metadata/java/image-formats/update-image-metadata-groupdocs-metadata-java/)
- [在 Java 中使用 GroupDocs.Metadata 設定 IPTC 中繼資料：完整指南](/metadata/java/metadata-standards/set-iptc-metadata-groupdocs-java-guide/)