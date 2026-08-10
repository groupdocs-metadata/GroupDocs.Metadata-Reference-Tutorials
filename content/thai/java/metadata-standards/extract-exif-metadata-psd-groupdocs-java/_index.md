---
date: '2026-08-10'
description: เรียนรู้วิธีการดึงข้อมูลเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata
  สำหรับ Java คู่มือนี้ครอบคลุมการดึงข้อมูลพื้นฐาน, แพ็กเกจ IFD, ข้อมูล GPS, และกรณีการใช้งานจริง
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: เรียนรู้วิธีการดึงข้อมูลเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata
  สำหรับ Java คู่มือแบบ Step‑by‑step, code snippets, และเคล็ดลับการแก้ปัญหาสำหรับนักพัฒนา
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: วิธีการดึงข้อมูลเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: วิธีการดึงข้อมูลเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata
type: docs
url: /th/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# วิธีดึงข้อมูลเมตาดาต้า EXIF จากไฟล์ PSD ด้วย GroupDocs.Metadata

การดึง **เมตาดาต้า EXIF** จากไฟล์ PSD เป็นขั้นตอนที่ทำบ่อยแต่มีประสิทธิภาพเมื่อคุณต้องการตรวจสอบแหล่งที่มาของภาพ, ทำการแท็กสินทรัพย์อัตโนมัติ, หรือสร้างห้องสมุดสื่อที่สามารถค้นหาได้ ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีดึง EXIF** อย่างรวดเร็วด้วย GroupDocs.Metadata สำหรับ Java, ดูการเรียก API อย่างละเอียด, และเรียนรู้วิธีจัดการกับแพ็กเกจ IFD ขั้นสูงและพิกัด GPS เมื่อเสร็จสิ้นคุณจะพร้อมผสานการดึงเมตาดาต้าเข้ากับกระบวนการทำงานใด ๆ ที่ใช้ Java

## คำตอบด่วน
คลาส `Metadata` แทนไฟล์และให้การเข้าถึงเมตาดาต้าของไฟล์

- **บรรทัดแรกของโค้ดคืออะไร?** `Metadata metadata = new Metadata("sample.psd");`
- **เมธอดใดที่คืนค่าชื่อศิลปิน?** `metadata.getExif().getArtist();`
- **ฉันสามารถอ่านข้อมูล GPS ได้หรือไม่?** ได้ – ใช้ `metadata.getExif().getGpsInfo();`
- **ฉันต้องการใบอนุญาตสำหรับการใช้งานจริงหรือไม่?** จำเป็นต้องมีใบอนุญาต GroupDocs.Metadata ที่ถูกต้องหลังจากช่วงทดลองใช้งาน
- **เวอร์ชัน Java ที่รองรับ?** Java 8 หรือใหม่กว่า (สูงสุดถึง Java 21).

## เมตาดาต้า EXIF คืออะไร?
เมตาดาต้า EXIF (Exchangeable Image File Format) เก็บการตั้งค่ากล้อง, เวลาสร้าง, และข้อมูลตำแหน่งภายในไฟล์ภาพ GroupDocs.Metadata อ่านข้อมูลนี้โดยตรงจากโครงสร้างไบนารีของไฟล์ PSD และเปิดเผยผ่าน Java API ที่สะอาดตา มันทำให้ผู้พัฒนาสามารถดึงรายละเอียดเช่น รุ่นกล้อง, เวลาเปิดรับแสง, และพิกัด GPS ได้โดยอัตโนมัติโดยไม่ต้องตรวจสอบด้วยตนเอง

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
GroupDocs.Metadata รองรับ **ไฟล์รูปแบบกว่า 30** (รวมถึง PSD, JPEG, PNG, TIFF) และสามารถประมวลผลไฟล์ได้ถึง **2 GB** โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ ไลบรารีนี้ดึง **แท็ก EXIF มากกว่า 150 รายการ** ทำให้คุณมีชุดเต็มของคุณลักษณะกล้องและ GPS ที่จำเป็นสำหรับการวิเคราะห์หรือการปฏิบัติตามข้อกำหนด

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8** หรือใหม่กว่า ติดตั้งบนเครื่องของคุณ.  
- **Maven** สำหรับการจัดการ dependencies.  
- **GroupDocs.Metadata for Java รุ่น 24.12** (หรือใหม่กว่า).  
- ความคุ้นเคยพื้นฐานกับคลาส, ออบเจ็กต์, และการจัดการข้อยกเว้นของ Java.

### ไลบรารีและ dependencies ที่จำเป็น
| ไลบรารี | พิกัด Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### การตั้งค่าสภาพแวดล้อม
คุณควรมี IDE ที่รองรับ Maven เช่น IntelliJ IDEA หรือ Eclipse สร้างโปรเจกต์ Maven ใหม่หรือเพิ่ม dependency ลงในโปรเจกต์ที่มีอยู่

## วิธีตั้งค่า GroupDocs.Metadata สำหรับ Java
สามารถเพิ่ม GroupDocs.Metadata ไปยังโปรเจกต์ Maven ด้วยการกำหนดค่าเพียงไม่กี่บรรทัด ขั้นตอนต่อไปนี้แสดงวิธีรวม repository และ dependency เพื่อให้ไลบรารีพร้อมใช้งานใน classpath

### การตั้งค่า Maven
เพิ่มโค้ดสแนปด้านล่างนี้ในไฟล์ `pom.xml` ของคุณภายในส่วน `<dependencies>`:

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

### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจากหน้าปล่อยอย่างเป็นทางการ: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### การรับใบอนุญาต
เพื่อใช้งานไลบรารีหลังจากระยะทดลอง 30 วัน ให้รับใบอนุญาตชั่วคราวหรือเต็มรูปแบบ:

1. เยี่ยมชม [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. เลือก **temporary** สำหรับการทดสอบหรือ **full** สำหรับการใช้งานจริง.  
3. ทำตามคำแนะนำบนหน้าจอเพื่อฝังไฟล์ใบอนุญาต (`metadata.lic`) ใน classpath ของ Java ของคุณ.

### การเริ่มต้นและตั้งค่าพื้นฐาน
หลังจากไลบรารีอยู่ใน classpath แล้ว ให้เริ่มต้นตามตัวอย่างด้านล่าง:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## วิธีดึงคุณสมบัติเมตาดาต้า EXIF พื้นฐานจากภาพ PSD
ส่วนนี้อธิบายวิธีโหลดไฟล์ PSD, เข้าถึงคอนเทนเนอร์ EXIF, และอ่านแท็กที่พบบ่อยที่สุดเช่น **artist**, **copyright**, และ **software** กระบวนการประกอบด้วยการสร้างอินสแตนซ์ `Metadata`, เรียก `getExif()`, แล้วดึงคุณสมบัติเฉพาะด้วยเมธอด getter อย่างง่าย

### การดำเนินการแบบขั้นตอนต่อขั้นตอน
1. สร้างอินสแตนซ์ `Metadata` ที่ชี้ไปยังไฟล์ PSD ของคุณ.  
2. เรียก `getExif()` เพื่อรับคอนเทนเนอร์ EXIF.  
3. อ่านคุณสมบัติเฉพาะเช่น `getArtist()`, `getCopyright()`, และ `getSoftware()`.  
4. พิมพ์หรือเก็บค่าตามตรรกะของแอปพลิเคชันของคุณ.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **เคล็ดลับ:** อ็อบเจ็กต์ `Metadata` จะตรวจจับรูปแบบไฟล์โดยอัตโนมัติ ดังนั้นคุณสามารถใช้โค้ดเดียวกันสำหรับไฟล์ JPEG หรือ TIFF ได้โดยไม่ต้องแก้ไข.

## วิธีดึงคุณสมบัติแพ็กเกจ EXIF IFD จากภาพ PSD
ส่วน IFD (Image File Directory) เก็บรายละเอียดเชิงเทคนิคเชิงลึกเช่น **camera serial number**, **lens model**, และ **user comments** `Ifd0` แทน Image File Directory หลักที่มีข้อมูลพื้นฐานของกล้อง การดึงฟิลด์เหล่านี้มีประโยชน์สำหรับการวิเคราะห์ทางนิติวิทยาศาสตร์หรือการทำแคตาล็อกความแม่นยำสูง

### ขั้นตอนการดำเนินการ
1. ใช้ซ้ำอินสแตนซ์ `Metadata` จากส่วนก่อนหน้า.  
2. นำทางไปยังคอนเทนเนอร์ IFD ผ่าน `metadata.getExif().getIfd0()`.  
3. อ่านคุณสมบัติเช่น `getBodySerialNumber()` และ `getUserComment()`.  
4. แสดงผลข้อมูลหรือแมปไปยังโมเดลโดเมนของคุณ.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## วิธีดึงข้อมูล GPS (ละติจูด, ลองจิจูด) จากไฟล์ PSD
กล้องสมัยใหม่หลายรุ่นฝังพิกัด GPS ไว้ในบล็อก EXIF `GpsInfo` เก็บพิกัดทางภูมิศาสตร์ที่ดึงจากข้อมูล EXIF เรียก `metadata.getExif().getGpsInfo()` แล้วใช้ `getLatitude()`, `getLongitude()`, และ `getAltitude()` เพื่อรับข้อมูลตำแหน่งที่แม่นยำ—ไม่ต้องทำการแยกวิเคราะห์เพิ่มเติม

### ขั้นตอนโดยละเอียด
1. รับอ็อบเจ็กต์ GPS info: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. อ่านละติจูดและลองจิจูด: `gps.getLatitude()` คืนค่า `double` ในหน่วยองศาทศนิยม.  
3. จัดการข้อมูลที่หายไป: API จะคืนค่า `null` หากไม่มีแท็กดังกล่าว ดังนั้นควรป้องกัน `NullPointerException`.

> **ข้อผิดพลาดทั่วไป:** บางไฟล์ PSD เก็บพิกัด GPS เป็นจำนวนเชิงอัตรา; ไลบรารีจะทำให้เป็นค่าปกติอัตโนมัติ แต่ไฟล์เก่าอาจต้องแปลงด้วยตนเอง.

## ปัญหาทั่วไปและการแก้ไขปัญหา
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| `Unsupported format` exception | ใช้ GroupDocs.Metadata เวอร์ชันเก่าที่ไม่รู้จัก PSD | อัปเกรดเป็นเวอร์ชัน 24.12 หรือใหม่กว่า |
| `NullPointerException` when calling `getArtist()` | ไม่มีแท็ก EXIF ในไฟล์ต้นทาง | ตรวจสอบ `metadata.getExif().hasArtist()` ก่อนอ่าน |
| License error after 30 days | ไม่พบไฟล์ใบอนุญาตใน classpath | วาง `metadata.lic` ใน `src/main/resources` หรือกำหนด `Metadata.setLicense("path/to/license")` |

## คำถามที่พบบ่อย

**Q: ฉันสามารถดึงเมตาดาต้า EXIF จากไฟล์ PSD ที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ได้. โหลดไฟล์ด้วย `new Metadata("file.psd", "password")` แล้วเข้าถึงข้อมูล EXIF ตามปกติ.

**Q: GroupDocs.Metadata รองรับการประมวลผลแบบชุดของไฟล์ PSD จำนวนมากหรือไม่?**  
A: แน่นอน. สร้างอ็อบเจ็กต์ `Metadata` ภายในลูป หรือใช้ตัวช่วย `MetadataCollection` เพื่อประมวลผลไดเรกทอรีอย่างมีประสิทธิภาพ.

**Q: เวอร์ชัน Java ที่รองรับอย่างเป็นทางการคืออะไร?**  
A: Java 8 ถึง Java 21 ได้รับการทดสอบอย่างเต็มที่ ไลบรารีใช้เฉพาะ API มาตรฐาน ดังนั้นจึงทำงานบน JVM ใด ๆ ที่สอดคล้อง.

**Q: สามารถเขียนข้อมูล EXIF กลับเข้าไปในไฟล์ PSD ได้หรือไม่?**  
A: ได้. หลังจากแก้ไขคุณสมบัติโดยใช้วัตถุ `Exif` แล้วเรียก `metadata.save("output.psd")` เพื่อบันทึกการเปลี่ยนแปลง.

**Q: ไลบรารีสามารถจัดการไฟล์ PSD ขนาดเท่าไหร่โดยไม่เกิดการใช้หน่วยความจำเต็ม?**  
A: GroupDocs.Metadata สตรีมข้อมูลและสามารถประมวลผลไฟล์ได้ถึง **2 GB** บนเครื่องที่มี RAM 8 GB ปกติ ด้วยสถาปัตยกรรมใช้หน่วยความจำน้อย.

## สรุป
ตอนนี้คุณรู้ **วิธีดึงเมตาดาต้า EXIF** จากไฟล์ PSD ด้วย GroupDocs.Metadata สำหรับ Java ตั้งแต่แท็กพื้นฐานจนถึง IFD ขั้นสูงและข้อมูล GPS ผสานโค้ดเหล่านี้เข้าสู่ pipeline การประมวลผลภาพของคุณเพื่อทำการจัดทำแคตาล็อกอัตโนมัติ, ตรวจสอบการปฏิบัติตาม, หรือบริการที่อิงตำแหน่ง สำหรับการสำรวจเพิ่มเติม ลองดึงเมตาดาต้าจากรูปแบบที่รองรับอื่น ๆ (JPEG, TIFF, PNG) หรือทดลองความสามารถในการเขียนกลับเพื่อฝังแท็กที่กำหนดเอง.

---

**Last Updated:** 2026-08-10  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [ดึงทรัพยากรภาพจากไฟล์ PSD ด้วย GroupDocs.Metadata ใน Java: คู่มือเชิงลึก](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [ดึงข้อมูล Header และ Layer ของ PSD ด้วย GroupDocs.Metadata สำหรับ Java: คู่มือเชิงลึก](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [ดึงคุณสมบัติ MakerNote เป็นแท็ก TIFF/EXIF ด้วย GroupDocs.Metadata ใน Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)