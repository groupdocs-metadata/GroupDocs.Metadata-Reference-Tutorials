---
date: '2026-01-19'
description: 學習如何在 Java 中使用 GroupDocs.Metadata 更改圖表檔案的建立時間並自動更新中繼資料。
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: 使用 GroupDocs Java 更改圖表元資料的建立時間
type: docs
url: /zh-hant/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# 使用 GroupDocs Java 更改圖表元資料的建立時間

手動更新諸如建立者、**變更建立時間**和類別等元資料屬性可能相當繁瑣。使用 GroupDocs.Metadata Java 函式庫自動化此流程，您即可在單一步驟中 **變更建立時間** 以及其他內建屬性。本指南將帶您設定函式庫、更新圖表元資料，並提供最佳實踐的效能建議，讓您的文件保持一致且易境需購買完整授權。  
- **可以批次處理多個圖表嗎？** 可以——在迴 或以上。

## 圖表元資料中的「變更建立時間」是什麼？
變更建立時間指的是將圖表檔案（例如 VDX、VSDX始時間戳記覆寫為新的日期。當您需要檔案的元資料反映實際的處理日期，而非原始的創建日期時，此功能相當有用。

## 為什麼要自動化圖表的元資料更新？
- **一致性：** 確保每個檔案遵循相同的命名與分類規則。  
- **可搜尋性：** 更新的關鍵字與類別提升在 DMS 解決方案中的文件搜尋效果。  
- **合規性：** 透過確保時間戳記正確，協助符合稽核需求。  

## 前置條件
- **Java Development Kit (JDK) 8+** 已安裝。  
- **IDE**（如 IntelliJ IDEA 或 Eclipse）。  
- **Maven**（或手動 JAR 管理）用於相依性管理。  
- 具備 Java 類別、方法與例外處理的基本知識。  

### 必要的函式庫與相依性
如果使用 Maven，請在 `pom.xml` 檔案中加入以下儲存庫與相依性：

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
如果您偏好直接下載，請前往 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 取得最新版本。

### 環境設定
- JDK 8 或更新版本。  
- IntelliJ IDEA、Eclipse，或任何相容 Java 的 IDE。  

### 知識前置條件
了解 Java 語法與基本檔案 I/O 會讓本教學更順暢，但所有步驟皆以簡單語言說明。

## 設定 GroupDocs.Metadata for Java
### 安裝說明
**Maven 使用者：** 上面的程式碼片段會自動加入儲存庫與所需的 JAR。  
**直接下載使用者：** 從 [GroupDocs](https://releases.groupdocs.com/metadata/java/) 下載 JAR 後，將其加入專案的 classpath。

### 授權取得
- **免費試用：** 無償探索函式庫。  
- **臨時授權：** 取得延長測試用的臨時授權，請點此 [here](https://purchase.groupdocs.com/temporary-license/)。  
- **購買：** 為正式環境取得完整授權。  

### 基本初始化
開始使用 GroupDocs.Metadata 時，先匯入類別並開啟圖表檔案：

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

函式庫初始化後，您即可修改任何內建屬性，包括建立時間。

## 實作指南
### 如何在圖表檔案中變更建立時間
本節將逐步說** 以及更新其他常見屬性（如作者、公司與類別）的每個步驟。

#### 步驟 1：載入圖表文件
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*說明：* `Metadata` 建構子接受圖表檔案的路徑。`try‑with‑resources` 區塊確保操作完成後正確關閉檔案。

#### 步驟 2：存取根套件
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*說明：* 根套件讓您直接存取圖表的所有內建元資料欄位。

#### 步驟 3：設定建立者屬性
```java
root.getDocumentProperties().setCreator("test author");
```
*說明：* 指定新的作者名稱。將 `"test author"` 替換為實際的建立者。

#### 步驟 4：**變更建立時間**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*說明：* 這行程式碼 **變更建立時間** 為目前系統日期與時間。若需自訂時間戳記，也可傳入特定的 `Date` 例項。

#### 步驟 5：定義公司資訊
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*說明：* 儲存與圖表相關的公司名稱——對企業追蹤很有幫助。

#### 步驟 6：設定文件類別
```java
root.getDocumentProperties().setCategory("test category");
```
*說明：* 為檔案設定類別，協助您在整個儲存庫中 **更新圖表類別**，保持一致性。

#### 步驟 7：新增關鍵字
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*說明：* 關鍵字提升可搜尋性；您可以列出任何與圖表內容相關的詞彙。

#### 步驟 8：儲存變更
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*說明：* 將所有修改持久化至新檔案，保留原始檔不變。

### 常見問題與除錯
- **找不到檔案：** 請確認輸入路徑，並確保檔案副檔名與實際格式相符。  
- **存取被拒：** 檢查輸入與輸出目錄的讀寫權限。  
- **日期格式無效：** 使用與 API 相容的 `java.util.Date` 或 `java.time` 物件。  

## 實務應用
1. **自動化文件歸檔** – 將舊圖表移至歸檔時，自動 **變更建立時間** 為歸檔日期，並設定統一的類別。  
2. **版本控制整合** – 在每次發行時更新建立時間，使時間戳記與 Git 提交同步。  
3. **企業 DMS 標準化** – 在所有圖表資產中執行全公司範圍的作者、公司與關鍵字政策。  

## 效能考量
- **批次處理：** 將上述步驟包在迴圈中，一次處理數十個檔案。  
- **記憶體管理：** 及時釋放每個 `Metadata` 實例（`try‑with‑resources` 區塊會自動完成）。  
- **非同步執行：** 大批次時，可考慮使用 `CompletableFuture` 平行執行更新，避免阻塞主執行緒。  

## 結論
您現在已了解如何使用 GroupDocs.Metadata for Java **變更建立時間**，以及更新圖表文件的其他內建元資料屬性。透過自動化這些步驟，您能在組織內維持一致、可搜尋且符合規範的文件。

**下一步**
- 嘗試 GroupDocs.Metadata 支援的其他檔案格式（PDF、DOCX 等）。  
- 將程式碼整合至 CI/CD 流程，以在每次建置時強制執行元資料標準。

準備好試試看了嗎？前往 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 開始實作您自己的元資料自動化吧。

---

**最後更新：** 2026-01-19  
**測試版本：** GroupDocs.Metadata 24.12  
**作者：** GroupDocs  

## 常見問答

**Q: 我可以將此方法用於其他圖表格式（如 VSDX）嗎？**  
A: 可以，相同的 API 可用於 GroupDocs.Metadata 支援的所有圖表格式。

**Q: 開發版需要授權部署則Q: 如何在一次呼叫中更新多個屬性？**  
A: 在呼叫 `metadata.save(...)` 之前，先於 `DocumentProperties` 物件設定各屬性；函式庫會一次寫入全部。

**Q: 覆寫原始檔案是否安全？**  
A: 建議先儲存為新檔案（如示範），以避免資料遺失，必要時再取代原檔。

**Q: 如果需要設定自訂的建立日期而非目前時間，該怎麼做？**  
A: 建立帶有目標時間戳記的 `java` 例項），並傳入 `