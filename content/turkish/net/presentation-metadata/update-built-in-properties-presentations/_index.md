---
title: .NET kullanarak Sunumlardaki Yerleşik Özellikleri Güncelleme
linktitle: .NET kullanarak Sunumlardaki Yerleşik Özellikleri Güncelleme
second_title: GroupDocs.Metadata .NET API'si
description: Çok yönlü bir meta veri işleme kitaplığı olan GroupDocs.Metadata ile .NET kullanarak sunumlardaki yerleşik özellikleri nasıl güncelleyeceğinizi öğrenin.
weight: 15
url: /tr/net/presentation-metadata/update-built-in-properties-presentations/
---
## giriiş
Bu öğreticide, .NET çerçevesini kullanarak belgeler içindeki meta verileri işlemek için tasarlanmış kapsamlı bir kitaplık olan GroupDocs.Metadata for .NET'in güçlü yeteneklerini inceleyeceğiz. Özellikle, sunumlardaki yerleşik özellikleri (.PPT ve .PPTX dosyaları) C# kullanarak programlı olarak güncellemeye odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Visual Studio: Sisteminizde kuruludur.
-  GroupDocs.Metadata for .NET: şuradan indirildi ve yüklendi:[Burada](https://releases.groupdocs.com/metadata/net/).
- Temel C# Bilgisi: C# programlama diline aşinalık.

## Ad Alanlarını İçe Aktar
Gerekli ad alanlarını C# projenize aktararak başlayın:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Adım 1: Sunum Dosyasını Yükleyin
 İlk önce yeni bir örnek oluşturun`Metadata` sunum dosyanızı yükleyerek:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## 2. Adım: Yerleşik Özellikleri Güncelleyin
Şimdi sunumun istediğiniz yerleşik özelliklerini güncelleyin. Örneğin yazarı, oluşturulma tarihini, şirketi, kategoriyi, anahtar kelimeleri vb. değiştirebilirsiniz. Bunu şu şekilde yapabilirsiniz:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## 3. Adım: Değişiklikleri Kaydet
Özellikleri güncelledikten sonra değişiklikleri sunum dosyasına geri kaydedin:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Çözüm
Bu öğreticide, sunum dosyalarındaki yerleşik özellikleri program aracılığıyla güncelleştirmek için GroupDocs.Metadata for .NET'in nasıl kullanılacağını araştırdık. Bu adımları izleyerek .NET uygulamalarınızdaki meta verileri verimli bir şekilde yönetebilir ve değiştirebilirsiniz.

## SSS'ler
### S: .NET için GroupDocs.Metadata nedir?
C: GroupDocs.Metadata for .NET, geliştiricilerin çeşitli belge formatlarındaki meta verileri okumasına, yazmasına ve düzenlemesine olanak tanıyan, .NET çerçevesine yönelik güçlü bir meta veri işleme kitaplığıdır.
### S: GroupDocs.Metadata belgelerini nerede bulabilirim?
 C: Detaylı dokümantasyona ulaşabilirsiniz.[Burada](https://tutorials.groupdocs.com/metadata/net/).
### S: GroupDocs.Metadata için nasıl geçici lisans alabilirim?
 C: Geçici bir lisans alabilirsiniz[Burada](https://purchase.groupdocs.com/temporary-license/).
### S: GroupDocs.Metadata sunumların yanı sıra diğer dosya formatlarını da destekliyor mu?
C: Evet, GroupDocs.Metadata belgeler, e-tablolar, resimler, videolar ve daha fazlasını içeren çok çeşitli formatları destekler.
### S: GroupDocs.Metadata hakkında nereden destek alabilirim veya soru sorabilirim?
 C: Destek ve tartışmalar için şu adresi ziyaret edin:[GroupDocs.Meta veri forumu](https://forum.groupdocs.com/c/metadata/14).