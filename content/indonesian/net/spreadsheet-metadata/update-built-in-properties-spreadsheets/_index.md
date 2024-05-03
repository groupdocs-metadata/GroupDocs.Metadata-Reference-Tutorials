---
title: Perbarui Properti Bawaan di Spreadsheet menggunakan .NET
linktitle: Perbarui Properti Bawaan di Spreadsheet menggunakan .NET
second_title: GroupDocs.Metadata .NET API
description: Pelajari cara memperbarui properti metadata bawaan di file Excel menggunakan GroupDocs.Metadata untuk .NET. Ubah penulis, waktu pembuatan, perusahaan, dan lainnya dengan C#.
type: docs
weight: 14
url: /id/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara memanfaatkan GroupDocs.Metadata untuk .NET untuk memperbarui properti bawaan di file spreadsheet menggunakan C#. GroupDocs.Metadata adalah API canggih yang memungkinkan pengembang membaca, mengedit, dan menghapus properti metadata dari berbagai format file, termasuk spreadsheet. Kami akan fokus secara khusus pada modifikasi properti seperti penulis, waktu pembuatan, perusahaan, kategori, dan kata kunci dalam file Excel.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Visual Studio: Instal Visual Studio versi terbaru.
-  GroupDocs.Metadata untuk .NET: Unduh dan instal GroupDocs.Metadata untuk .NET dari[Unduh Halaman](https://releases.groupdocs.com/metadata/net/).
- Pengetahuan Dasar C#: Pemahaman bahasa pemrograman C# dan kerangka .NET.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Langkah 1: Muat File Spreadsheet
 Pertama, inisialisasi a`Metadata` objek dengan memuat file spreadsheet input:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Akses properti dokumen dalam root
}
```
## Langkah 2: Perbarui Properti Bawaan
 Akses properti dokumen bawaan melalui`SpreadsheetRootPackage` dan memodifikasinya sesuai kebutuhan:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Pastikan untuk mengganti placeholder (`YourAuthorName`, `YourCompany`, `YourCategory`dengan nilai aktual yang ingin Anda tetapkan untuk properti.
## Langkah 3: Simpan Perubahan
Setelah memperbarui properti, simpan perubahan kembali ke file spreadsheet:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Kesimpulan
Dalam tutorial ini, kami telah menunjukkan cara menggunakan GroupDocs.Metadata untuk .NET untuk memperbarui properti bawaan file spreadsheet secara terprogram. Dengan memanfaatkan API ini, pengembang dapat mengelola metadata dalam dokumen Excel secara efisien, meningkatkan pengorganisasian dan aksesibilitas data.

## FAQ
### Format file apa yang didukung GroupDocs.Metadata?
GroupDocs.Metadata mendukung berbagai format file, termasuk dokumen Microsoft Office, PDF, gambar, file audio, dan banyak lagi.
### Bisakah saya mengambil properti metadata yang ada dari file?
Ya, Anda dapat mengekstrak dan membaca properti metadata seperti penulis, tanggal pembuatan, kata kunci, dan properti khusus menggunakan GroupDocs.Metadata.
### Apakah GroupDocs.Metadata kompatibel dengan .NET Core?
Ya, GroupDocs.Metadata kompatibel dengan .NET Framework dan .NET Core.
### Apakah GroupDocs.Metadata menyediakan uji coba gratis?
 Ya, Anda dapat mengunduh uji coba gratis GroupDocs.Metadata dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Metadata?
 Untuk dukungan dan diskusi, kunjungi[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).