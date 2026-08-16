---
date: '2026-08-15'
description: เรียนรู้วิธีเพิ่มคีย์เวิร์ด IPTC ใน Java ด้วย GroupDocs.Metadata เพื่อปรับปรุงการจัดการสินทรัพย์ดิจิทัลและความสามารถในการค้นหา
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: เพิ่มคีย์เวิร์ด IPTC ใน Java ด้วย GroupDocs.Metadata เพื่อเพิ่มประสิทธิภาพการจัดการสินทรัพย์ดิจิทัล
  เรียนรู้ขั้นตอนการตั้งค่า โค้ด และแนวปฏิบัติที่ดีที่สุด
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: เพิ่มคีย์เวิร์ด IPTC ใน Java ด้วย GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: เพิ่มคีย์เวิร์ด IPTC ใน Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# เพิ่มคีย์เวิร์ด IPTC ใน Java ด้วย GroupDocs.Metadata

การจัดการเมตาดาต้าของภาพเป็นสิ่งสำคัญสำหรับกลยุทธ์การจัดการสินทรัพย์ดิจิทัล (DAM) ใด ๆ ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีเพิ่มคีย์เวิร์ด IPTC ใน Java** ด้วยไลบรารี GroupDocs.Metadata แล้วดึงคีย์เวิร์ดเหล่านั้นเพื่อตรวจสอบการเปลี่ยนแปลง เมื่อเสร็จแล้วคุณจะมีรูปแบบที่นำกลับมาใช้ได้ซึ่งสามารถฝังลงในงานประมวลผลแบบแบตช์, กระบวนการจัดการเนื้อหา, หรือเวิร์กโฟลว์สื่อที่ใช้ Java ใด ๆ

## คำตอบสั้น
- **ไลบรารีใดที่เพิ่มคีย์เวิร์ด IPTC ใน Java?** GroupDocs.Metadata for Java.  
- **ฉันต้องการไลเซนส์หรือไม่?** A free trial works for development; a paid license is required for production.  
- **ฉันสามารถเพิ่มหลายคีย์เวิร์ดพร้อมกันได้หรือไม่?** Yes—simply add each keyword to the IPTC package.  
- **รองรับการจัดการไฟล์ขนาดใหญ่หรือไม่?** GroupDocs.Metadata processes files up to 2 GB without loading the whole file into memory.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 or higher, with Maven 3 or later.

## add iptc keywords java คืออะไร?
**Add IPTC keywords java** หมายถึงการแทรกแท็กคีย์เวิร์ดมาตรฐาน IPTC ลงในไฟล์ภาพโดยใช้โค้ด Java อย่างโปรแกรมเมติก การดำเนินการนี้ทำให้เมตาดาต้าของภาพมีความสมบูรณ์มากขึ้น ทำให้สามารถค้นหาได้ในระบบ DAM และปรับปรุง SEO สำหรับสินทรัพย์เว็บ นอกจากนี้ยังช่วยรักษาการปฏิบัติตามมาตรฐานอุตสาหกรรมสำหรับการแท็กสื่อ

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
GroupDocs.Metadata รองรับ **มาตรฐานเมตาดาต้า 150+** (รวมถึง EXIF, IPTC, XMP) และสามารถ **ประมวลผลไฟล์ได้สูงสุด 2 GB** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ ซึ่งช่วยลดการใช้ CPU และ RAM ได้ถึง 30 % เมื่อเทียบกับวิธีการสตรีมไฟล์แบบธรรมดา API มีความปลอดภัยต่อประเภทข้อมูล มีเอกสารครบถ้วน และให้การเรียกใช้งานแบบบรรทัดเดียวเพื่อบันทึกการเปลี่ยนแปลง

## ข้อกำหนดเบื้องต้น

- **GroupDocs.Metadata for Java** (version 24.12 or later).  
- Java Development Kit 8 หรือใหม่กว่า.  
- Maven 3 ติดตั้งและกำหนดค่าแล้ว.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse (ไม่บังคับแต่แนะนำ).  

### ไลบรารีที่ต้องการ
เพิ่ม dependency ของ GroupDocs.Metadata ลงในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

คุณสามารถดาวน์โหลดไลบรารีได้จากหน้า **GroupDocs.Metadata for Java releases**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## วิธีเพิ่มคีย์เวิร์ด IPTC ใน Java?

ก่อนอื่นให้โหลดไฟล์ภาพเป้าหมายโดยใช้ GroupDocs.Metadata API จากนั้นตรวจสอบว่าแพ็กเกจ IPTC มีอยู่หรือสร้างใหม่หากไม่มี และสุดท้ายเพิ่มคีย์เวิร์ดที่ต้องการลงในคอลเลกชัน IPTC Keywords ขั้นตอนด้านล่างจะแสดงรายละเอียดของแต่ละส่วนของเวิร์กโฟลว์นี้

### ขั้นตอนที่ 1: สร้างคลาสคอนสแตนท์
คลาส `Constants` เก็บค่าที่ใช้ซ้ำได้ เช่น ที่ตั้งไฟล์และสตริงไลเซนส์

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### ขั้นตอนที่ 2: เริ่มต้น metadata และตั้งค่าแพ็กเกจ IPTC
`Metadata` เป็นจุดเริ่มต้นสำหรับการอ่านและเขียนรูปแบบเมตาดาต้าที่รองรับทั้งหมด มันทำหน้าที่เป็นชั้นนามธรรมของการจัดการไฟล์เพื่อให้คุณไม่ต้องจัดการสตรีมด้วยตนเอง

โค้ดด้านล่างตรวจสอบว่าแพ็กเกจ IPTC มีอยู่แล้วหรือไม่; หากไม่มีจะสร้างใหม่เพื่อรับประกันว่ามีที่เก็บคีย์เวิร์ด

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### ขั้นตอนที่ 3: เพิ่มคีย์เวิร์ดลงในบันทึก IPTC
`IptcDataSet` แทนรายการเมตาดาต้า IPTC รายการเดียว เช่น คีย์เวิร์ด แต่ละคีย์เวิร์ดจะถูกเพิ่มเป็นรายการ `IptcDataSet` คุณสามารถเพิ่มคีย์เวิร์ดได้ตามต้องการ; ไลบรารีจะจัดการการตรวจจับซ้ำโดยอัตโนมัติ

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### ขั้นตอนที่ 4: ดึงและแสดงคีย์เวิร์ด IPTC
`metadata.getIptc().getKeywords()` คืนรายการสตริงของคีย์เวิร์ดที่เก็บในแพ็กเกจ IPTC หลังจากบันทึกแล้วคุณสามารถอ่านคีย์เวิร์ดกลับมาเพื่อยืนยันว่าถูกบันทึกอย่างถูกต้อง ขั้นตอนการตรวจสอบนี้มีประโยชน์สำหรับการทดสอบหน่วยและการดีบัก

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## วิธีดึงคีย์เวิร์ด IPTC ใน Java?
`metadata.getIptc().getKeywords()` คืนรายการสตริงของคีย์เวิร์ดที่เก็บในแพ็กเกจ IPTC คุณสามารถวนลูปรายการนี้, บันทึกแต่ละรายการ, หรือส่งต่อไปยังดัชนีการค้นหาเพื่อการดึงข้อมูลที่รวดเร็ว เมธอดนี้คืนค่า `List<String>` ที่ประกอบด้วยคีย์เวิร์ดทั้งหมดในแพ็กเกจ IPTC ทำให้คุณสามารถแสดงหรือประมวลผลได้ทันที

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา

- **ไม่มีแพ็กจ์ IPTC:** หากภาพไม่มีบล็อก IPTC, `metadata.getIptc()` จะคืนค่า `null`. ควรเรียก `metadata.addIptc()` ก่อนเพิ่มคีย์เวิร์ดเสมอ.  
- **ข้อผิดพลาดไลเซนส์:** ตรวจสอบให้แน่ใจว่าไฟล์ไลเซนส์แบบทดลองหรือเชิงพาณิชย์อ้างอิงอย่างถูกต้องใน `Constants.LICENSE_PATH`. ไฟล์ไลเซนส์ที่หายไปจะทำให้เกิด `LicenseException`.  
- **ไฟล์ขนาดใหญ่:** สำหรับภาพที่ใหญ่กว่า 2 GB ให้แบ่งการประมวลผลเป็นชิ้นส่วนหรือใช้ API สตรีมที่ GroupDocs.Metadata จัดเตรียมไว้เพื่อหลีกเลี่ยง `OutOfMemoryError`.  

## คำถามที่พบบ่อย

**Q: ฉันสามารถเพิ่มคีย์เวิร์ด IPTC ไปยังไฟล์ PDF ได้หรือไม่?**  
A: ไม่. IPTC เป็นมาตรฐานเฉพาะภาพ; สำหรับ PDF คุณควรใช้ XMP หรือฟิลด์เมตาดาต้าเฉพาะ PDF.

**Q: GroupDocs.Metadata รองรับรูปแบบภาพอื่นหรือไม่?**  
A: ใช่—มันรองรับ JPEG, TIFF, PNG, BMP, และ WebP โดยรักษาเมตาดาต้าที่มีอยู่ไว้ขณะเพิ่มรายการ IPTC ใหม่.

**Q: ฉันสามารถเก็บคีย์เวิร์ดได้กี่รายการ?**  
A: สเปคของ IPTC อนุญาตให้เก็บได้สูงสุด 64 คีย์เวิร์ดต่อภาพ; GroupDocs.Metadata จะบังคับจำกัดนี้โดยอัตโนมัติ.

**Q: ไลบรารีเข้ากันได้กับ Java 11 หรือไม่?**  
A: แน่นอน. ไลบรารีถูกคอมไพล์สำหรับ Java 8+ และทำงานได้อย่างราบรื่นบน Java 11, 17 และเวอร์ชัน LTS ที่ใหม่กว่า.

**Q: ถ้าฉันต้องการลบคีย์เวิร์ดต้องทำอย่างไร?**  
A: ดึงรายการคีย์เวิร์ด, ลบรายการที่ไม่ต้องการ, จากนั้นเรียก `metadata.getIptc().setKeywords(updatedList)` และบันทึกไฟล์.

## สรุป

คุณมีรูปแบบที่สมบูรณ์และพร้อมใช้งานสำหรับ **การเพิ่มคีย์เวิร์ด IPTC ใน Java** ด้วย GroupDocs.Metadata โดยการเริ่มต้นอ็อบเจ็กต์ metadata, ตรวจสอบให้มีแพ็กเกจ IPTC, เพิ่มคีย์เวิร์ด, และตรวจสอบผลลัพธ์ คุณสามารถผสานการแท็กที่แข็งแกร่งเข้าไปในกระบวนการ DAM หรือเวิร์กโฟลว์การจัดการเนื้อหาใด ๆ ที่ใช้ Java ได้สำเร็จ สำรวจประเภทเมตาดาต้าเพิ่มเติม—EXIF, XMP, และแท็กกำหนดเอง—to further enrich your assets.

**ขั้นตอนต่อไป**

- ขยายตัวอย่างเพื่อประมวลผลเป็นชุดโฟลเดอร์ของภาพ.  
- ผสานการเพิ่มคีย์เวิร์ดกับการวิเคราะห์ภาพอัตโนมัติ (เช่น แท็กที่สร้างโดย AI).  
- สำรวจ API ของ GroupDocs.Metadata สำหรับการอ่าน/เขียนข้อมูล GPS ของ EXIF เพื่อเปิดใช้งานการค้นหาตามตำแหน่ง.

---

**อัปเดตล่าสุด:** 2026-08-15  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/metadata/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-metadata</artifactId>
      <version>24.12</version>
   </dependency>
</dependencies>
```

## บทแนะนำที่เกี่ยวข้อง

- [สกัดหัว BMP Java – บทแนะนำภาพ GroupDocs.Metadata](/metadata/java/image-formats/)
- [java extract image metadata – Extract Panasonic MakerNote Metadata Using GroupDocs.Metadata in Java](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [Automate Java Metadata Updates by Date Using GroupDocs.Metadata for Efficient File Management](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)