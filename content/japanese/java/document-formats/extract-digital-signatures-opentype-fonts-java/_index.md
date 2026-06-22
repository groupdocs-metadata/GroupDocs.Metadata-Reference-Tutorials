---
date: '2026-06-22'
description: Java用GroupDocs.Metadataを使用してOpenTypeフォントからフォント署名とデジタル署名の詳細を抽出する方法を学びます。このガイドはドキュメントのセキュリティ確保に役立ちます。
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
title: JavaでGroupDocs.Metadataを使用してOpenTypeフォント署名を抽出する方法
type: docs
url: /ja/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# JavaでGroupDocs.Metadataを使用してOpenTypeフォント署名を抽出する方法

現代のアプリケーションでは、**OpenTypeフォント署名の抽出**データは、フォントの真正性を確認し、デジタル資産を保護するために不可欠です。このチュートリアルでは、**GroupDocs.Metadata for Java** を使用して、OpenTypeフォントから署名フラグと完全な暗号詳細の両方を取得する手順をステップバイステップで示します。セキュリティ重視のコンテンツパイプラインを構築する場合でも、フォントライブラリを監査するだけの場合でも、以下の手法によりワークフローが信頼性と高速性を兼ね備えるようになります。

## クイック回答
- **必要なライブラリは何ですか？** GroupDocs.Metadata for Java (v24.12)  
- **必要なJavaバージョンは？** JDK 8 以降  
- **ライセンスは必要ですか？** 評価用に無料トライアルが利用可能です。製品版ではフルライセンスが必要です。  
- **複数のフォントを処理できますか？** はい – バッチ処理または同時処理がサポートされています。  
- **コードはスレッドセーフですか？** スレッドごとに新しい `Metadata` インスタンスを作成してください。インスタンス自体はスレッドセーフではありません。  

## OpenTypeフォント署名とは？
**OpenTypeフォント署名** は、フォント内に埋め込まれた暗号ブロックで、署名後にファイルが改ざんされていないことを証明します。署名時間、証明書チェーン、ハッシュアルゴリズム識別子、オプションの失効情報が含まれます。また、署名アルゴリズム識別子、署名者の証明書チェーン、オプションの失効リストも含まれ、フォントの完全性と出所を包括的に検証できるようになっています。

## なぜJavaでGroupDocs.Metadataを使用するのか？
GroupDocs.Metadata は **50 以上の入力および出力フォーマット**（DOCX、PDF、PPTX、HTML、各種画像形式など）をサポートし、フォント全体をメモリに読み込むことなく OpenType 署名を読み取れるため、数百ページ規模のフォントコレクションを効率的に処理できます。

## 前提条件
- **Java Development Kit (JDK)：** バージョン 8 以上。  
- **IDE：** 任意の Java 対応 IDE（IntelliJ IDEA、Eclipse、VS Code など）。  
- **Maven：** 依存関係管理に使用。  

### 必要なライブラリと依存関係
`pom.xml` に GroupDocs.Metadata の Maven 座標を追加してください。これにより、サンプルで必要な正確なパッケージが取得されます。

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

### 直接ダウンロード
または、最新バージョンを [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) からダウンロードしてください。

### ライセンス取得
- **無料トライアル：** 機能を試すために無料トライアルから開始してください。  
- **一時ライセンス：** [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license) から一時ライセンスを取得してください。  
- **購入：** 本番環境で使用する場合はフルライセンスを購入してください。

## GroupDocs.Metadataを使用してOpenTypeフォント署名を抽出する方法
`Metadata` クラスは、ファイル全体をロードせずにドキュメントメタデータにアクセスするための GroupDocs.Metadata のコア API です。フォントの署名を読み取るには、`.otf` ファイルへのパスで `Metadata` オブジェクトをインスタンス化し、`DigitalSignaturePackage` にアクセスします。このアプローチは必要なメタデータ構造のみをロードし、フォント全体のパースを回避してメモリ使用量を抑えます。`Metadata` インスタンスは try‑with‑resources ブロック内で使用し、適切に破棄されるようにしてください。

`new Metadata("font.otf")` でフォントファイルをロードし、try‑with‑resources ブロック内で使用します。`Metadata` クラスは、OpenType フォントを含むすべてのサポート対象ドキュメントタイプの読み取りエントリーポイントです。オブジェクトは自動的に閉じられ、リソースリークを防止します。

### デジタル署名フラグの抽出方法
`DigitalSignaturePackage` オブジェクトは、フォントに関するすべての署名情報（フラグと個別署名）を集約します。  
**直接的な回答:** フォントを開いた後に `metadata.getDigitalSignaturePackage().getFlags()` を呼び出します。返されるフラグセットにより、署名が有効か、失効しているか、特別な条件があるかが分かります。この単一呼び出しで、詳細に入る前の迅速なヘルスチェックが可能です。フラグは列挙型として表現され、署名ステータス、タイムスタンプの有無、署名時に適用されたポリシー制約などを判定できます。

1. フォントファイルを指す `Metadata` インスタンスを初期化します。  
2. `DigitalSignaturePackage` を取得します。  
3. フラグ値を出力またはログに記録します。

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**説明**  
- `documentPath` – OpenType フォントへの絶対パスまたは相対パス。  
- try‑with‑resources ブロックは `Metadata` オブジェクトを自動的に閉じ、メモリリークを防止します。

### 詳細なデジタル署名情報の抽出方法
`CmsSignature` はフォントに埋め込まれた個々の CMS/PKCS#7 署名を表し、暗号プロパティへのアクセスを提供します。  
**直接的な回答:** `metadata.getDigitalSignaturePackage().getSignatures()` を反復処理します。各 `CmsSignature` オブジェクトは署名時間、ダイジェストアルゴリズム、カプセル化コンテンツ、証明書情報を公開し、完全な監査レポートを作成できます。各署名について、署名者の証明書チェーンを取得し、ハッシュアルゴリズムを検証し、タイムスタンプトークンを抽出して署名が適用された時点を確認できます。

1. 上記と同じ `Metadata` 初期化を再利用します。  
2. パッケージ内の各 `CmsSignature` をループ処理します。  
3. `getSignTime()`、`getDigestAlgorithms()`、`getCertificates()`、`getSignerInfo()` などのプロパティを抽出します。

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

**主要セクションの説明**  
- **Sign Time（署名時間）：** 署名が適用されたタイムスタンプ。  
- **Digest Algorithms & OIDs（ダイジェストアルゴリズムと OID）：** 使用されたハッシュアルゴリズム（例：SHA‑256）。  
- **Encapsulated Content（カプセル化コンテンツ）：** 署名内にラップされた追加データ。  
- **Certificates（証明書）：** 有効期限と生データサイズが署名者の身元確認に役立ちます。  
- **Signers（署名者）：** 各署名者のアルゴリズム選択と署名タイムスタンプを提供します。

#### トラブルシューティングのヒント
- フォントにデジタル署名がない場合、`getDigitalSignaturePackage()` は `null` を返します。フラグや署名にアクセスする前に必ず `null` チェックを行ってください。  
- Maven 依存関係で指定した **GroupDocs.Metadata** のバージョンと同じものを使用し、互換性の問題を回避してください。  

## 実用的な活用例
OpenType フォント署名の抽出は、さまざまな実務シナリオで価値があります。

1. **ドキュメント検証：** コンテンツ管理システムで署名済みフォントファイルのチェックを自動化。  
2. **デジタル資産管理：** ブランドプロジェクトに展開する前にフォントの真正性を検証。  
3. **セキュリティ監査：** 署名詳細をレビューし、内部セキュリティポリシーへの準拠を確認。  

## パフォーマンス上の考慮点
- **リソース管理：** try‑with‑resources を使用して `Metadata` オブジェクトを速やかに閉じる。  
- **バッチ処理：** フォントをグループで処理し I/O オーバーヘッドを最小化。GroupDocs.Metadata は各フォント全体をメモリにロードせずに数千ファイルを処理可能。  
- **並列処理：** 大規模ワークロード向けにスレッドごとに個別の `Metadata` インスタンスを実行。インスタンス自体はスレッドセーフではないため、スレッドごとに分離してください。  

## よくある質問

**Q: デジタル署名がないフォントから署名を抽出できますか？**  
A: `DigitalSignaturePackage` は `null` になるため、フラグや詳細にアクセスする前に必ずこの条件をチェックしてください。

**Q: 必要な GroupDocs.Metadata のバージョンは？**  
A: サンプルはバージョン **24.12** を対象としていますが、最新リリースでも OpenType フォントに対して下位互換性があります。

**Q: 署名を読むために特別なライセンスが必要ですか？**  
A: 評価用にはトライアルライセンスで可能ですが、本番環境ではフルライセンスが必要です。

**Q: クラウドバケットに保存されているフォントはどう扱いますか？**  
A: フォントを一時的なローカルファイルにダウンロードし、そのパスを `Metadata` に渡してください。ローカルパスにアクセスできればライブラリは問題なく動作します。

**Q: 署名の暗号的有効性を検証できますか？**  
A: GroupDocs.Metadata は生の署名データを提供しますので、証明書チェーンやハッシュ値を別の暗号ライブラリに渡して完全な検証を行うことができます。

## 結論
本ガイドに従うことで、**Java 用 GroupDocs.Metadata** を使用して **OpenType フォント署名** 情報と詳細なデジタル署名データを抽出する方法が分かります。これらの手順をアプリケーションに統合すれば、ドキュメントのセキュリティが強化され、資産検証が効率化され、コンプライアンスイニシアチブを支援できます。

**次のステップ**  
- バッチ処理を試して、大規模なフォントライブラリを効率的に処理。  
- 抽出したデータをセキュリティ監査ツールと組み合わせて、コンプライアンスレポートを自動化。  
- 必要に応じて、署名の編集や削除など、GroupDocs.Metadata の他のメタデータ機能も探索してください。

---

**Last Updated:** 2026-06-22  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs

## 関連チュートリアル

- [JavaでGroupDocsを使用したWordドキュメントメタデータへのアクセス：包括的ガイド](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [JavaでGroupDocs.Metadataを使用してPDFからカスタムメタデータを抽出する方法：包括的ガイド](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)