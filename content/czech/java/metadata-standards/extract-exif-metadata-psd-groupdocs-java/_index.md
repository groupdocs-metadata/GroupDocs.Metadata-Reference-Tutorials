---
date: '2026-08-10'
description: Naučte se, jak extrahovat EXIF metadata z PSD souborů pomocí GroupDocs.Metadata
  pro Java. Tento průvodce zahrnuje základní extrakci, IFD balíčky, GPS data a reálné
  příklady použití.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Naučte se, jak extrahovat EXIF metadata z PSD souborů pomocí GroupDocs.Metadata
  pro Java. Krok za krokem průvodce, ukázky kódu a tipy na řešení problémů pro vývojáře.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Jak extrahovat EXIF metadata z PSD souborů pomocí GroupDocs.Metadata
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
title: Jak extrahovat EXIF metadata z PSD souborů pomocí GroupDocs.Metadata
type: docs
url: /cs/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Jak extrahovat EXIF metadata ze souborů PSD pomocí GroupDocs.Metadata

Extrahování **EXIF metadata** ze souborů PSD je rutinní, ale výkonný krok, když potřebujete auditovat původ obrázků, automatizovat označování aktiv nebo vytvářet prohledávatelné mediální knihovny. V tomto tutoriálu objevíte **jak rychle extrahovat EXIF** pomocí GroupDocs.Metadata pro Javu, uvidíte přesné volání API a naučíte se pracovat s pokročilými IFD balíčky a GPS souřadnicemi. Na konci budete připraveni integrovat extrakci metadat do jakéhokoli workflow založeného na Javě.

## Rychlé odpovědi

Třída `Metadata` představuje soubor a poskytuje přístup k jeho metadatům.

- **Co je první řádek kódu?** `Metadata metadata = new Metadata("sample.psd");`
- **Která metoda vrací jméno autora?** `metadata.getExif().getArtist();`
- **Mohu číst GPS data?** Ano – použijte `metadata.getExif().getGpsInfo();`
- **Potřebuji licenci pro produkci?** Platná licence GroupDocs.Metadata je vyžadována po uplynutí zkušebního období.
- **Podporovaná verze Javy?** Java 8 nebo novější (až do Java 21).

## Co jsou EXIF metadata?

EXIF (Exchangeable Image File Format) metadata ukládá nastavení fotoaparátu, časové razítka vytvoření a údaje o poloze uvnitř souborů obrázků. GroupDocs.Metadata čte tyto informace přímo ze struktury binárních dat souborů PSD a zpřístupňuje je prostřednictvím čistého Java API. Umožňuje vývojářům programově získávat podrobnosti jako model fotoaparátu, expoziční čas a GPS souřadnice bez ruční kontroly.

## Proč používat GroupDocs.Metadata pro Javu?

GroupDocs.Metadata podporuje **30+ formátů souborů** (včetně PSD, JPEG, PNG, TIFF) a může zpracovávat soubory až do **2 GB** bez načítání celého dokumentu do paměti. Knihovna extrahuje **více než 150 různých EXIF značek**, což zajišťuje, že máte kompletní sadu atributů fotoaparátu a GPS potřebných pro analytiku nebo soulad s předpisy.

## Požadavky

- **Java Development Kit (JDK) 8** nebo novější nainstalovaný na vašem počítači.  
- **Maven** pro správu závislostí.  
- **GroupDocs.Metadata pro Javu verze 24.12** (nebo novější).  
- Základní znalost Java tříd, objektů a zpracování výjimek.

### Požadované knihovny a závislosti
| Závislost | Maven koordináty |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Nastavení prostředí
Měli byste mít IDE kompatibilní s Mavenem, jako je IntelliJ IDEA nebo Eclipse. Vytvořte nový Maven projekt nebo přidejte závislost do existujícího.

## Jak nastavit GroupDocs.Metadata pro Javu

GroupDocs.Metadata lze přidat do Maven projektu pomocí několika řádků konfigurace. Následující kroky ukazují, jak zahrnout repozitář a závislost, aby byla knihovna dostupná na classpath.

### Nastavení Maven
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

### Přímé stažení
Alternativně stáhněte nejnovější JAR z oficiální stránky vydání: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Získání licence
To run the library beyond the 30‑day trial, obtain a temporary or full license:

1. Navštivte [Stránka pro nákup licence](https://purchase.groupdocs.com/temporary-license).  
2. Vyberte **temporary** pro testování nebo **full** pro produkci.  
3. Postupujte podle pokynů na obrazovce a vložte licenční soubor (`metadata.lic`) do classpath vaší Javy.

### Základní inicializace a nastavení
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

## Jak extrahovat základní vlastnosti EXIF metadata z PSD obrázku
Tato sekce vysvětluje, jak načíst soubor PSD, získat přístup k EXIF kontejneru a přečíst nejčastější značky jako **artist**, **copyright** a **software**. Proces zahrnuje vytvoření instance `Metadata`, zavolání `getExif()` a následné získání jednotlivých vlastností pomocí jednoduchých getter metod.

### Implementace krok za krokem
1. **Vytvořte instanci `Metadata`** ukazující na váš PSD soubor.  
2. **Zavolejte `getExif()`** pro získání EXIF kontejneru.  
3. **Přečtěte jednotlivé vlastnosti** jako `getArtist()`, `getCopyright()` a `getSoftware()`.  
4. **Vytiskněte nebo uložte** hodnoty podle logiky vaší aplikace.

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

> **Tip:** Objekt `Metadata` automaticky detekuje formát souboru, takže můžete znovu použít stejný kód pro JPEG nebo TIFF soubory bez úprav.

## Jak extrahovat vlastnosti EXIF IFD balíčku z PSD obrázku
Sekce IFD (Image File Directory) obsahuje podrobnější technické informace jako **camera serial number**, **lens model** a **user comments**. `Ifd0` představuje primární Image File Directory obsahující základní informace o fotoaparátu. Extrahování těchto polí je užitečné pro forenzní analýzu nebo vysoce přesné katalogizování.

### Kroky implementace
1. **Znovu použijte instanci `Metadata`** z předchozí sekce.  
2. **Navigujte do IFD kontejneru** pomocí `metadata.getExif().getIfd0()`.  
3. **Přečtěte vlastnosti** jako `getBodySerialNumber()` a `getUserComment()`.  
4. **Vypište data** nebo je mapujte do vašeho doménového modelu.

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

## Jak získat GPS data (šířka, délka) z PSD souboru
Mnoho moderních fotoaparátů vkládá GPS souřadnice do EXIF bloku. `GpsInfo` obsahuje geografické souřadnice extrahované z EXIF dat. Zavolejte `metadata.getExif().getGpsInfo()` a poté použijte `getLatitude()`, `getLongitude()` a `getAltitude()` k získání přesných údajů o poloze – není potřeba žádné další parsování.

### Podrobné kroky
1. **Získejte objekt GPS info**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Přečtěte šířku a délku**: `gps.getLatitude()` vrací `double` v desetinných stupních.  
3. **Zpracujte chybějící data**: API vrací `null`, pokud značka chybí, takže se chraňte před `NullPointerException`.

> **Častý úskalí:** Některé PSD soubory ukládají GPS souřadnice jako racionální čísla; knihovna je automaticky normalizuje, ale starší soubory mohou vyžadovat ruční konverzi.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| `Unsupported format` výjimka | Použití starší verze GroupDocs.Metadata, která nerozpoznává PSD | Aktualizujte na verzi 24.12 nebo novější |
| `NullPointerException` při volání `getArtist()` | EXIF značka není v zdrojovém souboru přítomna | Zkontrolujte `metadata.getExif().hasArtist()` před čtením |
| Chyba licence po 30 dnech | Licenční soubor nebyl nalezen na classpath | Umístěte `metadata.lic` do `src/main/resources` nebo nastavte `Metadata.setLicense("path/to/license")` |

## Často kladené otázky

**Q: Mohu extrahovat EXIF metadata z heslem chráněného PSD souboru?**  
A: Ano. Načtěte soubor pomocí `new Metadata("file.psd", "password")` a poté přistupujte k EXIF datům jako obvykle.

**Q: Podporuje GroupDocs.Metadata hromadné zpracování mnoha PSD souborů?**  
A: Rozhodně. Vytvořte objekt `Metadata` uvnitř smyčky nebo použijte pomocníka `MetadataCollection` pro efektivní zpracování adresářů.

**Q: Jaké verze Javy jsou oficiálně podporovány?**  
A: Java 8 až Java 21 jsou plně testovány. Knihovna používá pouze standardní API, takže funguje na jakémkoli kompatibilním JVM.

**Q: Je možné zapisovat EXIF data zpět do PSD souboru?**  
A: Ano. Po úpravě vlastností pomocí objektu `Exif` zavolejte `metadata.save("output.psd")` pro uložení změn.

**Q: Jak velký PSD soubor může knihovna zpracovat, aniž by došlo k nedostatku paměti?**  
A: GroupDocs.Metadata streamuje data a může zpracovat soubory až do **2 GB** na typickém stroji s 8 GB RAM díky své nízkopaměťové architektuře.

## Závěr
Nyní víte **jak extrahovat EXIF** metadata ze souborů PSD pomocí GroupDocs.Metadata pro Javu, od základních značek po pokročilé IFD a GPS informace. Integrujte tyto úryvky do vašeho zpracovatelského řetězce obrázků pro automatizaci katalogizace, kontrol souladu nebo služeb založených na poloze. Pro hlubší zkoumání zkuste extrahovat metadata z dalších podporovaných formátů (JPEG, TIFF, PNG) nebo experimentujte s možnostmi zápisu zpět pro vložení vlastních značek.

---

**Poslední aktualizace:** 2026-08-10  
**Testováno s:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Extrahovat obrazové zdroje ze souborů PSD pomocí GroupDocs.Metadata v Javě: Kompletní průvodce](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Extrahovat hlavičku PSD a informace o vrstvách pomocí GroupDocs.Metadata pro Javu: Kompletní průvodce](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Extrahovat vlastnosti MakerNote jako TIFF/EXIF značky pomocí GroupDocs.Metadata v Javě](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)