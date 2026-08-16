---
date: 2026-07-26
description: คู่มือขั้นตอนต่อขั้นตอนในการอ่านเมตาดาต้า IPTC ด้วย GroupDocs.Metadata
  สำหรับ Java พร้อมวิธีเพิ่ม XMP, ดึงข้อมูล EXIF, และเขียนเมตาดาต้า XMP
keywords:
- read iptc metadata
- how to add xmp
- how to extract exif
- write xmp metadata
- read xmp properties
lastmod: 2026-07-26
og_description: เรียนรู้วิธีอ่านเมตาดาต้า IPTC ด้วย GroupDocs.Metadata สำหรับ Java
  บทเรียนนี้ยังครอบคลุมวิธีเพิ่ม XMP, ดึงข้อมูล EXIF, และเขียนเมตาดาต้า XMP ใน Java
og_image_alt: 'Guide: read IPTC metadata using GroupDocs.Metadata Java library'
og_title: อ่านเมตาดาต้า IPTC ด้วย GroupDocs.Metadata สำหรับ Java – คู่มือฉบับเต็ม
schemas:
- author: GroupDocs
  dateModified: '2026-07-26'
  description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  headline: Read IPTC Metadata with GroupDocs.Metadata for Java
  type: TechArticle
- description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  name: Read IPTC Metadata with GroupDocs.Metadata for Java
  steps:
  - name: Initialise the Metadata object
    text: The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata.
      Provide the file path and optional load options.
  - name: Access IPTC tags
    text: Call `metadata.getIptc()` to obtain the IPTC handler, then `getAllTags()`
      returns a `Map<String, String>` containing every available IPTC field.
  - name: Process the tags
    text: Iterate over the map, log the values, or store them in your database. You
      can also filter for specific keys such as “Keywords” or “Creator”.
  - name: (Optional) Read EXIF or XMP in the same session
    text: Use `metadata.getExif()` or `metadata.getXmp()` to pull additional metadata
      without reopening the file. This is useful when you need to combine IPTC keywords
      with camera settings.
  type: HowTo
- questions:
  - answer: Yes, GroupDocs.Metadata extracts IPTC embedded in PDF/X‑4 files, returning
      the same tag map as with images.
    question: Can I read IPTC metadata from PDF files?
  - answer: “How to add XMP” focuses on embedding a new XMP package, while “write
      XMP metadata” refers to updating existing XMP properties; both use the same
      API methods.
    question: How does “how to add xmp” differ from “write xmp metadata”?
  - answer: The library extracts EXIF from RAW, JPEG, TIFF, and PSD files; for proprietary
      RAW types, ensure the latest version is installed.
    question: Is “how to extract exif” supported for RAW formats?
  - answer: Yes, `metadata.getXmp().getProperties()` returns a dictionary of all XMP
      key‑value pairs, satisfying the “read xmp properties” requirement.
    question: Does the library support reading XMP properties directly?
  - answer: Version 22.11 or newer includes full EXIF support for Java; earlier releases
      lack some newer camera tags.
    question: What version of GroupDocs.Metadata is required for “extract exif java”?
  type: FAQPage
tags:
- iptc metadata
- groupdocs metadata
- java document processing
- exif extraction
- xmp handling
title: อ่านเมตาดาต้า IPTC ด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/metadata-standards/
weight: 4
---

# อ่านข้อมูลเมตา IPTC ด้วย GroupDocs.Metadata สำหรับ Java

หากคุณต้องการ **อ่านข้อมูลเมตา IPTC** จากภาพ, PDF หรือสื่ออื่นในแอปพลิเคชัน Java คุณมาถูกที่แล้ว บทแนะนำนี้จะพาคุณผ่านการใช้ไลบรารี GroupDocs.Metadata เพื่อดึงแท็ก IPTC, แสดงวิธีเพิ่มแพ็กเกจ XMP ที่กำหนดเอง, และแม้แต่สาธิตวิธีดึงข้อมูล EXIF เมื่อจำเป็น เมื่อเสร็จแล้ว คุณจะมีวิธีการที่ชัดเจนและพร้อมใช้งานในระดับผลิตที่ทำงานได้กับไฟล์กว่า 50 รูปแบบและสามารถขยายขนาดไปยังเอกสารหลายร้อยหน้าโดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ

