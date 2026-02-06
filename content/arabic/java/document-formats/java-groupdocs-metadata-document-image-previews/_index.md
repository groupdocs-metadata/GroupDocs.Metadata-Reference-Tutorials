---
date: '2026-02-06'
description: تعلم كيفية إنشاء معاينة مستند جافا وإخراج الصفحة كصورة باستخدام GroupDocs.Metadata.
  يغطي هذا الدليل إعداد البرنامج، وتكوينه، وخطوات التنفيذ.
keywords:
- document image preview
- GroupDocs Metadata Java
- creating document previews with Java
title: كيفية إنشاء معاينة مستند جافا باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/document-formats/java-groupdocs-metadata-document-image-previews/
weight: 1
---

# إتقان معاينات صور المستندات في Java باستخدام GroupDocs.Metadata

## المقدمة

إذا كنت بحاجة إلى إنشاء تطبيقات **create document preview java**—سواء لنظام إدارة مستندات، مكتبة رقمية، أو ميزة النظرة السريعة في بوابة مؤسسية—فإن GroupDocs.Metadata يجعل الأمر بسيطًا. في هذا الدرس ستتعلم كيفية تحميل مستند، تكوين خيارات المعاينة، وإخراج الصفحات كملفات صورة، كل ذلك باستخدام شفرة Java نظيفة.

سنستعرض سير العمل الكامل، من إعداد Maven إلى إنشاء معاينات PNG لصفحات محددة. هل أنت مستعد لرؤية مستنداتك تتحول إلى صور؟ هيا نبدأ!

## إجابات سريعة
- **ماذا يعني “create document preview java”؟** إنشاء لقطات بصرية (مثل PNG) لصفحات المستند باستخدام شفرة Java.  
- **ما المكتبة التي تدعم ذلك مباشرةً؟** GroupDocs.Metadata for Java.  
- **هل يمكنني اختيار تنسيق الصورة؟** نعم—خيارات المعاينة تتيح لك اختيار PNG، JPEG، BMP، إلخ.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ الترخيص المدفوع مطلوب للإنتاج.  
- **هل يمكن معاينة صفحات محددة فقط؟** بالتأكيد—استخدم `setPageNumbers` لاستهداف صفحات معينة.

## ما هو **create document preview java**؟
إنشاء معاينة مستند في Java يعني تحويل صفحة أو أكثر من ملف (DOCX، PDF، PPT، إلخ) إلى ملفات صورة برمجياً. هذا يتيح إنشاء معارض مصغرات، فحوصات بصرية سريعة، وتكامل سلس مع مكونات واجهة المستخدم على الويب أو سطح المكتب.

## لماذا نستخدم GroupDocs.Metadata لإنشاء المعاينات؟
- **بدون تبعيات خارجية** – Java نقي، بدون ملفات ثنائية أصلية.  
- **يدعم أكثر من 100 تنسيق ملف** – من Office إلى CAD.  
- **تحكم دقيق** – اختيار تنسيق الصورة، DPI، ونطاق الصفحات.  
- **أداء عالي** – مُحسّن للوثائق الكبيرة ومعالجة الدُفعات.

## المتطلبات المسبقة

- **المكتبات المطلوبة:** GroupDocs.Metadata for Java (أحدث نسخة).  
- **نظام البناء:** مشروع Maven (أو إضافة JAR يدويًا).  
- **المهارات المطلوبة:** الإلمام بـ Java I/O، try‑with‑resources، ومعالجة الاستثناءات.

## إعداد GroupDocs.Metadata لـ Java

### معلومات التثبيت

Add the GroupDocs repository and dependency to your `pom.xml`:

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

**تحميل مباشر**  
بدلاً من ذلك، قم بتحميل أحدث ملفات JAR من [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) وأضفها إلى مسار الفئة (classpath) الخاص بمشروعك.

### الحصول على الترخيص

ابدأ بنسخة تجريبية مجانية أو اطلب ترخيصًا مؤقتًا. للاستخدام في الإنتاج، اشترِ ترخيصًا هنا: [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/).

### التهيئة الأساسية والإعداد

The following snippet shows the minimal code required to open a document with GroupDocs.Metadata:

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;

public class LoadDocument {
    public static void main(String[] args) {
        // Replace with your actual document path
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            System.out.println("Document loaded successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## دليل التنفيذ

فيما يلي نقسم الحل إلى ثلاث ميزات مركزة. كل ميزة تتضمن شروحات مختصرة والكود الدقيق الذي تحتاجه—بدون أي مقتطفات إضافية، فقط الكتل الأصلية محفوظة.

### الميزة 1: تهيئة Metadata لمعالجة المستند

**نظرة عامة**  
تحميل المستند هو الخطوة الأولى قبل إمكانية إنشاء أي معاينة.

#### الخطوة 1 – استيراد الفئات  

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;
```

#### الخطوة 2 – تحميل المستند  

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
try (Metadata metadata = new Metadata(documentPath)) {
    System.out.println("Document loaded successfully.");
} catch (IOException e) {
    e.printStackTrace();
}
```

**نصائح**  
- تحقق من مسار الملف وأذونات القراءة قبل تشغيل الشفرة.  
- استخدم مسارات مطلقة أثناء الاختبار لتجنب ارتباك مسار الفئة.

### الميزة 2: إنشاء خيارات المعاينة لصفحات المستند

**نظرة عامة**  
قم بتكوين مظهر المعاينة والصفحات التي يجب عرضها.

#### الخطوة 1 – استيراد فئات المعاينة  

```java
import com.groupdocs.metadata.options.PreviewFormats;
import com.groupdocs.metadata.options.PreviewOptions;
import java.io.OutputStream;
```

#### الخطوة 2 – إعداد خيارات المعاينة  

```java
OutputStream outputStream = null; // Replace with actual implementation if needed

PreviewOptions previewOptions = new PreviewOptions(outputStream::write);
previewOptions.setPreviewFormat(PreviewFormats.PNG); // Set the format of the preview image
previewOptions.setPageNumbers(new int[]{1}); // Specify page numbers to generate previews for
```

**لماذا هذا مهم**  
اختيار `PNG` يضمن جودة غير مضغوطة، وهو مثالي للمصغرات. عدّل `setPageNumbers` لمعاينة أي نطاق صفحات تحتاجه.

### الميزة 3: إنشاء تدفق الصفحة لإخراج الصورة

**نظرة عامة**  
يجب كتابة كل صورة معاينة إلى ملف أو وجهة إخراج أخرى.

#### الخطوة 1 – استيراد فئات I/O  

```java
import java.io.FileOutputStream;
import java.io.File;
import java.io.OutputStream;
import java.io.IOException;
```

#### الخطوة 2 – إنشاء التدفق وكتابة الصورة  

```java
int pageNumber = 1; // Example page number

try {
    File outputFile = new File(String.format("YOUR_OUTPUT_DIRECTORY/result_%d.png", pageNumber));
    OutputStream stream = new FileOutputStream(outputFile);
    System.out.println("Page stream created for output.");
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

**نصيحة احترافية:** تأكد من وجود `YOUR_OUTPUT_DIRECTORY` مسبقًا، أو أنشئه برمجياً باستخدام `outputFile.getParentFile().mkdirs();`.

## كيفية **output page as image** باستخدام GroupDocs.Metadata

من خلال دمج خيارات المعاينة من الميزة 2 مع منطق التدفق من الميزة 3، يمكنك تحويل أي صفحة إلى ملف صورة:

1. تهيئة `Metadata` (الميزة 1).  
2. بناء كائن `PreviewOptions`، حدد `PNG` وأرقام الصفحات المطلوبة.  
3. مرّر دالة لامبدا التي تكتب بايتات المعاينة إلى `OutputStream` التي أنشأتها في الميزة 3.

هذا التسلسل يتيح لك **output page as image** بكفاءة، حتى للوثائق الكبيرة.

## تطبيقات عملية

- **أنظمة إدارة المستندات:** عرض المصغرات في متصفحات الملفات.  
- **المكتبات الرقمية:** توفير إشارات بصرية سريعة للكتب الممسوحة.  
- **القانونية/المالية:** تمكين فحص سريع لصفحات العقود.  
- **منصات CMS:** إنشاء صور معاينة تلقائيًا للتقارير المرفوعة.  
- **التعليم الإلكتروني:** إتاحة لمحة للطلاب عن شرائح المحاضرات قبل التحميل.

## اعتبارات الأداء

- **تحديد دفعات الصفحات:** إنشاء العديد من الصفحات مرة واحدة قد يرفع استهلاك الذاكرة.  
- **استخدام try‑with‑resources:** يضمن إغلاق التدفقات، مما يمنع التسريبات.  
- **مراقبة ذاكرة JVM:** قد تتطلب ملفات PDF الكبيرة زيادة الذاكرة (`-Xmx`).

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|-------|-----|
| `NullPointerException` على `outputStream` | `outputStream` غير مهيأ | قدم `OutputStream` حقيقي (مثال: `new FileOutputStream(...)`). |
| لم يتم إنشاء معاينة | رقم صفحة غير صحيح | تحقق من وجود الصفحة؛ استخدم `metadata.getPageCount()` للتحقق. |
| خطأ في الأذونات عند كتابة الملف | دليل الإخراج للقراءة فقط | امنح أذونات كتابة أو اختر مجلدًا قابلًا للكتابة. |

## الأسئلة المتكررة

**س: هل يمكنني إنشاء معاينات للوثائق المحمية بكلمة مرور؟**  
ج: نعم. افتح المستند باستخدام المُنشئ المناسب الذي يقبل كلمة مرور، ثم تابع مع خيارات المعاينة.

**س: ما هي تنسيقات الصور المدعومة؟**  
ج: PNG، JPEG، BMP، و GIF متاحة عبر `PreviewFormats`.

**س: كيف يمكنني معاينة عدة صفحات في استدعاء واحد؟**  
ج: مرّر مصفوفة من أرقام الصفحات إلى `previewOptions.setPageNumbers(new int[]{1,2,3});`.

**س: هل هناك طريقة للتحكم في دقة الصورة؟**  
ج: اضبط DPI باستخدام `previewOptions.setDpi(int dpi)` (الإعداد الافتراضي هو 96 DPI).

**س: هل تعمل المكتبة على Android؟**  
ج: GroupDocs.Metadata هي Java نقي ويمكن استخدامها على Android مع ملفات JAR المناسبة، لكن يجب أن يتولى إطار Android عرض الواجهة.

## الخلاصة

أنت الآن تمتلك دليلًا كاملاً وجاهزًا للإنتاج لحلول **create document preview java** التي **output page as image** باستخدام GroupDocs.Metadata. باتباع خطوات الميزات الثلاث—تهيئة metadata، تكوين خيارات المعاينة، وكتابة تدفق الصورة—يمكنك دمج معاينات عالية الجودة في أي تطبيق Java.

**آخر تحديث:** 2026-02-06  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 for Java  
**المؤلف:** GroupDocs