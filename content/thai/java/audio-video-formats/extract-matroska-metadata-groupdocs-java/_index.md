---
date: '2025-12-22'
description: เรียนรู้วิธีการดึงเมตาดาต้า mkv ด้วย Java โดยใช้ GroupDocs.Metadata for
  Java ครอบคลุมส่วนหัว EBML, ข้อมูลเซกเมนต์, แท็ก และข้อมูลแทร็ก
keywords:
- extract mkv metadata java
- groupdocs.metadata java
- read matroska file
title: สกัดข้อมูลเมตาดาต้า MKV ด้วย Java – คู่มือการใช้ GroupDocs.Metadata
type: docs
url: /th/java/audio-video-formats/extract-matroska-metadata-groupdocs-java/
weight: 1
---

# ดึงข้อมูลเมตาดาต้า MKV ด้วย Java และ GroupDocs.Metadata

ไฟล์มัลติมีเดียมีอยู่ทั่วทุกที่ และการสามารถอ่านรายละเอียดภายในของไฟล์เหล่านั้นเป็นสิ่งสำคัญสำหรับการจัดการสื่อ การทำแคตาล็อก และการวิเคราะห์ ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีดึงข้อมูลเมตาดาต้า mkv ด้วย Java** โดยใช้ไลบรารีที่ทรงพลังของ GroupDocs.Metadata เราจะอธิบายขั้นตอนการตั้งค่าไลบรารี การดึงหัวข้อ EBML ข้อมูลส่วนของเซกเมนต์ แท็ก และข้อมูลแทร็กจากไฟล์ MKV พร้อมแสดงตัวอย่างสถานการณ์จริงที่ความรู้นี้เป็นประโยชน์

## คำตอบอย่างรวดเร็ว
- **“extract mkv metadata java” หมายถึงอะไร?** เป็นกระบวนการอ่านเมตาดาต้าจากไฟล์ MKV ด้วยโปรแกรมโดยใช้ Java.  
- **ควรใช้ไลบรารีใด?** GroupDocs.Metadata for Java มี API ครบวงจรสำหรับไฟล์ Matroska.  
- **ต้องการไลเซนส์หรือไม่?** สามารถใช้รุ่นทดลองฟรีเพื่อประเมิน; ไลเซนส์จะลบข้อจำกัดการใช้งาน.  
- **สามารถอ่านฟอร์แมตอื่นได้หรือไม่?** ได้, ไลบรารีเดียวกันสนับสนุน MP4, AVI, MP3 และอื่น ๆ อีกมาก  
- **ต้องการการเชื่อมต่ออินเทอร์เน็ตขณะรันหรือไม่?** ไม่, การดึงข้อมูลทั้งหมดทำในเครื่องหลังจากเพิ่มไลบรารีลงในโปรเจคของคุณ  

## Matroska (MKV) Metadata คืออะไร?
Matroska เป็นคอนเทนเนอร์แบบเปิดและยืดหยุ่น เมตาดาต้าของมันประกอบด้วยหัวข้อ EBML (เวอร์ชันไฟล์, ประเภทเอกสาร), รายละเอียดเซกเมนต์ (ระยะเวลา, แอปพลิเคชันการมิกซ์), แท็ก (ชื่อ, คำอธิบาย) และสเปคของแทร็ก (โคเดกเสียง/วิดีโอ, ภาษา) การเข้าถึงข้อมูลนี้ทำให้คุณสามารถสร้างแคตาล็อกสื่อ, ตรวจสอบความสมบูรณ์ของไฟล์, หรือสร้างภาพย่อโดยอัตโนมัติ

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
- **API ครบฟีเจอร์** – จัดการ EBML, เซกเมนต์, แท็ก, และแทร็กโดยไม่ต้องพาร์สระดับต่ำ  
- **ประสิทธิภาพสูง** – ทำงานอย่างมีประสิทธิภาพแม้กับไฟล์ขนาดใหญ่  
- **สนับสนุนหลายฟอร์แมต** – โค้ดเบสเดียวสามารถนำกลับมาใช้กับคอนเทนเนอร์เสียง/วิดีโออื่นได้  
- **การรวม Maven ง่าย** – เพิ่ม dependency เพียงหนึ่งรายการและเริ่มดึงข้อมูล  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Metadata for Java** เวอร์ชัน 24.12 หรือใหม่กว่า.  
- ติดตั้ง Java Development Kit (JDK).  
- Maven (หรือการจัดการ JAR ด้วยตนเอง).  
- ไฟล์ MKV สำหรับทดลอง (วางไว้ใน `YOUR_DOCUMENT_DIRECTORY`).  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java
เพิ่มไลบรารีลงในโปรเจคของคุณโดยใช้ Maven หรือดาวน์โหลด JAR โดยตรง

