---
title: Perbarui Properti Bawaan dalam Presentasi menggunakan .NET
linktitle: Perbarui Properti Bawaan dalam Presentasi menggunakan .NET
second_title: GroupDocs.Metadata .NET API
description: Pelajari cara memperbarui properti bawaan dalam presentasi menggunakan .NET dengan GroupDocs.Metadata, pustaka manipulasi metadata serbaguna.
weight: 15
url: /id/net/presentation-metadata/update-built-in-properties-presentations/
type: docs
---
# Perbarui Properti Bawaan dalam Presentasi menggunakan .NET

## Perkenalan
Dalam tutorial ini, kita akan mempelajari kemampuan hebat GroupDocs.Metadata untuk .NET, pustaka komprehensif yang dirancang untuk memanipulasi metadata dalam dokumen menggunakan kerangka .NET. Secara khusus, kami akan fokus pada memperbarui properti bawaan dalam presentasi (file .PPT dan .PPTX) secara terprogram menggunakan C#.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio: Diinstal di sistem Anda.
-  GroupDocs.Metadata untuk .NET: Diunduh dan diinstal dari[Di Sini](https://releases.groupdocs.com/metadata/net/).
- Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C#.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Langkah 1: Muat File Presentasi
 Pertama, buat instance baru`Metadata` dengan memuat file presentasi Anda:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Langkah 2: Perbarui Properti Bawaan
Sekarang, perbarui properti bawaan presentasi yang diinginkan. Misalnya, Anda dapat mengubah penulis, tanggal pembuatan, perusahaan, kategori, kata kunci, dll. Berikut cara melakukannya:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Langkah 3: Simpan Perubahan
Setelah memperbarui properti, simpan perubahan kembali ke file presentasi:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menggunakan GroupDocs.Metadata untuk .NET guna memperbarui properti bawaan dalam file presentasi secara terprogram. Dengan mengikuti langkah-langkah ini, Anda dapat mengelola dan mengubah metadata secara efisien dalam aplikasi .NET Anda.

## FAQ
### T: Apa itu GroupDocs.Metadata untuk .NET?
J: GroupDocs.Metadata for .NET adalah pustaka manipulasi metadata yang kuat untuk kerangka .NET, memungkinkan pengembang membaca, menulis, dan mengedit metadata dalam berbagai format dokumen.
### T: Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Metadata?
 J: Anda dapat mengakses dokumentasi detailnya[Di Sini](https://tutorials.groupdocs.com/metadata/net/).
### T: Bagaimana cara mendapatkan lisensi sementara untuk GroupDocs.Metadata?
 J: Anda dapat memperoleh lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### T: Apakah GroupDocs.Metadata mendukung format file lain selain presentasi?
J: Ya, GroupDocs.Metadata mendukung berbagai format termasuk dokumen, spreadsheet, gambar, video, dan banyak lagi.
### T: Di mana saya bisa mendapatkan dukungan atau mengajukan pertanyaan tentang GroupDocs.Metadata?
 J: Untuk dukungan dan diskusi, kunjungi[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).