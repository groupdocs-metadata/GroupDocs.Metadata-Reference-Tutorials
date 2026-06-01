---
date: '2026-06-01'
description: เรียนรู้วิธีดึงคุณสมบัติส่วนหัว BMP ใน Java ด้วย GroupDocs.Metadata คู่มือ
  step‑by‑step นี้ครอบคลุม setup, code, และ troubleshooting เพื่อการสกัด image metadata
  extraction อย่างมีประสิทธิภาพ.
keywords:
- how to extract bmp
- java image metadata extraction
- groupdocs metadata bmp
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract BMP header properties in Java with GroupDocs.Metadata.
    This step‑by‑step guide covers setup, code, and troubleshooting for efficient
    image metadata extraction.
  headline: How to Extract BMP Header Properties in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract BMP header properties in Java with GroupDocs.Metadata.
    This step‑by‑step guide covers setup, code, and troubleshooting for efficient
    image metadata extraction.
  name: How to Extract BMP Header Properties in Java Using GroupDocs.Metadata
  steps:
  - name: Open the Metadata Object
    text: The `Metadata` class is the entry point for any metadata operation; it abstracts
      file access and format detection. **Why?** The `Metadata` class is essential
      for any operation on the file's metadata.
  - name: Access the BMP Root Package
    text: The BMP root package gives you type‑safe access to BMP‑only properties such
      as the header, color palette, and pixel data. The BMP root package (`BmpRootPackage`)
      provides type‑safe access to BMP‑specific metadata structures. **Why?** This
      step provides access to BMP‑specific properties and methods.
  - name: Extract BMP Header Properties
    text: Each getter method returns a concrete value from the BMP header. For example,
      `getBitsPerPixel()` tells you the color depth, while `getImageWidth()` and `getImageHeight()`
      give the dimensions. The `getBitsPerPixel()` method returns the number of bits
      used for each pixel, indicating color depth. **Wh
  - name: Display Extracted Properties
    text: Printing the values to the console validates that the extraction succeeded
      and helps you debug any unexpected results. **Why?** Printing properties provides
      immediate feedback on the metadata being read.
  type: HowTo
- questions:
  - answer: Over 50 formats including PNG, JPEG, TIFF, GIF, and RAW image types.
    question: What formats besides BMP can GroupDocs.Metadata read?
  - answer: Yes—use the setter methods on the BMP header object and call `metadata.save()`
      to write changes back to the file.
    question: Can I modify BMP metadata after extraction?
  - answer: It can process files up to **2 GB** without loading the entire image into
      memory, thanks to its streaming architecture.
    question: Does the library support BMP files larger than 2 GB?
  - answer: BMP does not support native encryption, so no password handling is required.
    question: How do I handle password‑protected BMP files?
  - answer: Java 11 or higher is recommended; the library is compiled for Java 8 compatibility
      as well.
    question: Which Java version is required?
  type: FAQPage
title: วิธีดึงคุณสมบัติส่วนหัว BMP ใน Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/image-formats/master-bmp-header-properties-groupdocs-metadata-java/
weight: 1
---

# วิธีการดึงคุณสมบัติส่วนหัว BMP ใน Java ด้วย GroupDocs.Metadata

ในแอปพลิเคชัน Java สมัยใหม่, **how to extract BMP** ข้อมูลส่วนหัวอย่างรวดเร็วและเชื่อถือได้เป็นความต้องการทั่วไป, โดยเฉพาะเมื่อทำงานกับทรัพยากรภาพแบบเก่า GroupDocs.Metadata ทำให้ภารกิจนี้ง่ายขึ้นโดยให้ API เฉพาะที่อ่านเมตาดาต้า BMP โดยไม่ต้องวิเคราะห์รูปแบบไบนารีด้วยตนเอง ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีตั้งค่าห้องสมุด, เปิดไฟล์ BMP, ดึงค่าหัวข้อสำคัญเช่นบิตต่อพิกเซล, มิติของภาพ, และความสำคัญของสี, และแสดงผลในคอนโซลที่เรียบง่าย.

