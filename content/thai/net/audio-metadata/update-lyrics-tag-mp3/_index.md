---
title: อัปเดตแท็กเนื้อเพลงในไฟล์ MP3 โดยใช้ .NET
linktitle: อัปเดตแท็กเนื้อเพลงในไฟล์ MP3 โดยใช้ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตข้อมูลเมตาของไฟล์ MP3 รวมถึงเนื้อเพลง ศิลปิน และรายละเอียดอัลบั้มโดยทางโปรแกรมโดยใช้ GroupDocs.Metadata สำหรับ .NET
weight: 21
url: /th/net/audio-metadata/update-lyrics-tag-mp3/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสาธิตวิธีใช้ไลบรารี GroupDocs.Metadata สำหรับ .NET เพื่ออัปเดตแท็กเนื้อเพลงในไฟล์ MP3 โดยทางโปรแกรม กระบวนการนี้เกี่ยวข้องกับการเข้าถึงและแก้ไขข้อมูลเมตาของไฟล์ MP3 โดยเฉพาะการกำหนดเป้าหมายข้อมูลเนื้อเพลง
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  ติดตั้ง GroupDocs.Metadata สำหรับไลบรารี .NET แล้ว (โปรดดูที่[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/metadata/net/)-
- ไฟล์ MP3 เพื่อการทดสอบ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## ขั้นตอนที่ 1: โหลดไฟล์ MP3
 ขั้นแรกให้โหลดไฟล์ MP3 ลงในไฟล์`Metadata` วัตถุที่ใช้ GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // เข้าถึงแท็ก Lyrics3V2
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## ขั้นตอนที่ 2: อัปเดตข้อมูลเนื้อเพลง
จากนั้น อัปเดตข้อมูลเนื้อเพลงพร้อมกับรายละเอียดอื่นๆ ที่เกี่ยวข้อง เช่น ศิลปิน อัลบั้ม และแทร็ก:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## ขั้นตอนที่ 3: เพิ่มฟิลด์ที่กำหนดเอง (ไม่บังคับ)
คุณสามารถเลือกเพิ่มฟิลด์ที่กำหนดเองให้กับแท็กได้:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
สุดท้าย ให้บันทึกข้อมูลเมตาที่แก้ไขแล้วกลับไปยังไฟล์ MP3:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีอัปเดตแท็กเนื้อเพลงในไฟล์ MP3 โดยใช้ GroupDocs.Metadata สำหรับ .NET เมื่อทำตามขั้นตอนที่ระบุไว้ คุณจะจัดการและแก้ไขข้อมูลเมตาภายในไฟล์ MP3 โดยทางโปรแกรมได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ฉันสามารถอัปเดตข้อมูลเมตาอื่น ๆ นอกเหนือจากเนื้อเพลงโดยใช้ GroupDocs.Metadata สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Metadata สำหรับ .NET ช่วยให้คุณสามารถทำงานกับเมตาดาต้าประเภทต่างๆ ในรูปแบบไฟล์ที่แตกต่างกันได้
### GroupDocs.Metadata สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ ไลบรารีรองรับทั้ง .NET Framework และ .NET Core
### GroupDocs.Metadata สำหรับ .NET จำเป็นต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
 ใช่ คุณสามารถขอรับใบอนุญาตได้จาก[GroupDocs](https://purchase.groupdocs.com/buy) เพื่อการใช้งานเชิงพาณิชย์
### ฉันจะรับการสนับสนุนหรือถามคำถามที่เกี่ยวข้องกับ GroupDocs.Metadata สำหรับ .NET ได้อย่างไร
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14) สำหรับการสนับสนุนและการอภิปราย
### ฉันสามารถทดลองใช้ GroupDocs.Metadata สำหรับ .NET ได้ฟรีหรือไม่
 ใช่ คุณจะได้รับ[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อสำรวจคุณลักษณะต่างๆ