**Maven:**  
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

**Direct Download:**  
ถ้าคุณไม่ต้องการใช้ Maven, ดาวน์โหลดเวอร์ชันล่าสุดจาก [รุ่นปล่อยของ GroupDocs.Metadata สำหรับ Java](https://releases.groupdocs.com/metadata/java/).

### การรับไลเซนส์
เริ่มต้นด้วยรุ่นทดลองฟรีเพื่อสำรวจฟีเจอร์. สำหรับการใช้งานในผลิตภัณฑ์, ซื้อไลเซนส์หรือรับไลเซนส์ชั่วคราวจาก [GroupDocs](https://purchase.groupdocs.com/temporary-license/) เพื่อยกเลิกข้อจำกัดของรุ่นทดลอง.

### การเริ่มต้นและการตั้งค่าพื้นฐาน
ด้านล่างเป็นโค้ดขั้นต่ำที่จำเป็นสำหรับเปิดไฟล์ MKV ด้วย GroupDocs.Metadata.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class MetadataExtraction {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();
            // Access and manipulate metadata here
        }
    }
}
```

## วิธีดึงข้อมูลเมตาดาต้า mkv ด้วย Java ด้วย GroupDocs.Metadata
ตอนนี้เราจะเจาะลึกแต่ละส่วนของเมตาดาต้าที่คุณสามารถอ่านได้

### การอ่านหัวข้อ EBML ของ Matroska
หัวข้อ EBML เก็บข้อมูลหลักของไฟล์เช่นเวอร์ชันและประเภทเอกสาร.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaEBMLHeader {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            String docType = root.getMatroskaPackage().getEbmlHeader().getDocType();
            String docTypeReadVersion = root.getMatroskaPackage().getEbmlHeader().getDocTypeReadVersion();
            String docTypeVersion = root.getMatroskaPackage().getEbmlHeader().getDocTypeVersion();
            String readVersion = root.getMatroskaPackage().getEbmlHeader().getReadVersion();
            String version = root.getMatroskaPackage().getEbmlHeader().getVersion();

            // Use the extracted header details as needed
        }
    }
}
```

**ประเด็นสำคัญ**
- `getRootPackageGeneric()` ให้จุดเริ่มต้นของแพ็กเกจ Matroska.  
- คุณสมบัติ EBML (`docType`, `version`, ฯลฯ) ช่วยให้คุณตรวจสอบความเข้ากันของไฟล์.

### การอ่านข้อมูลส่วน Segment ของ Matroska
Segment อธิบายไทม์ไลน์สื่อโดยรวมและเครื่องมือที่ใช้สร้าง.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaSegmentInformation {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var segment : root.getMatroskaPackage().getSegments()) {
                String dateUtc = segment.getDateUtc();
                long duration = segment.getDuration();
                String muxingApp = segment.getMuxingApp();
                String segmentFilename = segment.getSegmentFilename();
                String segmentUid = segment.getSegmentUid();
                long timecodeScale = segment.getTimecodeScale();
                String title = segment.getTitle();
                String writingApp = segment.getWritingApp();

                // Process the extracted segment information as needed
            }
        }
    }
}
```

**ประเด็นสำคัญ**
- `getSegments()` คืนค่าคอลเลกชัน; แต่ละ segment สามารถมีชื่อ, ระยะเวลา, และรายละเอียดแอปที่สร้าง.  
- มีประโยชน์สำหรับสร้างเพลย์ลิสต์หรือยืนยันพารามิเตอร์การเข้ารหัส.

### การอ่านเมตาดาต้า Tag ของ Matroska
Tag เก็บข้อมูลที่มนุษย์อ่านได้ เช่น ชื่อ, ศิลปิน, หรือโน๊ตกำหนดเอง.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;
import com.groupdocs.metadata.core.MetadataProperty;

public class ReadMatroskaTagMetadata {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var tag : root.getMatroskaPackage().getTags()) {
                String targetType = tag.getTargetType();
                String targetTypeValue = tag.getTargetTypeValue();
                String tagTrackUid = tag.getTagTrackUid();

                for (MetadataProperty simpleTag : tag.getSimpleTags()) {
                    String name = simpleTag.getName();
                    String value = simpleTag.getValue();

                    // Utilize the extracted tag information as needed
                }
            }
        }
    }
}
```

**ประเด็นสำคัญ**
- Tag ถูกจัดระเบียบตาม `targetType` (เช่น `movie`, `track`).  
- รายการ `simpleTag` เก็บคู่คีย์/ค่า เช่น `TITLE=My Video`.

### การอ่านเมตาดาต้า Track ของ Matroska
Track แทนสตรีมเสียง, วิดีโอ หรือซับไตเติลแต่ละอัน.  
```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaTrackMetadata {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var track : root.getMatroskaPackage().getTracks()) {
                String trackType = track.getType();
                String codecId = track.getCodecId();
                String language = track.getLanguage();
                long duration = track.getDuration();
                
                // Process the extracted track information as needed
            }
        }
    }
}
```

**ประเด็นสำคัญ**
- `track.getType()` บอกว่ามันเป็นวิดีโอ, เสียง, หรือซับไตเติล.  
- `codecId` ช่วยระบุโคเดก (เช่น `V_MPEG4/ISO/AVC`).  
- ข้อมูลนี้สำคัญสำหรับพายป์ไลน์การแปลงรหัสหรือการตรวจสอบคุณภาพ.

## ปัญหาทั่วไปและการแก้ไขข้อผิดพลาด
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| `NullPointerException` เมื่อเข้าถึง `getEbmlHeader()` | เส้นทางไฟล์ไม่ถูกต้องหรือไฟล์ไม่พบ | ตรวจสอบเส้นทางใน `new Metadata("...")` และให้แน่ใจว่าไฟล์มีอยู่. |
| ไม่มี Tag ถูกส่งคืน | ไฟล์ MKV ไม่มีองค์ประกอบ Tag | ใช้ไฟล์สื่อที่มี Tag เมตาดาต้า (เช่น ที่เพิ่มโดย MKVToolNix). |
| การประมวลผลช้าในไฟล์ขนาดใหญ่ | หน่วยความจำ heap ไม่เพียงพอ | เพิ่ม heap ของ JVM (`-Xmx2g` หรือสูงกว่า) หรือประมวลผลไฟล์เป็นชิ้นส่วนถ้าเป็นไปได้. |

## คำถามที่พบบ่อย
**Q: ฉันสามารถดึงเมตาดาต้าจากฟอร์แมตวิดีโออื่นด้วยไลบรารีเดียวกันได้หรือไม่?**  
A: ใช่, GroupDocs.Metadata รองรับ MP4, AVI, MOV และอื่น ๆ อีกมาก. รูปแบบ API คล้ายกัน—เพียงใช้คลาส root package ที่เหมาะสม.

**Q: จำเป็นต้องมีไลเซนส์สำหรับการใช้งานในผลิตภัณฑ์หรือไม่?**  
A: ไลเซนส์จะลบข้อจำกัดของรุ่นทดลองและให้ฟังก์ชันเต็ม. ไลบรารีทำงานในโหมดทดลองเพื่อการประเมิน.

**Q: การดึงข้อมูลทำแบบออฟไลน์หรือไม่?**  
A: แน่นอน. เมื่อ JAR อยู่ใน classpath ของคุณ, การอ่านเมตาดาต้าทั้งหมดจะทำในเครื่องโดยไม่ต้องเรียกเครือข่าย.

**Q: ประสิทธิภาพเป็นอย่างไรกับไฟล์ MKV ขนาดใหญ่มาก (หลาย GB)?**  
A: ไลบรารีสตรีมโครงสร้างคอนเทนเนอร์, ดังนั้นการใช้หน่วยความจำจะค่อนข้างต่ำ, แต่ให้แน่ใจว่า JVM มี heap เพียงพอสำหรับคอลเลกชัน Tag ขนาดใหญ่.

**Q: ฉันสามารถแก้ไขเมตาดาต้าและเขียนกลับไปยังไฟล์ได้หรือไม่?**  
A: GroupDocs.Metadata มุ่งเน้นที่การอ่านเป็นหลัก. ความสามารถในการเขียนจำกัด; ตรวจสอบเอกสาร API ล่าสุดสำหรับการสนับสนุนการเขียนใด ๆ.

## สรุป
ตอนนี้คุณมีคู่มือที่ครบถ้วนและพร้อมใช้งานในผลิตภัณฑ์สำหรับ **การดึงข้อมูลเมตาดาต้า mkv ด้วย Java** ด้วย GroupDocs.Metadata. ด้วยการเข้าถึงหัวข้อ EBML, ข้อมูลเซกเมนต์, แท็ก, และรายละเอียดแทร็ก, คุณสามารถเสริมพลังให้กับแคตาล็อกสื่อ, ทำการตรวจสอบคุณภาพอัตโนมัติ, หรือเพิ่มคุณค่าให้กับบริการสตรีมวิดีโอ. ทดลองใช้โค้ดตัวอย่าง, ปรับให้เข้ากับกระบวนการของคุณ, และสำรวจการสนับสนุนฟอร์แมตที่กว้างขวางของไลบรารีเพื่อโอกาสที่มากขึ้น.

---

**อัปเดตล่าสุด:** 2025-12-22  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs