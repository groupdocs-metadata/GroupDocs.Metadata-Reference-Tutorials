---
date: '2025-12-26'
description: GroupDocs.Metadata for Java का उपयोग करके ASF मेटाडाटा निकालना सीखें।
  यह गाइड सेटअप, प्रॉपर्टी पढ़ने और कोडेक जानकारी तक पहुँचने को कवर करता है।
keywords:
- ASF Metadata Extraction
- GroupDocs.Metadata for Java
- Java Media Management
title: GroupDocs.Metadata for Java के साथ ASF मेटाडेटा कैसे निकालें
type: docs
url: /hi/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata for Java के साथ ASF मेटाडेटा निकालें

**परिचय**

आज के डिजिटल परिदृश्य में, मल्टीमीडिया सामग्री का कुशल प्रबंधन अत्यंत महत्वपूर्ण है। यदि आपको अपने मीडिया फ़ाइलों से **ASF मेटाडेटा निकालना** है, तो इसे मैन्युअल रूप से करना समय‑साध्य और त्रुटिप्रवण हो सकता है। यह ट्यूटोरियल आपको **GroupDocs.Metadata for Java** का उपयोग करके विभिन्न ASF गुणों को पढ़ने और प्रदर्शित करने के चरण दिखाता है, जिससे आप अपने एसेट्स को आत्मविश्वास के साथ व्यवस्थित, खोज और प्रोसेस कर सकते हैं।

### आप क्या सीखेंगे
- Java प्रोजेक्ट में GroupDocs.Metadata को सेटअप करने का तरीका  
- **ASF मेटाडेटा** जैसे निर्माण तिथि, फ़ाइल ID, और फ़्लैग्स निकालने का तरीका  
- ASF फ़ाइलों में एम्बेडेड कोडेक जानकारी पढ़ने का तरीका  
- विस्तृत मेटाडेटा डिस्क्रिप्टर्स और बेस‑स्ट्रीम प्रॉपर्टीज़ प्रदर्शित करने का तरीका  

आइए आवश्यकताओं के साथ शुरू करते हैं।

## त्वरित उत्तर
- **“ASF मेटाडेटा निकालना” का क्या अर्थ है?** इसका अर्थ है प्रोग्रामेटिक रूप से ASF फ़ाइल से एम्बेडेड जानकारी (जैसे टाइमस्टैम्प, कोडेक्स, डिस्क्रिप्टर्स) पढ़ना।  
- **कौन सी लाइब्रेरी आवश्यक है?** GroupDocs.Metadata for Java (संस्करण 24.12 या बाद का)।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल या टेम्पररी लाइसेंस काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **कौन सा Java संस्करण समर्थित है?** JDK 8 या उससे ऊपर।  
- **क्या मैं Maven का उपयोग कर सकता हूँ?** हाँ – Maven अनुशंसित डिपेंडेंसी मैनेजर है।

## पूर्वापेक्षाएँ

- **Java Development Kit (JDK)** 8 या नया स्थापित हो।  
- **IDE** जैसे IntelliJ IDEA या Eclipse, सुविधाजनक कोडिंग के लिए।  
- **Maven** आपके IDE में कॉन्फ़िगर किया हुआ (वैकल्पिक लेकिन अनुशंसित)।  
- Java और बाहरी लाइब्रेरियों की बुनियादी परिचितता।

## GroupDocs.Metadata for Java सेटअप करना

### Maven इंस्टॉलेशन

`pom.xml` में रिपॉजिटरी और डिपेंडेंसी जोड़ें:

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

### डायरेक्ट डाउनलोड

यदि आप Maven का उपयोग नहीं करना चाहते हैं, तो नवीनतम JAR को [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) से डाउनलोड करें।

### लाइसेंसिंग अवलोकन

- **Free Trial** – मूल्यांकन के लिए GroupDocs वेबसाइट पर उपलब्ध।  
- **Temporary License** – विकास के दौरान सभी फीचर्स को बिना प्रतिबंध के एक्सप्लोर करने देता है।  
- **Full License** – व्यावसायिक या प्रोडक्शन डिप्लॉयमेंट के लिए आवश्यक।

