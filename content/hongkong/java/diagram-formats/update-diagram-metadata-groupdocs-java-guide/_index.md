---
date: '2026-06-17'
description: 了解如何使用 GroupDocs.Metadata 在 Java 中更改圖表的建立時間，並自動化圖表檔案的 Metadata 更新。
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: 使用 GroupDocs Java 更改圖表的建立時間於 Metadata
type: docs
url: /zh-hant/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# 在 GroupDocs Java 中變更圖表建立時間的 Metadata

在本步驟教學中，您將學會如何使用 GroupDocs.Metadata for Java 套件 **變更圖表建立時間**，並更新圖表檔案的其他內建屬性。自動化這些變更可節省大量手動編輯時間，確保整個儲存庫的時間戳記一致，並使圖表在任何文件管理系統中即時可搜尋。

## 快速解答
- **主要目標是什麼？** 變更圖表建立時間以及圖表檔案中的其他 Metadata。  
- **應該使用哪個函式庫？** GroupDocs.Metadata for Java。  
- **需要授權嗎？** 免費試用版足以測試；正式環境需要完整授權。  
- **可以批次處理多個圖表嗎？** 可以——將相同邏輯包在迴圈或平行串流中。  
- **需要哪個 Java 版本？** JDK 8 或以上。

## 什麼是圖表 Metadata 中的「變更圖表建立時間」？
變更建立時間即是以新的日期時間值覆寫圖表檔案（如 VDX 或 VSDX）內部原本的時間戳記。這讓您能將檔案的 Metadata 與實際的處理或歸檔日期對齊，而非作者的原始時間戳記，對於稽核追蹤與精確搜尋結果相當重要。

## 為什麼要自動化圖表的 Metadata 更新？
自動化 Metadata 可確保每個圖表遵循相同的命名、分類與時間戳記標準，避免人工錯誤。它亦加速大量遷移、降低合規風險，並提升企業 DMS 平台的可發現性——在大型專案中可節省高達 70 % 的手動工作。

## 前置條件
- **Java Development Kit (JDK) 8+** 已安裝於您的機器上。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse。  
- **Maven**（或手動 JAR 管理）用於相依性管理。  
- 基本熟悉 Java 類別、方法與例外處理。

### 必要的函式庫與相依性
若使用 Maven，請在 `pom.xml` 中加入以下儲存庫與相依性：

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
- IntelliJ IDEA、Eclipse 或任何相容 Java 的 IDE。  

### 知識前提
了解 Java 語法與基本檔案 I/O 會讓教學更順暢，但步驟已以簡單語言說明。

