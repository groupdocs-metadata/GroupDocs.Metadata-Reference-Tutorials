---
date: '2026-06-12'
description: GroupDocs.Metadata for Java kullanarak özel XMP paketleri oluşturmayı,
  dosya meta verilerini yönetmeyi ve PDF'lere özel meta veri eklemeyi öğrenin.
keywords:
- create custom xmp package
- manage file metadata
- add custom metadata pdf
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  headline: Create Custom XMP Package with GroupDocs.Metadata for Java
  type: TechArticle
- description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  name: Create Custom XMP Package with GroupDocs.Metadata for Java
  steps:
  - name: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
    text: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
  - name: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
    text: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
  - name: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
    text: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
  type: HowTo
- questions:
  - answer: Over 50 formats—including JPEG, PNG, PDF, DOCX, and TIFF—support XMP packet
      injection. See the full list in the [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).
    question: What file formats support custom XMP packages?
  - answer: Yes, the library lets you read, modify, and delete any XMP property using
      the `IXmp` interface.
    question: Can I edit existing XMP metadata with GroupDocs.Metadata?
  - answer: For unsupported formats, consider wrapping the file in a container that
      does support XMP (e.g., converting to PDF) or using an alternative metadata
      store.
    question: How do I handle files that don’t natively support XMP?
  - answer: Absolutely—GroupDocs.Metadata is tested against Java 8 through Java 21,
      including all LTS releases.
    question: Is the library compatible with Java 17 LTS?
  - answer: Common pitfalls include using an incorrect namespace URI, exceeding the
      maximum packet size (≈ 2 MB), or attempting to write to a read‑only file. Ensure
      proper permissions and validate your XML schema before saving.
    question: What are typical errors when adding XMP packages?
  type: FAQPage
title: GroupDocs.Metadata for Java ile Özel XMP Paketi Oluşturun
type: docs
url: /tr/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata for Java ile Özel XMP Paketi Oluşturma

Modern dijital iş akışlarında, **özel XMP paketleri oluşturma** dosyalar içinde zengin, aranabilir meta verileri gömmek için gereklidir. Görseller, PDF'ler veya multimedya varlıklarıyla çalışıyor olun, GroupDocs.Metadata for Java, **dosya meta verilerini yönetme** ve **PDF'lere özel meta veri ekleme** için dış veri tabanlarına ihtiyaç duymadan güvenilir bir yol sunar. Bu öğreticide, kütüphaneyi kurmaktan tam özellikli bir XMP paketini gömmeye kadar tüm süreci adım adım göstereceğiz—böylece belgelerinizi bugün zenginleştirmeye başlayabilirsiniz.

## Hızlı Yanıtlar
- **İlk adım nedir?** GroupDocs.Metadata'i Maven bağımlılığı olarak ekleyin veya JAR'ı indirin.  
- **Kaç satır kod?** Özel bir XMP paketi oluşturmak ve eklemek için yalnızca üç kısa ifade yeterlidir.  
- **Hangi dosya formatları destekleniyor?** JPEG, PNG, PDF, DOCX ve TIFF dahil olmak üzere 50'den fazla format.  
- **Lisans gerekir mi?** Geliştirme için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Bunu Java 11+ ile kullanabilir miyim?** Evet, kütüphane Java 8'den Java 21'e kadar uyumludur.

## “özel xmp paketi oluşturma” nedir?
*Özel bir XMP paketi oluşturma*, kullanıcı tanımlı meta veri alanlarını içeren bir XMP paketi oluşturmak ve bunu desteklenen bir dosyaya gömmek anlamına gelir. Bu paket, dosyanın XMP bölümünde saklanır ve meta verileri taşınabilir ve XMP‑bilgili herhangi bir uygulama tarafından aranabilir hâle getirir.

## Dosya meta verilerini yönetmek için GroupDocs.Metadata for Java neden kullanılmalı?
GroupDocs.Metadata **50+ giriş ve çıkış formatını** destekler ve **2 GB**'a kadar dosyaları tüm belgeyi belleğe yüklemeden işleyebilir, bu da büyük varlıklarda RAM tüketimini **%80**'e kadar azaltır. API ayrıca iş parçacığı‑güvenli işlemler sunar, kurumsal ortamlarda yüksek verimli toplu işleme olanak tanır.

## Önkoşullar
- **Java Development Kit** 8 veya daha yeni (Java 11+ önerilir).  
- **IntelliJ IDEA** veya **Eclipse** gibi bir IDE.  
- Bağımlılık yönetimi için Maven kurulmuş.  
- Java sınıfları ve meta veri kavramları hakkında temel anlayış.

## GroupDocs.Metadata for Java Kurulumu
### Maven Kurulumu
GroupDocs.Metadata'i eklemek için `pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin:

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

Tam metod imzaları için [API Documentation](https://reference.groupdocs.com/metadata/java/) sayfasına bakın.  
Ayrıntılı API referansı için [GroupDocs.Metadata Java Docs](https://docs.groupdocs.com/metadata/java/) sayfasına bakın.

**Direct Download** – Manuel kurulum tercih ediyorsanız, en son JAR'ı [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) adresinden edinin. Değişiklik günlüğü detayları için [Latest Releases](https://releases.groupdocs.com/metadata/java/) sayfasını da görüntüleyebilirsiniz.

### Lisans Edinme
- **Free Trial** – Tüm özellikleri ücretsiz olarak değerlendirin.  
- **Temporary License** – Geliştirme testi için zaman sınırlı bir anahtar alın. ([Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/))  
- **Purchase** – Üretim kullanımı için kalıcı bir lisans edinin.

Kaynak kod ve örnekler [GroupDocs Metadata on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) adresinde mevcuttur.

## Uygulama Kılavuzu
Aşağıda, **özel bir XMP paketi oluşturma** ve bir dosyaya gömme işlemini adım adım gösteren bir rehber bulunmaktadır.

### Özel bir XMP paketi nasıl oluşturulur ve bir dosyaya eklenir?
`Metadata` sınıfı ile hedef dosyanızı yükleyin, bir `XmpPacketWrapper` oluşturun, özel XMP alanlarınızı tanımlayın ve son olarak değişiklikleri kaydedin. Bu uçtan uca akış, başlatmadan sonra yalnızca üç metod çağrısı gerektirir. İşlem, XMP paketinin doğru şekilde gömülmesini ve dosyanın tüm desteklenen uygulamalarda tam işlevsel kalmasını sağlar.

### Metadata Nesnesini Başlatma
`Metadata`, bir dosyayı temsil eden ve meta verilerini okuma ve yazma metodlarını sağlayan temel sınıftır.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### Yeni Bir XmpPacketWrapper Oluşturma
`XmpPacketWrapper`, bir veya daha fazla XMP paketini tutan bir kapsayıcı görevi görür ve kaydetmeden önce toplu güncellemeler yapılmasına olanak tanır.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### Özel XMP Paketi Tanımlama ve Yapılandırma
`IXmp` arayüzü, özel XMP şemaları tanımlamanıza ve paket içinde özellik değerlerini ayarlamanıza olanak tanır.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### Güncellenmiş Meta Veriyi Kaydetme
`Metadata.save()` değiştirilmiş meta verileri orijinal dosyaya yazar ve eklenen XMP paketlerini kalıcı hâle getirir.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### Ana Bileşenlerin Açıklaması
- **Metadata Object** – Dosyanın meta verilerine erişim için merkezi bir hub.  
- **IXmp Interface** – XMP‑özel alanları okuma/yazma metodları sağlar.  
- **XmpPacketWrapper** – Bir veya daha fazla XMP paketini tutar, toplu güncellemeyi mümkün kılar.  
- **Custom XMP Package** – Ek bilgi depolayan kullanıcı tanımlı şemanız.

## Yaygın Sorunlar ve Çözümler
- **Unsupported File Format** – Hedef dosya tipinin resmi format listesinde (50'den fazla desteklenen format) yer aldığını doğrulayın.  
- **License Not Found** – Lisans dosyasının uygulamanın kök dizinine yerleştirildiğinden veya `License.setLicense("license_path")` ile ayarlandığından emin olun.  
- **Memory Exhaustion on Large Files** – Meta verileri tembel (lazy) işlemek ve bellek kullanımını düşük tutmak için `metadata.setLoadOptions(LoadOptions.lazyLoad())` kullanın.

Ek yardım için [GroupDocs Support](https://forum.groupdocs.com/c/metadata/) forumunu ziyaret edin.

## Pratik Uygulamalar
1. **Digital Asset Management** – Lisanslama ve kullanım haklarını doğrudan görsellere ve PDF'lere gömün.  
2. **Content Personalization** – Hedefli dağıtım için belgelere kullanıcı‑özel tanımlayıcılar ekleyin.  
3. **Regulatory Compliance** – Denetim izlerini ve saklama politikalarını dosyanın içinde tutarak yönetişim denetimlerini basitleştirin.

## Performans Düşünceleri
- **Resource Optimization** – **1 GB**'den büyük dosyalar için RAM kullanımını **100 MB**'nin altında tutmak amacıyla meta verileri akış (streaming) modunda işleyin.  
- **Version Updates** – Kütüphaneyi güncel tutun; her büyük sürüm yeni formatları destekler ve işleme hızını **%30**'a kadar artırır.

## Sonuç
Bu kılavuzu izleyerek, GroupDocs.Metadata for Java ile **özel XMP paketleri oluşturmayı** öğrendiniz; bu sayede **dosya meta verilerini** verimli bir şekilde **yönetebilir** ve **PDF'lere ve diğer birçok formata özel meta veri ekleyebilirsiniz**. Ek XMP şemalarıyla denemeler yapın, iş akışını CI boru hattınıza entegre edin veya uçtan uca belge işleme için GroupDocs.Viewer ile birleştirin.

## Sıkça Sorulan Sorular

**S: Özel XMP paketlerini hangi dosya formatları destekler?**  
C: JPEG, PNG, PDF, DOCX ve TIFF dahil olmak üzere 50'den fazla format XMP paket enjeksiyonunu destekler. Tam listeyi [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/) içinde görebilirsiniz.

**S: Mevcut XMP meta verilerini GroupDocs.Metadata ile düzenleyebilir miyim?**  
C: Evet, kütüphane `IXmp` arayüzünü kullanarak herhangi bir XMP özelliğini okuyabilir, değiştirebilir ve silebilir.

**S: XMP'yi yerel olarak desteklemeyen dosyalarla nasıl başa çıkabilirim?**  
C: Desteklenmeyen formatlar için dosyayı XMP destekleyen bir kapsayıcıya (ör. PDF'ye dönüştürmek) sarmayı veya alternatif bir meta veri deposu kullanmayı düşünün.

**S: Kütüphane Java 17 LTS ile uyumlu mu?**  
C: Kesinlikle—GroupDocs.Metadata, Java 8'den Java 21'e kadar, tüm LTS sürümleri dahil olmak üzere test edilmiştir.

**S: XMP paketleri eklerken tipik hatalar nelerdir?**  
C: Yaygın hatalar arasında hatalı bir ad alanı URI'si kullanmak, maksimum paket boyutunu (≈ 2 MB) aşmak veya salt‑okunur bir dosyaya yazmaya çalışmak bulunur. Doğru izinleri sağladığınızdan ve kaydetmeden önce XML şemanızı doğruladığınızdan emin olun.

---

**Son Güncelleme:** 2026-06-12  
**Test Edilen Versiyon:** GroupDocs.Metadata 23.12 for Java  
**Yazar:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with operations on metadata
}
```

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Get the root XMP package from the metadata
    IXmp root = (IXmp) metadata.getRootPackage();
```

```java
import com.groupdocs.metadata.core.XmpPacketWrapper;

// Create a new XmpPacketWrapper to hold custom packages
XmpPacketWrapper packet = new XmpPacketWrapper();
```

```java
import com.groupdocs.metadata.core.XmpPackage;
import com.groupdocs.metadata.core.XmpArray;
import com.groupdocs.metadata.core.XmpArrayType;

// Define and configure the custom XMP package
custom = new XmpPackage("gd", "GroupDocs Custom Package");
custom.set("CustomProperty", "CustomValue");

// Add it to the packet
packet.addPackage(custom);
```

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```

## İlgili Öğreticiler

- [GroupDocs.Metadata Java ile Dosyalara Özel XMP Meta Verisi Ekleme: Kapsamlı Rehber](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [GroupDocs.Metadata for Java ile PDF'ye Meta Veri Ekleme – Geliştirici Rehberi](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [GroupDocs.Metadata ile Java'da PDF'lerden Özel Meta Veri Çıkarma: Kapsamlı Rehber](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)