---
date: '2026-03-22'
description: 了解如何使用 GroupDocs.Metadata for Java 更改 Excel 的建立日期並更新 Excel 元資料。請遵循此一步一步的指南，向
  Excel 添加關鍵字並修改文件屬性。
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: 使用 GroupDocs.Metadata 在 Java 中更改 Excel 建立日期
type: docs
url: /zh-hant/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# 使用 GroupDocs.Metadata 在 Java 中變更 Excel 建立日期

在現代以數據為驅動的環境中，**變更 Excel 建立日期** 並保持其他中繼資料即時更新，可大幅提升文件組織、可搜尋性與合規性。無論您處理的是財務報告、專案追蹤表或歸檔資料，正確的中繼資料可確保相關人員在適當的時間找到正確的檔案。本教學將指引您如何在 Java 應用程式中使用 GroupDocs.Metadata 函式庫來 **變更 Excel 建立日期**、**為 Excel 加入關鍵字**，以及 **修改 Excel 文件屬性**。

## 快速解答
- **我可以變更 Excel 檔案的建立日期嗎？** 可以，使用 GroupDocs.Metadata 的 `setCreatedTime`。  
- **哪個函式庫支援在 Java 中更新 Excel 中繼資料？** GroupDocs.Metadata for Java。  
- **我需要授權嗎？** 免費試用可用於評估；正式環境需購買永久授權。  
- **需要哪個 Java 版本？** JDK 8 或更高。  
- **我可以為 Excel 工作簿加入自訂關鍵字嗎？** 當然可以—使用文件屬性的 `setKeywords`。  

## 什麼是「變更 Excel 建立日期」？

變更 Excel 建立日期是指更新儲存在工作簿檔案內的內建 *Created* 屬性。此屬性屬於標準 Office Open XML 中繼資料的一部份，且可透過程式編輯而不會改變實際工作表內容。

## 為什麼要使用 GroupDocs.Metadata 處理 Excel 中繼資料？

GroupDocs.Metadata 提供高階、型別安全的 API，抽象化了 Office Open XML 格式所需的低階 XML 處理。它讓您能夠：

- **更新核心屬性**，如作者、公司與建立日期，只需一次呼叫。  
- **為 Excel 加入關鍵字**，以提升在 SharePoint、OneDrive 或本機檔案系統中的搜尋結果。  
- **修改 Excel 文件屬性**，無需在 Excel 中開啟工作簿，從而節省時間與資源。  

## 前置條件
- Java Development Kit (JDK) 8 或更新版本。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 具備基本的 Java 檔案 I/O 知識。  

## 設定 GroupDocs.Metadata（Java 版）

### 安裝

將 GroupDocs.Metadata 的 Maven 儲存庫與相依性加入您的 `pom.xml`：

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

或者，若您偏好手動設定，也可以[直接下載最新版本](https://releases.groupdocs.com/metadata/java/)。

### 取得授權

GroupDocs 提供免費試用以供評估。正式環境使用時，請向供應商取得臨時或永久授權。詳情請參閱[GroupDocs 購買頁面](https://purchase.groupdocs.com/temporary-license/)。

#### 基本初始化

在您的 Java 原始檔案中匯入必要的類別：

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## 步驟說明實作

### 步驟 1：開啟 Excel 工作簿

提供來源工作簿的路徑並建立 `Metadata` 實例。`try‑with‑resources` 區塊會自動關閉檔案句柄。

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### 步驟 2：更新內建中繼資料屬性

現在您可以 **變更 Excel 建立日期**，設定作者、公司、類別，並 **為 Excel 加入關鍵字**。`new Date()` 會取得目前時間戳記，您亦可自行提供任意 `java.util.Date`。

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **專業提示：** 使用一致的關鍵字命名規則（例如 `project:Q2, finance, confidential`）可提升未來搜尋的效能。

### 步驟 3：儲存更新後的工作簿

指定輸出路徑並寫入變更。原始檔案保持不變，方便審計追蹤。

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## 常見問題與解決方案

| 問題 | 為何發生 | 解決方法 |
|-------|----------------|-----|
| **檔案路徑錯誤** | 相對或絕對路徑不正確 | 再次確認 `inputFilePath` 與 `outputFilePath`。使用 `Paths.get(...)` 以取得跨平台的路徑。 |
| **函式庫版本不相容** | 使用較舊的 GroupDocs.Metadata，未支援 `setCreatedTime` 方法 | 升級至最新版本（如 Maven 片段所示）。 |
| **缺少授權** | 試用期已過 | 套用臨時授權或透過購買頁面取得完整授權。 |
| **大型工作簿記憶體使用量** | 載入巨大的 Excel 檔案會佔用堆積記憶體 | 分批處理檔案，必要時增加 JVM 堆積 (`-Xmx`)。 |

## 常見問答

**Q: GroupDocs.Metadata 支援哪些 Java 版本？**  
A: 完全支援 Java 8 及更新版本。

**Q: 更新中繼資料時該如何處理例外？**  
A: 將程式碼包在 `try‑catch` 區塊中，並記錄 `MetadataException` 以捕捉任何 I/O 或格式錯誤。

**Q: 我可以在一次執行中更新多個 Excel 檔案嗎？**  
A: 可以，遍歷檔案路徑集合，但對於大量批次需留意記憶體使用。

**Q: 是否可以還原已修改的中繼資料？**  
A: 在套用更新前保留原始工作簿的備份，必要時即可還原。

**Q: 我可以在哪裡找到更詳細的文件？**  
A: 請參閱官方指南 [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/)。

## 實務應用

1. **財務審計** – 記錄誰在何時修改工作簿，提供審計追蹤。  
2. **專案管理** – 使用專案相關關鍵字標記試算表，以快速檢索。  
3. **資料歸檔** – 保留原始建立日期與公司資訊，以符合合規要求。  

## 效能建議

- 限制每次執行的中繼資料操作，以免過度消耗記憶體。  
- 及時關閉 `Metadata` 物件（`try‑with‑resources` 模式會自動完成）。  
- 對於極大型工作簿，建議在背景執行緒中處理，以保持 UI 響應。  

## 結論

現在您已了解如何使用 GroupDocs.Metadata 在 Java 中 **變更 Excel 建立日期**、**為 Excel 加入關鍵字**，以及 **修改 Excel 文件屬性**。此功能讓您能夠使試算表保持良好組織、易於搜尋，並符合內部治理政策的合規要求。下一步，您可以探索其他中繼資料功能，如自訂屬性或批次處理，以進一步簡化文件管理工作流程。

---

**最後更新：** 2026-03-22  
**測試版本：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

**資源**
- [文件說明](https://docs.groupdocs.com/metadata/java/)
- [API 參考](https://reference.groupdocs.com/metadata/java/)
- [下載 GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [GitHub 程式庫](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [免費支援論壇](https://forum.groupdocs.com/c/metadata/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)