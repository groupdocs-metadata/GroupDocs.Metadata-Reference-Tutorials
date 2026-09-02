---
date: '2026-09-02'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 asf。此指南涵蓋 Maven 設定、讀取基本屬性、codec
  詳細資訊、descriptors，以及排除故障，以確保可靠的 media handling。
keywords:
- how to extract asf
- groupdocs metadata java
- asf metadata extraction
lastmod: '2026-09-02'
og_description: 了解如何在 Java 中使用 GroupDocs.Metadata 提取 asf。此分步指南展示 Maven 設定、讀取屬性、codec
  資訊，以及排除故障，以實現無縫的 media management。
og_image_alt: Guide showing how to extract asf metadata in Java with GroupDocs.Metadata
og_title: 如何在 Java 中使用 GroupDocs.Metadata 提取 asf
schemas:
- author: GroupDocs
  dateModified: '2026-09-02'
  description: Learn how to extract asf in Java using GroupDocs.Metadata. The guide
    covers Maven setup, reading basic properties, codec details, descriptors, and
    troubleshooting for reliable media handling.
  headline: How to extract asf in Java with GroupDocs.Metadata
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, MOV, and many more. Simply
      instantiate the corresponding package class for the format you need.
    question: Can I extract metadata from other video formats with the same library?
  - answer: Absolutely. The library provides setter methods for most properties, allowing
      you to edit values and then save the file back to disk.
    question: Is it possible to modify ASF metadata after extraction?
  - answer: Not strictly, but a 64‑bit JVM gives you a larger heap, which is beneficial
      when processing files larger than 2 GB.
    question: Do I need a 64‑bit JVM for large ASF files?
  - answer: The trial license removes functional limits but adds a watermark to certain
      export operations. For unrestricted production use, purchase a full license.
    question: How does licensing affect trial usage?
  - answer: GroupDocs.Metadata is built for Java SE. For Android, use the .NET version
      with Xamarin or a compatible wrapper.
    question: Can I run this code on Android devices?
  type: FAQPage
tags:
- asf metadata
- groupdocs.metadata
- java media processing
title: 如何在 Java 中使用 GroupDocs.Metadata 提取 asf
type: docs
url: /zh-hant/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Metadata 提取 asf

在現代媒體流程中，能夠 **在 Java 中提取 asf metadata** 對於目錄編制、合規性以及自動化處理至關重要。手動解析 ASF 容器容易出錯且耗時，但 GroupDocs.Metadata for Java 提供了高階 API，為您完成繁重工作。本教學將帶您完成庫的安裝、讀取核心屬性、存取編解碼器資訊以及處理常見陷阱，讓您能自信地將 ASF metadata 提取整合至任何 Java 應用程式。

## 快速回答
- **「提取 ASF metadata」是什麼意思？** 意指以程式方式讀取嵌入於 ASF 檔案中的資訊——例如時間戳記、編解碼器識別碼與串流描述子。  
- **需要哪個函式庫？** GroupDocs.Metadata for Java（版本 24.12 或更新）。  
- **需要授權嗎？** 開發階段可使用免費試用或臨時授權；正式上線需購買完整授權。  
- **支援哪個 Java 版本？** JDK 8 以上。  
- **可以使用 Maven 嗎？** 可以——Maven 為推薦的相依管理工具。

## 什麼是 asf metadata？
`ASF`（Advanced Systems Format）metadata 是儲存在 ASF 容器內的一組結構化標籤，用來描述媒體檔案的技術與描述屬性。這些標籤包括建立時間戳記、編解碼器識別碼、語言描述子，以及如位元率與時長等串流層級屬性。以程式方式存取此資料，可協助您建立可搜尋的目錄、執行合規性檢查，或驅動自動轉碼決策。

## 為什麼使用 GroupDocs.Metadata for Java 來提取 asf metadata？
GroupDocs.Metadata 支援 **30+ 音/視格式**，且可在不將整個檔案載入記憶體的情況下處理高達 **5 GB** 的檔案，得益於其串流架構。函式庫提供乾淨的物件模型——不需低階位元組解析——只要呼叫少數方法即可取得屬性、編解碼器、描述子與串流細節。相較自行開發解析器，開發工時通常可減少 **70 %**。

## 前置條件
- **Java Development Kit (JDK)** 8 或更新版本已安裝。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse，方便撰寫程式。  
- **Maven** 已在 IDE 中設定（非必須，但建議使用）。  
- 具備基本的 Java 與外部函式庫使用經驗。

## 設定 GroupDocs.Metadata for Java

### 如何設定 GroupDocs.Metadata for Java？
將 GroupDocs 套件庫與相依項目加入 `pom.xml`。此一步即可讓整個 API 在專案中可用。

```xml
<!-- Maven repository -->
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<!-- GroupDocs.Metadata dependency -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

`GroupDocs.Metadata` JAR 會在 Maven 建置時自動解析。

### 直接下載（不使用 Maven）
若不想使用 Maven，可從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新 JAR，放入 classpath 後即可使用。

### 授權概覽
- **免費試用** – 無功能限制的評估版；不會加上浮水印。  
- **臨時授權** – 適合開發與自動化測試。  
- **完整授權** – 商業部署必須，並可解鎖高級支援。

### 基本初始化
`Metadata` 類別是載入檔案並提供格式專屬存取器的入口點。以下為開啟 ASF 檔案的最小程式碼。

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

## 如何提取基本 ASF metadata 屬性
載入 ASF 檔案並取得高階屬性，如建立日期、檔案識別碼與全域旗標。這可讓您立即了解資產的建立時間與播放標記。

```java
// Load the ASF file
AsfPackage asf = new AsfPackage("sample.asf");

