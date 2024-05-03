---
title: อัปเดตแท็ก ID3V2 ในไฟล์ MP3 โดยใช้ .NET
linktitle: อัปเดตแท็ก ID3V2 ในไฟล์ MP3 โดยใช้ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตแท็ก ID3V2 ในไฟล์ MP3 โดยใช้ .NET พร้อมด้วย GroupDocs.Metadata เพื่อการจัดการไฟล์ที่มีประสิทธิภาพ
type: docs
weight: 20
url: /th/net/audio-metadata/update-id3v2-tag-mp3/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีอัปเดตแท็ก ID3V2 ในไฟล์ MP3 โดยใช้ไลบรารี GroupDocs.Metadata สำหรับ .NET GroupDocs.Metadata เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเมตาดาต้าในรูปแบบไฟล์ต่างๆ รวมถึง MP3 บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการแก้ไขแท็ก ID3V2 ทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  GroupDocs.Metadata สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/metadata/net/).

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## ขั้นตอนที่ 1: เริ่มต้นวัตถุข้อมูลเมตา
 ขั้นตอนแรกคือการเริ่มต้น`Metadata` วัตถุที่มีเส้นทางไปยังไฟล์ MP3 ของคุณ
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 2: เข้าถึงแพ็คเกจรูท MP3
 จากนั้นดึงข้อมูลแพ็คเกจรูทของไฟล์ MP3 สำหรับไฟล์เสียงนี้จะเป็นตัวอย่างของ`MP3RootPackage`.
```csharp
var root = metadata.GetRootPackage<MP3RootPackage>();
```
## ขั้นตอนที่ 3: ตรวจสอบและสร้างแท็ก ID3V2
 ตอนนี้ตรวจสอบว่าไฟล์ MP3 มีแท็ก ID3V2 อยู่แล้วหรือไม่ ถ้าไม่เช่นนั้น ให้สร้างอินสแตนซ์ใหม่ของ`ID3V2Tag`.
```csharp
if (root.ID3V2 == null)
{
    root.ID3V2 = new ID3V2Tag();
}
```
## ขั้นตอนที่ 4: อัปเดตคุณสมบัติแท็ก ID3V2
ตอนนี้คุณสามารถอัปเดตคุณสมบัติต่างๆ ของแท็ก ID3V2 ได้ เช่น อัลบั้ม, ศิลปิน, วงดนตรี, หมายเลขแทร็ก, คีย์ดนตรี, ชื่อ, วันที่ ฯลฯ
```csharp
root.ID3V2.Album = "test album";
root.ID3V2.Artist = "test artist";
root.ID3V2.Band = "test band";
root.ID3V2.TrackNumber = "1";
root.ID3V2.MusicalKey = "C#";
root.ID3V2.Title = "code sample";
root.ID3V2.Date = "2019";
```
## ขั้นตอนที่ 5: บันทึกการเปลี่ยนแปลงข้อมูลเมตา
สุดท้าย ให้บันทึกข้อมูลเมตาที่แก้ไขกลับไปยังไฟล์ MP3
```csharp
metadata.Save("YourInputFile.mp3");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการอัปเดตแท็ก ID3V2 ในไฟล์ MP3 โดยใช้ GroupDocs.Metadata สำหรับ .NET คุณได้เรียนรู้วิธีการเริ่มต้นออบเจ็กต์ข้อมูลเมตา เข้าถึงแพ็คเกจรูท MP3 แก้ไขคุณสมบัติแท็ก ID3V2 และบันทึกการเปลี่ยนแปลงกลับไปยังไฟล์

## คำถามที่พบบ่อย
### ฉันสามารถใช้ GroupDocs.Metadata ได้ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสาร GroupDocs.Metadata ได้จากที่ไหน
 เอกสารก็มีให้[ที่นี่](https://reference.groupdocs.com/metadata/net/).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Metadata ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).
### มีฟอรัมสนับสนุนสำหรับ GroupDocs.Metadata หรือไม่
 ใช่ คุณสามารถไปที่ฟอรั่มการสนับสนุนได้[ที่นี่](https://forum.groupdocs.com/c/metadata/14).
### ฉันสามารถขอรับใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้หรือไม่?
 ใช่ คุณสามารถรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).