## คำตอบสั้น
- **IPTC metadata คืออะไร?** เป็นชุดแท็กมาตรฐานสำหรับอธิบายเนื้อหาภาพ เช่น คำสำคัญ, ผู้สร้าง, และลิขสิทธิ์.
- **ไลบรารีใดที่อ่าน IPTC ใน Java?** GroupDocs.Metadata for Java provides a simple API for reading and writing IPTC.
- **ฉันสามารถอ่าน EXIF และ XMP ได้ด้วยหรือไม่?** ใช่ – ไลบรารีเดียวกันสนับสนุนการดึง EXIF และ XMP ในการเรียกเดียว.
- **ฉันต้องการไลเซนส์หรือไม่?** ไลเซนส์ชั่วคราวใช้ได้สำหรับการประเมิน; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง.
- **เวอร์ชัน Java ที่รองรับคืออะไร?** Java 8 ถึง 17 รองรับเต็มรูปแบบ.

## การอ่าน IPTC metadata คืออะไร?
*Read IPTC metadata* หมายถึงการดึงแท็กอธิบายมาตรฐานที่ฝังอยู่ในไฟล์ภาพ แท็กเหล่านี้ทำให้การจัดการสินทรัพย์ที่ค้นหาได้, การจัดประเภทอัตโนมัติ, และการปฏิบัติตามกระบวนการเผยแพร่, ทำให้แอปพลิเคชันสามารถทำดัชนี, กรอง, และแสดงสื่อตามผู้สร้าง, คำสำคัญ, ลิขสิทธิ์, และคุณสมบัติสำคัญอื่น ๆ

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
GroupDocs.Metadata รองรับ **รูปแบบการนำเข้าและส่งออกกว่า 50**—รวมถึง JPEG, TIFF, PSD, PDF, และ EPUB—และสามารถประมวลผล **เอกสารขนาดสูงสุด 1 GB** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่ RAM ไลบรารียังให้การทำงาน **thread‑safe**, การสตรีมประสิทธิภาพสูง, และการตรวจสอบมาตรฐานเมตาดาต้าในตัว ทำให้เหมาะสำหรับสายงานสินทรัพย์ดิจิทัลระดับองค์กรที่ต้องการความน่าเชื่อถือและความเร็ว

## ข้อกำหนดเบื้องต้น
- ติดตั้ง Java 8 หรือใหม่กว่า
- ระบบการสร้าง Maven หรือ Gradle
- ไลบรารี GroupDocs.Metadata สำหรับ Java (เพิ่ม dependency ของ Maven ตามที่แสดงในเอกสารอย่างเป็นทางการ)
- ไฟล์ไลเซนส์ชั่วคราวหรือเต็ม (วางไว้ใน resources ของโปรเจกต์ของคุณ)

## วิธีการอ่าน IPTC metadata ทีละขั้นตอน
โหลดไฟล์ของคุณ, รับตัวจัดการ IPTC, และดึงแผนที่แท็ก—ทั้งหมดในกระบวนการทำงานสั้น ๆ สามขั้นตอนที่สามารถห่อหุ้มในเมธอดยูทิลิตี้เพื่อใช้ซ้ำในโค้ดของคุณ

**คำตอบโดยตรง (45 คำ):**  
สร้างอ็อบเจกต์ `Metadata` สำหรับไฟล์เป้าหมาย, เรียก `metadata.getIptc().getAllTags()` เพื่อรับแผนที่ของชื่อและค่าของแท็ก, จากนั้นวนลูปผ่านแผนที่เพื่อบันทึก, เก็บ, หรือประมวลผลข้อมูล IPTC ต่อไปตามต้องการ.

คลาส `Metadata` เป็นจุดเริ่มต้นหลักที่โหลดไฟล์และให้การเข้าถึงส่วนเมตาดาต้าต่าง ๆ

### ขั้นตอน 1: เริ่มต้นอ็อบเจกต์ Metadata
คลาส `Metadata` เป็นจุดเริ่มต้นสำหรับการดำเนินการเมตาดาต้าทั้งหมดใน GroupDocs.Metadata ให้เส้นทางไฟล์และตัวเลือกการโหลด (optional) ตามต้องการ

### ขั้นตอน 2: เข้าถึงแท็ก IPTC
เรียก `metadata.getIptc()` เพื่อรับตัวจัดการ IPTC, จากนั้น `getAllTags()` จะคืนค่า `Map<String, String>` ที่มีทุกฟิลด์ IPTC ที่มีอยู่

### ขั้นตอน 3: ประมวลผลแท็ก
วนลูปผ่านแผนที่, บันทึกค่าหรือเก็บไว้ในฐานข้อมูลของคุณ คุณยังสามารถกรองตามคีย์เฉพาะเช่น “Keywords” หรือ “Creator”

### ขั้นตอน 4: (ทางเลือก) อ่าน EXIF หรือ XMP ในเซสชันเดียวกัน
ใช้ `metadata.getExif()` หรือ `metadata.getXmp()` เพื่อดึงเมตาดาต้าเพิ่มเติมโดยไม่ต้องเปิดไฟล์ใหม่ ซึ่งมีประโยชน์เมื่อคุณต้องการรวมคำสำคัญ IPTC กับการตั้งค่ากล้อง

## วิธีการเพิ่มเมตาดาต้า XMP ไปยังไฟล์?
การฝังแพ็กเกจ XMP ที่กำหนดเองพร้อมกับข้อมูล IPTC ที่มีอยู่เป็นเรื่องง่าย: สร้าง XMP package, แนบเข้ากับอ็อบเจกต์เมตาดาต้า, และบันทึกไฟล์ การดำเนินการนี้จะคงเมตาดาต้าที่มีอยู่ไว้ขณะขยายไฟล์ด้วยคุณสมบัติใหม่ที่สอดคล้องกับมาตรฐาน

**คำตอบโดยตรง (48 คำ):**  
สร้างอินสแตนซ์ของ `XmpPackage`, เติมข้อมูลด้วยคุณสมบัติ XMP ที่กำหนดเองของคุณ, เพิ่มแพ็กเกจไปยังไฟล์ผ่าน `metadata.getXmp().addPackage(xmpPackage)`, และสุดท้ายเรียก `metadata.save()` เพื่อเขียนการเปลี่ยนแปลงกลับไปยังดิสก์, ทำให้บล็อก XMP ใหม่ถูกผสานอย่างสมบูรณ์.

คลาส `XmpPackage` แสดงถึงคอนเทนเนอร์สำหรับคุณสมบัติ XMP ที่กำหนดเองที่สามารถฝังลงในไฟล์ได้.

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
- **ส่วน IPTC หายไป:** Some PNG files lack IPTC; always check `metadata.getIptc().isPresent()` before accessing tags.
- **รูปภาพขนาดใหญ่:** สำหรับไฟล์ที่ใหญ่กว่า 200 MB, เปิดโหมดสตรีมมิ่งโดยใช้ `LoadOptions.setUseMemoryCache(true)` เพื่อหลีกเลี่ยง `OutOfMemoryError`. คลาส `LoadOptions` ให้คุณกำหนดวิธีการโหลดไฟล์, เช่น การเปิดใช้งานสตรีมมิ่งแบบแคชหน่วยความจำ.
- **ข้อผิดพลาดไลเซนส์:** ตรวจสอบให้แน่ใจว่าเส้นทางไฟล์ไลเซนส์ถูกต้อง; หากไม่, ไลบรารีจะทำงานในโหมดทดลองและอาจจำกัดจำนวนไฟล์ที่ประมวลผล.

## คำถามที่พบบ่อย

**Q: ฉันสามารถอ่าน IPTC metadata จากไฟล์ PDF ได้หรือไม่?**  
A: ใช่, GroupDocs.Metadata ดึง IPTC ที่ฝังในไฟล์ PDF/X‑4, คืนค่าแผนที่แท็กเดียวกันกับภาพ

