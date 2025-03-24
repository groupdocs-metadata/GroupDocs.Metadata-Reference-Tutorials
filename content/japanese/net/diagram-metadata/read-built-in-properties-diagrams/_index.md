---
title: .NET のダイアグラムから組み込みプロパティを読み取る
linktitle: .NET のダイアグラムから組み込みプロパティを読み取る
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata を使用して .NET のダイアグラム ファイルからメタデータを抽出する方法を学習します。ドキュメントの管理と分析を効率的に強化します。
weight: 10
url: /ja/net/diagram-metadata/read-built-in-properties-diagrams/
---

# .NET のダイアグラムから組み込みプロパティを読み取る

## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を使用してダイアグラムから組み込みプロパティを読み取る方法について詳しく説明します。GroupDocs.Metadata for .NET は、ダイアグラム、プレゼンテーション、画像など、さまざまなドキュメント タイプに関連付けられたメタデータを開発者が操作できるようにする強力なライブラリです。具体的には、このライブラリを使用してダイアグラム ファイルからメタデータ プロパティを抽出することに焦点を当てます。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
- C# および .NET 開発に関する基本的な知識。
- マシンに Visual Studio IDE がインストールされています。
-  GroupDocs.Metadata for .NETライブラリ。ここからダウンロードできます。[ここ](https://releases.groupdocs.com/metadata/net/).
- メタデータを抽出する入力ダイアグラム ファイル (例: .vsdx)。

## 名前空間のインポート
GroupDocs.Metadata 機能を使用するには、まず C# プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ1: ダイアグラムファイルを読み込む
まず、メタデータを抽出するダイアグラム ファイルを読み込みます。
```csharp
using (Metadata metadata = new Metadata("YourDiagramFile.vsdx"))
{
    //図のルート パッケージにアクセスする
    var root = metadata.GetRootPackage<DiagramRootPackage>();
    //さまざまなドキュメントプロパティにアクセスできるようになりました
    //いくつかのプロパティをコンソールに出力してみましょう
}
```
## ステップ 2: 組み込みプロパティにアクセスする
ダイアグラム ファイルがロードされると、次の方法でその組み込みプロパティにアクセスできます。`DocumentProperties`:
```csharp
Console.WriteLine(root.DocumentProperties.Creator);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.Language);
Console.WriteLine(root.DocumentProperties.TimeCreated);
Console.WriteLine(root.DocumentProperties.Category);
```
## ステップ 3: 他のメタデータ情報を利用する
とは別に`DocumentProperties`GroupDocs.Metadata は、図ファイルに固有の他のメタデータ プロパティへのアクセスを提供します。たとえば、図の種類に応じて、レイヤー、ページ、図形などにアクセスできます。

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して、図ファイルから組み込みプロパティを簡単に読み取る方法を検討しました。このライブラリを利用することで、開発者は、.NET アプリケーション内のさまざまなドキュメント タイプに関連付けられたメタデータを効率的に管理および抽出できます。

## よくある質問
### GroupDocs.Metadata for .NET ではどのような種類の図ファイルがサポートされていますか?
GroupDocs.Metadata for .NET は、.vsdx、.vssx、.vstx などを含む幅広い図ファイル形式をサポートしています。
### GroupDocs.Metadata for .NET を使用してメタデータ プロパティを変更できますか?
はい、このライブラリを使用すると、メタデータ プロパティを読み取るだけでなく、更新や削除もできます。
### GroupDocs.Metadata for .NET の試用版はありますか?
はい、無料試用版にアクセスできます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Metadata for .NET のテクニカル サポートを受けるにはどうすればよいですか?
技術的なサポートが必要な場合は、次のサイトにアクセスしてください。[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14).
### GroupDocs.Metadata for .NET のライセンスはどこで購入できますか?
からライセンスを購入できます[ここ](https://purchase.groupdocs.com/buy).