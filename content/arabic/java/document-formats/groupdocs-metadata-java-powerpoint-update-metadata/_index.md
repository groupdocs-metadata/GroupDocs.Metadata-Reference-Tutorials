---
date: '2026-05-27'
description: تعلم كيفية ضبط CreatedTime لملف pptx في Java باستخدام تبعية GroupDocs
  Maven لتحديث بيانات تعريف PowerPoint، بما في ذلك كيفية تغيير تاريخ إنشاء PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: ضبط CreatedTime لملف PPTX في Java باستخدام تبعية GroupDocs Maven
type: docs
url: /ar/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# تعيين وقت الإنشاء لملف PPTX في Java باستخدام GroupDocs.Metadata

البيانات الوصفية الدقيقة ضرورية للامتثال وإمكانية الاكتشاف في سير عمل المستندات الحديثة. باستخدام **GroupDocs.Metadata** يمكنك برمجيًا **تعيين وقت الإنشاء لملف PPTX في Java**، مما يتيح لك **تغيير تاريخ إنشاء PPTX** إلى جانب خصائص مدمجة أخرى مثل المؤلف أو الشركة. هذا الدليل يشرح إعداد Maven، تهيئة الـ API، تحديث البيانات الوصفية، وحفظ العرض المعدل — كل ذلك بكود واضح وجاهز للإنتاج.

## إجابات سريعة
- **أي مكتبة تقوم بتحديث بيانات PowerPoint الوصفية في Java؟** GroupDocs.Metadata عبر تبعية Maven الخاصة بـ GroupDocs.  
- **هل يمكنني تعيين خاصية وقت الإنشاء PPTX؟** نعم — استخدم `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **هل يلزم الحصول على ترخيص للإنتاج؟** الإصدار التجريبي يعمل للتقييم؛ الترخيص التجاري إلزامي للنشر في بيئة الإنتاج.  
- **ما أداة البناء المستخدمة في المثال؟** Maven (يمكنك أيضًا تنزيل ملف JAR يدويًا).  
- **هل يدعم الـ API Java 8 والإصدارات الأحدث؟** بالطبع — GroupDocs.Metadata تستهدف Java 8+.

## ما هي تبعية Maven الخاصة بـ GroupDocs؟
تُعد **تبعية Maven الخاصة بـ GroupDocs** إدخالًا في مستودع متوافق مع Maven يقوم بسحب أحدث مكتبة GroupDocs.Metadata إلى مشروع Java الخاص بك. إنها تبسط إدارة التبعيات من خلال حل المكتبات المتعاقبة تلقائيًا، وتضمن لك دائمًا استخدام أحدث نسخة آمنة، وتلغي الحاجة إلى تنزيل ملفات JAR يدويًا أو تتبع الإصدارات.

## لماذا نستخدم GroupDocs.Metadata لتغيير تاريخ إنشاء PPTX؟
يتيح GroupDocs.Metadata تحديثات آلية وجاهزة للدفعات لتواريخ إنشاء PPTX، مما يضمن أن كل عرض تقديمي يلتزم بسياسات الشركة أو المتطلبات القانونية. من خلال تعيين خاصية CreatedTime برمجيًا، تتجنب التحرير اليدوي، تقلل الأخطاء البشرية، ويمكنك دمج التغيير في خطوط CI/CD أو سكريبتات الهجرة لإدارة المستندات بسلاسة.

## المتطلبات المسبقة
- Java 8 أو أعلى مثبت.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- Maven لإدارة التبعيات.  
- الوصول إلى نسخة تجريبية من GroupDocs أو ترخيص مُشتَرَى.

## كيفية تعيين وقت الإنشاء PPTX في Java؟

تمثل الفئة `Metadata` مستندًا وتوفر الوصول إلى خصائص البيانات الوصفية الخاصة به.

حمّل ملف PowerPoint باستخدام `new Metadata("presentation.pptx")`، استرجع الحزمة الجذرية، استدعِ `setCreatedTime` مع تاريخ `java.util.Date` المطلوب، وأخيرًا نفّذ `save` لكتابة التغييرات. هذه العملية الشاملة تعدل تاريخ الإنشاء مع الحفاظ على محتوى جميع الشرائح والخصائص الأخرى.

### إعداد Maven
أضف مستودع GroupDocs وتبعيات metadata إلى ملف `pom.xml` الخاص بك:

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

> **نصيحة احترافية:** الحفاظ على تحديث رقم الإصدار يضمن لك الاستفادة من أحدث تصحيحات الأخطاء وتحسينات الأداء.

### تنزيل مباشر (إذا كنت تفضل عدم استخدام Maven)

بدلاً من ذلك، قم بتنزيل أحدث ملف JAR من [إصدارات GroupDocs.Metadata للـ Java](https://releases.groupdocs.com/metadata/java/).

#### الحصول على الترخيص

ابدأ بنسخة تجريبية مجانية أو اطلب ترخيصًا مؤقتًا لتقييم GroupDocs.Metadata. للاستخدام في الإنتاج، اشترِ ترخيصًا عبر [الموقع الرسمي لـ GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## التهيئة الأساسية والإعداد

بمجرد أن تكون المكتبة في مسار الفئة (classpath)، يمكنك إنشاء مثيل `Metadata` يشير إلى ملف PowerPoint الخاص بك:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

يفتح هذا الكود العرض التقديمي داخل كتلة try‑with‑resources، مما يضمن تحرير مقبض الملف تلقائيًا.

## دليل خطوة بخطوة لتحديث البيانات الوصفية المدمجة

### الخطوة 1: تحميل مستند العرض التقديمي

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

يؤسس تحميل الملف اتصالًا يتيح لك قراءة أو كتابة البيانات الوصفية.

### الخطوة 2: الوصول إلى الحزمة الجذرية للعرض التقديمي

كائن `root` يمنحك الوصول إلى الحزمة الأساسية للعرض وخصائصه المدمجة.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

كائن `root` يعرض جميع خصائص المستند المدمجة.

### الخطوة 3: تحديث خصائص المستند المدمجة (بما في ذلك تاريخ الإنشاء)

`setCreatedTime` يعيّن طابع زمن جديد لتاريخ الإنشاء في المستند.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

هنا نوضح كيفية **تعيين وقت الإنشاء PPTX** عن طريق إسناد كائن `Date` جديد إلى `CreatedTime`. استبدل `new Date()` بأي طابع زمني محدد تحتاجه.

### الخطوة 4: حفظ العرض المحدث

`save` يكتب البيانات الوصفية المعدلة إلى ملف.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

استدعاء `save` يكتب البيانات الوصفية المعدلة إلى ملف PowerPoint جديد، مع ترك الأصلي دون تعديل.

## نصائح استكشاف الأخطاء وإصلاحها
- **الملف غير موجود:** تحقق مرة أخرى من مسار الإدخال وأذونات الملف.  
- **عدم توافق الإصدارات:** تأكد من أن نسخة `groupdocs-metadata` تتطابق مع بيئة تشغيل Java الخاصة بك.  
- **الخاصية لا تتحدث:** تحقق من أنك تستدعي `setCreatedTime` (أو الدالة المناسبة) قبل استدعاء `save`.

## تطبيقات عملية
1. **العلامة التجارية للشركة:** حقن اسم الشركة الصحيح والفئة تلقائيًا في جميع عروض الشرائح قبل التوزيع.  
2. **أنظمة إدارة المستندات:** إغناء ملفات PPTX ببيانات وصفية قابلة للبحث لتسريع الاسترجاع.  
3. **الموارد التعليمية:** الحفاظ على معلومات المؤلف والمنهج محدثة عبر شرائح المحاضرات.  
4. **تتبع التعاون:** تسجيل أسماء المساهمين للحفاظ على المساءلة.  
5. **تكامل نظام إدارة المحتوى:** مزامنة تغييرات البيانات الوصفية مع منصة إدارة المحتوى الخاصة بك في الوقت الفعلي.

## اعتبارات الأداء
- **معالجة دفعات:** تكرار عبر قائمة من الملفات وإعادة استخدام مثيل `Metadata` واحد حيثما أمكن.  
- **إدارة الذاكرة:** استخدم دائمًا try‑with‑resources (كما هو موضح) لتحرير الموارد الأصلية بسرعة.  
- **هياكل بيانات فعّالة:** خزن تحديثات البيانات الوصفية في خريطة قبل تطبيقها لتقليل الاستدعاءات المتكررة.

## الأسئلة المتكررة

**س: ما هو الغرض الأساسي من تبعية Maven الخاصة بـ GroupDocs؟**  
ج: إنها توفر طريقة مريحة لتضمين أحدث مكتبة GroupDocs.Metadata في مشاريع Java القائمة على Maven.

**س: كيف يمكنني تعيين تاريخ إنشاء PPTX دون التأثير على الخصائص الأخرى؟**  
ج: استخدم `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` قبل استدعاء `metadata.save()`.

**س: هل أحتاج إلى ترخيص لتشغيل هذا الكود في بيئة التطوير؟**  
ج: ترخيص تجريبي مؤقت يكفي للتطوير والاختبار؛ ترخيص كامل مطلوب للإنتاج.

**س: هل يمكنني تحديث حقول البيانات الوصفية المخصصة أيضًا؟**  
ج: نعم — يدعم GroupDocs.Metadata كلًا من الخصائص المدمجة والمخصصة عبر API الخاص به.

**س: هل هناك طريقة للعودة عن التغييرات إذا ارتكبت خطأ؟**  
ج: احتفظ بنسخة من الملف الأصلي أو اقرأ قيم الخصائص الحالية قبل الكتابة فوقها، ثم استعدها إذا لزم الأمر.

## الموارد

- [التوثيق](https://docs.groupdocs.com/metadata/java/)
- [مرجع API](https://apireference.groupdocs.com/metadata/java/)

**آخر تحديث:** 2026-05-27  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 for Java  
**المؤلف:** GroupDocs  

## دروس ذات صلة

- [تحديث البيانات الوصفية المخصصة في PowerPoint باستخدام GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [كيفية تحديث بيانات وصفية لمستند Word باستخدام GroupDocs.Metadata Java: دليل كامل](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [تحديث بيانات PDF الوصفية بفعالية باستخدام GroupDocs.Metadata في Java لإدارة المستندات](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)