---
date: '2026-06-27'
description: GroupDocs.Metadata for Java के साथ PowerPoint प्रस्तुतियों से फ़ाइल निर्माण
  टाइमस्टैम्प प्राप्त करने और अन्य दस्तावेज़ गुणों को निकालने का तरीका सीखें। दस्तावेज़
  प्रबंधन और अनुपालन के लिए आदर्श।
keywords:
- java get file creation timestamp
- java extract document properties
- GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  headline: How to java get file creation timestamp from Presentation Files Using
    GroupDocs.Metadata
  type: TechArticle
- description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  name: How to java get file creation timestamp from Presentation Files Using GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
    text: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
  - name: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
    text: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
  - name: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
    text: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
  - name: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
    text: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
  type: HowTo
- questions:
  - answer: 'The API returns `null` for unset fields. Use a conditional expression
      like `(author != null ? author : "N/A")` to provide a fallback value.'
    question: How do I handle missing metadata properties?
  - answer: Yes, beyond the built‑in properties you can read and write custom key/value
      pairs using the same API.
    question: Can GroupDocs.Metadata extract custom metadata fields?
  - answer: GroupDocs.Metadata works with PowerPoint (`.ppt`, `.pptx`) and also supports
      PDF, Word, Excel, and many image formats.
    question: Is there support for other presentation formats?
  - answer: A compatible JDK (8 or higher) and sufficient heap memory for the size
      of the documents you process (e.g., 1 GB heap for 500‑page presentations).
    question: What are the system requirements for GroupDocs.Metadata Java?
  - answer: 'Visit the official support forum for assistance: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)'
    question: Where can I get help if I run into problems?
  type: FAQPage
title: GroupDocs.Metadata का उपयोग करके Presentation Files से फ़ाइल निर्माण टाइमस्टैम्प
  कैसे प्राप्त करें (java)
type: docs
url: /hi/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# Presentation Files से फ़ाइल निर्माण टाइमस्टैम्प प्राप्त करने के लिए Java का उपयोग कैसे करें GroupDocs.Metadata

Metadata का प्रबंधन आधुनिक दस्तावेज़ वर्कफ़्लो का एक मुख्य आधार है, और **java get file creation timestamp** अक्सर वह पहली जानकारी होती है जिसे आपको फ़ाइल की उत्पत्ति सत्यापित करने के लिए चाहिए। इस चरण‑दर‑चरण गाइड में आप जानेंगे कि PowerPoint प्रस्तुति से निर्माण टाइमस्टैम्प कैसे पढ़ें, लेखक, कंपनी और कीवर्ड जैसी अतिरिक्त प्रॉपर्टीज़ कैसे निकालें, और परिणाम को किसी भी Java‑आधारित समाधान में एकीकृत करें—चाहे वह दस्तावेज़‑प्रबंधन प्रणाली, ऑडिट‑ट्रेल जेनरेटर, या अनुपालन डैशबोर्ड हो।

## त्वरित उत्तर
- **java get file creation timestamp क्या मतलब है?** यह फ़ाइल की मूल निर्माण तिथि को Java कोड के माध्यम से मेटाडेटा API का उपयोग करके प्राप्त करने को दर्शाता है।  
- **कौन सी लाइब्रेरी इसे संभालती है?** GroupDocs.Metadata for Java एक साफ़, फ़ॉर्मेट‑अज्ञेय API प्रदान करती है टाइमस्टैम्प और अन्य बिल्ट‑इन प्रॉपर्टीज़ पढ़ने के लिए।  
- **उत्पादन के लिए मुझे लाइसेंस चाहिए?** हाँ—उत्पादन के लिए एक स्थायी लाइसेंस आवश्यक है; विकास और परीक्षण के लिए एक मुफ्त ट्रायल पर्याप्त है।  
- **क्या मैं एक साथ अन्य मेटाडेटा निकाल सकता हूँ?** बिल्कुल—लेखक, कंपनी, श्रेणी, कीवर्ड, और कस्टम फ़ील्ड सभी एक ही API के माध्यम से उपलब्ध हैं।  
- **कौन सा Java संस्करण समर्थित है?** JDK 8 या उससे ऊपर (Java 11, 17, और बाद के संस्करणों के साथ संगत)।

## “java get file creation timestamp” क्या है?
`java get file creation timestamp` वह ऑपरेशन है जो दस्तावेज़ के भीतर संग्रहीत **Created** मेटाडेटा फ़ील्ड तक पहुँचता है, जो फ़ाइल के पहले उत्पन्न होने के सटीक क्षण को रिकॉर्ड करता है। यह टाइमस्टैम्प संस्करण नियंत्रण, ऑडिट ट्रेल और नियामक अनुपालन के लिए महत्वपूर्ण है क्योंकि यह सामग्री के उत्पन्न होने के समय का अपरिवर्तनीय रिकॉर्ड प्रदान करता है।

## दस्तावेज़ प्रॉपर्टीज़ निकालने के लिए GroupDocs.Metadata for Java का उपयोग क्यों करें?
GroupDocs.Metadata दर्जनों फ़ाइल फ़ॉर्मेट्स के लो‑लेवल पार्सिंग को एब्स्ट्रैक्ट करता है, जिससे आप व्यवसायिक लॉजिक पर ध्यान केंद्रित कर सकते हैं। यह **50 से अधिक इनपुट और आउटपुट फ़ॉर्मेट्स** का समर्थन करता है—जैसे .pptx, .ppt, .pdf, .docx, .xlsx, और कई इमेज प्रकार—और पूरी फ़ाइल को मेमोरी में लोड किए बिना सैकड़ों‑पृष्ठीय प्रस्तुतियों को प्रोसेस कर सकता है, जिससे बड़े‑पैमाने पर पर्यावरण के लिए मेमोरी‑कुशल समाधान मिलता है।

## पूर्वापेक्षाएँ
- **GroupDocs.Metadata for Java** संस्करण 24.12 या बाद का।  
- Java Development Kit (JDK 8 या नया)।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- Java फ़ाइल I/O और एक्सेप्शन हैंडलिंग की बुनियादी परिचितता।

## GroupDocs.Metadata for Java सेट अप करना

### Maven सेटअप
यदि आप Maven के साथ डिपेंडेंसीज़ प्रबंधित करते हैं, तो अपने `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

### सीधे डाउनलोड
वैकल्पिक रूप से, आप आधिकारिक रिलीज़ पेज से लाइब्रेरी डाउनलोड कर सकते हैं:  
[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

#### लाइसेंस प्राप्त करने के चरण
- **Free Trial:** API का अन्वेषण करने के लिए एक मुफ्त ट्रायल से शुरू करें।  
- **Temporary License:** अनियंत्रित परीक्षण के लिए एक अस्थायी कुंजी प्राप्त करें।  
- **Purchase:** उत्पादन परिनियोजन के लिए पूर्ण लाइसेंस प्राप्त करें।

### बुनियादी इनिशियलाइज़ेशन और सेटअप
`Metadata` GroupDocs.Metadata for Java में मुख्य एंट्री पॉइंट क्लास है जो दस्तावेज़ की मेटाडेटा तक पहुँच प्रदान करता है। एक बार डिपेंडेंसी स्थापित हो जाने पर, एक `Metadata` ऑब्जेक्ट बनाएं और उसे अपनी प्रस्तुति फ़ाइल की ओर इंगित करें:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## प्रस्तुति से java get file creation timestamp कैसे प्राप्त करें और अन्य प्रॉपर्टीज़ निकालें?
`new Metadata("sample.pptx")` के साथ प्रस्तुति लोड करें, फिर उपयुक्त गेटर मेथड्स—`getCreatedTime()`, `getAuthor()`, `getCompany()` आदि—को कॉल करके प्रत्येक जानकारी प्राप्त करें। यह एक‑ऑब्जेक्ट दृष्टिकोण आपको कुछ ही कोड लाइनों में सभी बिल्ट‑इन प्रॉपर्टीज़ निकालने की सुविधा देता है, जिससे फ़ॉर्मेट‑विशिष्ट पार्सर्स की आवश्यकता समाप्त हो जाती है।

### लेखक जानकारी निकालना
`getAuthor()` दस्तावेज़ की मेटाडेटा में संग्रहीत लेखक नाम लौटाता है, या यदि फ़ील्ड खाली है तो `null`।

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*यह मेथड एक साधारण `String` लौटाता है जिसे आप लॉग, डिस्प्ले या डेटाबेस में स्टोर कर सकते हैं।*

### निर्माण समय निकालना (java get file creation timestamp)
`getCreatedTime()` एक `java.util.Date` ऑब्जेक्ट प्रदान करता है जो फ़ाइल के पहले बनाए जाने के सटीक क्षण को दर्शाता है—बिल्कुल वही जो “java get file creation timestamp” वर्णन करता है।

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*आप इस `Date` को `SimpleDateFormat` या नए `java.time` API के साथ फ़ॉर्मेट कर सकते हैं डिस्प्ले या तुलना के लिए।*

### कंपनी जानकारी निकालना
`getCompany()` प्रस्तुति से जुड़ी संगठन का नाम लौटाता है, या यदि फ़ील्ड सेट नहीं है तो `null`।

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*यह मान दस्तावेज़ों को कॉर्पोरेट रिकॉर्ड या CRM एंटिटीज़ से लिंक करने में उपयोगी है।*

### अतिरिक्त मेटाडेटा जिसे आप निकाल सकते हैं
आप समान रूप से अन्य बिल्ट‑इन फ़ील्ड्स जैसे **Category**, **Keywords**, **Last Printed Date**, और **Application Name** को `getCategory()`, `getKeywords()` आदि मेथड्स के माध्यम से प्राप्त कर सकते हैं। प्रत्येक गेटर समान पैटर्न का पालन करता है: एक संक्षिप्त, null‑सेफ़ रिटर्न वैल्यू जो तुरंत उपयोग के लिए तैयार होती है।

## व्यावहारिक अनुप्रयोग
1. **Document Management Systems:** प्रस्तुतियों को लेखक, कंपनी, या निर्माण तिथि के आधार पर इंडेक्स करें तेज़ खोज और पुनर्प्राप्ति के लिए।  
2. **Compliance Auditing:** सुनिश्चित करें कि प्रत्येक संग्रहित स्लाइड डेक में कानूनी रखरखाव से पहले एक निर्माण टाइमस्टैम्प शामिल हो।  
3. **Automated Reporting:** दैनिक सारांश बनाएं जो बताता है किसने प्रत्येक डेक बनाया और कब, डेटा को BI डैशबोर्ड में फीड करें।  
4. **CRM Integration:** `Company` मेटाडेटा को मौजूदा क्लाइंट रिकॉर्ड्स से मिलाएँ, जिससे प्रस्तुतियों को ग्राहक प्रोफ़ाइल से सहजता से जोड़ सकें।

## प्रदर्शन संबंधी विचार
- **Parallel Processing:** हजारों फ़ाइलों से मेटाडेटा निकालते समय, प्रत्येक एक्सट्रैक्शन को अलग थ्रेड में चलाएँ या थ्रेड पूल का उपयोग करके CPU उपयोग को अधिकतम करें।  
- **Resource Management:** try‑with‑resources (जैसा दिखाया गया) का उपयोग करके `Metadata` ऑब्जेक्ट को स्वचालित रूप से बंद करें और नेटिव रिसोर्सेज़ मुक्त करें।  
- **Batch Extraction:** GroupDocs.Metadata बल्क ऑपरेशन्स का समर्थन करता है; फ़ाइल पाथ्स के संग्रह पर इटररेट करें और जहाँ संभव हो एक ही `Metadata` इंस्टेंस को पुन: उपयोग करें ओवरहेड कम करने के लिए।

## सामान्य समस्याएँ और समाधान
- **Missing Metadata:** यदि कोई getter `null` लौटाता है, तो स्रोत फ़ाइल में वह प्रॉपर्टी नहीं है। `null` मानों से बचने के लिए कंडीशनल चेक या डिफ़ॉल्ट फ़ॉलबैक का उपयोग करें।  
- **Unsupported Format:** सुनिश्चित करें कि फ़ाइल समर्थित PowerPoint फ़ॉर्मेट (`.pptx` या `.ppt`) है। असमर्थित प्रकार लोड करने का प्रयास करने पर `UnsupportedFormatException` फेंका जाता है।  
- **License Errors:** सुनिश्चित करें कि आपका लाइसेंस फ़ाइल क्लासपाथ पर सही जगह पर रखी गई है या ट्रायल अवधि समाप्त नहीं हुई है; अन्यथा API `LicenseException` उठाएगा।

## अक्सर पूछे जाने वाले प्रश्न

**Q: How do I handle missing metadata properties?**  
A: API अनसेट फ़ील्ड्स के लिए `null` लौटाता है। एक कंडीशनल एक्सप्रेशन जैसे `(author != null ? author : "N/A")` का उपयोग करके फ़ॉलबैक वैल्यू प्रदान करें।

**Q: Can GroupDocs.Metadata extract custom metadata fields?**  
A: हाँ, बिल्ट‑इन प्रॉपर्टीज़ के अलावा आप समान API का उपयोग करके कस्टम की/वैल्यू जोड़े पढ़ और लिख सकते हैं।

**Q: Is there support for other presentation formats?**  
A: GroupDocs.Metadata PowerPoint (`.ppt`, `.pptx`) के साथ काम करता है और PDF, Word, Excel, तथा कई इमेज फ़ॉर्मेट्स को भी सपोर्ट करता है।

**Q: What are the system requirements for GroupDocs.Metadata Java?**  
A: एक संगत JDK (8 या ऊपर) और प्रोसेस किए जाने वाले दस्तावेज़ों के आकार के लिए पर्याप्त हीप मेमोरी (उदाहरण: 500‑पृष्ठीय प्रस्तुतियों के लिए 1 GB हीप) आवश्यक है।

**Q: Where can I get help if I run into problems?**  
A: सहायता के लिए आधिकारिक सपोर्ट फ़ोरम देखें: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## संसाधन

- **Documentation:** https://docs.groupdocs.com/metadata/java/
- **API Reference:** https://reference.groupdocs.com/metadata/java/
- **Download:** https://releases.groupdocs.com/metadata/java/
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
- **Free Support:** https://forum.groupdocs.com/c/metadata/
- **Temporary License:** https://purchase.groupdocs.com/temporary-license/

By following this guide, you now know how to **java get file creation timestamp** and **java extract document properties** from PowerPoint presentations using GroupDocs.Metadata. Incorporate these snippets into your projects to boost document intelligence, streamline compliance workflows, and empower downstream analytics.

---

**Last Updated:** 2026-06-27  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs

## संबंधित ट्यूटोरियल

- [How to Extract Metadata from PowerPoint Presentations Using GroupDocs.Metadata in Java](/metadata/java/working-with-metadata/extract-presentation-metadata-groupdocs-java/)
- [Automate Java Metadata Updates by Date Using GroupDocs.Metadata for Efficient File Management](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)
- [Master Metadata Management: Detect Document Properties & Encryption Status with GroupDocs.Metadata for Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)