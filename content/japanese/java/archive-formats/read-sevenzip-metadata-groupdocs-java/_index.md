---
date: '2025-12-20'
description: Java 用の GroupDocs.Metadata を使用して SevenZip アーカイブのメタデータを読み取る方法を学びましょう。これはメタデータ抽出
  Java プロジェクトにおける重要なステップです。
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: JavaでGroupDocs.Metadataを使用してSevenZipメタデータを読み取る方法
type: docs
url: /ja/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# JavaでGroupDocs.Metadataを使用してSevenZipメタデータの読み取り方法

Javaアプリケーションから**sevenzip**アーカイブ情報を読み取る方法をお探しなら、ここが最適な場所です。このチュートリアルでは、**GroupDocs.Metadata**を使用して、ファイル名、サイズ、日付など、バックアップ検証、同期、ストレージ最適化タスクに必要なデータを取得する方法について説明します。

## はじめに

Javaを使用してSevenZipアーカイブファイルのメタデータプロパティにアクセスして読み取るのに苦労していませんか？このチュートリアルでは、**GroupDocs.Metadata**の使用方法を説明します。強力なライブラリであるこのライブラリは、ファイル名、サイズ、更新日などの重要な情報をアーカイブから直接抽出することを簡素化します。

この記事では、**GroupDocs.Metadata for Java**を使用して、SevenZipファイル内のメタデータプロパティに効率的にアクセスする方法を説明します。

### 学習内容
- Java プロジェクトで GroupDocs.Metadata を設定する
- 特定のメソッドとクラスを使用して SevenZip アーカイブからメタデータを読み取る
- 名前、圧縮サイズ、変更日などの主要なファイル属性を抽出する実用的な例

## クイックアンサー
- **どのライブラリを使用すればよいですか？** Java 版 GroupDocs.Metadata
- **SevenZip アーカイブ内のファイルを一覧表示できますか？** はい – `getSevenZipPackage().getFiles()` を使用してください
- **ライセンスは必要ですか？** 評価には無料トライアルをご利用いただけますが、本番環境ではフルライセンスが必要です
- **サポートされている Java のバージョンは？** JDK8 以上
- **Maven は必須ですか？** 必須ではありませんが、Maven を使用すると依存関係の管理が簡素化されます

## Java で「sevenzip の読み取り方法」とは何ですか？
SevenZip メタデータの読み取りとは、`.7z` コンテナを開き、各エントリを列挙し、**圧縮サイズ**、**非圧縮サイズ**、**ファイル名**、**変更日** などのプロパティを、実際のファイルを解凍せずに取得することを意味します。

## メタデータ抽出に GroupDocs.Metadata Java を使用する理由
- **統合 API** – 数十種類のアーカイブおよびドキュメント形式に対応
- **外部ツール不要** – すべて Java プロセス内で処理されます
- **パフォーマンス重視** – メタデータ抽出 Java タスクに必要なヘッダー情報のみを読み取ります
- **堅牢なライセンス** – 試用版あり、商用利用にはフルライセンス

## 前提条件

**GroupDocs.Metadata for Java** を使用する前に、開発環境が適切に設定されていることを確認してください。必要な環境は次のとおりです。

- **Java 開発キット (JDK):** バージョン 8 以上。
- **Maven:** 依存関係の処理にはMavenの使用を推奨しますが、JARファイルを手動で追加することも可能です。
- **Javaの基礎知識:** クラス、メソッド、例外処理に関する知識。

## Java用GroupDocs.Metadataの設定

GroupDocs.Metadataを使用するには、Maven経由でプロジェクトに追加するか、ライブラリを直接ダウンロードしてプロジェクトに追加します。

### Mavenの使用

`pom.xml`ファイルに以下の設定を追加します。

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

または、[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) から最新バージョンをダウンロードしてください。

#### ライセンスの取得

1. **無料トライアル:** 無料トライアルで GroupDocs.Metadata の機能をお試しください。

2. **一時ライセンス:** 評価目的でアクセス期間を延長する必要がある場合は、一時ライセンスを申請してください。

3. **購入:** 長期使用の場合は、フルライセンスのご購入をご検討ください。

セットアップが完了したら、メタデータ読み取り機能の実装に進みましょう。

## 実装ガイド

### SevenZip アーカイブからのメタデータへのアクセス

このセクションでは、SevenZip アーカイブからファイル名やサイズなどのメタデータプロパティを抽出して出力します。

#### ステップ 1: メタデータ オブジェクトの初期化

まず、SevenZip ファイルへのパスを指定して `Metadata` オブジェクトを初期化します。これにより、GroupDocs はどのファイルを処理するかを知ることができます。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### ステップ 2: ルートパッケージを取得する

次に、アーカイブのルートパッケージにアクセスして、すべてのファイルとそのプロパティへのエントリポイントを取得します。

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **`getRootPackageGeneric()` を使う理由** アーカイブの内容を汎用的に表示することで、特定のファイル形式を気にすることなく、エントリの反復処理を容易にします。

#### ステップ 3: アーカイブエントリの反復処理

アーカイブのルートパッケージにアクセスしたら、各エントリを反復処理してメタデータプロパティを抽出します。これには、名前、圧縮サイズ、変更日などの詳細情報の取得が含まれます。

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

- **これらのプロパティを抽出する理由** ファイルサイズが分かればストレージ管理が容易になり、更新日は同期タスクにおいて重要になる場合があります。

#### ステップ 4: リソースのクリーンアップ

最後に、メタデータ オブジェクトを破棄して、GroupDocs.Metadata によって占有されているリソースを解放します。

```java
} finally {
    metadata.dispose();
}
```

- **なぜ破棄するのか？** オブジェクトを適切に破棄することで、長時間実行されるアプリケーションにおけるメモリリークを防ぐことができます。

## 実用的なアプリケーション

SevenZip メタデータの読み方を理解することで、多くの実用的なメリットが得られます。

1. **データバックアップ管理:** バックアップアーカイブの整合性と完全性を迅速に検証できます。

2. **ファイル同期ツール:** 更新日に基づいて、更新が必要なファイルを判断できます。

3. **ストレージ最適化:** 圧縮時と非圧縮時のサイズを比較して、容量計画を立てることができます。

他のシステムとの統合が可能で、より大規模なデータ管理ワークフローの一部として、メタデータの自動抽出を行うことができます。

## パフォーマンスに関する考慮事項

GroupDocs.Metadata と大規模なアーカイブを扱う際は、以下のヒントに留意してください。

- **バッチ処理:** ファイルをバッチ処理して、メモリ使用量を効率的に管理します。
- **効率的な例外処理:** try-with-resources を使用して、リソースを自動管理します。
- **非同期処理:** 負荷の高いワークロードには非同期処理を実装します。

## よくある問題と解決策

| 問題 | 解決策 |
|-------|----------|
| **ファイルアクセス時に`NullPointerException`が発生する** | アーカイブパスが正しく、ファイルが破損していないことを確認してください。|
| **巨大なアーカイブでメモリスパイクが発生する** | バッチ処理を有効にするか、JVMヒープサイズを増やしてください(`-Xmx`)。|
| **ライセンスが認識されない** | ライセンスファイルがアプリケーションの作業ディレクトリに配置されているか、`License.setLicense(path)` で設定されていることを確認してください。|

## よくある質問

**Q:** GroupDocs.Metadataとは何ですか？
**A:** SevenZipアーカイブを含む、さまざまなファイル形式のメタデータを処理するためのJavaライブラリです。

**Q:** GroupDocs.Metadata は Maven なしで使用できますか？
**A:** はい、公式サイトから JAR をダウンロードし、プロジェクトのクラスパスに追加できます。

**Q:** 大きなアーカイブを効率的に処理するにはどうすればよいですか？
**A:** バッチ処理を実装するか、非同期ストリームを使用してメモリ消費を制限してください。

**Q:** より詳細なガイダンスはどこで入手できますか？
**A:** 包括的な API リファレンスについては、[公式ドキュメント](https://docs.groupdocs.com/metadata/java/) を参照してください。

**Q:** ライブラリで問題が発生した場合はどうすればよいですか？
**A:** [GroupDocs サポートフォーラム](https://forum.groupdocs.com/c/metadata/) でコミュニティに質問してください。

## リソース

- **ドキュメント:** [GroupDocs.Metadata ドキュメント](https://docs.groupdocs.com/metadata/java/) で詳細をご確認ください。
- **API リファレンス:** [GroupDocs.API リファレンス](https://reference.groupdocs.com/metadata/java/) で詳細な API 情報をご確認ください。
- **ダウンロード:** [GroupDocs ダウンロード](https://releases.groupdocs.com/metadata/java/) から最新バージョンを入手してください。
- **GitHub リポジトリ:** [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) でコードサンプルにアクセスできます。
- **無料サポートフォーラム:** [GroupDocs 無料サポート](https://forum.groupdocs.com/c/metadata/) でディスカッションに参加したり、質問したりできます。

---

**最終更新日:** 2025年12月20日
**テスト済み対象:** GroupDocs.Metadata 24.12 for Java
**作成者:** GroupDocs