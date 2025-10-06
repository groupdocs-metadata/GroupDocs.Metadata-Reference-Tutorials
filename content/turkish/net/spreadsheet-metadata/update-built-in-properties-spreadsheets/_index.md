---
title: .NET kullanarak Elektronik Tablolardaki Yerleşik Özellikleri Güncelleme
linktitle: .NET kullanarak Elektronik Tablolardaki Yerleşik Özellikleri Güncelleme
second_title: GroupDocs.Metadata .NET API'si
description: GroupDocs.Metadata for .NET'i kullanarak Excel dosyalarındaki yerleşik meta veri özelliklerini nasıl güncelleştireceğinizi öğrenin. Yazarı, oluşturma zamanını, şirketi ve daha fazlasını C# ile değiştirin.
weight: 14
url: /tr/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
type: docs
---
# .NET kullanarak Elektronik Tablolardaki Yerleşik Özellikleri Güncelleme

## giriiş
Bu öğreticide, C# kullanarak elektronik tablo dosyalarındaki yerleşik özellikleri güncellemek için GroupDocs.Metadata for .NET'in nasıl kullanılacağını keşfedeceğiz. GroupDocs.Metadata, geliştiricilerin elektronik tablolar da dahil olmak üzere çeşitli dosya formatlarındaki meta veri özelliklerini okumasına, düzenlemesine ve kaldırmasına olanak tanıyan güçlü bir API'dir. Özellikle Excel dosyalarındaki yazar, oluşturulma zamanı, şirket, kategori ve anahtar kelimeler gibi özellikleri değiştirmeye odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Visual Studio: Visual Studio'nun en son sürümünü yükleyin.
-  GroupDocs.Metadata for .NET: GroupDocs.Metadata for .NET'i şu adresten indirip yükleyin:[indirme sayfası](https://releases.groupdocs.com/metadata/net/).
- Temel C# Bilgisi: C# programlama dili ve .NET çerçevesinin anlaşılması.

## Ad Alanlarını İçe Aktar
C# projenize gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Adım 1: Elektronik Tablo Dosyasını Yükleyin
 İlk olarak, bir başlat`Metadata` giriş elektronik tablosu dosyasını yükleyerek nesne:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Kök içindeki belge özelliklerine erişme
}
```
## 2. Adım: Yerleşik Özellikleri Güncelleyin
 Yerleşik belge özelliklerine şu adresten erişin:`SpreadsheetRootPackage` ve bunları gerektiği gibi değiştirin:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Yer tutucuları değiştirdiğinizden emin olun (`YourAuthorName`, `YourCompany`, `YourCategory`özellikler için ayarlamak istediğiniz gerçek değerlerle.
## 3. Adım: Değişiklikleri Kaydet
Özellikleri güncelledikten sonra değişiklikleri elektronik tablo dosyasına geri kaydedin:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Çözüm
Bu öğreticide, elektronik tablo dosyalarının yerleşik özelliklerini program aracılığıyla güncelleştirmek için GroupDocs.Metadata for .NET'in nasıl kullanılacağını gösterdik. Geliştiriciler bu API'den yararlanarak Excel belgelerindeki meta verileri verimli bir şekilde yönetebilir, böylece veri organizasyonunu ve erişilebilirliğini geliştirebilirler.

## SSS'ler
### GroupDocs.Metadata hangi dosya formatlarını destekler?
GroupDocs.Metadata, Microsoft Office belgeleri, PDF'ler, resimler, ses dosyaları ve daha fazlasını içeren çok çeşitli dosya formatlarını destekler.
### Dosyalardan mevcut meta veri özelliklerini alabilir miyim?
Evet, GroupDocs.Metadata'yı kullanarak yazar, oluşturulma tarihi, anahtar sözcükler ve özel özellikler gibi meta veri özelliklerini çıkarabilir ve okuyabilirsiniz.
### GroupDocs.Metadata .NET Core ile uyumlu mu?
Evet, GroupDocs.Metadata hem .NET Framework hem de .NET Core ile uyumludur.
### GroupDocs.Metadata ücretsiz deneme sunuyor mu?
 Evet, GroupDocs.Metadata'nın ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Metadata desteğini nerede bulabilirim?
 Destek ve tartışmalar için şu adresi ziyaret edin:[GroupDocs.Meta veri forumu](https://forum.groupdocs.com/c/metadata/14).