---
date: '2026-06-01'
description: เรียนรู้วิธีดึงส่วนข้อความของ png ด้วย GroupDocs.Metadata สำหรับ Java
  – อ่านเมตาดาต้า png อย่างมีประสิทธิภาพและผสานการจัดการภาพที่แข็งแกร่ง
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: วิธีดึงส่วนข้อความของ png โดยใช้ GroupDocs.Metadata Java API
type: docs
url: /th/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# วิธีการสกัดชังค์ข้อความ PNG ด้วย GroupDocs.Metadata Java API

การสกัดข้อมูลข้อความจากไฟล์รูปภาพอาจเป็นเรื่องท้าทาย โดยเฉพาะรูปแบบที่ไม่ได้อิงข้อความเช่น PNGs. **GroupDocs.Metadata for Java** ทำให้กระบวนการนี้ง่ายขึ้นด้วยเครื่องมือที่แข็งแกร่งในการดึงและจัดการเมตาดาต้าที่ฝังอยู่ในภาพเหล่านี้ ไม่ว่าคุณจะจัดการกับชังค์ข้อความทั่วไป, ชังค์ที่บีบอัด, หรือชังค์ข้อความระดับสากล, GroupDocs.Metadata มีโซลูชันที่ราบรื่นให้คุณ

ในบทแนะนำนี้ เราจะพาคุณผ่านขั้นตอนการสกัดชังค์ข้อความประเภทต่าง ๆ จากไฟล์ PNG ด้วยไลบรารี GroupDocs.Metadata ใน Java. เมื่อเข้าใจเทคนิคเหล่านี้แล้ว คุณสามารถรวมฟีเจอร์การสกัดข้อความเข้ากับแอปพลิเคชันของคุณได้อย่างไร้รอยต่อ, เพิ่มศักยภาพการประมวลผลข้อมูลในหลายโดเมน

## คำตอบสั้น
- **GroupDocs.Metadata สามารถอ่านเมตาดาต้า PNG ได้หรือไม่?** ใช่, สามารถอ่านเมตาดาต้า PNG มาตรฐานทั้งหมดรวมถึงชังค์ข้อความ  
- **ต้องใช้ Java เวอร์ชันใด?** รองรับ Java 8 หรือใหม่กว่าอย่างเต็มที่  
- **ต้องการไลเซนส์สำหรับการพัฒนาหรือไม่?** ทดลองใช้งานฟรีสามารถอ่านเมตาดาต้าได้; ต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในผลิตภัณฑ์  
- **สามารถสกัดชังค์ข้อความได้กี่ประเภท?** มี 3 ประเภทหลัก: ทั่วไป, บีบอัด, และระดับสากล  
- **ประสิทธิภาพเป็นปัญหาหรือไม่?** การสกัดใช้เวลาไม่เกิน 200 ms สำหรับ PNG ขนาดประมาณ 5 MB บน CPU สมัยใหม่

## “how to extract png” คืออะไร?
**“how to extract png”** หมายถึงกระบวนการดึงชังค์ข้อความที่ฝังอยู่ในไฟล์ภาพ PNG ด้วย API โปรแกรมเมชัน ชังค์ข้อความเหล่านี้อาจบรรจุเมตาดาต้าเชิงอธิบาย, คอมเมนต์, หรือสตริงระดับสากล โดยการใช้ GroupDocs.Metadata for Java นักพัฒนาสามารถอ่าน, กรอง, และจัดการชังค์เหล่านี้ได้โดยไม่ต้องถอดรหัสภาพทั้งหมด

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับการสกัดข้อความ PNG?
GroupDocs.Metadata รองรับ **รูปแบบภาพและเอกสารกว่า 50+** และสามารถประมวลผลไฟล์ PNG **โดยไม่ต้องโหลดภาพทั้งหมดเข้าสู่หน่วยความจำ**, ให้ความเร็วการสกัดเฉลี่ย **150 ms** สำหรับไฟล์ขนาดสูงสุด 10 MB. ไลบรารียังรับประกัน **ความเที่ยงตรงของข้อมูล 100 %**, รักษาตัวอักษร Unicode ในชังค์ข้อความระดับสากล

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มสกัดชังค์ข้อความจากภาพ PNG ด้วย GroupDocs.Metadata for Java, โปรดตรวจสอบว่าคุณมีสิ่งต่อไปนี้:

### ไลบรารีและการพึ่งพาที่จำเป็น
- **GroupDocs.Metadata for Java**: เพิ่มไลบรารีนี้ในโปรเจกต์ของคุณผ่าน Maven หรือดาวน์โหลดโดยตรง

### ความต้องการการตั้งค่าสภาพแวดล้อม
- สภาพแวดล้อมการพัฒนาที่ตั้งค่าไว้ด้วย Java (แนะนำ JDK 8 หรือใหม่กว่า)  
- IDE เช่น IntelliJ IDEA, Eclipse, หรือเครื่องมืออื่นที่รองรับโปรเจกต์ Java

### ความรู้พื้นฐานที่ต้องมี
- ความเข้าใจพื้นฐานการเขียนโปรแกรม Java  
- ความคุ้นเคยกับการจัดการไฟล์และไดเรกทอรีในแอปพลิเคชัน Java

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

เพื่อเริ่มต้นใช้งาน GroupDocs.Metadata, คุณต้องเพิ่มไลบรารีนี้ในโปรเจกต์ของคุณ ดำเนินการตามขั้นตอนต่อไปนี้โดยใช้ Maven หรือดาวน์โหลดไลบรารีโดยตรง:

### การตั้งค่า Maven
เพิ่ม repository และ dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [เวอร์ชันล่าสุดของ GroupDocs.Metadata สำหรับ Java](https://releases.groupdocs.com/metadata/java/)

#### ขั้นตอนการรับไลเซนส์
- **ทดลองใช้ฟรี**: เริ่มต้นด้วยการทดลองใช้ฟรีเพื่อสำรวจฟีเจอร์  
- **ไลเซนส์ชั่วคราว**: รับไลเซนส์ชั่วคราวสำหรับการทดสอบต่อเนื่อง  
- **ซื้อ**: ซื้อไลเซนส์หากคุณพร้อมใช้งานในผลิตภัณฑ์

### การเริ่มต้นและตั้งค่าพื้นฐาน

หลังจากตั้งค่าไลบรารีแล้ว, ให้เริ่มต้น GroupDocs.Metadata ในแอปพลิเคชัน Java ของคุณดังนี้:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## วิธีสกัดชังค์ข้อความ PNG จากไฟล์ PNG?

คลาส `Metadata` เป็นจุดเริ่มต้นสำหรับการเข้าถึงสตรีมเมตาดาต้าของไฟล์ โหลดไฟล์ PNG ด้วย `new Metadata("yourImage.png")`, เข้าถึงแพ็กเกจราก, และวนลูปผ่านคอลเลกชันชังค์ข้อความที่ต้องการ – ทั้งหมดในไม่กี่บรรทัดของโค้ด วิธีนี้จะคืนค่าชังค์ข้อความทั่วไป, บีบอัด, และระดับสากลทั้งหมด, ให้คุณจัดการตามที่ต้องการ

### คำอธิบายสั้น
คลาส `Metadata` เป็นจุดเริ่มต้นของ GroupDocs.Metadata, เป็นคอนเทนเนอร์ที่ให้คุณเข้าถึงสตรีมเมตาดาต้าทั้งหมดภายในไฟล์แบบโปรแกรม

## การสกัดชังค์ข้อความทั่วไปจาก PNG

ฟีเจอร์นี้ช่วยให้คุณดึงชังค์ข้อความทั่วไปทั้งหมดที่ฝังอยู่ในไฟล์ PNG วิธีทำดังนี้:

#### ภาพรวม
คุณจะเข้าถึงและวนลูปผ่านแต่ละชังค์ข้อความที่เก็บอยู่ในเมตาดาต้าของภาพ

#### การดำเนินการแบบขั้นตอน
1. **นำเข้าคลาสที่จำเป็น:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **เริ่มต้น Metadata และเข้าถึงแพ็กเกจราก:**  
   `PngRootPackage` แสดงถึงคอนเทนเนอร์รากของเมตาดาต้า PNG, เปิดเผยคอลเลกชันของชังค์ข้อความ

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **คำอธิบายพารามิเตอร์:**  
   - `pngFilePath`: เส้นทางไปยังไฟล์ PNG ของคุณ  
   - `PngRootPackage`: แสดงถึงแพ็กเกจรากที่บรรจุชังค์เมตาดาต้า

#### เคล็ดลับการแก้ปัญหา
- ตรวจสอบให้แน่ใจว่าไฟล์ PNG ของคุณมีชังค์ข้อความ; หากไม่มีจะไม่มีข้อมูลที่ดึงออกมา  
- ตรวจสอบว่าเส้นทางไปยังไฟล์ PNG ถูกต้อง

## การสกัดชังค์ข้อความบีบอัดจาก PNG

เพื่อจัดการกับชังค์ข้อความบีบอัดโดยเฉพาะ, ทำตามขั้นตอนต่อไปนี้:

#### ภาพรวม
ฟีเจอร์นี้มุ่งเน้นการดึงและจัดการชังค์ข้อความบีบอัดภายในเมตาดาต้า PNG

#### การดำเนินการแบบขั้นตอน
1. **นำเข้าคลาสที่จำเป็น:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **เริ่มต้น Metadata และเข้าถึงแพ็กเกจราก:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **คำอธิบายพารามิเตอร์:**  
   - `getCompressionMethod()`: คืนค่าวิธีการบีบอัดที่ใช้. เมธอด `getCompressionMethod()` จะคืนค่าอัลกอริทึมบีบอัดที่ใช้สำหรับชังค์ข้อความบีบอัด

#### เคล็ดลับการแก้ปัญหา
- ตรวจสอบว่าไฟล์ PNG ของคุณใช้วิธีบีบอัดที่รองรับ  
- จัดการข้อยกเว้นในกรณีที่ชังค์ข้อความอาจไม่ได้บีบอัด

## การสกัดชังค์ข้อความระดับสากลจาก PNG

สำหรับการสกัดชังค์ข้อความระดับสากล, ทำตามขั้นตอนต่อไปนี้:

#### ภาพรวม
ดึงและจัดการชังค์ข้อความระดับสากลภายในเมตาดาต้า PNG, รวมถึงรายละเอียดภาษา

#### การดำเนินการแบบขั้นตอน
1. **นำเข้าคลาสที่จำเป็น:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **เริ่มต้น Metadata และเข้าถึงแพ็กเกจราก:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **คำอธิบายพารามิเตอร์:**  
   - `getLanguage()`: ดึงแท็กภาษาสำหรับชังค์ข้อความ. เมธอด `getLanguage()` ให้แท็กภาษา ISO ที่เชื่อมโยงกับชังค์ข้อความระดับสากล  
   - `isCompressed()`: ระบุว่าชังค์ข้อความถูกบีบอัดหรือไม่. เมธอด `isCompressed()` แสดงว่าชังค์ข้อความถูกเก็บในรูปแบบบีบอัดหรือไม่

#### เคล็ดลับการแก้ปัญหา
- ตรวจสอบว่าไฟล์ PNG ของคุณตั้งค่าเมตาดาต้าระดับสากลอย่างถูกต้อง  
- จัดการสถานการณ์ที่การแปลอาจไม่มีให้ใช้งาน

## การประยุกต์ใช้งานจริง

การเข้าใจวิธีสกัดชังค์ข้อความจาก PNG ด้วย GroupDocs.Metadata สามารถนำไปใช้ในแอปพลิเคชันต่าง ๆ ได้อย่างมีคุณค่า:
- **ระบบจัดการเนื้อหา (CMS)**: ดึงและจัดระเบียบเมตาดาต้าอัตโนมัติสำหรับห้องสมุดภาพ  
- **เครื่องมือวิเคราะห์ข้อมูล**: เพิ่มความสามารถในการสกัดข้อมูลโดยรวมการวิเคราะห์เมตาดาต้าภาพ  
- **โครงการเว็บสแครปปิ้ง**: สกัดข้อมูลสำคัญจากภาพที่ฝังอยู่บนเว็บไซต์

## คำถามที่พบบ่อย

**Q: สามารถอ่านเมตาดาต้า PNG ได้โดยไม่ต้องมีไลเซนส์หรือไม่?**  
A: ใช่, การทดลองใช้ฟรีสามารถอ่านเมตาดาต้าได้, แต่ต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในผลิตภัณฑ์

**Q: GroupDocs.Metadata รองรับรูปแบบภาพอื่น ๆ หรือไม่?**  
A: แน่นอน – รองรับ JPEG, BMP, TIFF, และรูปแบบเพิ่มเติมกว่า 40 รูปแบบอื่น

**Q: จะจัดการไฟล์ PNG ขนาดใหญ่อย่างมีประสิทธิภาพอย่างไร?**  
A: ใช้ API สตรีมมิ่ง; มันประมวลผลไฟล์โดยไม่โหลดภาพเต็มเข้าสู่หน่วยความจำ, ทำให้การใช้ RAM ต่ำกว่า 50 MB

**Q: ถ้า PNG ไม่มีชังค์ข้อความจะเกิดอะไรขึ้น?**  
A: API จะคืนคอลเลกชันว่าง; คุณสามารถตรวจสอบ `isEmpty()` ก่อนทำการประมวลผลได้อย่างปลอดภัย

**Q: Unicode รองรับในชังค์ข้อความระดับสากลหรือไม่?**  
A: รองรับเต็มที่, GroupDocs.Metadata รองรับ UTF‑8, รักษาตัวอักษรทุกภาษา

## สรุป

โดยทำตามบทแนะนำนี้ คุณได้เรียนรู้วิธีสกัดชังค์ข้อความทั่วไป, บีบอัด, และระดับสากลจากไฟล์ PNG ด้วยไลบรารี GroupDocs.Metadata ใน Java. ทักษะนี้จะช่วยเพิ่มความสามารถของแอปพลิเคชันในการประมวลผลและวิเคราะห์ข้อมูลภาพอย่างมีประสิทธิภาพ สำหรับการสำรวจต่อไป, พิจารณาเรียนรู้เทคนิคการจัดการเมตาดาต้าขั้นสูงที่ GroupDocs.Metadata มีให้

**ขั้นตอนต่อไป**
- ทดลองสกัดเมตาดาต้าประเภทต่าง ๆ  
- สำรวจฟีเจอร์เพิ่มเติมของไลบรารี GroupDocs.Metadata  
- แชร์ผลลัพธ์หรือแอปพลิเคชันของคุณในชุมชนนักพัฒนาเพื่อรับข้อเสนอแนะและการปรับปรุง

---

**อัปเดตล่าสุด:** 2026-06-01  
**ทดสอบกับ:** GroupDocs.Metadata Java 23.9  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [วิธีสกัดบล็อกทรัพยากรภาพจาก JPEG ด้วย GroupDocs.Metadata for Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [สกัดคอมเมนต์ภาพ JPEG2000 ใน Java ด้วย GroupDocs.Metadata: คู่มือขั้นตอนโดยละเอียด](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [สกัดทรัพยากรภาพจากไฟล์ PSD ด้วย GroupDocs.Metadata ใน Java: คู่มือครบวงจร](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)