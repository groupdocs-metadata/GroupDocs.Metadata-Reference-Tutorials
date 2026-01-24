---
date: '2026-01-24'
description: 學習如何使用 GroupDocs.Metadata for Java 從 OpenType 字型中提取簽名與數位簽章資訊。此一步一步的指南可提升文件安全性。
keywords:
- extract digital signatures OpenType fonts Java
- digital signature flags OpenType fonts
- GroupDocs Metadata Java
title: 如何在 Java 中使用 GroupDocs.Metadata 從 OpenType 字體提取簽名
type: docs
url: /zh-hant/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Metadata 從 OpenType 字型提取簽章

## 介紹
在當今的數位時代，**如何提取簽章**資訊是需要驗證真偽與維持完整性的開發者常見需求。本教學將帶您使用 **GroupDocs.Metadata for Java** 從 OpenType 字型中提取數位簽章旗標與詳細簽章資料。稽核字型資產，掌握此流程都能讓您的工作流程物一次取數位簽章資料之前，請確保您的環境符合以下需求：

### 必 環境設定需求
- **Java Development Kit (JDK)：** 安裝 JDK 8 或更新版本。  
- **IDE：** 任意支援 Java 的開發環境 (IntelliJ IDEA、Eclipse、VS Code 等)。

### 知識前置條件
具備基本的 Java簽章的概念會比較順利，但本指南亦提供新手友善的說明。

## 設定 GroupDocs.Metadata for Java
### Maven 安裝
將以下設定加入您的 `pom.xml` 檔案，即可取得範例所需的 **groupdocs metadata java** 套件。

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
或是直接從 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) 下載最新版本。

### 授權取得
- **免費試用：** 先取得免費試用版以探索功能。  
- **臨時授權：** 如有需要，可前往 [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license) 取得臨時授權。  
- **購買授權：** 若需完整功能，建議購買正式授權。

安裝函式庫並取得授權後，即可開始提取簽章。

## OpenType 字型中的數位簽章是什麼？
嵌入於 OpenType 字型的數位簽章可保證字型檔案自簽署以來未被更改。簽章內含簽署時間、憑證與雜湊演算法等加密資訊，您可使用 GroupDocs.Metadata 以程式方式讀取。

## 如何提取數位簽章旗標
### 概觀
提取數位簽章旗標可快速辨識簽章的狀態與屬性（例如是否有效、是否撤銷或是否具特殊條件）。

### 實作步驟
1. **初始化 Metadata：** 建立指向字型檔案的 `Metadata` 實例。  
2. **讀取旗標：** 取得 `DigitalSignaturePackage` 並列印其旗標。

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
- `documentPath` – OpenType 字型的絕對或相對路徑。  
- `try‑with‑resources` 區塊會自動關閉 `Metadata` 物件，避免資源泄漏。

## 如何提取詳細的數位簽章資訊
### 概觀
除了旗標外，您通常還需要檢視每筆簽章的中繼資料——簽署時間、演算法、憑證與封裝內容等。

### 實作步驟
1. **初始化 Metadata**（同上）。  
2. **遍歷簽章：** 針對每個 `CmsSignature`，列印相關屬性。

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

**關鍵段落說明**
- **簽署時間：** 簽章被套用的時間。  
- **摘要演算法與 OID：** 使用的雜湊演算法（例如 SHA‑256）。  
- **封裝內容：** 簽章內部封裝的任何額外資料。  
- **憑證：** 有效日期與原始資料大小有助於驗證簽署者身份。  
- **簽署者：** 提供每位簽署者的演算法選擇與簽署時間戳記。

### 疑難排解技巧
- 確保字型實際包含數位簽章；否則 `getDigitalSignaturePackage()` 會回傳 `null`。  
- 確認使用的 **GroupDocs.Metadata** 版本與 Maven 依賴中顯示的相同，以避免相容性問題。  

## 實務應用
從 OpenType 字型提取數位簽章資料在多種情境下都很有用：
1. **文件驗證：** 在內容管理系統中自動檢查已簽署的字型檔案。  
2. **數位資產管理：** 在品牌專案部署前驗證字型真偽。  
3. **安全稽核：** 檢閱簽章細節以確保符合內部安全政策。

## 效能考量
- **資源管理：** 始終使用 `try‑with‑resources` 及時關閉 `Metadata` 物件。  
- **批次處理：** 處理大量字型時，分批執行以降低 I/O 開銷。  
- **平行執行：** 大規模工作負載時，可在平行執行緒中各自建立 `Metadata` 實例；單一實例本身並非執行緒安全。

## 常見問答

**Q: 可以從沒有數位簽章的字型提取簽章嗎？**  
A: `DigitalSignaturePackage` 會是 `null`；在存取旗標或細節前請先檢查此情況。

**Q: 需要哪個版本的 GroupDocs.Metadata？**  
A: 範例使用 **24.12** 版，較新版本亦相容於 OpenType 字型。

**Q: 讀取簽章需要特別授權嗎？**  
A: 試用授權可用於評估；正式環境需購買完整授權。

**Q: 若字型存放在雲端儲存桶，該如何處理？**  
A: 先將字型下載至暫存本機檔案，然後將其路徑傳給 `Metadata`。函式庫支援任何可透過本機路徑存取的檔案。

**Q: 能否驗證簽章的加密有效性？**  
A: GroupDocs.Metadata 只提供原始資料；您可將憑證鏈與雜湊值交給其他加密函式庫，以完成完整的驗證。

## 結論
透過本指南，您已瞭解 **如何提取簽章** 資訊與 OpenType 字型的詳細數位簽章資料，並能使用 **GroupDocs.Metadata for Java** 將此技術整合至應用程式中。此技巧可提升文件安全性、簡化資產驗證 將提取的資料與安全稽核工具結合，- 探索 GroupDocs.Metadata 的其他元資料功能，例如在適當情況下編輯或移除簽章。

---

**最後更新：** 2026-01-24  
**測試版本：** GroupDocs.Metadata 24.12  
**作者：** GroupDocs