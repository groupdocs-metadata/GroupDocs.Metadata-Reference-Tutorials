---
date: '2025-12-26'
description: 學習如何使用 GroupDocs.Metadata for Java 提取 ASF 元資料。本指南涵蓋設定、讀取屬性以及存取編解碼器資訊。
keywords:
- ASF Metadata Extraction
- GroupDocs.Metadata for Java
- Java Media Management
title: 如何使用 GroupDocs.Metadata for Java 提取 ASF 元資料
type: docs
url: /zh-hant/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# 使用 GroupDocs.Metadata for Java 提取 ASF 元資料

**簡介**

在當今的數位環境中，高效管理多媒體內容至關重要。如果您需要從媒體檔案中 **提取 ASF 元資料**，手動操作既耗時又容易出錯。本教學將指導您使用 **GroupDocs.Metadata for Java** 讀取並顯示各種 ASF 屬性，讓您能自信地組織、搜尋及處理資產。

### 您將學習到
- 如何在 Java 專案中設定 GroupDocs.Metadata  
- 如何 **提取 ASF 元資料**（例如建立日期、檔案 ID 與旗標）  
- 如何讀取嵌入於 ASF 檔案中的編解碼器資訊  
- 如何顯示詳細的元資料描述子與基礎串流屬性  

讓我們先從先決條件開始。

## 快速解答
- **「提取 ASF 元資料」是什麼意思？** 這表示以程式方式讀取 ASF 檔案中嵌入的資訊（例如時間戳記、編解碼器、描述子）。
- **需要哪個函式庫？** GroupDocs.Metadata for Java（版本 24.12 或更新）。
- **我需要授權嗎？** 開發階段可使用免費試用或臨時授權；正式上線則需完整授權。
- **支援哪個 Java 版本？** JDK 8 或更高版本。
- **可以使用 Maven 嗎？** 可以——Maven 為推薦的相依管理工具。

## 先決條件

- **Java Development Kit (JDK)** 8 或更新版本已安裝。  
- **IDE**（如 IntelliJ IDEA 或 Eclipse）以方便編寫程式。  
- **Maven** 已在 IDE 中設定（非必須但建議）。  
- 具備 Java 及外部函式庫的基本知識。

## 設定 GroupDocs.Metadata for Java

### Maven 安裝

將以下儲存庫與相依項目加入 `pom.xml`：

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

如果您偏好不使用 Maven，請從 [GroupDocs.Metadata for Java 版本發佈](https://releases.groupdocs.com/metadata/java/) 下載最新的 JAR。

### 授權概覽

- **免費試用** – 可於 GroupDocs 官方網站取得，用於評估。  
- **臨時授權** – 允許在開發期間無限制使用所有功能。  
- **完整授權** – 商業或正式部署時必須取得。

### 基本初始化

以下為使用 GroupDocs.Metadata 開啟 ASF 檔案的最小程式碼：

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

## 什麼是 ASF 元資料？

ASF（Advanced Systems Format）是 Microsoft 的串流格式，可在單一容器中儲存音訊、視訊與元資料。元資料包含建立時間戳記、編解碼器細節、串流描述子等。透過 **提取 ASF 元資料**，您可程式化取得檔案來源、編碼參數與內容說明等資訊，這對於媒體庫、轉碼流程與合規稽核皆相當重要。

## 為何使用 GroupDocs.Metadata 提取 ASF 元資料？

- **零程式碼解析** – 無需自行實作低階 ASF 解析器。  
- **完整物件模型** – 透過直觀的 Java 類別存取屬性、編解碼器、描述子與串流細節。  
- **跨平台** – 可在任何支援 Java 的作業系統上執行。  
- **授權彈性** – 可先使用試用版，視需求升級至完整授權。

## 實作指南

在以下各節將示範具體程式碼片段，逐步說明如何 **提取 ASF 元資料**。

### 讀取基本 ASF 元資料屬性

**概觀** – 取得基本資訊，如建立日期、檔案 ID 與旗標。

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

*為何重要*：了解建立日期有助於版本控制，而檔案 ID 則能在系統間唯一識別資產。

### 顯示 ASF 編解碼器資訊

**概觀** – 列舉音訊與視訊串流所使用的編解碼器。

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

*為何重要*：編解碼器細節對於確保與播放裝置相容或決定是否需轉碼至關重要。

### 顯示元資料描述子

**概觀** – 取得詳細的描述子，如語言、串流編號與原始標題。

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

*為何重要*：描述子提供諸如字幕語言或原始檔名等上下文資訊，對於目錄編排相當有價值。

### 顯示基礎串流屬性

**概觀** – 取得每個基礎串流的位元率、時間與語言資訊。

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

*為何重要*：串流屬性協助您評估品質（位元率）並在播放或編輯時同步音訊/視訊。

## 常見問題與除錯

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| `NullPointerException` when calling `getAsfPackage()` | 檔案路徑不正確或檔案不是有效的 ASF 容器。 | 檢查路徑並確保檔案為正確的 ASF 檔案。 |
| No codec information displayed | ASF 檔案使用的專有編解碼器未被此版本函式庫辨識。 | 將 GroupDocs.Metadata 更新至最新版本，或使用自訂編解碼器解析器。 |
| Empty descriptor list | 檔案缺少元資料描述子（例如在編碼過程中被移除）。 | 使用含有嵌入元資料的來源檔案，或重新編碼並保留元資料。 |

## 常見問答

**問：我可以使用同一函式庫從其他影片格式提取元資料嗎？**  
答：可以，GroupDocs.Metadata 支援 MP4、MKV、AVI 等多種格式。只需建立對應的套件類別即可。

**問：提取後能修改 ASF 元資料嗎？**  
答：當然可以。函式庫提供大多數屬性的 setter 方法，讓您可以編輯後再儲存檔案。

**問：處理大型 ASF 檔案是否需要 64 位元 JVM？**  
答：未必需要，但 64 位元 JVM 可提供更大的堆積空間，對於處理極大型媒體檔案較為有利。

**問：授權對試用版的使用有何影響？**  
答：試用授權會解除所有功能限制，但會在部分輸出加入浮水印。正式環境需購買完整授權。

**問：我可以在 Android 上執行此程式碼嗎？**  
答：GroupDocs.Metadata 為 Java SE 所建置；若要在 Android 使用，需改用 .NET 版或相容的封裝。

## 結論

透過本指南，您已掌握如何使用 GroupDocs.Metadata for Java **提取 ASF 元資料**。您可以讀取基本屬性、編解碼器資訊、詳細描述子與串流屬性，從而完整掌握媒體資產。接下來可將此提取功能整合至批次處理流程、建置可搜尋的元資料資料庫，或擴充程式碼以修改並重新儲存 ASF 檔案。

---

**最後更新：** 2025-12-26  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs