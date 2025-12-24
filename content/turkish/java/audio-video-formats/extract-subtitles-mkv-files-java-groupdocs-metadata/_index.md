---
date: '2025-12-24'
description: Java ve GroupDocs.Metadata kullanarak MKV dosyalarından mkv altyazılarını
  nasıl çıkaracağınızı öğrenin. Bu adım adım kılavuz, kurulum, uygulama ve gerçek
  dünya kullanım örneklerini kapsar.
keywords:
- extract subtitles MKV
- Java GroupDocs.Metadata
- subtitle extraction Java
title: Java ve GroupDocs.Metadata ile mkv altyazılarını nasıl çıkarılır
type: docs
url: /tr/java/audio-video-formats/extract-subtitles-mkv-files-java-groupdocs-metadata/
weight: 1
---

# Java ve GroupDocs.Metadata ile mkv altyazılarını çıkarma

MKV kapsayıcılarından altyazı çıkarmak, özellikle çeviri, erişilebilirlik veya içerik‑yönetimi iş akışları için metne ihtiyaç duyduğunuzda, samanlıkta iğne aramaya benzer bir çaba gibi hissettirebilir. Bu öğreticide, GroupDocs.Metadata Java kütüphanesini kullanarak **mkv altyazılarını nasıl çıkarılır** verimli bir şekilde öğreneceksiniz. Gerekli kurulumu adım adım gösterecek, ihtiyacınız olan tam kodu sunacak ve altyazı çıkarımının gerçek bir fark yarattığı pratik senaryoları tartışacağız.

## Hızlı Yanıtlar
- **MKV altyazı çıkarımını hangi kütüphane yönetir?** GroupDocs.Metadata for Java  
- **Bu rehberin hedeflediği birincil anahtar kelime nedir?** extractv subtitles  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme çalışır; üretim için tam lisans gereklidir.  
- **Büyük MKV dosyalarını işleyebilir miyim?** Evet—bellek kullanımını düşük tutmak için altyazıları akışlar veya toplu işlemler halinde işleyin.  
- **Java 8 yeterli mi?** Evet, JDK 8 veya daha yenisi desteklenir.

## “extract mkv subtitles” nedir?
mkv altyazılarını çıkarmak, bir Matroska (MKV) kapsayıcısına gömülmüş altyazı izlerini okuyup metin, zamanlama ve dil bilgilerini elde etmek anlamına gelir. Bu işlem, otomatik çeviri hatları, altyazı kalite kontrolleri ve erişilebilirlik uyumluluğu gibi iş akışları için esastır.

## Neden GroupDocs.Metadata for Java kullanmalı?
GroupDocs.Metadata, karmaşık Matroska yapısını soyutlayan yüksek seviyeli bir API sunar, böylece düşük seviyeli ayrıştırma yerine iş mantığına odaklanabilirsiniz. Birçok altyazı formatını destekler, dil etiketlerini işler ve standart Java projeleriyle sorunsuz bir şekilde bütünleşir.

## Önkoşullar
- **Java Development Kit (JDK)** 8 veya daha yenisi  
- **IDE** (IntelliJ IDEA, Eclipse veya benzeri)  
- **Maven** bağımlılık yönetimi için  
- Java ve video dosyası kavramlarına temel aşinalık  

## GroupDocs.Metadata for Java Kurulumu

### Maven Kurulumu
`pom.xml` dosyanıza GroupDocs deposunu ve metadata bağımlılığını ekleyin:

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
Maven kullanmak istemiyorsanız, en son JAR dosyasını [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) adresinden indirebilirsiniz.

### Lisans Edinme
- API'yi keşfetmek için ücretsiz deneme ile başlayın.  
- Gerekirse geçici bir geliştirme lisansı edinin.  
- Ticari dağıtımlar için tam lisans satın alın.

### Temel Başlatma ve Kurulum
MKV dosyanıza işaret eden bir `Metadata` örneği oluşturun:

```java
try (Metadata metadata = new Metadata("path/to/your/file.mkv")) {
    // Your code here
}
```

Bu satır dosyayı açar ve metadata çıkarımı için hazırlar.

## GroupDocs.Metadata kullanarak mkv altyazılarını nasıl çıkarılır

### Adım 1: Metadata nesnesini başlatma
İlk olarak, `Metadata` sınıfını MKV dosyanızın yolu ile örnekleyin:

```java
try (Metadata metadata = new Metadata(filePath)) {
    // Proceed with extracting subtitles
}
```

### Adım 2: Matroska kök paketine erişim
Kapsayıcı içindeki tüm izlere giriş noktaları sağlayan kök paketi alın:

```java
MatroskaRootPackage root = metadata.getRootPackageGeneric();
```

### Adım 3: Altyazı izlerini döngüye al
Her bir altyazı izini döngüye alarak dil, zaman kodu, süre ve gerçek altyazı metnini okuyun:

```java
for (MatroskaSubtitleTrack subtitleTrack : root.getMatroskaPackage().getSubtitleTracks()) {
    String language = subtitleTrack.getLanguageIetf() != null ? 
        subtitleTrack.getLanguageIetf() : subtitleTrack.getLanguage();
    
    for (com.groupdocs.metadata.core.MatroskaSubtitle subtitle : subtitleTrack.getSubtitles()) {
        String timecode = subtitle.getTimecode();
        long duration = subtitle.getDuration();

        System.out.println(String.format("Language=%s, Timecode=%s, Duration=%d", language, timecode, duration));
        System.out.println(subtitle.getText());
    }
}
```

Döngü, her altyazının metadata'sını ve metin içeriğini yazdırır, böylece MKV dosyasına gömülmüş tüm altyazıların tam bir görünümünü elde edersiniz.

## Yaygın Sorunlar ve Çözümler
- **Dosya Bulunamadı** – Mutlak yolu ve dosya izinlerini iki kez kontrol edin.  
- **Desteklenmeyen MKV sürümü** – En son GroupDocs.Metadata sürümünü kullandığınızdan emin olun.  
- **Büyük dosyalarda yetersiz bellek** – Altyazıları parçalar halinde işleyin veya mevcutsa akış API'lerini kullanın.

## Pratik Uygulamalar
1. **Çeviri Projeleri** – Altyazıları dışa aktarın, çevirin ve videoya yeniden ekleyin.  
2. **İçerik Yönetim Sistemleri** – Video kütüphanesinde aranabilirlik için altyazı metnini indeksleyin.  
3. **Erişilebilirlik İyileştirmeleri** – Her videonun doğru zamanlanmış altyazı içerdiğini doğrulayın.

## Performans İpuçları
- Geçici depolama için verimli koleksiyonlar (ör. `ArrayList`) kullanın.  
- Yerel kaynakları serbest bırakmak için `Metadata` nesnesini hızlıca kapatın (try‑with‑resources).  
- Performans iyileştirmeleri için GroupDocs.Metadata kütüphanesini güncel tutun.

## Sonuç
Artık Java'da GroupDocs.Metadata kullanarak **mkv altyazılarını çıkarmak** için net ve üretim‑hazır bir yönteme sahipsiniz. İster bir altyazı‑çeviri hattı oluşturuyor, medya CMS'ini zenginleştiriyor ya da erişilebilirlik uyumluluğunu sağlıyor olun, bu yaklaşım zaman kazandırır ve düşük seviyeli ayrıştırma ihtiyacını ortadan kaldırır.

Sonra, özel metadata ekleme, ses izlerini çıkarma veya birden fazla video dosyasını toplu işleme gibi diğer özellikleri keşfedin. Kodlamanın tadını çıkarın!

## Sıkça Sorulan Sorular

**S: GroupDocs.Metadata kullanmak için gereken minimum Java sürümü nedir?**  
C: JDK 8 veya daha yenisi gereklidir.

**S: GroupDocs.Metadata ile diğer video formatlarından altyazı çıkarabilir miyim?**  
C: Evet, kütüphane çeşitli kapsayıcıları destekler, ancak bu rehber MKV üzerine odaklanmıştır.

**S: Bir MKV dosyasındaki birden fazla altyazı izini nasıl yönetirim?**  
C: Kod örneğinde gösterildiği gibi her `MatroskaSubtitleTrack` üzerinden döngüye alın.

**S: Uygulamam `FileNotFoundException` hatası verirse ne yapmalıyım?**  
C: Dosya yolunun doğru, dosyanın mevcut ve işlemin okuma izinlerine sahip olduğundan emin olun.

**S: İngilizce dışındaki altyazı dilleri destekleniyor mu?**  
C: Kesinlikle—GroupDocs.Metadata ISO 639‑2/IETF BCP‑47 dil etiketlerini okur, böylece desteklenen herhangi bir dil işlenir.

---

**Son Güncelleme:** 2025-12-24  
**Test Edilen Sürüm:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs  

**Kaynaklar**
- **Dokümantasyon:** [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **API Referansı:** [GroupDocs API Reference](https://reference.groupdocs.com/metadata/java/)  
- **İndirme:** [Get the latest version](https://releases.groupdocs.com/metadata/java/)  
- **GitHub Deposu:** [Explore on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Ücretsiz Destek Forumu:** [Ask questions and get support](https://forum.groupdocs.com/c/metadata/)  
- **Geçici Lisans:** [Obtain a temporary license](https://purchase.groupdocs.com/temporary-license/)