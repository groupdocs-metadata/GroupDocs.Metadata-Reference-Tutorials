---
title: กำลังโหลดข้อมูลเมตาจากสตรีมใน .NET Tutorial
linktitle: กำลังโหลดข้อมูลเมตาจากสตรีมใน .NET Tutorial
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีจัดการข้อมูลเมตาของไฟล์ใน .NET ด้วย GroupDocs.Metadata คำแนะนำทีละขั้นตอนสำหรับการโหลด แก้ไข และลบข้อมูลเมตาออกจากสตรีม
weight: 11
url: /th/net/metadata-loading/load-metadata-stream/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Metadata สำหรับ .NET เพื่อจัดการข้อมูลเมตาภายในแอปพลิเคชัน .NET ของคุณอย่างมีประสิทธิภาพ ข้อมูลเมตา เช่น คุณสมบัติเอกสาร สามารถให้ข้อมูลที่เป็นประโยชน์เกี่ยวกับไฟล์ รวมถึงรายละเอียด เช่น ผู้เขียน วันที่สร้าง และคำสำคัญ GroupDocs.Metadata ลดความซับซ้อนของกระบวนการอ่าน แก้ไข และลบข้อมูลเมตาจากไฟล์รูปแบบต่างๆ ในสภาพแวดล้อม .NET คู่มือนี้จะเน้นที่การโหลดข้อมูลเมตาจากสตรีม ซึ่งสาธิตขั้นตอนทีละขั้นตอนโดยใช้ตัวอย่างที่เป็นประโยชน์
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# และกรอบงาน .NET
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  ดาวน์โหลดและตั้งค่า GroupDocs.Metadata สำหรับไลบรารี .NET แล้ว (ดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/metadata/net/-)
- เข้าถึงไฟล์ตัวอย่างพร้อมข้อมูลเมตาสำหรับการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก ใส่เนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using System.IO;
```
## ขั้นตอนที่ 1: เริ่มต้นข้อมูลเมตาจากสตรีม
เริ่มต้นด้วยการโหลดข้อมูลเมตาจากสตรีมไฟล์โดยใช้ GroupDocs.Metadata สำหรับ .NET ข้อมูลโค้ดต่อไปนี้สาธิตวิธีการเปิดสตรีมไปยังไฟล์และเริ่มต้นออบเจ็กต์ Metadata:

```csharp
using (Stream stream = File.Open("Your Input File", FileMode.Open, FileAccess.ReadWrite))
using (Metadata metadata = new Metadata(stream))
{
    // แยก แก้ไข หรือลบข้อมูลเมตาที่นี่
}
```
## ขั้นตอนที่ 2: การเข้าถึงคุณสมบัติข้อมูลเมตา
เมื่อเตรียมใช้งานออบเจ็กต์ Metadata แล้ว คุณจะสามารถเข้าถึงคุณสมบัติและข้อมูลเมตาต่างๆ ของไฟล์ได้ ตัวอย่างเช่น หากต้องการดึงข้อมูลผู้เขียนเอกสาร:

```csharp
var root = metadata.GetRootPackage<MetadataPackage>();
var authorProperty = root.DocumentProperties.Author;
Console.WriteLine($"Author: {authorProperty}");
```
## ขั้นตอนที่ 3: การแก้ไขข้อมูลเมตา
คุณสามารถแก้ไขคุณสมบัติข้อมูลเมตาที่มีอยู่หรือเพิ่มคุณสมบัติใหม่ลงในไฟล์ได้ มาอัพเดตชื่อผู้เขียนกัน:

```csharp
root.DocumentProperties.Author = "John Doe";
metadata.Save("Output File");
```
## ขั้นตอนที่ 4: การลบข้อมูลเมตา
หากต้องการลบคุณสมบัติข้อมูลเมตาเฉพาะออกจากไฟล์ ให้ใช้วิธีการลบ:

```csharp
root.DocumentProperties.RemoveProperty(StandardProperty.Author);
metadata.Save("Output File");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการโหลดข้อมูลเมตาจากสตรีมโดยใช้ GroupDocs.Metadata สำหรับ .NET คุณได้เรียนรู้วิธีการเริ่มต้นออบเจ็กต์ Metadata เข้าถึงและแก้ไขคุณสมบัติ Metadata และลบ Metadata ที่ไม่ต้องการออกจากไฟล์ ใช้เทคนิคเหล่านี้เพื่อจัดการข้อมูลเมตาภายในแอปพลิเคชัน .NET ของคุณอย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ถาม: ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Metadata ได้อย่างไร
 ตอบ: คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ถาม: ฉันจะหาเอกสารที่ครอบคลุมสำหรับ GroupDocs.Metadata ได้ที่ไหน
 ตอบ: สำรวจเอกสารโดยละเอียด[ที่นี่](https://tutorials.groupdocs.com/metadata/net/).
### ถาม: GroupDocs.Metadata มีการทดลองใช้ฟรีหรือไม่
 ตอบ: ได้ คุณสามารถทดลองใช้งานฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ถาม: ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Metadata ได้อย่างไร
 ตอบ: สำหรับการสนับสนุนและการสนทนา โปรดไปที่[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).
### ถาม: ฉันสามารถซื้อใบอนุญาตสำหรับ GroupDocs.Metadata ได้หรือไม่
 ตอบ: ได้ คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).