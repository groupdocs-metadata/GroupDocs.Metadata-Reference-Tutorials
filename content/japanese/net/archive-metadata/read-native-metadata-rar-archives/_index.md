---
title: .NET で RAR アーカイブからネイティブ メタデータ プロパティを読み取る
linktitle: .NET で RAR アーカイブからネイティブ メタデータ プロパティを読み取る
second_title: GroupDocs.Metadata .NET API
description: C# で GroupDocs.Metadata for .NET を使用して RAR アーカイブからメタデータ プロパティを抽出する方法を学習します。ファイルの詳細を簡単に調べることができます。
weight: 10
url: /ja/net/archive-metadata/read-native-metadata-rar-archives/
type: docs
---
# .NET で RAR アーカイブからネイティブ メタデータ プロパティを読み取る

## 導入
RAR (Roshal Archive) は、データの圧縮とアーカイブ化に使用される一般的なファイル形式です。.NET アプリケーションで RAR ファイルを操作する場合、これらのアーカイブ内に埋め込まれたメタデータ プロパティを読み取って抽出することが必要になることがよくあります。このチュートリアルでは、GroupDocs.Metadata for .NET を使用して RAR アーカイブからネイティブ メタデータ プロパティにアクセスし、抽出するプロセスについて説明します。
## 前提条件

始める前に、次の前提条件を満たしていることを確認してください。
- C# プログラミング言語の基本的な理解。
- 開発マシンに Visual Studio がインストールされています。
-  GroupDocs.Metadata for .NETライブラリがインストールされている（[ダウンロードリンク](https://releases.groupdocs.com/metadata/net/)）。
- テスト目的での RAR アーカイブ ファイルへのアクセス。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## ステップ1: RARアーカイブをロードする
まず、`Metadata` RAR アーカイブ ファイルをロードしてオブジェクトを作成します。
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## ステップ2: RARアーカイブ内のエントリの合計数にアクセスする
RAR アーカイブ内のエントリ (ファイル/フォルダー) の合計数を取得します。
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## ステップ 3: アーカイブ内のファイルを反復処理する
RAR アーカイブ内の各ファイルをループして、特定のメタデータ プロパティにアクセスします。
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して RAR アーカイブからメタデータ プロパティを抽出する方法を学習しました。このライブラリは、さまざまなファイル形式に埋め込まれたメタデータにアクセスして利用するプロセスを簡素化し、.NET アプリケーションの機能を強化します。

## よくある質問
### .NET 用の GroupDocs.Metadata とは何ですか?
GroupDocs.Metadata for .NET は、開発者が RAR などのアーカイブを含むさまざまなファイル形式のメタデータを操作できるようにする強力なライブラリです。
### GroupDocs.Metadata for .NET の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスは次から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Metadata は RAR 以外のアーカイブ形式をサポートしていますか?
はい、GroupDocs.Metadata は、ZIP、TAR、7z などの幅広いアーカイブ形式をサポートしています。
### このライブラリを使用して、メタデータのプロパティを変更し、RAR アーカイブ内で更新できますか?
はい、GroupDocs.Metadata を使用すると、サポートされているファイル形式のメタデータ プロパティを更新、削除、追加できます。
### GroupDocs.Metadata に関する追加のヘルプやサポートはどこで見つかりますか?
訪問[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14)コミュニティのサポートとディスカッションのため。