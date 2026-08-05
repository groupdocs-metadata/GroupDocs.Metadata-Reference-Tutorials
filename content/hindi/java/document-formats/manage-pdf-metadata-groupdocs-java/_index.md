---
date: '2026-08-05'
description: GroupDocs.Metadata for Java का उपयोग करके PDF संस्करण java का पता लगाना
  और PDF metadata अपडेट करना सीखें। इसमें संस्करण का पता लगाना, properties पढ़ना,
  और metadata संपादन शामिल है।
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: GroupDocs.Metadata के साथ PDF संस्करण java का पता लगाएँ और PDF metadata
  अपडेट करें। Step‑by‑step Java गाइड संस्करण का पता लगाना, properties पढ़ना, और metadata
  संपादन दिखाता है।
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: PDF संस्करण java का पता लगाएँ और PDF metadata अपडेट करें
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: PDF संस्करण java का पता लगाएँ और PDF metadata अपडेट करें
type: docs
url: /hi/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# PDF संस्करण जावा का पता लगाएँ और PDF मेटाडेटा अपडेट करें

प्रोग्रामेटिक रूप से PDF फ़ाइलों का प्रबंधन अक्सर इसका मतलब होता है कि आपको **detect PDF version java** और **update PDF metadata** की आवश्यकता होती है — लेखक, शीर्षक, निर्माण तिथि, या यहाँ तक कि PDF संस्करण स्वयं। असंगत मेटाडेटा रेंडरिंग गड़बड़ियों का कारण बन सकता है या बड़े रिपॉज़िटरी में दस्तावेज़ों को खोजने में कठिनाई पैदा कर सकता है। यह ट्यूटोरियल आपको **GroupDocs.Metadata** for Java का उपयोग करके PDF संस्करण का पता लगाने और PDF मेटाडेटा अपडेट करने की प्रक्रिया दिखाता है, जिससे आप अपने PDF को व्यवस्थित, खोज योग्य और किसी भी व्यूअर के साथ संगत रख सकते हैं।

## त्वरित उत्तर
- **“update PDF metadata” का क्या अर्थ है?** Adding, modifying, or removing information stored inside a PDF file.  
- **Java में इसके लिए कौन‑सी लाइब्रेरी मदद करती है?** GroupDocs.Metadata.  
- **क्या मैं PDF संस्करण भी पता लगा सकता हूँ?** Yes, the same API provides version detection.  
- **क्या मुझे लाइसेंस चाहिए?** A free trial works for evaluation; a paid license is required for production.  
- **कौन‑सी Java संस्करण आवश्यक है?** JDK 8 or newer.

## PDF मेटाडेटा अपडेट करना क्या है?
PDF मेटाडेटा अपडेट करना मतलब प्रोग्रामेटिक रूप से PDF फ़ाइल में एम्बेडेड वर्णनात्मक जानकारी को पढ़ना और लिखना है — जैसे लेखक, शीर्षक, विषय, और कस्टम प्रॉपर्टीज़। उचित मेटाडेटा खोज योग्यता, अनुपालन, और दस्तावेज़ प्रबंधन प्रणालियों में संस्करण नियंत्रण को सुधारता है। सटीक मेटाडेटा स्वचालित इंडेक्सिंग, अनुपालन रिपोर्टिंग, और दस्तावेज़ प्रबंधन प्रणालियों में संस्करण ट्रैकिंग को भी सक्षम बनाता है।

## Java में PDF संस्करण का पता क्यों लगाएँ?
PDF संस्करण का पता लगाने से आप यह सत्यापित कर सकते हैं कि फ़ाइल लक्ष्य व्यूअर पर सही ढंग से रेंडर होगी और यह डाउनस्ट्रीम प्रोसेसिंग आवश्यकताओं को पूरा करती है। यह जानना कि PDF संस्करण 1.4, 1.7, या नया है, आपको आर्काइविंग, प्रकाशन, या दस्तावेज़ को परिवर्तित करने से पहले संगतता नियम लागू करने में मदद करता है।

## आवश्यकताएँ
- **Java Development Kit (JDK)** 8 या उससे ऊपर।  
- **Maven** डिपेंडेंसी मैनेजमेंट के लिए (या आप JAR सीधे डाउनलोड कर सकते हैं)।  
- Java फ़ाइल I/O की बुनियादी परिचितता।

## GroupDocs.Metadata for Java सेटअप करना
### Maven सेटअप
`pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

### सीधा डाउनलोड
वैकल्पिक रूप से, आधिकारिक रिलीज़ पेज से नवीनतम JAR डाउनलोड करें: [GroupDocs.Metadata for Java रिलीज़](https://releases.groupdocs.com/metadata/java/).

#### लाइसेंस प्राप्त करने के चरण
- **Free trial** – बिना लागत के प्रयोग शुरू करें।  
- **Temporary license** – आवश्यकता पड़ने पर ट्रायल बढ़ाएँ।  
- **Purchase** – प्रोडक्शन उपयोग के लिए पूर्ण‑फ़ीचर लाइसेंस प्राप्त करें।

## बुनियादी इनिशियलाइज़ेशन और सेटअप
`Metadata` क्लास GroupDocs.Metadata में PDF फ़ाइलों के साथ काम करने का एंट्री पॉइंट है। यह एक कंटेनर का प्रतिनिधित्व करता है जो आपको दस्तावेज़ प्रॉपर्टीज़, संस्करण जानकारी, और कस्टम XMP डेटा तक पढ़ने/लिखने की पहुंच देता है।

एक `Metadata` इंस्टेंस बनाएँ जो आपके PDF फ़ाइल की ओर इशारा करता हो:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

अब आप प्रॉपर्टीज़ पढ़ने, संस्करण का पता लगाने, और मेटाडेटा अपडेट करने के लिए तैयार हैं।

## PDF संस्करण जावा का पता कैसे लगाएँ
`new Metadata("sample.pdf")` के साथ अपना PDF लोड करें और `getRootPackage().getVersion()` को कॉल करें — यह मेथड एक ही कॉल में सटीक PDF संस्करण (जैसे 1.4, 1.7) लौटाता है। यह सीधा उत्तर आपको आगे की प्रोसेसिंग से पहले शीघ्रता से संगतता सत्यापित करने में मदद करता है। संस्करण स्ट्रिंग फ़ाइल द्वारा अनुसरण किए गए PDF स्पेसिफिकेशन लेवल को दर्शाती है, जो संगतता जांच के लिए महत्वपूर्ण है।  
`getVersion()` PDF संस्करण को स्ट्रिंग के रूप में लौटाता है, जैसे "1.4" या "1.7".

### चरण‑दर‑चरण मार्गदर्शिका
1. **Open the PDF** – `Metadata` ऑब्जेक्ट को इंस्टैंशिएट करें (ऊपर के इनिशियलाइज़ेशन देखें)।  
2. **Access the PDF‑specific root package** – `metadata.getRootPackage()` को कॉल करें।  
3. **Retrieve the version** – `pdfRoot.getVersion()` को इनवोक करें; लौटाई गई स्ट्रिंग में संस्करण संख्या होती है।

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Pro tip:** PDF बैच प्रोसेस करने से पहले संगतता जांच लागू करने के लिए `version` मान का उपयोग करें।

#### समस्या निवारण
- फ़ाइल पाथ सत्यापित करें; गलत पाथ `FileNotFoundException` फेंकेगा।  
- सुनिश्चित करें कि GroupDocs.Metadata संस्करण आपके JDK से मेल खाता है (उदाहरण में 24.12 उपयोग किया गया है)।

## Java में PDF प्रॉपर्टीज़ कैसे पढ़ें
`DocumentInfo` पूर्ण दस्तावेज़ लोड किए बिना मानक PDF मेटाडेटा फ़ील्ड्स तक पहुंच प्रदान करता है। `DocumentInfo` क्लास लेखक, शीर्षक, और निर्माण तिथि जैसी मानक PDF प्रॉपर्टीज़ तक पहुंच देता है। यह एक हल्का रैपर है जो पूरे दस्तावेज़ को मेमोरी में लोड किए बिना मेटाडेटा पढ़ता है।

खोले हुए `Metadata` ऑब्जेक्ट से एक `DocumentInfo` इंस्टेंस बनाएँ:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

आप फिर `getAuthor()`, `getTitle()`, और `getCreationDate()` जैसे गेटर्स को कॉल करके मान प्राप्त कर सकते हैं।

## Java में PDF मेटाडेटा कैसे अपडेट करें
PDF लोड करें (ऊपर जैसा), `DocumentInfo` पैकेज प्राप्त करें, इच्छित फ़ील्ड्स को संशोधित करें, और परिवर्तन सहेजें। यह ऑपरेशन मौजूदा मेटाडेटा ब्लॉक को ओवरराइट करता है जबकि दस्तावेज़ के बाकी हिस्से को संरक्षित रखता है। फ़ील्ड्स संशोधित करने के बाद, `save()` को कॉल करने से परिवर्तन फ़ाइल में वापस लिखे जाते हैं जबकि कंटेंट स्ट्रीम्स संरक्षित रहते हैं।

`DocumentInfo` क्लास GroupDocs.Metadata का वह ऑब्जेक्ट है जो PDF‑स्तर की प्रॉपर्टीज़ जैसे लेखक, शीर्षक, विषय, और कस्टम XMP फ़ील्ड्स को संपादित करने के लिए उपयोग होता है।

मेटाडेटा फ़ील्ड्स अपडेट करें:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Note:** सेट्टर कॉल्स पहले दिखाए गए गेटर्स के समान पैटर्न का पालन करते हैं, जिससे API सहज और सुसंगत बनती है।

#### सामान्य जाल
- किसी PDF पर मेटाडेटा संशोधित करने का प्रयास करना जो लक्ष्य प्रॉपर्टी नहीं रखता, `null` लौटाता है — नया मान सेट करने से पहले हमेशा `null` की जाँच करें।  
- बड़े PDF को बढ़े हुए JVM हीप की आवश्यकता हो सकती है; बैच अपडेट के दौरान मेमोरी उपयोग की निगरानी रखें।

## व्यावहारिक उपयोग केस
1. **Compliance audits** – सभी PDFs न्यूनतम संस्करण (जैसे 1.7) को कानूनी फ़ाइलिंग से पहले पूरा करते हैं, यह सत्यापित करें।  
2. **Automated archiving** – आसान पुनः प्राप्ति के लिए PDFs को लेखक, विभाग, और निर्माण तिथि के साथ टैग करें।  
3. **Document management integration** – PDFs को कस्टम प्रॉपर्टीज़ के साथ समृद्ध करें जिन्हें DMS प्लेटफ़ॉर्म इंडेक्स कर सकते हैं।  
4. **Report generation** – स्वचालित रूप से जनरेट किए गए रिपोर्ट में संस्करण जानकारी डालें।  
5. **Cross‑platform testing** – संस्करण असंगतियों का पता लगाएँ जो पुराने व्यूअर्स पर रेंडरिंग समस्याएँ पैदा कर सकते हैं।

## प्रदर्शन टिप्स
- **Use try‑with‑resources** (जैसा दिखाया गया है) `Metadata` ऑब्जेक्ट्स को स्वचालित रूप से बंद करने के लिए।  
- **Batch process** लूप में कई फ़ाइलों को प्रोसेस करके ओवरहेड कम करें।  
- **Monitor heap** बहुत बड़े PDFs के लिए; यदि मेमोरी सीमा तक पहुँचते हैं तो उन्हें चंक्स में प्रोसेस करने पर विचार करें।  
- **GroupDocs.Metadata supports 50+ input and output formats** और यह मल्टी‑हंड्रेड‑पेज PDFs से मेटाडेटा पढ़ सकता है बिना पूरे फ़ाइल को मेमोरी में लोड किए, जिससे मानक सर्वर हार्डवेयर पर तेज़ प्रदर्शन मिलता है।

## अक्सर पूछे जाने वाले प्रश्न
**Q: क्या मैं पासवर्ड‑सुरक्षित PDFs पर मेटाडेटा अपडेट कर सकता हूँ?**  
A: हाँ, लेकिन `Metadata` ऑब्जेक्ट बनाते समय आपको पासवर्ड प्रदान करना होगा।

**Q: क्या GroupDocs.Metadata कस्टम XMP प्रॉपर्टीज़ का समर्थन करता है?**  
A: बिल्कुल। आप उसी API के माध्यम से कस्टम XMP फ़ील्ड्स को पढ़ और लिख सकते हैं।

**Q: क्या PDF संस्करण स्वयं बदलना संभव है?**  
A: लाइब्रेरी संस्करण रिपोर्ट कर सकती है; इसे बदलने के लिए दस्तावेज़ को अलग संस्करण प्रोफ़ाइल के साथ सहेजना आवश्यक है, जो अतिरिक्त सहेजने विकल्पों के माध्यम से समर्थित है।

**Q: यदि PDF में कोई मौजूदा मेटाडेटा नहीं है तो क्या होता है?**  
A: गेटर्स `null` लौटाएंगे। आप सुरक्षित रूप से सेटर्स को कॉल करके नई मेटाडेटा एंट्री बना सकते हैं।

**Q: क्या व्यावसायिक उपयोग के लिए कोई लाइसेंस प्रतिबंध हैं?**  
A: प्रोडक्शन डिप्लॉयमेंट के लिए एक कमर्शियल लाइसेंस आवश्यक है; ट्रायल केवल मूल्यांकन उद्देश्यों के लिए सीमित है।

**अंतिम अपडेट:** 2026-08-05  
**परीक्षण किया गया:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल
- [दस्तावेज़ प्रबंधन के लिए Java में GroupDocs.Metadata के साथ PDF मेटाडेटा को कुशलतापूर्वक अपडेट करें](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [मेटाडेटा प्रबंधन में महारत: GroupDocs.Metadata for Java के साथ दस्तावेज़ प्रॉपर्टीज़ और एन्क्रिप्शन स्थिति का पता लगाएँ](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [डॉक्यूमेंट प्रीव्यू Java बनाएं – GroupDocs.Metadata ट्यूटोरियल](/metadata/java/document-formats/)