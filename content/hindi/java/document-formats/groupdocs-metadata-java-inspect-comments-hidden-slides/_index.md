---
date: '2026-02-01'
description: GroupDocs.Metadata Java API का उपयोग करके छिपी स्लाइड्स की जाँच करना
  और PPT टिप्पणियों को निकालना सीखें। अपनी प्रस्तुति प्रबंधन कार्यप्रवाह को अनुकूलित
  करें।
keywords:
- GroupDocs Metadata Java
- inspect presentation comments
- identify hidden slides
title: GroupDocs.Metadata Java का उपयोग करके छिपी स्लाइड्स जांचें
type: docs
url: /hi/java/document-formats/groupdocs-metadata-java-inspect-comments-hidden-slides/
weight: 1
---

# GroupDocs.Metadata Java का उपयोग करके छिपी स्लाइड्स जांचें

ाइड्स जांचनी** पड़ती हैं या समीक्षक नोट्स निकालने पड़ते हैं जो पहली नज़र में दिखाई नहीं देते। चाहे आप क्लाइंट डेक तैयार कर रहे हों, अनुपालन ऑडिट कर रहे हों, या बसस्थित कर रहे हों, प्रोग्रामेटिक। इस गाइड में हम आपको **छिपी स्लाइड्स जांचने** और **ppt कमेंट्स निकालने** का तरीका दिखाएंगे **GroupDocs.Metadata Java** लाइब्रेरी के साथ, ताकि कुछ भी अनदेखा न रहे।

## त्वरित उत्तर
- **“check hidden slides” का क्या अर्थ है?** इसका मतलब है प्रोग्रामेटिकली उन स्लाइड्स का पता लगाना जो PowerPoint फ़ाइल में छिपी (hidden) के रूप में चिह्नित हैं।  
- **कौन सा API कमेंट्स को संभालता है?** `GroupDocs.Metadata` `getComments()` मेथड प्रदान करता है **ppt कमेंट्स निकालने** के लिए।  
- **क्या करता है; प्रोडक्शन के लिए एक कमर्शियल लाइसेंस आवश्यक है।  
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 या उससे ऊपर; लाइब्रेरी Java 11 + के साथ भी संगत है।  
- **क्या मैं Maven का उपयोग कर सकता हूँ?** हाँ – Maven कोऑर्डिनेट्स सेटअप सेक्शन में दिखाए गए हैं।

## “check hidden slides” क्या है?
एक छिपी स्लाइड वह स्लाइड है जिसका विज़िबिलिटी फ़्लैग प्रस्तुति फ़ाइल में *false* पर सेट होता है। ये स्लाइड्स सामान्य स्लाइड शो में दिखायी नहीं देतीं लेकिन फ़ाइल का हिस्सा बनी रहती हैं। इन्हें पहचानने से आप कंटेंट का या प्रकाशित़ कर सकते हैं।

## GroupDocs.Metadata Java का उपयोग क्यों करें?
* **Full‑metadata access** – PowerPoint में फ़ाइल खोलनेformat support** – PPT, PPTX और अन्य Office फ़ॉर्मैट्स के साथ काम करता है।  
* **Lightweight** – भारी UI डिपेंडेंसीज़ नहीं, बैकएंड सर्विसेज़ के लिए उपयुक्त।  
* **Robust licensing** – परीक्षण के लिए ट्रायल, प्रोडक्शन के लिए कमर्शियल लाइसेंस।

## आवश्यकताएँ
शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:
12 या नया) – मुख्य लाइब्रेरी जो आपको मेटाडेटा पढ़ने और लिखने देती है।  
- **Java Development Kit (JDK)** – आपके मशीन पर JDK 8 ।  
- **Maven** (वैकल्पिक) – यदि आप Maven के माध्यम से डिपेंडेंसी मैनेजमेंट पसंद करते हैं।  
- बेसिक Java ज्ञान – आपको क्लासेज़, try‑with‑resources, और लूप्स में सहज होना चाहिए।

## GroupDocs.Metadata for Java सेटअप करना

