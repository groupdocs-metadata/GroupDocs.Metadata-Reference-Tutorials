---
title: .NET kullanarak PDF'lerdeki Yerleşik Özellikleri Güncelleme
linktitle: .NET kullanarak PDF'lerdeki Yerleşik Özellikleri Güncelleme
second_title: GroupDocs.Metadata .NET API'si
description: C# ve GroupDocs.Metadata for .NET kullanarak PDF belge özelliklerini nasıl güncelleyeceğinizi öğrenin. Yazarı, başlığı, anahtar kelimeleri ve daha fazlasını programlı bir şekilde değiştirin.
weight: 15
url: /tr/net/pdf-metadata/update-built-in-properties-pdfs/
---
## giriiş
Bu öğreticide, PDF belgelerinin yerleşik özelliklerini güncellemek için GroupDocs.Metadata for .NET'in nasıl kullanılacağını öğreneceğiz. Bu kitaplık, çeşitli belge formatlarındaki meta verileri işlemek için güçlü bir araç seti sağlar. C# kullanarak bir PDF dosyasındaki yazar, başlık, oluşturulma tarihi, anahtar kelimeler, oluşturucu ve yapımcı gibi özellikleri değiştirmek için gerekli adımları izleyeceğiz.
## Önkoşullar
Başlamadan önce aşağıdakilerin mevcut olduğundan emin olun:
-  GroupDocs.Metadata for .NET Kitaplığı: Kitaplığı şu adresten indirin:[Burada](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: C# kodunu yazmak ve yürütmek için Visual Studio'yu yükleyin.
- Temel C# Anlayışı: C# programlama diline aşinalık önerilir.

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını ekleyerek başlayın:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1. Adım: Meta Veri Nesnesini Başlatın
 Bir başlatarak başlayın`Metadata`PDF dosyanızın yolunu içeren nesne:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Kodunuz buraya gelecek
}
```
## Adım 2: PDF Kök Paketine Erişin
 Daha sonra, özellikle PDF için kök paketi kullanarak şunu alın:`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## 3. Adım: Belge Özelliklerini Güncelleyin
 Şimdi PDF belgesinin istediğiniz özelliklerini`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## 4. Adım: Değişiklikleri Kaydet
Özellikleri değiştirdikten sonra değişiklikleri tekrar PDF dosyasına kaydedin:
```csharp
metadata.Save("Your Output File Path");
```
## Adım 5: Güncellenmiş Özellikleri Alın
Değişiklikleri doğrulamak için meta verileri yeniden yükleyin ve güncellenen özellikleri alın:
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

## Çözüm
Bu öğreticide, PDF belgelerinin yerleşik özelliklerini programlı olarak güncellemek için GroupDocs.Metadata for .NET'ten nasıl yararlanılacağını araştırdık. Özetlenen adımları izleyerek, C# kullanarak PDF dosyalarındaki meta verileri verimli bir şekilde yönetebilir ve değiştirebilirsiniz. Kapsamlı meta veri işleme için GroupDocs.Metadata tarafından sunulan daha fazla özellik ve yeteneği keşfetmekten çekinmeyin.

## SSS'ler
### S: .NET için GroupDocs.Metadata nedir?
C: GroupDocs.Metadata for .NET, geliştiricilerin çeşitli belge formatlarındaki meta verileri programlı olarak okumasına, düzenlemesine, kaldırmasına ve değiştirmesine olanak tanıyan bir kitaplıktır.
### S: GroupDocs.Metadata for .NET belgelerini nerede bulabilirim?
 C: Dokümantasyona erişebilirsiniz[Burada](https://tutorials.groupdocs.com/metadata/net/).
### S: GroupDocs.Metadata for .NET'i nasıl indirebilirim?
 C: GroupDocs.Metadata for .NET'i şu adresten indirebilirsiniz:[bu bağlantı](https://releases.groupdocs.com/metadata/net/).
### S: Ücretsiz deneme mevcut mu?
 C: Evet, ücretsiz deneme sürümünü alabilirsiniz[Burada](https://releases.groupdocs.com/).
### S: .NET için GroupDocs.Metadata desteğini nereden alabilirim?
 C: Destek için GroupDocs.Metadata forumunu ziyaret edin[Burada](https://forum.groupdocs.com/c/metadata/14).