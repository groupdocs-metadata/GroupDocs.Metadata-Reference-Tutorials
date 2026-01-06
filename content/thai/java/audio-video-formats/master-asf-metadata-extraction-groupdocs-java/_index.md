---
date: '2025-12-26'
description: เรียนรู้วิธีสกัดเมตาดาต้า ASF ด้วย GroupDocs.Metadata สำหรับ Java คู่มือนี้ครอบคลุมการตั้งค่า
  การอ่านคุณสมบัติ และการเข้าถึงข้อมูลของโค้ดเดค
keywords:
- ASF Metadata Extraction
- GroupDocs.Metadata for Java
- Java Media Management
title: วิธีดึงข้อมูลเมตา ASF ด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# ดึงข้อมูลเมตาดาต้า ASF ด้วย GroupDocs.Metadata สำหรับ Java

**คำนำ**

ในยุคดิจิทัลปัจจุบัน การจัดการเนื้อหามัลติมีเดียอย่างมีประสิทธิภาพเป็นสิ่งสำคัญ หากคุณต้องการ **extract ASF metadata** จากไฟล์สื่อของคุณ การทำด้วยตนเองอาจใช้เวลานานและเสี่ยงต่อข้อผิดพลาด บทแนะนำนี้จะพาคุณผ่านการใช้ **GroupDocs.Metadata for Java** เพื่ออ่านและแสดงคุณสมบัติต่าง ๆ ของ ASF อย่างครบถ้วน ช่วยให้คุณจัดระเบียบ ค้นหา และประมวลผลสินทรัพย์ของคุณได้อย่างมั่นใจ

### สิ่งที่คุณจะได้เรียนรู้
- วิธีตั้งค่า GroupDocs.Metadata ในโครงการ Java  
- วิธี **extract ASF metadata** เช่น วันที่สร้าง ไฟล์ ID และแฟล็ก  
- วิธีอ่านข้อมูล codec ที่ฝังอยู่ในไฟล์ ASF  
- วิธีแสดงรายละเอียดของตัวอธิบายเมตาดาต้าและคุณสมบัติของสตรีมพื้นฐาน  

มาเริ่มต้นด้วยข้อกำหนดเบื้องต้นกันเลย

## คำตอบด่วน
- **What does “extract ASF metadata” mean?** หมายถึงการอ่านข้อมูลที่ฝังอยู่ (เช่น เวลา, codec, ตัวอธิบาย) จากไฟล์ ASF อย่างโปรแกรมเมติก  
- **Which library is required?** GroupDocs.Metadata for Java (เวอร์ชัน 24.12 หรือใหม่กว่า)  
- **Do I need a license?** การทดลองใช้ฟรีหรือไลเซนส์ชั่วคราวทำงานได้สำหรับการพัฒนา; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง  
- **What Java version is supported?** JDK 8 หรือสูงกว่า  
- **Can I use Maven?** ใช่ – Maven เป็นตัวจัดการ dependencies ที่แนะนำ  

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK)** 8 หรือใหม่กว่า ติดตั้งแล้ว  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse เพื่อการเขียนโค้ดที่สะดวก  
- **Maven** ตั้งค่าใน IDE ของคุณ (ไม่บังคับแต่แนะนำ)  
- ความคุ้นเคยพื้นฐานกับ Java และไลบรารีภายนอก  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### การติดตั้งด้วย Maven

เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

หากคุณไม่ต้องการใช้ Maven ให้ดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### ภาพรวมการให้ลิขสิทธิ์

- **Free Trial** – มีให้บนเว็บไซต์ GroupDocs สำหรับการประเมิน  
- **Temporary License** – ให้คุณสำรวจคุณสมบัติทั้งหมดโดยไม่มีข้อจำกัดในระหว่างการพัฒนา  
- **Full License** – จำเป็นสำหรับการใช้งานเชิงพาณิชย์หรือการผลิต  

### การเริ่มต้นพื้นฐาน

ต่อไปนี้เป็นโค้ดขั้นต่ำที่จำเป็นเพื่อเปิดไฟล์ ASF ด้วย GroupDocs.Metadata:

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

## ASF Metadata คืออะไร?

ASF (Advanced Systems Format) เป็นรูปแบบสตรีมของ Microsoft ที่เก็บเสียง, วิดีโอ, และเมตาดาต้าไว้ในคอนเทนเนอร์เดียว เมตาดาต้ารวมถึงเวลาสร้าง, รายละเอียด codec, ตัวอธิบายสตรีม, และอื่น ๆ โดยการ **extract ASF metadata** คุณจะได้ข้อมูลเชิงโปรแกรมเกี่ยวกับที่มาของไฟล์, พารามิเตอร์การเข้ารหัส, และคำอธิบายเนื้อหา—ซึ่งจำเป็นสำหรับห้องสมุดสื่อ, กระบวนการแปลงรหัส, และการตรวจสอบความสอดคล้อง  

## ทำไมต้องดึง ASF Metadata ด้วย GroupDocs.Metadata?

- **Zero‑code parsing** – ไม่จำเป็นต้องเขียนตัวแยกวิเคราะห์ ASF ระดับล่าง  
- **Rich object model** – เข้าถึงคุณสมบัติ, codec, ตัวอธิบาย, และรายละเอียดสตรีมผ่านคลาส Java ที่เข้าใจง่าย  
- **Cross‑platform** – ทำงานบนระบบปฏิบัติการใด ๆ ที่รองรับ Java  
- **License flexibility** – เริ่มต้นด้วยการทดลองและขยายเป็นไลเซนส์เต็มตามความต้องการ  

## คู่มือการใช้งาน

ในส่วนต่อไปนี้ เราจะอธิบายโค้ดตัวอย่างที่แสดงวิธี **extract ASF metadata** ทีละขั้นตอน

### การอ่านคุณสมบัติพื้นฐานของ ASF Metadata

**Overview** – ดึงข้อมูลพื้นฐานเช่น วันที่สร้าง, ไฟล์ ID, และแฟล็ก

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

*ทำไมจึงสำคัญ*: การรู้วันที่สร้างช่วยในการควบคุมเวอร์ชัน, ส่วนไฟล์ ID ระบุสินทรัพย์อย่างเฉพาะเจาะจงในระบบต่าง ๆ  

### การแสดงข้อมูล Codec ของ ASF

**Overview** – แสดงรายการ codec ที่ใช้สำหรับสตรีมเสียงและวิดีโอ

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

*ทำไมจึงสำคัญ*: รายละเอียด codec มีความสำคัญเมื่อตรวจสอบความเข้ากันได้กับอุปกรณ์เล่นหรือเมื่อตัดสินใจว่าจะทำการแปลงรหัสหรือไม่  

### การแสดงตัวอธิบายเมตาดาต้า

**Overview** – ดึงตัวอธิบายละเอียด เช่น ภาษา, หมายเลขสตรีม, และชื่อเรื่องต้นฉบับ

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

*ทำไมจึงสำคัญ*: ตัวอธิบายให้บริบทเช่นภาษาของคำบรรยายหรือชื่อไฟล์ต้นฉบับ ซึ่งมีคุณค่าสำหรับการจัดทำแคตาล็อก  

### การแสดงคุณสมบัติของสตรีมพื้นฐาน

**Overview** – เข้าถึงบิตเรต, เวลา, และข้อมูลภาษา สำหรับแต่ละสตรีมพื้นฐาน

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

*ทำไมจึงสำคัญ*: คุณสมบัติของสตรีมช่วยประเมินคุณภาพ (บิตเรต) และซิงโครไนซ์เสียง/วิดีโอระหว่างการเล่นหรือการแก้ไข  

## ปัญหาทั่วไปและการแก้ไข

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|-------------------|----------|
| `NullPointerException` when calling `getAsfPackage()` | เส้นทางไฟล์ไม่ถูกต้องหรือไฟล์ไม่ใช่คอนเทนเนอร์ ASF ที่ถูกต้อง | ตรวจสอบเส้นทางและยืนยันว่าไฟล์เป็นไฟล์ ASF ที่ถูกต้อง |
| No codec information displayed | ไฟล์ ASF ใช้ codec ที่เป็นกรรมสิทธิ์ซึ่งไม่รองรับโดยเวอร์ชันของไลบรารี | อัปเดต GroupDocs.Metadata เป็นเวอร์ชันล่าสุดหรือใช้ตัวแยกวิเคราะห์ codec แบบกำหนดเอง |
| Empty descriptor list | ไฟล์ไม่มีตัวอธิบายเมตาดาต้า (เช่น ถูกลบระหว่างการเข้ารหัส) | ใช้ไฟล์ต้นฉบับที่มีเมตาดาต้าฝังอยู่หรือทำการเข้ารหัสใหม่โดยคงเมตาดาต้าไว้ |

## คำถามที่พบบ่อย

**Q: ฉันสามารถดึงเมตาดาต้าจากรูปแบบวิดีโออื่นด้วยไลบรารีเดียวกันได้หรือไม่?**  
A: ได้, GroupDocs.Metadata รองรับ MP4, MKV, AVI และอื่น ๆ อีกมาก. เพียงสร้างอินสแตนซ์ของคลาสแพคเกจที่เหมาะสม.

**Q: สามารถแก้ไขเมตาดาต้า ASF หลังจากการดึงข้อมูลได้หรือไม่?**  
A: แน่นอน. ไลบรารีมีเมธอด setter สำหรับคุณสมบัติจำนวนมาก ทำให้คุณสามารถแก้ไขและบันทึกไฟล์ได้.

**Q: จำเป็นต้องใช้ JVM 64‑bit สำหรับไฟล์ ASF ขนาดใหญ่หรือไม่?**  
A: ไม่จำเป็นเสมอไป, แต่ JVM 64‑bit จะให้พื้นที่ heap มากขึ้น ซึ่งช่วยเมื่อประมวลผลไฟล์สื่อขนาดใหญ่มาก.

**Q: การให้ลิขสิทธิ์มีผลต่อการใช้รุ่นทดลองอย่างไร?**  
A: ไลเซนส์ทดลองจะลบข้อจำกัดการทำงานทั้งหมด แต่จะเพิ่มลายน้ำในผลลัพธ์บางส่วน. สำหรับการใช้งานจริง ควรซื้อไลเซนส์เต็ม.

**Q: สามารถรันโค้ดนี้บน Android ได้หรือไม่?**  
A: GroupDocs.Metadata ถูกสร้างสำหรับ Java SE; สำหรับ Android คุณต้องใช้เวอร์ชัน .NET หรือ wrapper ที่เข้ากันได้.

## สรุป

โดยการทำตามคู่มือนี้ คุณจะรู้วิธี **extract ASF metadata** ด้วย GroupDocs.Metadata สำหรับ Java คุณสามารถอ่านคุณสมบัติพื้นฐาน, รายละเอียด codec, ตัวอธิบายละเอียด, และคุณสมบัติของสตรีมได้ทั้งหมด ซึ่งให้การมองเห็นเต็มรูปแบบของสินทรัพย์สื่อของคุณ ขั้นตอนต่อไปอาจรวมถึงการผสานการดึงข้อมูลนี้เข้าสู่กระบวนการประมวลผลแบบแบตช์, การสร้างฐานข้อมูลเมตาดาต้าที่ค้นหาได้, หรือการขยายโค้ดเพื่อแก้ไขและบันทึกไฟล์ ASF ใหม่

---

**อัปเดตล่าสุด:** 2025-12-26  
**ทดสอบกับ:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs