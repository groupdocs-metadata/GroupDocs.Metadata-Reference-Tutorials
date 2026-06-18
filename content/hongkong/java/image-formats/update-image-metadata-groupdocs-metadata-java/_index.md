---
date: '2026-06-12'
description: 了解如何使用 GroupDocs.Metadata for Java 更新 Java 影像元資料，涵蓋 Dublin Core、Camera
  Raw、XMP Basic 以及 Job Ticket 方案。
keywords:
- update image metadata java
- GroupDocs.Metadata Java
- image metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  headline: How to update image metadata java using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  name: How to update image metadata java using GroupDocs.Metadata
  steps:
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Dublin Core Package:**'
    text: '**Create or Retrieve Dublin Core Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Camera Raw Package:**'
    text: '**Create or Retrieve Camera Raw Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Replace Existing XMP Basic Package:**'
    text: '**Replace Existing XMP Basic Package:**'
  type: HowTo
- questions:
  - answer: Yes. After creating one `Metadata` instance, you can retrieve and modify
      any combination of packages before calling `save()` once.
    question: Can I update multiple metadata schemes in a single operation?
  - answer: Absolutely. Load the image into a `InputStream` from S3, pass the stream
      to the `Metadata` constructor, and save the result back to the cloud.
    question: Does the library work with images stored in cloud storage (e.g., AWS
      S3)?
  - answer: A valid commercial license is required for production deployments; a trial
      license is limited to evaluation and non‑commercial testing.
    question: Is a commercial license required for production use?
  - answer: GroupDocs.Metadata for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: What Java versions are officially supported?
  - answer: The API streams data and never loads the entire file into memory, allowing
      you to process very large images without excessive heap usage.
    question: How does the library handle large image files (e.g., >100 MB)?
  type: FAQPage
title: 如何使用 GroupDocs.Metadata 更新 Java 影像元資料
type: docs
url: /zh-hant/java/image-formats/update-image-metadata-groupdocs-metadata-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 更新影像 metadata java

## 快速解答
- **哪個函式庫在 Java 中處理影像 metadata？** GroupDocs.Metadata for Java.  
- **我可以一次性更新 Dublin Core 和 XMP 嗎？** 可以 – 建立 `Metadata` 物件，並在儲存前同時處理多個套件。  
- **試用需要授權嗎？** 免費試用授權會解鎖所有功能；完整授權則移除使用限制。  
- **需要哪個 Java 版本？** JDK 8 或以上。  
- **唯一的加入相依方式是 Maven 嗎？** 建議使用 Maven，但也可以從官方發行頁面下載 JAR。

## 如何使用 GroupDocs.Metadata 更新影像 metadata java？
`Metadata` 是提供讀寫影像 metadata 的主要類別。將目標影像載入 `Metadata` 實例，取得或建立所需的 metadata 套件（例如 Dublin Core、Camera Raw），設定必要的屬性，然後呼叫 `save()` 將變更寫回磁碟。此流程支援 JPEG、PNG、TIFF 以及許多其他格式。

### 為何選擇 GroupDocs.Metadata for Java？
GroupDocs.Metadata 支援 **50+** 種輸入與輸出格式，能在不將整個檔案載入記憶體的情況下處理上百頁的影像檔，並提供流暢的 API，讓您在一次操作中更新多個 metadata 方案。此函式庫具備完整的執行緒安全性，適合高吞吐量的伺服器環境。

## 前置條件
- **Java Development Kit (JDK) 8+** – 確認 `java -version` 顯示 1.8 或更新版本。  
- **Maven** – 用於相依管理；若需要也可使用 Gradle。  
- **基本的 Java 知識** – 熟悉 IntelliJ IDEA 或 Eclipse 等 IDE。  

## 設定 GroupDocs.Metadata for Java
在 Maven 專案的 `pom.xml` 檔案中加入以下相依，即可將函式庫加入專案：

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

