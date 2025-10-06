---
title: .NET のスプレッドシートから検査プロパティを読み取る
linktitle: .NET のスプレッドシートから検査プロパティを読み取る
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata for .NET を使用してスプレッドシートから検査プロパティを読み取る方法を学習します。コメント、デジタル署名、非表示のシートに簡単にアクセスできます。
weight: 13
url: /ja/net/spreadsheet-metadata/read-inspection-properties-spreadsheets/
type: docs
---
# .NET のスプレッドシートから検査プロパティを読み取る

## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を使用してスプレッドシートのプロパティを検査する方法について説明します。GroupDocs.Metadata for .NET は、開発者がスプレッドシートを含むさまざまなファイル形式に関連付けられたメタデータを読み取り、編集、削除できるようにする強力なライブラリです。このチュートリアルでは、C# を使用してスプレッドシート ファイルから検査プロパティを読み取ることに特に焦点を当てています。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: 開発マシンに Visual Studio がインストールされていることを確認してください。
-  GroupDocs.Metadata for .NET: GroupDocs.Metadata for .NETを以下のサイトからダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/metadata/net/).
- 入力ファイル: サンプルのスプレッドシート ファイル (Excel ファイルなど) を準備して、そのプロパティを検査します。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ 1: メタデータをロードする
まず、入力スプレッドシート ファイルからメタデータを読み込みます。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
```
## ステップ2: 検査プロパティにアクセスする
ここで、コメント、デジタル署名、非表示のシートなどのさまざまな検査プロパティにアクセスしてみましょう。
### コメントを読む
スプレッドシートにあるコメントを取得して表示します。
```csharp
if (root.InspectionPackage.Comments != null)
{
    foreach (var comment in root.InspectionPackage.Comments)
    {
        Console.WriteLine("Author: " + comment.Author);
        Console.WriteLine("Comment Text: " + comment.Text);
        Console.WriteLine("Sheet Number: " + comment.SheetNumber);
        Console.WriteLine("Row: " + comment.Row);
        Console.WriteLine("Column: " + comment.Column);
        Console.WriteLine();
    }
}
```
### デジタル署名の読み取り
スプレッドシートに関連付けられたデジタル署名を抽出して表示します。
```csharp
if (root.InspectionPackage.DigitalSignatures != null)
{
    foreach (var signature in root.InspectionPackage.DigitalSignatures)
    {
        Console.WriteLine("Certificate Subject: " + signature.CertificateSubject);
        Console.WriteLine("Comments: " + signature.Comments);
        Console.WriteLine("Sign Time: " + signature.SignTime);
        Console.WriteLine();
    }
}
```
### 隠しシートの読み取り
スプレッドシート内の非表示のシートを取得して一覧表示します。
```csharp
if (root.InspectionPackage.HiddenSheets != null)
{
    foreach (var sheet in root.InspectionPackage.HiddenSheets)
    {
        Console.WriteLine("Sheet Name: " + sheet.Name);
        Console.WriteLine("Sheet Number: " + sheet.Number);
        Console.WriteLine();
    }
}
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用してスプレッドシートのさまざまなプロパティを検査する方法について説明しました。この機能をさらに拡張して、要件に応じてメタデータを操作、更新、または削除することができます。

## よくある質問
### GroupDocs.Metadata は、スプレッドシート以外のファイル形式からメタデータを読み取ることができますか?
はい、GroupDocs.Metadata は幅広いドキュメントおよび画像形式をサポートしています。
### GroupDocs.Metadata は .NET Core と互換性がありますか?
はい、GroupDocs.Metadata は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Metadata を使用してメタデータを編集するにはどうすればよいですか?
GroupDocs.Metadata API メソッドを使用してメタデータのプロパティを変更できます。
### GroupDocs.Metadata は暗号化されたドキュメントをサポートしていますか?
はい、GroupDocs.Metadata は暗号化されパスワードで保護されたファイル内のメタデータを処理できます。
### GroupDocs.Metadata を使用してファイルからメタデータを削除できますか?
はい、GroupDocs.Metadata ライブラリを使用してファイルからメタデータを削除できます。