**Q: “how to add xmp” แตกต่างจาก “write xmp metadata” อย่างไร?**  
A: “How to add XMP” มุ่งเน้นการฝังแพ็กเกจ XMP ใหม่, ส่วน “write XMP metadata” หมายถึงการอัปเดตคุณสมบัติ XMP ที่มีอยู่; ทั้งสองใช้เมธอด API เดียวกัน.

**Q: “how to extract exif” รองรับรูปแบบ RAW หรือไม่?**  
A: ไลบรารีดึง EXIF จากไฟล์ RAW, JPEG, TIFF, และ PSD; สำหรับ RAW แบบเฉพาะ, ตรวจสอบให้แน่ใจว่าติดตั้งเวอร์ชันล่าสุด.

**Q: ไลบรารีสนับสนุนการอ่านคุณสมบัติ XMP โดยตรงหรือไม่?**  
A: ใช่, `metadata.getXmp().getProperties()` คืนพจนานุกรมของคู่คีย์‑ค่า XMP ทั้งหมด, ตอบสนองความต้องการ “read xmp properties”.

**Q: เวอร์ชันของ GroupDocs.Metadata ที่ต้องการสำหรับ “extract exif java” คืออะไร?**  
A: เวอร์ชัน 22.11 หรือใหม่กว่า มีการสนับสนุน EXIF อย่างเต็มสำหรับ Java; รุ่นก่อนหน้าไม่มีแท็กกล้องใหม่บางส่วน.

---

**อัปเดตล่าสุด:** 2026-07-26  
**ทดสอบด้วย:** GroupDocs.Metadata for Java 23.5  
**ผู้เขียน:** GroupDocs  

## บทเรียนที่พร้อมใช้งาน

### [เพิ่มเมตาดาต้า XMP ที่กำหนดเองไปยังไฟล์ด้วย GroupDocs.Metadata Java&#58; คู่มือฉบับสมบูรณ์](./add-custom-xmp-metadata-groupdocs-java/)
เรียนรู้วิธีเพิ่มแพ็กเกจเมตาดาต้า XMP ที่กำหนดเองไปยังไฟล์โดยใช้ GroupDocs.Metadata สำหรับ Java. ปรับปรุงการจัดการข้อมูลไฟล์ด้วยบทแนะนำขั้นตอนต่อขั้นตอนนี้.

### [การจัดการเมตาดาต้า EXIF ใน Java&#58; คู่มือฉบับสมบูรณ์โดยใช้ GroupDocs.Metadata](./exif-metadata-management-java-groupdocs-metadata/)
เรียนรู้วิธีจัดการเมตาดาต้า EXIF อย่างมีประสิทธิภาพในแอปพลิเคชัน Java ด้วย GroupDocs.Metadata, ครอบคลุมการตั้งค่า, การอัปเดต, และการบันทึกการเปลี่ยนแปลง.

### [การดึงเมตาดาต้า Dublin Core จากไฟล์ EPUB ด้วย GroupDocs.Metadata ใน Java](./extract-dublin-core-metadata-epub-groupdocs-java/)
เรียนรู้วิธีดึงเมตาดาต้า Dublin Core จากไฟล์ EPUB ด้วยไลบรารี GroupDocs.Metadata สำหรับ Java. คู่มือนี้ครอบคลุมการตั้งค่า, การทำงาน, และการประยุกต์ใช้จริง.

### [การดึงเมตาดาต้า Dublin Core จากเอกสาร Word ด้วย Java และ GroupDocs.Metadata](./extract-dublin-core-metadata-word-docs-java/)
เรียนรู้วิธีดึงเมตาดาต้า Dublin Core จากเอกสาร Word ด้วยไลบรารี GroupDocs.Metadata ใน Java. ทำตามขั้นตอนเพื่อปรับปรุงกระบวนการจัดการเอกสารของคุณ.

### [การดึงเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata สำหรับ Java | คู่มือฉบับสมบูรณ์](./extract-exif-metadata-psd-groupdocs-java/)
เรียนรู้วิธีดึงเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata สำหรับ Java. คู่มือนี้ครอบคลุมเทคนิคพื้นฐานและขั้นสูงในการดึงข้อมูลเมตาดาต้า.

### [การดึงแท็กซอฟต์แวร์ EXIF ใน Java&#58; คู่มือฉบับสมบูรณ์โดยใช้ GroupDocs.Metadata](./master-exif-data-java-groupdocs-metadata/)
เรียนรู้การดึงแท็กซอฟต์แวร์จากข้อมูล EXIF ของภาพด้วย GroupDocs.Metadata สำหรับ Java. ปรับปรุงการจัดการสินทรัพย์ดิจิทัลและประสบการณ์ผู้ใช้ของคุณ.

### [การดึงเมตาดาต้า XMP ด้วย GroupDocs.Metadata สำหรับ Java&#58; คู่มือฉบับสมบูรณ์](./extract-xmp-metadata-groupdocs-metadata-java/)
เรียนรู้วิธีดึงและจัดการเมตาดาต้า XMP ใน Java ด้วย GroupDocs.Metadata. คู่มือนี้ครอบคลุมเมตาดาต้าเบื้องต้น, Dublin Core, และเมตาดาต้าเฉพาะของ Photoshop.

### [วิธีการดึงเมตาดาต้า Dublin Core ด้วย GroupDocs.Metadata สำหรับ Java&#58; คู่มือฉบับสมบูรณ์](./extract-dublin-core-metadata-groupdocs-java/)
เรียนรู้วิธีดึงและจัดการเมตาดาต้า Dublin Core ใน Java ด้วย GroupDocs.Metadata. คู่มือนี้ครอบคลุมการตั้งค่า, การทำงาน, และการประยุกต์ใช้จริง.

### [วิธีการดึงเมตาดาต้า EXIF จากภาพ TIFF ด้วย GroupDocs.Metadata ใน Java](./extract-exif-metadata-groupdocs-java-tiff/)
เรียนรู้วิธีดึงและจัดการเมตาดาต้า EXIF จากไฟล์ TIFF ด้วย GroupDocs.Metadata สำหรับ Java. ปรับปรุงแอปพลิเคชันการจัดการสินทรัพย์ดิจิทัลของคุณด้วยข้อมูลภาพละเอียด.

### [วิธีการดึงเมตาดาต้า IPTC จากภาพ TIFF ด้วย GroupDocs.Metadata สำหรับ Java](./extract-iptc-metadata-tiff-groupdocs-java/)
เรียนรู้วิธีดึงเมตาดาต้า IPTC จากภาพ TIFF อย่างมีประสิทธิภาพด้วย GroupDocs.Metadata สำหรับ Java. ทำให้การจัดการข้อมูลภาพของคุณเป็นระบบด้วยขั้นตอนนี้.

### [วิธีการอ่านและจัดการเมตาดาต้า DICOM ใน Java ด้วย GroupDocs.Metadata](./master-dicom-metadata-groupdocs-metadata-java/)
เรียนรู้วิธีดึงและจัดการเมตาดาต้า DICOM อย่างมีประสิทธิภาพในแอปพลิเคชัน Java ของคุณด้วยไลบรารี GroupDocs.Metadata ที่ทรงพลัง.

### [วิธีการอ่านและจัดการเมตาดาต้า EXIF ใน Java ด้วย GroupDocs.Metadata](./read-exif-metadata-groupdocs-java/)
เรียนรู้วิธีดึงและใช้เมตาดาต้า EXIF จากภาพด้วย GroupDocs.Metadata สำหรับ Java. คู่มือนี้ครอบคลุมการตั้งค่า, การอ่านแท็ก, และการประยุกต์ใช้จริง.

### [วิธีการลบเมตาดาต้า EXIF จาก JPEG ด้วย GroupDocs.Metadata สำหรับ Java&#58; คู่มือฉบับสมบูรณ์](./remove-exif-metadata-jpeg-groupdocs-java/)
เรียนรู้วิธีลบเมตาดาต้า EXIF ที่เป็นข้อมูลสำคัญจากไฟล์ JPEG ด้วย GroupDocs.Metadata สำหรับ Java. เพิ่มความเป็นส่วนตัวและปรับแต่งภาพของคุณด้วยขั้นตอนนี้.

### [วิธีการตั้งค่าเมตาดาต้า IPTC ด้วย GroupDocs.Metadata ใน Java&#58; คู่มือฉบับสมบูรณ์](./set-iptc-metadata-groupdocs-java-guide/)
เรียนรู้วิธีจัดการและตั้งค่าเมตาดาต้า IPTC ที่หายไปด้วย GroupDocs.Metadata สำหรับ Java. ปรับปรุงแอปพลิเคชันการจัดการภาพของคุณวันนี้.

### [การจัดการเมตาดาต้า Java ด้วย GroupDocs&#58; เพิ่มและดึงคีย์เวิร์ด IPTC สำหรับการจัดการสินทรัพย์ดิจิทัล](./java-metadata-groupdocs-add-retrieve-iptc-keywords/)
เรียนรู้วิธีเพิ่มและดึงคีย์เวิร์ด IPTC อย่างมีประสิทธิภาพด้วย GroupDocs.Metadata ใน Java, เพื่อการจัดการสินทรัพย์ดิจิทัลที่ดียิ่งขึ้น.

### [เชี่ยวชาญ GroupDocs.Metadata Java&#58; ดึงเมตาดาต้า IPTC จาก JPEG อย่างง่ายดาย](./reading-iptc-metadata-jpeg-groupdocs-metadata-java/)
เรียนรู้วิธีดึงเมตาดาต้า IPTC จากไฟล์ JPEG ด้วย GroupDocs.Metadata for Java. คู่มือขั้นตอนต่อขั้นตอนสำหรับการจัดการสินทรัพย์ดิจิทัลอย่างมีประสิทธิภาพ.

### [เชี่ยวชาญการจัดการเมตาดาต้า IPTC ใน Java ด้วย GroupDocs.Metadata สำหรับ Java](./java-iptc-metadata-groupdocs-metadata/)
เรียนรู้วิธีจัดการและปรับแต่งเมตาดาต้า IPTC ในแอปพลิเคชัน Java ด้วย GroupDocs.Metadata. เพิ่มประสิทธิภาพการจัดระเบียบเอกสาร, การค้นหา, และการจัดการสินทรัพย์.

### [อ่านเมตาดาต้า IPTC ใน Java โดยใช้ไลบรารี GroupDocs.Metadata](./groupdocs-metadata-java-read-iptc-datasets/)
เรียนรู้วิธีอ่านและจัดการเมตาดาต้า IPTC ภายในภาพด้วยไลบรารี GroupDocs.Metadata ใน Java. ค้นพบขั้นตอน, แนวปฏิบัติที่ดีที่สุด, และการประยุกต์ใช้จริง.

## แหล่งข้อมูลเพิ่มเติม

- [เอกสาร GroupDocs.Metadata สำหรับ Java](https://docs.groupdocs.com/metadata/java/)
- [อ้างอิง API GroupDocs.Metadata สำหรับ Java](https://reference.groupdocs.com/metadata/java/)
- [ดาวน์โหลด GroupDocs.Metadata สำหรับ Java](https://releases.groupdocs.com/metadata/java/)
- [ฟอรั่ม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata)
- [สนับสนุนฟรี](https://forum.groupdocs.com/)
- [ไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

## บทเรียนที่เกี่ยวข้อง

- [การจัดการเมตาดาต้า Java ด้วย GroupDocs: เพิ่มและดึงคีย์เวิร์ด IPTC สำหรับการจัดการสินทรัพย์ดิจิทัล](/metadata/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/)
- [การดึงเมตาดาต้า XMP ด้วย GroupDocs.Metadata สำหรับ Java: คู่มือฉบับสมบูรณ์](/metadata/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/)
- [การดึงเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata สำหรับ Java | คู่มือฉบับสมบูรณ์](/metadata/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/)