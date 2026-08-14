---
date: '2026-06-17'
description: GroupDocs.Metadata for Java का उपयोग करके Java में Diagram Metadata को
  अपडेट करना और document properties सेट करना सीखें। सर्वोत्तम प्रथाओं के साथ चरण-दर-चरण
  गाइड।
keywords:
- update diagram metadata java
- set document properties java
- groupdocs metadata java tutorial
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to update diagram metadata java and set document properties
    java using GroupDocs.Metadata for Java. Step‑by‑step guide with best practices.
  headline: How to Update Diagram Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to update diagram metadata java and set document properties
    java using GroupDocs.Metadata for Java. Step‑by‑step guide with best practices.
  name: How to Update Diagram Metadata Java with GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems** – Tag diagrams with project IDs, department
      codes, or retention dates.'
    text: '**Document Management Systems** – Tag diagrams with project IDs, department
      codes, or retention dates.'
  - name: '**Collaboration Platforms** – Store reviewer names and status flags directly
      inside the file.'
    text: '**Collaboration Platforms** – Store reviewer names and status flags directly
      inside the file.'
  - name: '**Regulatory Compliance** – Embed audit trails (e.g., “ApprovedBy”, “ComplianceLevel”)
      for easy extraction during audits.'
    text: '**Regulatory Compliance** – Embed audit trails (e.g., “ApprovedBy”, “ComplianceLevel”)
      for easy extraction during audits.'
  type: HowTo
- questions:
  - answer: Metadata in diagrams refers to built‑in and custom properties (author,
      creation date, tags, etc.) that describe the file without altering its visual
      content.
    question: What is metadata in diagrams?
  - answer: Yes—iterate over a `Map<String,String>` and call `set` for each entry
      within the same `Metadata` session.
    question: Can I update multiple metadata properties at once?
  - answer: It supports over 30 popular diagram formats, including VSDX, VDX, VSSX,
      and VSTX. Check the official compatibility matrix for newer or niche formats.
    question: Is GroupDocs.Metadata Java compatible with all diagram formats?
  - answer: Wrap your code in a `try‑catch` block and handle specific exceptions such
      as `FileNotFoundException`, `UnsupportedFormatException`, or a generic `Exception`
      for unexpected errors.
    question: How do I handle exceptions when updating metadata?
  - answer: Options include a free trial, temporary evaluation licenses, and full
      commercial licenses for unlimited production use.
    question: What are the licensing options for GroupDocs.Metadata Java?
  type: FAQPage
title: GroupDocs.Metadata के साथ Java में Diagram Metadata कैसे अपडेट करें
type: docs
url: /hi/java/diagram-formats/update-diagram-metadata-groupdocs-java/
weight: 1
---

# डायग्राम मेटाडेटा जावा को GroupDocs.Metadata के साथ अपडेट करें

डायग्राम फ़ाइलों को **updating diagram metadata java** द्वारा सुधारना एक सामान्य आवश्यकता है जब आपको खोज, अनुपालन, या सहयोग के लिए कस्टम जानकारी एम्बेड करनी होती है। इस ट्यूटोरियल में आप सीखेंगे कि कैसे **set document properties java** को VSDX (Visio) फ़ाइलों के भीतर GroupDocs.Metadata लाइब्रेरी का उपयोग करके किया जाता है। हम पूर्ण कार्यप्रवाह—प्रोजेक्ट सेटअप से लेकर ट्रबलशूटिंग तक—परिचित कराएंगे ताकि आप वास्तविक‑दुनिया के अनुप्रयोगों में इस तकनीक को लागू कर सकें।

## त्वरित उत्तर
- **कौन सी लाइब्रेरी आवश्यक है?** GroupDocs.Metadata for Java (v24.12 या नया)।  
- **कौन से डायग्राम फ़ॉर्मेट समर्थित हैं?** VSDX, VDX, VSSX, VSTX और अन्य फ़ॉर्मेट जो संगतता मैट्रिक्स में सूचीबद्ध हैं।  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए एक स्थायी लाइसेंस आवश्यक है।  
- **कोड की कितनी पंक्तियाँ?** फ़ाइल लोड करने, प्रॉपर्टीज़ संशोधित करने और सहेजने के लिए 30 से कम पंक्तियाँ।  
- **क्या यह थ्रेड‑सेफ़ है?** हाँ—प्रत्येक थ्रेड को अपना `Metadata` ऑब्जेक्ट बनाना चाहिए।

## “update diagram metadata java” क्या है?

Updating diagram metadata java का मतलब है प्रोग्रामेटिक रूप से एक डायग्राम फ़ाइल को पढ़ना, उसकी बिल्ट‑इन या कस्टम प्रॉपर्टीज़ को संशोधित करना, और बदलावों को फ़ाइल में वापस सहेजना। इस जानकारी को सीधे डायग्राम के भीतर एम्बेड करने से डाउनस्ट्रीम सिस्टम बिना विज़ुअल कंटेंट खोले मानों को क्वेरी कर सकते हैं, जिससे ऑटोमेशन सरल होता है, गवर्नेंस बेहतर होता है, और उन्नत खोज तथा अनुपालन परिदृश्यों को समर्थन मिलता है।

## GroupDocs.Metadata के साथ document properties java सेट क्यों करें?

डायग्राम को लोड करना, उसकी प्रॉपर्टीज़ बदलना, और उसे वापस सहेजना केवल दो API कॉल्स में किया जा सकता है। GroupDocs.Metadata केवल फ़ाइल स्ट्रीम को प्रोसेस करता है, जिसका अर्थ है **200‑पेज़ VSDX फ़ाइल के लिए भी मेमोरी उपयोग 5 MB से कम रहता है**, और ऑपरेशन सामान्य सर्वर हार्डवेयर पर एक सेकंड से कम समय में समाप्त हो जाता है। लाइब्रेरी **30 से अधिक डायग्राम फ़ॉर्मेट** का समर्थन भी करती है और भ्रष्ट आउटपुट को रोकने के लिए बिल्ट‑इन वैलिडेशन प्रदान करती है।

## पूर्वापेक्षाएँ

- **Java Development Kit (JDK 8 या बाद का)** एक IDE जैसे IntelliJ IDEA या Eclipse के साथ।  
- **GroupDocs.Metadata 24.12+** (नवीनतम स्थिर रिलीज़)।  
- जावा और फ़ाइल मेटाडेटा की अवधारणा का बुनियादी ज्ञान।

## GroupDocs.Metadata को जावा के लिए सेटअप करना

### Maven का उपयोग करके

अपने `pom.xml` में GroupDocs रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

वैकल्पिक रूप से आधिकारिक रिलीज़ पेज से नवीनतम JAR डाउनलोड करें:  
[GroupDocs.Metadata जावा रिलीज़](https://releases.groupdocs.com/metadata/java/)

#### लाइसेंस प्राप्त करने के चरण

- **Free Trial** – लाइसेंस कुंजी के बिना सभी फीचर एक्सप्लोर करें।  
- **Temporary License** – विस्तारित मूल्यांकन के लिए समय‑सीमित कुंजी का अनुरोध करें।  
- **Full Purchase** – प्रोडक्शन डिप्लॉयमेंट के लिए स्थायी लाइसेंस प्राप्त करें।

लाइब्रेरी आपके क्लासपाथ पर होने के बाद, आप इसका उपयोग शुरू कर सकते हैं:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        // Load your document and start metadata operations here
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVsdx")) {
            System.out.println("Document loaded successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## कस्टम प्रॉपर्टीज़ को अपडेट करने के लिए चरण-दर-चरण गाइड

### 1. डायग्राम दस्तावेज़ लोड करें

`Metadata` क्लास डायग्राम मेटाडेटा पढ़ने और लिखने का एंट्री पॉइंट है। यह मेमोरी में एकल डायग्राम फ़ाइल का प्रतिनिधित्व करता है और प्रॉपर्टी कलेक्शन्स को एक्सपोज़ करता है।

पहले, अपने VSDX फ़ाइल की ओर इशारा करने वाला एक `Metadata` इंस्टेंस बनाएँ:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.DiagramRootPackage;

public class DiagramUpdateCustomProperties {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVsdx")) {
            // Proceed with accessing and modifying properties
        }
    }
}
```

### 2. रूट पैकेज तक पहुँचें

`DiagramRootPackage` प्रॉपर्टी कलेक्शन्स और कस्टम पार्ट्स जैसे डॉक्यूमेंट‑लेवल स्ट्रक्चर तक पहुँच प्रदान करता है। यह सभी डायग्राम मेटाडेटा के लिए टॉप‑लेवल कंटेनर है।

`Metadata` ऑब्जेक्ट से रूट पैकेज प्राप्त करें:

```java
// Obtain the root package of the document
DiagramRootPackage root = metadata.getRootPackageGeneric();
```

### 3. कस्टम प्रॉपर्टीज़ सेट करें (set document properties java)

`DocumentProperties` वह कलेक्शन है जो बिल्ट‑इन और यूज़र‑डिफाइंड दोनों की/वैल्यू पेयर्स रखता है। प्रॉपर्टी जोड़ने या ओवरराइट करने के लिए इसका `set` मेथड उपयोग करें।

“ProjectId” जैसी कस्टम प्रॉपर्टी जोड़ें या अपडेट करें:

```java
// Set a custom property named 'customProperty1'
root.getDocumentProperties().set("customProperty1", "Your Value Here");
```

**Method breakdown**

- `getDocumentProperties()` – वह कलेक्शन लौटाता है जो बिल्ट‑इन और कस्टम दोनों प्रॉपर्टीज़ रखता है।  
- `set(String key, String value)` – यदि प्रॉपर्टी मौजूद नहीं है तो उसे जोड़ता है या मौजूदा मान को ओवरराइट करता है।

### 4. सहेजें और बंद करें (स्वचालित रूप से संभाला जाता है)

चूँकि `Metadata` `AutoCloseable` को इम्प्लीमेंट करता है, `try‑with‑resources` ब्लॉक स्वचालित रूप से बदलावों को सहेजता है और ब्लॉक से बाहर निकलते ही फ़ाइल हैंडल्स को रिलीज़ कर देता है।

## सामान्य समस्याएँ और ट्रबलशूटिंग टिप्स

- **FileNotFoundException** – पाथ (`YOUR_DOCUMENT_DIRECTORY/InputVsdx`) सही है और फ़ाइल एक्सेसिबल है, यह सत्यापित करें।  
- **Unsupported Format** – सुनिश्चित करें कि आपका GroupDocs.Metadata संस्करण आप जिस विशिष्ट डायग्राम फ़ॉर्मेट का उपयोग कर रहे हैं, उसे सपोर्ट करता है।  
- **Permission Errors** – विशेषकर Linux/macOS पर JVM को पर्याप्त फ़ाइल सिस्टम परमिशन के साथ चलाएँ।

## व्यावहारिक अनुप्रयोग

1. **Document Management Systems** – डायग्राम को प्रोजेक्ट आईडी, डिपार्टमेंट कोड, या रिटेंशन डेट्स से टैग करें।  
2. **Collaboration Platforms** – रिव्यूअर नाम और स्टेटस फ्लैग्स को सीधे फ़ाइल में स्टोर करें।  
3. **Regulatory Compliance** – ऑडिट ट्रेल्स (जैसे, “ApprovedBy”, “ComplianceLevel”) को एम्बेड करें ताकि ऑडिट के दौरान आसान एक्सट्रैक्शन हो सके।

## प्रदर्शन विचार

- **Load Only Needed Parts** – `Metadata` API का उपयोग करके केवल प्रॉपर्टी कलेक्शन को फ़ेच करें, पूरी डायग्राम इमेज डेटा नहीं।  
- **Dispose Resources Promptly** – ऊपर दिखाया गया `try‑with‑resources` पैटर्न सुनिश्चित करता है कि स्ट्रीम्स तुरंत बंद हो जाएँ।  
- **Batch Processing** – बड़े बैच के लिए, फ़ाइलों को क्रमिक रूप से प्रोसेस करें या सीमित कन्करेंसी वाले थ्रेड पूल का उपयोग करें ताकि हीप उपयोग 200 MB से नीचे रहे।

## अक्सर पूछे जाने वाले प्रश्न

**Q: डायग्राम में मेटाडेटा क्या है?**  
A: डायग्राम में मेटाडेटा का मतलब है बिल्ट‑इन और कस्टम प्रॉपर्टीज़ (लेखक, निर्माण तिथि, टैग आदि) जो फ़ाइल का वर्णन करती हैं बिना उसके विज़ुअल कंटेंट को बदले।

**Q: क्या मैं एक साथ कई मेटाडेटा प्रॉपर्टीज़ अपडेट कर सकता हूँ?**  
A: हाँ—एक `Map<String,String>` पर इटरेट करें और उसी `Metadata` सत्र में प्रत्येक एंट्री के लिए `set` कॉल करें।

**Q: क्या GroupDocs.Metadata Java सभी डायग्राम फ़ॉर्मेट्स के साथ संगत है?**  
A: यह 30 से अधिक लोकप्रिय डायग्राम फ़ॉर्मेट्स का समर्थन करता है, जिसमें VSDX, VDX, VSSX, और VSTX शामिल हैं। नवीनतम या विशेष फ़ॉर्मेट्स के लिए आधिकारिक संगतता मैट्रिक्स देखें।

**Q: मेटाडेटा अपडेट करते समय अपवादों को कैसे संभालूँ?**  
A: अपने कोड को `try‑catch` ब्लॉक में रैप करें और `FileNotFoundException`, `UnsupportedFormatException` जैसे विशिष्ट अपवादों या अप्रत्याशित त्रुटियों के लिए सामान्य `Exception` को हैंडल करें।

**Q: GroupDocs.Metadata Java के लिए लाइसेंसिंग विकल्प क्या हैं?**  
A: विकल्पों में फ्री ट्रायल, अस्थायी इवैल्यूएशन लाइसेंस, और अनलिमिटेड प्रोडक्शन उपयोग के लिए पूर्ण कमर्शियल लाइसेंस शामिल हैं।

## संसाधन

- [GroupDocs मेटाडेटा दस्तावेज़ीकरण](https://docs.groupdocs.com/metadata/java/)
- [API रेफ़रेंस](https://reference.groupdocs.com/metadata/java/)
- [GroupDocs.Metadata डाउनलोड करें](https://releases.groupdocs.com/metadata/java/)
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [फ़्री सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/metadata/)
- [अस्थायी लाइसेंस प्राप्ति](https://purchase.groupdocs.com/temporary-license/) 

---

**अंतिम अपडेट:** 2026-06-17  
**परीक्षण किया गया:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs  

## संबंधित ट्यूटोरियल

- [java डॉक्यूमेंट प्रॉपर्टीज़ – GroupDocs for Java के साथ डायग्राम मेटाडेटा निकालें](/metadata/java/diagram-formats/extract-diagram-metadata-groupdocs-java/)
- [GroupDocs.Metadata for Java के साथ DXF ऑथर मेटाडेटा कैसे अपडेट करें – एक पूर्ण गाइड](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [डॉक्यूमेंट मैनेजमेंट के लिए जावा में GroupDocs.Metadata के साथ PDF मेटाडेटा को कुशलतापूर्वक अपडेट करें](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)