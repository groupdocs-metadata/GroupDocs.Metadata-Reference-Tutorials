---
date: '2026-08-10'
description: Java için GroupDocs.Metadata kullanarak PSD dosyalarından EXIF meta verilerini
  nasıl çıkaracağınızı öğrenin. Bu rehber temel çıkarma, IFD paketleri, GPS verileri
  ve gerçek dünya kullanım örneklerini kapsar.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Java için GroupDocs.Metadata kullanarak PSD dosyalarından EXIF meta
  verilerini nasıl çıkaracağınızı öğrenin. Adım adım rehber, kod parçacıkları ve geliştiriciler
  için sorun giderme ipuçları.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: GroupDocs.Metadata ile PSD dosyalarından EXIF meta verilerini nasıl çıkarabilirsiniz
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: GroupDocs.Metadata ile PSD dosyalarından EXIF meta verilerini nasıl çıkarabilirsiniz
type: docs
url: /tr/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata ile PSD dosyalarından EXIF meta verilerini çıkarmak

Extracting **EXIF metadata** from PSD files is a routine but powerful step when you need to audit image provenance, automate asset tagging, or build searchable media libraries. In this tutorial you’ll discover **how to extract EXIF** quickly with GroupDocs.Metadata for Java, see the exact API calls, and learn how to handle advanced IFD packages and GPS coordinates. By the end you’ll be ready to integrate metadata extraction into any Java‑based workflow.

## Hızlı cevaplar
The `Metadata` class represents a file and provides access to its metadata.

- **Kodun ilk satırı nedir?** `Metadata metadata = new Metadata("sample.psd");`
- **Hangi metod sanatçı adını döndürür?** `metadata.getExif().getArtist();`
- **GPS verilerini okuyabilir miyim?** Evet – `metadata.getExif().getGpsInfo();` kullanın
- **Üretim için lisansa ihtiyacım var mı?** Deneme süresinin ardından geçerli bir GroupDocs.Metadata lisansı gereklidir.
- **Desteklenen Java sürümü?** Java 8 ve üzeri (Java 21'e kadar).

## EXIF meta verileri nedir?
EXIF (Exchangeable Image File Format) meta verileri, kamera ayarlarını, oluşturma zaman damgalarını ve konum verilerini görüntü dosyalarının içinde depolar. GroupDocs.Metadata, bu bilgileri PSD dosyalarının ikili yapısından doğrudan okur ve temiz bir Java API'si aracılığıyla sunar. Geliştiricilerin kamera modeli, poz süresi ve GPS koordinatları gibi ayrıntıları manuel inceleme yapmadan programlı olarak almasını sağlar.

## Java için GroupDocs.Metadata neden kullanılmalı?
GroupDocs.Metadata **30+ dosya formatını** (PSD, JPEG, PNG, TIFF dahil) destekler ve belgeyi belleğe tamamen yüklemeden **2 GB**'a kadar dosyaları işleyebilir. Kütüphane **150'den fazla ayrı EXIF etiketi** çıkarır ve analiz veya uyumluluk için gereken kamera ve GPS özelliklerinin tam setine sahip olmanızı garanti eder.

## Önkoşullar
- **Java Development Kit (JDK) 8** veya daha yeni bir sürüm makinenizde kurulu olmalıdır.  
- **Maven** bağımlılık yönetimi için.  
- **GroupDocs.Metadata for Java sürüm 24.12** (veya daha yeni).  
- Java sınıfları, nesneleri ve istisna yönetimi konusunda temel bilgi.

### Gerekli kütüphaneler ve bağımlılıklar
| Bağımlılık | Maven koordinatları |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Ortam kurulumu
IntelliJ IDEA veya Eclipse gibi Maven uyumlu bir IDE'niz olmalıdır. Yeni bir Maven projesi oluşturun veya bağımlılığı mevcut bir projeye ekleyin.

## Java için GroupDocs.Metadata nasıl kurululur
GroupDocs.Metadata, birkaç yapılandırma satırıyla bir Maven projesine eklenebilir. Aşağıdaki adımlar, depoyu ve bağımlılığı nasıl ekleyeceğinizi gösterir, böylece kütüphane sınıf yolunda bulunur.

### Maven kurulumu
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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

### Doğrudan indirme
Alternatif olarak, resmi sürüm sayfasından en son JAR'ı indirin: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Lisans edinme
To run the library beyond the 30‑day trial, obtain a temporary or full license:

1. [Lisans Satın Alma Sayfasını](https://purchase.groupdocs.com/temporary-license) ziyaret edin.  
2. Test için **temporary** (geçici), üretim için **full** (tam) seçin.  
3. Ekrandaki talimatları izleyerek lisans dosyasını (`metadata.lic`) Java sınıf yolunuza yerleştirin.

### Temel başlatma ve kurulum
After the library is on the classpath, initialize it as shown below:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## PSD görüntüsünden temel EXIF meta veri özelliklerini nasıl çıkarılır
Bu bölüm, bir PSD dosyasını nasıl yükleyeceğinizi, EXIF konteynerine nasıl erişeceğinizi ve **artist**, **copyright**, **software** gibi en yaygın etiketleri nasıl okuyacağınızı açıklar. İşlem, bir `Metadata` örneği oluşturmayı, `getExif()` çağırmayı ve ardından basit getter metodlarıyla bireysel özellikleri almayı içerir.

### Adım adım uygulama
1. **PSD dosyanıza işaret eden bir `Metadata` örneği oluşturun.**  
2. **EXIF konteynerini elde etmek için `getExif()` çağırın.**  
3. **`getArtist()`, `getCopyright()` ve `getSoftware()` gibi bireysel özellikleri okuyun.**  
4. **Uygulama mantığınıza göre değerleri yazdırın veya saklayın.**  

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **İpucu:** `Metadata` nesnesi dosya formatını otomatik olarak algılar, bu yüzden aynı kodu JPEG veya TIFF dosyaları için değişiklik yapmadan yeniden kullanabilirsiniz.

## PSD görüntüsünden EXIF IFD paket özelliklerini nasıl çıkarılır
IFD (Image File Directory) bölümü, **kamera seri numarası**, **lens modeli** ve **kullanıcı yorumları** gibi daha derin teknik detayları içerir. `Ifd0`, temel kamera bilgilerini içeren birincil Image File Directory'yi temsil eder. Bu alanların çıkarılması adli analiz veya yüksek hassasiyetli kataloglama için faydalıdır.

### Uygulama adımları
1. **Önceki bölümdeki `Metadata` örneğini yeniden kullanın.**  
2. **`metadata.getExif().getIfd0()` aracılığıyla IFD konteynerine gidin.**  
3. **`getBodySerialNumber()` ve `getUserComment()` gibi özellikleri okuyun.**  
4. **Verileri çıktıya verin** veya alan modelinize eşleyin.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## PSD dosyasından GPS verilerini (enlem, boylam) nasıl alırsınız
Birçok modern kamera, EXIF bloğuna GPS koordinatlarını gömer. `GpsInfo`, EXIF verilerinden çıkarılan coğrafi koordinatları tutar. `metadata.getExif().getGpsInfo()` çağırın ve ardından `getLatitude()`, `getLongitude()` ve `getAltitude()` kullanarak kesin konum verilerini elde edin—ek bir ayrıştırma gerekmez.

### Ayrıntılı adımlar
1. **GPS bilgi nesnesini alın**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Enlem ve boylamı okuyun**: `gps.getLatitude()` ondalık derece cinsinden bir `double` döndürür.  
3. **Eksik verileri ele alın**: Etiket yoksa API `null` döndürür, bu yüzden `NullPointerException`'a karşı önlem alın.  

> **Yaygın tuzak:** Bazı PSD dosyaları GPS koordinatlarını rasyonel sayılar olarak saklar; kütüphane bunları otomatik olarak normalleştirir, ancak eski dosyalar manuel dönüşüm gerektirebilir.

## Yaygın sorunlar ve sorun giderme
| Semptom | Muhtemel neden | Çözüm |
|---------|----------------|-------|
| `Unsupported format` istisnası | PSD'yi tanımayan eski bir GroupDocs.Metadata sürümü kullanmak | Sürümü 24.12 veya daha yenisine yükseltin |
| `NullPointerException` `getArtist()` çağrıldığında | Kaynak dosyada EXIF etiketi bulunmuyor | Okumadan önce `metadata.getExif().hasArtist()` kontrol edin |
| 30 gün sonra lisans hatası | Lisans dosyası sınıf yolunda bulunamadı | `metadata.lic` dosyasını `src/main/resources` içine koyun veya `Metadata.setLicense("path/to/license")` ayarlayın |

## Sıkça sorulan sorular

**S: Parola korumalı bir PSD dosyasından EXIF meta verilerini çıkarabilir miyim?**  
C: Evet. Dosyayı `new Metadata("file.psd", "password")` ile yükleyin ve ardından EXIF verilerine normal şekilde erişin.

**S: GroupDocs.Metadata birçok PSD dosyasının toplu işlenmesini destekliyor mu?**  
C: Kesinlikle. Bir döngü içinde `Metadata` nesnesi oluşturun veya dizinleri verimli işlemek için `MetadataCollection` yardımcı sınıfını kullanın.

**S: Resmi olarak hangi Java sürümleri destekleniyor?**  
C: Java 8'den Java 21'e kadar tam test edilmiştir. Kütüphane yalnızca standart API'leri kullanır, bu yüzden uyumlu herhangi bir JVM'de çalışır.

**S: EXIF verilerini bir PSD dosyasına geri yazmak mümkün mü?**  
C: Evet. `Exif` nesnesi üzerinden özellikleri değiştirdikten sonra `metadata.save("output.psd")` çağırarak değişiklikleri kalıcı hale getirin.

**S: Kütüphane bellek tükenmeden ne kadar büyük bir PSD dosyasını işleyebilir?**  
C: GroupDocs.Metadata verileri akış olarak işler ve tipik 8 GB RAM bir makinede **2 GB**'a kadar dosyaları işleyebilir, düşük bellek mimarisi sayesinde.

## Sonuç
Artık GroupDocs.Metadata for Java kullanarak PSD dosyalarından **EXIF meta verilerini nasıl çıkaracağınızı** biliyorsunuz; temel etiketlerden gelişmiş IFD ve GPS bilgilerine kadar. Bu kod parçacıklarını görüntü işleme hattınıza entegre ederek kataloglamayı, uyumluluk kontrollerini veya konuma dayalı hizmetleri otomatikleştirin. Daha derin bir keşif için, diğer desteklenen formatlardan (JPEG, TIFF, PNG) meta veri çıkarmayı deneyin veya özel etiketler eklemek için yazma yetenekleriyle deney yapın.

---

**Son Güncelleme:** 2026-08-10  
**Test Edilen:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [Java'da GroupDocs.Metadata Kullanarak PSD Dosyalarından Görüntü Kaynaklarını Çıkarmak: Kapsamlı Kılavuz](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Java için GroupDocs.Metadata Kullanarak PSD Başlık ve Katman Bilgilerini Çıkarmak: Kapsamlı Kılavuz](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Java'da GroupDocs.Metadata Kullanarak MakerNote Özelliklerini TIFF/EXIF Etiketleri Olarak Çıkarmak](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)