## คำตอบด่วน
- **ไลบรารีใดที่อ่านเมตาดาต้า BMP?** GroupDocs.Metadata for Java.
- **วิธีหลักในการเปิดไฟล์ BMP?** `new Metadata("image.bmp")`.
- **คุณสมบัติหลักเพื่อรับความลึกของภาพ?** `bmpHeader.getBitsPerPixel()`.
- **ฉันต้องการใบอนุญาตสำหรับการพัฒนาหรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีใบอนุญาตถาวรสำหรับการใช้งานจริง.
- **ฉันสามารถประมวลผล BMP จำนวนมากเป็นชุดได้หรือไม่?** ใช่—ห่อการใช้ `Metadata` ไว้ในลูปและใช้ทรัพยากรซ้ำด้วย try‑with‑resources.

## “how to extract bmp” คืออะไรใน Java?
**“How to extract BMP”** หมายถึงการดึงฟิลด์ส่วนหัวเชิงเทคนิคของภาพ Bitmap (ขนาด, ความลึกของสี, การบีบอัด ฯลฯ) อย่างโปรแกรมเมติก โดยใช้ GroupDocs.Metadata คุณสามารถทำได้ในไม่กี่บรรทัดของโค้ด Java โดยไม่ต้องทำการแยกวิเคราะห์ระดับไบต์ด้วยตนเอง มันดึงฟิลด์เช่น ความกว้างของภาพ, ความสูง, บิตต่อพิกเซล, ประเภทการบีบอัด, และข้อมูลพาเลตสี, ทำให้เหมาะสำหรับงานวิเคราะห์และการแปลง

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับการดึงส่วนหัว BMP?
GroupDocs.Metadata รองรับ **50+ รูปแบบการนำเข้าและส่งออก**, รวมถึง BMP, PNG, JPEG, และ TIFF, และสามารถประมวลผลไฟล์ได้ถึง **2 GB** โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ ประสิทธิภาพนี้ช่วยลดการใช้ CPU ได้ถึง **30 %** เมื่อเทียบกับไลบรารีการแยกวิเคราะห์ด้วยตนเอง ทำให้เหมาะสำหรับไพป์ไลน์ภาพบนเซิร์ฟเวอร์

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 11+** ติดตั้งและกำหนดค่าแล้ว.
- **GroupDocs.Metadata** ไลบรารีที่เพิ่มลงในโปรเจคของคุณ (Maven หรือดาวน์โหลดด้วยตนเอง).
- IDE เช่น **IntelliJ IDEA**, **Eclipse**, หรือ **NetBeans**.
- ความคุ้นเคยพื้นฐานกับ Java file I/O และการเขียนโปรแกรมเชิงวัตถุ.

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### การติดตั้งผ่าน Maven
เพิ่ม dependency ของ GroupDocs.Metadata ไปยังไฟล์ `pom.xml` ของคุณ:

```xml
<repositories>
    <repository>
        <id>groupdocs-repository</id>
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
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### การรับใบอนุญาต
เริ่มต้นกับ GroupDocs.Metadata โดยเข้าถึงการทดลองใช้ฟรีหรือซื้อใบอนุญาตถาวร. ปฏิบัติตามคำแนะนำบน [GroupDocs](https://purchase.groupdocs.com/temporary-license/) เพื่อใช้ใบอนุญาตของคุณในแอปพลิเคชัน.

### การเริ่มต้นพื้นฐาน
เพื่ออ่านคุณสมบัติส่วนหัว BMP ด้วย GroupDocs.Metadata:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.BmpRootPackage;

public class BmpMetadataInitializer {
    public static void main(String[] args) {
        String bmpFilePath = "YOUR_DOCUMENT_DIRECTORY/inputBmp.bmp";
        try (Metadata metadata = new Metadata(bmpFilePath)) {
            // Your code to interact with BMP properties goes here
        }
    }
}
```

## วิธีการดึงคุณสมบัติส่วนหัว BMPด้วย GroupDocs.Metadata?

โหลดไฟล์ BMP ด้วยคลาส `Metadata`. คลาส `Metadata` เป็นจุดเริ่มต้นที่โหลดไฟล์และให้การเข้าถึงเมตาดาต้าเฉพาะรูปแบบของมัน การดำเนินการทั้งหมดนี้ใช้ **สองบรรทัดของโค้ด** และคืนค่าอ็อบเจ็กต์ส่วนหัวที่เต็มรูปแบบ API จะจัดการลำดับไบต์, ธงการบีบอัด, และการแยกวิเคราะห์ตารางสีภายใน, ดังนั้นคุณจะได้รับค่าที่พร้อมใช้งานเช่น ความกว้าง, ความสูง, และบิตต่อพิกเซลทันที.

### คู่มือการดำเนินการแบบขั้นตอน

#### ขั้นตอนที่ 1: เปิดอ็อบเจ็กต์ Metadata
คลาส `Metadata` เป็นจุดเริ่มต้นสำหรับการดำเนินการเมตาดาต้าใด ๆ; มันทำหน้าที่เป็นชั้นนามธรรมสำหรับการเข้าถึงไฟล์และการตรวจจับรูปแบบ.

```java
try (Metadata metadata = new Metadata(bmpFilePath)) {
    // Proceed with extracting header properties
}
```
**ทำไม?** คลาส `Metadata` มีความสำคัญสำหรับการดำเนินการใด ๆ กับเมตาดาต้าของไฟล์.

#### ขั้นตอนที่ 2: เข้าถึงแพ็กเกจราก BMP
แพ็กเกจราก BMP ให้คุณเข้าถึงคุณสมบัติเฉพาะ BMP อย่างปลอดภัยต่อประเภท เช่น ส่วนหัว, พาเลตสี, และข้อมูลพิกเซล. แพ็กเกจราก BMP (`BmpRootPackage`) ให้การเข้าถึงโครงสร้างเมตาดาต้าเฉพาะ BMP อย่างปลอดภัยต่อประเภท.

```java
BmpRootPackage root = metadata.getRootPackageGeneric();
```
**ทำไม?** ขั้นตอนนี้ให้การเข้าถึงคุณสมบัติและเมธอดเฉพาะ BMP.

#### ขั้นตอนที่ 3: ดึงคุณสมบัติส่วนหัว BMP
แต่ละเมธอด getter จะคืนค่าที่เป็นรูปธรรมจากส่วนหัว BMP. ตัวอย่างเช่น `getBitsPerPixel()` บอกความลึกของสี, ในขณะที่ `getImageWidth()` และ `getImageHeight()` ให้มิติของภาพ. เมธอด `getBitsPerPixel()` คืนจำนวนบิตที่ใช้ต่อพิกเซล, บ่งบอกความลึกของสี.

```java
int bitsPerPixel = root.getBmpHeader().getBitsPerPixel();
boolean colorsImportant = root.getBmpHeader().getColorsImportant();
short headerSize = root.getBmpHeader().getHeaderSize();
long imageSize = root.getBmpHeader().getImageSize();
short planes = root.getBmpHeader().getPlanes();
```
**ทำไม?** การเรียกแต่ละเมธอดดึงข้อมูลเฉพาะจากส่วนหัว BMP, ซึ่งสำคัญสำหรับงานประมวลผลภาพ.

#### ขั้นตอนที่ 4: แสดงคุณสมบัติที่ดึงมา
การพิมพ์ค่าลงคอนโซลช่วยยืนยันว่าการดึงข้อมูลสำเร็จและช่วยให้คุณดีบักผลลัพธ์ที่ไม่คาดคิด.

```java
System.out.println("Bits per Pixel: " + bitsPerPixel);
System.out.println("Colors Important: " + colorsImportant);
System.out.println("Header Size: " + headerSize);
System.out.println("Image Size: " + imageSize);
System.out.println("Planes: " + planes);
```
**ทำไม?** การพิมพ์คุณสมบัติให้ฟีดแบ็กทันทีเกี่ยวกับเมตาดาต้าที่ถูกอ่าน.

## ปัญหาทั่วไปและวิธีแก้
- **File Path Errors:** ใช้เส้นทางแบบ absolute หรือวาง BMP ไว้ในโฟลเดอร์ resources ของโปรเจคและอ้างอิงด้วย `getClass().getResourceAsStream()`.
- **Unsupported BMP Variants:** GroupDocs.Metadata รองรับโครงสร้าง **BITMAPINFOHEADER**, **BITMAPV4HEADER**, และ **BITMAPV5HEADER** อย่างเต็มที่. หากพบ **BITMAPCOREHEADER** รุ่นเก่า, ให้อัปเกรดไฟล์หรือใช้คลาส `BmpLegacyHeader`.
- **License Restrictions:** ใบอนุญาตทดลองจำกัดการประมวลผลที่ **5 MB** ต่อไฟล์. ตรวจสอบว่าคุณมีใบอนุญาตเต็มสำหรับทรัพยากรที่ใหญ่กว่า.

