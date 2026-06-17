---
date: '2026-06-17'
description: GroupDocs.Metadata का उपयोग करके Java में Diagram फ़ाइलों के लिए Metadata
  अपडेट को स्वचालित करने और Diagram निर्माण समय बदलने के तरीके सीखें।
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: GroupDocs Java के साथ Metadata में Diagram निर्माण समय बदलें
type: docs
url: /hi/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# GroupDocs Java के साथ मेटाडेटा में डायग्राम निर्माण समय बदलें

इस चरण‑दर‑चरण ट्यूटोरियल में आप जानेंगे कि **डायग्राम निर्माण समय** को कैसे बदलें और GroupDocs.Metadata लाइब्रेरी फ़ॉर जावा का उपयोग करके डायग्राम फ़ाइलों की अन्य बिल्ट‑इन प्रॉपर्टीज़ को कैसे अपडेट करें। इन बदलावों को स्वचालित करने से मैन्युअल संपादन में घंटों की बचत होती है, आपके रिपॉज़िटरी में टाइमस्टैम्प्स सुसंगत रहते हैं, और आपके डायग्राम किसी भी दस्तावेज़‑प्रबंधन प्रणाली में तुरंत खोज योग्य बन जाते हैं।

## त्वरित उत्तर
- **प्राथमिक लक्ष्य क्या है?** डायग्राम निर्माण समय और डायग्राम फ़ाइलों में अन्य मेटाडेटा बदलें।  
- **कौन सी लाइब्रेरी उपयोग करनी चाहिए?** GroupDocs.Metadata for Java.  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए एक फ्री ट्रायल पर्याप्त है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **क्या मैं कई डायग्रामों को बैच‑प्रोसेस कर सकता हूँ?** हाँ—इसी लॉजिक को लूप या पैरलल स्ट्रीम में रैप करें।  
- **कौन सा जावा संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।

## डायग्राम मेटाडेटा में “डायग्राम निर्माण समय बदलना” क्या है?
निर्माण समय बदलने से डायग्राम फ़ाइल (जैसे VDX या VSDX) के अंदर संग्रहीत मूल टाइमस्टैम्प को नई तिथि‑समय मान से ओवरराइट किया जाता है। इससे आप फ़ाइल के मेटाडेटा को वास्तविक प्रोसेसिंग या आर्काइविंग तिथि के साथ संरेखित कर सकते हैं, न कि लेखक के मूल टाइमस्टैम्प के साथ, जो ऑडिट ट्रेल और सटीक खोज परिणामों के लिए आवश्यक है।

## डायग्राम के लिए मेटाडेटा अपडेट को स्वचालित क्यों करें?
मेटाडेटा को स्वचालित करने से यह सुनिश्चित होता है कि प्रत्येक डायग्राम बिना मानवीय त्रुटि के समान नामकरण, वर्गीकरण और टाइमस्टैम्प मानकों का पालन करे। यह बड़े पैमाने पर माइग्रेशन को तेज़ करता है, अनुपालन जोखिम को कम करता है, और एंटरप्राइज़ DMS प्लेटफ़ॉर्म में खोजयोग्यता को सुधारता है—बड़े‑पैमाने के प्रोजेक्ट्स में मैन्युअल प्रयास का 70 % तक बचाता है।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK) 8+** आपके मशीन पर स्थापित होना चाहिए।  
- **IDE** जैसे IntelliJ IDEA या Eclipse।  
- **Maven** (या मैन्युअल JAR हैंडलिंग) डिपेंडेंसी मैनेजमेंट के लिए।  
- Java क्लासेज़, मेथड्स, और एक्सेप्शन हैंडलिंग की बुनियादी समझ।

### आवश्यक लाइब्रेरीज़ और डिपेंडेंसीज़
यदि आप Maven का उपयोग कर रहे हैं तो अपने `pom.xml` फ़ाइल में निम्नलिखित रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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
यदि आप सीधे डाउनलोड करना पसंद करते हैं, तो नवीनतम संस्करण प्राप्त करने के लिए [GroupDocs.Metadata for Java रिलीज़](https://releases.groupdocs.com/metadata/java/) पर जाएँ।

### पर्यावरण सेटअप
- JDK 8 या नया।  
- IntelliJ IDEA, Eclipse, या कोई भी Java‑संगत IDE।

### ज्ञान पूर्वापेक्षाएँ
Java सिंटैक्स और बुनियादी फ़ाइल I/O की समझ ट्यूटोरियल को सुगम बनाएगी, लेकिन चरणों को सरल भाषा में समझाया गया है।

## GroupDocs.Metadata फ़ॉर जावा सेटअप करना
### इंस्टॉलेशन निर्देश
**Maven उपयोगकर्ता:** ऊपर दिया गया स्निपेट रिपॉज़िटरी और आवश्यक JAR को स्वचालित रूप से जोड़ता है।  
**डायरेक्ट डाउनलोड उपयोगकर्ता:** [GroupDocs](https://releases.groupdocs.com/metadata/java/) से JAR डाउनलोड करने के बाद, इसे अपने प्रोजेक्ट के क्लासपाथ में जोड़ें।

### लाइसेंस प्राप्ति
- **Free Trial:** लाइब्रेरी को बिना लागत के एक्सप्लोर करें।  
- **Temporary License:** विस्तारित परीक्षण के लिए एक टेम्पररी लाइसेंस प्राप्त करें [यहाँ](https://purchase.groupdocs.com/temporary-license/)।  
- **Purchase:** प्रोडक्शन एनवायरनमेंट्स के लिए पूर्ण लाइसेंस प्राप्त करें।

### बुनियादी इनिशियलाइज़ेशन
`Metadata` वह कोर क्लास है जो दस्तावेज़ के मेटाडेटा कंटेनर को दर्शाता है और सभी बिल्ट‑इन प्रॉपर्टीज़ तक रीड/राइट एक्सेस प्रदान करता है। GroupDocs.Metadata का उपयोग शुरू करने के लिए, क्लास इम्पोर्ट करें और एक डायग्राम फ़ाइल खोलें:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

लाइब्रेरी इनिशियलाइज़ होने के बाद, आप अब किसी भी बिल्ट‑इन प्रॉपर्टी को संशोधित कर सकते हैं, जिसमें निर्माण समय भी शामिल है।

## कार्यान्वयन गाइड
### डायग्राम फ़ाइलों में निर्माण समय कैसे बदलें
इस सेक्शन में हम प्रत्येक चरण को समझेंगे जो **डायग्राम निर्माण समय बदलने** और लेखक, कंपनी, तथा श्रेणी जैसी अन्य सामान्य प्रॉपर्टीज़ को अपडेट करने के लिए आवश्यक है। प्रक्रिया में Metadata API के साथ डायग्राम लोड करना, उसके रूट पैकेज तक पहुंचना, इच्छित फ़ील्ड सेट करना, और अंत में बदलावों को नई फ़ाइल में सेव करना शामिल है, जिससे मूल फ़ाइल अपरिवर्तित रहती है।

#### चरण 1: डायग्राम दस्तावेज़ लोड करें
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Explanation:* `Metadata` कंस्ट्रक्टर आपके डायग्राम फ़ाइल का पाथ लेता है। `try‑with‑resources` ब्लॉक ऑपरेशन के बाद फ़ाइल को सही तरीके से बंद करता है।

#### चरण 2: रूट पैकेज तक पहुंचें
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Explanation:* रूट पैकेज आपको डायग्राम के सभी बिल्ट‑इन मेटाडेटा फ़ील्ड्स तक सीधी पहुंच देता है।

#### चरण 3: क्रिएटर प्रॉपर्टी सेट करें
```java
root.getDocumentProperties().setCreator("test author");
```  
*Explanation:* नया लेखक नाम असाइन करता है। `"test author"` को वास्तविक निर्माता से बदलें।

#### चरण 4: निर्माण समय बदलें
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Explanation:* यह लाइन **निर्माण समय बदलती** है और इसे वर्तमान सिस्टम तिथि और समय पर सेट करती है। यदि आपको कस्टम टाइमस्टैम्प चाहिए तो आप एक विशिष्ट `Date` इंस्टेंस भी पास कर सकते हैं।

#### चरण 5: कंपनी जानकारी निर्धारित करें
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Explanation:* डायग्राम से जुड़ा कंपनी नाम संग्रहीत करता है—एंटरप्राइज़ ट्रैकिंग के लिए उपयोगी।

#### चरण 6: दस्तावेज़ श्रेणी सेट करें
```java
root.getDocumentProperties().setCategory("test category");
```  
*Explanation:* फ़ाइल को वर्गीकृत करता है, जिससे आप अपने रिपॉज़िटरी में **डायग्राम श्रेणी अपडेट** को सुसंगत रूप से कर सकते हैं।

#### चरण 7: कीवर्ड जोड़ें
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Explanation:* कीवर्ड खोजयोग्यता को बढ़ाते हैं; आप डायग्राम की सामग्री से संबंधित कोई भी शब्द सूचीबद्ध कर सकते हैं।

#### चरण 8: बदलाव सहेजें
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Explanation:* सभी संशोधनों को नई फ़ाइल में सहेजता है, मूल फ़ाइल को अपरिवर्तित छोड़ता है।

### सामान्य कठिनाइयाँ और ट्रबलशूटिंग
- **File Not Found:** फ़ाइल नहीं मिली — इनपुट पाथ की जाँच करें और सुनिश्चित करें कि फ़ाइल एक्सटेंशन वास्तविक फ़ॉर्मेट से मेल खाता है।  
- **Access Denied:** एक्सेस अस्वीकृत — इनपुट और आउटपुट दोनों डायरेक्टरी के रीड/राइट परमिशन की जाँच करें।  
- **Invalid Date Format:** अमान्य तिथि फ़ॉर्मेट — API के साथ संगत `java.util.Date` या `java.time` ऑब्जेक्ट्स का उपयोग करें।

## व्यावहारिक अनुप्रयोग
1. **डॉक्यूमेंट आर्काइविंग का स्वचालन** – पुराने डायग्रामों को आर्काइव में ले जाते समय, स्वचालित रूप से **डायग्राम निर्माण समय** को आर्काइविंग तिथि पर बदलें और एक समान श्रेणी सेट करें।  
2. **वर्ज़न कंट्रोल इंटीग्रेशन** – प्रत्येक रिलीज़ के दौरान निर्माण समय अपडेट करके टाइमस्टैम्प को Git कमिट्स के साथ सिंक रखें।  
3. **एंटरप्राइज़ DMS मानकीकरण** – सभी डायग्राम एसेट्स में लेखक, कंपनी, और कीवर्ड के लिए कंपनी‑व्यापी नीति लागू करें।

## प्रदर्शन संबंधी विचार
- **बैच प्रोसेसिंग:** ऊपर दिए गए चरणों को लूप में रैप करके एक रन में दर्जनों फ़ाइलों को संभालें।  
- **मेमोरी मैनेजमेंट:** प्रत्येक `Metadata` इंस्टेंस को तुरंत रिलीज़ करें (try‑with‑resources ब्लॉक यह स्वचालित रूप से करता है)।  
- **असिंक्रोनस एक्सिक्यूशन:** बड़े बैच के लिए, `CompletableFuture` पर विचार करें ताकि अपडेट्स को पैरालल में चलाया जा सके बिना मुख्य थ्रेड को ब्लॉक किए।  
- **मात्रात्मक क्षमता:** GroupDocs.Metadata 30 से अधिक डायग्राम फ़ॉर्मेट्स को सपोर्ट करता है और 500 MB तक की फ़ाइलों को बिना पूरे दस्तावेज़ को मेमोरी में लोड किए प्रोसेस कर सकता है, सामान्य सर्वर हार्डवेयर पर प्रति फ़ाइल 200 ms से कम समय में अपडेट प्रदान करता है।

## निष्कर्ष
अब आप जानते हैं कि GroupDocs.Metadata का उपयोग करके जावा में **डायग्राम निर्माण समय बदलना** और डायग्राम दस्तावेज़ों के अन्य बिल्ट‑इन मेटाडेटा प्रॉपर्टीज़ को कैसे अपडेट करना है। इन चरणों को स्वचालित करके, आप अपने संगठन में सुसंगत, खोज योग्य, और अनुपालनयुक्त दस्तावेज़ीकरण बनाए रख सकते हैं।

**अगले कदम**
- GroupDocs.Metadata द्वारा समर्थित अन्य फ़ाइल फ़ॉर्मेट्स (PDF, DOCX, आदि) के साथ प्रयोग करें।  
- कोड को CI/CD पाइपलाइन में इंटीग्रेट करें ताकि हर बिल्ड पर मेटाडेटा मानकों को लागू किया जा सके।  

इसे आज़माने के लिए तैयार हैं? [GroupDocs.Metadata for Java रिलीज़](https://releases.groupdocs.com/metadata/java/) पर जाएँ और आज ही अपनी मेटाडेटा ऑटोमेशन लागू करना शुरू करें।

---

**अंतिम अपडेट:** 2026-06-17  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12  
**लेखक:** GroupDocs  

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं इस दृष्टिकोण को VSDX जैसे अन्य डायग्राम फ़ॉर्मेट्स के साथ उपयोग कर सकता हूँ?**  
A: हाँ, वही API GroupDocs.Metadata द्वारा समर्थित सभी डायग्राम फ़ॉर्मेट्स के लिए काम करता है।

**Q: क्या विकास बिल्ड्स के लिए मुझे लाइसेंस चाहिए?**  
A: विकास और परीक्षण के लिए फ्री ट्रायल पर्याप्त है; प्रोडक्शन डिप्लॉयमेंट्स के लिए पूर्ण लाइसेंस आवश्यक है।

**Q: मैं एक कॉल में कई प्रॉपर्टीज़ को कैसे अपडेट कर सकता हूँ?**  
A: `metadata.save(...)` को कॉल करने से पहले `DocumentProperties` ऑब्जेक्ट पर प्रत्येक प्रॉपर्टी सेट करें; लाइब्रेरी उन्हें एक साथ लिखती है।

**Q: क्या मूल फ़ाइल को ओवरराइट करना सुरक्षित है?**  
A: यह सलाह दी जाती है कि नई फ़ाइल में सहेजें (जैसा दिखाया गया है) और अपडेट सफल होने की पुष्टि के बाद ही मूल को बदलें।

**Q: यदि मुझे वर्तमान समय के बजाय कस्टम निर्माण तिथि सेट करनी हो तो क्या करें?**  
A: इच्छित टाइमस्टैम्प के साथ एक `java.util.Date` (या `java.time` इंस्टेंस) बनाएं और उसे `setTimeCreated` को पास करें।

## संबंधित ट्यूटोरियल्स

- [डायग्राम मेटाडेटा जावा को GroupDocs.Metadata के साथ अपडेट कैसे करें](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [GroupDocs.Metadata फ़ॉर जावा के साथ DXF ऑथर मेटाडेटा अपडेट कैसे करें – एक पूर्ण गाइड](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [डेट द्वारा जावा मेटाडेटा अपडेट को स्वचालित करें GroupDocs.Metadata के साथ – प्रभावी फ़ाइल प्रबंधन के लिए](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)