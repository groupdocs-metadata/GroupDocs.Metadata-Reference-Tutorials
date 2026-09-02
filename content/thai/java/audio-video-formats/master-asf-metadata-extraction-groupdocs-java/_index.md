---
date: '2026-09-02'
description: เรียนรู้วิธีการดึงข้อมูล asf ใน Java ด้วย GroupDocs.Metadata คู่มือครอบคลุมการตั้งค่า
  Maven, การอ่านคุณสมบัติพื้นฐาน, รายละเอียด codec, descriptors, และการแก้ไขปัญหาเพื่อการจัดการสื่อที่เชื่อถือได้
keywords:
- how to extract asf
- groupdocs metadata java
- asf metadata extraction
lastmod: '2026-09-02'
og_description: เรียนรู้วิธีการดึงข้อมูล asf ใน Java ด้วย GroupDocs.Metadata คู่มือแบบขั้นตอนแสดงการตั้งค่า
  Maven, การอ่านคุณสมบัติ, ข้อมูล codec, และการแก้ไขปัญหาเพื่อการจัดการสื่อที่ราบรื่น
og_image_alt: Guide showing how to extract asf metadata in Java with GroupDocs.Metadata
og_title: วิธีการดึงข้อมูล asf ใน Java ด้วย GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-09-02'
  description: Learn how to extract asf in Java using GroupDocs.Metadata. The guide
    covers Maven setup, reading basic properties, codec details, descriptors, and
    troubleshooting for reliable media handling.
  headline: How to extract asf in Java with GroupDocs.Metadata
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, MOV, and many more. Simply
      instantiate the corresponding package class for the format you need.
    question: Can I extract metadata from other video formats with the same library?
  - answer: Absolutely. The library provides setter methods for most properties, allowing
      you to edit values and then save the file back to disk.
    question: Is it possible to modify ASF metadata after extraction?
  - answer: Not strictly, but a 64‑bit JVM gives you a larger heap, which is beneficial
      when processing files larger than 2 GB.
    question: Do I need a 64‑bit JVM for large ASF files?
  - answer: The trial license removes functional limits but adds a watermark to certain
      export operations. For unrestricted production use, purchase a full license.
    question: How does licensing affect trial usage?
  - answer: GroupDocs.Metadata is built for Java SE. For Android, use the .NET version
      with Xamarin or a compatible wrapper.
    question: Can I run this code on Android devices?
  type: FAQPage
tags:
- asf metadata
- groupdocs.metadata
- java media processing
title: วิธีการดึงข้อมูล asf ใน Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# วิธีการดึงข้อมูล asf ใน Java ด้วย GroupDocs.Metadata

ในสายการทำงานสื่อสมัยใหม่ การสามารถ **extract asf metadata in Java** มีความสำคัญต่อการจัดทำแคตาล็อก การปฏิบัติตามกฎระเบียบ และการประมวลผลอัตโนมัติ การแยกวิเคราะห์คอนเทนเนอร์ ASF ด้วยตนเองมีความเสี่ยงต่อข้อผิดพลาดและใช้เวลามาก แต่ GroupDocs.Metadata for Java ให้ API ระดับสูงที่ทำหน้าที่หนักให้คุณ คู่มือฉบับนี้จะพาคุณผ่านการติดตั้งไลบรารี การอ่านคุณสมบัติหลัก การเข้าถึงข้อมูล codec และการจัดการกับปัญหาทั่วไป เพื่อให้คุณสามารถรวมการดึงข้อมูลเมตาดาต้า ASF เข้าไปในแอปพลิเคชัน Java ใดก็ได้ด้วยความมั่นใจ

## คำตอบสั้น
- **“extract ASF metadata” หมายถึงอะไร?** หมายถึงการอ่านข้อมูลที่ฝังอยู่ในไฟล์โดยโปรแกรม—เช่น timestamp, ตัวระบุ codec, และ descriptor ของสตรีม—from an ASF file.  
- **ต้องใช้ไลบรารีใด?** GroupDocs.Metadata for Java (version 24.12 or later).  
- **ต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีหรือไลเซนส์ชั่วคราวใช้ได้สำหรับการพัฒนา; จำเป็นต้องมีไลเซนส์เต็มสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **เวอร์ชัน Java ที่รองรับคืออะไร?** JDK 8 or higher.  
- **สามารถใช้ Maven ได้หรือไม่?** Yes – Maven is the recommended dependency manager.

## asf metadata คืออะไร?
`ASF` (Advanced Systems Format) metadata คือชุดของแท็กที่มีโครงสร้างซึ่งจัดเก็บอยู่ภายในคอนเทนเนอร์ ASF ที่อธิบายคุณลักษณะทางเทคนิคและเชิงบรรยายของไฟล์สื่อ แท็กเหล่านี้รวมถึง timestamp การสร้าง, ตัวระบุ codec, descriptor ของภาษา, และคุณสมบัติระดับสตรีมเช่น bitrate และ duration การเข้าถึงข้อมูลนี้โดยโปรแกรมทำให้คุณสามารถสร้างแคตาล็อกที่ค้นหาได้, บังคับใช้กฎการปฏิบัติตาม, หรือขับเคลื่อนการตัดรหัสอัตโนมัติ

## ทำไมต้องใช้ GroupDocs.Metadata for Java เพื่อดึงข้อมูล asf metadata?
GroupDocs.Metadata รองรับ **30+ รูปแบบ audio/video** และสามารถประมวลผลไฟล์ได้สูงสุด **5 GB** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ ด้วยสถาปัตยกรรมสตรีมมิ่ง ไลบรารีนี้มีโมเดลอ็อบเจกต์ที่สะอาด—ไม่ต้องทำการแยกไบต์ระดับต่ำ—ทำให้คุณสามารถดึงคุณสมบัติ, codec, descriptor, และรายละเอียดสตรีมได้ด้วยการเรียกเมธอดไม่กี่ครั้ง สิ่งนี้มักจะลดความพยายามในการพัฒนาลงได้ถึง **70 %** เมื่อเทียบกับการสร้าง parser เอง

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK)** 8 หรือใหม่กว่า ติดตั้งแล้ว.  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse เพื่อความสะดวกในการเขียนโค้ด.  
- **Maven** ตั้งค่าใน IDE ของคุณ (ไม่บังคับแต่แนะนำ).  
- มีความคุ้นเคยพื้นฐานกับ Java และไลบรารีภายนอก.

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### วิธีตั้งค่า GroupDocs.Metadata สำหรับ Java?
เพิ่ม repository ของ GroupDocs และ dependency ลงใน `pom.xml` ของคุณ ขั้นตอนเดียวนี้ทำให้ API ทั้งหมดพร้อมใช้งานในโปรเจกต์ของคุณ.

```xml
<!-- Maven repository -->
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<!-- GroupDocs.Metadata dependency -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

`GroupDocs.Metadata` JAR จะถูกดึงมาโดยอัตโนมัติระหว่างการสร้างด้วย Maven.

### ดาวน์โหลดโดยตรง (ไม่มี Maven)
หากคุณไม่ต้องการใช้ Maven ให้ดาวน์โหลด JAR ล่าสุดจาก [การปล่อย GroupDocs.Metadata สำหรับ Java](https://releases.groupdocs.com/metadata/java/). วาง JAR ไว้ใน classpath ของคุณและพร้อมใช้งาน.

### ภาพรวมการให้ลิขสิทธิ์
- **Free trial** – การเข้าถึงคุณสมบัติไม่จำกัดสำหรับการประเมิน; ไม่มี watermark.  
- **Temporary license** – เหมาะสำหรับการพัฒนาและการทดสอบอัตโนมัติ.  
- **Full license** – จำเป็นสำหรับการใช้งานเชิงพาณิชย์และเพื่อเปิดใช้งานการสนับสนุนระดับพรีเมียม.

### การเริ่มต้นพื้นฐาน
คลาส `Metadata` เป็นจุดเริ่มต้นที่โหลดไฟล์และให้ตัวเข้าถึงเฉพาะรูปแบบ ด้านล่างเป็นโค้ดขั้นต่ำที่จำเป็นสำหรับการเปิดไฟล์ ASF.

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## วิธีดึงคุณสมบัติพื้นฐานของ ASF metadata
โหลดไฟล์ ASF และดึงคุณสมบัติระดับสูงเช่นวันที่สร้าง, ตัวระบุไฟล์, และแฟล็กระดับโลก ซึ่งจะให้ข้อมูลทันทีว่าแอสเซ็ตถูกสร้างเมื่อใดและถูกตั้งค่าอย่างไรสำหรับการเล่น.

```java
// Load the ASF file
AsfPackage asf = new AsfPackage("sample.asf");

// Retrieve basic properties
Date creationDate = asf.getCreationDate();
String fileId = asf.getFileId();
int flags = asf.getFlags();
```

*ทำไมจึงสำคัญ*: การรู้วันที่สร้างช่วยในการควบคุมเวอร์ชัน, ส่วนไฟล์ ID จะระบุตัวแอสเซ็ตอย่างเฉพาะเจาะจงในระบบกระจาย.

## วิธีแสดงข้อมูล ASF codec
คอลเลกชัน `AsfCodecInfo` แสดงรายการ codec แต่ละตัวที่ใช้ในสตรีม audio และ video เมธอด `getCodecs()` จะคืนค่าอ็อบเจกต์ที่เปิดเผยชื่อ codec, ประเภท, และ bitrate การเข้าใจการใช้ codec มีความสำคัญต่อการทดสอบความเข้ากันได้, การตัดสินใจว่าต้องทำการแปลงรหัสหรือไม่, และเพื่อให้แน่ใจว่าอุปกรณ์เป้าหมายสามารถถอดรหัสสตรีมได้โดยไม่มีข้อผิดพลาด.

```java
// Get codec collection
List<AsfCodecInfo> codecs = asf.getCodecs();

for (AsfCodecInfo codec : codecs) {
    System.out.println("Codec name: " + codec.getName());
    System.out.println("Codec type: " + codec.getType());
}
```

*ทำไมจึงสำคัญ*: รายละเอียด codec ช่วยให้คุณตรวจสอบว่าอุปกรณ์เป้าหมายรองรับรูปแบบที่ต้องการหรือไม่, ป้องกันความล้มเหลวในการเล่นในสภาพแวดล้อมการผลิต.

## วิธีแสดง metadata descriptors
Descriptor ให้บริบทที่มนุษย์อ่านได้ เช่น ภาษา, ชื่อเดิม, และหมายเลขสตรีม ใช้เมธอด `getDescriptors()` เพื่อดึงรายการอ็อบเจกต์ `AsfDescriptor` แต่ละอ็อบเจกต์มีคีย์, ค่า, และแท็กภาษา (ถ้ามี) ข้อมูลนี้ช่วยเสริมดัชนีการค้นหา, ปรับปรุงการแสดงผล UI, และช่วยในการจัดระเบียบห้องสมุดหลายภาษา.

```java
// Retrieve descriptor collection
List<AsfDescriptor> descriptors = asf.getDescriptors();

for (AsfDescriptor descriptor : descriptors) {
    System.out.println("Language: " + descriptor.getLanguage());
    System.out.println("Original title: " + descriptor.getOriginalTitle());
}
```

*ทำไมจึงสำคัญ*: Descriptor ให้ข้อมูลภาษาของซับไตเติลหรือชื่อไฟล์ต้นฉบับ ซึ่งมีคุณค่าเมื่อจัดระเบียบห้องสมุดสื่อหลายภาษา.

## วิธีแสดงคุณสมบัติพื้นฐานของสตรีม
คุณสมบัติพื้นฐานของสตรีมเปิดเผย bitrate, เวลา, และภาษาแต่ละสตรีม ทำให้สามารถวิเคราะห์คุณภาพอย่างละเอียด เมธอด `getStreams()` คืนค่าอ็อบเจกต์ `AsfStream`; แต่ละสตรีมมีคุณสมบัติเช่น `bitrate`, `duration`, และ `language`. การตรวจสอบค่าต่าง ๆ นี้ช่วยประเมินว่าไฟล์ตรงตามเกณฑ์คุณภาพก่อนการแจกจ่ายหรือการเก็บถาวรหรือไม่.

```java
// Access base streams
List<AsfBaseStream> streams = asf.getBaseStreams();

for (AsfBaseStream stream : streams) {
    System.out.println("Bitrate: " + stream.getBitrate());
    System.out.println("Duration: " + stream.getDuration());
    System.out.println("Language: " + stream.getLanguage());
}
```

*ทำไมจึงสำคัญ*: เมตริกระดับสตรีมช่วยให้คุณประเมินว่าไฟล์ตรงตามเกณฑ์คุณภาพก่อนการแจกจ่ายหรือการเก็บถาวรหรือไม่.

## ปัญหาทั่วไป & การแก้ไขข้อผิดพลาด

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| `NullPointerException` เมื่อเรียก `getAsfPackage()` | เส้นทางไฟล์ไม่ถูกต้องหรือไฟล์ไม่ใช่คอนเทนเนอร์ ASF ที่ถูกต้อง. | ตรวจสอบเส้นทางและให้แน่ใจว่าไฟล์เป็นไฟล์ ASF ที่ถูกต้อง. |
| ไม่มีข้อมูล codec แสดงผล | ไฟล์ ASF ใช้ codec ที่เป็นกรรมสิทธิ์ซึ่งไม่รองรับโดยเวอร์ชันไลบรารีปัจจุบัน. | อัปเดต GroupDocs.Metadata ไปยังรุ่นล่าสุดหรือพัฒนา parser codec แบบกำหนดเอง. |
| รายการ descriptor ว่าง | ไฟล์ไม่มี descriptor ฝังอยู่ (เช่น ถูกลบระหว่างการเข้ารหัส). | ใช้ไฟล์ต้นทางที่มี metadata หรือทำการเข้ารหัสใหม่โดยเปิดการรักษา metadata. |
| ประสิทธิภาพช้าลงกับไฟล์ >2 GB | ขนาดบัฟเฟอร์เริ่มต้นเล็กเกินไปสำหรับสตรีมขนาดใหญ่. | เพิ่มขนาดบัฟเฟอร์โดยใช้ `MetadataLoadOptions.setBufferSize()` ก่อนการโหลด. |

## คำถามที่พบบ่อย

**Q: ฉันสามารถดึง metadata จากรูปแบบวิดีโออื่นด้วยไลบรารีเดียวกันได้หรือไม่?**  
A: ใช่, GroupDocs.Metadata รองรับ MP4, MKV, AVI, MOV และอื่น ๆ อีกมากมาย เพียงสร้างอินสแตนซ์ของคลาสแพ็กเกจที่สอดคล้องกับรูปแบบที่คุณต้องการ.

**Q: สามารถแก้ไข ASF metadata หลังจากดึงข้อมูลได้หรือไม่?**  
A: แน่นอน. ไลบรารีมีเมธอด setter สำหรับคุณสมบัติจำนวนมาก ทำให้คุณแก้ไขค่าและบันทึกไฟล์กลับไปยังดิสก์ได้.

**Q: จำเป็นต้องใช้ JVM 64‑bit สำหรับไฟล์ ASF ขนาดใหญ่หรือไม่?**  
A: ไม่จำเป็นอย่างเคร่งครัด, แต่ JVM 64‑bit ให้ heap ขนาดใหญ่ขึ้น ซึ่งเป็นประโยชน์เมื่อประมวลผลไฟล์ที่ใหญ่กว่า 2 GB.

**Q: การให้ลิขสิทธิ์มีผลต่อการใช้รุ่นทดลองอย่างไร?**  
A: ไลเซนส์ทดลองลบข้อจำกัดการทำงานแต่เพิ่ม watermark ในการส่งออกบางประเภท. สำหรับการใช้งานในสภาพแวดล้อมการผลิตโดยไม่มีข้อจำกัด, ควรซื้อไลเซนส์เต็ม.

**Q: ฉันสามารถรันโค้ดนี้บนอุปกรณ์ Android ได้หรือไม่?**  
A: GroupDocs.Metadata ถูกสร้างสำหรับ Java SE. สำหรับ Android ให้ใช้เวอร์ชัน .NET ร่วมกับ Xamarin หรือ wrapper ที่เข้ากันได้.

## สรุป
โดยทำตามคู่มือนี้ คุณจะรู้ **วิธีดึง asf metadata ใน Java** ด้วย GroupDocs.Metadata แล้ว คุณสามารถอ่านคุณสมบัติพื้นฐาน, แยกรายการ codec, ดึง descriptor รายละเอียด, และตรวจสอบคุณลักษณะระดับสตรีม—ให้คุณมองเห็นสื่อของคุณได้อย่างครบถ้วน ขั้นตอนต่อไปคือการฝังการดึงข้อมูลนี้เข้าไปใน pipeline การประมวลผลแบบแบตช์, สร้างที่เก็บ metadata ที่ค้นหาได้, หรือขยายโค้ดเพื่อแก้ไขและบันทึกไฟล์ ASF ใหม่.

---

**อัปเดตล่าสุด:** 2026-09-02  
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

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

## บทแนะนำที่เกี่ยวข้อง

- [ดึงข้อมูล wav metadata ด้วย Java ด้วย GroupDocs.Metadata – คู่มือครบถ้วน](/metadata/java/audio-video-formats/extract-wav-metadata-groupdocs-java/)
- [ดึงข้อมูลวิดีโอ metadata ด้วย Java โดยใช้ GroupDocs.Metadata](/metadata/java/audio-video-formats/mastering-avi-metadata-handling-groupdocs-java/)
- [เชี่ยวชาญการดึง Metadata ของ Java ด้วย GroupDocs.Metadata: คู่มือครบถ้วนสำหรับนักพัฒนา](/metadata/java/working-with-metadata/java-metadata-extraction-groupdocs-metadata/)