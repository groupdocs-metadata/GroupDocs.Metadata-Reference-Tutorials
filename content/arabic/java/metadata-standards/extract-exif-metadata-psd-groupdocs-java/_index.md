---
date: '2026-08-10'
description: تعلم كيفية استخراج بيانات EXIF الوصفية من ملفات PSD باستخدام GroupDocs.Metadata
  للغة Java. يغطي هذا الدليل الاستخراج الأساسي، حزم IFD، بيانات GPS، وحالات الاستخدام
  الواقعية.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: تعلم كيفية استخراج بيانات EXIF الوصفية من ملفات PSD باستخدام GroupDocs.Metadata
  للغة Java. دليل خطوة بخطوة، مقتطفات شفرة، ونصائح استكشاف الأخطاء للمطورين.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: كيفية استخراج بيانات EXIF الوصفية من ملفات PSD باستخدام GroupDocs.Metadata
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
title: كيفية استخراج بيانات EXIF الوصفية من ملفات PSD باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# كيفية استخراج بيانات EXIF الوصفية من ملفات PSD باستخدام GroupDocs.Metadata

استخراج **بيانات EXIF الوصفية** من ملفات PSD هو خطوة روتينية ولكن قوية عندما تحتاج إلى تدقيق أصل الصورة، أتمتة وسم الأصول، أو بناء مكتبات وسائط قابلة للبحث. في هذا الدرس ستكتشف **كيفية استخراج EXIF** بسرعة باستخدام GroupDocs.Metadata للغة Java، وتطلع على استدعاءات API الدقيقة، وتتعلم كيفية التعامل مع حزم IFD المتقدمة وإحداثيات GPS. في النهاية ستكون جاهزًا لدمج استخراج البيانات الوصفية في أي سير عمل مبني على Java.

## إجابات سريعة
فئة `Metadata` تمثل ملفًا وتوفر الوصول إلى بياناته الوصفية.

- **ما هو السطر الأول من الشيفرة؟** `Metadata metadata = new Metadata("sample.psd");`
- **ما هي الطريقة التي تُرجع اسم الفنان؟** `metadata.getExif().getArtist();`
- **هل يمكنني قراءة بيانات GPS؟** نعم – استخدم `metadata.getExif().getGpsInfo();`
- **هل أحتاج إلى ترخيص للإنتاج؟** يتطلب ترخيص صالح لـ GroupDocs.Metadata بعد فترة التجربة.
- **إصدار Java المدعوم؟** Java 8 أو أحدث (حتى Java 21).

## ما هي بيانات EXIF الوصفية؟
تخزن بيانات EXIF (Exchangeable Image File Format) الوصفية إعدادات الكاميرا، طوابع زمن الإنشاء، وبيانات الموقع داخل ملفات الصورة. يقرأ GroupDocs.Metadata هذه المعلومات مباشرةً من البنية الثنائية لملفات PSD، ويعرضها عبر API Java نظيف. يتيح ذلك للمطورين استرجاع التفاصيل برمجيًا مثل طراز الكاميرا، زمن التعرض، وإحداثيات GPS دون فحص يدوي.

## لماذا نستخدم GroupDocs.Metadata للغة Java؟
يدعم GroupDocs.Metadata **أكثر من 30 تنسيق ملف** (بما في ذلك PSD، JPEG، PNG، TIFF) ويمكنه معالجة ملفات تصل إلى **2 GB** دون تحميل المستند بالكامل في الذاكرة. تستخرج المكتبة **أكثر من 150 علامة EXIF مميزة**، مما يضمن حصولك على مجموعة كاملة من خصائص الكاميرا وGPS اللازمة للتحليلات أو الامتثال.

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8** أو أحدث مثبت على جهازك.  
- **Maven** لإدارة التبعيات.  
- **GroupDocs.Metadata للغة Java الإصدار 24.12** (أو أحدث).  
- إلمام أساسي بفئات Java، الكائنات، ومعالجة الاستثناءات.

### المكتبات والتبعيات المطلوبة
| التبعية | إحداثيات Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### إعداد البيئة
يجب أن يكون لديك بيئة تطوير متوافقة مع Maven مثل IntelliJ IDEA أو Eclipse. أنشئ مشروع Maven جديدًا أو أضف التبعية إلى مشروع موجود.

## كيفية إعداد GroupDocs.Metadata للغة Java
يمكن إضافة GroupDocs.Metadata إلى مشروع Maven ببضع أسطر من الإعداد. توضح الخطوات التالية كيفية تضمين المستودع والتبعية بحيث تكون المكتبة متاحة في مسار الفئة.

### إعداد Maven
أضف المقتطف التالي إلى ملف `pom.xml` داخل قسم `<dependencies>`:

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

### التحميل المباشر
بدلاً من ذلك، قم بتحميل أحدث ملف JAR من صفحة الإصدارات الرسمية: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### الحصول على الترخيص
لتشغيل المكتبة بعد فترة التجربة التي تبلغ 30 يومًا، احصل على ترخيص مؤقت أو كامل:

1. قم بزيارة [صفحة شراء الترخيص](https://purchase.groupdocs.com/temporary-license).  
2. اختر **temporary** للاختبار أو **full** للإنتاج.  
3. اتبع التعليمات على الشاشة لتضمين ملف الترخيص (`metadata.lic`) في مسار الفئة Java الخاص بك.

### التهيئة الأساسية والإعداد
بعد أن تكون المكتبة على مسار الفئة، قم بتهيئتها كما هو موضح أدناه:

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

## كيفية استخراج خصائص بيانات EXIF الوصفية الأساسية من صورة PSD
يوضح هذا القسم كيفية تحميل ملف PSD، الوصول إلى حاوية EXIF، وقراءة العلامات الأكثر شيوعًا مثل **artist**، **copyright**، و**software**. تتضمن العملية إنشاء كائن `Metadata`، استدعاء `getExif()`، ثم استرجاع الخصائص الفردية باستخدام طرق getter بسيطة.

### تنفيذ خطوة بخطوة
1. **إنشاء كائن `Metadata`** يشير إلى ملف PSD الخاص بك.  
2. **استدعاء `getExif()`** للحصول على حاوية EXIF.  
3. **قراءة الخصائص الفردية** مثل `getArtist()`، `getCopyright()`، و`getSoftware()`.  
4. **طباعة أو تخزين** القيم وفقًا لمنطق تطبيقك.

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

> **نصيحة احترافية:** يكتشف كائن `Metadata` تنسيق الملف تلقائيًا، لذا يمكنك إعادة استخدام نفس الشيفرة لملفات JPEG أو TIFF دون تعديل.

## كيفية استخراج خصائص حزمة EXIF IFD من صورة PSD
قسم IFD (Image File Directory) يحتوي على تفاصيل تقنية أعمق مثل **camera serial number**، **lens model**، و**user comments**. يمثل `Ifd0` دليل ملف الصورة الأساسي الذي يحتوي على معلومات الكاميرا الأساسية. استخراج هذه الحقول مفيد للتحليل الجنائي أو الفهرسة ذات الدقة العالية.

### خطوات التنفيذ
1. **إعادة استخدام كائن `Metadata`** من القسم السابق.  
2. **الانتقال إلى حاوية IFD** عبر `metadata.getExif().getIfd0()`.  
3. **قراءة الخصائص** مثل `getBodySerialNumber()` و`getUserComment()`.  
4. **إخراج البيانات** أو ربطها بنموذج النطاق الخاص بك.

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

## كيفية استرجاع بيانات GPS (خط العرض، خط الطول) من ملف PSD
تضمّن العديد من الكاميرات الحديثة إحداثيات GPS في كتلة EXIF. يحتوي `GpsInfo` على الإحداثيات الجغرافية المستخرجة من بيانات EXIF. استدعِ `metadata.getExif().getGpsInfo()` ثم استخدم `getLatitude()`، `getLongitude()`، و`getAltitude()` للحصول على بيانات موقع دقيقة—بدون الحاجة إلى تحليل إضافي.

### خطوات مفصلة
1. **الحصول على كائن معلومات GPS**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **قراءة خط العرض وخط الطول**: `gps.getLatitude()` تُعيد قيمة `double` بالدرجات العشرية.  
3. **معالجة البيانات المفقودة**: تُعيد API القيمة `null` إذا كانت العلامة غير موجودة، لذا احمِ نفسك من `NullPointerException`.  

> **مشكلة شائعة:** بعض ملفات PSD تخزن إحداثيات GPS كأعداد نسبية؛ تقوم المكتبة بتطبيعها تلقائيًا، لكن الملفات القديمة قد تتطلب تحويلًا يدويًا.

## المشكلات الشائعة واستكشاف الأخطاء
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| `Unsupported format` exception | استخدام نسخة أقدم من GroupDocs.Metadata لا تتعرف على PSD | الترقي إلى الإصدار 24.12 أو أحدث |
| `NullPointerException` when calling `getArtist()` | علامة EXIF غير موجودة في الملف المصدر | تحقق من `metadata.getExif().hasArtist()` قبل القراءة |
| License error after 30 days | ملف الترخيص غير موجود في مسار الفئة | ضع `metadata.lic` في `src/main/resources` أو اضبط `Metadata.setLicense("path/to/license")` |

## الأسئلة المتكررة
**س: هل يمكنني استخراج بيانات EXIF الوصفية من ملف PSD محمي بكلمة مرور؟**  
**ج:** نعم. حمّل الملف باستخدام `new Metadata("file.psd", "password")` ثم وصول إلى بيانات EXIF كالمعتاد.

**س: هل يدعم GroupDocs.Metadata معالجة دفعة من ملفات PSD متعددة؟**  
**ج:** بالتأكيد. أنشئ كائن `Metadata` داخل حلقة، أو استخدم المساعد `MetadataCollection` لمعالجة الأدلة بكفاءة.

**س: ما إصدارات Java المدعومة رسميًا؟**  
**ج:** تم اختبار Java 8 حتى Java 21 بالكامل. تستخدم المكتبة فقط واجهات برمجة التطبيقات القياسية، لذا تعمل على أي JVM متوافق.

**س: هل يمكن كتابة بيانات EXIF مرة أخرى إلى ملف PSD؟**  
**ج:** نعم. بعد تعديل الخصائص عبر كائن `Exif`، استدعِ `metadata.save("output.psd")` لحفظ التغييرات.

**س: ما هو أقصى حجم لملف PSD يمكن للمكتبة التعامل معه دون نفاد الذاكرة؟**  
**ج:** تقوم GroupDocs.Metadata ببث البيانات ويمكنها معالجة ملفات تصل إلى **2 GB** على جهاز بذاكرة 8 GB تقريبًا، بفضل بنية الذاكرة المنخفضة.

## الخلاصة
أنت الآن تعرف **كيفية استخراج بيانات EXIF** الوصفية من ملفات PSD باستخدام GroupDocs.Metadata للغة Java، من العلامات الأساسية إلى معلومات IFD المتقدمة وGPS. دمج هذه الشيفرات في خط أنابيب معالجة الصور الخاص بك لأتمتة الفهرسة، فحوصات الامتثال، أو الخدمات القائمة على الموقع. لاستكشاف أعمق، جرّب استخراج البيانات الوصفية من صيغ أخرى مدعومة (JPEG، TIFF، PNG) أو جرب إمكانيات الكتابة لإدراج علامات مخصصة.

---

**آخر تحديث:** 2026-08-10  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 للغة Java  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [استخراج موارد الصور من ملفات PSD باستخدام GroupDocs.Metadata في Java: دليل شامل](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [استخراج رأس PSD ومعلومات الطبقة باستخدام GroupDocs.Metadata للغة Java: دليل شامل](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [استخراج خصائص MakerNote كعلامات TIFF/EXIF باستخدام GroupDocs.Metadata في Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)