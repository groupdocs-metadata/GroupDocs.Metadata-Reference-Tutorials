---
date: '2026-02-06'
description: GroupDocs.Metadata का उपयोग करके जावा में दस्तावेज़ प्रीव्यू बनाना और
  पृष्ठ को इमेज के रूप में आउटपुट करना सीखें। यह गाइड सेटअप, कॉन्फ़िगरेशन और इम्प्लीमेंटेशन
  चरणों को कवर करता है।
keywords:
- document image preview
- GroupDocs Metadata Java
- creating document previews with Java
title: GroupDocs.Metadata के साथ जावा में दस्तावेज़ प्रीव्यू कैसे बनाएं
type: docs
url: /hi/java/document-formats/java-groupdocs-metadata-document-image-previews/
weight: 1
---

# जावा में GroupDocs.Metadata के साथ दस्तावेज़ इमेज प्रीव्यू में महारत हासिल करना

## परिचय

यदि आपको **create document preview java** एप्लिकेशन बनाने की आवश्यकता है—चाहे वह दस्तावेज़ प्रबंधन प्रणाली, डिजिटल लाइब्रेरी, या एंटरप्राइज़ पोर्टल में क्विक‑लुक फीचर के लिए हो—GroupDocs.Metadata इसे सरल बनाता है। इस ट्यूटोरियल में आप सीखेंगे कि कैसे एक दस्तावेज़ लोड करें, प्रीव्यू विकल्प कॉन्फ़िगर करें, और पेज को इमेज फ़ाइलों के रूप में आउटपुट करें, सभी साफ़ जावा कोड के साथ।

हम पूर्ण वर्कफ़्लो को कवर करेंगे, Maven सेटअप से लेकर विशिष्ट पृष्ठों के लिए PNG प्रीव्यू जेनरेट करने तक। क्या आप अपने दस्तावेज़ों को इमेज के रूप में जीवंत होते देखना चाहते हैं? चलिए शुरू करते हैं!

## त्वरित उत्तर
- **create document preview java** का क्या मतलब है? जावा कोड का उपयोग करके दस्तावेज़ पृष्ठों के दृश्य स्नैपशॉट (जैसे PNG) बनाना।  
- **कौन सी लाइब्रेरी इसको आउट‑ऑफ़‑द‑बॉक्स सपोर्ट करती है?** GroupDocs.Metadata for Java।  
- **क्या मैं इमेज फ़ॉर्मेट चुन सकता हूँ?** हाँ—प्रीव्यू विकल्प आपको PNG, JPEG, BMP आदि चुनने देते हैं।  
- **क्या मुझे लाइसेंस चाहिए?** मूल्यांकन के लिए फ्री ट्रायल काम करता है; प्रोडक्शन के लिए पेड लाइसेंस आवश्यक है।  
- **क्या केवल चयनित पृष्ठों का प्रीव्यू संभव है?** बिल्कुल—विशिष्ट पृष्ठों को लक्षित करने के लिए `setPageNumbers` का उपयोग करें।

## क्या है **create document preview java**?

जावा में दस्तावेज़ प्रीव्यू बनाना मतलब है कि प्रोग्रामेटिकली फ़ाइल (DOCX, PDF, PPT, आदि) के एक या अधिक पृष्ठों को इमेज फ़ाइलों में रेंडर करना। यह थंबनेल गैलरी, त्वरित दृश्य जांच, और वेब या डेस्कटॉप UI घटकों के साथ सहज इंटीग्रेशन को सक्षम बनाता है।

## प्रीव्यू जेनरेशन के लिए GroupDocs.Metadata क्यों उपयोग करें?

- **कोई बाहरी निर्भरताएँ नहीं** – शुद्ध जावा, कोई नेटिव बाइनरी नहीं।  
- **100 से अधिक फ़ाइल फ़ॉर्मेट्स का समर्थन** – ऑफिस से लेकर CAD तक।  
- **सूक्ष्म नियंत्रण** – इमेज फ़ॉर्मेट, DPI, और पेज रेंज चुनें।  
- **उच्च प्रदर्शन** – बड़े दस्तावेज़ों और बैच प्रोसेसिंग के लिए ऑप्टिमाइज़्ड।

## पूर्वापेक्षाएँ

- **आवश्यक लाइब्रेरीज़:** GroupDocs.Metadata for Java (नवीनतम संस्करण)।  
- **बिल्ड सिस्टम:** Maven प्रोजेक्ट (या मैन्युअल JAR इन्क्लूज़न)।  
- **कौशल सेट:** Java I/O, try‑with‑resources, और एक्सेप्शन हैंडलिंग की परिचितता।

## GroupDocs.Metadata को जावा के लिए सेट अप करना

### इंस्टॉलेशन जानकारी

