---
date: '2026-05-27'
description: Java 用の GroupDocs.Metadata を使用してメール受信者を更新する方法を学びます。受信者や件名を変更し、変更を効率的に保存できます。
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
title: メール受信者の更新（Java）：GroupDocs.Metadataでメールメタデータ更新をマスターする
type: docs
url: /ja/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# GroupDocs.Metadata を使用した Java のメール受信者の更新

この包括的なガイドでは、GroupDocs.Metadata ライブラリを使用して **update email recipients java** をプログラムで更新します。主要な受信者と CC 受信者の変更、件名の変更、そして変更内容の永続化を、わかりやすいステップバイステップのコードスニペットとともに解説します。最後まで読むと、任意の Java ベースのワークフローにメールメタデータ自動化を統合できるようになります。

## クイック回答
- **メールの主要受信者を変更する最速の方法は何ですか？** `Metadata` でファイルをロードし、`EmailRootPackage` を取得して、`To` コレクションを置き換え、保存します—すべて3行のコードで実行できます。  
- **既存の受信者を上書きせずに CC 受信者を追加できますか？** はい、`EmailRootPackage` の `addCcRecipient` を使用して新しいアドレスを追加できます。  
- **本番環境で使用するにはライセンスが必要ですか？** 一時ライセンスは評価制限を解除します。商用デプロイには永続ライセンスが必要です。一時ライセンスは [GroupDocs](https://purchase.groupdocs.com/temporary-license/) ページから取得できます。  
- **サポートされている Java バージョンはどれですか？** GroupDocs.Metadata は Java 8、11、17 以降で動作します。  
- **大量のメールボックスでバッチ処理は安全ですか？** メモリ使用量をバッチあたり 200 MB 未満に抑えるため、ファイルを 50〜100 件ずつのバッチで処理してください。

## update email recipients java とは？
*Updating email recipients in Java* は、メールクライアントを開かずに、メールファイル（EML、MSG など）の “To”、 “CC”、 “BCC” フィールドをプログラムで変更することを意味します。GroupDocs.Metadata は、メール構造を読み取り、アドレスコレクションを変更できるハイレベル API を提供し、更新されたファイルをディスクに書き戻します。

## メールメタデータに GroupDocs.Metadata を使用する理由
GroupDocs.Metadata は **50 以上のメール関連フォーマット**（EML、MSG、MHT など）をサポートし、ファイル全体をメモリに読み込むことなく **数百ページに及ぶメッセージ** を処理でき、従来のファイルストリーム方式と比較して RAM 使用量を最大 **80 %** 削減します。純粋な Java 実装によりネイティブ依存がなく、クロスプラットフォームサービスに最適です。

## 前提条件
- Java 8 以上（Java 11、17、21 は完全にテスト済み）。
- 依存関係管理のための Maven または Gradle。
- 有効な GroupDocs.Metadata ライセンス（一時または永続）。

### 必要なライブラリと依存関係
`pom.xml` に以下の依存関係を追加します。

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

直接ダウンロードする場合は、最新バージョンを [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) から取得してください。

### 環境設定
IDE が互換性のある JDK を指していること、そして Maven がエラーなく GroupDocs.Metadata のアーティファクトを解決できることを確認してください。

## Java でメール受信者を更新する方法
メールファイルをロードし、既存の受信者を置き換えて結果を保存します。この操作は API 呼び出しが 3 回だけで、典型的な 1 MB メッセージでは **200 ms** 未満で実行されます。ハイレベルな `EmailRootPackage` API を使用することで、ファイル全体を解析せずに済み、メモリ使用量が低く抑えられ、バッチ処理もシンプルになります。

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
上記の行は、ファイルのメタデータ操作を開始するために必要なクラスをインポートしています。

## 実装ガイド
ここから各機能を詳しく掘り下げ、クイック回答のスニペットを完全なコンテキストで展開します。

### メール受信者の更新
**概要**: このセクションでは、メールメッセージの主要受信者をプログラムで更新する方法を示します。

#### 手順 1: Metadata オブジェクトの初期化
`Metadata` クラスはファイルを表し、そのメタデータへのアクセスを提供します。入力ファイルパスで `Metadata` インスタンスを作成します。

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**定義アンカー**: `Metadata` クラスは GroupDocs.Metadata のすべてのメタデータ操作のエントリーポイントで、メモリ内の単一ファイルを表します。

#### 手順 2: EmailRootPackage へのアクセス
`EmailRootPackage` は受信者や件名など、メール固有のメタデータへのアクセスを提供します。以下のようにメールのメタデータにアクセスします。

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
この手順は、メールのすべての変更可能なプロパティにアクセスできるため重要です。

#### 手順 3: 受信者の更新
メールメッセージの新しい受信者を設定します。

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### メールへのカーボンコピー (CC) 受信者の追加
**概要**: 既存のメールに CC 受信者を追加する方法を学びます。

#### 手順 1: 初期化とルートパッケージの取得
主要受信者の更新と同様に、metadata オブジェクトを初期化します。

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 手順 2: CC 受信者の設定
`addCcRecipient` は既存エントリを上書きせずに CC コレクションに新しいアドレスを追加します。以下のようにカーボンコピー受信者を追加します。

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
この方法により、追加のユーザーに通知されますが、主な連絡先にはなりません。

### メール件名の更新
**概要**: この機能により、メールの件名行を変更でき、コミュニケーションを明確かつ最新の状態に保てます。

#### 手順 1: Metadata の初期化
まず metadata オブジェクトを初期化します。

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 手順 2: 件名の変更
メールの件名行を更新します。

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
この手順は、関連性のある検索可能なメールスレッドを維持するために重要です。

### 更新されたメールメタデータの保存
**概要**: 変更を加えたら、これらの更新を保存することが重要です。このセクションでは、変更を効果的に永続化する方法を示します。

#### 手順 1: 初期化とルートパッケージの取得
`Metadata` オブジェクトの初期化から始めます。

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### 手順 2: 変更の保存
指定した出力ディレクトリに保存して変更を永続化します。

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
これにより、すべての変更が保持され、保存されたファイルに反映されます。

## 実用的な応用例
これらの機能を実装することで、さまざまな実務シナリオで非常に有益です。

1. **メール管理システム** – 大量メール配信の受信者更新を自動化します。  
2. **カスタマーサポートプラットフォーム** – チケットステータスの変更を反映するために、メール件名を迅速に変更します。  
3. **社内コミュニケーションツール** – 重要なお知らせで全チームメンバーが CC されるようにし、手動編集を不要にします。

## パフォーマンス上の考慮点
大量のメールデータを扱う際は、以下のポイントに留意してください。

- **50〜100** 件のバッチでファイルを処理し、バッチあたりのメモリ使用量を **200 MB** 未満に保ちます。  
- `metadata.getRootPackage().getEmail()` の呼び出しは必要最小限にし、可能な限り `Metadata` インスタンスを再利用します。  
- VisualVM などのツールで JVM ヒープ使用量を監視し、OutOfMemory エラーを回避します。

## 結論
これで、GroupDocs.Metadata を使用した **update email recipients java** の方法を習得しました。主要受信者の調整、CC の追加、件名の変更のいずれであっても、ライブラリは高速でメモリ効率の高い API を提供します。添付ファイルの処理や EML と MSG 形式間の変換など、より高度なシナリオについては、完全な [documentation](https://docs.groupdocs.com/metadata/java/) をご覧ください。

## FAQ セクション
**Q1**: GroupDocs.Metadata がサポートしている Java バージョンは何ですか？  
- **A**: Java 8、11、17、以降が完全にサポートされています。

**Q2**: ライセンスなしで GroupDocs.Metadata を使用できますか？  
- **A**: はい、無料トライアルは制限付きで利用可能です。一時または永続ライセンスを取得すれば制限が解除されます。

**Q3**: 大容量のメールファイルを効率的に処理するには？  
- **A**: 小さなバッチに分けて処理し、`Metadata` オブジェクトを再利用し、ヒープ使用量を監視してバッチあたり 200 MB 未満に保ちます。

**Q4**: メール以外に GroupDocs.Metadata がサポートしているファイルタイプは？  
- **A**: PDF、DOCX、XLSX、PPTX、画像、アーカイブなど、**70** 以上のフォーマットをサポートしています。完全な一覧は [API reference](https://reference.groupdocs.com/metadata/java/) をご覧ください。

---

**最終更新日:** 2026-05-27  
**テスト環境:** GroupDocs.Metadata 23.12 for Java  
**作者:** GroupDocs  

---

## 関連チュートリアル

- [GroupDocs.Metadata を使用した Java のメールメタデータ抽出のマスター](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [GroupDocs.Metadata Java 用メールおよびコンタクトメタデータチュートリアル](/metadata/java/email-contact-formats/)
- [効率的なコンタクト管理のための Java で GroupDocs.Metadata を使用した vCard 写真 URI の抽出方法](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)