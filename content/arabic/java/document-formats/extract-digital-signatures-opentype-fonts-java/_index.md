---
date: '2026-06-22'
description: تعلم كيفية استخراج توقيع خط OpenType وتفاصيل digital signature من خطوط
  OpenType باستخدام GroupDocs.Metadata لـ Java. يساعدك هذا الدليل في تأمين مستنداتك.
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: كيفية استخراج توقيع خط OpenType في Java باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# كيفية استخراج توقيع خط OpenType في Java باستخدام GroupDocs.Metadata

في التطبيقات الحديثة، **استخراج توقيع خط OpenType** أمر ضروري لتأكيد أصالة الخط وحماية أصولك الرقمية. يوضح لك هذا الدليل، خطوة بخطوة، كيفية سحب كل من أعلام التوقيع والتفاصيل التشفيرية الكاملة من خط OpenType باستخدام **GroupDocs.Metadata for Java**. سواءً كنت تبني خط أنابيب محتوى يركز على الأمان أو تحتاج فقط إلى تدقيق مكتبة خطوط، فإن التقنيات أدناه ستجعل سير عملك موثوقًا وسريعًا.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** GroupDocs.Metadata for Java (v24.12)  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أحدث  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تعمل للتقييم؛ الترخيص الكامل مطلوب للإنتاج  
- **هل يمكنني معالجة خطوط متعددة؟** نعم – يدعم المعالجة الدفعية أو المتزامنة  
- **هل الشيفرة آمنة للخطوط المتعددة؟** أنشئ كائن `Metadata` جديد لكل خيط؛ الكائن نفسه ليس آمنًا للخطوط المتعددة  

## ما هو توقيع خط OpenType؟
إن **توقيع خط OpenType** هو كتلة تشفيرية مدمجة داخل الخط تُثبت أن الملف لم يتم تغييره منذ توقيعه. يحتوي على وقت التوقيع، سلسلة الشهادات، معرفات خوارزميات التجزئة، ومعلومات إلغاء الاختبار الاختيارية. كما يتضمن معرف خوارزمية التوقيع، سلسلة شهادات المُوقّع، وقوائم إلغاء الاختبار الاختيارية، مما يتيح تحققًا شاملاً من سلامة الخط وأصله.

## لماذا نستخدم GroupDocs.Metadata للـ Java؟
يدعم GroupDocs.Metadata **أكثر من 50 تنسيقًا للمدخلات والمخرجات** (بما في ذلك DOCX، PDF، PPTX، HTML، والعديد من أنواع الصور) ويمكنه قراءة توقيعات OpenType دون تحميل الملف بالكامل في الذاكرة، مما يتيح لك معالجة مجموعات خطوط مئات الصفحات بكفاءة.

## المتطلبات المسبقة
- **Java Development Kit (JDK):** الإصدار 8 أو أحدث.  
- **IDE:** أي بيئة تطوير متوافقة مع Java (IntelliJ IDEA، Eclipse، VS Code، إلخ).  
- **Maven:** لإدارة التبعيات.  

### المكتبات والتبعيات المطلوبة
أضف إحداثيات Maven الخاصة بـ GroupDocs.Metadata إلى ملف `pom.xml`. سيجلب ذلك الحزمة الدقيقة المطلوبة للأمثلة.

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
بدلاً من ذلك، قم بتحميل أحدث نسخة من [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية:** ابدأ بنسخة تجريبية مجانية لاستكشاف الميزات.  
- **ترخيص مؤقت:** احصل على ترخيص مؤقت عبر [صفحة ترخيص GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **شراء:** للاستخدام الإنتاجي، اشترِ ترخيصًا كاملاً.

## كيفية استخراج توقيع خط OpenType باستخدام GroupDocs.Metadata
فئة `Metadata` هي واجهة برمجة التطبيقات الأساسية في GroupDocs.Metadata للوصول إلى بيانات تعريف المستند دون تحميل الملف بالكامل.  
لقراءة توقيع الخط، أنشئ كائن `Metadata` مع مسار ملف .otf ثم وصول إلى `DigitalSignaturePackage` الخاص به. هذه الطريقة تقوم بتحميل هياكل البيانات الوصفية الضرورية فقط، متجنبةً تحليل الخط بالكامل والحفاظ على استهلاك الذاكرة منخفضًا. يجب استخدام كائن `Metadata` داخل كتلة try‑with‑resources لضمان التخلص الصحيح.

حمّل ملف الخط باستخدام `new Metadata("font.otf")` داخل كتلة try‑with‑resources. فئة `Metadata` هي نقطة الدخول في GroupDocs.Metadata لقراءة أي نوع مستند مدعوم، بما في ذلك خطوط OpenType. يغلق الكائن تلقائيًا، مما يمنع تسرب الموارد.

### كيفية استخراج أعلام التوقيع الرقمي
كائن `DigitalSignaturePackage` يجمع كل المعلومات المتعلقة بالتوقيع للخط، بما في ذلك الأعلام والتواقيع الفردية.  
**الإجابة المباشرة:** استدعِ `metadata.getDigitalSignaturePackage().getFlags()` بعد فتح الخط؛ مجموعة الأعلام المسترجعة تخبرك ما إذا كان التوقيع صالحًا، ملغى، أو يحتوي على شروط خاصة. هذه الاستدعاءة الواحدة تمنحك فحصًا سريعًا قبل الغوص في تفاصيل أعمق. تُمثَّل الأعلام كعدد تعداد يمكن فحصه لتحديد حالة التوقيع، وجود الطابع الزمني، وأي قيود سياساتية تم تطبيقها أثناء التوقيع.

1. تهيئة كائن `Metadata` مع الإشارة إلى ملف الخط الخاص بك.  
2. استرجاع `DigitalSignaturePackage`.  
3. طباعة أو تسجيل قيم الأعلام.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**شرح**  
- `documentPath` – المسار المطلق أو النسبي إلى خط OpenType.  
- تضمن كتلة try‑with‑resources إغلاق كائن `Metadata` تلقائيًا، متجنبةً تسرب الذاكرة.

### كيفية استخراج معلومات التوقيع الرقمي التفصيلية
`CmsSignature` يمثل توقيع CMS/PKCS#7 فردي مدمج في الخط، ويوفر الوصول إلى خصائصه التشفيرية.  
**الإجابة المباشرة:** كرّر عبر `metadata.getDigitalSignaturePackage().getSignatures()`؛ كل كائن `CmsSignature` يكشف عن وقت التوقيع، خوارزميات التجزئة، المحتوى المغلف، وتفاصيل الشهادة، مما يتيح لك بناء تقرير تدقيق كامل. لكل توقيع يمكنك استرجاع سلسلة شهادات المُوقّع، التحقق من خوارزمية التجزئة، واستخراج أي رموز طابع زمني لتأكيد متى تم تطبيق التوقيع.

1. إعادة استخدام تهيئة `Metadata` نفسها كما في الأعلى.  
2. التكرار عبر كل `CmsSignature` في الحزمة.  
3. استخراج الخصائص مثل `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`, و `getSignerInfo()`.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**شرح الأقسام الرئيسية**  
- **Sign Time:** الطابع الزمني عندما تم تطبيق التوقيع.  
- **Digest Algorithms & OIDs:** خوارزميات التجزئة المستخدمة (مثل SHA‑256).  
- **Encapsulated Content:** أي بيانات إضافية مغلفة داخل التوقيع.  
- **Certificates:** تواريخ الصلاحية وحجم البيانات الخام تساعد في التحقق من هوية المُوقّع.  
- **Signers:** يوفر خيارات الخوارزمية لكل مُوقّع وطوابع التوقيت الخاصة بالتوقيع.

#### نصائح استكشاف الأخطاء وإصلاحها
- إذا كان الخط يفتقر إلى توقيع رقمي، فإن `getDigitalSignaturePackage()` تُعيد `null`. تحقق دائمًا من `null` قبل الوصول إلى الأعلام أو التواقيع.  
- تأكد من أنك تستخدم نفس نسخة **GroupDocs.Metadata** المحددة في تبعية Maven لتجنب مشاكل التوافق.

## التطبيقات العملية
استخراج توقيعات خطوط OpenType ذو قيمة في العديد من السيناريوهات الواقعية:

1. **تحقق المستندات:** أتمتة الفحص للخطوط الموقعة في نظام إدارة المحتوى.  
2. **إدارة الأصول الرقمية:** التحقق من أصالة الخط قبل نشره في مشاريع العلامة التجارية.  
3. **تدقيق الأمان:** مراجعة تفاصيل التوقيع لضمان الامتثال لسياسات الأمان الداخلية.

## اعتبارات الأداء
- **إدارة الموارد:** استخدم try‑with‑resources لإغلاق كائنات `Metadata` بسرعة.  
- **المعالجة الدفعية:** عالج الخطوط في مجموعات لتقليل عبء الإدخال/الإخراج؛ يمكن لـ GroupDocs.Metadata التعامل مع آلاف الملفات دون تحميل كل خط بالكامل في الذاكرة.  
- **التزامن:** شغّل كائنات `Metadata` منفصلة في خيوط متوازية لأعباء عمل واسعة النطاق؛ المكتبة نفسها ليست آمنة للخطوط المتعددة لكل كائن، لذا عزل كل كائن في خيط منفصل.

## الأسئلة المتكررة

**س: هل يمكنني استخراج التواقيع من خط لا يحتوي على توقيع رقمي؟**  
ج: ستكون `DigitalSignaturePackage` `null`؛ تحقق دائمًا من هذا الشرط قبل الوصول إلى الأعلام أو التفاصيل.

**س: أي نسخة من GroupDocs.Metadata مطلوبة؟**  
ج: تستهدف الأمثلة النسخة **24.12**، لكن الإصدارات الأحدث تظل متوافقة مع خطوط OpenType.

**س: هل أحتاج إلى ترخيص خاص لقراءة التواقيع؟**  
ج: ترخيص تجريبي يعمل للتقييم؛ ترخيص كامل مطلوب للاستخدام الإنتاجي.

**س: كيف أتعامل مع الخطوط المخزنة في سحابة؟**  
ج: قم بتنزيل الخط إلى ملف محلي مؤقت، ثم مرّر مساره إلى `Metadata`. المكتبة تعمل مع أي ملف يمكن الوصول إليه عبر مسار محلي.

**س: هل يمكن التحقق من صحة التوقيع من الناحية التشفيرية؟**  
ج: توفر GroupDocs.Metadata بيانات التوقيع الخام؛ يمكنك تمرير سلسلة الشهادات وقيم التجزئة إلى مكتبة تشفير منفصلة لإجراء التحقق الكامل.

## الخلاصة
باتباعك لهذا الدليل، أصبحت الآن تعرف **كيفية استخراج توقيع خط OpenType** والمعلومات التفصيلية للتوقيع الرقمي باستخدام **GroupDocs.Metadata for Java**. دمج هذه الخطوات في تطبيقاتك يعزز أمان المستندات، يبسط عملية التحقق من الأصول، ويدعم مبادرات الامتثال.

**الخطوات التالية**  
- جرّب المعالجة الدفعية للتعامل مع مكتبات خطوط كبيرة بكفاءة.  
- ادمج البيانات المستخرجة مع أدوات تدقيق الأمان الخاصة بك لتقارير امتثال آلية.  
- استكشف قدرات البيانات الوصفية الأخرى في GroupDocs.Metadata، مثل تحرير أو إزالة التواقيع عند الحاجة.

---

**آخر تحديث:** 2026-06-22  
**تم الاختبار مع:** GroupDocs.Metadata 24.12  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [الوصول إلى بيانات تعريف مستند Word باستخدام GroupDocs في Java&#58; دليل شامل](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [كيفية استخراج البيانات التعريفية المخصصة من ملفات PDF باستخدام GroupDocs.Metadata في Java&#58; دليل شامل](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)