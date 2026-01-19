---
date: '2026-01-19'
description: GroupDocs.Metadata का उपयोग करके जावा में डायग्राम फ़ाइलों के निर्माण
  समय को बदलना और मेटाडेटा अपडेट को स्वचालित करना सीखें।
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: GroupDocs Java का उपयोग करके डायग्राम मेटाडाटा में निर्माण समय बदलें
type: docs
url: /hi/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Change Creation Time in Diagram Metadata Using GroupDocs Java

डायग्राम मेटाडेटा में निर्माण समय बदलें GroupDocs Java का उपयोग करके

Updating metadata properties such as creator, **change creation time**, and category manually can be tedious. Automate this process with the GroupDocs.Metadata library for Java, and you’ll be able to **change creation time** and other built‑in properties in a single, repeatable step. This guide walks you through setting up the library, updating diagram metadata, and applying best‑practice performance tips so you can keep your documents consistent and searchable.

## त्वरित उत्तर
- **What is the primary goal?** डायग्राम फ़ाइलों में निर्माण समय और अन्य मेटाडेटा बदलना।  
- **Which library should I use?** GroupDocs.Metadata for Java.  
- **Do I need a license?** परीक्षण के लिए फ्री ट्रायल काम करता है; प्रोडक्शन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **Can I batch‑process many diagrams?** हाँ—लूप या पैरालल स्ट्रीम के अंदर वही तरीका उपयोग करें।  
- **What Java version is required?** JDK 8 या उससे ऊपर।

## डायग्राम मेटाडेटा में “change creation time” क्या है?
क्रिएशन टाइम बदलना मतलब डायग्राम फ़ाइल (जैसे VDX, VSDX) के अंदर संग्रहीत मूल टाइमस्टैम्प को नई तिथि से ओवरराइट करना है। यह तब उपयोगी होता है जब आपको फ़ाइल की मेटाडेटा वास्तविक प्रोसेसिंग तिथि को दर्शाना हो, न कि मूल लेखन तिथि को।

## डायग्राम के लिए मेटाडेटा अपडेट को ऑटोमेट क्यों करें?
- **Consistency:** सुनिश्चित करता है कि हर फ़ाइल समान नामकरण और वर्गीकरण नियमों का पालन करे।  
- **Searchability:** अपडेटेड कीवर्ड और कैटेगरीज DMS समाधान में दस्तावेज़ खोज को बेहतर बनाते हैं।  
- **Compliance:** सटीक टाइमस्टैम्प सुनिश्चित करके ऑडिट आवश्यकताओं को पूरा करने में मदद करता है।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK) 8+** स्थापित हो।  
- **IDE** जैसे IntelliJ IDEA या Eclipse।  
- **Maven** (या मैन्युअल JAR हैंडलिंग) डिपेंडेंसी मैनेजमेंट के लिए।  
- जावा क्लासेज़, मेथड्स, और एक्सेप्शन हैंडलिंग का बुनियादी ज्ञान।

### आवश्यक लाइब्रेरीज़ और डिपेंडेंसिज़
`pom.xml` फ़ाइल में Maven उपयोग कर रहे हैं तो नीचे दिया गया रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

यदि आप सीधे डाउनलोड करना पसंद करते हैं, तो नवीनतम संस्करण प्राप्त करने के लिए [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) पर जाएँ।

### पर्यावरण सेटअप
- JDK 8 या नया।  
- IntelliJ IDEA, Eclipse, या कोई भी Java‑compatible IDE।

### ज्ञान पूर्वापेक्षाएँ
जावा सिंटैक्स और बुनियादी फ़ाइल I/O की समझ ट्यूटोरियल को सुगम बनाएगी, लेकिन चरणों को सरल भाषा में समझाया गया है।

## GroupDocs.Metadata for Java सेटअप करना
### इंस्टॉलेशन निर्देश
**Maven Users:** ऊपर दिया गया स्निपेट रिपॉज़िटरी और आवश्यक JAR को स्वचालित रूप से जोड़ता है।  
**Direct Download Users:** [GroupDocs](https://releases.groupdocs.com/metadata/java/) से JAR डाउनलोड करने के बाद, इसे अपने प्रोजेक्ट की क्लासपाथ में जोड़ें।

### लाइसेंस प्राप्त करना
- **Free Trial:** लाइब्रेरी को बिना लागत के एक्सप्लोर करें।  
- **Temporary License:** विस्तारित परीक्षण के लिए एक टेम्पररी लाइसेंस प्राप्त करें [here](https://purchase.groupdocs.com/temporary-license/)।  
- **Purchase:** प्रोडक्शन एनवायरनमेंट्स के लिए पूर्ण लाइसेंस प्राप्त करें।

### बेसिक इनिशियलाइज़ेशन
GroupDocs.Metadata का उपयोग शुरू करने के लिए, क्लास इम्पोर्ट करें और एक डायग्राम फ़ाइल खोलें:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

लाइब्रेरी इनिशियलाइज़ होने के बाद, आप अब किसी भी बिल्ट‑इन प्रॉपर्टी को बदल सकते हैं, जिसमें निर्माण समय भी शामिल है।

## इम्प्लीमेंटेशन गाइड
### डायग्राम फ़ाइलों में निर्माण समय कैसे बदलें
इस सेक्शन में हम प्रत्येक चरण को देखेंगे जो **change creation time** करने और अन्य सामान्य प्रॉपर्टीज़ जैसे author, company, और category को अपडेट करने के लिए आवश्यक हैं।

#### चरण 1: डायग्राम डॉक्यूमेंट लोड करें
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*व्याख्या:* `Metadata` कंस्ट्रक्टर आपके डायग्राम फ़ाइल का पाथ लेता है। `try‑with‑resources` ब्लॉक ऑपरेशन के बाद फ़ाइल को सही तरीके से बंद करता है।

#### चरण 2: रूट पैकेज एक्सेस करें
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*व्याख्या:* रूट पैकेज आपको डायग्राम के सभी बिल्ट‑इन मेटाडेटा फ़ील्ड्स तक सीधे पहुंच देता है।

#### चरण 3: क्रिएटर प्रॉपर्टी सेट करें
```java
root.getDocumentProperties().setCreator("test author");
```
*व्याख्या:* नया लेखक नाम असाइन करता है। `"test author"` को वास्तविक क्रिएटर से बदलें।

#### चरण 4: **Change Creation Time**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*व्याख्या:* यह लाइन **changes creation time** को वर्तमान सिस्टम तिथि और समय पर सेट करती है। यदि आपको कस्टम टाइमस्टैम्प चाहिए तो आप एक विशिष्ट `Date` इंस्टेंस भी पास कर सकते हैं।

#### चरण 5: कंपनी जानकारी परिभाषित करें
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*व्याख्या:* डायग्राम से जुड़ी कंपनी का नाम स्टोर करता है—एंटरप्राइज़ ट्रैकिंग के लिए उपयोगी।

#### चरण 6: डॉक्यूमेंट कैटेगरी सेट करें
```java
root.getDocumentProperties().setCategory("test category");
```
*व्याख्या:* फ़ाइल को वर्गीकृत करता है, जिससे आप अपने रिपॉज़िटरी में **update diagram category** को सुसंगत रूप से कर सकें।

#### चरण 7: कीवर्ड जोड़ें
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*व्याख्या:* कीवर्ड सर्चेबिलिटी को बढ़ाते हैं; आप डायग्राम की सामग्री से संबंधित कोई भी शब्द सूचीबद्ध कर सकते हैं।

#### चरण 8: बदलाव सेव करें
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*व्याख्या:* सभी बदलावों को नई फ़ाइल में सेव करता है, मूल फ़ाइल को अपरिवर्तित छोड़ता है।

### सामान्य समस्याएँ और ट्रबलशूटिंग
- **File Not Found:** इनपुट पाथ को सत्यापित करें और सुनिश्चित करें कि फ़ाइल एक्सटेंशन वास्तविक फॉर्मेट से मेल खाता हो।  
- **Access Denied:** इनपुट और आउटपुट दोनों डायरेक्टरीज़ के रीड/राइट परमिशन चेक करें।  
- **Invalid Date Format:** API के साथ संगत `java.util.Date` या `java.time` ऑब्जेक्ट्स का उपयोग करें।

## व्यावहारिक अनुप्रयोग
1. **Automating Document Archiving** – जब पुराने डायग्राम को आर्काइव में ले जा रहे हों, तो स्वचालित रूप से **change creation time** को आ समान कैटेगरी सेट करें।  
2. **Version Control Integration** – प्रत्येक रिलीज़ के दौरान निर्माण समय अपडेट करके टाइमस्टैम्प को Git कमिट्स के साथ सिंक रखें।  
3. **Enterprise DMS Standardization** – सभी डायग्राम एसेट्स में author, company, और keywords के लिए कंपनी‑व्यापी नीति लागू करें।

## प्रदर्शन संबंधी विचार
- **Batch Processing:** ऊपर दिए गए चरणों को लूप में रैप करें ताकि एक रन में दर्जनों फ़ाइलों को प्रोसेस किया जा सके।  
- **Memory Management:** प्रत्येक `Metadata` इंस्टेंस को तुरंत रिलीज़ करें (try‑with‑resources ब्लॉक यह स्वचालित करता है)।  
- **Asynchronous Execution:** बड़े बैच के लिए, `CompletableFuture` का उपयोग करके अपडेट्स को पैरलल चलाने पर विचार करें, जिससे मुख्य थ्रेड ब्लॉक न हो।

## निष्कर्ष
अब आप जानते हैं कि GroupDocs.Metadata in Java का उपयोग करके डायग्राम डॉक्यूमेंट्स के लिए **change creation time** और अन्य बिल्ट‑इन मेटाडेटा प्रॉपर्टीज़ को कैसे अपडेट करें। इन चरणों को ऑटोमेट करके, आप अपने संगठन में सुसंगत, सर्चेबल, और अनुपालनयुक्त दस्तावेज़ीकरण बनाए रख सकते हैं।

**अगले कदम**
- GroupDocs.Metadata द्वारा समर्थित अन्य फ़ाइल फ़ॉर्मेट्स (PDF, DOCX, आदि) के साथ प्रयोग करें।  
- कोड को CI/CD पाइपलाइन में इंटीग्रेट करें ताकि हर बिल्ड पर मेटाडेटा मानकों को लागू किया जा सके।

इसे आज़माने के लिए तैयार हैं? [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) पर जाएँ और आज ही अपनी मेटाडेटा ऑटोमेशन लागू करना शुरू करें।

---

**अंतिम अपडेट:** 2026-01-19  
**टेस्टेड विद:** GroupDocs.Metadata 24.12  
**लेखक:** GroupDocs  

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं इस दृष्टिकोण को VSDX जैसे अन्य डायग्राम फ़ॉर्मेट्स के साथ उपयोग कर सकता हूँ?**  
A: हाँ, वही API GroupDocs.Metadata द्वारा समर्थित सभी डायग्राम फ़ॉर्मेट्स के लिए काम करता है।

**Q: क्या विकास बिल्ड्स के लिए लाइसेंस चाहिए?**  
A: विकास और परीक्षण के लिए फ्री ट्रायल पर्याप्त है; प्रोडक्शन डिप्लॉयमेंट्स के लिए पूर्ण लाइसेंस आवश्यक है।

**Q: मैं एक कॉल में कई प्रॉपर्टीज़ को कैसे अपडेट करूँ?**  
A: `metadata.save(...)` कॉल करने से पहले `DocumentProperties` ऑब्जेक्ट पर प्रत्येक प्रॉपर्टी सेट करें; लाइब्रेरी उन्हें एक साथ लिख देती है।

**Q: क्या मूल फ़ाइल को ओवरराइट करना सुरक्षित है?**  
A: डेटा लॉस से बचने के लिए नई फ़ाइल में सेव करना (जैसा दिखाया गया है) अनुशंसित है, फिर आवश्यकता पड़ने पर मूल को बदलें।

**Q: यदि मुझे वर्तमान समय के बजाय कस्टम निर्माण तिथि सेट करनी हो तो क्या करें?**  
A: इच्छित टाइमस्टैम्प के साथ `java.util.Date` (या `java.time` इंस्टेंस) बनाएं और उसे `setTimeCreated` को पास करें।