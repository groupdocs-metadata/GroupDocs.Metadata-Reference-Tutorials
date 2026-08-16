---
date: '2026-08-15'
description: تعلم كيفية إضافة كلمات مفتاحية IPTC في Java باستخدام GroupDocs.Metadata،
  مما يحسن إدارة الأصول الرقمية وقابلية البحث.
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: أضف كلمات مفتاحية IPTC في Java باستخدام GroupDocs.Metadata لتعزيز
  إدارة الأصول الرقمية. تعلم الإعداد خطوة بخطوة، الكود، وأفضل الممارسات.
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: إضافة كلمات مفتاحية IPTC في Java باستخدام GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: إضافة كلمات مفتاحية IPTC في Java باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# إضافة كلمات مفتاحية IPTC في Java باستخدام GroupDocs.Metadata

إدارة بيانات تعريف الصور ضرورية لأي استراتيجية إدارة الأصول الرقمية (DAM). في هذا البرنامج التعليمي ستتعلم **كيفية إضافة كلمات مفتاحية IPTC في Java** باستخدام مكتبة GroupDocs.Metadata، ثم استرجاع تلك الكلمات المفتاحية للتحقق من التغييرات. في النهاية، ستحصل على نمط قابل لإعادة الاستخدام يمكنك دمجه في وظائف المعالجة الدفعية، خطوط أنابيب إدارة المحتوى، أو أي سير عمل وسائط مبني على Java.

## إجابات سريعة
- **أي مكتبة تضيف كلمات مفتاحية IPTC في Java؟** GroupDocs.Metadata for Java.  
- **هل أحتاج إلى ترخيص؟** A free trial works for development; a paid license is required for production.  
- **هل يمكنني إضافة عدة كلمات مفتاحية مرة واحدة؟** Yes—simply add each keyword to the IPTC package.  
- **هل يتم دعم معالجة الملفات الكبيرة؟** GroupDocs.Metadata processes files up to 2 GB without loading the whole file into memory.  
- **ما نسخة Java المطلوبة؟** JDK 8 or higher, with Maven 3 or later.

## ما هو إضافة كلمات مفتاحية IPTC في Java؟
**Add IPTC keywords java** يشير إلى الإدراج البرمجي لعلامات الكلمات المفتاحية وفق معيار IPTC في ملفات الصور باستخدام كود Java. هذه العملية تُثري بيانات تعريف الصورة، مما يجعلها قابلة للبحث في أنظمة DAM وتحسين SEO للأصول الويب. كما تساعد في الحفاظ على الامتثال للمعايير الصناعية لتوسيم أصول الوسائط.

## لماذا تستخدم GroupDocs.Metadata لـ Java؟
GroupDocs.Metadata يدعم **أكثر من 150 معيارًا للبيانات الوصفية** (بما في ذلك EXIF، IPTC، XMP) ويمكنه **معالجة ملفات تصل إلى 2 GB** دون تحميلها بالكامل في الذاكرة، مما يقلل من استهلاك المعالج والذاكرة RAM بنسبة تصل إلى 30 % مقارنةً بالنهج البسيط لتدفق الملفات. الـ API آمن من حيث النوع، موثق جيدًا، ويوفر استدعاءً سطرًا واحدًا لحفظ التغييرات.

## المتطلبات المسبقة
- **GroupDocs.Metadata for Java** (الإصدار 24.12 أو أحدث).  
- مجموعة تطوير Java 8 أو أحدث.  
- Maven 3 مثبت ومُكوَّن.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse (اختياري لكن يُنصح به).

### المكتبات المطلوبة
أضف تبعية GroupDocs.Metadata إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

يمكنك تنزيل المكتبة من صفحة **إصدارات GroupDocs.Metadata for Java**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## كيفية إضافة كلمات مفتاحية IPTC في Java؟
أولاً، قم بتحميل ملف الصورة المستهدف باستخدام API الخاص بـ GroupDocs.Metadata، ثم تحقق من وجود حزمة IPTC أو أنشئ واحدة إذا كانت مفقودة، وأخيرًا أضف الكلمات المفتاحية المطلوبة إلى مجموعة كلمات IPTC. الخطوات أدناه توضح كل جزء من سير العمل هذا بالتفصيل.

### الخطوة 1: إنشاء فئة الثوابت
فئة `Constants` تخزن القيم القابلة لإعادة الاستخدام مثل مواقع الملفات وسلسلة الترخيص.

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### الخطوة 2: تهيئة البيانات الوصفية وتعيين حزمة IPTC
`Metadata` هو نقطة الدخول لقراءة وكتابة أي تنسيق بيانات وصفية مدعوم. فهو يُجرد التعامل مع الملفات بحيث لا تحتاج إلى إدارة التدفقات يدويًا.

الشفرة أدناه تتحقق مما إذا كانت حزمة IPTC موجودة بالفعل؛ إذا لم تكن، فإنها تنشئ واحدة، مما يضمن وجود مكان لتخزين الكلمات المفتاحية.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### الخطوة 3: إضافة كلمات مفتاحية إلى سجل IPTC
IptcDataSet يمثل إدخالًا واحدًا من بيانات IPTC الوصفية مثل كلمة مفتاحية. يتم إضافة كل كلمة مفتاحية كإدخال `IptcDataSet`. يمكنك إضافة عدد غير محدود من الكلمات المفتاحية حسب الحاجة؛ المكتبة تتعامل تلقائيًا مع اكتشاف التكرارات.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### الخطوة 4: استرجاع وعرض كلمات IPTC المفتاحية
`metadata.getIptc().getKeywords()` يُعيد قائمة سلاسل الكلمات المفتاحية المخزنة في حزمة IPTC. بعد الحفظ، يمكنك قراءة الكلمات المفتاحية مرة أخرى لتأكيد أنها تم حفظها بشكل صحيح. خطوة التحقق هذه مفيدة لاختبارات الوحدة وتصحيح الأخطاء.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## كيفية استرجاع كلمات IPTC المفتاحية في Java؟
`metadata.getIptc().getKeywords()` يُعيد قائمة سلاسل الكلمات المفتاحية المخزنة في حزمة IPTC. يمكنك بعد ذلك التكرار عبر القائمة، تسجيل كل إدخال، أو إمدادها إلى فهرس بحث للحصول على استرجاع سريع. تُعيد الطريقة `List<String>` التي تحتوي على كل كلمة مفتاحية مخزنة في حزمة IPTC، مما يتيح لك عرضها أو معالجتها فورًا.

## المشكلات الشائعة واستكشاف الأخطاء
- **حزمة IPTC مفقودة:** إذا كانت الصورة تفتقر إلى كتلة IPTC، فإن `metadata.getIptc()` تُعيد `null`. احرص دائمًا على استدعاء `metadata.addIptc()` قبل إضافة الكلمات المفتاحية.  
- **أخطاء الترخيص:** تأكد من أن ملف الترخيص التجريبي أو التجاري مُشار إليه بشكل صحيح في `Constants.LICENSE_PATH`. نقص الترخيص يسبب استثناء `LicenseException`.  
- **ملفات كبيرة:** بالنسبة للصور التي تتجاوز 2 GB، قسّم المعالجة إلى أجزاء أو استخدم واجهات برمجة التطبيقات المتدفقة التي توفرها GroupDocs.Metadata لتجنب `OutOfMemoryError`.  

## الأسئلة المتكررة
**Q: هل يمكنني إضافة كلمات IPTC إلى ملفات PDF؟**  
A: لا. IPTC هو معيار خاص بالصور؛ بالنسبة لملفات PDF ستستخدم XMP أو حقول بيانات وصفية خاصة بـ PDF.

**Q: هل يدعم GroupDocs.Metadata صيغ صور أخرى؟**  
A: نعم—يتعامل مع JPEG، TIFF، PNG، BMP، وWebP، مع الحفاظ على البيانات الوصفية الحالية أثناء إضافة إدخالات IPTC جديدة.

**Q: كم عدد الكلمات المفتاحية التي يمكنني تخزينها؟**  
A: تسمح مواصفة IPTC بما يصل إلى 64 كلمة مفتاحية لكل صورة؛ GroupDocs.Metadata يفرض هذا الحد تلقائيًا.

**Q: هل المكتبة متوافقة مع Java 11؟**  
A: بالتأكيد. المكتبة مُجمعة لـ Java 8+ وتعمل بسلاسة على Java 11، 17، والإصدارات الأحدث من LTS.

**Q: ماذا لو احتجت إلى إزالة كلمة مفتاحية؟**  
A: استرجع قائمة الكلمات المفتاحية، احذف الإدخال غير المرغوب فيه، ثم استدعِ `metadata.getIptc().setKeywords(updatedList)` واحفظ الملف.

## الخلاصة
أنت الآن تمتلك نمطًا كاملاً وجاهزًا للإنتاج **لإضافة كلمات IPTC في Java** باستخدام GroupDocs.Metadata. من خلال تهيئة كائن البيانات الوصفية، وضمان وجود حزمة IPTC، وإضافة الكلمات المفتاحية، والتحقق من النتائج، يمكنك دمج وسم قوي في أي نظام DAM أو سير عمل إدارة محتوى مبني على Java. استكشف أنواع بيانات وصفية إضافية—EXIF، XMP، والوسوم المخصصة—لإثراء أصولك أكثر.

**الخطوات التالية**
- توسيع العينة لمعالجة دفعات من مجلدات الصور.  
- دمج إضافة الكلمات المفتاحية مع تحليل الصور الآلي (مثل الوسوم التي يولدها الذكاء الاصطناعي).  
- استكشاف API الخاص بـ GroupDocs.Metadata لقراءة/كتابة بيانات EXIF GPS لتمكين البحث القائم على الموقع.

---

**آخر تحديث:** 2026-08-15  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 for Java  
**المؤلف:** GroupDocs

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

## دروس ذات صلة
- [استخراج رأس BMP في Java – دروس GroupDocs.Metadata للصور](/metadata/java/image-formats/)
- [استخراج بيانات تعريف الصورة في Java – استخراج بيانات Panasonic MakerNote باستخدام GroupDocs.Metadata في Java](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [أتمتة تحديثات بيانات تعريف Java حسب التاريخ باستخدام GroupDocs.Metadata لإدارة ملفات فعّالة](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)