---
date: '2026-08-10'
description: 了解如何使用 GroupDocs.Metadata for Java 從 PSD 檔案中提取 EXIF 中繼資料。本指南涵蓋基本提取、IFD
  套件、GPS 資料以及實務案例。
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: 了解如何使用 GroupDocs.Metadata for Java 從 PSD 檔案中提取 EXIF 中繼資料。一步一步的指南、程式碼片段與開發人員除錯技巧。
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: 如何使用 GroupDocs.Metadata 從 PSD 檔案中提取 EXIF 中繼資料
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
title: 如何使用 GroupDocs.Metadata 從 PSD 檔案中提取 EXIF 中繼資料
type: docs
url: /zh-hant/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 從 PSD 檔案提取 EXIF 中繼資料

從 PSD 檔案提取 **EXIF 中繼資料** 是在需要審核影像來源、自動化資產標記或建立可搜尋的媒體庫時常見且強大的步驟。在本教學中，您將快速了解如何使用 GroupDocs.Metadata for Java **提取 EXIF**，查看具體的 API 呼叫，並學習如何處理進階的 IFD 套件與 GPS 座標。完成後，您即可將中繼資料提取整合到任何基於 Java 的工作流程中。

## 快速答覆

`Metadata` 類別代表一個檔案，並提供存取其中繼資料的功能。

- **第一行程式碼是什麼？** `Metadata metadata = new Metadata("sample.psd");`
- **哪個方法會回傳藝術家名稱？** `metadata.getExif().getArtist();`
- **我可以讀取 GPS 資料嗎？** 是 – 使用 `metadata.getExif().getGpsInfo();`
- **生產環境需要授權嗎？** 試用期結束後需要有效的 GroupDocs.Metadata 授權。
- **支援的 Java 版本？** Java 8 或更新版本（最高至 Java 21）。

## 什麼是 EXIF 中繼資料？

EXIF（可交換影像檔案格式）中繼資料將相機設定、建立時間戳記與位置資訊儲存在影像檔案內。GroupDocs.Metadata 直接從 PSD 檔案的二進位結構讀取這些資訊，並透過簡潔的 Java API 對外提供。開發者因此能以程式方式取得相機型號、曝光時間與 GPS 座標等細節，無需手動檢查。

## 為何在 Java 中使用 GroupDocs.Metadata？

GroupDocs.Metadata 支援 **30 多種檔案格式**（包括 PSD、JPEG、PNG、TIFF），且可在不將整個文件載入記憶體的情況下處理最高 **2 GB** 的檔案。此函式庫可提取 **超過 150 個不同的 EXIF 標籤**，確保您擁有進行分析或合規所需的完整相機與 GPS 屬性。

## 前置條件

- **Java Development Kit (JDK) 8** 或更新版本已安裝於您的機器上。  
- **Maven** 用於相依管理。  
- **GroupDocs.Metadata for Java 版本 24.12**（或更新版本）。  
- 具備 Java 類別、物件與例外處理的基本認識。

### 必要的函式庫與相依性

| 相依項目 | Maven 坐標 |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### 環境設定

您應該具備支援 Maven 的 IDE，例如 IntelliJ IDEA 或 Eclipse。建立新的 Maven 專案或將相依項目加入現有專案中。

## 如何在 Java 中設定 GroupDocs.Metadata

只需幾行設定，即可將 GroupDocs.Metadata 加入 Maven 專案。以下步驟說明如何加入儲存庫與相依項目，使函式庫可在類別路徑上使用。

### Maven 設定

在 `pom.xml` 的 `<dependencies>` 區段內加入以下程式碼片段：

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

或者，從官方發佈頁面下載最新的 JAR 檔案：[GroupDocs.Metadata for Java 版本發佈](https://releases.groupdocs.com/metadata/java/)。

### 取得授權

若要在 30 天試用期後繼續使用函式庫，請取得臨時或正式授權：

1. 造訪 [授權購買頁面](https://purchase.groupdocs.com/temporary-license)。  
2. 選擇 **temporary** 以供測試，或 **full** 以供正式環境使用。  
3. 依照畫面指示將授權檔案 (`metadata.lic`) 嵌入至 Java 類別路徑中。

### 基本初始化與設定

將函式庫加入類別路徑後，請依照下列方式初始化：

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

## 如何從 PSD 圖像提取基本 EXIF 中繼資料屬性

本節說明如何載入 PSD 檔案、存取 EXIF 容器，並讀取最常見的標籤，例如 **artist**、**copyright** 與 **software**。此流程包括建立 `Metadata` 實例、呼叫 `getExif()`，再以簡單的 getter 方法取得各屬性。

### 步驟實作

1. **建立指向 PSD 檔案的 `Metadata` 實例**。  
2. **呼叫 `getExif()`** 以取得 EXIF 容器。  
3. **讀取個別屬性**，如 `getArtist()`、`getCopyright()` 與 `getSoftware()`。  
4. **根據應用程式邏輯列印或儲存** 這些值。

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

> **專業提示：**`Metadata` 物件會自動偵測檔案格式，因此您可以在 JPEG 或 TIFF 檔案上直接重複使用相同程式碼，無需修改。

## 如何從 PSD 圖像提取 EXIF IFD 套件屬性

IFD（Image File Directory）區段包含更深入的技術細節，如 **camera serial number**、**lens model** 與 **user comments**。`Ifd0` 代表主要的 Image File Directory，內含基本的相機資訊。提取這些欄位對於鑑識分析或高精度目錄編制相當有用。

### 實作步驟

1. **重複使用前一節的 `Metadata` 實例**。  
2. **透過 `metadata.getExif().getIfd0()` 前往 IFD 容器**。  
3. **讀取屬性**，如 `getBodySerialNumber()` 與 `getUserComment()`。  
4. **輸出資料** 或映射至您的領域模型。

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

## 如何從 PSD 檔案取得 GPS 資料（緯度、經度）

許多現代相機會將 GPS 座標嵌入 EXIF 區塊。`GpsInfo` 保存從 EXIF 資料中提取的地理座標。呼叫 `metadata.getExif().getGpsInfo()` 後，再使用 `getLatitude()`、`getLongitude()` 與 `getAltitude()` 即可取得精確位置資料——無需額外解析。

### 詳細步驟

1. **取得 GPS 資訊物件**：`GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **讀取緯度與經度**：`gps.getLatitude()` 會回傳十進位度的 `double`。  
3. **處理缺失資料**：若標籤不存在，API 會回傳 `null`，因此需防範 `NullPointerException`。  

> **常見陷阱：**某些 PSD 檔案以有理數形式儲存 GPS 座標；函式庫會自動正規化，但較舊的檔案可能需要手動轉換。  

## 常見問題與疑難排解

| 症狀 | 可能原因 | 解決方案 |
|---------|--------------|-----|
| `Unsupported format` exception | 使用較舊的 GroupDocs.Metadata 版本，無法辨識 PSD | 升級至 24.12 版或更新版本 |
| `NullPointerException` when calling `getArtist()` | 來源檔案中未包含 EXIF 標籤 | 在讀取前檢查 `metadata.getExif().hasArtist()` |
| License error after 30 days | 類別路徑上找不到授權檔案 | 將 `metadata.lic` 放置於 `src/main/resources`，或使用 `Metadata.setLicense("path/to/license")` 設定 |

## 常見問答

**Q: 我可以從受密碼保護的 PSD 檔案提取 EXIF 中繼資料嗎？**  
A: 可以。使用 `new Metadata("file.psd", "password")` 載入檔案，然後照常存取 EXIF 資料。

**Q: GroupDocs.Metadata 是否支援批次處理大量 PSD 檔案？**  
A: 當然支援。可在迴圈中建立 `Metadata` 物件，或使用 `MetadataCollection` 輔助工具有效率地處理目錄。

**Q: 官方支援哪些 Java 版本？**  
A: 完全測試過的版本為 Java 8 至 Java 21。函式庫僅使用標準 API，因而可在任何相容的 JVM 上運作。

**Q: 能否將 EXIF 資料寫回 PSD 檔案？**  
A: 可以。透過 `Exif` 物件修改屬性後，呼叫 `metadata.save("output.psd")` 以儲存變更。

**Q: 函式庫能處理多大的 PSD 檔案而不會耗盡記憶體？**  
A: 由於採用低記憶體架構，GroupDocs.Metadata 以串流方式處理資料，在一般配備 8 GB 記憶體的機器上可處理最高 **2 GB** 的檔案。

## 結論

您現在已了解如何使用 GroupDocs.Metadata for Java 從 PSD 檔案 **提取 EXIF** 中繼資料，涵蓋基本標籤、進階 IFD 與 GPS 資訊。將這些程式碼片段整合至影像處理流程，可自動化目錄編制、合規檢查或基於位置的服務。欲進一步探索，可嘗試從其他支援的格式（JPEG、TIFF、PNG）提取中繼資料，或實驗寫回功能以嵌入自訂標籤。

---

**最後更新：** 2026-08-10  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

## 相關教學

- [使用 GroupDocs.Metadata 在 Java 中提取 PSD 檔案的影像資源：完整指南](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [使用 GroupDocs.Metadata for Java 提取 PSD 標頭與圖層資訊：完整指南](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [使用 GroupDocs.Metadata in Java 提取 MakerNote 屬性作為 TIFF/EXIF 標籤](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)