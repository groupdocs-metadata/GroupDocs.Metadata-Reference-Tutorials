---
title: .NET で PDF から組み込みプロパティを読み取る
linktitle: .NET で PDF から組み込みプロパティを読み取る
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata を使用して .NET で PDF メタデータを読み取る方法を学習します。C# コードを使用して、作成者名、作成日、件名などにアクセスします。
weight: 10
url: /ja/net/pdf-metadata/read-built-in-properties-pdfs/
---

# .NET で PDF から組み込みプロパティを読み取る

## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を利用して PDF ファイルから組み込みプロパティを読み取る方法について説明します。GroupDocs.Metadata は、開発者が PDF、Microsoft Office ドキュメント、画像など、さまざまなドキュメント形式に関連付けられたメタデータを操作できるようにする強力なライブラリです。このライブラリを使用すると、作成者名、作成日、件名など、PDF ファイルに埋め込まれたメタデータ属性に簡単にアクセスして操作できます。
## 前提条件
このチュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
- Visual Studio: マシンに Visual Studio がインストールされていることを確認してください。
-  GroupDocs.Metadata for .NET: GroupDocs.Metadata for .NETを以下のサイトからダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/metadata/net/).
- C# の基礎知識: C# プログラミング言語と .NET フレームワークに精通していること。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間を追加します。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ1: PDFメタデータを読み込む
まず、PDF ファイルを読み込み、GroupDocs.Metadata を使用してメタデータを抽出します。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // PDFファイルのルートパッケージにアクセスする
    var root = metadata.GetRootPackage<PdfRootPackage>();
    //組み込みプロパティを取得して表示する
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    //追加のプロパティも同様にアクセスできます
    //...
}
```
GroupDocs.Metadata では、メタデータの読み取りだけでなく、プログラムによる PDF ファイルのメタデータ プロパティの編集、削除、追加などの高度な操作も実行できます。この柔軟性により、.NET アプリケーション内でドキュメント メタデータを包括的に管理できます。
## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を利用して、C# で PDF ファイルから組み込みプロパティを抽出する方法について説明しました。このライブラリをプロジェクトに統合することで、ドキュメント メタデータ操作をシームレスに処理し、強化されたドキュメント管理機能を提供できます。

## よくある質問
### GroupDocs.Metadata は他のドキュメント形式でも動作しますか?
はい、GroupDocs.Metadata は、DOCX、XLSX、PPTX、PDF、JPG、PNG など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Metadata に利用できる無料トライアルはありますか?
はい、次から GroupDocs.Metadata の無料トライアルにアクセスできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Metadata を使用してメタデータ プロパティを変更するにはどうすればよいですか?
対応するドキュメント パッケージにアクセスし、新しい値を設定することで、メタデータ プロパティをプログラムで変更できます。
### GroupDocs.Metadata は .NET Core をサポートしていますか?
はい、GroupDocs.Metadata は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Metadata に関するサポートや質問はどこで見つけられますか?
サポートとディスカッションについては、次のサイトにアクセスしてください。[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14).