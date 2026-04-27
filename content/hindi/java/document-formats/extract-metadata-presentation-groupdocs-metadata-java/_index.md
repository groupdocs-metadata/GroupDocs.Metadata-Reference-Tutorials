---
date: '2026-01-26'
description: GroupDocs.Metadata for Java का उपयोग करके PowerPoint प्रस्तुतियों से
  निर्मित समय पढ़ना और अन्य दस्तावेज़ गुण निकालना सीखें। दस्तावेज़ प्रबंधन और अनुपालन
  के लिए आदर्श।
keywords:
- read created time java
- java extract document properties
- presentation metadata
title: GroupDocs.Metadata का उपयोग करके प्रस्तुति फ़ाइलों से जावा में निर्मित समय
  कैसे पढ़ें – एक चरण‑दर‑चरण मार्गदर्शिका
type: docs
url: /hi/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata का उपयोग करके प्रेजेंटेशन फ़ाइलों से जावा में निर्मित समय कैसे पढ़ें

## त्वरित उत्तर
- **“read created time java” का क्या मतलब है?** यह जावा कोड के माध्यम से फ़ाइल के निर्माण टाइमस्टैम्प को प्राप्त करने की प्रक्रिया है।  
- **कौन सी लाइब्रेरी इसे सपोर्ट करती है?** GroupDocs.Metadata for Java सभी बिल्ट‑इन प्रेजेंटेशन प्रॉपर्टीज़ के लिए एक साफ़ API प्रदान करती है।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए एक स्थायी लाइसेंस आवश्यक है।  
- **क्या मैं एक साथ अन्य प्रॉपर्टीज़ भी निकाल सकता हूँ?** हाँ—लेखक, कंपनी, श्रेणी, और अधिक वही API के माध्यम से उपलब्ध हैं।  
- **कौन सा जावा संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।

## “read created time java” क्या है?
जावा में दस्तावेज़ का निर्मित समय पढ़ना मतलब उस मेटाडेटा फ़ील्ड तक पहुंचना है जो फ़ाइल के मूल रूप से जनरेट होने का समय संग्रहीत करता है। यह टाइमस्टैम्प संस्करण नियंत्रण, ऑडिट ट्रेल और अनुपालन सत्यापन के लिए आवश्यक है।

## दस्तावेज़ गुण निकालने के लिए GroupDocs.Metadata for Java का उपयोग क्यों करें?
GroupDocs.Metadata विभिन्न फ़ाइल फ़ॉर्मेट की जटिलताओं को एब्स्ट्रैक्ट करता है, जिससे आप लो‑लेवल पार्सिंग की बजाय बिज़नेस लॉजिक पर ध्यान केंद्रित कर सकते हैं। यह PowerPoint, PDF, Word और कई इमेज प्रकारों को सपोर्ट करता है, जिससे यह किसी भी जावा प्रोजेक्ट के लिए एक बहुमुखी विकल्प बनता है जिसे **java extract document properties** विश्वसनीय रूप से चाहिए।

## पूर्वापेक्षाएँ
- **GroupDocs.Metadata for Java** संस्करण 24.12 या बाद का।  
- Java Development Kit (JDK 8 या नया)।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- बेसिक जावा फ़ाइल‑हैंडलिंग ज्ञान।

## GroupDocs.Metadata for Java सेटअप करना

### Maven सेटअप
यदि आप Maven के साथ डिपेंडेंसीज़ मैनेज करते हैं, तो अपने `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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
- **Free Trial:** API का अन्वेषण करने के लिए फ्री ट्रायल से शुरू करें।  
- **Temporary License:** बिना प्रतिबंध के परीक्षण के लिए एक टेम्पररी की प्राप्त करें।  
- **Purchase:** प्रोडक्शन डिप्लॉयमेंट के लिए पूर्ण लाइसेंस खरीदें।

### बेसिक इनिशियलाइज़ेशन और सेटअप
डिपेंडेंसी सेट होने के बाद, एक `Metadata` ऑब्जेक्ट बनाएं और उसे अपनी प्रेजेंटेशन फ़ाइल की ओर पॉइंट करें:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## प्रेजेंटेशन से जावा डॉक्यूमेंट प्रॉपर्टीज़ निकालना कैसे करें
नीचे हम सबसे सामान्य बिल्ट‑इन प्रॉपर्टीज़ को देखते हैं, यह दिखाते हुए कि उन्हें ठीक‑ठीक कैसे पढ़ा जाए।

### लेखक जानकारी निकालना
**Overview:** प्रेजेंटेशन बनाने वाले व्यक्ति का नाम प्राप्त करें।

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*`getAuthor()` मेथड लेखक स्ट्रिंग लौटाता है या यदि फ़ील्ड खाली है तो `null`।*

### निर्मित समय निकालना (read created time java)
**Overview:** वह टाइमस्टैम्प प्राप्त करें जो दर्शाता है कि फ़ाइल पहली बार कब बनाई गई थी।

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*`getCreatedTime()` एक `java.util.Date` ऑब्जेक्ट प्रदान करता है जो निर्माण क्षण को दर्शाता है—यही “read created time java” का संदर्भ है।*

### कंपनी जानकारी निकालना
**Overview:** प्रेजेंटेशन से जुड़ी संगठन का नाम प्राप्त करें।

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*`getCompany()` मेथड कंपनी मेटाडेटा लौटाता है या यदि सेट नहीं है तो `null`।*

### आप द्वारा निकाली जा सकने वाली अतिरिक्त मेटाडेटा
आप समान रूप से अन्य बिल्ट‑इन फ़ील्ड जैसे **Category**, **Keywords**, **Last Printed Date**, और **Application Name** को `getCategory()`, `getKeywords()` आदि मेथड्स का उपयोग करके प्राप्त कर सकते हैं।

## व्यावहारिक अनुप्रयोग
1. **डॉक्यूमेंट मैनेजमेंट सिस्टम:** तेज़ रिट्रीवल के लिए प्रेजेंटेशन को लेखक, कंपनी या निर्माण तिथि के आधार पर इंडेक्स करें।  
2. **अनुपालन ऑडिटिंग:** आर्काइव करने से पहले यह सत्यापित करें कि आवश्यक मेटाडेटा (जैसे निर्माण टाइमस्टैम्प) मौजूद है।  
3. **ऑटोमेटेड रिपोर्टिंग:** सारांश रिपोर्ट जेनरेट करें जो बताती है कि प्रत्येक स्लाइड डेक किसने और कब बनाया।  
4. **CRM इंटीग्रेशन:** कंपनी मेटाडेटा फ़ील्ड का उपयोग करके प्रेजेंटेशन को क्लाइंट रिकॉर्ड से लिंक करें।

## प्रदर्शन संबंधी विचार
- **पैरेलल प्रोसेसिंग:** बड़े बैच को संभालते समय थ्रेड्स में फ़ाइलों को प्रोसेस करके थ्रूपुट बढ़ाएँ।  
- **रिसोर्स मैनेजमेंट:** स्ट्रिम्स को स्वचालित रूप से बंद करने और मेमोरी लीक्स से बचने के लिए `try‑with‑resources` (जैसा दिखाया गया है) का उपयोग करें।  
- **बैच एक्सट्रैक्शन:** GroupDocs.Metadata बल्क ऑपरेशन्स सपोर्ट करता है; दक्षता के लिए एक लूप में कई फ़ाइलें पढ़ने पर विचार करें।

## सामान्य समस्याएँ और समाधान
- **मेटाडेटा नहीं मिला:** यदि कोई प्रॉपर्टी `null` लौटाती है, तो स्रोत फ़ाइल में वह जानकारी नहीं है। जैसा दिखाया गया है, `null` वैल्यूज़ को हैंडल करें।  
- **असमर्थित फ़ॉर्मेट:** सुनिश्चित करें कि फ़ाइल समर्थित PowerPoint फ़ॉर्मेट (`.pptx`, `.ppt`) में है।  
- **लाइसेंस त्रुटियाँ:** जांचें कि आपका लाइसेंस फ़ाइल सही जगह रखी गई है या ट्रायल अवधि समाप्त नहीं हुई है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: यदि मेटाडेटा प्रॉपर्टीज़ गायब हों तो मैं कैसे हैंडल करूँ?**  
उत्तर: API अनसेट फ़ील्ड्स के लिए `null` लौटाता है। फॉलबैक वैल्यू देने के लिए कंडीशनल एक्सप्रेशन जैसे `(author != null ? author : "N/A")` का उपयोग करें।

**प्रश्न: क्या GroupDocs.Metadata कस्टम मेटाडेटा फ़ील्ड्स निकाल सकता है?**  
उत्तर: हाँ, बिल्ट‑इन प्रॉपर्टीज़ के अलावा आप समान API का उपयोग करके कस्टम की/वैल्यू पेयर्स पढ़ और लिख सकते हैं।

**प्रश्न: क्या अन्य प्रेजेंटेशन फ़ॉर्मेट्स का समर्थन है?**  
उत्तर: GroupDocs.Metadata PowerPoint (`.ppt`, `.pptx`) के साथ-साथ PDF, Word और कई इमेज फ़ॉर्मेट्स को भी सपोर्ट करता है।

**प्रश्न: GroupDocs.Metadata Java के सिस्टम आवश्यकताएँ क्या हैं?**  
उत्तर: एक संगत JDK (8 या उससे ऊपर) और उन दस्तावेज़ों के आकार के अनुसार पर्याप्त हीप मेमोरी चाहिए जिसे आप प्रोसेस करेंगे।

**प्रश्न: अगर समस्या आए तो मदद कहाँ मिलेगी?**  
उत्तर: आधिकारिक सपोर्ट फ़ोरम पर सहायता प्राप्त करें: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## संसाधन

- **डॉक्यूमेंटेशन:** https://docs.groupdocs.com/metadata/java/  
- **API रेफ़रेंस:** https://reference.groupdocs.com/metadata/java/  
- **डाउनलोड:** https://releases.groupdocs.com/metadata/java/  
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java  
- **फ्री सपोर्ट:** https://forum.groupdocs.com/c/metadata/  
- **टेम्पररी लाइसेंस:** https://purchase.groupdocs.com/temporary-license/

इस गाइड को फॉलो करके आप अब **read created time java** और **java extract document properties** को PowerPoint प्रेजेंटेशन से GroupDocs.Metadata का उपयोग करके निकालना जानते हैं। इन स्निपेट्स को अपने प्रोजेक्ट्स में इंटीग्रेट करें ताकि दस्तावेज़ इंटेलिजेंस बढ़े और अनुपालन वर्कफ़्लो सुगम हो सकें।

---

**Last Updated:** 2026-01-26  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs