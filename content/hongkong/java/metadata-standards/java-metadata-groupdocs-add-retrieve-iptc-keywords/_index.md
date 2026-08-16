---
date: '2026-08-15'
description: 了解如何在 Java 中使用 GroupDocs.Metadata 新增 IPTC 關鍵字，提升數位資產管理與可搜尋性。
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: 使用 GroupDocs.Metadata 在 Java 中新增 IPTC 關鍵字，提升數位資產管理。學習逐步設定、程式碼與最佳實踐。
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: 在 Java 中使用 GroupDocs.Metadata 新增 IPTC 關鍵字
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: 在 Java 中使用 GroupDocs.Metadata 新增 IPTC 關鍵字
type: docs
url: /zh-hant/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# 在 Java 中使用 GroupDocs.Metadata 新增 IPTC 關鍵字

管理影像中繼資料對任何數位資產管理（DAM）策略都至關重要。在本教學中，您將學習 **如何在 Java 中新增 IPTC 關鍵字**，使用 GroupDocs.Metadata 函式庫，然後檢索這些關鍵字以驗證變更。完成後，您將擁有一個可重複使用的模式，可嵌入批次處理工作、內容管理管線或任何基於 Java 的媒體工作流程。

## 快速答覆
- **哪個函式庫可在 Java 中新增 IPTC 關鍵字？** GroupDocs.Metadata for Java.  
- **我需要授權嗎？** 免費試用可用於開發；正式環境需購買授權。  
- **我可以一次新增多個關鍵字嗎？** 可以——只需將每個關鍵字加入 IPTC 套件。  
- **是否支援大型檔案處理？** GroupDocs.Metadata 可處理高達 2 GB 的檔案，且不會將整個檔案載入記憶體。  
- **需要哪個 Java 版本？** JDK 8 或以上，搭配 Maven 3 或更高版本。

## 什麼是 add iptc keywords java？
**Add IPTC keywords java** 指的是使用 Java 程式碼以程式化方式插入符合 IPTC 標準的關鍵字標籤至影像檔案。此操作可豐富影像的中繼資料，使其在 DAM 系統中可搜尋，並提升網站資產的 SEO。它亦有助於遵循媒體資產標記的行業標準。

## 為何使用 GroupDocs.Metadata for Java？
GroupDocs.Metadata 支援 **150+ 種中繼資料標準**（包括 EXIF、IPTC、XMP），且可 **處理高達 2 GB 的檔案**，無需完整載入記憶體，與傳統檔案串流方式相比，可降低 CPU 與記憶體使用量最高達 30 %。API 為型別安全、文件完整，且提供單行呼叫即可持久化變更。

## 前置條件

- **GroupDocs.Metadata for Java**（版本 24.12 或更新）。  
- Java Development Kit 8 或更新版本。  
- 已安裝並設定 Maven 3。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE（非必須，但建議使用）。  

### 必要的函式庫
在您的 `pom.xml` 中加入 GroupDocs.Metadata 相依性：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

您可以從 **GroupDocs.Metadata for Java releases** 頁面下載此函式庫：[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## 如何在 Java 中新增 IPTC 關鍵字？

首先，使用 GroupDocs.Metadata API 載入目標影像檔案，接著驗證是否已存在 IPTC 套件，若不存在則建立，最後將所需的關鍵字加入 IPTC Keywords 集合。以下步驟將詳細說明此工作流程的每個部分。

### 步驟 1：建立常數類別
`Constants` 類別儲存可重複使用的值，例如檔案位置與授權字串。

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### 步驟 2：初始化 metadata 並設定 IPTC 套件
`Metadata` 是讀寫任何支援的中繼資料格式的入口點。它抽象化檔案處理，讓您不必手動管理串流。

以下程式碼會檢查是否已存在 IPTC 套件；若不存在，則建立一個，以確保有關鍵字儲存位置。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### 步驟 3：將關鍵字加入 IPTC 記錄
IptcDataSet 代表單一 IPTC 中繼資料項目，例如關鍵字。每個關鍵字皆以 `IptcDataSet` 項目加入。您可以依需求加入任意數量的關鍵字；函式庫會自動處理重複偵測。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### 步驟 4：取得並顯示 IPTC 關鍵字
`metadata.getIptc().getKeywords()` 會回傳儲存在 IPTC 套件中的關鍵字字串清單。儲存後，您可以重新讀取關鍵字以確認已正確持久化。此驗證步驟對單元測試與除錯非常有用。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## 如何在 Java 中取得 IPTC 關鍵字？

`metadata.getIptc().getKeywords()` 會回傳儲存在 IPTC 套件中的關鍵字字串清單。您可以遍歷此清單、記錄每個項目，或將其輸入搜尋索引以快速檢索。此方法回傳 `List<String>`，包含 IPTC 套件中所有關鍵字，讓您即時顯示或處理它們。

## 常見陷阱與故障排除

- **缺少 IPTC 套件：** 若影像沒有 IPTC 區塊，`metadata.getIptc()` 會回傳 `null`。在新增關鍵字前，務必先呼叫 `metadata.addIptc()`。  
- **授權錯誤：** 確認在 `Constants.LICENSE_PATH` 中正確引用試用或商業授權檔案。缺少授權會拋出 `LicenseException`。  
- **大型檔案：** 若影像大於 2 GB，請將處理分割為多個區塊，或使用 GroupDocs.Metadata 提供的串流 API，以避免 `OutOfMemoryError`。  

## 常見問答

**Q: 我可以將 IPTC 關鍵字加入 PDF 檔案嗎？**  
A: 不能。IPTC 是針對影像的標準；PDF 檔案應使用 XMP 或 PDF 專屬的中繼資料欄位。

**Q: GroupDocs.Metadata 支援其他影像格式嗎？**  
A: 支援——它可處理 JPEG、TIFF、PNG、BMP 與 WebP，保留現有中繼資料，同時新增 IPTC 項目。

**Q: 我可以儲存多少個關鍵字？**  
A: IPTC 規範允許每張影像最多 64 個關鍵字；GroupDocs.Metadata 會自動強制此上限。

**Q: 此函式庫相容於 Java 11 嗎？**  
A: 完全相容。函式庫編譯目標為 Java 8+，可在 Java 11、17 以及更新的 LTS 版本上無縫運作。

**Q: 若需要移除關鍵字該怎麼做？**  
A: 先取得關鍵字清單，移除不需要的項目，然後呼叫 `metadata.getIptc().setKeywords(updatedList)` 並儲存檔案。

## 結論

您現在已掌握使用 GroupDocs.Metadata 在 **Java 中新增 IPTC 關鍵字** 的完整、可投入生產的模式。透過初始化 metadata 物件、確保 IPTC 套件存在、追加關鍵字並驗證結果，您可以將穩健的標記整合至任何基於 Java 的 DAM 或內容管理工作流程。探索其他中繼資料類型——EXIF、XMP 與自訂標籤，以進一步豐富您的資產。

**下一步**
- 將範例擴充為批次處理影像資料夾。  
- 結合關鍵字新增與自動影像分析（例如 AI 生成的標籤）。  
- 探索 GroupDocs.Metadata 的 API，以讀寫 EXIF GPS 資料，實現基於位置的搜尋。

---

**最後更新：** 2026-08-15  
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

## 相關教學

- [提取 BMP 標頭 Java – GroupDocs.Metadata 影像教學](/metadata/java/image-formats/)
- [java 提取影像中繼資料 – 使用 GroupDocs.Metadata 提取 Panasonic MakerNote 中繼資料（Java）](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [使用 GroupDocs.Metadata 自動化 Java 中繼資料依日期更新，以提升檔案管理效率](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)