### बेसिक इनिशियलाइज़ेशन

नीचे वह न्यूनतम कोड है जो GroupDocs.Metadata के साथ ASF फ़ाइल खोलने के लिए आवश्यक है:

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## ASF मेटाडेटा क्या है?

ASF (Advanced Systems Format) माइक्रोसॉफ्ट का एक स्ट्रीमिंग फ़ॉर्मेट है जो ऑडियो, वीडियो और मेटाडेटा को एक ही कंटेनर में संग्रहीत करता है। मेटाडेटा में निर्माण टाइमस्टैम्प, कोडेक विवरण, स्ट्रीम डिस्क्रिप्टर्स आदि शामिल होते हैं। **ASF मेटाडेटा निकालकर**, आप फ़ाइल की उत्पत्ति, एन्कोडिंग पैरामीटर्स और कंटेंट विवरणों की प्रोग्रामेटिक समझ प्राप्त करते हैं—जो मीडिया लाइब्रेरीज़, ट्रांसकोडिंग पाइपलाइन और अनुपालन ऑडिट के लिए आवश्यक है।

## GroupDocs.Metadata के साथ ASF मेटाडेटा क्यों निकालें?

- **Zero‑code parsing** – लो‑लेवल ASF पार्सर लागू करने की आवश्यकता नहीं।  
- **Rich object model** – सहज Java क्लासेज़ के माध्यम से प्रॉपर्टीज़, कोडेक्स, डिस्क्रिप्टर्स और स्ट्रीम विवरणों तक पहुंच।  
- **Cross‑platform** – किसी भी OS पर काम करता है जो Java को सपोर्ट करता है।  
- **License flexibility** – आवश्यकता अनुसार ट्रायल से शुरू करके पूर्ण लाइसेंस तक स्केल कर सकते हैं।

## इम्प्लीमेंटेशन गाइड

नीचे के सेक्शन्स में, हम ठोस कोड स्निपेट्स के माध्यम से दिखाएंगे कि कैसे **ASF मेटाडेटा निकालें** कदम‑दर‑कदम।

### बेसिक ASF मेटाडेटा प्रॉपर्टीज़ पढ़ना

**Overview** – निर्माण तिथि, फ़ाइल ID और फ़्लैग्स जैसी मूलभूत जानकारी प्राप्त करना।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

*Why it matters*: निर्माण तिथि जानना संस्करण नियंत्रण में मदद करता है, जबकि फ़ाइल ID सिस्टमों में एसेट को विशिष्ट रूप से पहचानती है।

### ASF कोडेक जानकारी प्रदर्शित करना

**Overview** – ऑडियो और वीडियो स्ट्रीम में उपयोग किए गए कोडेक्स की सूची बनाना।

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

*Why it matters*: कोडेक विवरण प्लेबैक डिवाइसों के साथ संगतता सुनिश्चित करने या ट्रांसकोड करने का निर्णय लेने में आवश्यक हैं।

### मेटाडेटा डिस्क्रिप्टर्स प्रदर्शित करना

**Overview** – भाषा, स्ट्रीम नंबर और मूल शीर्षक जैसे विस्तृत डिस्क्रिप्टर्स निकालना।

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

*Why it matters*: डिस्क्रिप्टर्स सबटाइटल की भाषा या मूल फ़ाइलनाम जैसे संदर्भ देते हैं, जो कैटलॉगिंग के लिए मूल्यवान है।

### बेस स्ट्रीम प्रॉपर्टीज़ प्रदर्शित करना

**Overview** – प्रत्येक बेस स्ट्रीम के बिटरेट, टाइमिंग और भाषा जानकारी तक पहुंच।

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

*Why it matters*: स्ट्रीम प्रॉपर्टीज़ आपको क्वालिटी (बिटरेट) का मूल्यांकन करने और प्लेबैक या एडिटिंग के दौरान ऑडियो/वीडियो को सिंक्रनाइज़ करने में मदद करती हैं।

## सामान्य समस्याएँ और ट्रबलशूटिंग

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| `NullPointerException` जब `getAsfPackage()` कॉल किया जाता है | फ़ाइल पाथ गलत है या फ़ाइल एक वैध ASF कंटेनर नहीं है। | पाथ की जाँच करें और सुनिश्चित करें कि फ़ाइल एक उचित ASF फ़ाइल है। |
| कोडेक जानकारी प्रदर्शित नहीं हो रही है | ASF फ़ाइल में एक प्रोप्राइटरी कोडेक है जिसे लाइब्रेरी संस्करण पहचान नहीं रहा है। | GroupDocs.Metadata को नवीनतम संस्करण में अपडेट करें या कस्टम कोडेक पार्सर का उपयोग करें। |
| डिस्क्रिप्टर सूची खाली है | फ़ाइल में मेटाडेटा डिस्क्रिप्टर्स नहीं हैं (जैसे एन्कोडिंग के दौरान हटाए गए)। | एम्बेडेड मेटाडेटा वाली स्रोत फ़ाइल का उपयोग करें या मेटाडेटा को संरक्षित रखते हुए पुनः‑एन्कोड करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं उसी लाइब्रेरी से अन्य वीडियो फ़ॉर्मेट्स से मेटाडेटा निकाल सकता हूँ?**  
A: हाँ, GroupDocs.Metadata MP4, MKV, AVI और कई अन्य फ़ॉर्मेट्स को सपोर्ट करता है। बस उपयुक्त पैकेज क्लास को इंस्टैंशिएट करें।

**Q: क्या एक्सट्रैक्शन के बाद ASF मेटाडेटा को संशोधित करना संभव है?**  
A: बिल्कुल। लाइब्रेरी अधिकांश प्रॉपर्टीज़ के लिए सेट्टर मेथड्स प्रदान करती है, जिससे आप फ़ाइल को संपादित करके फिर सेव कर सकते हैं।

**Q: बड़े ASF फ़ाइलों के लिए क्या मुझे 64‑bit JVM चाहिए?**  
A: अनिवार्य नहीं, लेकिन 64‑bit JVM अधिक हीप स्पेस देता है, जो बहुत बड़ी मीडिया फ़ाइलों को प्रोसेस करने में मदद करता है।

**Q: लाइसेंसिंग ट्रायल उपयोग को कैसे प्रभावित करती है?**  
A: ट्रायल लाइसेंस सभी कार्यात्मक सीमाओं को हटा देता है लेकिन कुछ आउटपुट में वॉटरमार्क जोड़ता है। प्रोडक्शन के लिए पूर्ण लाइसेंस खरीदें।

**Q: क्या मैं इस कोड को Android पर चला सकता हूँ?**  
A: GroupDocs.Metadata Java SE के लिए बनाया गया है; Android के लिए आपको .NET संस्करण या कोई संगत रैपर उपयोग करना पड़ेगा।

## निष्कर्ष

इस गाइड को फॉलो करके, अब आप जानते हैं कि **GroupDocs.Metadata for Java** का उपयोग करके ASF मेटाडेटा कैसे निकालें। आप बेसिक प्रॉपर्टीज़, कोडेक जानकारी, विस्तृत डिस्क्रिप्टर्स और स्ट्रीम एट्रिब्यूट्स पढ़ सकते हैं—जो आपके मीडिया एसेट्स की पूरी दृश्यता प्रदान करता है। अगले कदमों में इस एक्सट्रैक्शन को बैच प्रोसेसिंग पाइपलाइन में इंटीग्रेट करना, सर्चेबल मेटाडेटा डेटाबेस बनाना, या कोड को विस्तारित करके ASF फ़ाइलों को संशोधित और पुनः‑सेव करना शामिल है।

---

**अंतिम अपडेट:** 2025-12-26  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs