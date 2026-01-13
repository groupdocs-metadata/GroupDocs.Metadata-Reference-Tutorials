---
date: '2026-01-13'
description: GroupDocs.Metadata for Java kullanarak diyagram sayfa sayısını nasıl
  alacağınızı ve diyagramlardan metin istatistiklerini nasıl çıkaracağınızı öğrenin.
  Adım adım kurulum ve kod örnekleri dahil.
keywords:
- get diagram page count
- extract text statistics diagrams
- GroupDocs.Metadata Java setup
- Java diagram metadata extraction
title: GroupDocs.Metadata for Java ile Diyagram Sayfa Sayısını Al
type: docs
url: /tr/java/diagram-formats/extract-text-statistics-diagrams-groupdocs-metadata-java/
weight: 1
---

# Java için GroupDocs.Metadata Kullanarak Diyagram Sayfa Sayısını Alın

Modern yazılım projelerinde, **get diagram page count** işlemini hızlı bir şekilde yapabilmek çok zaman kazandırabilir—özellikle raporlar oluşturmanız veya dokümantasyon boru hatlarını otomatikleştirmeniz gerektiğinde. Bu öğreticide, GroupDocs.Metadata for Java'yı kullanarak VDX gibi diyagram dosyalarından sayfa sayısını ve diğer faydalı metin istatistiklerini nasıl çıkaracağınızı öğreneceksiniz. Gerekli kurulum adımlarını gösterecek, ihtiyacınız olan tam kodu sunacak ve bu özelliğin gerçek dünyadaki senaryolarda nasıl parladığını tartışacağız.

## Hızlı Yanıtlar
- **What does “get diagram page count” mean?** Bir diyagram dosyasındaki toplam sayfa (veya sayfa) sayısını döndürür.  
- **Which library provides this feature?** GroupDocs.Metadata for Java.  
- **Do I need a license?** Değerlendirme için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gerekir.  
- **What Java version is required?** JDK 8 veya daha üstü.  
- **Can I process multiple diagrams in a loop?** Evet—döngünüzdeki her dosya için `Metadata` nesnesini örnekleyin.

## “get diagram page count” nedir?
Diyagram sayfa sayısını almak, dosyanın kaç ayrı sayfa veya kanvas içerdiğini keşfetmek için diyagramın meta verilerini sorgulamak anlamına gelir. Bu bilgi, GroupDocs.Metadata'in sunduğu belge istatistiklerinin bir parçasıdır.

## Neden GroupDocs.Metadata for Java Kullanılır?
- **Fast, lightweight extraction** – Tüm diyagramı render etmeye gerek yok.  
- **Broad format support** – VDX, VSDX ve birçok diğer diyagram türüyle çalışır.  
- **Simple API** – Birkaç satır kod size sayfa sayısını, yazarını, oluşturulma tarihini ve daha fazlasını verir.  

## Önkoşullar
- **GroupDocs.Metadata for Java** (version 24.12 veya daha yeni).  
- **JDK 8+** makinenizde kurulu.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Bağımlılık yönetimi için Maven.  

## GroupDocs.Metadata for Java Kurulumu

### Maven Kullanarak
`pom.xml` dosyanıza aşağıda gösterildiği gibi depo ve bağımlılığı ekleyin:

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

### Doğrudan İndirme
Maven kullanmak istemiyorsanız, resmi sürüm sayfasından en son JAR'ı alın: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Lisans Edinme
- **Free Trial** – Ücretsiz olarak tüm özellikleri indirin ve keşfedin.  
- **Temporary License** – Sınırsız test için geçici bir anahtar isteyin.  
- **Full License** – Sınırsız üretim kullanımı için satın alın.

### Temel Başlatma
Aşağıda bir diyagram dosyasıyla çalışmaya başlamak için gereken minimum kod bulunmaktadır. Bu snippet **Metadata nesnesini başlatır**, bu nesne diyagram sayfa sayısını almayı da içeren tüm sonraki işlemler için giriş noktasıdır.

```java
import com.groupdocs.metadata.Metadata;

public class DiagramInitialization {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        try (Metadata metadata = new Metadata(inputPath)) {
            System.out.println("GroupDocs.Metadata initialized successfully.");
        }
    }
}
```

## Uygulama Kılavuzu – Diyagram Sayfa Sayısını Alma

Kütüphane hazır olduğuna göre, sayfa sayısını elde etmek için tam adımlara göz atalım.

### Adım 1: Root Paketi Alın
Her diyagram tipinin meta verilerine erişim sağlayan belirli bir root paketi vardır. Bunu almak için genel `getRootPackageGeneric()` metodunu kullanın.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.DiagramRootPackage;

public class DiagramReadDocumentStatistics {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        
        try (Metadata metadata = new Metadata(inputPath)) {
            // Obtain the root package for the diagram document type
            DiagramRootPackage root = metadata.getRootPackageGeneric();
```

### Adım 2: Belge İstatistiklerine Erişin (Diyagram Sayfa Sayısını Alın)
Root paket elinizde olduğunda, `getDocumentStatistics()` ve ardından `getPageCount()` metodunu çağırarak **get diagram page count** elde edebilirsiniz.

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**Explanation**: `getDocumentStatistics()` sayfa sayısı dahil olmak üzere çeşitli faydalı metrikleri tutan bir nesne döndürür. Bu nedenle `pageCount` değişkeni diyagramdaki toplam sayfayı temsil eder.

### Adım 3: İstisnaları Zarifçe Ele Alın
Dosya ile ilgili işlemler birçok nedenden dolayı başarısız olabilir (eksik dosya, desteklenmeyen format vb.). Kodunuzu bir try‑catch bloğuna sararak net hata mesajları alabilirsiniz.

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

**Troubleshooting Tips**  
- Dosya yolunun (`inputPath`) mevcut bir diyagram dosyasına işaret ettiğini doğrulayın.  
- Diyagram formatının (ör. VDX) mevcut GroupDocs.Metadata sürümü tarafından desteklendiğinden emin olun.  
- Lisans hatası alıyorsanız, geçerli bir deneme veya tam lisans anahtarının uygulandığını kontrol edin.

## Pratik Uygulamalar

| Kullanım Durumu | Sayfa Sayısının Yardımcı Olduğu Şekil |
|-----------------|----------------------------------------|
| **Proje Yönetimi** | Akış şemaları veya mimari diyagramlardaki sayfaları sayarak çabayı hızlı bir şekilde tahmin edin. |
| **Otomatik Raporlama** | Paydaş incelemeleri için her diyagramı ve sayfa sayısını listeleyen özet tablolar oluşturun. |
| **Veri Analitiği** | Sayfa sayısı metriklerini panellere aktararak zaman içinde dokümantasyon büyümesini izleyin. |

## Performans Düşünceleri

- **Resource Management**: Java’nın try‑with‑resources (gösterildiği gibi) kullanarak `Metadata` nesnesini otomatik olarak kapatın ve belleği serbest bırakın.  
- **Batch Processing**: Çok sayıda diyagram işlenirken, dosya başına tek bir `Metadata` örneğini yeniden kullanın ve gereksiz veri yüklemelerinden kaçının.  

## Sonuç

Artık GroupDocs.Metadata for Java kullanarak **get diagram page count** ve diğer metin istatistiklerini nasıl çıkaracağınızı biliyorsunuz. Bu hafif yaklaşım, daha büyük otomasyon boru hatlarına, raporlama araçlarına veya diyagram dosyalarına hızlı bir içgörü sağlayan herhangi bir uygulamaya entegre edilebilir.

### Sonraki Adımlar
- Yazar, oluşturulma tarihi ve özel özellikler gibi ek istatistikleri keşfedin.  
- Sayfa sayısı mantığını dosya sistemi taramasıyla birleştirerek tüm diyagram klasörlerini işleyin.  
- Daha derin API kapsamı için resmi kaynaklara göz atın.

## SSS Bölümü

1. **What file formats are supported by GroupDocs.Metadata for diagrams?**  
   - VDX, VSDX ve kurumsal ortamlarda kullanılan birçok diğer yaygın diyagram formatını destekler.

2. **Can I use GroupDocs.Metadata with non‑diagram documents?**  
   - Evet, kütüphane PDF'ler, Word dosyaları, elektronik tablolar ve daha fazlası ile çalışır, birleşik bir meta veri çıkarma deneyimi sunar.

3. **How do I handle unsupported file formats?**  
   - Dosyanın uzantısını belgelerdeki desteklenen listelerle doğrulayın. Bilinmeyen formatlar için önce desteklenen bir tipe dönüştürmeyi düşünün.

4. **Is there a limit to the number of diagrams I can process at once?**  
   - Katı bir limit yok, ancak çok büyük bir toplu işlem bellek kullanımı ve çoklu iş parçacığı stratejilerine dikkat gerektirebilir.

5. **What should I do if I encounter an initialization error?**  
   - Dosya yolunu tekrar kontrol edin, JAR'ların sınıf yolunuza doğru eklendiğinden emin olun ve geçerli bir lisansın (deneme bile olsa) uygulandığını doğrulayın.

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/metadata/java/)
- [API Referansı](https://reference.groupdocs.com/metadata/java/)
- [İndirme](https://releases.groupdocs.com/metadata/java/)
- [GitHub Deposu](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/metadata/)
- [Geçici Lisans Başvurusu](https://purchase.groupdocs.com/temporary-license/) 

---

**Son Güncelleme:** 2026-01-13  
**Test Edilen Versiyon:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs