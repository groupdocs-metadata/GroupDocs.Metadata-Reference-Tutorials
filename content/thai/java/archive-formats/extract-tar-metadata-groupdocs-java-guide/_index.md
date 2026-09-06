---
date: '2026-09-06'
description: เรียนรู้วิธีดึงเมตาดาต้า TAR ด้วย Java โดยใช้ GroupDocs.Metadata สำหรับ
  Java ในคู่มือขั้นตอนต่อขั้นตอนนี้
keywords:
- extract tar metadata java
- GroupDocs.Metadata for Java
- TAR archive metadata
lastmod: '2026-09-06'
og_description: ดึงเมตาดาต้า TAR ด้วย Java โดยใช้ GroupDocs.Metadata สำหรับ Java.
  ทำตามบทแนะนำสั้นนี้เพื่ออ่านไฟล์ TAR, ดึงรายละเอียดไฟล์, และผสานผลลัพธ์เข้ากับแอปพลิเคชัน
  Java ของคุณ.
og_image_alt: Guide showing Java code extracting TAR metadata with GroupDocs.Metadata
og_title: ดึงเมตาดาต้า TAR ด้วย Java ด้วย GroupDocs.Metadata – คู่มือ Java อย่างรวดเร็ว
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract TAR metadata java using GroupDocs.Metadata for
    Java in this step-by-step guide.
  headline: How to extract TAR metadata java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract TAR metadata java using GroupDocs.Metadata for
    Java in this step-by-step guide.
  name: How to extract TAR metadata java with GroupDocs.Metadata
  steps:
  - name: '**Data migration:** Validate file counts and sizes before moving data between
      systems.'
    text: '**Data migration:** Validate file counts and sizes before moving data between
      systems.'
  - name: '**Backup solutions:** Generate inventory reports to confirm that every
      file in a backup archive is accounted for.'
    text: '**Backup solutions:** Generate inventory reports to confirm that every
      file in a backup archive is accounted for.'
  - name: '**Content management systems (CMS):** Enrich stored assets with TAR‑level
      metadata for better search and organization.'
    text: '**Content management systems (CMS):** Enrich stored assets with TAR‑level
      metadata for better search and organization.'
  type: HowTo
- questions:
  - answer: Metadata extraction aids in file management tasks like validation, backup,
      and migration.
    question: What is the primary use case for extracting metadata from TAR files?
  - answer: GroupDocs.Metadata supports various archive formats; you’ll need to decompress
      the .gz layer first.
    question: Can I extract metadata from compressed .tar.gz files?
  - answer: The library handles large archives efficiently, but overall performance
      depends on your system’s resources.
    question: Is there a limit on the number of files that can be processed in a single
      TAR archive?
  - answer: Call `metadata.dispose()` to release native resources after operations
      are completed.
    question: How do I dispose of metadata objects properly?
  - answer: Visit the [GroupDocs Metadata Java Docs](https://docs.groupdocs.com/metadata/java/)
      and join their community forum for support.
    question: Where can I find more information or support for GroupDocs.Metadata?
  type: FAQPage
tags:
- extract tar metadata
- GroupDocs.Metadata
- Java archive processing
- TAR metadata extraction
- Java
title: วิธีดึงเมตาดาต้า TAR ด้วย Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/
weight: 1
---

# วิธีการดึงข้อมูลเมตาดาต้า TAR ด้วย Java และ GroupDocs.Metadata

ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีการดึงข้อมูลเมตาดาต้า TAR ด้วย Java** โดยใช้ไลบรารี GroupDocs.Metadata เมื่อจบคู่มือคุณจะสามารถอ่านไฟล์อาร์ไคฟ์ `.tar` นับรายการแต่ละรายการ และดึงข้อมูลระดับไฟล์ เช่น ชื่อ ขนาด และเวลา‑ประทับ – ทั้งหมดด้วยเพียงไม่กี่บรรทัดของโค้ด Java

## คำตอบสั้น
- **ไลบรารีใดที่จัดการเมตาดาต้า TAR ใน Java?** GroupDocs.Metadata for Java  
- **ใช้เวลานานเท่าไหร่สำหรับการทำงานพื้นฐาน?** ประมาณ 10–15 นาที  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีหรือไลเซนส์ชั่วคราวทำงานได้สำหรับการประเมิน; จำเป็นต้องมีไลเซนส์แบบชำระเงินสำหรับการใช้งานจริง  
- **ฉันสามารถประมวลผลไฟล์ TAR ขนาดใหญ่ได้หรือไม่?** ใช่, แต่ต้องทำการกำจัดอ็อบเจ็กต์ `Metadata` เพื่อปล่อยทรัพยากร  
- **นี่คือการอ่าน .tar.gz เหมือนกันหรือไม่?** คุณต้องทำการแตกไฟล์ .gz ก่อน, แล้วจึงใช้วิธีเดียวกัน  

## วิธีการดึงเมตาดาต้า TAR ด้วย Java ด้วย GroupDocs.Metadata สำหรับ Java?

`Metadata` class ให้ API ระดับสูงสำหรับอ่านข้อมูลอาร์ไคฟ์ โหลดไฟล์ TAR ด้วยอ็อบเจ็กต์ `Metadata`, เข้าถึงแพ็กเกจราก, วนลูปแต่ละรายการ, และอ่านคุณสมบัติที่ต้องการ กระบวนการที่ตรงไปตรงมานี้ทำให้คุณดึงข้อมูลเมตาดาต้าทุกส่วนโดยไม่ต้องเขียนตรรกะการพาร์สระดับต่ำด้วยตนเอง

**คำตอบโดยตรง:** สร้างอ็อบเจ็กต์ `Metadata` ที่ชี้ไปยังไฟล์ `.tar` ของคุณ, เรียก `getRootPackage()` เพื่อรับแพ็กเกจของอาร์ไคฟ์, จากนั้นวนลูปผ่าน `getEntries()` เพื่ออ่านชื่อ, ขนาด, และเวลา‑ประทับของแต่ละรายการ. สุดท้ายเรียก `metadata.dispose()` เพื่อปล่อยทรัพยากรเนทีฟ กระบวนการทั้งหมดนี้โดยทั่วไปต้องใช้โค้ดน้อยกว่าสิบบรรทัด

### ทำไมต้องเลือก GroupDocs.Metadata?

GroupDocs.Metadata รองรับ **กว่า 30 รูปแบบอาร์ไคฟ์และเอกสาร**, รวมถึง TAR, ZIP, RAR, และ 7z, และสามารถประมวลผลอาร์ไคฟ์ที่มี **สูงสุด 10,000 รายการ** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ runtime Java ข้ามแพลตฟอร์มทำงานบน Windows, Linux, และ macOS, มีการจัดการข้อผิดพลาดและทรัพยากรในตัวที่ทำให้ **วิธีการอ่าน tar** ง่ายขึ้นเมื่อทำงานในระดับใหญ่

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK) 8 หรือสูงกว่า  
- Maven สำหรับการจัดการ dependencies  
- GroupDocs.Metadata for Java 24.12 หรือใหม่กว่า – สามารถดาวน์โหลดเวอร์ชันล่าสุดจากหน้า releases อย่างเป็นทางการ  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

`Metadata` class เป็นจุดเริ่มต้นสำหรับการอ่านข้อมูลอาร์ไคฟ์.  
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

**ดาวน์โหลดโดยตรง:** หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### ขั้นตอนการรับไลเซนส์

เริ่มต้นด้วยการทดลองใช้ฟรีหรือขอไลเซนส์ชั่วคราวจากเว็บไซต์ของ GroupDocs. สิ่งนี้ทำให้คุณสามารถสำรวจคุณสมบัติทั้งหมดโดยไม่มีข้อจำกัดระหว่างการพัฒนา.

### การเริ่มต้นและตั้งค่าเบื้องต้น

เมื่อไลบรารีพร้อมใช้งาน, คุณสามารถสร้างอ็อบเจ็กต์ `Metadata` ที่ชี้ไปยังไฟล์ TAR ของคุณ:

คอนสตรัคเตอร์ `new Metadata("path/to/archive.tar")` จะโหลดเมตาดาต้าอาร์ไคฟ์เข้าสู่หน่วยความจำ.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.TarFile;
import com.groupdocs.metadata.core.TarRootPackage;

public class TarMetadataExample {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("path/to/your/input.tar");
        
        try {
            // Perform operations with metadata
        } finally {
            if (metadata != null) {
                metadata.dispose();
            }
        }
    }
}
```

## คู่มือการใช้งาน

### การอ่านเมตาดาต้าจากอาร์ไคฟ์ TAR

#### เริ่มต้นอ็อบเจ็กต์ metadata

สร้างอินสแตนซ์ของ `Metadata` ด้วยเส้นทางไฟล์ `.tar` ของคุณ.

`Metadata` object แยกตรรกะการพาร์ส TAR ระดับต่ำออก, ให้คุณใช้ API ระดับสูงในการทำงาน.  
```java
Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.tar");
```
**ทำไม:** ขั้นตอนนี้เตรียมอ็อบเจ็กต์ที่ให้คุณเข้าถึงโครงสร้างภายในของอาร์ไคฟ์, ซึ่งเป็นพื้นฐานของ **วิธีการอ่าน tar**

#### เข้าถึงแพ็กเกจราก

ดึงแพ็กเกจรากเพื่อทำงานกับเนื้อหาในอาร์ไคฟ์ TAR:

แพ็กเกจรากเป็นคอนเทนเนอร์ระดับบนของอาร์ไคฟ์และให้เมธอดสำหรับนับรายการของมัน.  
```java
TarRootPackage root = metadata.getRootPackageGeneric();
```
การเรียกนี้เป็นสิ่งสำคัญสำหรับการนำทางโครงสร้างของอาร์ไคฟ์.

#### รับจำนวนรายการทั้งหมด

กำหนดจำนวนรายการ (ไฟล์/โฟลเดอร์) ที่อาร์ไคฟ์มี:

`rootPackage.getEntries().size()` คืนค่าจำนวนที่แน่นอน, ช่วยให้คุณจัดสรรทรัพยากรล่วงหน้าหรือแสดงความคืบหน้า.  
```java
int totalEntries = root.getTarPackage().getTotalEntries();
System.out.println("Total Entries: " + totalEntries);
```
**คำอธิบาย:** การรู้จำนวนรายการช่วยให้คุณวางแผนลูปและตรวจสอบความสมบูรณ์ของอาร์ไคฟ์.

#### วนลูปแต่ละรายการไฟล์

`TarFile` class แทนรายการไฟล์เดียวภายในอาร์ไคฟ์ TAR.

แต่ละอ็อบเจ็กต์ `TarFile` มีคุณสมบัติเช่น `getFileName()`, `getSize()`, และ `getModifiedTime()`.  
```java
for (TarFile file : root.getTarPackage().getFiles()) {
    String fileName = file.getName();
    long fileSize = file.getSize();
    System.out.println("File Name: " + fileName);
    System.out.println("File Size: " + fileSize);
}
```
**ทำไม:** การประมวลผลแต่ละไฟล์แยกกันทำให้คุณได้เมตาดาต้าแบบละเอียด, ซึ่งมักจำเป็นสำหรับการรายงาน, การย้ายข้อมูล, หรือการตรวจสอบการสำรองข้อมูล.

### เคล็ดลับการแก้ไขปัญหา
- **ปัญหาทั่วไป:** การสกัดข้อมูลล้มเหลว – ตรวจสอบเส้นทางไฟล์อีกครั้งและให้แน่ใจว่าไฟล์ TAR สามารถอ่านได้โดยกระบวนการ Java.  
- **เคล็ดลับด้านประสิทธิภาพ:** ควรเรียก `metadata.dispose()` เสมอหลังจากเสร็จงานเพื่อปล่อยทรัพยากรเนทีฟ, โดยเฉพาะเมื่อจัดการอาร์ไคฟ์ขนาดใหญ่.  

## การประยุกต์ใช้งานจริง
1. **การย้ายข้อมูล:** ตรวจสอบจำนวนและขนาดไฟล์ก่อนย้ายข้อมูลระหว่างระบบ.  
2. **โซลูชันสำรองข้อมูล:** สร้างรายงานสินค้าคงคลังเพื่อยืนยันว่าไฟล์ทุกไฟล์ในอาร์ไคฟ์สำรองได้รับการบันทึก.  
3. **ระบบจัดการเนื้อหา (CMS):** เพิ่มเมตาดาต้าในระดับ TAR ให้กับทรัพยากรที่จัดเก็บเพื่อการค้นหาและการจัดระเบียบที่ดีขึ้น.  

## พิจารณาด้านประสิทธิภาพ
เมื่อทำงานกับอาร์ไคฟ์ขนาดใหญ่:
- กำจัดอ็อบเจ็กต์โดยเร็วเพื่อหลีกเลี่ยงการรั่วไหลของหน่วยความจำ.  
- ใช้ Java streaming APIs หากต้องการประมวลผลรายการโดยไม่โหลดรายการทั้งหมดเข้าสู่หน่วยความจำ.  

## สรุป
คุณตอนนี้มีวิธีที่ครบถ้วนจากต้นจนจบสำหรับ **การดึงเมตาดาต้า TAR ด้วย Java** โดยใช้ GroupDocs.Metadata สำหรับ Java. ความสามารถนี้สามารถนำไปผสานกับเครื่องมือย้ายข้อมูล, ยูทิลิตี้สำรองข้อมูล, หรือระบบใด ๆ ที่พัฒนาด้วย Java ที่ต้องการข้อมูลเชิงลึกของเนื้อหาอาร์ไคฟ์.

**ขั้นตอนต่อไป:** สำรวจคลาสเพิ่มเติมใน GroupDocs.Metadata API—เช่นคุณสมบัติของ `TarFile` สำหรับเวลา‑ประทับหรือสิทธิ์—to further enrich your metadata extraction workflow.

## คำถามที่พบบ่อย

**ถาม: จุดประสงค์หลักของการดึงเมตาดาต้าจากไฟล์ TAR คืออะไร?**  
**ตอบ:** การดึงเมตาดาต้าช่วยในงานจัดการไฟล์เช่นการตรวจสอบ, การสำรอง, และการย้ายข้อมูล.

**ถาม: ฉันสามารถดึงเมตาดาต้าจากไฟล์ .tar.gz ที่บีบอัดได้หรือไม่?**  
**ตอบ:** GroupDocs.Metadata รองรับรูปแบบอาร์ไคฟ์หลายประเภท; คุณต้องแตกชั้น .gz ก่อน.

**ถาม: มีขีดจำกัดจำนวนไฟล์ที่สามารถประมวลผลในอาร์ไคฟ์ TAR เดียวหรือไม่?**  
**ตอบ:** ไลบรารีจัดการอาร์ไคฟ์ขนาดใหญ่ได้อย่างมีประสิทธิภาพ, แต่ประสิทธิภาพโดยรวมขึ้นอยู่กับทรัพยากรของระบบของคุณ.

**ถาม: ฉันจะกำจัดอ็อบเจ็กต์เมตาดาต้าอย่างถูกต้องได้อย่างไร?**  
**ตอบ:** เรียก `metadata.dispose()` เพื่อปล่อยทรัพยากรเนทีฟหลังจากดำเนินการเสร็จสิ้น.

**ถาม: ฉันสามารถหาข้อมูลเพิ่มเติมหรือรับการสนับสนุนสำหรับ GroupDocs.Metadata ได้จากที่ไหน?**  
**ตอบ:** เยี่ยมชม [GroupDocs Metadata Java Docs](https://docs.groupdocs.com/metadata/java/) และเข้าร่วมฟอรั่มชุมชนของพวกเขาเพื่อรับการสนับสนุน.

**คำถามเพิ่มเติม**

**ถาม: GroupDocs.Metadata ทำงานบนสภาพแวดล้อม Windows และ Linux ทั้งสองหรือไม่?**  
**ตอบ:** ใช่, ไลบรารี Java เป็นแบบข้ามแพลตฟอร์มและทำงานได้ทุกที่ที่ติดตั้ง JDK ที่เข้ากันได้.

**ถาม: ฉันสามารถดึงเวลา‑ประทับของไฟล์ (การสร้าง/การแก้ไข) จากรายการ TAR ได้หรือไม่?**  
**ตอบ:** คลาส `TarFile` ให้เข้าถึงฟิลด์หัวข้อ TAR มาตรฐานรวมถึงเวลา‑ประทับ.

**ถาม: ฉันจะจัดการกับอาร์ไคฟ์ที่มีการป้องกันด้วยรหัสผ่านอย่างไร?**  
**ตอบ:** สำหรับอาร์ไคฟ์ที่เข้ารหัส, ให้ระบุรหัสผ่านเมื่อสร้างอ็อบเจ็กต์ `Metadata` (ดูเอกสาร API สำหรับ overload ที่ตรงกัน).

**แหล่งข้อมูล**
- **เอกสาร:** [GroupDocs Metadata Java Docs](https://docs.groupdocs.com/metadata/java/)  
- **API reference:** [GroupDocs API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download:** [GroupDocs Releases](https://releases.groupdocs.com/metadata/java/)  
- **GitHub:** [GroupDocs Metadata on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Free support:** [GroupDocs Forum](https://forum.groupdocs.com/c/metadata/)  
- **Temporary license:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**อัปเดตล่าสุด:** 2026-09-06  
**ทดสอบด้วย:** GroupDocs.Metadata for Java 24.12  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [วิธีการดึงคอมเมนต์ zip ด้วย Java โดยใช้ GroupDocs.Metadata – คู่มือ](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)
- [อัปเดตคอมเมนต์อาร์ไคฟ์ zip Groupdocs Metadata Java](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [วิธีการดึงเมตาดาต้าด้วย GroupDocs.Metadata สำหรับ Java – บทแนะนำและตัวอย่าง](/metadata/java/)