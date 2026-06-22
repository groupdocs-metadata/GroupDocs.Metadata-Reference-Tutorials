---
date: '2026-06-22'
description: 了解如何使用 GroupDocs.Metadata for Java 讀取 SevenZip 中繼資料（Java），包括如何取得壓縮大小（Java）及其他壓縮檔屬性。
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: 如何在 Java 中使用 GroupDocs.Metadata 讀取 SevenZip 中繼資料
type: docs
url: /zh-hant/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Metadata 讀取 SevenZip 元資料（Java）

如果您需要從 Java 應用程式 **read sevenzip metadata java**，您來對地方了。在本教學中，我們將示範如何使用 **GroupDocs.Metadata** 取得檔案名稱、壓縮大小、未壓縮大小、修改日期等——正是您在備份驗證、同步或儲存空間最佳化任務中所需的資料。

## 介紹

在使用 Java 存取和讀取 SevenZip 壓縮檔的元資料屬性時遇到困難嗎？本教學將指導您使用 **GroupDocs.Metadata** 的流程。這個功能強大的函式庫可簡化直接從壓縮檔中提取檔名、大小與修改日期等關鍵資訊的工作。

## 快速解答
- **我應該使用哪個函式庫？** GroupDocs.Metadata for Java – 為超過 70 種壓縮與文件格式提供單一 API 解決方案。  
- **我可以列出 SevenZip 壓縮檔內的檔案嗎？** 可以——在初始化 `Metadata` 物件後呼叫 `getSevenZipPackage().getFiles()`。  
- **我需要授權嗎？** 免費試用可用於評估；正式環境需購買完整授權。  
- **支援哪個 Java 版本？** JDK 8 或更高（相容於 Java 17 LTS）。  
- **是否必須使用 Maven？** 非必須，但 Maven 能自動處理傳遞性相依性。  

## 在 Java 中「如何讀取 sevenzip」是什麼？

Reading SevenZip metadata means opening the `.7z` container, enumerating each entry, and pulling properties such as **compressed size**, **uncompressed size**, **file name**, and **modification date** without extracting the actual files. This process gives you insight into archive composition, enables verification of backup integrity, and allows you to make storage‑capacity decisions without the overhead of full extraction.

## read sevenzip metadata java

Using the primary keyword in a dedicated heading helps both readers and search engines understand the focus of this guide. Below we’ll dive into the exact steps you need to **read sevenzip metadata java** efficiently.

## 為何使用 GroupDocs.Metadata Java 進行元資料擷取？

GroupDocs.Metadata reads only the header information required for metadata extraction, so the operation finishes in milliseconds even for multi‑gigabyte archives. It supports **70+** archive and document formats, processes archives up to **2 GB** without loading the whole file into memory, and provides a consistent API across all supported types.

## 前置條件

Before diving into **GroupDocs.Metadata for Java**, ensure your development environment is properly set up. Here’s what you’ll need:

- **Java Development Kit (JDK)：** 版本 8 或以上。  
- **Maven：** 建議用於相依性管理，亦可手動加入 JAR。  
- **基本 Java 知識：** 熟悉類別、方法與例外處理。  

## 設定 GroupDocs.Metadata for Java

To use GroupDocs.Metadata, include it in your project via Maven or by downloading the library directly.

### 使用 Maven

Add the following configuration to your `pom.xml` file:

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

Alternatively, download the latest version from [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### 取得授權

1. **免費試用：** 開始免費試用以測試 GroupDocs.Metadata 的功能。  
2. **臨時授權：** 若需延長評估期間，可申請臨時授權。  
3. **購買：** 長期使用時，請考慮購買完整授權。  

With the setup complete, let’s move on to implementing the metadata‑reading functionality.

## 實作指南

### 從 SevenZip 壓縮檔存取元資料

In this section, we’ll extract and print metadata properties such as file names and sizes from a SevenZip archive.

#### 步驟 1：初始化 Metadata 物件

The `Metadata` class represents the entry point for loading and interacting with archive files.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 步驟 2：取得根套件

The `getRootPackageGeneric()` method returns a generic view of the archive's root package, allowing you to work with entries without needing format‑specific code.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Why Use `getRootPackageGeneric()`?** It provides a generalized view of the archive's contents, making it easier to iterate over its entries without worrying about specific file formats.

#### 步驟 3：遍歷壓縮檔條目

The `SevenZipPackage` class represents the SevenZip container, and each entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class provides direct access to properties like name, compressed size, and modification date.

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

- **Why Extract These Properties?** Knowing file sizes helps manage storage, while the modification date can be crucial for synchronization tasks. The `getCompressedSize()` call is the Java way to **get compressed size java** for each entry.

#### 步驟 4：清理資源

Calling `close()` on the `Metadata` instance releases native resources and avoids memory leaks in long‑running services.

```java
} finally {
    metadata.dispose();
}
```

- **Why Dispose?** Properly disposing of objects helps prevent memory leaks in long‑running applications.

## 如何有效擷取元資料？

Load the SevenZip archive with a single `Metadata` instance, call `getRootPackageGeneric()` once, and then stream through entries using a `for‑each` loop. This pattern avoids repeated I/O, reduces GC pressure, and completes in O(n) time where *n* is the number of entries.

## 實務應用

Understanding how to **read sevenzip metadata java** has numerous real‑world benefits:

1. **資料備份管理：** 快速驗證備份壓縮檔的完整性與正確性。  
2. **檔案同步工具：** 使用修改日期決定哪些檔案需要更新。  
3. **儲存空間最佳化：** 比較壓縮與未壓縮大小以規劃容量。  

Integration with other systems is possible, allowing for automated metadata extraction as part of larger data‑management workflows.

## 效能考量

When working with GroupDocs.Metadata and large archives, keep these tips in mind:

- **批次處理：** 以批次方式處理檔案以有效管理記憶體使用。  
- **有效的例外處理：** 使用 try‑with‑resources 以自動管理資源。  
- **非同步處理：** 為大量工作實作非同步技術。  

## 常見問題與解決方案

| 問題 | 解決方案 |
|-------|----------|
| **`NullPointerException` 在存取檔案時發生** | Verify the archive path is correct and the file is not corrupted. |
| **大型壓縮檔導致記憶體激增** | Enable batch processing or increase the JVM heap size (`-Xmx`). |
| **授權未被識別** | Ensure the license file is placed in the application’s working directory or set via `License.setLicense(path)`. |

## 常見問答

**Q:** 什麼是 GroupDocs.Metadata？  
**A:** 它是一個用於處理各種檔案格式元資料的 Java 函式庫，包括 SevenZip 壓縮檔。

**Q:** 是否可以在不使用 Maven 的情況下使用 GroupDocs.Metadata？  
**A:** 可以，您可以從官方網站下載 JAR 並加入專案的 classpath。

**Q:** 如何有效處理大型壓縮檔？  
**A:** 實作批次處理或使用非同步串流以限制記憶體消耗。

**Q:** 哪裡可以找到更詳細的說明？  
**A:** 請參閱 [official documentation](https://docs.groupdocs.com/metadata/java/) 取得完整的 API 參考。

**Q:** 若使用函式庫時遇到問題該怎麼辦？  
**A:** 可前往 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 向社群求助。

## 資源

- **文件說明：** 前往 [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/) 瞭解更多。  
- **官方文件：** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **API 參考：** 前往 [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/) 查看詳細 API 資訊。  
- **下載：** 從 [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/) 取得最新版本。  
- **GitHub 程式庫：** 在 [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) 上取得程式碼範例。  
- **免費支援論壇：** 前往 [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) 參與討論或提問。  

---

**最後更新：** 2026-06-22  
**測試環境：** GroupDocs.Metadata 24.12 for Java  
**作者：** GroupDocs

## 相關教學

- [如何使用 GroupDocs.Metadata for Java 讀取 TAR 檔並擷取元資料](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)  
- [Update ZIP Comment Java – 如何使用 GroupDocs.Metadata 更新 ZIP 壓縮檔註解](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)  
- [Extract Video Metadata Java: 如何使用 GroupDocs.Metadata 讀取 AVI 檔](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)