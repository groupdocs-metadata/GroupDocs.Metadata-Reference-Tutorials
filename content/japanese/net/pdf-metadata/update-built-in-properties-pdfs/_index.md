---
title: .NET を使用して PDF の組み込みプロパティを更新する
linktitle: .NET を使用して PDF の組み込みプロパティを更新する
second_title: GroupDocs.Metadata .NET API
description: C# と GroupDocs.Metadata for .NET を使用して PDF ドキュメントのプロパティを更新する方法を学習します。作成者、タイトル、キーワードなどをプログラムで変更します。
weight: 15
url: /ja/net/pdf-metadata/update-built-in-properties-pdfs/
---
## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して PDF ドキュメントの組み込みプロパティを更新する方法を学習します。このライブラリは、さまざまなドキュメント形式内のメタデータを操作するための強力なツール セットを提供します。C# を使用して、PDF ファイルの作成者、タイトル、作成日、キーワード、作成者、プロデューサーなどのプロパティを変更するために必要な手順を説明します。
## 前提条件
始める前に、以下のものを用意しておいてください。
-  GroupDocs.Metadata for .NETライブラリ: ライブラリをここからダウンロードしてください[ここ](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: C# コードを記述して実行するには、Visual Studio をインストールします。
- C# の基本的な理解: C# プログラミング言語に精通していることが推奨されます。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間を含めます。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ1: メタデータオブジェクトの初期化
を初期化することから始めます`Metadata`PDF ファイルへのパスを持つオブジェクト:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    //コードはここに入力してください
}
```
## ステップ2: PDFルートパッケージにアクセスする
次に、PDF専用のルートパッケージを取得します。`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## ステップ3: ドキュメントのプロパティを更新する
次に、PDFドキュメントの必要なプロパティを更新します。`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## ステップ4: 変更を保存する
プロパティを変更したら、変更を PDF ファイルに保存します。
```csharp
metadata.Save("Your Output File Path");
```
## ステップ5: 更新されたプロパティを取得する
変更を確認するには、メタデータを再読み込みし、更新されたプロパティを取得します。
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を利用して PDF ドキュメントの組み込みプロパティをプログラムで更新する方法について説明しました。概要の手順に従うことで、C# を使用して PDF ファイル内のメタデータを効率的に管理および変更できます。包括的なメタデータ操作のために、GroupDocs.Metadata が提供するその他の機能や機能を自由に探索してください。

## よくある質問
### Q: GroupDocs.Metadata for .NET とは何ですか?
A: GroupDocs.Metadata for .NET は、開発者がさまざまなドキュメント形式のメタデータをプログラムで読み取り、編集、削除、操作できるようにするライブラリです。
### Q: GroupDocs.Metadata for .NET のドキュメントはどこにありますか?
 A: ドキュメントにアクセスできます[ここ](https://tutorials.groupdocs.com/metadata/net/).
### Q: GroupDocs.Metadata for .NET をダウンロードするにはどうすればいいですか?
 A: GroupDocs.Metadata for .NETは以下からダウンロードできます。[このリンク](https://releases.groupdocs.com/metadata/net/).
### Q: 無料トライアルはありますか?
 A: はい、無料試用版を入手できます[ここ](https://releases.groupdocs.com/).
### Q: GroupDocs.Metadata for .NET のサポートはどこで受けられますか?
 A: サポートについては、GroupDocs.Metadata フォーラムをご覧ください。[ここ](https://forum.groupdocs.com/c/metadata/14).