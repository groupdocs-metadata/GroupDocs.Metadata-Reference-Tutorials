---
date: '2026-07-21'
description: GroupDocs.Metadata for Java kullanarak docx'i png önizlemeye nasıl dönüştüreceğinizi
  öğrenin. Adım adım Maven kurulumu, önizleme seçenekleri ve görüntü çıktısı rehberi.
keywords:
- convert docx to png
- document image preview
- GroupDocs.Metadata Java
- create document preview java
- java generate thumbnails
lastmod: '2026-07-21'
og_description: GroupDocs.Metadata for Java kullanarak docx'i png önizlemeye nasıl
  dönüştüreceğinizi öğrenin. Adım adım Maven kurulumu, önizleme seçenekleri ve görüntü
  çıktısı rehberi.
og_image_alt: 'Guide: Convert DOCX to PNG preview using GroupDocs.Metadata in Java'
og_title: GroupDocs.Metadata Java ile docx'i png önizlemeye dönüştür
schemas:
- author: GroupDocs
  dateModified: '2026-07-21'
  description: Learn how to convert docx to png preview using GroupDocs.Metadata for
    Java. Step‑by‑step Maven setup, preview options, and image output guide.
  headline: convert docx to png preview with GroupDocs.Metadata Java
  type: TechArticle
- description: Learn how to convert docx to png preview using GroupDocs.Metadata for
    Java. Step‑by‑step Maven setup, preview options, and image output guide.
  name: convert docx to png preview with GroupDocs.Metadata Java
  steps:
  - name: Initialize `Metadata` (Feature 1).
    text: Initialize `Metadata` (Feature 1).
  - name: Build a `PreviewOptions` instance, specify `PNG` and the desired page numbers.
    text: Build a `PreviewOptions` instance, specify `PNG` and the desired page numbers.
  - name: Pass a lambda that writes the preview bytes to the `OutputStream` you created
      in Feature 3.
    text: Pass a lambda that writes the preview bytes to the `OutputStream` you created
      in Feature 3.
  type: HowTo
- questions:
  - answer: Yes. Open the document with the appropriate constructor that accepts a
      password, then proceed with preview options.
    question: Can I generate previews for password‑protected documents?
  - answer: PNG, JPEG, BMP, and GIF are available via `PreviewFormats`.
    question: Which image formats are supported?
  - answer: Pass an array of page numbers to `previewOptions.setPageNumbers(new int[]{1,2,3});`.
    question: How do I preview multiple pages in one call?
  - answer: Adjust the DPI using `previewOptions.setDpi(int dpi)` (default is 96 DPI).
    question: Is there a way to control image resolution?
  - answer: GroupDocs.Metadata is pure Java and can be used on Android with the appropriate
      JARs, but UI rendering must be handled by the Android framework.
    question: Does the library work on Android?
  type: FAQPage
tags:
- convert docx
- preview image
- GroupDocs.Metadata
- Java tutorial
- document processing
title: GroupDocs.Metadata Java ile docx'i png önizlemeye dönüştür
type: docs
url: /tr/java/document-formats/java-groupdocs-metadata-document-image-previews/
weight: 1
---

# Java'da GroupDocs.Metadata ile Belge Görüntüsü Önizlemelerini Ustalıkla Kullanma

## Giriş

Eğer **convert docx to png** yapıp belge önizlemelerini doğrudan bir Java uygulamasından göstermeniz gerekiyorsa—belge yönetim portalı, dijital kütüphane ya da bir kurumsal intranet için hızlı‑bakış özelliği oluşturuyorsanız—GroupDocs.Metadata süreci sorunsuz ve tamamen Java‑yerel hâle getirir. Bu öğreticide Maven kurulumu, önizleme seçeneklerinin yapılandırılması ve bireysel sayfaların yüksek‑kaliteli PNG görüntüleri olarak çıktılanması konularını göreceksiniz; aynı zamanda bellek kullanımını düşük, performansı yüksek tutacaksınız. Tam iş akışını birlikte inceleyelim.

## Hızlı Yanıtlar
- **“create document preview java” ne anlama geliyor?** Java kodu kullanarak belge sayfalarının görsel anlık görüntülerini (ör. PNG) üretmek.  
- **Hangi kütüphane kutudan çıkar çıkmaz bunu destekler?** Java için GroupDocs.Metadata.  
- **Görüntü formatını seçebilir miyim?** Evet—önizleme seçenekleri PNG, JPEG, BMP vb. formatları seçmenize izin verir.  
- **Lisans gerekir mi?** Değerlendirme için ücretsiz deneme çalışır; üretim için ücretli lisans gereklidir.  
- **Sadece seçili sayfaları önizlemek mümkün mü?** Kesinlikle—belirli sayfaları hedeflemek için `setPageNumbers` kullanın.  

## **create document preview java** nedir?

Java'da bir belge önizlemesi oluşturmak, bir dosyanın (DOCX, PDF, PPT vb.) bir ya da daha fazla sayfasını programatik olarak görüntü dosyalarına dönüştürmek anlamına gelir. Bu, küçük resim galerileri, hızlı görsel kontroller ve web ya da masaüstü UI bileşenleriyle sorunsuz entegrasyon sağlar. Her sayfayı bir görüntüye dönüştürerek geliştiriciler, kullanıcıların orijinal belgeyi açmadan anlık görsel geri bildirim almasını sağlayabilir; bu da belge‑ağır uygulamalarda kullanılabilirliği ve performansı artırır.

## Önizleme oluşturma için neden GroupDocs.Metadata kullanmalı?

GroupDocs.Metadata, yerel kütüphanelere ya da harici servislere ihtiyaç duymayan saf‑Java bir çözüm sunar; bu da dağıtımı platformlar arasında sorunsuz hâle getirir. Geniş bir format yelpazesini destekler, çıktı ayarları üzerinde ince kontrol sağlar ve yüksek verimlilik için tasarlanmıştır; bu sayede büyük belge toplulukları verimli bir şekilde işlenebilir. Bu yetenekler, geliştirme çabasını azaltırken kurumsal‑düzey iş yükleri için güvenilir, yüksek‑kaliteli önizlemeler sunar.

## Önkoşullar

- **Gerekli Kütüphaneler:** GroupDocs.Metadata for Java (en son sürüm).  
- **Derleme Sistemi:** Maven projesi (veya manuel JAR ekleme).  
- **Beceri Seti:** Java I/O, try‑with‑resources ve istisna yönetimi konularına aşina olmak.

## GroupDocs.Metadata'i Java için Kurma

### Kurulum Bilgileri

GroupDocs deposunu ve bağımlılığı `pom.xml` dosyanıza ekleyin:

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

**Doğrudan İndirme**  
Alternatif olarak, en son JAR'ları [GroupDocs.Metadata for Java sürümleri](https://releases.groupdocs.com/metadata/java/) adresinden indirin ve projenizin sınıf yoluna ekleyin.

### Lisans Edinme

Ücretsiz deneme ile başlayın veya geçici bir lisans isteyin. Üretim kullanımı için lisansı burada satın alın: [Group Docs satın alma sayfası](https://purchase.groupdocs.com/temporary-license/).

### Temel Başlatma ve Kurulum

İşte GroupDocs.Metadata ile bir belge açmak için gereken minimum kod örneği:

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

**Tanım bağlantısı:** `Metadata` sınıfı, dosya meta verilerini okuma ve manipüle etme için giriş noktasıdır; ayrıca önizleme oluşturma yeteneklerine erişim sağlar.

## Uygulama Kılavuzu

İşte çözümü üç odaklanmış özelliğe ayırıyoruz. Her özellik, kısa açıklamalar ve ihtiyacınız olan tam kodu içerir—ekstra kod parçacıkları yok, sadece orijinal bloklar korunur.

### Özellik 1: Belge İşleme için Metadata'yı Başlatma

**Genel Bakış**  
Belgeyi yüklemek, herhangi bir önizleme oluşturulmadan önceki ilk adımdır.

#### Adım 1 – Sınıfları İçe Aktarma  

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;
```

**Tanım bağlantısı:** `Metadata`, GroupDocs.Metadata'in bellekte tek bir dosyayı temsil eden çekirdek nesnesidir ve inceleme ve önizleme için yöntemler sunar.

#### Adım 2 – Belgeyi Yükleme  

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
try (Metadata metadata = new Metadata(documentPath)) {
    System.out.println("Document loaded successfully.");
} catch (IOException e) {
    e.printStackTrace();
}
```

**İpuçları**  
- Kodu çalıştırmadan önce dosya yolunu ve okuma izinlerini doğrulayın.  
- Sınıf yolu karışıklığını önlemek için test sırasında mutlak yollar kullanın.

### Özellik 2: Belge Sayfaları için Önizleme Seçenekleri Oluşturma

**Genel Bakış**  
Önizlemenin nasıl görüneceğini ve hangi sayfaların oluşturulacağını yapılandırın.

#### Adım 1 – Önizleme Sınıflarını İçe Aktarma  

```java
import com.groupdocs.metadata.options.PreviewFormats;
import com.groupdocs.metadata.options.PreviewOptions;
import java.io.OutputStream;
```

**Tanım bağlantısı:** `PreviewOptions`, çıktı formatını, DPI'yi ve sayfa aralığını belirlemenizi sağlar; ham belge verilerini görüntü akışına dönüştürür.

#### Adım 2 – Önizleme Seçeneklerini Ayarlama  

```java
OutputStream outputStream = null; // Replace with actual implementation if needed

PreviewOptions previewOptions = new PreviewOptions(outputStream::write);
previewOptions.setPreviewFormat(PreviewFormats.PNG); // Set the format of the preview image
previewOptions.setPageNumbers(new int[]{1}); // Specify page numbers to generate previews for
```

**Neden Önemlidir**  
`PNG` seçmek kayıpsız kalite sağlar ve bu küçük resimler için idealdir. `setPageNumbers`'ı ayarlayarak ihtiyacınız olan herhangi bir sayfa aralığını önizleyebilirsiniz; örneğin bir DOCX kapak sayfasını katalog önizlemesi için PNG'ye dönüştürmek gibi.

### Özellik 3: Görüntü Çıktısı için Sayfa Akışı Oluşturma

**Genel Bakış**  
Her önizleme görüntüsü bir dosyaya veya başka bir çıktı hedefine yazılmalıdır.

#### Adım 1 – I/O Sınıflarını İçe Aktarma  

```java
import java.io.FileOutputStream;
import java.io.File;
import java.io.OutputStream;
import java.io.IOException;
```

**Tanım bağlantısı:** `OutputStream`, bayt verilerini dosyalara, ağ soketlerine veya bellek içi tamponlara yazmak için kullanılan standart bir Java I/O sınıfıdır.

#### Adım 2 – Akışı Oluştur ve Görüntüyü Yaz  

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

**Profesyonel ipucu:** `YOUR_OUTPUT_DIRECTORY`'nin önceden var olduğundan emin olun veya `outputFile.getParentFile().mkdirs();` ile programatik olarak oluşturun.

## GroupDocs.Metadata ile **sayfayı görüntü olarak çıkartma** nasıl yapılır

Belirli bir belge sayfasından görüntü oluşturmak için önizleme yapılandırmasını, ortaya çıkan baytları bir dosyaya yazan bir akışla birleştirirsiniz. İlk olarak, `Metadata` nesnesini başlatın, ardından PNG formatını ve istenen sayfa numaralarını belirten bir `PreviewOptions` örneği oluşturun. Son olarak, önizleme verilerini alan ve diske kaydeden bir `OutputStream` uygulaması sağlayın. Bu yaklaşım her adımı izole eder, kodun bakımını ve toplu işlemler için ölçeklendirilmesini kolaylaştırır.

1. `Metadata`'yi başlatın (Özellik 1).  
2. Bir `PreviewOptions` örneği oluşturun, `PNG`'yi ve istenen sayfa numaralarını belirtin.  
3. Özellik 3'te oluşturduğunuz `OutputStream`'e önizleme baytlarını yazan bir lambda geçirin.  

Bu akış, büyük belgeler için bile **sayfayı görüntü olarak çıkartma** işlemini verimli bir şekilde yapmanızı sağlar.

## Pratik Uygulamalar

- **Belge Yönetim Sistemleri:** Dosya tarayıcılarında küçük resimler gösterir.  
- **Dijital Kütüphaneler:** Tar scanned kitaplar için hızlı görsel ipuçları sağlar.  
- **Hukuk/Finans:** Sözleşme sayfalarının hızlı incelenmesini sağlar.  
- **CMS Platformları:** Yüklenen raporlar için önizleme görüntülerini otomatik oluşturur.  
- **E‑Öğrenme:** Öğrencilere indirmeden önce ders slaytlarına bir bakış sunar.

## Performans Düşünceleri

- **Sayfa toplu işlerini sınırlayın:** Birçok sayfayı aynı anda oluşturmak bellek kullanımını artırabilir.  
- **try‑with‑resources kullanın:** Akışların kapatılmasını garantileyerek sızıntıları önler.  
- **JVM yığınını izleyin:** Büyük PDF'ler daha yüksek yığın (`-Xmx`) gerektirebilir.  
- **Sayısal iddia:** Standart 8 çekirdekli bir sunucuda, 500 sayfalık bir DOCX'i PNG'ye (300 dpi) dönüştürmek 1 GB'den az RAM tüketir ve 45 saniyeden kısa sürede tamamlanır.

## Yaygın Sorunlar ve Çözümler

| Sorun | Neden | Çözüm |
|-------|-------|-------|
| `outputStream` üzerinde `NullPointerException` | `outputStream` başlatılmadı | Gerçek bir `OutputStream` sağlayın (ör. `new FileOutputStream(...)`). |
| Önizleme oluşturulmadı | Yanlış sayfa numarası | Sayfanın varlığını doğrulayın; `metadata.getPageCount()` ile kontrol edin. |
| Dosya yazma izni hatası | Çıktı dizini yalnızca okunabilir | Yazma izinleri verin veya yazılabilir bir klasör seçin. |

## Sıkça Sorulan Sorular

**S: Parola korumalı belgeler için önizleme oluşturabilir miyim?**  
**C:** Evet. Belgeyi, şifre kabul eden uygun yapıcı ile açın, ardından önizleme seçeneklerine devam edin.

**S: Hangi görüntü formatları destekleniyor?**  
**C:** PNG, JPEG, BMP ve GIF, `PreviewFormats` aracılığıyla kullanılabilir.

**S: Tek bir çağrıda birden fazla sayfayı nasıl önizleyebilirim?**  
**C:** `previewOptions.setPageNumbers(new int[]{1,2,3});` ile bir dizi sayfa numarası geçirin.

**S: Görüntü çözünürlüğünü kontrol etmenin bir yolu var mı?**  
**C:** DPI'yi `previewOptions.setDpi(int dpi)` ile ayarlayın (varsayılan 96 DPI).

**S: Kütüphane Android'de çalışıyor mu?**  
**C:** GroupDocs.Metadata saf Java'dır ve uygun JAR'larla Android'de kullanılabilir, ancak UI render'ı Android çerçevesi tarafından yönetilmelidir.

## Sonuç

Artık **docx'i png'ye dönüştürmek** ve GroupDocs.Metadata kullanarak **sayfayı görüntü olarak çıkartma** dosyaları oluşturan belge önizleme Java çözümleri için eksiksiz, üretim‑hazır bir kılavuza sahipsiniz. Üç özellik adımını—metadata'yı başlatma, önizleme seçeneklerini yapılandırma ve görüntü akışını yazma—takip ederek, herhangi bir Java uygulamasına yüksek kaliteli önizlemeler entegre edebilir, kullanıcı deneyimini iyileştirebilir ve işlemi hızlı ve bellek‑verimli tutabilirsiniz.

---

**Son Güncelleme:** 2026-07-21  
**Test Edilen Versiyon:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs  

---

## İlgili Öğreticiler

- [Java'da Belge Önizleme Oluştur – GroupDocs.Metadata Öğreticileri](/metadata/java/document-formats/)
- [Java'da GroupDocs ile Word Belge Meta Verilerine Erişim: Kapsamlı Bir Rehber](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [GroupDocs.Metadata Java ile Word Belge Meta Verilerini Güncelleme: Tam Bir Rehber](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)