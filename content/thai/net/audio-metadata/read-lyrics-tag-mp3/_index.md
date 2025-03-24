---
title: อ่านแท็กเนื้อเพลงจากไฟล์ MP3 ใน .NET
linktitle: อ่านแท็กเนื้อเพลงจากไฟล์ MP3 ใน .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีแยกแท็กเนื้อเพลงจากไฟล์ MP3 โดยใช้ GroupDocs.Metadata สำหรับ .NET ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเรา
weight: 13
url: /th/net/audio-metadata/read-lyrics-tag-mp3/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะเรียนรู้วิธีแยกและอ่านแท็กเนื้อเพลงจากไฟล์ MP3 โดยใช้ GroupDocs.Metadata API ใน .NET GroupDocs.Metadata เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเมตาดาต้าที่เกี่ยวข้องกับไฟล์รูปแบบต่างๆ รวมถึงไฟล์ MP3 เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถดึงข้อมูลที่เกี่ยวข้องกับเนื้อเพลงที่ฝังอยู่ในไฟล์ MP3 ได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
-  ไลบรารี GroupDocs.Metadata สำหรับ .NET คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/metadata/net/).
- เข้าถึงไฟล์ MP3 ที่มีแท็กเนื้อเพลงสำหรับการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก รวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## ขั้นตอนที่ 1: โหลดไฟล์ MP3
 เริ่มต้นด้วยการเริ่มต้น a`Metadata` วัตถุที่มีเส้นทางไฟล์ MP3 อินพุตของคุณ:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // ดึงข้อมูลแพ็คเกจรูทสำหรับรูปแบบ MP3
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## ขั้นตอนที่ 2: เข้าถึงแท็กเนื้อเพลง
ตรวจสอบว่าไฟล์ MP3 มีแท็ก Lyrics3V2 หรือไม่ และดึงข้อมูลที่เกี่ยวข้อง:
```csharp
    if (root.Lyrics3V2 != null)
    {
        //ส่งออกฟิลด์แท็กเฉพาะ
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## ขั้นตอนที่ 3: วนซ้ำช่องแท็กทั้งหมด
หรือคุณสามารถวนซ้ำฟิลด์แท็กที่มีอยู่ทั้งหมดภายใน Lyrics3V2:
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีการแยกและอ่านแท็กเนื้อเพลงจากไฟล์ MP3 โดยใช้ GroupDocs.Metadata สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถดึงข้อมูลเมตาที่เกี่ยวข้องกับเนื้อเพลงที่ฝังอยู่ในไฟล์ MP3 ของคุณได้อย่างมีประสิทธิภาพเพื่อการประมวลผลหรือแสดงในแอปพลิเคชันของคุณเพิ่มเติม

## คำถามที่พบบ่อย
### ฉันสามารถแก้ไขหรืออัปเดตแท็กเนื้อเพลงโดยใช้ GroupDocs.Metadata ได้หรือไม่
ใช่ GroupDocs.Metadata ช่วยให้คุณสามารถอัปเดตและแก้ไขข้อมูลเมตาภายในไฟล์ MP3 รวมถึงแท็กเนื้อเพลง
### GroupDocs.Metadata รองรับรูปแบบเสียงอื่นนอกเหนือจาก MP3 หรือไม่
ใช่ GroupDocs.Metadata รองรับรูปแบบเสียงและวิดีโอที่หลากหลายสำหรับการดึงและจัดการข้อมูลเมตา
### ฉันจะหาเอกสารรายละเอียดเพิ่มเติมสำหรับ GroupDocs.Metadata ได้ที่ไหน
 คุณสามารถเข้าถึงเอกสารฉบับเต็มได้[ที่นี่](https://tutorials.groupdocs.com/metadata/net/).
### GroupDocs.Metadata มีการทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถรับเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Metadata ได้อย่างไร
 หากต้องการความช่วยเหลือด้านเทคนิค คุณสามารถไปที่ฟอรัมสนับสนุน GroupDocs.Metadata[ที่นี่](https://forum.groupdocs.com/c/metadata/14).