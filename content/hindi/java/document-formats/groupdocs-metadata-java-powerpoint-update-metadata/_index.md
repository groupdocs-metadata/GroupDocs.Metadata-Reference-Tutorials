---
date: '2026-02-03'
description: जावा के साथ GroupDocs Maven निर्भरता का उपयोग करके PowerPoint मेटाडेटा
  को अपडेट करना सीखें, जिसमें PPTX निर्माण तिथि को बदलना शामिल है।
keywords:
- update PowerPoint metadata Java
- GroupDocs.Metadata Java library
- presentation metadata management
title: GroupDocs Maven निर्भरता के साथ PowerPoint मेटाडेटा अपडेट करें
type: docs
url: /hi/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

Docs करें

## त्वरित उत्तर
- **Java में PowerPoint मेटाडाटा को संप सी है?** GroupDocs.Metadata Java, groupdocs Maven dependency के माध्यम से।  
- **क्या मैं PPTX निर्माण तिथि बदल सकता हूँ?** हाँ—सिर्फ `CreatedTime` प्रॉपर्टी सेट करें।  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए मुफ्त ट्रायल काम करता है; उत्पादन के लिए व्यावसायिक लाइसेंस आवश्यक है।  
- **कौन सा बिल्ड टूल समर्थित है?** Maven (नीचे दिखाया गया) या मैन्युअल JAR डाउनलोड।  
- **क्या कोड Java 8+ के साथ संगत है?** बिल्कुल—GroupDocs.Metadata Java 8 और उससे ऊपर को लक्षित करता है।

## GroupDocs Maven Dependency क्या है?
**groupdocs Maven dependency** एक Maven‑संगत रिपॉजिटरी एंट्री है जो नवीनतम GroupDocs.Metadata लाइब्रेरी को आपके Java प्रोजेक्ट में लाती है। यह डिपेंडेंसी प्रबंधन को सरल बनाता है और सुनिश्चित करता है कि आपके पास हमेशा सबसे नया, सुरक्षित संस्करण हो।

## PPTX निर्माण तिथि बदलने के लिए GroupDocs.Metadata का उपयोग क्यों करें?
- **केंद्रीकृत नियंत्रण:** बैच जॉब में कई प्रस्तुतियों को अपडेट करें।  
- **अनुपालन:** निर्माण टाइमस्टैम्प को आपके दस्तावेज़‑प्रबंधन नीतियों के अनुसार रखें।  
- **कोई UI आवश्यक नहीं:** CI/CD पाइपलाइन या कंटेंट माइग्रेशन के दौरान मेटाडाटा परिवर्तन को स्वचालित करें।

## आवश्यकताएँ
- Java 8 या उससे ऊपर स्थापित हो।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- डिपेंडेंसी प्रबंधन के लिए Maven।  
- GroupDocs ट्रायल या खरीदे गए लाइसेंस तक पहुंच।

## अपने Java प्रोजेक्ट में GroupDocs Maven Dependency का उपयोग

### Maven सेटअप
अपने `pom.xml` में GroupDocs रिपॉजिटरी और मेटाडाटा डिपेंडेंसी जोड़ें:

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

> **Pro tip:** संस्करण संख्या को अद्यतित रखना आपको नवीनतम बग फिक्स और प्रदर्शन सुधारों का लाभ देता है।

### सीधे डाउनलोड (यदि आप Maven का उपयोग नहीं करना चाहते)

वैकल्पिक रूप से, नवीनतम JAR को [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) से डाउनलोड करें।

#### लाइसेंस प्राप्त करना
पहले एक मुफ्त ट्रायल से शुरू करें या GroupDocs.Metadata का मूल्यांकन करने के लिए अस्थायी लाइसेंस का अनुरोध करें। उत्पादन उपयोग के लिए, [GroupDocs की आधिकारिक वेबसाइट](https://purchase.groupdocs.com/temporary-license/) से लाइसेंस खरीदें।

## बुनियादी इनिशियलाइज़ेशन और सेटअप

जब लाइब्रेरी क्लासपाथ में हो, तो आप एक `Metadata` इंस्टेंस बना सकते हैं जो आपके PowerPoint फ़ाइल की ओर इशारा करता है:

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

यह कोड प्रस्तुति को try‑with‑resources ब्लॉक में खोलता है, जिससे फ़ाइल हैंडल स्वचालित रूप से रिलीज़ हो जाता है।

## बिल्ट‑इन मेटाडाटा अपडेट करने के लिए चरण‑दर‑चरण गाइड

### चरण 1: प्रस्तुति दस्तावेज़ लोड करें

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

फ़ाइल को लोड करने से एक कनेक्शन स्थापित होता है जो आपको मेटाडाटा पढ़ने या लिखने की अनुमति देता है।

### चरण 2: प्रस्तुति के रूट पैकेज तक पहुंचें

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` ऑब्जेक्ट सभी बिल्ट‑इन दस्तावेज़ प्रॉपर्टीज़ को उजागर करता है।

### चरण 3: बिल्ट‑इन दस्तावेज़ प्रॉपर्टीज़ अपडेट करें (निर्माण तिथि सहित)

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

यहाँ हम दिखाते हैं कि कैसे **PPTX निर्माण तिथि बदलें** एक नया `Date` ऑब्जेक्ट `CreatedTime` को असाइन करके। आप `new Date()` को अपनी आवश्यक किसी भी विशिष्ट टाइमस्टैम्प से बदल सकते हैं।

### चरण 4: अपडेटेड प्रस्तुति सहेजें

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` कॉल संशोधित मेटाडाटा को एक नई PowerPoint फ़ाइल में लिखता है, जबकि मूल फ़ाइल अपरिवर्तित रहती है।

## समस्या निवारण टिप्स
- **फ़ाइल नहीं मिली:** इनपुट पाथ और फ़ाइल अनुमतियों को दोबारा जांचें।  
- **संस्करण असंगतता:** सुनिश्चित करें कि `groupdocs-metadata` संस्करण आपके Java रनटाइम से मेल खाता है।  
- **प्रॉपर्टी अपडेट नहीं हो रही:** `save` कॉल करने से पहले `setCreatedTime` (या संबंधित setter) को कॉल कर रहे हैं, यह सुनिश्चित करें।

## व्यावहारिक अनुप्रयोग

1. **कॉरपोरेट ब्रांडिंग:** वितरण से पहले सभी स्लाइड डेक में सही कंपनी नाम और श्रेणी को स्वचालित रूप से डालें।  
2. **डॉक्यूमेंट मैनेजमेंट सिस्टम:** तेज़ पुनर्प्राप्ति के लिए खोज योग्य मेटाडाटा के साथ PPTX फ़ाइलों को समृद्ध बनाएं।  
3. **शैक्षिक संसाधन:** लेक्चर स्लाइड्स में लेखक और पाठ्यक्रम जानकारी को अद्यतित रखें।  
4. **सहयोग ट्रैकिंग:** उत्तरदायित्व बनाए रखने के लिए योगदानकर्ताओं के नाम रिकॉर्ड करें।  
5. **CMS इंटीग्रेशन:** वास्तविक समय में आपके कंटेंट मैनेजमेंट प्लेटफ़ॉर्म के साथ मेटाडाटा परिवर्तन को सिंक करें।

## प्रदर्शन विचार
- **बैच प्रोसेसिंग:** फ़ाइलों की सूची पर लूप करें और जहाँ संभव हो एक ही `Metadata` इंस्टेंस को पुन: उपयोग करें।  
- **मेमोरी प्रबंधन:** हमेशा try‑with‑resources (जैसा दिखाया गया) का उपयोग करें ताकि नेटिव संसाधन तुरंत मुक्त हों।  
- **कुशल डेटा स्ट्रक्चर:** मेटाडाटा अपडेट को एक मैप में संग्रहीत करें और फिर लागू करें ताकि दोहराव वाले कॉल कम हों।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न:** groupdocs Maven dependency का मुख्य उद्देश्य क्या है?  
**उत्तर:** यह Maven‑आधारित Java प्रोजेक्ट्स में नवीनतम GroupDocs.Metadata लाइब्रेरी को शामिल करने का सुविधाजनक तरीका प्रदान करता है।

**प्रश्न:** अन्य प्रॉपर्टीज़ को प्रभावित किए बिना PPTX निर्माण तिथि कैसे बदलूँ?  
**उत्तर:** `metadata.save()` कॉल करने से पहले `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` का उपयोग करें।

**प्रश्न:** विकास में इस कोड को चलाने के लिए क्या लाइसेंस चाहिए?  
**उत्तर:** विकास और परीक्षण के लिए एक अस्थायी ट्रायल लाइसेंस पर्याप्त है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।

**प्रश्न:** क्या मैं कस्टम मेटाडाटा फ़ील्ड भी अपडेट कर सकता हूँ?  
**उत्तर:** हाँ—GroupDocs.Metadata अपने API के माध्यम से बिल्ट‑इन और कस्टम दोनों प्रॉपर्टीज़ को सपोर्ट करता है।

**प्रश्न:** यदि मैं गलती करूँ तो क्या परिवर्तन वापस करने का तरीका है?  
**उत्तर:** मूल फ़ाइल की एक कॉपी रखें या ओवरराइट करने से पहले मौजूदा प्रॉपर्टी मान पढ़ें, फिर आवश्यकता पड़ने पर पुनर्स्थापित करें।

## संसाधन

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**अंतिम अपडेट:** 2026-02-03  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs