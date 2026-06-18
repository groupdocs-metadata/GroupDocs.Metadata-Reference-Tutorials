---
date: '2026-02-19'
description: 學習如何使用 GroupDocs.Metadata for Java 讀取 SevenZip 元資料，包括如何取得壓縮大小以及其他壓縮檔屬性。
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: 如何在 Java 中使用 GroupDocs.Metadata 讀取 SevenZip 元資料
type: docs
url: /zh-hant/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Metadata 讀取 SevenZip 元資料

如果您需要在 Java 應用程式中 **read sevenzip metadata java**，您來對地方了。在本教學中，我們將示範如何使用 **GroupDocs.Metadata** 取得檔名、壓縮大小、未壓縮大小、修改日期等資訊——正是您在備份驗證、同步或儲存空間最佳化任務中所需的資料。

## 介紹

在使用 Java 存取與讀取 SevenZip 壓縮檔的元資料屬性時感到困難嗎？本教學將指導您使用 **GroupDocs.Metadata** 的流程。這個功能強大的函式庫可簡化直接從壓縮檔中提取檔名、大小與修改日期等關鍵資訊的步驟。

## 快速答覆

- **我應該使用哪個函式庫？** GroupDocs.Metadata for Java  
- **我可以列出 SevenZip 壓縮檔內的檔案嗎？** Yes – use `getSevenZipPackage().getFiles()`  
- **我需要授權嗎？** A free trial works for evaluation; a full license is required for production  
- **支援哪個 Java 版本？** JDK 8 or higher  
- **需要 Maven 嗎？** Not mandatory, but Maven simplifies dependency management  

## 在 Java 中「how to read sevenzip」是什麼？

讀取 SevenZip 元資料表示開啟 `.7z` 容器，列舉每個項目，並取得 **compressed size**、**uncompressed size**、**file name** 與 **modification date** 等屬性，而不必實際解壓縮檔案。

## read sevenzip metadata java

在專屬標題中使用主要關鍵字有助於讀者與搜尋引擎了解本指南的重點。以下我們將深入說明您需要 **read sevenzip metadata java** 的具體步驟，以高效完成。

## 為何使用 GroupDocs.Metadata Java 進行元資料擷取？

- **Unified API** – 可在數十種壓縮與文件格式間運作  
- **No external tools** – 所有操作皆在您的 Java 程序內完成  
- **Performance‑focused** – 僅讀取進行 metadata extraction java 任務所需的標頭資訊  
- **Robust licensing** – 提供試用版，商業使用需完整授權  

## 前置條件

在深入使用 **GroupDocs.Metadata for Java** 之前，請確保開發環境已正確設定。您需要以下項目：

- **Java Development Kit (JDK)：** 版本 8 或以上。  
- **Maven：** 建議用於管理相依性，亦可手動加入 JAR。  
- **Basic Java Knowledge：** 熟悉類別、方法與例外處理。  

## 設定 GroupDocs.Metadata for Java

若要使用 GroupDocs.Metadata，請透過 Maven 或直接下載函式庫將其加入專案。

### 使用 Maven

在您的 `pom.xml` 檔案中加入以下設定：

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

或者，從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新版本。

#### 取得授權

1. **Free Trial：** 使用免費試用版測試 GroupDocs.Metadata 的功能。  
2. **Temporary License：** 若需延長評估期間，可申請臨時授權。  
3. **Purchase：** 長期使用時，建議購買完整授權。  

設定完成後，讓我們繼續實作元資料讀取功能。

## 實作指南

### 從 SevenZip 壓縮檔存取元資料

在本節中，我們將從 SevenZip 壓縮檔中提取並列印檔名與大小等元資料屬性。

#### 步驟 1：初始化 Metadata 物件

首先，以 SevenZip 檔案路徑初始化 `Metadata` 物件，告訴 GroupDocs 要處理哪個檔案。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 步驟 2：取得根套件

接著，存取壓縮檔的根套件，以作為所有檔案與屬性的入口點。

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **為何使用 `getRootPackageGeneric()`？** 它提供壓縮檔內容的通用檢視，使您能更輕鬆遍歷條目，而無需關注特定檔案格式。

#### 步驟 3：遍歷壓縮檔條目

取得根套件後，遍歷每個條目以提取元資料屬性。這包括取得名稱、壓縮大小與修改日期等資訊。

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **為何提取這些屬性？** 瞭解檔案大小有助於儲存管理，修改日期則對同步任務至關重要。`getCompressedSize()` 呼叫是 Java 取得每個條目 **get compressed size java** 的方式。

#### 步驟 4：清理資源

最後，請確保釋放 Metadata 物件，以解除 GroupDocs.Metadata 所佔用的資源。

```java
} finally {
    metadata.dispose();
}
```

- **為何要釋放？** 正確釋放物件可防止長時間執行的應用程式發生記憶體洩漏。

## 實務應用

了解如何 **read sevenzip metadata java** 具備多項實務效益：

1. **Data Backup Management：** 快速驗證備份壓縮檔的完整性與一致性。  
2. **File Synchronization Tools：** 依據修改日期判斷哪些檔案需要更新。  
3. **Storage Optimization：** 比較壓縮與未壓縮大小，以規劃容量需求。  

可與其他系統整合，將自動化的元資料擷取納入更大型的資料管理工作流程中。

## 效能考量

在使用 GroupDocs.Metadata 處理大型壓縮檔時，請留意以下建議：

- **Batch Processing：** 以批次方式處理檔案，以有效管理記憶體使用量。  
- **Efficient Exception Handling：** 使用 try‑with‑resources 進行自動資源管理。  
- **Asynchronous Processing：** 針對大量工作負載實作非同步處理技術。  

## 常見問題與解決方案

| 問題 | 解決方案 |
|-------|----------|
| **`NullPointerException` when accessing a file** | 確認壓縮檔路徑正確且檔案未損壞。 |
| **Memory spikes on huge archives** | 啟用批次處理或增加 JVM 堆積大小 (`-Xmx`)。 |
| **License not recognized** | 確保授權檔案放置於應用程式的工作目錄，或透過 `License.setLicense(path)` 設定。 |

## 常見問答

**Q:** GroupDocs.Metadata 是什麼？  
**A:** 它是一個用於處理不同檔案格式元資料的 Java 函式庫，亦支援 SevenZip 壓縮檔。

**Q:** 是否可以在不使用 Maven 的情況下使用 GroupDocs.Metadata？  
**A:** 可以，您可從官方網站下載 JAR，並將其加入專案的 classpath。

**Q:** 如何有效處理大型壓縮檔？  
**A:** 實作批次處理或使用非同步串流以降低記憶體消耗。

**Q:** 在哪裡可以找到更詳細的說明？  
**A:** 請參閱 [official documentation](https://docs.groupdocs.com/metadata/java/) 以取得完整的 API 參考。

**Q:** 若使用函式庫時遇到問題該怎麼辦？  
**A:** 可在 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 社群詢問。

## 資源

- **Documentation：** Explore more at [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **API Reference：** Check detailed API information at [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download：** Get the latest version from [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub Repository：** Access code samples on [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Free Support Forum：** Join discussions or ask questions at [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**最後更新：** 2026-02-19  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs