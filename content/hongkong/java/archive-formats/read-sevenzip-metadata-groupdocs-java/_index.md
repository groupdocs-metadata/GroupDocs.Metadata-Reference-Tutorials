---
date: '2025-12-20'
description: 學習如何使用 GroupDocs.Metadata for Java 讀取 SevenZip 壓縮檔的元資料，這是元資料提取 Java 專案中的關鍵步驟。
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: 如何在 Java 中使用 GroupDocs.Metadata 讀取 SevenZip 元資料
type: docs
url: /zh-hant/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Metadata 讀取 SevenZip 中的 Metadata

如果您需要在 Java 應用程式中 **讀取 SevenZip** 壓縮檔資訊，您來對地方了。在本教學中，我們將示範如何使用 **GroupDocs.Metadata** 取得檔名、大小、日期等資料——正是備份驗證、同步或儲存最佳化任務所需的資訊。

## 介紹

在使用 Java 存取 SevenZip 壓縮檔的 Metadata 屬性時感到困難嗎？本教學將指引您使用 **GroupDocs.Metadata** 的流程。這個功能強大的函式庫可簡化直接從壓縮檔中擷取檔名、大小、修改日期等關鍵資訊。

在本文中，我們將示範如何運用 **GroupDocs.Metadata for Java** 高效存取 SevenZip 檔案的 Metadata 屬性。

### 您將學會
- 在 Java 專案中設定 GroupDocs.Metadata  
- 使用特定方法與類別從 SevenZip 壓縮檔讀取 Metadata  
- 實作範例，抽取檔案名稱、壓縮大小、修改日期等關鍵屬性  

## 快速回答
- **應該使用哪個函式庫？** GroupDocs.Metadata for Java  
- **可以列出 SevenZip 壓縮檔內的檔案嗎？** 可以 – 使用 `getSevenZipPackage().getFiles()`  
- **需要授權嗎？** 免費試用可用於評估；正式環境需購買正式授權  
- **支援哪個 Java 版本？** JDK 8 或以上  
- **必須使用 Maven 嗎？** 非必須，但 Maven 可簡化相依管理  

## 在 Java 中「讀取 SevenZip」是什麼意思？
讀取 SevenZip Metadata 意指開啟 `.7z` 容器、列舉每個條目，並取得 **壓縮大小**、**未壓縮大小**、**檔名**、**修改日期** 等屬性，而不必實際解壓檔案。

## 為何使用 GroupDocs.Metadata Java 進行 Metadata 抽取？
- **統一 API** – 可跨數十種壓縮與文件格式使用  
- **無需外部工具** – 全部操作皆在 Java 程序內完成  
- **效能導向** – 僅讀取所需的標頭資訊以執行 metadata 抽取任務  
- **授權彈性** – 提供試用版，正式版適用於商業使用  

## 前置條件

在深入 **GroupDocs.Metadata for Java** 之前，請先確保開發環境已正確設定。您需要以下項目：

- **Java Development Kit (JDK)：** 8 版或以上。  
- **Maven：** 建議用於相依管理，亦可手動加入 JAR。  
- **基本 Java 知識：** 熟悉類別、方法與例外處理。  

## 設定 GroupDocs.Metadata for Java

要使用 GroupDocs.Metadata，請透過 Maven 或直接下載函式庫加入專案。

### 使用 Maven

在 `pom.xml` 中加入以下設定：

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

或是從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新版本。

#### 取得授權

1. **免費試用：** 先使用免費試用版測試 GroupDocs.Metadata 功能。  
2. **臨時授權：** 若需延長評估期間，可申請臨時授權。  
3. **購買授權：** 長期使用時，請考慮購買正式授權。  

完成設定後，我們即可進入實作 metadata 讀取功能的步驟。

## 實作指南

### 從 SevenZip 壓縮檔存取 Metadata

本節將示範如何從 SevenZip 壓縮檔抽取並印出檔名、大小等 Metadata 屬性。

#### 步驟 1：初始化 Metadata 物件

先以 SevenZip 檔案路徑建立 `Metadata` 物件，告訴 GroupDocs 要處理哪個檔案。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 步驟 2：取得根套件 (Root Package)

接著，存取壓縮檔的根套件，作為所有檔案與屬性的入口點。

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **為何使用 `getRootPackageGeneric()`？** 它提供壓縮檔內容的通用視圖，讓您在不關心特定檔案格式的情況下，輕鬆遍歷條目。

#### 步驟 3：遍歷壓縮檔條目

取得根套件後，遍歷每個條目以抽取 Metadata 屬性。此步驟會取得名稱、壓縮大小與修改日期等資訊。

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

- **為何抽取這些屬性？** 檔案大小有助於儲存管理，修改日期則在同步任務中相當關鍵。

#### 步驟 4：釋放資源

最後，務必釋放 `Metadata` 物件，以解除 GroupDocs.Metadata 佔用的資源。

```java
} finally {
    metadata.dispose();
}
```

- **為何需要釋放？** 正確釋放物件可防止長時間執行的應用程式發生記憶體泄漏。

## 實務應用

了解如何讀取 SevenZip Metadata 可帶來多項實務效益：

1. **資料備份管理：** 快速驗證備份壓縮檔的完整性與正確性。  
2. **檔案同步工具：** 依據修改日期判斷哪些檔案需要更新。  
3. **儲存最佳化：** 比較壓縮與未壓縮大小，以規劃容量需求。  

此功能亦可與其他系統整合，實現自動化的 Metadata 抽取，成為更大型資料管理工作流程的一部份。

## 效能考量

在使用 GroupDocs.Metadata 處理大型壓縮檔時，請留意以下建議：

- **批次處理：** 以批次方式處理檔案，降低記憶體使用。  
- **有效的例外處理：** 使用 try‑with‑resources 以自動管理資源。  
- **非同步處理：** 對於大量工作負載，可實作非同步技術。  

## 常見問題與解決方案

| 問題 | 解決方案 |
|------|----------|
| **存取檔案時拋出 `NullPointerException`** | 確認壓縮檔路徑正確且檔案未損毀。 |
| **大型壓縮檔導致記憶體激增** | 啟用批次處理或增加 JVM 堆疊大小 (`-Xmx`)。 |
| **授權未被識別** | 確認授權檔放置於應用程式工作目錄，或透過 `License.setLicense(path)` 設定。 |

## 常見問答

**Q：什麼是 GroupDocs.Metadata？**  
**A：** 這是一套用於處理多種檔案格式 Metadata 的 Java 函式庫，亦支援 SevenZip 壓縮檔。

**Q：可以不使用 Maven 嗎？**  
**A：** 可以，直接下載官方 JAR 並加入專案的 classpath 即可。

**Q：如何有效處理大型壓縮檔？**  
**A：** 採用批次處理或非同步串流，以限制記憶體消耗。

**Q：哪裡可以找到更詳細的說明文件？**  
**A：** 請參閱 [官方文件](https://docs.groupdocs.com/metadata/java/) 取得完整 API 參考。

**Q：若使用函式庫時遇到問題該怎麼辦？**  
**A：** 可在 [GroupDocs 支援論壇](https://forum.groupdocs.com/c/metadata/) 向社群求助。

## 資源

- **文件說明：** 前往 [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/) 瀏覽更多資訊  
- **API 參考：** 查看 [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/) 取得詳細 API 說明  
- **下載：** 從 [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/) 取得最新版本  
- **GitHub 程式庫：** 前往 [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) 瀏覽範例程式碼  
- **免費支援論壇：** 加入 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 參與討論或提問  

---

**最後更新：** 2025-12-20  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

---