---
date: '2026-06-12'
description: เรียนรู้วิธีอัปเดตเมตาดาต้าภาพ Java ด้วย GroupDocs.Metadata สำหรับ Java
  รวมถึงโครงสร้าง Dublin Core, Camera Raw, XMP Basic และ Job Ticket
keywords:
- update image metadata java
- GroupDocs.Metadata Java
- image metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  headline: How to update image metadata java using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  name: How to update image metadata java using GroupDocs.Metadata
  steps:
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Dublin Core Package:**'
    text: '**Create or Retrieve Dublin Core Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Camera Raw Package:**'
    text: '**Create or Retrieve Camera Raw Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Replace Existing XMP Basic Package:**'
    text: '**Replace Existing XMP Basic Package:**'
  type: HowTo
- questions:
  - answer: Yes. After creating one `Metadata` instance, you can retrieve and modify
      any combination of packages before calling `save()` once.
    question: Can I update multiple metadata schemes in a single operation?
  - answer: Absolutely. Load the image into a `InputStream` from S3, pass the stream
      to the `Metadata` constructor, and save the result back to the cloud.
    question: Does the library work with images stored in cloud storage (e.g., AWS
      S3)?
  - answer: A valid commercial license is required for production deployments; a trial
      license is limited to evaluation and non‑commercial testing.
    question: Is a commercial license required for production use?
  - answer: GroupDocs.Metadata for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: What Java versions are officially supported?
  - answer: The API streams data and never loads the entire file into memory, allowing
      you to process very large images without excessive heap usage.
    question: How does the library handle large image files (e.g., >100 MB)?
  type: FAQPage
title: วิธีอัปเดตเมตาดาต้าภาพ Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/image-formats/update-image-metadata-groupdocs-metadata-java/
weight: 1
---

# วิธีอัปเดตเมตาดาต้าภาพ java ด้วย GroupDocs.Metadata

ในกระบวนการทำงานดิจิทัลสมัยใหม่, **updating image metadata java** มีความสำคัญสำหรับการทำให้สินทรัพย์สามารถค้นหาได้, ปฏิบัติตามข้อกำหนด, และพร้อมสำหรับการประมวลผลต่อเนื่อง ไม่ว่าคุณจะสร้างแอปจัดการรูปภาพ, ระบบจัดการเนื้อหา, หรือสายงานอัตโนมัติ การแก้ไขเมตาดาต้าโดยโปรแกรมช่วยประหยัดเวลามนุษย์เป็นจำนวนมาก คู่มือนี้จะพาคุณผ่านทุกขั้นตอนที่จำเป็นในการแก้ไขสคีมเมตาดาต้า Dublin Core, Camera Raw, XMP Basic, และ Basic Job Ticket ด้วย GroupDocs.Metadata for Java.

## คำตอบสั้น
- **ไลบรารีใดที่จัดการเมตาดาต้าภาพใน Java?** GroupDocs.Metadata for Java.  
- **ฉันสามารถอัปเดต Dublin Core และ XMP ในหนึ่งขั้นตอนได้หรือไม่?** ใช่ – instantiate a `Metadata` object and work with multiple packages before saving.  
- **ฉันต้องการใบอนุญาตสำหรับการทดลองใช้หรือไม่?** A free trial license unlocks all features; a full license removes usage limits.  
- **เวอร์ชัน Java ที่ต้องการคืออะไร?** JDK 8 or higher.  
- **Maven เป็นวิธีเดียวในการเพิ่ม dependency หรือไม่?** Maven is recommended, but you can also download the JAR from the official releases page.

## วิธีอัปเดตเมตาดาต้าภาพ java ด้วย GroupDocs.Metadata?
`Metadata` เป็นคลาสหลักที่ให้การเข้าถึงแบบอ่าน/เขียนต่อเมตาดาต้าภาพ โหลดภาพเป้าหมายเข้าสู่ `Metadata` instance, ดึงหรือสร้างแพ็กเกจเมตาดาต้าที่ต้องการ (เช่น Dublin Core, Camera Raw), ตั้งค่าคุณสมบัติที่จำเป็น, และเรียก `save()` เพื่อเขียนการเปลี่ยนแปลงกลับไปยังดิสก์ กระบวนการนี้ทำงานกับ JPEG, PNG, TIFF, และรูปแบบอื่น ๆ มากมาย.

### ทำไมต้องเลือก GroupDocs.Metadata สำหรับ Java?
GroupDocs.Metadata รองรับ **50+ input and output formats**, ประมวลผลไฟล์ภาพหลายร้อยหน้าโดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ, และให้ API ที่เป็น fluent ที่ช่วยให้คุณอัปเดตหลายสคีมเมตาดาต้าในหนึ่งการดำเนินการ ไลบรารีนี้เป็น thread‑safe อย่างเต็มที่ ทำให้เหมาะสำหรับสภาพแวดล้อมเซิร์ฟเวอร์ที่ต้องการประมวลผลสูง.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8+** – ตรวจสอบให้ `java -version` แสดง 1.8 หรือใหม่กว่า.  
- **Maven** – สำหรับการจัดการ dependency; คุณสามารถใช้ Gradle ได้หากต้องการ.  
- **Basic Java knowledge** – ความคุ้นเคยกับ IDE เช่น IntelliJ IDEA หรือ Eclipse.  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java
เพิ่มไลบรารีลงในโครงการ Maven ของคุณโดยใส่ dependency ต่อไปนี้ลงในไฟล์ `pom.xml` ของคุณ:

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

คุณยังสามารถดาวน์โหลด JAR ล่าสุดจากหน้า releases อย่างเป็นทางการ: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### การรับใบอนุญาต
เริ่มต้นด้วยใบอนุญาตทดลองฟรีเพื่อสำรวจทุกฟีเจอร์ สำหรับการใช้งานในผลิตจริง, ซื้อใบอนุญาตเต็มหรือขอใบอนุญาตชั่วคราวผ่าน [purchase page](https://purchase.groupdocs.com/temporary-license). ใบอนุญาตที่ถูกต้องจะลบข้อจำกัดการทดลองทั้งหมดและเปิดใช้งานการสนับสนุนระดับพรีเมี่ยม.

### การเริ่มต้นพื้นฐาน
คลาส `Metadata` เป็นจุดเริ่มต้นสำหรับการดำเนินการอ่าน/เขียนทั้งหมดบนไฟล์ภาพ หลังจากเพิ่ม dependency แล้ว, คุณสามารถเริ่มต้นไลบรารีได้ดังนี้:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataUpdater {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
            // Your code to update metadata will go here
        }
    }
}
```

## การอัปเดตสคีมเมตาดาต้าเฉพาะ

### ฉันจะอัปเดตสคีมเมตาดาต้า Dublin Core ด้วย GroupDocs.Metadata for Java อย่างไร?
`Metadata` เป็นจุดเริ่มต้นหลักสำหรับการเข้าถึงเมตาดาต้าภาพ `DublinCorePackage` แทนชุดเมตาดาต้า Dublin Core และอนุญาตให้ตั้งค่าฟิลด์อธิบายมาตรฐาน เช่น `format`, `rights`, และ `subject`. สร้างอ็อบเจ็กต์ `Metadata`, ดึง `DublinCorePackage`, ตั้งค่า, และบันทึกไฟล์เพื่อให้ข้อมูลอธิบายสอดคล้องกับมาตรฐาน.

1. **เริ่มต้นอ็อบเจ็กต์ Metadata:**  
   คลาส `Metadata` แสดงไฟล์ภาพเดียวในหน่วยความจำและให้การเข้าถึงแพ็กเกจเมตาดาต้าทั้งหมดที่รองรับ.

   ```java
   try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
       IXmp root = (IXmp) metadata.getRootPackage();
       if (root.getXmpPackage() != null) {
           // Further steps will be added here
       }
   }
   ```

2. **สร้างหรือดึงแพ็กเกจ Dublin Core:**  
   ใช้ `metadata.getDublinCorePackage()` เพื่อดึงแพ็กเกจที่มีอยู่หรือสร้างใหม่หากไม่มี.

   ```java
   if (root.getXmpPackage().getSchemes().getDublinCore() == null) {
       root.getXmpPackage().getSchemes().setDublinCore(new XmpDublinCorePackage());
   }
   ```

3. **อัปเดตคุณสมบัติ:**  
   ตั้งค่าคุณสมบัติเช่น `format`, `rights`, และ `subject` โดยตรงบนอ็อบเจ็กต์แพ็กเกจ.

   ```java
   root.getXmpPackage().getSchemes().getDublinCore()
       .setFormat("image/gif")
       .setRights("Copyright (C) 2011-2021 GroupDocs. All Rights Reserved")
       .setSubject("test");
   ```

4. **บันทึกการเปลี่ยนแปลง:**  
   เรียก `metadata.save(outputPath)` เพื่อบันทึกเมตาดาต้าที่อัปเดต.

   ```java
   metadata.save("YOUR_OUTPUT_DIRECTORY/OutputGif");
   ```

### ฉันจะแก้ไขเมตาดาต้า Camera Raw ด้วย GroupDocs.Metadata for Java อย่างไร?
`Metadata` เป็นคลาสหลักสำหรับการอ่านและเขียนเมตาดาต้าภาพ `CameraRawPackage` ให้การเข้าถึงเมตาดาต้าเฉพาะของ Camera Raw เช่น exposure และ shadows. เมตาดาต้า Camera Raw เก็บพารามิเตอร์การถ่ายเทคนิคเช่น shadows, auto‑brightness, และ exposure. การอัปเดตฟิลด์เหล่านี้ทำให้เครื่องมือเช่น Lightroom แปลความหมายภาพได้อย่างถูกต้อง, ปรับปรุงการประมวลผลแบบแบทช์และรักษาความสอดคล้องในคอลเลกชันภาพขนาดใหญ่.

1. **เริ่มต้นอ็อบเจ็กต์ Metadata:**  
   ใช้ `Metadata` instance เดียวกันที่คุณสร้างสำหรับ Dublin Core.

2. **สร้างหรือดึงแพ็กเกจ Camera Raw:**  
   ตรวจสอบว่ามี `CameraRawPackage` อยู่หรือไม่ก่อนทำการเปลี่ยนแปลง.

   ```java
   if (root.getXmpPackage().getSchemes().getCameraRaw() == null) {
       root.getXmpPackage().getSchemes().setCameraRaw(new XmpCameraRawPackage());
   }
   ```

3. **อัปเดตคุณสมบัติ:**  
   ปรับค่าต่าง ๆ เช่น `shadows`, `autoBrightness`, และ `exposure` ให้สอดคล้องกับลักษณะภาพที่ต้องการ.

   ```java
   root.getXmpPackage().getSchemes().getCameraRaw()
       .setShadows(50)
       .setAutoBrightness(true)
       .setAutoExposure(true)
       .setCameraProfile("test")
       .setExposure(0.0001);
   ```

4. **บันทึกการเปลี่ยนแปลง:**  
   บันทึกการแก้ไขไปยังไดเรกทอรีผลลัพธ์ที่คุณเลือก.

### ฉันจะอัปเดตเมตาดาต้า XMP Basic ด้วย GroupDocs.Metadata for Java อย่างไร?
`Metadata` เป็นคลาสหลักที่ใช้จัดการเมตาดาต้าภาพ `XmpBasicPackage` แทนสคีม XMP Basic สำหรับฟิลด์เมตาดาต้าหลัก. XMP Basic ครอบคลุมฟิลด์หลักเช่น creation date, base URL, และ rating. การอัปเดตแอตทริบิวต์เหล่านี้ช่วยเพิ่มการจัดทำแคตาล็อก, ปรับปรุงความเกี่ยวข้องของการค้นหา, และทำให้การรวมกับระบบจัดการเนื้อหาดีขึ้น, ช่วยให้เครื่องมือสินทรัพย์ดิจิทัลจัดระเบียบและแสดงภาพตามเกณฑ์ที่ผู้ใช้กำหนด.

1. **เริ่มต้นอ็อบเจ็กต์ Metadata:**  
   ใช้ `Metadata` instance เดียวกันตลอดบทแนะนำ.

2. **แทนที่แพ็กเกจ XMP Basic ที่มีอยู่:**  
   หากไม่มีแพ็กเกจ XMP Basic, สร้างใหม่และแนบเข้ากับอ็อบเจ็กต์ `Metadata`.

   ```java
   root.getXmpPackage().getSchemes().setXmpBasic(new XmpBasicPackage());
   ```

3. **อัปเดตคุณสมบัติ:**  
   ตั้งค่า `creationDate`, `baseURL`, และ `rating` ตามต้องการ.

   ```java
   root.getXmpPackage().getSchemes().getXmpBasic()
       .setCreateDate(new Date())
       .setBaseUrl("https://groupdocs.com")
       .setRating(5);
   ```

4. **บันทึกการเปลี่ยนแปลง:**  
   เขียนเมตาดาต้าที่อัปเดตกลับไปยังดิสก์.

### ฉันจะทำงานกับสคีมเมตาดาต้า Basic Job Ticket ใน Java อย่างไร?
`Metadata` เป็นคลาสหลักสำหรับจัดการเมตาดาต้าภาพ `BasicJobTicketPackage` จัดการเมตาดาต้า job ticket, ทำให้สามารถฝังข้อมูลเวิร์กโฟลว์ลงในภาพได้ สคีม Basic Job Ticket ฝัง job ID, ชื่อ, และ URL ลงในไฟล์ภาพโดยตรง, ทำให้ระบบต่อเนื่องสามารถติดตามขั้นตอนการประมวลผลและเชื่อมโยงภาพกับงานเฉพาะ การรวม job ticket ช่วยเพิ่มความสามารถในการตรวจสอบและประสิทธิภาพการดำเนินงานในไพพ์ไลน์อัตโนมัติ.

1. **เริ่มต้นอ็อบเจ็กต์ Metadata:**  
   ใช้ `Metadata` instance เดียวกันต่อไป.

2. **ตั้งค่าแพ็กเกจ Basic Job Ticket:**  
   ดึงแพ็กเกจที่มีอยู่หรือสร้างใหม่หากไม่มี.

   ```java
   root.getXmpPackage().getSchemes().setBasicJobTicket(new XmpBasicJobTicketPackage());
   ```

3. **กำหนดค่างาน:**  
   กำหนดคุณสมบัติงานเช่น `id`, `name`, และ `url` เพื่อให้ระบบประมวลผลต่อเนื่องสามารถติดตามวงจรชีวิตของภาพ.

   ```java
   XmpJob job = new XmpJob();
   job.setID("1");
   job.setName("test job");
   job.setUrl("https://groupdocs.com");

   root.getXmpPackage().getSchemes().getBasicJobTicket()
       .setJobs(new XmpJob[]{job});
   ```

4. **บันทึกการเปลี่ยนแปลง:**  
   บันทึกข้อมูล job‑ticket ทั้งหมดไปยังโฟลเดอร์ผลลัพธ์.

## การประยุกต์ใช้งานจริง
- **Photography Studios:** อัตโนมัติการใส่ข้อมูลลิขสิทธิ์และใบอนุญาตลงใน JPEG ที่ส่งออกทุกไฟล์, เพื่อให้สอดคล้องกับกฎหมาย.  
- **Content Management Systems (CMS):** เพิ่มข้อมูลให้กับสินทรัพย์ที่อัปโหลดด้วย Dublin Core และ XMP เพื่อให้เครื่องมือค้นหาอินเดกซ์ภาพได้อย่างมีประสิทธิภาพมากขึ้น.  
- **Digital Asset Management (DAM):** ใช้สคีม Basic Job Ticket เพื่อฝังสถานะการประมวลผล, ทำให้ติดตามภาพผ่านไพพ์ไลน์ซับซ้อนได้ง่าย.

## ปัญหาทั่วไปและวิธีแก้
- **Missing Package Errors:** เรียกเมธอด `get...Package()` ก่อนตั้งค่าคุณสมบัติทุกครั้ง; หากคืนค่า `null` ให้สร้างแพ็กเกจก่อน.  
- **File Permission Problems:** รันกระบวนการ Java ของคุณด้วยสิทธิ์ OS ที่เพียงพอ, โดยเฉพาะเมื่อเขียนไปยังไดเรกทอรีที่ถูกป้องกัน.  
- **Unsupported Formats:** GroupDocs.Metadata รองรับรูปแบบภาพกว่า 50 แบบ; ตรวจสอบเอกสารอย่างเป็นทางการหากพบส่วนขยายที่ไม่รู้จัก.

## คำถามที่พบบ่อย

**Q: ฉันสามารถอัปเดตหลายสคีมเมตาดาต้าในหนึ่งการดำเนินการได้หรือไม่?**  
A: ใช่. หลังจากสร้างอ็อบเจ็กต์ `Metadata` หนึ่งตัว, คุณสามารถดึงและแก้ไขแพ็กเกจใด ๆ ที่ต้องการก่อนเรียก `save()` ครั้งเดียว.

**Q: ไลบรารีทำงานกับภาพที่จัดเก็บในคลาวด์สตอเรจ (เช่น AWS S3) หรือไม่?**  
A: แน่นอน. โหลดภาพเป็น `InputStream` จาก S3, ส่งสตรีมนี้ให้กับคอนสตรัคเตอร์ของ `Metadata`, แล้วบันทึกผลลัพธ์กลับไปยังคลาวด์.

**Q: ต้องการใบอนุญาตเชิงพาณิชย์สำหรับการใช้งานในผลิตจริงหรือไม่?**  
A: ต้องมีใบอนุญาตเชิงพาณิชย์ที่ถูกต้องสำหรับการใช้งานในผลิตจริง; ใบอนุญาตทดลองจำกัดการประเมินและการทดสอบที่ไม่ใช่เชิงพาณิชย์.

**Q: เวอร์ชัน Java ที่รองรับอย่างเป็นทางการคืออะไร?**  
A: GroupDocs.Metadata for Java รองรับ JDK 8, 11, และ 17, เพื่อให้เข้ากันได้กับแอปพลิเคชันทั้งแบบเก่าและใหม่.

**Q: ไลบรารีจัดการไฟล์ภาพขนาดใหญ่ (เช่น >100 MB) อย่างไร?**  
A: API สตรีมข้อมูลและไม่โหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ, ทำให้คุณสามารถประมวลผลภาพขนาดใหญ่มากโดยไม่ใช้ heap มากเกินไป.

## สรุป
โดยทำตามขั้นตอนในคู่มือนี้, คุณจะมีเวิร์กโฟลว์ที่ครบถ้วนและพร้อมใช้งานในผลิตจริงสำหรับ **updating image metadata java** ด้วย GroupDocs.Metadata. คุณสามารถเพิ่มข้อมูลให้กับภาพด้วย Dublin Core, Camera Raw, XMP Basic, และข้อมูล Job Ticket อย่างมั่นใจ, ทำให้สินทรัพย์ดิจิทัลของคุณค้นหาได้ง่าย, ปฏิบัติตามข้อกำหนด, และพร้อมสำหรับไพพ์ไลน์อัตโนมัติ. สำรวจฟีเจอร์อื่น ๆ ของไลบรารี—เช่นการสกัดเมตาดาต้าและการตรวจสอบความถูกต้อง—to further boost your asset‑management strategy.

---

**อัปเดตล่าสุด:** 2026-06-12  
**ทดสอบด้วย:** GroupDocs.Metadata for Java 23.12  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [สกัดเมตาดาต้าจากไฟล์ Canon CR2 ด้วย GroupDocs.Metadata Java: คู่มือเชิงลึกสำหรับรูปแบบภาพ](/metadata/java/image-formats/extract-metadata-groupdocs-metadata-canon-cr2/)
- [อัปเดตเมตาดาต้า PDF อย่างมีประสิทธิภาพด้วย GroupDocs.Metadata ใน Java สำหรับการจัดการเอกสาร](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [วิธีอัปเดตแท็ก MP3 ID3v2 ด้วย GroupDocs.Metadata ใน Java - คู่มือเชิงลึก](/metadata/java/audio-video-formats/update-mp3-id3v2-tags-groupdocs-metadata-java/)