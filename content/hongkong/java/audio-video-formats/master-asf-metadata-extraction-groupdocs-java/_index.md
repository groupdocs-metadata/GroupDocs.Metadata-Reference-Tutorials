---
date: '2026-09-01'
description: 了解如何使用 GroupDocs.Metadata for Java 提取 ASF 元資料。本分步指南涵蓋環境設定、讀取核心屬性、編解碼器細節以及故障排除。
keywords:
- extract asf metadata java
- asf metadata extraction
- groupdocs.metadata java
lastmod: '2026-09-01'
og_description: 了解如何使用 GroupDocs.Metadata 提取 ASF 元資料。請依照本指南設定函式庫、讀取核心 ASF 屬性，並處理常見問題。
og_image_alt: 'Developer guide: extract asf metadata java with GroupDocs.Metadata'
og_title: 如何使用 GroupDocs.Metadata 在 Java 中提取 ASF 元資料
schemas:
- author: GroupDocs
  dateModified: '2026-09-01'
  description: Learn how to extract asf metadata java using GroupDocs.Metadata for
    Java. This step‑by‑step guide covers setup, reading core properties, codec details,
    and troubleshooting.
  headline: How to extract asf metadata java with GroupDocs.Metadata
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, MOV, and many more. Just
      instantiate the appropriate package class for the format you are processing.
    question: Can I extract metadata from other video formats with the same library?
  - answer: Absolutely. The library provides setter methods for most properties, allowing
      you to edit values and then save the file back to disk.
    question: Is it possible to modify ASF metadata after extraction?
  - answer: Not strictly, but a 64‑bit JVM gives you a larger heap, which reduces
      the chance of `OutOfMemoryError` when handling multi‑gigabyte containers.
    question: Do I need a 64‑bit JVM for large ASF files?
  - answer: The trial license removes functional limits but adds a watermark to certain
      output files. For production you should purchase a full license to eliminate
      the watermark and unlock priority support.
    question: How does licensing affect trial usage?
  - answer: GroupDocs.Metadata is built for Java SE. For Android you would need the
      .NET version or a custom wrapper, as the Java library depends on APIs unavailable
      on Android.
    question: Can I run this code on Android?
  type: FAQPage
tags:
- extract asf metadata
- groupdocs.metadata
- java media processing
title: 如何使用 GroupDocs.Metadata 在 Java 中提取 ASF 元資料
type: docs
url: /zh-hant/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 提取 asf metadata java

在現代媒體流程中，能夠 **extract asf metadata java** 快速且可靠是一項競爭優勢。無論您是要建立可搜尋的目錄、驗證合規性，或是自動化轉碼決策，程式化讀取 ASF 標籤都能節省大量手動工作。本教學將示範如何使用 GroupDocs.Metadata for Java 開啟 ASF 檔案、擷取核心屬性、編解碼資訊與串流描述子，並處理您可能遇到的常見問題。

## 快速回答
- **「extract ASF metadata」是什麼意思？** 代表以程式方式讀取 ASF 檔案中內嵌的資訊（例如時間戳記、編解碼器、描述子）。  
- **需要哪個函式庫？** GroupDocs.Metadata for Java（版本 24.12 或更新）。  
- **需要授權嗎？** 開發階段可使用免費試用或暫時授權；正式上線須購買正式授權。  
- **支援哪個 Java 版本？** JDK 8 或以上。  
- **可以使用 Maven 嗎？** 可以 – Maven 為推薦的相依管理工具。

## 什麼是 extract asf metadata java？
`extract asf metadata java` 是指使用 Java 程式碼以程式化方式讀取 ASF（Advanced Systems Format）檔案內的中繼資料容器。中繼資料包括建立時間戳記、編解碼器識別碼、串流語言標籤以及其他描述媒體如何被解讀的資訊。

## 為何使用 GroupDocs.Metadata 提取 asf metadata java？
GroupDocs.Metadata 能在 **不將整個媒體串流載入記憶體** 的情況下讀取 ASF 資料，讓您可以處理數 GB 大小的檔案。此函式庫支援 **70+ 音視頻格式**，包括 ASF、MP4、MKV、AVI 與 MOV，且可提取 **超過 500 個不同的中繼資料欄位**。這樣的量化能力意味著您能取得比大多數開源解析器更完整的資料，同時保持 CPU 與記憶體使用率低。

## 前置條件
- **Java Development Kit (JDK)** 8 或更新版本，已安裝於工作站或建置伺服器。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse，用於編寫與除錯 Java 程式碼。  
- **Maven** 已安裝（非必須，但強烈建議用於相依管理）。  
- 具備基本的 Java 語法與物件導向概念。

## 設定 GroupDocs.Metadata for Java

### Maven 安裝
將 GroupDocs 套件庫與 metadata 相依加入您的 `pom.xml` 檔案：

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven2/</url>
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
若不想使用 Maven，可從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新的 JAR。

### 授權概覽
- **免費試用** – 評估期間允許無限制的讀寫。  
- **暫時授權** – 移除試用限制，適用於 CI 流程的有限期間。  
- **正式授權** – 商業部署必須，並保證長期支援。

### 基本初始化
以下程式碼片段示範開啟 ASF 檔案所需的最小程式碼：

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.formats.AsfPackage;

public class AsfMetadataExample {
    public static void main(String[] args) throws Exception {
        // Load the ASF file
        Metadata metadata = new Metadata("sample.asf");
        // Access the ASF package containing all ASF‑specific properties
        AsfPackage asf = metadata.getAsfPackage();
        // Example: print the file identifier
        System.out.println("File ID: " + asf.getFileId());
    }
}
```

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## 如何提取 asf metadata java？

`Metadata` 是用來開啟檔案並存取其中繼資料的主要類別。  
`AsfPackage` 提供 ASF 專屬資訊，如編解碼器與串流描述子。

使用 `new Metadata("yourfile.asf")` 載入 ASF 檔案，透過 `metadata.getAsfPackage()` 取得 `AsfPackage`，再呼叫相應的 getter（例如 `getCreationDate()`、`getCodecInfo()`、`getStreamDescriptors()`）。此模式讓您只需幾行 Java 程式碼即可取得所有支援的屬性，無需自行編寫低階解析程式。若需批次處理，只要將此邏輯放入遍歷目錄的迴圈，並將擷取結果寫入 CSV 或資料庫即可。

### 讀取基本 ASF 中繼資料屬性
**概覽** – 取得建立日期、檔案 ID 與旗標等基本資訊。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

*為何重要*：了解建立日期有助於版本管理，而檔案 ID 則可在系統間唯一識別資產。

### 顯示 ASF 編解碼器資訊
**概覽** – 列舉音訊與視訊串流使用的編解碼器。

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

*為何重要*：編解碼器細節對確保播放裝置相容性或決策是否需轉碼至關重要。

### 顯示中繼資料描述子
**概覽** – 抽取語言、串流編號、原始標題等詳細描述子。

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

*為何重要*：描述子提供語言（如字幕）或原始檔名等上下文資訊，對目錄編目非常有價值。

### 顯示基礎串流屬性
**概覽** – 取得每條基礎串流的位元率、時間與語言資訊。

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

*為何重要*：串流屬性有助於評估品質（位元率）以及在播放或編輯時同步音視訊。

## 常見問題與除錯

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| `NullPointerException` 在呼叫 `getAsfPackage()` 時發生 | 檔案路徑不正確或檔案不是有效的 ASF 容器。 | 核對路徑，確保檔案為正確的 ASF 檔案。 |
| 未顯示編解碼器資訊 | ASF 檔案使用函式庫版本未識別的專有編解碼器。 | 更新至最新的 GroupDocs.Metadata，或自行實作編解碼器解析器。 |
| 描述子清單為空 | 檔案缺乏中繼資料描述子（例如在編碼時被剝除）。 | 使用內嵌中繼資料的來源檔案，或重新編碼時保留中繼資料。 |

## 常見問答

**Q: 可以使用同一套函式庫提取其他影片格式的中繼資料嗎？**  
A: 可以，GroupDocs.Metadata 支援 MP4、MKV、AVI、MOV 等多種格式。只需為您處理的格式實例化相應的 package 類別。

**Q: 提取後可以修改 ASF 中繼資料嗎？**  
A: 完全可以。函式庫提供多數屬性的 setter 方法，允許您編輯值後再將檔案儲存回磁碟。

**Q: 處理大型 ASF 檔案是否需要 64 位元 JVM？**  
A: 非必須，但 64 位元 JVM 可提供更大的堆積空間，降低處理多 GB 容器時發生 `OutOfMemoryError` 的風險。

**Q: 授權對試用使用有何影響？**  
A: 試用授權會移除功能限制，但會在某些輸出檔案上加上浮水印。正式環境建議購買正式授權，以去除浮水印並取得優先支援。

**Q: 可以在 Android 上執行此程式碼嗎？**  
A: GroupDocs.Metadata 針對 Java SE 設計。若要在 Android 使用，需改用 .NET 版或自行開發封裝，因為 Java 版依賴 Android 不支援的 API。

---

**最後更新：** 2026-09-01  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

## 相關教學

- [Extract video metadata java using GroupDocs.Metadata](/metadata/java/audio-video-formats/mastering-avi-metadata-handling-groupdocs-java/)
- [Read ID3v2 Tags Java Using GroupDocs.Metadata – A Comprehensive Guide](/metadata/java/audio-video-formats/read-id3v2-tags-groupdocs-metadata-java/)
- [Master Java Metadata Extraction Using GroupDocs.Metadata: A Comprehensive Guide for Developers](/metadata/java/working-with-metadata/java-metadata-extraction-groupdocs-metadata/)