---
title: อ่านคุณสมบัติเมทาดาทาดั้งเดิมจากคลังเก็บ RAR ใน .NET
linktitle: อ่านคุณสมบัติเมทาดาทาดั้งเดิมจากคลังเก็บ RAR ใน .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีแยกคุณสมบัติเมทาดาทาจากไฟล์เก็บถาวร RAR โดยใช้ GroupDocs.Metadata สำหรับ .NET ใน C# สำรวจรายละเอียดไฟล์ได้อย่างง่ายดาย
type: docs
weight: 10
url: /th/net/archive-metadata/read-native-metadata-rar-archives/
---
## การแนะนำ
RAR (Roshal Archive) เป็นรูปแบบไฟล์ยอดนิยมที่ใช้สำหรับการบีบอัดและเก็บข้อมูล เมื่อทำงานกับไฟล์ RAR ในแอปพลิเคชัน .NET มักจำเป็นต้องอ่านและแยกคุณสมบัติข้อมูลเมตาที่ฝังอยู่ภายในไฟล์เก็บถาวรเหล่านี้ บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการใช้ GroupDocs.Metadata สำหรับ .NET เพื่อเข้าถึงและแยกคุณสมบัติเมตาดาต้าดั้งเดิมจากไฟล์เก็บถาวร RAR
## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องพัฒนาของคุณ
-  ติดตั้ง GroupDocs.Metadata สำหรับไลบรารี .NET แล้ว (โปรดดูที่[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/metadata/net/)-
- เข้าถึงไฟล์เก็บถาวร RAR เพื่อการทดสอบ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## ขั้นตอนที่ 1: โหลดไฟล์ RAR Archive
 ขั้นแรก ให้เริ่มต้น a`Metadata` วัตถุโดยการโหลดไฟล์เก็บถาวร RAR ของคุณ:
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## ขั้นตอนที่ 2: เข้าถึงรายการทั้งหมดในไฟล์ RAR
ดึงข้อมูลจำนวนรายการทั้งหมด (ไฟล์/โฟลเดอร์) ภายในไฟล์เก็บถาวร RAR:
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## ขั้นตอนที่ 3: วนซ้ำไฟล์ในไฟล์เก็บถาวร
วนซ้ำแต่ละไฟล์ภายในไฟล์ RAR เพื่อเข้าถึงคุณสมบัติข้อมูลเมตาเฉพาะ:
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีแยกคุณสมบัติข้อมูลเมตาจากไฟล์เก็บถาวร RAR โดยใช้ GroupDocs.Metadata สำหรับ .NET ไลบรารีนี้ทำให้กระบวนการเข้าถึงและใช้งานข้อมูลเมตาที่ฝังอยู่ในรูปแบบไฟล์ต่างๆ ง่ายขึ้น ช่วยเพิ่มขีดความสามารถของแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Metadata สำหรับ .NET คืออะไร
GroupDocs.Metadata สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถทำงานกับเมทาดาทาในรูปแบบไฟล์ต่างๆ รวมถึงไฟล์เก็บถาวรเช่น RAR
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Metadata สำหรับ .NET ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Metadata รองรับรูปแบบไฟล์เก็บถาวรอื่นนอกเหนือจาก RAR หรือไม่
ใช่ GroupDocs.Metadata รองรับรูปแบบไฟล์เก็บถาวรที่หลากหลาย รวมถึง ZIP, TAR และ 7z
### ฉันสามารถแก้ไขคุณสมบัติข้อมูลเมตาและอัปเดตภายในไฟล์เก็บถาวร RAR โดยใช้ไลบรารีนี้ได้หรือไม่
ใช่ GroupDocs.Metadata ช่วยให้คุณสามารถอัปเดต ลบ และเพิ่มคุณสมบัติข้อมูลเมตาลงในรูปแบบไฟล์ที่รองรับได้
### ฉันจะขอความช่วยเหลือหรือการสนับสนุนเพิ่มเติมสำหรับ GroupDocs.Metadata ได้ที่ไหน
 เยี่ยมชม[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14) สำหรับการสนับสนุนและการอภิปรายของชุมชน