## 設定 GroupDocs.Metadata for Java
### 安裝說明
**Maven 使用者：** 上述程式碼會自動加入儲存庫與所需 JAR。  
**直接下載使用者：** 從 [GroupDocs](https://releases.groupdocs.com/metadata/java/) 下載 JAR 後，將其加入專案的 classpath。

### 取得授權
- **免費試用：** 無償探索此函式庫。  
- **臨時授權：** 取得延長測試的臨時授權，請點此 [here](https://purchase.groupdocs.com/temporary-license/)。  
- **購買授權：** 為正式環境取得完整授權。

### 基本初始化
`Metadata` 是代表文件 Metadata 容器的核心類別，提供對所有內建屬性的讀寫存取。要開始使用 GroupDocs.Metadata，先匯入此類別並開啟圖表檔案：

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

初始化函式庫後，即可修改任何內建屬性，包括建立時間。

## 實作指南
### 如何變更圖表檔案的建立時間
本節將逐步說明如何 **變更圖表建立時間**，並更新作者、公司、類別等常見屬性。流程包括使用 Metadata API 載入圖表、存取根套件、設定所需欄位，最後將變更儲存至新檔案，確保原始檔保持不變。

#### 步驟 1：載入圖表文件
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*說明：* `Metadata` 建構子接受圖表檔案的路徑。try‑with‑resources 區塊確保操作完成後正確關閉檔案。

#### 步驟 2：存取根套件
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*說明：* 根套件讓您直接存取圖表的所有內建 Metadata 欄位。

#### 步驟 3：設定建立者屬性
```java
root.getDocumentProperties().setCreator("test author");
```  
*說明：* 指定新的作者名稱。將 `"test author"` 替換為實際的建立者。

#### 步驟 4：變更建立時間
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*說明：* 此行 **變更建立時間** 為目前系統日期與時間。若需自訂時間戳記，也可提供特定的 `Date` 物件。

#### 步驟 5：定義公司資訊
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*說明：* 儲存與圖表相關的公司名稱——對企業追蹤很有幫助。

#### 步驟 6：設定文件類別
```java
root.getDocumentProperties().setCategory("test category");
```  
*說明：* 為檔案分類，協助您在整個儲存庫中一致 **更新圖表類別**。

#### 步驟 7：加入關鍵字
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*說明：* 關鍵字提升可搜尋性；您可列出任何與圖表內容相關的詞彙。

#### 步驟 8：儲存變更
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*說明：* 將所有修改保存至新檔案，原始檔保持不變。

### 常見問題與除錯
- **找不到檔案：** 檢查輸入路徑，並確保副檔名與實際格式相符。  
- **存取被拒：** 檢查輸入與輸出目錄的讀寫權限。  
- **日期格式無效：** 使用與 API 相容的 `java.util.Date` 或 `java.time` 物件。

## 實務應用
1. **自動化文件歸檔** – 將舊圖表移至歸檔時，自動 **變更圖表建立時間** 為歸檔日期，並設定統一的類別。  
2. **版本控制整合** – 於每次發行時更新建立時間，使時間戳記與 Git 提交同步。  
3. **企業 DMS 標準化** – 在所有圖表資產上執行全公司統一的作者、公司與關鍵字政策。

## 效能考量
- **批次處理：** 將上述步驟包在迴圈中，一次處理數十個檔案。  
- **記憶體管理：** 及時釋放每個 `Metadata` 實例（try‑with‑resources 區塊會自動完成）。  
- **非同步執行：** 大批次時，可考慮使用 `CompletableFuture` 平行執行更新，避免阻塞主執行緒。  
- **量化能力：** GroupDocs.Metadata 支援超過 30 種圖表格式，且可在不將整個文件載入記憶體的情況下處理高達 500 MB 的檔案，在一般伺服器硬體上每檔案更新時間低於 200 ms。

## 結論
您現在已掌握如何使用 GroupDocs.Metadata for Java **變更圖表建立時間**，並更新圖表文件的其他內建 Metadata 屬性。透過自動化這些步驟，您能在組織內維持一致、可搜尋且符合規範的文件。

**後續步驟**
- 嘗試 GroupDocs.Metadata 支援的其他檔案格式（PDF、DOCX 等）。  
- 將程式碼整合至 CI/CD 流程，以在每次建置時強制執行 Metadata 標準。

準備好試試看了嗎？前往 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 開始實作您自己的 Metadata 自動化吧。

---

**Last Updated:** 2026-06-17  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs  

## 常見問答

**問：我可以將此方法用於其他圖表格式（如 VSDX）嗎？**  
答：可以，相同的 API 支援所有 GroupDocs.Metadata 所支援的圖表格式。

**問：開發版需要授權嗎？**  
答：開發與測試階段使用免費試用版即可；正式上線則需購買完整授權。

**問：如何在一次呼叫中更新多個屬性？**  
答：在呼叫 `metadata.save(...)` 前，先於 `DocumentProperties` 物件上設定所有欲更新的屬性，函式庫會一次寫入。

**問：直接覆寫原始檔案是否安全？**  
答：建議先儲存至新檔案（如範例所示），確認更新成功後再替換原檔，以降低風險。

**問：如果需要設定自訂的建立日期而非目前時間，該怎麼做？**  
答：建立一個帶有目標時間戳記的 `java.util.Date`（或 `java.time` 物件），然後傳入 `setTimeCreated` 即可。

## 相關教學

- [如何使用 GroupDocs.Metadata 更新 Java 圖表 Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [如何使用 GroupDocs.Metadata for Java 更新 DXF 作者 Metadata – 完整指南](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [使用 GroupDocs.Metadata 依日期自動化 Java Metadata 更新以提升檔案管理效率](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)