// Retrieve basic properties
Date creationDate = asf.getCreationDate();
String fileId = asf.getFileId();
int flags = asf.getFlags();
```

*為什麼重要*：了解建立日期有助於版本控制，而檔案 ID 則能在分散式系統中唯一識別資產。

## 如何顯示 ASF 編解碼器資訊
`AsfCodecInfo` 集合列舉每個音訊與視訊串流使用的編解碼器。`getCodecs()` 方法回傳的物件會顯示編解碼器名稱、類型與位元率。掌握編解碼器使用情況對相容性測試、是否需要轉碼以及確保目標裝置能正確解碼至關重要。

```java
// Get codec collection
List<AsfCodecInfo> codecs = asf.getCodecs();

for (AsfCodecInfo codec : codecs) {
    System.out.println("Codec name: " + codec.getName());
    System.out.println("Codec type: " + codec.getType());
}
```

*為什麼重要*：編解碼器細節讓您驗證目標裝置是否支援所需格式，避免在正式環境出現播放失敗。

## 如何顯示 metadata 描述子
描述子提供人類可讀的資訊，如語言、原始標題與串流編號。使用 `getDescriptors()` 方法可取得 `AsfDescriptor` 物件清單，每筆包含鍵、值與可選的語言標籤。此資料可豐富搜尋索引、改善 UI 顯示，並協助多語系圖書館的組織管理。

```java
// Retrieve descriptor collection
List<AsfDescriptor> descriptors = asf.getDescriptors();

for (AsfDescriptor descriptor : descriptors) {
    System.out.println("Language: " + descriptor.getLanguage());
    System.out.println("Original title: " + descriptor.getOriginalTitle());
}
```

*為什麼重要*：描述子可告訴您字幕語言或原始檔名，對於管理多語系媒體庫相當有價值。

## 如何顯示基礎串流屬性
基礎串流屬性揭示每條串流的位元率、時間與語言等資訊，讓您能進行細緻的品質分析。`getStreams()` 方法回傳 `AsfStream` 物件；每條串流皆包含 `bitrate`、`duration`、`language` 等屬性。檢視這些值可在分發或存檔前評估檔案是否符合品質門檻。

```java
// Access base streams
List<AsfBaseStream> streams = asf.getBaseStreams();

for (AsfBaseStream stream : streams) {
    System.out.println("Bitrate: " + stream.getBitrate());
    System.out.println("Duration: " + stream.getDuration());
    System.out.println("Language: " + stream.getLanguage());
}
```

*為什麼重要*：串流層級的指標協助您在分發或存檔前判斷檔案是否達到品質標準。

## 常見問題與除錯

| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| `NullPointerException` 在呼叫 `getAsfPackage()` 時 | 檔案路徑不正確或檔案不是有效的 ASF 容器。 | 核對路徑，確保檔案為正確的 ASF 檔案。 |
| 未顯示編解碼器資訊 | ASF 檔案使用了目前函式庫版本未識別的專有編解碼器。 | 更新至最新的 GroupDocs.Metadata 版本，或自行實作編解碼器解析器。 |
| 描述子清單為空 | 檔案缺少嵌入式描述子（例如在編碼過程中被剝除）。 | 使用含有 metadata 的來源檔案，或在編碼時啟用 metadata 保留。 |
| 處理 >2 GB 檔案時效能下降 | 預設緩衝區大小對大型串流而言過小。 | 在載入前透過 `MetadataLoadOptions.setBufferSize()` 增大緩衝區大小。 |

## 常見問答

**Q: 可以使用同一套函式庫提取其他影片格式的 metadata 嗎？**  
A: 可以，GroupDocs.Metadata 支援 MP4、MKV、AVI、MOV 等多種格式。只要為所需格式實例化對應的套件類別即可。

**Q: 提取後可以修改 ASF metadata 嗎？**  
A: 完全可以。函式庫提供大多數屬性的 setter 方法，讓您編輯值後再將檔案儲存回磁碟。

**Q: 處理大型 ASF 檔案需要 64 位元 JVM 嗎？**  
A: 非必須，但 64 位元 JVM 能提供更大的堆積空間，對處理超過 2 GB 的檔案較為有利。

**Q: 授權對試用版的使用有何影響？**  
A: 試用授權會移除功能限制，但會在某些匯出操作上加上浮水印。若需無限制的正式環境使用，請購買完整授權。

**Q: 可以在 Android 裝置上執行此程式碼嗎？**  
A: GroupDocs.Metadata 針對 Java SE 開發。若要在 Android 使用，請改用 .NET 版搭配 Xamarin 或其他相容的封裝。

## 結論
依照本指南，您已掌握 **如何在 Java 中使用 GroupDocs.Metadata 提取 asf metadata**。您可以讀取基本屬性、列舉編解碼器、取得詳細描述子，並檢視串流層級屬性，從而完整掌握媒體資產。接下來可將此提取流程嵌入批次處理管線、建構可搜尋的 metadata 資料庫，或擴充程式碼以修改並重新儲存 ASF 檔案。

---

**最後更新：** 2026-09-02  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

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

## 相關教學

- [使用 GroupDocs.Metadata 提取 wav metadata 的完整指南](/metadata/java/audio-video-formats/extract-wav-metadata-groupdocs-java/)
- [使用 GroupDocs.Metadata 提取影片 metadata 的教學](/metadata/java/audio-video-formats/mastering-avi-metadata-handling-groupdocs-java/)
- [掌握 Java Metadata 提取：開發者完整指南](/metadata/java/working-with-metadata/java-metadata-extraction-groupdocs-metadata/)