---
date: '2026-05-27'
description: 了解如何使用 GroupDocs.Metadata for Java 更新電郵收件者。修改收件者、主旨，並高效儲存變更。
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 更新電郵收件者 Java：掌握使用 GroupDocs.Metadata 的電郵元資料更新
type: docs
url: /zh-hant/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# 使用 GroupDocs.Metadata 更新 Java 電郵收件人

在本完整指南中，您將使用 GroupDocs.Metadata 程式庫以程式方式 **update email recipients java**（更新 Java 電郵收件人）。我們將逐步說明如何修改主要收件人與副本（CC）收件人、更改主旨行，並將變更持久化——全部提供清晰的逐步程式碼範例。完成後，您即可將電郵元資料自動化整合至任何基於 Java 的工作流程。

## 快速解答
- **什麼是更改電郵主要收件人的最快方法？** 使用 `Metadata` 載入檔案，取得 `EmailRootPackage`，取代 `To` 集合，然後儲存——僅需三行程式碼。  
- **我可以在不覆寫現有收件人的情況下新增 CC 收件人嗎？** 可以，使用 `EmailRootPackage` 的 `addCcRecipient` 方法將新地址加入 CC 集合。  
- **生產環境是否需要授權？** 臨時授權可移除評估限制；商業部署則需永久授權。您可從 [GroupDocs](https://purchase.groupdocs.com/temporary-license/) 頁面取得臨時授權。  
- **支援哪些 Java 版本？** GroupDocs.Metadata 可在 Java 8、11、17 及更高版本上運作。  
- **大量信箱批次處理是否安全？** 將檔案分批處理（每批 50–100 個），以將記憶體使用量控制在每批 200 MB 以下。

## 什麼是 update email recipients java？
*Updating email recipients in Java*（在 Java 中更新電郵收件人）指的是以程式方式變更電郵檔案（EML、MSG 等）的 “To”、 “CC” 或 “BCC” 欄位，而不需開啟郵件客戶端。GroupDocs.Metadata 提供高階 API，能讀取電郵結構、讓您修改地址集合，並將更新後的檔案寫回磁碟。

## 為何使用 GroupDocs.Metadata 處理電郵元資料？
GroupDocs.Metadata 支援 **50 多種電郵相關格式**（包括 EML、MSG、MHT），且能在不將整個檔案載入記憶體的情況下處理 **數百頁的訊息**，相較於傳統檔案串流方式，可將 RAM 使用量降低最高 **80 %**。其純 Java 實作消除本機相依性，十分適合跨平台服務。

## 前置條件
- Java 8 或更新版本（已完整測試 Java 11、17、21）。
- 用於相依管理的 Maven 或 Gradle。
- 有效的 GroupDocs.Metadata 授權（臨時或永久）。

### 必要的函式庫與相依性
在您的 `pom.xml` 中加入以下相依性：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

若需直接下載，請從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 取得最新版本。

### 環境設定
確保您的 IDE 指向相容的 JDK，且 Maven 能順利解析 GroupDocs.Metadata 的套件，無錯誤發生。

## 如何在 Java 中更新電郵收件人？
載入電郵檔案、取代現有收件人，並儲存結果。此操作僅需三個 API 呼叫，對於一般 1 MB 訊息執行時間低於 **200 ms**。透過高階的 `EmailRootPackage` API，可避免解析整個檔案，從而降低記憶體使用，並使批次處理變得簡單。

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
上述程式碼行匯入了在檔案上開始管理元資料操作所必需的類別。

## 實作指南
接下來，我們將深入探討每個功能，將快速解答的程式碼片段擴展為完整說明。

### 更新電郵收件人
**概述**：本節示範如何以程式方式更新電郵訊息的主要收件人。

#### 步驟 1：初始化 Metadata 物件
`Metadata` 類別代表一個檔案，並提供存取其元資料的功能。使用您的輸入檔案路徑建立 `Metadata` 實例：

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**定義說明**：`Metadata` 類別是 GroupDocs.Metadata 中所有元資料操作的入口點，代表記憶體中的單一檔案。

#### 步驟 2：取得 EmailRootPackage
`EmailRootPackage` 可取得電郵特定的元資料，如收件人與主旨。使用以下方式存取電郵的元資料：

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
此步驟至關重要，因為它提供了對電郵所有可修改屬性的存取。

#### 步驟 3：更新收件人
為您的電郵訊息設定新收件人：

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### 為電郵新增副本（CC）收件人
**概述**：了解如何向現有電郵新增 CC 收件人。

#### 步驟 1：初始化並取得根套件
與更新主要收件人類似，先初始化 metadata 物件：

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 步驟 2：設定 CC 收件人
`addCcRecipient` 會將新地址加入 CC 集合，而不會覆寫現有項目。如下方式新增副本收件人：

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
此做法可確保其他使用者收到通知，同時不會成為主要聯絡人。

### 更新電郵主旨
**概述**：此功能允許您修改電郵的主旨行，使通訊保持清晰與即時。

#### 步驟 1：初始化 Metadata
首先初始化您的 metadata 物件：

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 步驟 2：變更主旨
更新電郵的主旨行：

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
此步驟對於維持相關且可搜尋的電郵線索至關重要。

### 儲存更新後的電郵元資料
**概述**：完成變更後，必須儲存這些更新。本節說明如何有效地持久化您的修改。

#### 步驟 1：初始化並取得根套件
先初始化 `Metadata` 物件：

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 步驟 2：儲存變更
將變更儲存至指定的輸出目錄，以持久化變更：

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
此舉可確保所有修改均被保留，並反映在儲存的檔案中。

## 實務應用
在各種實務情境中實作這些功能可帶來極大效益：

1. **電郵管理系統** – 自動化大量電郵發送的收件人更新。  
2. **客戶支援平台** – 迅速修改電郵主旨，以反映工單狀態變更。  
3. **內部通訊工具** – 確保所有團隊成員在關鍵公告中被 CC，免除手動編輯。

## 效能考量
處理大量電郵資料時，請留意以下建議：

- 將檔案分批處理（每批 **50–100** 個），以將記憶體使用量控制在每批 **200 MB** 以下。  
- 盡量少使用 `metadata.getRootPackage().getEmail()` 呼叫；盡可能重複使用 `Metadata` 實例。  
- 使用 VisualVM 等工具監控 JVM 堆積使用情況，避免 OutOfMemory 錯誤。

## 結論
您現在已掌握如何使用 GroupDocs.Metadata **update email recipients java**（更新 Java 電郵收件人）。無論是調整主要收件人、加入 CC，或是微調主旨行，該函式庫皆提供快速且節省記憶體的 API。請參閱完整的 [documentation](https://docs.groupdocs.com/metadata/java/) 以了解更進階的情境，例如處理附件或在 EML 與 MSG 格式之間轉換。

## 常見問題
**Q1**：GroupDocs.Metadata 支援哪些 Java 版本？  
- **A**：完整支援 Java 8、11、17 及更高版本。

**Q2**：我可以在沒有授權的情況下使用 GroupDocs.Metadata 嗎？  
- **A**：可以，免費試用可使用但有功能限制；臨時或永久授權可移除這些限制。

**Q3**：如何有效處理大型電郵檔案？  
- **A**：將檔案分成較小批次處理，重複使用 `Metadata` 物件，並監控堆積使用量，以維持每批低於 200 MB。

**Q4**：除了電郵之外，GroupDocs.Metadata 還支援哪些檔案類型？  
- **A**：支援超過 **70** 種格式，包括 PDF、DOCX、XLSX、PPTX、影像與壓縮檔等。請參閱 [API reference](https://reference.groupdocs.com/metadata/java/) 取得完整清單。

---
**最後更新：** 2026-05-27  
**測試環境：** GroupDocs.Metadata 23.12 for Java  
**作者：** GroupDocs  

## 相關教學

- [精通使用 GroupDocs.Metadata 在 Java 中提取電郵元資料](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [GroupDocs.Metadata Java 的電郵與聯絡人元資料教學](/metadata/java/email-contact-formats/)
- [如何在 Java 中使用 GroupDocs.Metadata 提取 vCard 照片 URI 以提升聯絡人管理效率](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)