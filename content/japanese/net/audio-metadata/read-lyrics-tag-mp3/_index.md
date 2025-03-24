---
title: .NET で MP3 ファイルから歌詞タグを読み取る
linktitle: .NET で MP3 ファイルから歌詞タグを読み取る
second_title: GroupDocs.Metadata .NET API
description: GroupDocs.Metadata for .NET を使用して MP3 ファイルから歌詞タグを抽出する方法を学びます。ステップバイステップのチュートリアルに従ってください。
weight: 13
url: /ja/net/audio-metadata/read-lyrics-tag-mp3/
---
## 導入
このチュートリアルでは、.NET の GroupDocs.Metadata API を使用して MP3 ファイルから歌詞タグを抽出して読み取る方法を学習します。 GroupDocs.Metadata は、開発者が MP3 ファイルなどのさまざまなファイル形式に関連付けられたメタデータを操作できるようにする強力なライブラリです。以下の手順に従うことで、MP3 ファイルに埋め込まれた歌詞関連情報を効率的に取得できるようになります。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- マシンに Visual Studio がインストールされています。
- C# プログラミング言語の基本的な知識。
-  .NET 用の GroupDocs.Metadata ライブラリ。ダウンロードできます[ここ](https://releases.groupdocs.com/metadata/net/).
- テスト用の歌詞タグを含む MP3 ファイルへのアクセス。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトに含めます。
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## ステップ 1: MP3 ファイルをロードする
を初期化することから始めます`Metadata`オブジェクトを入力 MP3 ファイル パスに置き換えます。
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // MP3形式のルートパッケージを取得します。
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## ステップ 2: 歌詞タグにアクセスする
MP3 ファイルに Lyrics3V2 タグが含まれているかどうかを確認し、関連情報を取得します。
```csharp
    if (root.Lyrics3V2 != null)
    {
        //特定のタグフィールドを出力する
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## ステップ 3: すべてのタグフィールドをループする
あるいは、Lyrics3V2 内の使用可能なすべてのタグ フィールドをループすることもできます。
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して MP3 ファイルから歌詞タグを抽出して読み取る方法を検討しました。これらの手順に従うことで、MP3 ファイルに埋め込まれた歌詞関連のメタデータを効果的に取得して、アプリケーションでさらに処理したり表示したりできます。

## よくある質問
### GroupDocs.Metadata を使用して歌詞タグを変更または更新できますか?
はい、GroupDocs.Metadata を使用すると、歌詞タグを含む MP3 ファイル内のメタデータを更新および変更できます。
### GroupDocs.Metadata は MP3 以外のオーディオ形式をサポートしていますか?
はい。GroupDocs.Metadata は、メタデータの抽出と操作のために幅広いオーディオおよびビデオ形式をサポートしています。
### GroupDocs.Metadata の詳細なドキュメントはどこで見つけられますか?
完全なドキュメントにアクセスできます[ここ](https://tutorials.groupdocs.com/metadata/net/).
### GroupDocs.Metadata に利用できる無料トライアルはありますか?
はい、無料試用版を入手できます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Metadata のテクニカル サポートを受けるにはどうすればよいですか?
技術的なサポートが必要な場合は、GroupDocs.Metadata サポート フォーラムにアクセスしてください。[ここ](https://forum.groupdocs.com/c/metadata/14).