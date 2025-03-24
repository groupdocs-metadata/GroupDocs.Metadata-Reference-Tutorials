---
title: .NET を使用してスプレッドシートの組み込みプロパティを更新する
linktitle: .NET を使用してスプレッドシートの組み込みプロパティを更新する
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata for .NET を使用して Excel ファイルの組み込みメタデータ プロパティを更新する方法を学習します。 C# を使用して作成者、作成時刻、会社などを変更します。
weight: 14
url: /ja/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を利用して、C# を使用してスプレッドシート ファイルの組み込みプロパティを更新する方法を検討します。 GroupDocs.Metadata は、開発者がスプレッドシートを含むさまざまなファイル形式からメタデータ プロパティを読み取り、編集、削除できる強力な API です。特に、Excel ファイル内の作成者、作成時刻、会社、カテゴリ、キーワードなどのプロパティの変更に焦点を当てます。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: 最新バージョンの Visual Studio をインストールします。
-  GroupDocs.Metadata for .NET: GroupDocs.Metadata for .NETを以下のサイトからダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/metadata/net/).
- C# の基本知識: C# プログラミング言語と .NET フレームワークの理解。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ1: スプレッドシートファイルを読み込む
まず、`Metadata`入力スプレッドシート ファイルをロードしてオブジェクトを取得します。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    //ルート内のドキュメント プロパティにアクセスする
}
```
## ステップ 2: 組み込みプロパティを更新する
組み込みのドキュメント プロパティにアクセスするには、`SpreadsheetRootPackage`必要に応じて変更します。
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
プレースホルダー (`YourAuthorName`, `YourCompany`, `YourCategory`プロパティに設定する実際の値を置き換えます。
## ステップ3: 変更を保存する
プロパティを更新した後、変更をスプレッドシート ファイルに保存し直します。
```csharp
metadata.Save("YourInputFile.xlsx");
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して、スプレッドシート ファイルの組み込みプロパティをプログラムで更新する方法を説明しました。この API を活用することで、開発者は Excel ドキュメント内のメタデータを効率的に管理し、データの編成とアクセシビリティを強化できます。

## よくある質問
### GroupDocs.Metadata はどのようなファイル形式をサポートしていますか?
GroupDocs.Metadata は、Microsoft Office ドキュメント、PDF、画像、音声ファイルなどを含む幅広いファイル形式をサポートしています。
### ファイルから既存のメタデータ プロパティを取得できますか?
はい、GroupDocs.Metadata を使用して、作成者、作成日、キーワード、カスタム プロパティなどのメタデータ プロパティを抽出して読み取ることができます。
### GroupDocs.Metadata は .NET Core と互換性がありますか?
はい、GroupDocs.Metadata は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Metadata には無料トライアルが提供されていますか?
はい、GroupDocs.Metadata の無料トライアルを次のサイトからダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Metadata のサポートはどこで見つけられますか?
サポートとディスカッションについては、次のサイトにアクセスしてください。[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14).