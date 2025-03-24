---
title: .NET kullanarak MP3 Dosyalarındaki Şarkı Sözü Etiketini Güncelleyin
linktitle: .NET kullanarak MP3 Dosyalarındaki Şarkı Sözü Etiketini Güncelleyin
second_title: GroupDocs.Metadata .NET API'si
description: Şarkı sözleri, sanatçı ve albüm ayrıntılarını içeren MP3 dosyası meta verilerini GroupDocs.Metadata for .NET'i kullanarak programlı olarak nasıl güncelleyeceğinizi öğrenin.
weight: 21
url: /tr/net/audio-metadata/update-lyrics-tag-mp3/
---
## giriiş
Bu öğreticide, MP3 dosyalarındaki şarkı sözü etiketini program aracılığıyla güncellemek için GroupDocs.Metadata for .NET kitaplığının nasıl kullanılacağını göstereceğiz. Bu süreç, özellikle şarkı sözü bilgilerini hedefleyerek MP3 dosyalarının meta verilerine erişmeyi ve bunları değiştirmeyi içerir.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Temel C# programlama bilgisi.
- Makinenizde Visual Studio yüklü.
-  .NET kitaplığı için GroupDocs.Metadata yüklü (bkz.[İndirme: {link](https://releases.groupdocs.com/metadata/net/)).
- Test amaçlı bir MP3 dosyası.

## Ad Alanlarını İçe Aktar
Gerekli ad alanlarını C# projenize aktararak başlayın:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## Adım 1: MP3 Dosyasını Yükleyin
 İlk önce MP3 dosyasını bir`Metadata` GroupDocs.Metadata'yı kullanan nesne:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Lyrics3V2 etiketine erişin
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## Adım 2: Şarkı Sözü Bilgilerini Güncelleyin
Ardından şarkı sözü bilgilerini sanatçı, albüm ve parça gibi diğer ilgili ayrıntılarla birlikte güncelleyin:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## 3. Adım: Özel Alanlar Ekleyin (İsteğe Bağlı)
İsteğe bağlı olarak etikete özel alanlar ekleyebilirsiniz:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## 4. Adım: Değişiklikleri Kaydedin
Son olarak, değiştirilen meta verileri tekrar MP3 dosyasına kaydedin:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## Çözüm
Bu eğitimde, GroupDocs.Metadata for .NET'i kullanarak MP3 dosyalarındaki şarkı sözü etiketinin nasıl güncelleneceğini araştırdık. Belirtilen adımları izleyerek, MP3 dosyalarındaki meta verileri programlı bir şekilde verimli bir şekilde yönetebilir ve değiştirebilirsiniz.

## SSS'ler
### GroupDocs.Metadata for .NET'i kullanarak şarkı sözlerinin yanı sıra diğer meta verileri de güncelleyebilir miyim?
Evet, GroupDocs.Metadata for .NET, farklı dosya formatlarındaki çeşitli meta verilerle çalışmanıza olanak tanır.
### GroupDocs.Metadata for .NET, .NET Core ile uyumlu mu?
Evet, kitaplık hem .NET Framework'ü hem de .NET Core'u destekler.
### GroupDocs.Metadata for .NET ticari kullanım için lisans gerektiriyor mu?
 Evet, adresinden lisans alabilirsiniz.[GrupDoc'ları](https://purchase.groupdocs.com/buy) ticari kullanım için.
### GroupDocs.Metadata for .NET ile ilgili nasıl destek alabilirim veya soru sorabilirim?
 Ziyaret edebilirsiniz[GroupDocs.Meta veri forumu](https://forum.groupdocs.com/c/metadata/14) Destek ve tartışmalar için.
### GroupDocs.Metadata for .NET'i ücretsiz deneyebilir miyim?
 Evet, alabilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) özelliklerini keşfetmek için.