您也可以從官方發行頁面下載最新的 JAR： [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### 取得授權
先取得免費試用授權以探索所有功能。若要正式上線，請購買完整授權或透過 [purchase page](https://purchase.groupdocs.com/temporary-license) 申請臨時授權。有效的授權會移除所有試用限制，並解鎖高級支援。

### 基本初始化
`Metadata` 類別是所有影像檔讀寫操作的入口點。加入相依後，您可以如下初始化函式庫：

```java
import com.groupdocs.metadata.Metadata;

public class MetadataUpdater {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
            // Your code to update metadata will go here
        }
    }
}
```

## 更新特定的 Metadata 方案

### 如何使用 GroupDocs.Metadata for Java 更新 Dublin Core metadata 方案？
`Metadata` 是存取影像 metadata 的主要入口。`DublinCorePackage` 代表 Dublin Core metadata 集合，允許設定標準描述欄位，如 `format`、`rights`、`subject` 等通用欄位。建立 `Metadata` 物件，取得 `DublinCorePackage`，設定值後儲存檔案，即可確保符合標準的描述資訊。

1. **初始化 Metadata 物件：**  
   `Metadata` 類別在記憶體中代表單一影像檔，並提供對所有支援的 metadata 套件的存取。

   ```java
   try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
       IXmp root = (IXmp) metadata.getRootPackage();
       if (root.getXmpPackage() != null) {
           // Further steps will be added here
       }
   }
   ```

2. **建立或取得 Dublin Core 套件：**  
   使用 `metadata.getDublinCorePackage()` 取得現有套件，若不存在則實例化新套件。

   ```java
   if (root.getXmpPackage().getSchemes().getDublinCore() == null) {
       root.getXmpPackage().getSchemes().setDublinCore(new XmpDublinCorePackage());
   }
   ```

3. **更新屬性：**  
   直接在套件物件上設定 `format`、`rights`、`subject` 等屬性。

   ```java
   root.getXmpPackage().getSchemes().getDublinCore()
       .setFormat("image/gif")
       .setRights("Copyright (C) 2011-2021 GroupDocs. All Rights Reserved")
       .setSubject("test");
   ```

4. **儲存變更：**  
   呼叫 `metadata.save(outputPath)` 以寫入更新後的 metadata。

   ```java
   metadata.save("YOUR_OUTPUT_DIRECTORY/OutputGif");
   ```

### 如何使用 GroupDocs.Metadata for Java 修改 Camera Raw metadata？
`Metadata` 是讀寫影像 metadata 的主要類別。`CameraRawPackage` 提供對 Camera Raw 特定 metadata（如曝光與陰影）的存取。Camera Raw metadata 儲存技術拍攝參數，例如陰影、auto‑brightness、曝光等。更新這些欄位可確保 Lightroom 等工具正確解讀影像，提升批次處理效能，並在大型相片集保持一致性。

1. **初始化 Metadata 物件：**  
   重複使用先前為 Dublin Core 建立的 `Metadata` 實例。

2. **建立或取得 Camera Raw 套件：**  
   在變更前先檢查是否已有 `CameraRawPackage`。

   ```java
   if (root.getXmpPackage().getSchemes().getCameraRaw() == null) {
       root.getXmpPackage().getSchemes().setCameraRaw(new XmpCameraRawPackage());
   }
   ```

3. **更新屬性：**  
   調整 `shadows`、`autoBrightness`、`exposure` 等設定，以符合所需的影像特性。

   ```java
   root.getXmpPackage().getSchemes().getCameraRaw()
       .setShadows(50)
       .setAutoBrightness(true)
       .setAutoExposure(true)
       .setCameraProfile("test")
       .setExposure(0.0001);
   ```

4. **儲存變更：**  
   將修改持久化至您指定的輸出目錄。

### 如何使用 GroupDocs.Metadata for Java 更新 XMP Basic metadata？
`Metadata` 是操作影像 metadata 的核心類別。`XmpBasicPackage` 代表 XMP Basic 架構的核心欄位。XMP Basic 包含建立日期、base URL、評分等核心欄位。更新這些屬性可提升目錄編制、改善搜尋相關性，並加強與內容管理系統的整合，協助數位資產工具依使用者定義的條件組織與顯示影像。

1. **初始化 Metadata 物件：**  
   在整個教學中使用相同的 `Metadata` 實例。

2. **取代現有的 XMP Basic 套件：**  
   若缺少 XMP Basic 套件，請實例化新套件並附加至 `Metadata` 物件。

   ```java
   root.getXmpPackage().getSchemes().setXmpBasic(new XmpBasicPackage());
   ```

3. **更新屬性：**  
   依需求設定 `creationDate`、`baseURL`、`rating`。

   ```java
   root.getXmpPackage().getSchemes().getXmpBasic()
       .setCreateDate(new Date())
       .setBaseUrl("https://groupdocs.com")
       .setRating(5);
   ```

4. **儲存變更：**  
   將更新後的 metadata 寫回磁碟。

### 如何在 Java 中使用 Basic Job Ticket metadata 方案？
`Metadata` 是處理影像 metadata 的主要類別。`BasicJobTicketPackage` 處理工作票據 metadata，允許將工作流程資訊嵌入影像。Basic Job Ticket 架構會將工作 ID、名稱與 URL 直接寫入影像檔，使下游系統能追蹤處理階段並將影像與特定任務關聯。加入工作票據可提升可稽核性與自動化流程的營運效率。

1. **初始化 Metadata 物件：**  
   持續使用相同的 `Metadata` 實例。

2. **設定 Basic Job Ticket 套件：**  
   取得現有套件，若不存在則建立新套件。

   ```java
   root.getXmpPackage().getSchemes().setBasicJobTicket(new XmpBasicJobTicketPackage());
   ```

3. **設定工作：**  
   定義工作屬性，如 `id`、`name`、`url`，讓下游處理系統能追蹤影像的生命週期。

   ```java
   XmpJob job = new XmpJob();
   job.setID("1");
   job.setName("test job");
   job.setUrl("https://groupdocs.com");

   root.getXmpPackage().getSchemes().getBasicJobTicket()
       .setJobs(new XmpJob[]{job});
   ```

4. **儲存變更：**  
   將所有工作票據資訊持久化至輸出資料夾。

## 實務應用
- **攝影工作室：** 自動將版權與授權資訊注入每個匯出的 JPEG，確保符合法律規範。  
- **內容管理系統 (CMS)：** 為上傳的資產加入 Dublin Core 與 XMP 資料，提升搜尋引擎對影像的索引效果。  
- **數位資產管理 (DAM)：** 使用 Basic Job Ticket 架構嵌入處理狀態，方便在複雜流程中追蹤影像。

## 常見問題與解決方案
- **缺少套件錯誤：** 設定屬性前務必先呼叫 `get...Package()` 方法；若回傳 `null`，請先實例化套件。  
- **檔案權限問題：** 以足夠的作業系統權限執行 Java 程式，特別是寫入受保護目錄時。  
- **不支援的格式：** GroupDocs.Metadata 支援超過 50 種影像格式；若遇到未知副檔名，請參考官方文件。

## 常見問答

**Q: 我可以在一次操作中更新多個 metadata 方案嗎？**  
A: 可以。建立一個 `Metadata` 實例後，您可以在呼叫一次 `save()` 前取得並修改任意組合的套件。

**Q: 此函式庫能處理存放於雲端儲存 (例如 AWS S3) 的影像嗎？**  
A: 完全可以。從 S3 讀取影像至 `InputStream`，將該串流傳入 `Metadata` 建構子，然後將結果儲存回雲端。

**Q: 正式環境需要商業授權嗎？**  
A: 正式部署必須使用有效的商業授權；試用授權僅限於評估與非商業測試。

**Q: 官方支援哪些 Java 版本？**  
A: GroupDocs.Metadata for Java 支援 JDK 8、11 與 17，確保與舊版與新版應用程式相容。

**Q: 函式庫如何處理大型影像檔 (例如 >100 MB)？**  
A: API 以串流方式處理資料，從不將整個檔案載入記憶體，讓您在不佔用過多堆積的情況下處理極大檔案。

## 結論
依照本指南的步驟，您現在已具備使用 GroupDocs.Metadata 進行 **更新影像 metadata java** 的完整、可投入生產的工作流程。您可以自信地為影像加入 Dublin Core、Camera Raw、XMP Basic 與 Job Ticket 資訊，讓數位資產更易搜尋、符合法規，並可直接投入自動化流程。探索函式庫的其他功能，例如 metadata 抽取與驗證，以進一步提升資產管理策略。

---

**Last Updated:** 2026-06-12  
**Tested With:** GroupDocs.Metadata for Java 23.12  
**Author:** GroupDocs

## 相關教學

- [使用 GroupDocs.Metadata Java 從 Canon CR2 檔案提取 Metadata：影像格式完整指南](/metadata/java/image-formats/extract-metadata-groupdocs-metadata-canon-cr2/)
- [使用 GroupDocs.Metadata 在 Java 中高效更新 PDF Metadata：文件管理指南](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [使用 GroupDocs.Metadata 在 Java 中更新 MP3 ID3v2 標籤的完整指南](/metadata/java/audio-video-formats/update-mp3-id3v2-tags-groupdocs-metadata-java/)