### Maven सेटअप
अपने `pom.xml` फ़ाइल में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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
यदि आप Maven का उपयोग नहीं करना चाहते, तो आधिकारिक डाउनलोड पेज से नवीनतम JAR प्राप्त करें: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java लिए एक ट्रायल लाइसेंस डाउनलोड करें।  
- **Temporary License** – विस्तारित मूल्यांकन के लिए एक टेम्पररी की अनुरोध करें।  
- **Purchase** – अनलिमिटेड प्रोडक्शन उपयोग के लिए पूर्ण लाइसेंस प्राप्त करें।

### बेसिकअप

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata object with your document path
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputPpt")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

लाइब्रेरी तैयार होने के बाद, चलिए दो मुख्य कार्यों में डुबकी लगाते हैं: **ppt कमेंट्स निकालना** और **छिपी स्लाइड्स जांचना**।

## GroupDocs.Metadataेशन मेटाडेटा लोड करें
सबसे पहले, फ़ाइल खोलें करें जो आपको इंस्पेक्शन डेटा तक पहुंच देता है।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputPpt")) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
```

### चरण 2: कमेंट्स पर इटरेट करें
अब, सुनिश्चित करें कि कमेंट्स मौजूद हैं और प्रत्येक कमेंट पर लूप करके उपयोगी विवरण जैसे लेखक, टेक्स्ट, निर्माण समय, और स्लाइड नंबर निकालें।

```java
import com.groupdocs.metadata.core.PresentationComment;

if (root.getInspectionPackage().getComments() != null) {
    for (PresentationComment comment : root.getInspectionPackage().getComments()) {
        System.out.println(comment.getAuthor());
        System.out.println(comment.getText());
        System.out.println(comment.getCreatedTime());
        System.out.println(comment.getSlideNumber());
    }
}
```

**यह क्यों महत्वपूर्ण है:** कमेंट्स निकालनेत्रित कर सकते हैं, ऑ सारांश रिपोर्ट बना सकते हैं।

#### ट्रबलशूटिंग टिप्स
- **File path errors:** `YOUR_DOCUMENT_DIRECTORY` पाथ को दोबारा  
- **No comments found:** सुनिश्चित करें कि स्रोत PPT में वास्तव में कमेंट्स हैं; अन्यथा `getComments()` सूची `null` होगी।

## GroupDocs.Metadata Java का उपयोग करके प्रेज़ेंटेशन में छिपी स्लाइड्स कैसे जांचें

### चरण 1: प्रेज़ेंटेशन मेटाडेटा लोड करें (ऊपर जैसा ही)

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputPpt")) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
```

### चरण 2: छिपी स्लाइड्स पर इटरेट करें
`getHiddenSlides()` मेथड का उपयोग करके किसी भी छिपी स्लाइड को प्राप्त करें और उनके पहचानकर्ता प्रिंट करें।

```java
import com.groupdocs.metadata.core.PresentationSlide;

if (root.getInspectionPackage().getHiddenSlides() != null) {
    for (PresentationSlide slide : root.getInspectionPackage().getHiddenSlides()) {
        System.out.println(slide.getName());
        System.out.println(slide.getNumber());
        System.out.println(slide.getSlideId());
    }
}
```

**यह क्यों महत्वपूर्ण हैनीय सामग्री हटाना) और सुनिश्चित कर सकते हैं कि अंतिम डेक के साथ कोई अनपेक्षित सामग्री न भेजी जाए।

#### ट्रबलशूटिंग टिप्स
- **No hidden slides returned:** पुष्टि करें कि प्रेज़ेंटेशन में वास्तव में छिपी स्लाइड्स हैं; अन्यथा सूची `null` होगी।  
- **Permission issues:** सुनिश्चित करें कि आपका Java प्रोसेस PPT फ़ाइल वाले डायरेक्टरी को पढ़ने की अनुमति रखता है।

## व्यावहारिक अनुप्रयोग

| परिदृश्य | API कैसे मदद करता है |
|----------|----------------------|
| **रिव्यू समेकन** | **Extract ppt comments** को उपयोग करके समीक्षक फीडबैक को एक दस्तावेज़ में संकलित करें। |
| ** का उपयोग करके सुनिश्चित करें कि कोई गुप्त या पुरानी सामग्री वितरित न हो। |
| **स्वचालित सफ़ाई** | दोनों फीचर्स को मिलाकर छिपी सामग्री और कमेंट्स की रिपोर्ट बनाएं, फिर प्रोग्रामेटिकली उन्हें हटाएं या फ़्लवर्ज़न कंट्रोल** | एक्सट्रैक्टेड मेटाडेटा को डेटाबीजन में बदलावों को ट्रैक किया जा सके। |

