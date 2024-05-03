---
title: .NET を使用してプレゼンテーションの組み込みプロパティを更新する
linktitle: .NET を使用してプレゼンテーションの組み込みプロパティを更新する
second_title: GroupDocs.Metadata .NET API
description: 多目的メタデータ操作ライブラリである GroupDocs.Metadata を使用して .NET でプレゼンテーションの組み込みプロパティを更新する方法を学習します。
type: docs
weight: 15
url: /ja/net/presentation-metadata/update-built-in-properties-presentations/
---
## 導入
このチュートリアルでは、.NET フレームワークを使用してドキュメント内のメタデータを操作するために設計された包括的なライブラリである GroupDocs.Metadata for .NET の強力な機能を詳しく説明します。具体的には、C# を使用してプログラムでプレゼンテーション (.PPT および .PPTX ファイル) の組み込みプロパティを更新することに焦点を当てます。
## 前提条件
始める前に、以下のものを用意してください。
- Visual Studio: システムにインストールされています。
-  GroupDocs.Metadata for .NET: 次からダウンロードしてインストールします[ここ](https://releases.groupdocs.com/metadata/net/).
- C# の基本知識: C# プログラミング言語に精通していること。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ 1: プレゼンテーション ファイルをロードする
まず、新しいインスタンスを作成します。`Metadata`プレゼンテーション ファイルをロードして:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## ステップ 2: 組み込みプロパティを更新する
次に、プレゼンテーションの必要な組み込みプロパティを更新します。たとえば、作成者、作成日、会社、カテゴリ、キーワードなどを変更できます。その方法は次のとおりです。
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## ステップ3: 変更を保存する
プロパティを更新した後、変更をプレゼンテーション ファイルに保存し直します。
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して、プレゼンテーション ファイルの組み込みプロパティをプログラムで更新する方法について説明しました。これらの手順に従うことで、.NET アプリケーション内でメタデータを効率的に管理および変更できます。

## よくある質問
### Q: GroupDocs.Metadata for .NET とは何ですか?
A: GroupDocs.Metadata for .NET は、.NET フレームワーク用の強力なメタデータ操作ライブラリであり、開発者はさまざまなドキュメント形式でメタデータを読み取り、書き込み、編集できます。
### Q: GroupDocs.Metadata のドキュメントはどこにありますか?
 A: 詳細なドキュメントにアクセスできます[ここ](https://reference.groupdocs.com/metadata/net/).
### Q: GroupDocs.Metadata の一時ライセンスを取得するにはどうすればよいですか?
A: 臨時免許証を取得することができます[ここ](https://purchase.groupdocs.com/temporary-license/).
### Q: GroupDocs.Metadata はプレゼンテーション以外のファイル形式もサポートしていますか?
A: はい、GroupDocs.Metadata は、ドキュメント、スプレッドシート、画像、ビデオなど、幅広い形式をサポートしています。
### Q: GroupDocs.Metadata に関するサポートや質問はどこで受けられますか?
 A: サポートやディスカッションについては、[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14).