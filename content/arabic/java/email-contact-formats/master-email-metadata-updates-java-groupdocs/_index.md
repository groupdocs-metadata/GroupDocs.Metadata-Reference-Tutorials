---
date: '2026-05-27'
description: تعلم كيفية تحديث مستلمي البريد الإلكتروني Java باستخدام GroupDocs.Metadata
  للغة Java. عدّل المستلمين والموضوعات واحفظ التغييرات بكفاءة.
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'تحديث مستلمي البريد الإلكتروني Java: إتقان تحديثات بيانات البريد الإلكتروني
  باستخدام GroupDocs.Metadata'
type: docs
url: /ar/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# تحديث مستلمي البريد الإلكتروني Java باستخدام GroupDocs.Metadata

في هذا الدليل الشامل ستقوم **update email recipients java** برمجياً باستخدام مكتبة GroupDocs.Metadata. سنستعرض تعديل المستلمين الأساسيين و CC، وتغيير سطر الموضوع، وحفظ هذه التغييرات — كل ذلك مع مقتطفات كود واضحة خطوة بخطوة. في النهاية ستكون جاهزًا لدمج أتمتة بيانات البريد الإلكتروني في أي سير عمل مبني على Java.

## إجابات سريعة
- **ما هي أسرع طريقة لتغيير المستلم الأساسي للبريد الإلكتروني؟** قم بتحميل الملف باستخدام `Metadata`، احصل على `EmailRootPackage`، استبدل مجموعة `To`، واحفظ — كل ذلك في ثلاث أسطر من الكود.  
- **هل يمكنني إضافة مستلمي CC دون الكتابة فوق الموجودين؟** نعم، استخدم `addCcRecipient` على `EmailRootPackage` لإلحاق عناوين جديدة.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** ترخيص مؤقت يزيل حدود التقييم؛ ترخيص دائم مطلوب للنشر التجاري. يمكنك الحصول على ترخيص مؤقت من صفحة [GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **ما إصدارات Java المدعومة؟** يعمل GroupDocs.Metadata مع Java 8، 11، 17، والإصدارات الأحدث.  
- **هل المعالجة الدفعية آمنة لصناديق البريد الكبيرة؟** عالج الملفات على دفعات من 50–100 للحفاظ على استهلاك الذاكرة أقل من 200 MB لكل دفعة.

## ما هو update email recipients java؟
*Updating email recipients in Java* يعني تغيير حقول “To”، “CC”، أو “BCC” لملف بريد إلكتروني (EML، MSG، إلخ) برمجياً دون فتح عميل بريد. تُظهر GroupDocs.Metadata واجهة برمجة تطبيقات عالية المستوى تقرأ بنية البريد، وتسمح لك بتعديل مجموعات العناوين، وتكتب الملف المحدث مرة أخرى إلى القرص.

## لماذا نستخدم GroupDocs.Metadata لبيانات البريد الإلكتروني؟
GroupDocs.Metadata يدعم **أكثر من 50 تنسيقًا متعلقًا بالبريد** (بما في ذلك EML، MSG، MHT) ويمكنه معالجة **رسائل مئات الصفحات** دون تحميل الملف بالكامل إلى الذاكرة، مما يقلل استهلاك RAM بنسبة تصل إلى **80 %** مقارنةً بالنهج البسيط لتدفق الملفات. تنفيذها النقي بلغة Java يلغي الاعتماديات الأصلية، مما يجعلها مثالية للخدمات متعددة المنصات.

## المتطلبات المسبقة
- Java 8 أو أحدث (Java 11، 17، 21 تم اختبارها بالكامل).  
- Maven أو Gradle لإدارة الاعتمادات.  
- ترخيص صالح لـ GroupDocs.Metadata (مؤقت أو دائم).  

### المكتبات والاعتمادات المطلوبة
أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

للتنزيلات المباشرة، احصل على أحدث نسخة من [إصدارات GroupDocs.Metadata لجافا](https://releases.groupdocs.com/metadata/java/).

### إعداد البيئة
تأكد من أن بيئة التطوير المتكاملة (IDE) تشير إلى JDK متوافق وأن Maven يحلّ الاعتمادات الخاصة بـ GroupDocs.Metadata دون أخطاء.

## كيف يتم تحديث مستلمي البريد الإلكتروني في Java؟
حمّل ملف البريد الإلكتروني، استبدل المستلمين الحاليين، واحفظ النتيجة. هذه العملية تتطلب ثلاث نداءات فقط إلى API وتستغرق أقل من **200 ms** للرسائل النموذجية بحجم 1 MB. باستخدام API عالي المستوى `EmailRootPackage` تتجنب تحليل الملف بالكامل، مما يحافظ على انخفاض استهلاك الذاكرة ويسهل المعالجة الدفعية.

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
السطر أعلاه يستورد الفئة الأساسية لبدء إدارة عمليات البيانات الوصفية على ملفاتك.

## دليل التنفيذ
الآن سنغوص أعمق في كل ميزة، موسعين على مقتطفات الإجابات السريعة بسياق كامل.

### تحديث مستلمي البريد الإلكتروني
**نظرة عامة**: يوضح هذا القسم كيفية تحديث المستلمين الأساسيين لرسالة بريد إلكتروني برمجياً.

#### الخطوة 1: تهيئة كائن Metadata
فئة `Metadata` تمثل ملفًا وتوفر الوصول إلى بياناته الوصفية. أنشئ نسخة من `Metadata` باستخدام مسار ملف الإدخال الخاص بك:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**مرساة التعريف**: فئة `Metadata` هي نقطة الدخول لجميع عمليات البيانات الوصفية في GroupDocs.Metadata، وتمثل ملفًا واحدًا في الذاكرة.

#### الخطوة 2: الوصول إلى EmailRootPackage
`EmailRootPackage` يتيح الوصول إلى البيانات الوصفية الخاصة بالبريد مثل المستلمين والموضوع. احصل على بيانات البريد باستخدام:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
هذه الخطوة حاسمة لأنها توفر الوصول إلى جميع الخصائص القابلة للتعديل في بريدك.

#### الخطوة 3: تحديث المستلمين
عيّن مستلمين جدد لرسالة البريد الإلكتروني:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### إضافة مستلمي نسخة كربونية (CC) إلى البريد الإلكتروني
**نظرة عامة**: تعلم كيفية إلحاق مستلمي CC إلى بريد إلكتروني موجود.

#### الخطوة 1: التهيئة والحصول على الحزمة الجذرية
مشابه لتحديث المستلمين الأساسيين، قم بتهيئة كائن البيانات الوصفية:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### الخطوة 2: تعيين مستلمي CC
`addCcRecipient` يضيف عنوانًا جديدًا إلى مجموعة CC دون الكتابة فوق الإدخالات الموجودة. أضف مستلمي النسخة الكربونية كما يلي:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
هذا النهج يضمن إبلاغ المستخدمين الإضافيين دون أن يكونوا نقطة الاتصال الرئيسية.

### تحديث موضوع البريد الإلكتروني
**نظرة عامة**: تتيح لك هذه الميزة تعديل سطر الموضوع في البريد الإلكتروني، مما يحافظ على وضوح وتحديث الاتصالات.

#### الخطوة 1: تهيئة Metadata
ابدأ بتهيئة كائن البيانات الوصفية الخاص بك:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### الخطوة 2: تغيير الموضوع
قم بتحديث سطر موضوع البريد الإلكتروني:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
هذه الخطوة ضرورية للحفاظ على سلاسل بريد ذات صلة وقابلة للبحث.

### حفظ بيانات البريد الإلكتروني المحدثة
**نظرة عامة**: بعد إجراء التغييرات، من الضروري حفظ هذه التحديثات. يوضح هذا القسم كيفية حفظ تعديلاتك بفعالية.

#### الخطوة 1: التهيئة والحصول على الحزمة الجذرية
ابدأ بتهيئة كائن `Metadata`:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### الخطوة 2: حفظ التغييرات
احفظ تغييراتك في دليل إخراج محدد:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
هذا يضمن أن جميع التعديلات محفوظة وتظهر في الملف المحفوظ.

## التطبيقات العملية
تنفيذ هذه الميزات يمكن أن يكون مفيدًا للغاية في سيناريوهات العالم الحقيقي المختلفة:

1. **أنظمة إدارة البريد الإلكتروني** – أتمتة تحديث المستلمين لتوزيع رسائل جماعية.  
2. **منصات دعم العملاء** – تعديل موضوع البريد بسرعة لتعكس تغيّر حالة التذكرة.  
3. **أدوات التواصل الداخلي** – ضمان إلحاق جميع أعضاء الفريق بـ CC على الإعلانات الحرجة دون تعديل يدوي.

## اعتبارات الأداء
عند العمل مع كميات كبيرة من بيانات البريد الإلكتروني، ضع في اعتبارك النصائح التالية:

- عالج الملفات على دفعات من **50–100** للحفاظ على استهلاك الذاكرة أقل من **200 MB** لكل دفعة.  
- استخدم نداء `metadata.getRootPackage().getEmail()` بشكل مقتصد؛ أعد استخدام كائن `Metadata` عندما يكون ذلك ممكنًا.  
- راقب استهلاك الذاكرة في JVM باستخدام أدوات مثل VisualVM لتجنب أخطاء OutOfMemory.

## الخلاصة
لقد أصبحت الآن متمكنًا من **update email recipients java** باستخدام GroupDocs.Metadata. سواء كنت تعدل المستلمين الأساسيين، تضيف CC، أو تغير سطر الموضوع، توفر المكتبة API سريعًا وكفءً في استهلاك الذاكرة. استكشف التوثيق الكامل [documentation](https://docs.groupdocs.com/metadata/java/) لمزيد من السيناريوهات المتقدمة مثل التعامل مع المرفقات أو التحويل بين صيغ EML و MSG.

## قسم الأسئلة المتكررة
**س1**: ما إصدارات Java التي تدعمها GroupDocs.Metadata؟  
- **ج**: Java 8، 11، 17، والإصدارات الأحدث مدعومة بالكامل.

**س2**: هل يمكنني استخدام GroupDocs.Metadata بدون ترخيص؟  
- **ج**: نعم، النسخة التجريبية المجانية تعمل مع قيود؛ الترخيص المؤقت أو الدائم يزيل تلك القيود.

**س3**: كيف أتعامل مع ملفات بريد إلكتروني كبيرة بكفاءة؟  
- **ج**: عالجها على دفعات أصغر، أعد استخدام كائنات `Metadata`، وراقب استهلاك الذاكرة للبقاء تحت 200 MB لكل دفعة.

**س4**: ما أنواع الملفات الأخرى التي يدعمها GroupDocs.Metadata غير البريد الإلكتروني؟  
- **ج**: يدعم أكثر من **70** تنسيقًا بما في ذلك PDF، DOCX، XLSX، PPTX، الصور، والأرشيفات. راجع [API reference](https://reference.groupdocs.com/metadata/java/) للقائمة الكاملة.

---

**Last Updated:** 2026-05-27  
**Tested With:** GroupDocs.Metadata 23.12 for Java  
**Author:** GroupDocs  

---

## دروس ذات صلة

- [إتقان استخراج بيانات البريد الإلكتروني في Java باستخدام GroupDocs.Metadata](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [دروس بيانات البريد والاتصال لـ GroupDocs.Metadata Java](/metadata/java/email-contact-formats/)
- [كيفية استخراج عناوين URI لصور vCard باستخدام GroupDocs.Metadata في Java لإدارة جهات الاتصال بفعالية](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)