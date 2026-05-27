---
date: '2026-05-27'
description: GroupDocs Maven Dependency を使用して Java で pptx の CreatedTime を設定し、PowerPoint
  のメタデータを更新する方法を学びます。PPTX の作成日を変更する方法も含まれます。
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
title: GroupDocs Maven Dependency を使用して Java で PPTX の CreatedTime を設定する
type: docs
url: /ja/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# JavaでGroupDocs.Metadataを使用してPPTXのCreatedTimeを設定する

Accurate metadata is essential for compliance and discoverability in modern document workflows. With **GroupDocs.Metadata** you can programmatically **set PPTX CreatedTime in Java**, allowing you to **change PPTX creation date** alongside other built‑in properties such as author or company. This tutorial walks you through Maven setup, initializing the API, updating metadata, and saving the modified presentation—all with clear, production‑ready code.

## クイック回答
- **JavaでPowerPointメタデータを更新するライブラリはどれですか？** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **PPTXのCreatedTimeプロパティを設定できますか？** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **本番環境でライセンスが必要ですか？** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **この例で使用されているビルドツールは何ですか？** Maven (you can also download the JAR manually).  
- **APIはJava 8以降をサポートしていますか？** Absolutely—GroupDocs.Metadata targets Java 8+.

## GroupDocs Maven依存関係とは何ですか？
**GroupDocs Maven依存関係** は、Maven互換のリポジトリエントリで、最新のGroupDocs.MetadataライブラリをJavaプロジェクトに取り込みます。トランジティブなライブラリを自動的に解決し、常に最新かつ安全なバージョンを使用できることを保証し、手動でのJARダウンロードやバージョン管理の必要性を排除します。

## PPTX作成日を変更するためにGroupDocs.Metadataを使用する理由
GroupDocs.Metadata は、PPTXの作成タイムスタンプを自動化かつバッチ処理に対応した形で更新でき、すべてのプレゼンテーションが企業ポリシーや法的要件に準拠することを保証します。CreatedTimeプロパティをプログラムで設定することで、手動編集を回避し、ヒューマンエラーを減らし、CI/CDパイプラインやマイグレーションスクリプトに統合してシームレスな文書管理が可能になります。

## 前提条件
- Java 8以上がインストールされていること。  
- IntelliJ IDEAやEclipseなどのIDE。  
- 依存関係管理のためのMaven。  
- GroupDocsのトライアルまたは購入ライセンスへのアクセス。

## JavaでPPTX CreatedTimeを設定する方法？

`Metadata` クラスはドキュメントを表し、そのメタデータプロパティへのアクセスを提供します。

`new Metadata("presentation.pptx")` でPowerPointファイルをロードし、ルートパッケージを取得し、目的の `java.util.Date` を使用して `setCreatedTime` を呼び出し、最後に `save` を実行して変更を書き込みます。このエンドツーエンドのフローは、スライドの内容や他のプロパティを保持しながら作成日を変更します。

### Maven設定
GroupDocsリポジトリとメタデータ依存関係を `pom.xml` に追加します:

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

> **プロのヒント:** バージョン番号を最新に保つことで、最新のバグ修正やパフォーマンス向上の恩恵を受けられます。

### 直接ダウンロード（Mavenを使用したくない場合）
あるいは、最新のJARを [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) からダウンロードしてください。

#### ライセンス取得
まずは無料トライアルで開始するか、一時ライセンスをリクエストしてGroupDocs.Metadataを評価してください。本番環境で使用する場合は、[GroupDocsの公式ウェブサイト](https://purchase.groupdocs.com/temporary-license/) からライセンスを購入してください。

## 基本的な初期化と設定

ライブラリがクラスパスに配置されたら、PowerPointファイルを指す `Metadata` インスタンスを作成できます:

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

このコードは try‑with‑resources ブロックでプレゼンテーションを開き、ファイルハンドルが自動的に解放されることを保証します。

## 組み込みメタデータを更新するステップバイステップガイド

### 手順 1: プレゼンテーションドキュメントをロードする

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

ファイルをロードすると、メタデータの読み書きが可能な接続が確立されます。

### 手順 2: プレゼンテーションのルートパッケージにアクセスする

The `root` object gives access to the presentation's core package and its built‑in properties.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` オブジェクトはすべての組み込みドキュメントプロパティを公開します。

### 手順 3: 組み込みドキュメントプロパティを更新する（作成日を含む）

`setCreatedTime` assigns a new creation timestamp to the document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

ここでは、新しい `Date` オブジェクトを `CreatedTime` に割り当てて **PPTX CreatedTime を設定** する方法を示します。`new Date()` を必要な特定のタイムスタンプに置き換えてください。

### 手順 4: 更新されたプレゼンテーションを保存する

`save` writes the modified metadata back to a file.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` 呼び出しは、変更されたメタデータを新しいPowerPointファイルに書き込み、元のファイルはそのまま残します。

## トラブルシューティングのヒント
- **File Not Found:** 入力パスとファイル権限を再確認してください。  
- **Version Mismatch:** `groupdocs-metadata` のバージョンがJavaランタイムと一致していることを確認してください。  
- **Property Not Updating:** `save` を呼び出す前に `setCreatedTime`（または該当するセッター）を呼び出していることを確認してください。

## 実用的な活用例

1. **Corporate Branding:** 配布前にすべてのスライドデッキに正しい会社名とカテゴリを自動的に挿入します。  
2. **Document Management Systems:** PPTXファイルに検索可能なメタデータを付加し、より高速な検索を実現します。  
3. **Educational Resources:** 講義スライド全体で著者情報やカリキュラム情報を最新の状態に保ちます。  
4. **Collaboration Tracking:** 貢献者の名前を記録し、責任追跡を可能にします。  
5. **CMS Integration:** メタデータの変更をコンテンツ管理プラットフォームとリアルタイムで同期します。

## パフォーマンス上の考慮点
- **Batch Processing:** ファイルリストをループし、可能な限り単一の `Metadata` インスタンスを再利用します。  
- **Memory Management:** 常に try‑with‑resources を使用（上記参照）して、ネイティブリソースを速やかに解放します。  
- **Efficient Data Structures:** メタデータの更新をマップに格納してから適用し、繰り返し呼び出しを減らします。

## よくある質問

**Q: GroupDocs Maven依存関係の主な目的は何ですか？**  
最新のGroupDocs.MetadataライブラリをMavenベースのJavaプロジェクトに簡単に組み込む方法を提供します。

**Q: 他のプロパティに影響を与えずにPPTXの作成日を設定するにはどうすればよいですか？**  
`metadata.save()` を呼び出す前に `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` を使用してください。

**Q: 開発環境でこのコードを実行するのにライセンスは必要ですか？**  
開発・テストには一時的なトライアルライセンスで十分ですが、本番環境ではフルライセンスが必要です。

**Q: カスタムメタデータフィールドも更新できますか？**  
はい。GroupDocs.MetadataはAPIを通じて組み込みプロパティとカスタムプロパティの両方をサポートしています。

**Q: 誤って変更した場合に元に戻す方法はありますか？**  
元のファイルのコピーを保持するか、上書きする前に既存のプロパティ値を読み取り、必要に応じて復元してください。

## リソース
- [ドキュメント](https://docs.groupdocs.com/metadata/java/)
- [APIリファレンス](https://apireference.groupdocs.com/metadata/java/)

---

**最終更新日:** 2026-05-27  
**テスト環境:** GroupDocs.Metadata 24.12 for Java  
**作者:** GroupDocs  

---

## 関連チュートリアル

- [GroupDocs.Metadata Java APIを使用してPowerPointのカスタムメタデータを更新する](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [GroupDocs.Metadata Javaを使用してWord文書のメタデータを更新する方法：完全ガイド](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [文書管理のためにJavaでGroupDocs.Metadataを使用してPDFメタデータを効率的に更新する](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)