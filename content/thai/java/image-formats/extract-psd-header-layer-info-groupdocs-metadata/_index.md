---
date: '2026-04-26'
description: เรียนรู้วิธีการดึงชั้น PSD และข้อมูลส่วนหัวด้วย GroupDocs.Metadata สำหรับ
  Java คู่มือนี้ครอบคลุมการตั้งค่า ตัวอย่างโค้ด และเคล็ดลับการประมวลผลแบบกลุ่ม
keywords:
- extract psd layers
- how to extract psd
- groupdocs metadata java
title: ดึงเลเยอร์ PSD ด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/
weight: 1
---

# สกัดชั้น PSD ด้วย GroupDocs.Metadata สำหรับ Java

ในสายการออกแบบสมัยใหม่ การสามารถ **สกัดชั้น PSD** อย่างอัตโนมัติช่วยประหยัดเวลามนุษย์เป็นจำนวนมาก ไม่ว่าคุณจะต้องตรวจสอบไลบรารีการออกแบบขนาดใหญ่, ผสานรวมสินทรัพย์ PSD เข้ากับ CMS, หรือสร้างรายงานการใช้ชั้น, GroupDocs.Metadata สำหรับ Java ให้ API ที่สะอาดและปลอดภัยต่อชนิดเพื่อดึงรายละเอียดส่วนหัวและข้อมูลชั้นแต่ละชั้นจากไฟล์ Photoshop

## คำตอบสั้น
- **ฉันสามารถสกัดอะไรได้บ้าง?** ฟิลด์ส่วนหัว PSD (โหมดสี, จำนวนช่อง, ฯลฯ) และเมตาดาต้าชั้นเต็ม (ชื่อ, ขนาด, การมองเห็น).  
- **ฉันต้องการใบอนุญาตหรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการประเมิน; จำเป็นต้องมีใบอนุญาตถาวรสำหรับการใช้งานจริง.  
- **ฉันสามารถประมวลผลหลายไฟล์พร้อมกันได้หรือไม่?** ได้ – ผสานการเรียก API กับ Java streams เพื่อประมวลผลไฟล์ PSD เป็นชุด.  
- **เวอร์ชัน Java ที่รองรับคืออะไร?** Java 8 + (ไลบรารีนี้สร้างสำหรับ JDK สมัยใหม่).  
- **Maven เป็นวิธีเดียวในการติดตั้งหรือไม่?** ไม่ – คุณยังสามารถดาวน์โหลดไฟล์ JAR โดยตรงจากหน้าปล่อยของ GroupDocs.

## อะไรคือ “สกัดชั้น PSD”?
การสกัดชั้น PSD หมายถึงการอ่านคุณลักษณะของแต่ละชั้นโดยอัตโนมัติ—เช่น ชื่อ, มิติ, ความลึกบิต, และแฟล็กการมองเห็น—โดยไม่ต้องเปิด Photoshop. สิ่งนี้ทำให้สามารถทำงานอัตโนมัติ, การทำดัชนีสินทรัพย์, และการวิเคราะห์แบบรวมได้.

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
- **ไม่มีการพึ่งพา Photoshop การติดตั้ง:** ไลบรารีนี้แยกวิเคราะห์ไฟล์ PSD โดยตรง.  
- **โมเดลอ็อบเจกต์ที่สมบูรณ์:** เข้าถึงข้อมูลส่วนหัวและชั้นผ่าน getter ที่เข้าใจง่าย.  
- **เน้นประสิทธิภาพ:** ทำงานกับไฟล์ขนาดใหญ่เมื่อคุณปิดอ็อบเจกต์ `Metadata` อย่างทันท่วงที.  
- **พร้อมสำหรับการประมวลผลเป็นชุด:** ผสานกับ parallel streams ของ Java เพื่อการประมวลผลความเร็วสูง.

## ข้อกำหนดเบื้องต้น
- JDK 8 หรือใหม่กว่า ติดตั้งแล้ว.  
- IDE (IntelliJ IDEA, Eclipse หรือ VS Code) สำหรับเขียนและรันโค้ด Java.  
- Maven (ไม่บังคับ) หากคุณต้องการการจัดการ dependencies.  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### การตั้งค่า Maven
หากคุณจัดการ dependencies ด้วย Maven ให้เพิ่ม repository และ dependency ลงใน `pom.xml` ของคุณ:

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
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดของ GroupDocs.Metadata สำหรับ Java จาก [การปล่อย GroupDocs Metadata](https://releases.groupdocs.com/metadata/java/).

#### ขั้นตอนการรับใบอนุญาต
- **ทดลองใช้ฟรี:** เริ่มต้นด้วยการทดลองเพื่อสำรวจ API.  
- **ใบอนุญาตชั่วคราว:** รับคีย์ชั่วคราวสำหรับการประเมินต่อเนื่อง.  
- **ซื้อ:** รับใบอนุญาตเต็มรูปแบบสำหรับการใช้งานผลิตภัณฑ์โดยไม่มีข้อจำกัด.

### การเริ่มต้นพื้นฐาน
เมื่อไลบรารีอยู่ใน classpath ของคุณแล้ว คุณสามารถสร้างอินสแตนซ์ `Metadata` และชี้ไปที่ไฟล์ PSD:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class SetupGroupDocs {
    public static void main(String[] args) {
        // Basic initialization of Metadata object with a PSD file path
        try (Metadata metadata = new Metadata("path/to/your/file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            System.out.println("Setup complete! Ready to explore PSD features.");
        }
    }
}
```

## คู่มือการใช้งาน

### การอ่านข้อมูลส่วนหัว PSD

#### ขั้นตอนที่ 1: เปิดไฟล์ PSD
แรกสุด เปิดไฟล์ด้วยคลาส `Metadata`:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ReadPsdHeader {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/psd_file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
```

#### ขั้นตอนที่ 2: สกัดข้อมูลส่วนหัว
ต่อไปดึงฟิลด์ส่วนหัวที่คุณต้องการ:

```java
            System.out.println(root.getPsdPackage().getChannelCount()); // Number of channels in the image
            System.out.println(root.getPsdPackage().getColorMode());    // Color mode (e.g., RGB, Grayscale)
            System.out.println(root.getPsdPackage().getCompression());  // Compression method used
            System.out.println(root.getPsdPackage().getPhotoshopVersion()); // Photoshop version metadata
        }
    }
}
```

**คำอธิบายของ getter หลัก**
- `getChannelCount()` – จำนวนช่องภาพทั้งหมด (RGB, alpha, ฯลฯ).  
- `getColorMode()` – พื้นที่สีเช่น RGB หรือ CMYK.  
- `getCompression()` – อัลกอริทึมที่ใช้ (เช่น RLE, ZIP).  
- `getPhotoshopVersion()` – เวอร์ชัน Photoshop ที่สร้างไฟล์นี้.

### การสกัดข้อมูลชั้น PSD

#### ขั้นตอนที่ 1: เปิดไฟล์ PSD (อีกครั้งเพื่อความชัดเจน)
เราจะใช้รูปแบบเดียวกันเพื่อเข้าถึงข้อมูลชั้น:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdLayer;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractPsdLayers {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/psd_file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
```

#### ขั้นตอนที่ 2: วนลูปผ่านชั้น
วนลูปแต่ละ `PsdLayer` และพิมพ์คุณสมบัติของมัน:

```java
            for (PsdLayer layer : root.getPsdPackage().getLayers()) {
                System.out.println(layer.getName());         // Layer name
                System.out.println(layer.getBitsPerPixel());  // Bits per pixel of the layer
                System.out.println(layer.getChannelCount()); // Number of channels in the layer
                System.out.println(layer.getFlags());        // Flags set for the layer (e.g., visible, locked)
                System.out.println(layer.getHeight());       // Layer height
                System.out.println(layer.getWidth());        // Layer width
            }
        }
    }
}
```

**getter ชั้นสำคัญ**
- `getName()` – ป้ายชื่อชั้นที่อ่านได้โดยมนุษย์.  
- `getBitsPerPixel()` – ความลึกสีของชั้น.  
- `getChannelCount()` – จำนวนช่องที่ชั้นนี้มี.  
- `getFlags()` – แฟล็กการมองเห็น, การป้องกัน, และบิตสถานะอื่น ๆ.  
- `getHeight()` / `getWidth()` – มิติพิกเซลของแคนวาสชั้น.

## การประยุกต์ใช้งานจริง
ต่อไปนี้คือห้ากรณีการใช้งานจริงที่ **สกัดชั้น PSD** มีประโยชน์:

1. **การวิเคราะห์ไฟล์อัตโนมัติ** – สแกนคลังการออกแบบ, จัดประเภทไฟล์ตามโหมดสีหรือจำนวนชั้น, และสร้างรายงานสินค้าคงคลัง.  
2. **การจัดการสินทรัพย์การออกแบบ** – เก็บเมตาดาต้าชั้นในฐานข้อมูลเพื่อสนับสนุนการค้นหาและการนำกลับมาใช้ใหม่ในโครงการต่าง ๆ.  
3. **การผสานรวมกับ CMS** – ดึงชื่อและมิติของชั้นเพื่อสร้างภาพย่อหรือแกลเลอรีตัวอย่างโดยอัตโนมัติ.  
4. **การตรวจสอบการควบคุมเวอร์ชัน** – ติดตามการเปลี่ยนแปลงเวอร์ชัน Photoshop ในสินทรัพย์เพื่อการปฏิบัติตามและกลยุทธ์การย้อนกลับ.  
5. **เครื่องมือรายงานแบบกำหนดเอง** – สร้างแดชบอร์ดที่แสดงการกระจายชั้น (เช่น จำนวนไฟล์ที่มีชั้นปรับค่า).

## ข้อควรพิจารณาด้านประสิทธิภาพ
เมื่อจัดการกับคอลเลกชัน PSD ขนาดกิกะไบต์ ให้คำนึงถึงเคล็ดลับต่อไปนี้:

- **เพิ่มประสิทธิภาพการใช้หน่วยความจำ:** ใช้ try‑with‑resources (`try (Metadata …)`) เสมอเพื่อปิดอ็อบเจกต์อย่างทันท่วงที.  
- **การประมวลผลเป็นชุด:** ใช้ Java streams หรือ executor services เพื่อประมวลผลไฟล์แบบขนาน ลดระยะเวลาการทำงานโดยรวม.  
- **การทำโปรไฟล์:** เครื่องมือเช่น VisualVM หรือ YourKit สามารถเปิดเผยการเพิ่มขึ้นของหน่วยความจำ; ให้ความสนใจที่วงจรชีวิตของ `Metadata`.

## ปัญหาและวิธีแก้ไขทั่วไป
| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| `java.lang.NoClassDefFoundError` for `org.apache.commons.io.IOUtils` | การพึ่งพาแบบทรานซิทีฟที่หายไป | เพิ่ม Apache Commons IO ไปยัง `dependencies` ของ Maven ของคุณ. |
| จำนวนชั้นคืนค่าเป็น 0 | ไฟล์เปิดในโหมดอ่านอย่างเดียวพร้อมสิทธิ์จำกัด | ตรวจสอบให้แน่ใจว่าไฟล์ PSD สามารถเข้าถึงได้และไม่เสียหาย. |
| `null` ที่ไม่คาดคิดสำหรับ `getColorMode()` | ใช้เวอร์ชัน PSD เก่าที่ไม่ได้รับการสนับสนุนเต็มที่ | อัปเกรดเป็น GroupDocs.Metadata รุ่นล่าสุด (24.12) ซึ่งเพิ่มการสนับสนุนรุ่นเก่า. |

## คำถามที่พบบ่อย

**Q:** ฉันจะประมวลผลเป็นชุดหลายสิบไฟล์ PSD เพื่อสกัดชั้นได้อย่างไร?  
**A:** ผสานการเรียก `Metadata` ภายในสตรีม `Files.list(Paths.get("folder"))` และรวบรวมผลลัพธ์เป็น CSV หรือฐานข้อมูล.

**Q:** ฉันสามารถสกัดชั้นที่ซ่อนหรือถูกล็อกได้หรือไม่?  
**A:** ได้. เมธอด `getFlags()` แสดงสถานะการมองเห็นและการล็อก, ทำให้คุณสามารถกรองหรือรวมชั้นเหล่านั้นตามต้องการ.

**Q:** ไลบรารีรองรับไฟล์ PSD ที่ใหญ่กว่า 2 GB หรือไม่?  
**A:** API ทำงานกับไฟล์จนถึงขีดจำกัดหน่วยความจำที่ JVM สามารถเข้าถึง; สำหรับไฟล์ที่ใหญ่มาก ให้เพิ่ม heap (`-Xmx`) และประมวลผลเป็นชิ้นส่วน.

**Q:** มีวิธีส่งออกภาพย่อของชั้นหรือไม่?  
**A:** แม้ GroupDocs.Metadata จะเน้นที่เมตาดาต้า, คุณสามารถดึงข้อมูลพิกเซลดิบผ่าน API `PsdLayer` แล้วใช้ไลบรารีภาพ (เช่น TwelveMonkeys) เพื่อสร้างภาพย่อ.

**Q:** ฉันต้องการใบอนุญาตประเภทใดสำหรับการใช้งานเชิงพาณิชย์?  
**A:** จำเป็นต้องมีใบอนุญาต GroupDocs.Metadata แบบชำระเงินสำหรับการใช้งานในสภาพแวดล้อมการผลิต. คีย์ทดลองใช้ทำงานสำหรับการพัฒนาและการทดสอบเท่านั้น.

## สรุป
ตอนนี้คุณมีตัวอย่างครบวงจรที่มั่นคงเกี่ยวกับวิธี **สกัดชั้น PSD** และข้อมูลส่วนหัวโดยใช้ GroupDocs.Metadata สำหรับ Java. ด้วยการผสานส่วนโค้ดเหล่านี้เข้ากับกระบวนการของคุณ คุณสามารถทำการวิเคราะห์สินทรัพย์อัตโนมัติ, เพิ่มประสิทธิภาพการทำงาน, และรักษาคลังการออกแบบที่เป็นระเบียบ.

**ขั้นตอนต่อไป**
- ทดลองใช้ API เพื่อดึงคุณสมบัติเพิ่มเติมของ PSD (เช่น เนื้อหาชั้นข้อความ).  
- ผสานการสกัดเมตาดาต้านี้กับฐานข้อมูลหรือ Elasticsearch เพื่อทำให้สินทรัพย์การออกแบบสามารถค้นหาได้.  
- สำรวจรูปแบบการประมวลผลเป็นชุดเพื่อจัดการไฟล์หลายพันไฟล์อย่างมีประสิทธิภาพ.

---

**อัปเดตล่าสุด:** 2026-04-26  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12  
**ผู้เขียน:** GroupDocs