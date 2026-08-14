---
date: '2026-05-27'
description: 了解如何在 Java 中使用 GroupDocs Maven 依賴設定 pptx CreatedTime，以更新 PowerPoint 中的中繼資料，並說明如何變更
  PPTX 建立日期。
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: 使用 GroupDocs Maven 依賴在 Java 中設定 PPTX CreatedTime
type: docs
url: /zh-hant/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# 在 Java 中使用 GroupDocs.Metadata 設定 PPTX CreatedTime

精確的中繼資料對於現代文件工作流程中的合規性與可搜尋性至關重要。使用 **GroupDocs.Metadata**，您可以以程式方式 **在 Java 中設定 PPTX CreatedTime**，讓您能夠 **變更 PPTX 建立日期**，同時處理作者或公司等內建屬性。本教學將帶您完成 Maven 設定、API 初始化、更新中繼資料以及儲存已修改的簡報——全部提供清晰、可投入生產環境的程式碼。

## 快速解答
- **哪個函式庫可在 Java 中更新 PowerPoint 中繼資料？** GroupDocs.Metadata 透過 GroupDocs Maven 依賴項。  
- **我可以設定 PPTX CreatedTime 屬性嗎？** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **生產環境需要授權嗎？** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **範例使用哪個建置工具？** Maven (you can also download the JAR manually).  
- **API 是否支援 Java 8 及更新版本？** Absolutely—GroupDocs.Metadata targets Java 8+.

## 什麼是 GroupDocs Maven 依賴項？

**GroupDocs Maven 依賴項** 是一個相容於 Maven 的倉庫條目，可將最新的 GroupDocs.Metadata 函式庫引入您的 Java 專案。它透過自動解析傳遞性函式庫來簡化相依管理，確保您始終使用最新且最安全的版本，並免除手動下載 JAR 或追蹤版本的需求。

## 為何使用 GroupDocs.Metadata 變更 PPTX 建立日期？

GroupDocs.Metadata 讓您能自動化、批次處理 PPTX 建立時間戳記的更新，確保每份簡報符合公司政策或法律要求。透過程式設定 CreatedTime 屬性，您可避免手動編輯、減少人為錯誤，並可將此變更整合至 CI/CD 流程或遷移腳本，實現無縫的文件管理。

## 前置條件
- 安裝 Java 8 或更新版本。  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 用於相依管理的 Maven。  
- 取得 GroupDocs 試用版或正式授權。

## 如何在 Java 中設定 PPTX CreatedTime？

`Metadata` 類別代表一個文件，並提供存取其中繼資料屬性的功能。

使用 `new Metadata("presentation.pptx")` 載入您的 PowerPoint 檔案，取得根套件，呼叫 `setCreatedTime` 並傳入所需的 `java.util.Date`，最後呼叫 `save` 寫入變更。此端到端流程會在保留所有投影片內容與其他屬性的同時，修改建立日期。

### Maven 設定
Add the GroupDocs repository and the metadata dependency to your `pom.xml`:

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

> **專業提示：** 保持版本號為最新，可確保您受惠於最新的錯誤修復與效能提升。

### 直接下載（如果您不想使用 Maven）

或者，從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新的 JAR。

#### 取得授權

先使用免費試用版或申請臨時授權以評估 GroupDocs.Metadata。若要在生產環境使用，請透過 [GroupDocs 官方網站](https://purchase.groupdocs.com/temporary-license/) 購買授權。

## 基本初始化與設定

Once the library is on the classpath, you can create a `Metadata` instance that points to your PowerPoint file:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

此程式碼在 try‑with‑resources 區塊中開啟簡報，確保檔案句柄會自動釋放。

## 步驟指南：更新內建中繼資料

### 步驟 1：載入簡報文件

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

載入檔案會建立連線，使您能讀寫中繼資料。

### 步驟 2：存取簡報的根套件

`root` 物件提供對簡報核心套件及其內建屬性的存取。

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` 物件揭露所有內建的文件屬性。

### 步驟 3：更新內建文件屬性（包含建立日期）

`setCreatedTime` 為文件指派新的建立時間戳記。

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

此處示範如何 **設定 PPTX CreatedTime**，只需將新的 `Date` 物件指派給 `CreatedTime`。將 `new Date()` 替換為您需要的任何特定時間戳記。

### 步驟 4：儲存已更新的簡報

`save` 將修改後的中繼資料寫回檔案。

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` 呼叫會將修改後的中繼資料寫入新的 PowerPoint 檔案，原始檔案保持不變。

## 疑難排解技巧
- **檔案未找到：** 請再次確認輸入路徑與檔案權限。  
- **版本不匹配：** 確認 `groupdocs-metadata` 版本與您的 Java 執行環境相符。  
- **屬性未更新：** 請確認在呼叫 `save` 前已執行 `setCreatedTime`（或相關的 setter）。

## 實務應用
1. **企業品牌化：** 在發佈前自動將正確的公司名稱與類別注入所有投影片檔案。  
2. **文件管理系統：** 為 PPTX 檔案添加可搜尋的中繼資料，以加速檢索。  
3. **教育資源：** 在講義投影片中保持作者與課程資訊的即時更新。  
4. **協作追蹤：** 記錄貢獻者姓名，以維持問責制。  
5. **CMS 整合：** 即時將中繼資料變更同步至您的內容管理平台。

## 效能考量
- **批次處理：** 迭代檔案清單，盡可能重複使用單一 `Metadata` 實例。  
- **記憶體管理：** 始終使用 try‑with‑resources（如示範）即時釋放本機資源。  
- **有效資料結構：** 在套用前先將中繼資料更新存入映射表，以減少重複呼叫。

## 常見問題

**Q: GroupDocs Maven 依賴項的主要目的為何？**  
A: 它提供一種便利的方式，將最新的 GroupDocs.Metadata 函式庫納入基於 Maven 的 Java 專案中。

**Q: 如何在不影響其他屬性的情況下設定 PPTX 建立日期？**  
A: 在呼叫 `metadata.save()` 之前，使用 `root.getDocumentProperties().setCreatedTime(yourDesiredDate)`。

**Q: 在開發環境執行此程式碼是否需要授權？**  
A: 臨時試用授權足以用於開發與測試；正式授權則是生產環境的必要條件。

**Q: 我也能更新自訂中繼資料欄位嗎？**  
A: 可以——GroupDocs.Metadata 透過其 API 同時支援內建與自訂屬性。

**Q: 若發生錯誤，有沒有辦法還原變更？**  
A: 保留原始檔案的副本或在覆寫前讀取現有屬性值，必要時即可還原。

## 資源

- [文件說明](https://docs.groupdocs.com/metadata/java/)
- [API 參考](https://apireference.groupdocs.com/metadata/java/)

---

**最後更新：** 2026-05-27  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs  

---

## 相關教學

- [使用 GroupDocs.Metadata Java API 更新 PowerPoint 自訂中繼資料](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [使用 GroupDocs.Metadata Java 更新 Word 文件中繼資料的完整指南](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [在 Java 中使用 GroupDocs.Metadata 高效更新 PDF 中繼資料以支援文件管理](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)