Add the GroupDocs repository and dependency to your `pom.xml`:

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

**डायरेक्ट डाउनलोड**  
वैकल्पिक रूप से, नवीनतम JARs को [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) से डाउनलोड करें और उन्हें अपने प्रोजेक्ट के क्लासपाथ में जोड़ें।

### लाइसेंस प्राप्ति

फ्री ट्रायल से शुरू करें या एक अस्थायी लाइसेंस का अनुरोध करें। प्रोडक्शन उपयोग के लिए, यहाँ लाइसेंस खरीदें: [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)।

### बेसिक इनिशियलाइज़ेशन और सेटअप

The following snippet shows the minimal code required to open a document with GroupDocs.Metadata:

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;

public class LoadDocument {
    public static void main(String[] args) {
        // Replace with your actual document path
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            System.out.println("Document loaded successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## इम्प्लीमेंटेशन गाइड

नीचे हम समाधान को तीन केंद्रित फीचर्स में विभाजित करते हैं। प्रत्येक फीचर में संक्षिप्त व्याख्याएँ और आवश्यक कोड शामिल हैं—कोई अतिरिक्त स्निपेट नहीं, केवल मूल ब्लॉक्स संरक्षित।

### फ़ीचर 1: दस्तावेज़ प्रोसेसिंग के लिए मेटाडेटा इनिशियलाइज़ करें

**समीक्षा**  
दस्तावेज़ को लोड करना वह पहला कदम है जिसके बाद कोई भी प्रीव्यू जेनरेट किया जा सकता है।

#### Step 1 – Import Classes  

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;
```

#### Step 2 – Load the Document  

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
try (Metadata metadata = new Metadata(documentPath)) {
    System.out.println("Document loaded successfully.");
} catch (IOException e) {
    e.printStackTrace();
}
```

**टिप्स**  
- कोड चलाने से पहले फ़ाइल पाथ और रीड परमिशन की जाँच करें।  
- टेस्टिंग के दौरान क्लासपाथ की गड़बड़ी से बचने के लिए एब्सोल्यूट पाथ का उपयोग करें।

### फ़ीचर 2: दस्तावेज़ पृष्ठों के लिए प्रीव्यू विकल्प बनाएं

**समीक्षा**  
प्रीव्यू की दिखावट और कौन से पृष्ठ रेंडर करने हैं, इसे कॉन्फ़िगर करें।

#### Step 1 – Import Preview Classes  

```java
import com.groupdocs.metadata.options.PreviewFormats;
import com.groupdocs.metadata.options.PreviewOptions;
import java.io.OutputStream;
```

#### Step 2 – Set Up Preview Options  

```java
OutputStream outputStream = null; // Replace with actual implementation if needed

PreviewOptions previewOptions = new PreviewOptions(outputStream::write);
previewOptions.setPreviewFormat(PreviewFormats.PNG); // Set the format of the preview image
previewOptions.setPageNumbers(new int[]{1}); // Specify page numbers to generate previews for
```

**यह क्यों महत्वपूर्ण है**  
`PNG` चुनने से लॉसलेस क्वालिटी मिलती है, जो थंबनेल के लिए आदर्श है। आवश्यक पेज रेंज को प्रीव्यू करने के लिए `setPageNumbers` को एडजस्ट करें।

### फ़ीचर 3: इमेज आउटपुट के लिए पेज स्ट्रीम बनाएं

**समीक्षा**  
हर प्रीव्यू इमेज को फ़ाइल या किसी अन्य आउटपुट डेस्टिनेशन में लिखना आवश्यक है।

#### Step 1 – Import I/O Classes  

```java
import java.io.FileOutputStream;
import java.io.File;
import java.io.OutputStream;
import java.io.IOException;
```

#### Step 2 – Generate the Stream and Write the Image  

```java
int pageNumber = 1; // Example page number

try {
    File outputFile = new File(String.format("YOUR_OUTPUT_DIRECTORY/result_%d.png", pageNumber));
    OutputStream stream = new FileOutputStream(outputFile);
    System.out.println("Page stream created for output.");
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

**प्रो टिप:** सुनिश्चित करें कि `YOUR_OUTPUT_DIRECTORY` पहले से मौजूद है, या प्रोग्रामेटिकली `outputFile.getParentFile().mkdirs();` से बनाएं।

## GroupDocs.Metadata के साथ **output page as image** कैसे करें

फ़ीचर 2 के प्रीव्यू विकल्पों को फ़ीचर 3 की स्ट्रीम लॉजिक के साथ मिलाकर, आप किसी भी पेज को इमेज फ़ाइल में रेंडर कर सकते हैं:

1. `Metadata` इनिशियलाइज़ करें (फ़ीचर 1)।  
2. `PreviewOptions` इंस्टेंस बनाएं, `PNG` और इच्छित पेज नंबर निर्दिष्ट करें।  
3. एक लैम्ब्डा पास करें जो प्रीव्यू बाइट्स को उस `OutputStream` में लिखे जो आपने फ़ीचर 3 में बनाया था।  

यह फ्लो आपको **output page as image** को प्रभावी ढंग से करने देता है, यहाँ तक कि बड़े दस्तावेज़ों के लिए भी।

## व्यावहारिक अनुप्रयोग

- **डॉक्यूमेंट मैनेजमेंट सिस्टम:** फ़ाइल ब्राउज़र में थंबनेल दिखाएं।  
- **डिजिटल लाइब्रेरीज़:** स्कैन की गई पुस्तकों के लिए त्वरित दृश्य संकेत प्रदान करें।  
- **लीगल/फ़ाइनेंस:** अनुबंध पृष्ठों की तेज़ जांच सक्षम करें।  
- **CMS प्लेटफ़ॉर्म:** अपलोड किए गए रिपोर्ट्स के लिए ऑटो‑जेनरेट प्रीव्यू इमेज।  
- **ई‑लर्निंग:** छात्रों को डाउनलोड से पहले लेक्चर स्लाइड्स का एक झलक दें।

## प्रदर्शन संबंधी विचार

- **पेज बैच सीमित करें:** एक साथ कई पेज जेनरेट करने से मेमोरी उपयोग बढ़ सकता है।  
- **try‑with‑resources का उपयोग करें:** स्ट्रीम्स को बंद रखता है, लीक रोकता है।  
- **JVM हीप मॉनिटर करें:** बड़े PDFs को बढ़ी हुई हीप (`-Xmx`) की आवश्यकता हो सकती है।

## सामान्य समस्याएँ और समाधान

| समस्या | कारण | समाधान |
|-------|-------|-----|
| `outputStream` पर `NullPointerException` | `outputStream` इनिशियलाइज़ नहीं है | एक वास्तविक `OutputStream` प्रदान करें (जैसे, `new FileOutputStream(...)`)। |
| कोई प्रीव्यू जेनरेट नहीं हुआ | गलत पेज नंबर | पेज मौजूद है या नहीं जाँचें; वैधता के लिए `metadata.getPageCount()` का उपयोग करें। |
| फ़ाइल लिखते समय परमिशन त्रुटि | आउटपुट डायरेक्टरी केवल-रीड है | राइट परमिशन दें या लिखने योग्य फ़ोल्डर चुनें। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न:** क्या मैं पासवर्ड‑प्रोटेक्टेड दस्तावेज़ों के लिए प्रीव्यू जेनरेट कर सकता हूँ?  
**उत्तर:** हाँ। दस्तावेज़ को उस कंस्ट्रक्टर से खोलें जो पासवर्ड स्वीकार करता है, फिर प्रीव्यू विकल्पों के साथ आगे बढ़ें।

**प्रश्न:** कौन से इमेज फ़ॉर्मेट सपोर्टेड हैं?  
**उत्तर:** `PreviewFormats` के माध्यम से PNG, JPEG, BMP, और GIF उपलब्ध हैं।

**प्रश्न:** मैं एक कॉल में कई पेज कैसे प्रीव्यू करूँ?  
**उत्तर:** `previewOptions.setPageNumbers(new int[]{1,2,3});` में पेज नंबरों की एरे पास करें।

**प्रश्न:** क्या इमेज रेज़ोल्यूशन को नियंत्रित करने का कोई तरीका है?  
**उत्तर:** `previewOptions.setDpi(int dpi)` का उपयोग करके DPI समायोजित करें (डिफ़ॉल्ट 96 DPI है)।

**प्रश्न:** क्या लाइब्रेरी Android पर काम करती है?  
**उत्तर:** GroupDocs.Metadata शुद्ध जावा है और उपयुक्त JARs के साथ Android पर उपयोग की जा सकती है, लेकिन UI रेंडरिंग Android फ्रेमवर्क द्वारा संभाली जानी चाहिए।

## निष्कर्ष

अब आपके पास **create document preview java** समाधान के लिए एक पूर्ण, प्रोडक्शन‑रेडी गाइड है जो GroupDocs.Metadata का उपयोग करके **output page as image** फ़ाइलें बनाता है। तीन फीचर चरणों—मेटाडेटा इनिशियलाइज़ करना, प्रीव्यू विकल्प कॉन्फ़िगर करना, और इमेज स्ट्रीम लिखना—का पालन करके आप किसी भी जावा एप्लिकेशन में हाई‑क्वालिटी प्रीव्यू इंटीग्रेट कर सकते हैं।

---

**अंतिम अपडेट:** 2026-02-06  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs