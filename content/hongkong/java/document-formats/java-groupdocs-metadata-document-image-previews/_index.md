---
date: '2026-02-06'
description: 學習如何使用 GroupDocs.Metadata 建立文件預覽（Java）並將頁面輸出為圖像。本指南涵蓋設定、配置與實作步驟。
keywords:
- document image preview
- GroupDocs Metadata Java
- creating document previews with Java
title: 如何在 Java 中使用 GroupDocs.Metadata 建立文件預覽
type: docs
url: /zh-hant/java/document-formats/java-groupdocs-metadata-document-image-previews/
weight: 1
---

# 精通 Java 中使用 GroupDocs.Metadata 的文件影像預覽

## 介紹

如果您需要 **create document preview java** 應用程式——無論是文件管理系統、數位圖書館，或是企業入口網站的快速預覽功能——GroupDocs.Metadata 都能讓您輕鬆上手。在本教學中，您將學會如何載入文件、設定預覽選項，並將頁面輸出為影像檔案，全部使用乾淨的 Java 程式碼。

我們將逐步說明完整工作流程，從 Maven 設定到為特定頁面產生 PNG 預覽。準備好讓您的文件以影像形式呈現了嗎？讓我們開始吧！

## 快速解答
- **What does “create document preview java” mean?** 產生文件頁面的視覺快照（例如 PNG），使用 Java 程式碼。  
- **Which library supports this out‑of‑the‑box?** GroupDocs.Metadata for Java。  
- **Can I choose the image format?** 是的——預覽選項允許您選擇 PNG、JPEG、BMP 等。  
- **Do I need a license?** 免費試用可用於評估；正式環境需購買授權。  
- **Is it possible to preview only selected pages?** 完全可以——使用 `setPageNumbers` 針對特定頁面。

## 什麼是 **create document preview java**？

在 Java 中建立文件預覽，意指以程式方式將檔案（DOCX、PDF、PPT 等）的單頁或多頁渲染為影像檔案。這可用於縮圖畫廊、快速視覺檢查，並能無縫整合至 Web 或桌面 UI 元件。

## 為何使用 GroupDocs.Metadata 產生預覽？

- **No external dependencies** – 純 Java，無原生二進位檔案。  
- **Supports over 100 file formats** – 從 Office 到 CAD。  
- **Fine‑grained control** – 可選擇影像格式、DPI 與頁面範圍。  
- **High performance** – 為大型文件與批次處理進行最佳化。

## 前置條件

- **Required Libraries:** GroupDocs.Metadata for Java（最新版本）。  
- **Build System:** Maven 專案（或手動加入 JAR）。  
- **Skill Set:** 熟悉 Java I/O、try‑with‑resources 以及例外處理。

## 設定 GroupDocs.Metadata for Java

### 安裝資訊

Add the GroupDocs repository and dependency to your `pom.xml`:

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

**直接下載**  
或者，從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新的 JAR，並加入至專案的 classpath。

### 取得授權

先使用免費試用或申請臨時授權。正式環境請於此處購買授權：[GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)。

### 基本初始化與設定

The following snippet shows the minimal code required to open a document with GroupDocs.Metadata:

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;

public class LoadDocument {
    public static void main(String[] args) {
        // Replace with your actual document path
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            System.out.println("Document loaded successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## 實作指南

以下我們將解決方案分為三個重點功能。每個功能皆包含簡潔說明與您所需的完整程式碼——不含額外片段，只保留原始區塊。

### 功能 1：初始化文件處理的 Metadata

**概述**  
載入文件是產生任何預覽之前的第一步。

#### 第一步 – 匯入類別  

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;
```

#### 第二步 – 載入文件  

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
try (Metadata metadata = new Metadata(documentPath)) {
    System.out.println("Document loaded successfully.");
} catch (IOException e) {
    e.printStackTrace();
}
```

**提示**  
- 執行程式前請確認檔案路徑與讀取權限。  
- 測試時使用絕對路徑，以免產生 classpath 混淆。

### 功能 2：為文件頁面建立預覽選項

**概述**  
設定預覽的外觀以及要渲染的頁面。

#### 第一步 – 匯入預覽類別  

```java
import com.groupdocs.metadata.options.PreviewFormats;
import com.groupdocs.metadata.options.PreviewOptions;
import java.io.OutputStream;
```

#### 第二步 – 設定預覽選項  

```java
OutputStream outputStream = null; // Replace with actual implementation if needed

PreviewOptions previewOptions = new PreviewOptions(outputStream::write);
previewOptions.setPreviewFormat(PreviewFormats.PNG); // Set the format of the preview image
previewOptions.setPageNumbers(new int[]{1}); // Specify page numbers to generate previews for
```

**為何重要**  
選擇 `PNG` 可確保無損品質，適合縮圖使用。調整 `setPageNumbers` 以預覽任意頁面範圍。

### 功能 3：建立頁面串流以輸出影像

**概述**  
每個預覽影像必須寫入檔案或其他輸出目的地。

#### 第一步 – 匯入 I/O 類別  

```java
import java.io.FileOutputStream;
import java.io.File;
import java.io.OutputStream;
import java.io.IOException;
```

#### 第二步 – 產生串流並寫入影像  

```java
int pageNumber = 1; // Example page number

try {
    File outputFile = new File(String.format("YOUR_OUTPUT_DIRECTORY/result_%d.png", pageNumber));
    OutputStream stream = new FileOutputStream(outputFile);
    System.out.println("Page stream created for output.");
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

**專業提示：** 確認 `YOUR_OUTPUT_DIRECTORY` 事先已存在，或使用 `outputFile.getParentFile().mkdirs();` 程式碼自行建立。

## 如何使用 GroupDocs.Metadata **output page as image**

透過結合功能 2 的預覽選項與功能 3 的串流邏輯，即可將任意頁面渲染為影像檔案：

1. 初始化 `Metadata`（功能 1）。  
2. 建立 `PreviewOptions` 實例，指定 `PNG` 與所需的頁碼。  
3. 傳入 lambda，將預覽位元組寫入功能 3 中建立的 `OutputStream`。

此流程可讓您高效 **output page as image**，即使是大型文件亦然。

## 實務應用

- **Document Management Systems:** 在檔案瀏覽器中顯示縮圖。  
- **Digital Libraries:** 為掃描書籍提供快速視覺提示。  
- **Legal/Finance:** 快速檢視合約頁面。  
- **CMS Platforms:** 為上傳的報告自動產生預覽影像。  
- **E‑Learning:** 讓學生在下載前先預覽講義投影片。

## 效能考量

- **Limit page batches:** 同時產生大量頁面可能導致記憶體使用激增。  
- **Use try‑with‑resources:** 確保串流在使用後關閉，防止記憶體泄漏。  
- **Monitor JVM heap:** 大型 PDF 可能需要提升堆積大小（`-Xmx`）。

## 常見問題與解決方案

| 問題 | 原因 | 解決方案 |
|-------|-------|-----|
| `outputStream` 上的 `NullPointerException` | `outputStream` 未初始化 | 提供實際的 `OutputStream`（例如 `new FileOutputStream(...)`）。 |
| 未產生預覽 | 頁碼錯誤 | 確認頁面是否存在；使用 `metadata.getPageCount()` 進行驗證。 |
| 寫入檔案時的權限錯誤 | 輸出目錄為唯讀 | 授予寫入權限或選擇可寫入的資料夾。 |

## 常見問答

**Q: 我可以為受密碼保護的文件產生預覽嗎？**  
A: 可以。使用接受密碼的建構子開啟文件，之後即可使用預覽選項。

**Q: 支援哪些影像格式？**  
A: 透過 `PreviewFormats` 可使用 PNG、JPEG、BMP 與 GIF。

**Q: 如何一次預覽多個頁面？**  
A: 將頁碼陣列傳入 `previewOptions.setPageNumbers(new int[]{1,2,3});`。

**Q: 有辦法控制影像解析度嗎？**  
A: 使用 `previewOptions.setDpi(int dpi)` 調整 DPI（預設 96 DPI）。

**Q: 此函式庫能在 Android 上使用嗎？**  
A: GroupDocs.Metadata 為純 Java，可於 Android 使用相應的 JAR，但 UI 渲染需由 Android 框架處理。

## 結論

您現在擁有一套完整、可投入生產的 **create document preview java** 解決方案指南，使用 GroupDocs.Metadata 可 **output page as image** 檔案。透過遵循三個功能步驟——初始化 metadata、設定預覽選項、寫入影像串流，即可將高品質的預覽整合至任何 Java 應用程式。

---

**最後更新：** 2026-02-06  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs