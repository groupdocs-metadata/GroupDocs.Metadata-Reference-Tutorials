---
date: '2026-06-22'
description: 了解如何使用 GroupDocs.Metadata for Java 從 OpenType 字體中提取 OpenType 字體簽名及數位簽名詳細資訊。本指南有助於保護您的文件。
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: 如何在 Java 中使用 GroupDocs.Metadata 提取 OpenType 字體簽名
type: docs
url: /zh-hant/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Metadata 提取 OpenType 字體簽名

在現代應用程式中，**提取 OpenType 字體簽名** 資料對於確認字體真偽與保護數位資產至關重要。本教學將一步步示範如何使用 **GroupDocs.Metadata for Java** 從 OpenType 字體中取得簽名旗標與完整的加密細節。無論您是構建安全導向的內容管線，或只是需要審核字體庫，以下技術都能讓您的工作流程可靠且快速。

## 快速回答
- **需要哪個函式庫？** GroupDocs.Metadata for Java (v24.12)  
- **需要哪個 Java 版本？** JDK 8 或更新版本  
- **需要授權嗎？** 免費試用可用於評估；正式環境需購買完整授權  
- **可以處理多個字體嗎？** 是 – 支援批次或並行處理  
- **程式碼是執行緒安全的嗎？** 每個執行緒建立新的 `Metadata` 實例；單一物件本身並非執行緒安全  

## 什麼是 OpenType 字體簽名？
**OpenType 字體簽名** 是嵌入於字體內的加密區塊，用以證明檔案自簽署以來未被更改。它包含簽署時間、憑證鏈、雜湊演算法識別碼，以及可選的撤銷資訊。簽名還包括簽名演算法識別碼、簽署者的憑證鏈與可選的撤銷清單，從而實現對字體完整性與來源的全面驗證。

## 為什麼要在 Java 中使用 GroupDocs.Metadata？
GroupDocs.Metadata 支援 **50+ 輸入與輸出格式**（包括 DOCX、PDF、PPTX、HTML 以及各種影像類型），且可在不將整個檔案載入記憶體的情況下讀取 OpenType 簽名，讓您能有效處理數百頁的字體集合。

## 先決條件
- **Java Development Kit (JDK)：** 版本 8 或更新。  
- **IDE：** 任何相容 Java 的 IDE（IntelliJ IDEA、Eclipse、VS Code 等）。  
- **Maven：** 用於相依性管理。  

### 所需函式庫與相依性
將 GroupDocs.Metadata 的 Maven 座標加入 `pom.xml`，即可取得範例所需的完整套件。

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
亦可從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新版本。

### 取得授權
- **免費試用：** 開始使用免費試用以探索功能。  
- **臨時授權：** 透過 [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license) 取得臨時授權。  
- **購買：** 正式環境請購買完整授權。

## 如何使用 GroupDocs.Metadata 提取 OpenType 字體簽名
`Metadata` 類別是 GroupDocs.Metadata 的核心 API，可在不載入完整檔案的情況下存取文件中繼資料。  
要讀取字體的簽名，只需以 .otf 檔案路徑建立 `Metadata` 物件，然後存取其 `DigitalSignaturePackage`。此方式僅載入必要的中繼資料結構，避免完整字體解析，降低記憶體使用。`Metadata` 實例應放在 try‑with‑resources 區塊中，以確保正確釋放資源。

在 try‑with‑resources 區塊內使用 `new Metadata("font.otf")` 載入字體檔案。`Metadata` 類別是 GroupDocs.Metadata 讀取任何支援文件類型（包括 OpenType 字體）的入口點，物件會自動關閉，防止資源洩漏。

### 如何提取數位簽名旗標
`DigitalSignaturePackage` 物件彙總了字體所有與簽名相關的資訊，包括旗標與個別簽名。  
**直接答案：** 開啟字體後呼叫 `metadata.getDigitalSignaturePackage().getFlags()`；回傳的旗標集合會告訴您簽名是否有效、是否被撤銷或是否有特殊條件。此單一呼叫即可在深入細節前快速檢查健康狀態。旗標以列舉形式呈現，可檢查簽署狀態、時間戳記存在與任何政策限制。

1. 初始化指向字體檔案的 `Metadata` 實例。  
2. 取得 `DigitalSignaturePackage`。  
3. 列印或記錄旗標值。

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**說明**  
- `documentPath` – OpenType 字體的絕對或相對路徑。  
- try‑with‑resources 區塊確保 `Metadata` 物件自動關閉，避免記憶體洩漏。

### 如何提取詳細的數位簽名資訊
`CmsSignature` 代表嵌入字體中的單一 CMS/PKCS#7 簽名，提供其加密屬性存取。  
**直接答案：** 迭代 `metadata.getDigitalSignaturePackage().getSignatures()`；每個 `CmsSignature` 物件皆可取得簽署時間、摘要演算法、封裝內容與憑證細節，讓您建立完整的稽核報告。對每個簽名，您可取得簽署者的憑證鏈、驗證雜湊演算法，並抽取時間戳記以確認簽名的應用時間。

1. 重複使用上述相同的 `Metadata` 初始化。  
2. 迭代套件中的每個 `CmsSignature`。  
3. 抽取屬性，例如 `getSignTime()`、`getDigestAlgorithms()`、`getCertificates()` 與 `getSignerInfo()`。

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**關鍵部分說明**  
- **簽署時間：** 簽名套用時的時間戳記。  
- **摘要演算法與 OID：** 使用的雜湊演算法（例如 SHA‑256）。  
- **封裝內容：** 簽名內部封裝的任何額外資料。  
- **憑證：** 有效日期與原始資料大小有助於驗證簽署者身分。  
- **簽署者：** 提供每位簽署者的演算法選擇與簽署時間戳記。

#### 故障排除提示
- 如果字體缺少數位簽名，`getDigitalSignaturePackage()` 會回傳 `null`。在存取旗標或簽名前務必檢查是否為 `null`。  
- 確保使用與 Maven 相依性中定義相同的 **GroupDocs.Metadata** 版本，以避免相容性問題。  

## 實務應用
提取 OpenType 字體簽名在多種真實情境中相當有價值：

1. **文件驗證：** 在內容管理系統中自動檢查已簽署的字體檔案。  
2. **數位資產管理：** 在品牌專案部署前驗證字體真偽。  
3. **安全稽核：** 審查簽名細節以確保符合內部安全政策。  

## 效能考量
- **資源管理：** 使用 try‑with‑resources 及時關閉 `Metadata` 物件。  
- **批次處理：** 將字體分組處理以減少 I/O 開銷；GroupDocs.Metadata 可在不載入整個字體至記憶體的情況下處理成千上萬的檔案。  
- **併發：** 為大規模工作負載在平行執行緒中執行獨立的 `Metadata` 實例；庫本身每個實例並非執行緒安全，請為每個執行緒分離實例。  

## 常見問題

**Q: 我可以從沒有數位簽名的字體中提取簽名嗎？**  
A: `DigitalSignaturePackage` 會是 `null`；在存取旗標或細節前務必檢查此情況。

**Q: 需要哪個版本的 GroupDocs.Metadata？**  
A: 範例針對 **24.12** 版，但較新版本仍向下相容於 OpenType 字體。

**Q: 讀取簽名需要特別授權嗎？**  
A: 評估可使用試用授權；正式使用需購買完整授權。

**Q: 如何處理儲存在雲端儲存桶中的字體？**  
A: 先將字體下載至暫存本機檔案，再將其路徑傳遞給 `Metadata`。該庫可處理任何可透過本機路徑存取的檔案。

**Q: 能否驗證簽名的加密有效性？**  
A: GroupDocs.Metadata 提供原始簽名資料；您可以將憑證鏈與雜湊值交給其他加密函式庫以執行完整驗證。

## 結論
透過本指南，您已掌握 **如何使用 GroupDocs.Metadata for Java 提取 OpenType 字體簽名** 以及詳細的數位簽名資料。將這些步驟整合至您的應用程式，可加強文件安全、簡化資產驗證，並支援合規性計畫。

## 後續步驟
- 嘗試批次處理以有效處理大型字體庫。  
- 將提取的資料與安全稽核工具結合，以自動化合規報告。  
- 探索 GroupDocs.Metadata 的其他中繼資料功能，例如在適當時編輯或移除簽名。

---

**最後更新：** 2026-06-22  
**測試環境：** GroupDocs.Metadata 24.12  
**作者：** GroupDocs

## 相關教學

- [使用 GroupDocs 在 Java 中存取 Word 文件中繼資料：完整指南](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [如何使用 GroupDocs.Metadata 在 Java 中提取 PDF 的自訂中繼資料：完整指南](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)