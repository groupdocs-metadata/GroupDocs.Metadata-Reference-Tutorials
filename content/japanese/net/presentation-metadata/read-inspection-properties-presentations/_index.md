---
title: .NET のプレゼンテーションから検査プロパティを読み取る
linktitle: .NET のプレゼンテーションから検査プロパティを読み取る
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata for .NET を使用してプレゼンテーション メタデータを抽出する方法を学びます。コメント、非表示のスライドなどにプログラムでアクセスします。
weight: 14
url: /ja/net/presentation-metadata/read-inspection-properties-presentations/
---
## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を利用してプレゼンテーションからプロパティを読み取り、検査する方法を検討します。 GroupDocs.Metadata は、開発者がプレゼンテーション、PDF、画像などのドキュメント内に埋め込まれたメタデータを操作できるようにする強力な API です。特にプレゼンテーション (PPTX ファイル) に焦点を当て、コメントや非表示のスライドなどの情報を抽出する方法を示します。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- Visual Studio: Visual Studio または .NET 開発用の互換性のある IDE をインストールします。
-  GroupDocs.Metadata for .NET: GroupDocs.Metadata for .NET ライブラリを次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/metadata/net/).
- 入力ファイル: テスト用のサンプル プレゼンテーション (PPTX ファイル) を用意します。
## 名前空間のインポート
まず、必要な名前空間をプロジェクトに含めます。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ステップ 1: プレゼンテーション メタデータのロードと検査
まずプレゼンテーション ファイルをロードし、GroupDocs.Metadata を使用してそのルート パッケージにアクセスします。
```csharp
using (Metadata metadata = new Metadata("Your Input File"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## ステップ 2: プレゼンテーションからコメントを取得する
次に、プレゼンテーション内に埋め込まれたコメントを取得して繰り返し処理します。
```csharp
if (root.InspectionPackage.Comments != null)
{
    foreach (var comment in root.InspectionPackage.Comments)
    {
        Console.WriteLine(comment.Author);
        Console.WriteLine(comment.Text);
        Console.WriteLine(comment.CreatedTime);
        Console.WriteLine(comment.SlideNumber);
    }
}
```
## ステップ 3: 非表示のスライド情報にアクセスする
ここで、プレゼンテーション内の非表示のスライドに関連する情報にアクセスして処理します。
```csharp
if (root.InspectionPackage.HiddenSlides != null)
{
    foreach (var slide in root.InspectionPackage.HiddenSlides)
    {
        Console.WriteLine(slide.Name);
        Console.WriteLine(slide.Number);
        Console.WriteLine(slide.SlideId);
    }
}
```
## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用してプレゼンテーションからメタデータを抽出する方法を説明しました。 PPTX ファイル内のコメントや非表示のスライド情報にプログラムでアクセスする方法を学習しました。 GroupDocs.Metadata はドキュメント メタデータの操作を簡素化し、開発者に強力な機能を提供します。

## よくある質問
### Q: GroupDocs.Metadata for .NET とは何ですか?
A: GroupDocs.Metadata for .NET は、開発者がさまざまなドキュメント形式のメタデータをプログラムで読み取り、編集、削除、操作できるようにする API です。
### Q: GroupDocs.Metadata の一時ライセンスを取得するにはどうすればよいですか?
 A: 一時ライセンスは以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### Q: GroupDocs.Metadata for .NET のドキュメントはどこにありますか?
 A: ドキュメントを参照してください[ここ](https://tutorials.groupdocs.com/metadata/net/).
### Q: GroupDocs.Metadata のサポートを受けるにはどうすればよいですか?
 A: サポートとディスカッションについては、GroupDocs.Metadata フォーラムをご覧ください。[ここ](https://forum.groupdocs.com/c/metadata/14).
### Q: GroupDocs.Metadata for .NET の無料試用版をダウンロードできますか?
 A: はい、無料試用版をこちらからダウンロードできます。[ここ](https://releases.groupdocs.com/).