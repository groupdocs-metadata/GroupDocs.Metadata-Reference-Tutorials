---
date: '2026-03-22'
description: GroupDocs.Metadata for Java का उपयोग करके Excel निर्माण तिथि को बदलना
  और Excel मेटाडेटा को अपडेट करना सीखें। Excel में कीवर्ड जोड़ने और दस्तावेज़ गुणों
  को संशोधित करने के लिए इस चरण‑दर‑चरण गाइड का पालन करें।
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Java में GroupDocs.Metadata का उपयोग करके Excel निर्माण तिथि बदलें
type: docs
url: /hi/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata का उपयोग करके जावा में Excel निर्माण तिथि बदलें

आधुनिक डेटा‑ड्रिवेन वातावरण में, **Excel निर्माण तिथि बदलना** और अन्य मेटाडेटा को अद्यतन रखना दस्तावेज़ संगठन, खोजयोग्यता और अनुपालन को नाटकीय रूप से सुधार सकता है। चाहे आप वित्तीय रिपोर्ट, प्रोजेक्ट ट्रैकर, या अभिलेखीय डेटा संभाल रहे हों, सटीक मेटाडेटा सुनिश्चित करता है कि सही लोग सही फ़ाइलें सही समय पर पाएँ। यह ट्यूटोरियल आपको जावा एप्लिकेशन में GroupDocs.Metadata लाइब्रेरी का उपयोग करके **Excel निर्माण तिथि बदलने**, **Excel में कीवर्ड जोड़ने**, और **Excel डॉक्यूमेंट प्रॉपर्टीज़ संशोधित करने** के चरण दिखाता है।

## त्वरित उत्तर
- **क्या मैं Excel फ़ाइल की निर्माण तिथि बदल सकता हूँ?** हाँ, GroupDocs.Metadata के `setCreatedTime` का उपयोग करके।  
- **जावा में Excel मेटाडेटा अपडेट करने के लिए कौन‑सी लाइब्रेरी समर्थन करती है?** GroupDocs.Metadata for Java।  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए एक स्थायी लाइसेंस आवश्यक है।  
- **कौन‑सी जावा संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।  
- **क्या मैं Excel वर्कबुक में कस्टम कीवर्ड जोड़ सकता हूँ?** बिल्कुल—डॉक्यूमेंट प्रॉपर्टीज़ पर `setKeywords` का उपयोग करें।  

## “Excel निर्माण तिथि बदलना” क्या है?
Excel निर्माण तिथि बदलना का अर्थ है वर्कबुक फ़ाइल के भीतर संग्रहीत बिल्ट‑इन *Created* प्रॉपर्टी को अपडेट करना। यह प्रॉपर्टी मानक Office Open XML मेटाडेटा का हिस्सा है और इसे प्रोग्रामेटिक रूप से वर्कशीट सामग्री को बदले बिना संपादित किया जा सकता है।

## Excel मेटाडेटा के लिए GroupDocs.Metadata क्यों उपयोग करें?
GroupDocs.Metadata एक उच्च‑स्तरीय, टाइप‑सेफ़ API प्रदान करता है जो Office Open XML फ़ॉर्मेट के लिए आवश्यक लो‑लेवल XML हैंडलिंग को एब्स्ट्रैक्ट करता है। यह आपको सक्षम बनाता है:

- **कोर प्रॉपर्टीज़ अपडेट करें** जैसे लेखक, कंपनी, और निर्माण तिथि को एक ही कॉल में।  
- **Excel में कीवर्ड जोड़ें** ताकि SharePoint, OneDrive, या स्थानीय फ़ाइल सिस्टम में खोज परिणाम बेहतर हों।  
- **Excel डॉक्यूमेंट प्रॉपर्टीज़ संशोधित करें** बिना Excel में वर्कबुक खोले, जिससे समय और संसाधन बचते हैं।  

## पूर्वापेक्षाएँ
- Java Development Kit (JDK) 8 या नया।  
- IntelliJ IDEA या Eclipse जैसा IDE।  
- Java फ़ाइल I/O की बुनियादी जानकारी।  

## GroupDocs.Metadata को जावा के लिए सेट अप करना

### Installation

अपने `pom.xml` में GroupDocs.Metadata Maven रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

वैकल्पिक रूप से, यदि आप मैन्युअल सेटअप पसंद करते हैं तो आप सीधे [नवीनतम संस्करण डाउनलोड कर सकते हैं](https://releases.groupdocs.com/metadata/java/)।

### License Acquisition

GroupDocs मूल्यांकन के लिए एक मुफ्त ट्रायल प्रदान करता है। उत्पादन उपयोग के लिए, विक्रेता से एक अस्थायी या स्थायी लाइसेंस प्राप्त करें। विवरण के लिए [GroupDocs की खरीद पेज](https://purchase.groupdocs.com/temporary-license/) देखें।

#### Basic Initialization

अपने जावा स्रोत फ़ाइल में आवश्यक क्लासेस इम्पोर्ट करें:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Step‑by‑Step Implementation

### Step 1: Open the Excel Workbook

स्रोत वर्कबुक का पथ प्रदान करें और एक `Metadata` इंस्टेंस बनाएं। `try‑with‑resources` ब्लॉक फ़ाइल हैंडल को स्वचालित रूप से बंद कर देता है।

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Step 2: Update Built‑In Metadata Properties

अब आप **Excel निर्माण तिथि बदल सकते हैं**, लेखक, कंपनी, श्रेणी सेट कर सकते हैं, और **Excel में कीवर्ड जोड़ सकते हैं**। `new Date()` कॉल वर्तमान टाइमस्टैम्प को कैप्चर करता है, लेकिन आप कोई भी आवश्यक `java.util.Date` प्रदान कर सकते हैं।

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **प्रो टिप:** कीवर्ड के लिए एक सुसंगत नामकरण नियम उपयोग करें (उदा., `project:Q2, finance, confidential`) ताकि भविष्य की खोजें अधिक प्रभावी हों।

### Step 3: Save the Updated Workbook

एक आउटपुट पथ निर्दिष्ट करें और बदलावों को सहेजें। मूल फ़ाइल अपरिवर्तित रहती है, जो ऑडिट ट्रेल के लिए उपयोगी है।

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Common Issues and Solutions

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **फ़ाइल पथ त्रुटियाँ** | गलत रिलेटिव/एब्सोल्यूट पाथ | `inputFilePath` और `outputFilePath` को दोबारा जांचें। प्लेटफ़ॉर्म‑स्वतंत्र पाथ के लिए `Paths.get(...)` का उपयोग करें। |
| **असंगत लाइब्रेरी संस्करण** | ऐसी पुरानी GroupDocs.Metadata का उपयोग करना जो `setCreatedTime` मेथड को सपोर्ट नहीं करती। | नवीनतम संस्करण में अपग्रेड करें (जैसा कि Maven स्निपेट में दिखाया गया है)। |
| **लाइसेंस अनुपलब्ध** | ट्रायल अवधि समाप्त हो गई | अस्थायी लाइसेंस लागू करें या खरीद पेज के माध्यम से पूर्ण लाइसेंस खरीदें। |
| **बड़ी वर्कबुक मेमोरी उपयोग** | बड़ी Excel फ़ाइलें लोड करने से हीप स्पेस खपत होती है | फ़ाइलों को बैच में प्रोसेस करें और आवश्यक होने पर JVM हीप (`-Xmx`) बढ़ाएँ। |

## Frequently Asked Questions

**प्रश्न:** GroupDocs.Metadata कौन‑से जावा संस्करणों को सपोर्ट करता है?  
**उत्तर:** Java 8 और उसके बाद के संस्करण पूरी तरह सपोर्टेड हैं।

**प्रश्न:** मेटाडेटा अपडेट करते समय अपवादों को कैसे संभालें?  
**उत्तर:** कोड को `try‑catch` ब्लॉक में रखें और किसी भी I/O या फ़ॉर्मेट त्रुटि को पकड़ने के लिए `MetadataException` को लॉग करें।

**प्रश्न:** क्या मैं एक ही रन में कई Excel फ़ाइलें अपडेट कर सकता हूँ?  
**उत्तर:** हाँ, फ़ाइल पाथ के संग्रह पर इटररेट करें, लेकिन बड़े बैचों के लिए मेमोरी उपयोग पर नज़र रखें।

**प्रश्न:** क्या मेटाडेटा में किए गए बदलावों को वापस किया जा सकता है?  
**उत्तर:** अपडेट लागू करने से पहले मूल वर्कबुक का बैकअप रखें, फिर आवश्यकता पड़ने पर उसे पुनर्स्थापित करें।

**प्रश्न:** अधिक विस्तृत दस्तावेज़ीकरण कहाँ मिल सकता है?  
**उत्तर:** आधिकारिक गाइड देखें: [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/)।

## Practical Applications

1. **वित्तीय ऑडिट** – यह रिकॉर्ड करें कि किसने वर्कबुक को कब संशोधित किया, जिससे ऑडिट ट्रेल मिलता है।  
2. **प्रोजेक्ट मैनेजमेंट** – शीघ्र पुनः प्राप्ति के लिए स्प्रेडशीट्स को प्रोजेक्ट‑विशिष्ट कीवर्ड से टैग करें।  
3. **डेटा आर्काइविंग** – अनुपालन के लिए मूल निर्माण तिथियों और कंपनी जानकारी को संरक्षित रखें।

## Performance Tips

- प्रत्येक रन में मेटाडेटा ऑपरेशन्स को सीमित रखें ताकि अत्यधिक मेमोरी खपत न हो।  
- `Metadata` ऑब्जेक्ट को तुरंत बंद करें (`try‑with‑resources` पैटर्न इसे स्वचालित रूप से करता है)।  
- बहुत बड़ी वर्कबुक्स के लिए, UI को रिस्पॉन्सिव रखने हेतु बैकग्राउंड थ्रेड में प्रोसेस करने पर विचार करें।

## Conclusion

आप अब जानते हैं कि GroupDocs.Metadata का उपयोग करके जावा में **Excel निर्माण तिथि बदलना**, **Excel में कीवर्ड जोड़ना**, और **Excel डॉक्यूमेंट प्रॉपर्टीज़ संशोधित करना** कैसे किया जाता है। यह क्षमता आपको अपने स्प्रेडशीट्स को सुव्यवस्थित, खोज योग्य और आंतरिक गवर्नेंस नीतियों के अनुरूप रखने में सक्षम बनाती है। अगले चरण के रूप में, कस्टम प्रॉपर्टीज़ या बैच प्रोसेसिंग जैसी अन्य मेटाडेटा सुविधाओं का अन्वेषण करें ताकि दस्तावेज़ प्रबंधन वर्कफ़्लो को और अधिक सुव्यवस्थित किया जा सके।

---

**Last Updated:** 2026-03-22  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

**संसाधन**
- [डॉक्यूमेंटेशन](https://docs.groupdocs.com/metadata/java/)
- [API रेफ़रेंस](https://reference.groupdocs.com/metadata/java/)
- [GroupDocs.Metadata डाउनलोड करें](https://releases.groupdocs.com/metadata/java/)
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [फ़्री सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/metadata/)
- [अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/)