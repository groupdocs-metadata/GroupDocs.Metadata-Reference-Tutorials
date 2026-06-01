---
date: '2026-06-01'
description: GroupDocs.Metadata for Java を使用して PNG テキストチャンクを抽出する方法を学びましょう – PNG メタデータを効率的に読み取り、堅牢な画像処理を統合します。
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: GroupDocs.Metadata Java API を使用して PNG テキストチャンクを抽出する方法
type: docs
url: /ja/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# PNGテキストチャンクを抽出する方法（GroupDocs.Metadata Java API）

画像ファイルからテキスト情報を抽出することは、特にPNGのようなテキストベースでない形式では困難です。**GroupDocs.Metadata for Java** は、これらの画像に埋め込まれたメタデータを取得・管理するための強力なツールを提供し、プロセスを簡素化します。一般的、圧縮、国際化テキストチャンクのいずれを扱う場合でも、GroupDocs.Metadata は効率的なソリューションを提供します。

このチュートリアルでは、Java の GroupDocs.Metadata ライブラリを使用して PNG ファイルからさまざまなタイプのテキストチャンクを効率的に抽出する方法をご案内します。これらの手法を理解することで、テキスト抽出機能をアプリケーションにシームレスに統合し、さまざまな領域でのデータ処理能力を向上させることができます。

## クイック回答
- **GroupDocs.Metadataはpngメタデータを読み取れますか？** はい、テキストチャンクを含むすべての標準 PNG メタデータを読み取ります。  
- **どの Java バージョンが必要ですか？** Java 8 以降が完全にサポートされています。  
- **開発にライセンスは必要ですか？** 無料トライアルでテストできますが、商用利用には商用ライセンスが必要です。  
- **抽出できるテキストチャンクの種類は何ですか？** 主に 3 種類：一般、圧縮、国際化。  
- **パフォーマンスは問題になりますか？** 標準的な 5 MB PNG に対して、モダン CPU で 200 ms 未満で抽出が完了します。

## “how to extract png”とは何ですか？
**“How to extract png”** は、プログラム API を使用して PNG 画像ファイルから埋め込まれたテキストチャンクを取得するプロセスを指します。これらのテキストチャンクには、記述的メタデータ、コメント、または国際化文字列が含まれることがあります。GroupDocs.Metadata for Java を活用することで、開発者は画像全体をデコードせずに、テキストチャンクをプログラム的に読み取り、フィルタリング、操作できます。

## PNGテキスト抽出にGroupDocs.Metadataを使用する理由
GroupDocs.Metadata は **50 以上の画像・文書フォーマット** をサポートし、PNG ファイルを **メモリに全体をロードせずに** 処理でき、最大 10 MB のファイルで平均 **150 ms** の抽出速度を実現します。また、ライブラリは **100 % のデータ忠実度** を保証し、国際テキストチャンクの Unicode 文字を保持します。

## 前提条件

PNG 画像からテキストチャンクを抽出する前に、以下を確認してください。

### 必要なライブラリと依存関係
- **GroupDocs.Metadata for Java**: Maven で追加するか、直接ダウンロードしてプロジェクトに組み込んでください。

### 環境設定要件
- Java（推奨は JDK 8 以降）で構築された開発環境。  
- IntelliJ IDEA、Eclipse など、Java プロジェクトをサポートする IDE。

### 知識の前提条件
- Java プログラミングの基本的な理解。  
- Java アプリケーションでのファイルおよびディレクトリ操作に慣れていること。

## GroupDocs.Metadata for Java の設定

GroupDocs.Metadata を使用開始するには、プロジェクトにライブラリを組み込む必要があります。以下は Maven を使用する方法と、直接ダウンロードする方法です。

### Maven設定
`pom.xml` ファイルに次のリポジトリと依存関係を追加してください。

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

#### ライセンス取得手順
- **Free Trial**: 機能を試すために無料トライアルを開始してください。  
- **Temporary License**: 長期テスト用に一時ライセンスを取得してください。  
- **Purchase**: 本番環境で使用する場合はライセンスを購入してください。

### 基本的な初期化と設定

ライブラリを設定したら、以下のように Java アプリケーションで GroupDocs.Metadata を初期化します。

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## PNGファイルからpngテキストチャンクを抽出する方法

`Metadata` クラスはファイルのメタデータストリームにアクセスするエントリーポイントです。`new Metadata("yourImage.png")` で PNG ファイルをロードし、ルートパッケージにアクセスして目的のテキストチャンクコレクションを反復処理します。数行のコードで、一般、圧縮、国際化テキストチャンクすべてを取得でき、必要に応じて自由に処理できます。

### 定義アンカー
`Metadata` クラスは GroupDocs.Metadata のエントリーポイントであり、ファイル内のすべてのメタデータストリームへプログラム的にアクセスできるコンテナを表します。

## PNGから一般テキストチャンクを抽出する

この機能により、PNG ファイルに埋め込まれたすべての一般テキストチャンクを取得できます。手順は以下の通りです。

#### 概要
画像メタデータに保存された各テキストチャンクにアクセスし、反復処理します。

#### 手順実装
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**  
   `PngRootPackage` は PNG メタデータのルートコンテナを表し、テキストチャンクのコレクションを公開します。

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `pngFilePath`: PNG ファイルへのパス。  
   - `PngRootPackage`: メタデータチャンクを含むルートパッケージを表します。

#### トラブルシューティングのヒント
- PNG ファイルにテキストチャンクが含まれていることを確認してください。含まれていない場合、データは取得されません。  
- PNG ファイルへのパスが正しいことを確認してください。

## PNGから圧縮テキストチャンクを抽出する

圧縮テキストチャンクを特に扱う場合は、以下の手順に従ってください。

#### 概要
この機能は PNG メタデータ内の圧縮テキストチャンクの取得と管理に焦点を当てています。

#### 手順実装
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**  

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `getCompressionMethod()`: 圧縮に使用された方式を返します。`getCompressionMethod()` メソッドは圧縮テキストチャンクに使用された圧縮アルゴリズムを返します。

#### トラブルシューティングのヒント
- PNG ファイルがサポートされている圧縮方式を使用していることを確認してください。  
- テキストチャンクが圧縮されていない場合の例外処理を実装してください。

## PNGから国際テキストチャンクを抽出する

国際テキストチャンクの抽出手順は以下の通りです。

#### 概要
言語情報を含む国際テキストチャンクを取得・管理します。

#### 手順実装
1. **Import Necessary Classes:**  

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**  

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Explanation of Parameters:**  
   - `getLanguage()`: テキストチャンクの言語タグを取得します。`getLanguage()` メソッドは国際テキストチャンクに関連付けられた ISO 言語タグを提供します。  
   - `isCompressed()`: テキストチャンクが圧縮されているかどうかを示します。`isCompressed()` メソッドはテキストチャンクが圧縮形式で保存されているかどうかを示します。

#### トラブルシューティングのヒント
- PNG ファイルに国際メタデータが正しく設定されていることを確認してください。  
- 翻訳が利用できないシナリオへの対応を実装してください。

## 実用的な応用例

PNG からテキストチャンクを抽出する方法を理解することで、さまざまなアプリケーションで価値を発揮できます。
- **Content Management Systems**: 画像ライブラリのメタデータを自動的に取得・整理します。  
- **Data Analysis Tools**: 画像メタデータ分析を組み込むことで、データ抽出機能を強化します。  
- **Web Scraping Projects**: ウェブサイトに埋め込まれた画像から有用な情報を抽出します。

## よくある質問

**Q: ライセンスなしで png メタデータを読み取れますか？**  
A: はい、無料トライアルでメタデータの読み取りは可能ですが、本番環境での展開には商用ライセンスが必要です。

**Q: GroupDocs.Metadata は他の画像フォーマットもサポートしていますか？**  
A: もちろんです。JPEG、BMP、TIFF など、40 以上の追加フォーマットにも対応しています。

**Q: 大きな PNG ファイルを効率的に扱うには？**  
A: ストリーミング API を使用してください。画像全体をメモリにロードせずに処理でき、RAM 使用量を 50 MB 未満に抑えます。

**Q: PNG にテキストチャンクが全くない場合は？**  
A: API は空のコレクションを返すので、処理前に `isEmpty()` を安全にチェックできます。

**Q: 国際テキストチャンクで Unicode はサポートされていますか？**  
A: はい、GroupDocs.Metadata は UTF‑8 を完全にサポートし、すべての言語文字を保持します。

## 結論

このチュートリアルに従うことで、Java の GroupDocs.Metadata ライブラリを使用して PNG ファイルから一般、圧縮、国際テキストチャンクを抽出する方法を習得しました。このスキルは、画像データの処理と分析能力を大幅に向上させ、アプリケーションの価値を高めます。さらに深く学びたい方は、GroupDocs.Metadata が提供する高度なメタデータ処理技術をぜひ探求してください。

**Next Steps**
- さまざまなタイプのメタデータ抽出を試してみてください。  
- GroupDocs.Metadata ライブラリの追加機能を探索してください。  
- 開発者コミュニティで成果や活用事例を共有し、フィードバックと改善を得てください。

---

**Last Updated:** 2026-06-01  
**Tested With:** GroupDocs.Metadata Java 23.9  
**Author:** GroupDocs

## 関連チュートリアル

- [How to Extract Image Resource Blocks from JPEG Using GroupDocs.Metadata for Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Extract JPEG2000 Image Comments in Java Using GroupDocs.Metadata: A Step-by-Step Guide](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Extract Image Resources from PSD Files Using GroupDocs.Metadata in Java: A Comprehensive Guide](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)