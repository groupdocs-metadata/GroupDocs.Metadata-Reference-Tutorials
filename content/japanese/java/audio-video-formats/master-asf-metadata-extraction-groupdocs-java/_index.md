---
date: '2025-12-26'
description: GroupDocs.Metadata for Java を使用して ASF メタデータを抽出する方法を学びましょう。このガイドでは、セットアップ、プロパティの読み取り、コーデック情報へのアクセスについて説明します。
keywords:
- ASF Metadata Extraction
- GroupDocs.Metadata for Java
- Java Media Management
title: GroupDocs.Metadata for Java を使用して ASF メタデータを抽出する方法
type: docs
url: /ja/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# Extract ASF Metadata with GroupDocs.Metadata for Java

**Introduction**

今日のデジタル環境では、マルチメディアコンテンツを効率的に管理することが重要です。メディアファイルから **ASF メタデータを抽出** する必要がある場合、手作業で行うと時間がかかりミスも起きやすくなります。本チュートリアルでは、 **GroupDocs.Metadata for Java** を使用して ASF のさまざまなプロパティを読み取り表示する方法を解説し、資産の整理・検索・処理を自信を持って行えるようにします。

### What You’ll Learn
- Java プロジェクトに GroupDocs.Metadata を設定する方法  
- 作成日、ファイル ID、フラグなど **ASF メタデータを抽出** する方法  
- ASF ファイルに埋め込まれたコーデック情報を読み取る方法  
- 詳細なメタデータ記述子とベースストリームプロパティを表示する方法  

それでは、前提条件から始めましょう。

## Quick Answers
- **What does “extract ASF metadata” mean?** プログラムから ASF ファイルに埋め込まれた情報（タイムスタンプ、コーデック、記述子など）を読み取ることを指します。  
- **Which library is required?** GroupDocs.Metadata for Java（バージョン 24.12 以降）。  
- **Do I need a license?** 開発時は無料トライアルまたは一時ライセンスで動作します。商用・本番環境では正式ライセンスが必要です。  
- **What Java version is supported?** JDK 8 以上。  
- **Can I use Maven?** はい – Maven が推奨される依存関係マネージャです。

## Prerequisites

- **Java Development Kit (JDK)** 8 以上がインストールされていること。  
- **IDE**（IntelliJ IDEA や Eclipse など）で快適にコーディングできる環境。  
- **Maven** が IDE に設定されていること（任意ですが推奨）。  
- Java と外部ライブラリの基本的な知識。

## Setting Up GroupDocs.Metadata for Java

### Maven Installation

`pom.xml` にリポジトリと依存関係を追加します。

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

### Direct Download

Maven を使用したくない場合は、[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) から最新の JAR をダウンロードしてください。

### Licensing Overview

- **Free Trial** – GroupDocs のウェブサイトで評価用に利用可能。  
- **Temporary License** – 開発中に制限なくすべての機能を試せます。  
- **Full License** – 商用または本番環境での導入に必須。

### Basic Initialization

以下は GroupDocs.Metadata で ASF ファイルを開くための最小コードです。

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## What Is ASF Metadata?

ASF（Advanced Systems Format）は、Microsoft が提供するストリーミング形式で、音声・動画・メタデータを単一コンテナに格納します。メタデータには作成タイムスタンプ、コーデック情報、ストリーム記述子などが含まれます。 **ASF メタデータを抽出** することで、ファイルの出所やエンコードパラメータ、コンテンツの説明をプログラムから取得でき、メディアライブラリやトランスコーディングパイプライン、コンプライアンス監査に不可欠です。

## Why Extract ASF Metadata with GroupDocs.Metadata?

- **Zero‑code parsing** – 低レベルの ASF パーサーを自前で実装する必要がありません。  
- **Rich object model** – 直感的な Java クラスを通じてプロパティ、コーデック、記述子、ストリーム詳細にアクセスできます。  
- **Cross‑platform** – Java が動作するあらゆる OS で利用可能です。  
- **License flexibility** – トライアルから始め、必要に応じてフルライセンスへ拡張できます。

## Implementation Guide

以下のセクションでは、 **ASF メタデータを抽出** する具体的なコード例を段階的に示します。

### Reading Basic ASF Metadata Properties

**Overview** – 作成日、ファイル ID、フラグといった基本情報を取得します。

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

*Why it matters*: 作成日を把握することでバージョン管理が容易になり、ファイル ID はシステム間で資産を一意に識別できます。

### Displaying ASF Codec Information

**Overview** – オーディオ・ビデオストリームで使用されているコーデックを列挙します。

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

*Why it matters*: コーデック情報は再生デバイスとの互換性確認や、トランスコードの必要性判断に重要です。

### Displaying Metadata Descriptors

**Overview** – 言語、ストリーム番号、オリジナルタイトルなどの詳細記述子を取得します。

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

*Why it matters*: 記述子は字幕の言語や元ファイル名など、カタログ化に役立つ文脈情報を提供します。

### Displaying Base Stream Properties

**Overview** – 各ベースストリームのビットレート、タイミング、言語情報にアクセスします。

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

*Why it matters*: ストリームプロパティは品質（ビットレート）の評価や、再生・編集時の音声・映像同期に役立ちます。

## Common Issues & Troubleshooting

| 症状 | 考えられる原因 | 対策 |
|------|----------------|------|
| `NullPointerException` が `getAsfPackage()` 呼び出し時に発生 | ファイルパスが間違っている、または有効な ASF コンテナではない | パスを確認し、ファイルが正しい ASF 形式であることを確認してください |
| コーデック情報が表示されない | ASF ファイルがライブラリバージョンで認識されない独自コーデックを使用している | GroupDocs.Metadata を最新バージョンに更新するか、カスタムコーデックパーサーを使用してください |
| 記述子リストが空 | ファイルにメタデータ記述子が含まれていない（エンコード時に除去された） | メタデータが埋め込まれたソースファイルを使用するか、メタデータ保持設定で再エンコードしてください |

## Frequently Asked Questions

**Q: Can I extract metadata from other video formats with the same library?**  
A: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, and many more. Just instantiate the appropriate package class.

**Q: Is it possible to modify ASF metadata after extraction?**  
A: Absolutely. The library provides setter methods for most properties, allowing you to edit and then save the file.

**Q: Do I need a 64‑bit JVM for large ASF files?**  
A: Not necessarily, but a 64‑bit JVM gives you more heap space, which helps when processing very large media files.

**Q: How does licensing affect trial usage?**  
A: The trial license removes all functional limits but adds a watermark to certain outputs. For production, purchase a full license.

**Q: Can I run this code on Android?**  
A: GroupDocs.Metadata is built for Java SE; for Android you’d need to use the .NET version or a compatible wrapper.

## Conclusion

このガイドに従って、 **GroupDocs.Metadata for Java** を使用した **ASF メタデータの抽出** 方法を習得できました。基本プロパティ、コーデック情報、詳細記述子、ストリーム属性を読み取ることで、メディア資産をフルに可視化できます。次のステップとして、バッチ処理パイプラインへの統合、検索可能なメタデータデータベースの構築、またはコードを拡張して ASF ファイルの編集・再保存を検討してください。

---

**Last Updated:** 2025-12-26  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs