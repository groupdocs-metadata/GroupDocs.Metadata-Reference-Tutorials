---
date: '2026-05-27'
description: GroupDocs Maven dependency का उपयोग करके Java में pptx CreatedTime सेट
  करना सीखें, जिससे PowerPoint metadata अपडेट हो सके, जिसमें PPTX निर्माण तिथि बदलना
  भी शामिल है।
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
title: Java में GroupDocs Maven Dependency के साथ PPTX CreatedTime सेट करें
type: docs
url: /hi/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Java में GroupDocs.Metadata के साथ PPTX CreatedTime सेट करें

सटीक मेटाडाटा आधुनिक दस्तावेज़ कार्यप्रवाहों में अनुपालन और खोजयोग्यता के लिए आवश्यक है। **GroupDocs.Metadata** के साथ आप प्रोग्रामेटिक रूप से **Java में PPTX CreatedTime सेट** कर सकते हैं, जिससे आप **PPTX निर्माण तिथि बदल** सकते हैं, साथ ही लेखक या कंपनी जैसी अन्य निर्मित गुणों के साथ। यह ट्यूटोरियल आपको Maven सेटअप, API को इनिशियलाइज़ करने, मेटाडाटा अपडेट करने, और संशोधित प्रस्तुति को सहेजने की प्रक्रिया से ले जाता है—सभी स्पष्ट, प्रोडक्शन‑रेडी कोड के साथ।

## त्वरित उत्तर
- **Java में PowerPoint मेटाडाटा को अपडेट करने वाली लाइब्रेरी कौन सी है?** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **क्या मैं PPTX CreatedTime प्रॉपर्टी सेट कर सकता हूँ?** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **क्या उत्पादन के लिए लाइसेंस आवश्यक है?** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **उदाहरण किस बिल्ड टूल का उपयोग करता है?** Maven (you can also download the JAR manually).  
- **क्या API Java 8 और उससे नए संस्करणों को सपोर्ट करता है?** Absolutely—GroupDocs.Metadata targets Java 8+.

## GroupDocs Maven डिपेंडेंसी क्या है?
**GroupDocs Maven डिपेंडेंसी** एक Maven‑संगत रिपॉजिटरी एंट्री है जो नवीनतम GroupDocs.Metadata लाइब्रेरी को आपके Java प्रोजेक्ट में लाती है। यह ट्रांज़िटिव लाइब्रेरीज़ को स्वचालित रूप से हल करके डिपेंडेंसी प्रबंधन को सरल बनाती है, यह सुनिश्चित करती है कि आप हमेशा नवीनतम और सुरक्षित संस्करण का उपयोग करें, और मैन्युअल JAR डाउनलोड या संस्करण ट्रैकिंग की आवश्यकता को समाप्त करती है।

## PPTX निर्माण तिथि बदलने के लिए GroupDocs.Metadata का उपयोग क्यों करें?
GroupDocs.Metadata PPTX निर्माण टाइमस्टैम्प्स के स्वचालित, बैच‑रेडी अपडेट को सक्षम करता है, जिससे प्रत्येक प्रस्तुति कॉर्पोरेट नीतियों या कानूनी आवश्यकताओं के अनुरूप रहती है। प्रोग्रामेटिक रूप से CreatedTime प्रॉपर्टी सेट करके आप मैन्युअल संपादन से बचते हैं, मानव त्रुटियों को कम करते हैं, और इस परिवर्तन को CI/CD पाइपलाइन या माइग्रेशन स्क्रिप्ट्स में एकीकृत करके सहज दस्तावेज़ प्रबंधन प्राप्त कर सकते हैं।

## पूर्वापेक्षाएँ
- Java 8 या उससे उच्च संस्करण स्थापित हो।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- डिपेंडेंसी प्रबंधन के लिए Maven।  
- GroupDocs ट्रायल या खरीदे हुए लाइसेंस तक पहुँच।

## Java में PPTX CreatedTime कैसे सेट करें?
`Metadata` क्लास एक दस्तावेज़ का प्रतिनिधित्व करती है और इसके मेटाडाटा प्रॉपर्टीज़ तक पहुँच प्रदान करती है।

`new Metadata("presentation.pptx")` के साथ अपना PowerPoint फ़ाइल लोड करें, रूट पैकेज प्राप्त करें, इच्छित `java.util.Date` के साथ `setCreatedTime` कॉल करें, और अंत में बदलाव लिखने के लिए `save` को इनवोक करें। यह एंड‑टू‑एंड फ्लो निर्माण तिथि को संशोधित करता है जबकि सभी स्लाइड सामग्री और अन्य प्रॉपर्टीज़ को संरक्षित रखता है।

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

> **Pro tip:** संस्करण संख्या को अद्यतन रखने से आप नवीनतम बग फिक्स और प्रदर्शन सुधारों का लाभ उठा सकते हैं।

### सीधे डाउनलोड (यदि आप Maven का उपयोग नहीं करना चाहते)
वैकल्पिक रूप से, नवीनतम JAR को [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) से डाउनलोड करें।

#### लाइसेंस प्राप्ति
GroupDocs.Metadata का मूल्यांकन करने के लिए एक मुफ्त ट्रायल से शुरू करें या अस्थायी लाइसेंस का अनुरोध करें। उत्पादन उपयोग के लिए, [GroupDocs की आधिकारिक वेबसाइट](https://purchase.groupdocs.com/temporary-license/) के माध्यम से लाइसेंस खरीदें।

## बुनियादी इनिशियलाइज़ेशन और सेटअप
जब लाइब्रेरी क्लासपाथ पर हो जाए, तो आप एक `Metadata` इंस्टेंस बना सकते हैं जो आपके PowerPoint फ़ाइल की ओर इशारा करता है:

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

### चरण 2: प्रस्तुति के रूट पैकेज तक पहुँचें
`root` ऑब्जेक्ट प्रस्तुति के कोर पैकेज और उसकी बिल्ट‑इन प्रॉपर्टीज़ तक पहुँच प्रदान करता है।

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` ऑब्जेक्ट सभी बिल्ट‑इन दस्तावेज़ प्रॉपर्टीज़ को उजागर करता है।

### चरण 3: बिल्ट‑इन दस्तावेज़ प्रॉपर्टीज़ अपडेट करें (निर्माण तिथि सहित)
`setCreatedTime` दस्तावेज़ को एक नया निर्माण टाइमस्टैम्प असाइन करता है।

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

यहाँ हम दिखाते हैं कि कैसे **PPTX CreatedTime सेट** किया जाए, `CreatedTime` को एक नया `Date` ऑब्जेक्ट असाइन करके। `new Date()` को अपनी आवश्यक किसी भी विशिष्ट टाइमस्टैम्प से बदलें।

### चरण 4: अपडेटेड प्रस्तुति सहेजें
`save` संशोधित मेटाडाटा को फ़ाइल में वापस लिखता है।

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` कॉल संशोधित मेटाडाटा को एक नई PowerPoint फ़ाइल में लिखता है, मूल फ़ाइल को अपरिवर्तित छोड़ देता है।

## समस्या निवारण टिप्स
- **File Not Found:** इनपुट पाथ और फ़ाइल अनुमतियों को दोबारा जांचें।  
- **Version Mismatch:** सुनिश्चित करें कि `groupdocs-metadata` संस्करण आपके Java रनटाइम से मेल खाता है।  
- **Property Not Updating:** `save` को कॉल करने से पहले आप `setCreatedTime` (या संबंधित सेट्टर) को कॉल कर रहे हैं, यह सत्यापित करें।

## व्यावहारिक अनुप्रयोग
1. **Corporate Branding:** वितरण से पहले सभी स्लाइड डेक्स में सही कंपनी नाम और श्रेणी को स्वचालित रूप से डालें।  
2. **Document Management Systems:** तेज़ पुनः प्राप्ति के लिए PPTX फ़ाइलों को खोज योग्य मेटाडाटा से समृद्ध करें।  
3. **Educational Resources:** लेक्चर स्लाइड्स में लेखक और पाठ्यक्रम जानकारी को अद्यतन रखें।  
4. **Collaboration Tracking:** उत्तरदायित्व बनाए रखने के लिए योगदानकर्ताओं के नाम रिकॉर्ड करें।  
5. **CMS Integration:** रियल‑टाइम में आपके कंटेंट मैनेजमेंट प्लेटफ़ॉर्म के साथ मेटाडाटा बदलावों को सिंक करें।

## प्रदर्शन संबंधी विचार
- **Batch Processing:** फ़ाइलों की सूची पर लूप करें और जहाँ संभव हो एक ही `Metadata` इंस्टेंस को पुनः उपयोग करें।  
- **Memory Management:** हमेशा try‑with‑resources (जैसा दिखाया गया है) का उपयोग करके नेटिव रिसोर्सेज़ को तुरंत मुक्त करें।  
- **Efficient Data Structures:** दोहराव वाले कॉल्स को कम करने के लिए मेटाडाटा अपडेट्स को मैप में स्टोर करें और फिर लागू करें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: GroupDocs Maven डिपेंडेंसी का मुख्य उद्देश्य क्या है?**  
A: यह Maven‑आधारित Java प्रोजेक्ट्स में नवीनतम GroupDocs.Metadata लाइब्रेरी को शामिल करने का सुविधाजनक तरीका प्रदान करती है।

**Q: मैं अन्य प्रॉपर्टीज़ को प्रभावित किए बिना PPTX निर्माण तिथि कैसे सेट कर सकता हूँ?**  
A: `metadata.save()` कॉल करने से पहले `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` का उपयोग करें।

**Q: विकास में इस कोड को चलाने के लिए क्या मुझे लाइसेंस चाहिए?**  
A: विकास और परीक्षण के लिए एक अस्थायी ट्रायल लाइसेंस पर्याप्त है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।

**Q: क्या मैं कस्टम मेटाडाटा फ़ील्ड्स को भी अपडेट कर सकता हूँ?**  
A: हाँ—GroupDocs.Metadata अपने API के माध्यम से बिल्ट‑इन और कस्टम दोनों प्रॉपर्टीज़ को सपोर्ट करता है।

**Q: यदि मैं गलती करूँ तो क्या बदलावों को वापस करने का कोई तरीका है?**  
A: मूल फ़ाइल की एक कॉपी रखें या ओवरराइट करने से पहले मौजूदा प्रॉपर्टी मान पढ़ें, फिर आवश्यकता पड़ने पर पुनर्स्थापित करें।

## संसाधन

- [दस्तावेज़ीकरण](https://docs.groupdocs.com/metadata/java/)
- [API रेफ़रेंस](https://apireference.groupdocs.com/metadata/java/)

---

**अंतिम अपडेट:** 2026-05-27  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs  

## संबंधित ट्यूटोरियल

- [GroupDocs.Metadata Java API का उपयोग करके PowerPoint में कस्टम मेटाडाटा अपडेट करें](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [GroupDocs.Metadata Java का उपयोग करके Word दस्तावेज़ मेटाडाटा अपडेट करने का पूर्ण गाइड](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [दस्तावेज़ प्रबंधन के लिए Java में GroupDocs.Metadata के साथ PDF मेटाडाटा को कुशलतापूर्वक अपडेट करें](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)