## प्रदर्शन संबंधी विचार
- **try‑with‑resources** का उपयोग करके `Metadata` ऑब्जेक्ट को स्वचालित रूप से बंद करें और नेटिव रिसोर्सेज़ मुक्त करें।  
- यदि आपको केवल कुछ स्लाइड्स चाहिए तो बड़े डेक को चंक्स में प्रोसेस करें्रेरी द्वारा प्रदान किए गए बिल्ट‑इन कैशिंग का उपयोग करके एक ही फ़ाइल को बार‑बाराइल नहीं खोल पा रहा है | फ़ाइल पाथ की जाँच करें और सुनिश्चित करें कि फ़ाइल किसी अन्य प्रोसेस द्वारा लॉक नहीं है। |
| कोई कमेंट्स या छिपी स्लाइड्स नहीं मिलीं | PPT को PowerPoint में खोलकर पुष्टि करें। |
| लाइसेंस एक्सेप्शन फेंका गया | किसी भी API कॉल से पहले वैध ट्रायल या कमर्शियल लाइसेंस लागू करें। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं पासवर्ड‑सुरक्षित प्रेज़ेंटेशन से कमेंट्स निकाल सकता हूँ?**  
**उत्तर:** ह` कंस्ट्रक्टर का उपयोग करें जो `LoadOptions` ऑब्जेक्ट लेता है।

**प्रश्न: क्या API दोनों PPT और PPTX फ़ॉर्मैट्स को सपोर्ट करता है?**  
**उत्तर:** बिल्कुल। `GroupDocs.Metadata` स्वचालित रूप से फ़ॉर्मैट का पता लगाता है और एकीकृत इंस्पेक्शन इंटरफ़ेस प्रदान करता है।

**प्रश्न: क्या API के माध्यम से छिपी स्लाइड्स को संशोधित या हटाया जा सकता है?**  
**उत्तर:** वर्तमान संस्करण केवल रीड‑ओनली इंस्पेक्शन पर केंद्रित है। एडिटिंग के लिए, `GroupDocs.Metadata` को `Group्रेरीज़ के साथ मिलाएँ।

**प्रश्न: बड़े प्रेज़ेंटेशन (सैकड़ों MB) को कैसे हैंडल करें?**  
**उत्तर:** फ़ाइल को स्ट्रीमिंग तरीके से प्रोसेस करें और आवश्यक डेटा एकत्र करने के बाद प्रत्येक `PresentationSlide` ऑब्जेक्ट को डिस्पोज़ करें।

**प्रश्न: JAR डाउनलोड होने के बाद क्या मुझे इंटरनेट कनेक्शन की आवश्यकता है?**  
**उत्तर:** नहीं। JAR को प्रोजेक्ट में जोड़ने के बाद सभी ऑपरेशन्स लोकली चलते हैं।

## निष्कर्ष

अब आपके पास **छिपी स्लाइड्स जांचने** और **ppt कमेंट्स निकालने** के लिए एक पूर्ण, प्रोडक्शन‑रेडी एGroupDocs.Metadata Java** लाइब्रेरी का उपयोग करता है। इन स्निपेट्स को अपने बैकएंड सर्विसेज़ में इंटीग्रेट करके आप प्रेज़ेंटेशन ऑडिट्स को ऑटोमेट कर सकते हैं, फीडबैक लूप्स को सरल बना सकते हैं, और सुनिश्चित कर सकते हैं कि हर स्लाइड—दिखाई दे या छिपी—आपके संगठन के मानकों को पूरा करे।

अग जैसे दस्तावेज़ प्रॉपर्टी एक्सट्रैक्शन, वर्ज़न हिस्ट्री एनालिसिस, आदि को एक्सप्लोर करें ताकि अपने दस्तावेज़ प्रबंधन वर्कफ़्लो को और बेहतर बना सकें।

---

**अंतिम अपडेट:** 2026-02-01  
**परीक्षित संस्करण:** GroupDocs.Metadata Java 24.12  
**लेखक:** GroupDocs