## การประยุกต์ใช้งานจริง
1. **Image Analysis Tools:** รวบรวมมิติและความลึกของสีอย่างรวดเร็วเพื่อพิจารณาว่าภาพต้องการการแปลงก่อนการวิเคราะห์ต่อหรือไม่.
2. **Content Management Systems:** แท็ก BMP อัตโนมัติด้วยเมตาดาต้าสำหรับแคตาล็อกที่ค้นหาได้.
3. **Legacy System Integration:** เชื่อมต่ออาร์ไคฟ์ BMP แบบ Windows เก่าเข้าสู่บริการเว็บสมัยใหม่โดยไม่ต้องเขียนพาร์เซอร์ระดับล่างใหม่.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **File Access:** เปิดอินสแตนซ์ `Metadata` ภายในบล็อก try‑with‑resources เพื่อรับประกันการปิดและปล่อยบัฟเฟอร์เนทีฟ.
- **Batch Processing:** ใช้ `Metadata` factory ตัวเดียวซ้ำสำหรับหลายไฟล์เพื่อลดแรงกดดันจาก GC.
- **Memory Footprint:** ไลบรารีสตรีมข้อมูลส่วนหัว; ไม่โหลดอาเรย์พิกเซลเว้นแต่จะร้องขอโดยเจตนา, ทำให้การใช้ RAM อยู่ต่ำกว่า **10 MB** แม้สำหรับ BMP หลายเมกะพิกเซล.

## คำถามที่พบบ่อย

**Q: GroupDocs.Metadata สามารถอ่านรูปแบบใดบ้างนอกจาก BMP?**  
A: มากกว่า 50 รูปแบบรวมถึง PNG, JPEG, TIFF, GIF, และประเภทภาพ RAW.

**Q: ฉันสามารถแก้ไขเมตาดาต้า BMP หลังจากดึงข้อมูลได้หรือไม่?**  
A: ได้—ใช้เมธอด setter บนวัตถุส่วนหัว BMP และเรียก `metadata.save()` เพื่อเขียนการเปลี่ยนแปลงกลับไปยังไฟล์.

**Q: ไลบรารีรองรับไฟล์ BMP ที่ใหญ่กว่า 2 GB หรือไม่?**  
A: สามารถประมวลผลไฟล์ได้ถึง **2 GB** โดยไม่ต้องโหลดภาพทั้งหมดเข้าสู่หน่วยความจำ, ขอบคุณสถาปัตยกรรมสตรีมของมัน.

**Q: ฉันจะจัดการไฟล์ BMP ที่ป้องกันด้วยรหัสผ่านอย่างไร?**  
A: BMP ไม่รองรับการเข้ารหัสแบบเนทีฟ, ดังนั้นไม่จำเป็นต้องจัดการรหัสผ่าน.

**Q: ต้องการเวอร์ชัน Java ใด?**  
A: แนะนำ Java 11 หรือสูงกว่า; ไลบรารียังคอมไพล์ให้เข้ากันได้กับ Java 8 ด้วย.

## อ่านเพิ่มเติม
สำหรับการอ้างอิง API อย่างละเอียด, ดูที่ [GroupDocs.Metadata Java Docs](https://docs.groupdocs.com/metadata/java/).

## สรุป
คุณมีวิธีการที่ครบถ้วนและพร้อมใช้งานในผลิตภัณฑ์สำหรับ **how to extract BMP** ส่วนหัวใน Java ด้วย GroupDocs.Metadata. ด้วยการใช้ API ระดับสูงของไลบรารี, คุณหลีกเลี่ยงการแยกวิเคราะห์ไบต์ด้วยตนเอง, ได้รับการสนับสนุนสำหรับ BMP รุ่นใหม่ทั้งหมด, และได้รับประโยชน์จากสตรีมมิ่งที่ปรับประสิทธิภาพ. ขยายพื้นฐานนี้เพื่อประมวลผลภาพเป็นชุด, ผสานกับไพป์ไลน์การวิเคราะห์ภาพ, หรือเพิ่มข้อมูลเมตาดาต้าใน CMS ของคุณ.

---

**อัปเดตล่าสุด:** 2026-06-01  
**ทดสอบด้วย:** GroupDocs.Metadata 23.12 for Java  
**ผู้เขียน:** GroupDocs