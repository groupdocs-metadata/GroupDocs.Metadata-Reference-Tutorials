---
date: '2026-06-17'
description: Java で GroupDocs.Metadata を使用して、図ファイルの作成時間を変更し、メタデータの更新を自動化する方法を学びます。
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
title: GroupDocs Java でメタデータの図の作成時間を変更
type: docs
url: /ja/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# GroupDocs Java を使用したメタデータ内の図の作成時間の変更

このステップバイステップのチュートリアルでは、GroupDocs.Metadata ライブラリ for Java を使用して **図の作成時間を変更** し、図ファイルの他の組み込みプロパティを更新する方法を学びます。これらの変更を自動化することで、手作業の編集にかかる時間を何時間も節約でき、リポジトリ全体で一貫したタイムスタンプが保証され、任意のドキュメント管理システムで図が即座に検索可能になります。

## クイック回答
- **主な目的は何ですか？** 図ファイルの作成時間とその他のメタデータを変更します。  
- **どのライブラリを使用すべきですか？** GroupDocs.Metadata for Java。  
- **ライセンスは必要ですか？** テストには無料トライアルで十分です。製品環境ではフルライセンスが必要です。  
- **多数の図をバッチ処理できますか？** はい。同じロジックをループまたは並列ストリームでラップします。  
- **必要な Java バージョンは？** JDK 8 以上。

## 図メタデータにおける「作成時間の変更」とは何ですか？
作成時間を変更すると、図ファイル（VDX や VSDX など）に保存されている元のタイムスタンプが新しい日時値で上書きされます。これにより、ファイルのメタデータを作者の元のタイムスタンプではなく、実際の処理日やアーカイブ日と合わせることができ、監査トレイルや正確な検索結果に不可欠です。

## なぜ図のメタデータ更新を自動化するのか？
メタデータを自動化することで、すべての図が人為的ミスなしに同じ命名、カテゴリ付け、タイムスタンプ基準に従うようになります。また、バルク移行を高速化し、コンプライアンスリスクを低減し、エンタープライズ DMS プラットフォームでの発見性を向上させます。大規模プロジェクトでは手作業の労力を最大 70 % 削減できます。

## 前提条件
- **Java Development Kit (JDK) 8+** がマシンにインストールされていること。  
- **IDE**（IntelliJ IDEA や Eclipse など）。  
- **Maven**（または手動で JAR を管理）を使用した依存関係管理。  
- Java のクラス、メソッド、例外処理に関する基本的な知識。

### 必要なライブラリと依存関係
Maven を使用している場合は、`pom.xml` ファイルに以下のリポジトリと依存関係を追加してください。

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
直接ダウンロードを希望する場合は、[GroupDocs.Metadata for Java リリース](https://releases.groupdocs.com/metadata/java/) にアクセスして最新バージョンを取得してください。

### 環境設定
- JDK 8 以上。  
- IntelliJ IDEA、Eclipse、または任意の Java 対応 IDE。  

### 知識の前提条件
Java の構文と基本的なファイル I/O の理解があるとチュートリアルがスムーズになりますが、手順は平易な言葉で説明しています。

## GroupDocs.Metadata for Java の設定
### インストール手順
**Maven ユーザー:** 上記のスニペットはリポジトリと必要な JAR を自動的に追加します。  
**直接ダウンロードユーザー:** [GroupDocs](https://releases.groupdocs.com/metadata/java/) から JAR をダウンロードした後、プロジェクトのクラスパスに追加してください。

### ライセンス取得
- **無料トライアル:** ライブラリを無料で試すことができます。  
- **一時ライセンス:** 拡張テスト用に一時ライセンスを取得するには[こちら](https://purchase.groupdocs.com/temporary-license/)。  
- **購入:** 本番環境用にフルライセンスを取得します。

### 基本的な初期化
`Metadata` はドキュメントのメタデータコンテナを表すコアクラスで、すべての組み込みプロパティへの読み書きアクセスを提供します。GroupDocs.Metadata の使用を開始するには、クラスをインポートし、図ファイルを開きます:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

## 実装ガイド
### 図ファイルの作成時間を変更する方法
このセクションでは、**図の作成時間を変更**し、作者、会社、カテゴリなどの一般的なプロパティを更新するために必要な各ステップを順に説明します。プロセスは、Metadata API で図をロードし、ルートパッケージにアクセスし、目的のフィールドを設定し、最後に変更を新しいファイルに保存して元のファイルをそのまま残す、という流れです。

#### 手順 1: 図ドキュメントのロード
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*説明:* `Metadata` コンストラクタは図ファイルへのパスを受け取ります。try‑with‑resources ブロックにより、操作後にファイルが適切に閉じられます。

#### 手順 2: ルートパッケージへのアクセス
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*説明:* ルートパッケージは、図のすべての組み込みメタデータフィールドへの直接アクセスを提供します。

#### 手順 3: 作成者プロパティの設定
```java
root.getDocumentProperties().setCreator("test author");
```  
*説明:* 新しい作者名を割り当てます。`"test author"` を実際の作成者に置き換えてください。

#### 手順 4: 作成時間の変更
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*説明:* この行は **作成時間を** 現在のシステム日付と時刻に変更します。カスタムタイムスタンプが必要な場合は、特定の `Date` インスタンスを渡すこともできます。

#### 手順 5: 会社情報の定義
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*説明:* 図に関連付けられた会社名を保存します。エンタープライズのトラッキングに便利です。

#### 手順 6: ドキュメントカテゴリの設定
```java
root.getDocumentProperties().setCategory("test category");
```  
*説明:* ファイルにカテゴリを付与し、リポジトリ全体で **図のカテゴリを更新** できるようにします。

#### 手順 7: キーワードの追加
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*説明:* キーワードは検索性を向上させます。図の内容に関連する任意の用語を列挙できます。

#### 手順 8: 変更の保存
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*説明:* すべての変更を新しいファイルに永続化し、元のファイルはそのまま残します。

### よくある落とし穴とトラブルシューティング
- **ファイルが見つかりません:** 入力パスを確認し、ファイル拡張子が実際の形式と一致していることを確認してください。  
- **アクセスが拒否されました:** 入出力ディレクトリの読み書き権限を確認してください。  
- **無効な日付形式:** API と互換性のある `java.util.Date` または `java.time` オブジェクトを使用してください。

## 実用的な応用例
1. **ドキュメントアーカイブの自動化** – 古い図をアーカイブに移動する際、**図の作成時間を** アーカイブ日付に自動的に変更し、統一されたカテゴリを設定します。  
2. **バージョン管理との統合** – 各リリース時に作成時間を更新して、Git コミットとタイムスタンプを同期させます。  
3. **エンタープライズ DMS の標準化** – すべての図資産に対して、作者、会社、キーワードの社内ポリシーを適用します。

## パフォーマンス上の考慮点
- **バッチ処理:** 上記の手順をループでラップして、一度の実行で多数のファイルを処理します。  
- **メモリ管理:** 各 `Metadata` インスタンスを速やかに解放します（try‑with‑resources ブロックが自動的に行います）。  
- **非同期実行:** 大規模バッチの場合、`CompletableFuture` を使用してメインスレッドをブロックせずに並列で更新を実行することを検討してください。  
- **定量的な機能:** GroupDocs.Metadata は 30 以上の図フォーマットをサポートし、ファイル全体をメモリに読み込まずに最大 500 MB のファイルを処理でき、一般的なサーバハードウェア上でファイルあたり 200 ms 未満で更新を提供します。

## 結論
これで、Java の GroupDocs.Metadata を使用して **図の作成時間を変更** し、図ドキュメントの他の組み込みメタデータプロパティを更新する方法が分かりました。これらの手順を自動化することで、組織全体で一貫性があり、検索可能で、コンプライアンスに準拠したドキュメントを維持できます。

**次のステップ**
- GroupDocs.Metadata がサポートする他のファイル形式（PDF、DOCX など）を試してみてください。  
- コードを CI/CD パイプラインに統合し、すべてのビルドでメタデータ標準を適用します。  

試してみる準備はできましたか？[GroupDocs.Metadata for Java リリース](https://releases.groupdocs.com/metadata/java/) にアクセスして、今日から独自のメタデータ自動化を実装しましょう。

---

**最終更新日:** 2026-06-17  
**テスト環境:** GroupDocs.Metadata 24.12  
**作者:** GroupDocs  

## よくある質問

**Q: 他の図フォーマット（例: VSDX）でもこのアプローチを使用できますか？**  
A: はい、同じ API は GroupDocs.Metadata がサポートするすべての図フォーマットで機能します。

**Q: 開発ビルドにライセンスは必要ですか？**  
A: 開発・テストには無料トライアルで十分です。本番環境へのデプロイにはフルライセンスが必要です。

**Q: 1 回の呼び出しで複数のプロパティを更新するにはどうすればよいですか？**  
A: `metadata.save(...)` を呼び出す前に `DocumentProperties` オブジェクトに各プロパティを設定します。ライブラリはそれらを一括で書き込みます。

**Q: 元のファイルを上書きしても安全ですか？**  
A: 新しいファイルに保存し（上記参照）、更新が成功したことを確認してから元のファイルを置き換えることを推奨します。

**Q: 現在時刻ではなくカスタムの作成日付を設定したい場合はどうすればよいですか？**  
A: 目的のタイムスタンプで `java.util.Date`（または `java.time` インスタンス）を作成し、`setTimeCreated` に渡します。

## 関連チュートリアル
- [GroupDocs.Metadata を使用した Java での図メタデータ更新方法](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [GroupDocs.Metadata for Java を使用した DXF 作者メタデータ更新方法 – 完全ガイド](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [GroupDocs.Metadata を使用した日付による Java メタデータ更新の自動化 – 効率的なファイル管理](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)