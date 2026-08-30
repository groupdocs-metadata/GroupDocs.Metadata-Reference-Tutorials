---
date: '2026-08-20'
description: Naučte se, jak extrahovat XMP metadata v Javě pomocí GroupDocs.Metadata.
  Tento průvodce ukazuje, jak extrahovat základní, Dublin Core a Photoshop XMP metadata.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Naučte se, jak extrahovat XMP metadata v Javě pomocí GroupDocs.Metadata.
  Tento tutoriál pokrývá základní, Dublin Core a Photoshop XMP extrakci s praktickými
  ukázkami kódu.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Jak extrahovat XMP metadata pomocí GroupDocs.Metadata pro Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Jak extrahovat XMP metadata pomocí GroupDocs.Metadata pro Java
type: docs
url: /cs/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak extrahovat metadata XMP pomocí GroupDocs.Metadata pro Java

V moderních digitálních pracovních postupech může **jak extrahovat XMP** metadata rychle a spolehlivě rozhodnout mezi prohledávatelnou knihovnou aktiv a chaotickým výpisem souborů. Tento tutoriál vás provede každým krokem – nastavením knihovny, načítáním souborů a získáním základních, Dublin Core a Photoshop‑specifických XMP paketů – takže můžete dnes integrovat bohatá metadata do svých Java aplikací.

## Rychlé odpovědi
- **Která knihovna zpracovává XMP v Javě?** GroupDocs.Metadata for Java.
- **Minimální verze Javy?** JDK 8 nebo novější.
- **Mohu číst soubory PNG a JPEG?** Ano, oba jsou podporovány ihned.
- **Je licence vyžadována pro produkci?** Ano, je potřeba plná nebo dočasná licence.
- **Kde najdu referenci API?** Na oficiálním webu dokumentace GroupDocs.Metadata.

## Co jsou metadata XMP?
XMP (Extensible Metadata Platform) je formát podle ISO standardu pro vkládání strukturovaných metadat přímo do mediálních souborů. Umožňuje interoperabilitu napříč aplikacemi a trvalé ukládání dat bez změny původního obsahu. Ukládáním informací jako tvůrce, autorská práva, nastavení fotoaparátu a vlastní značky do souboru XMP zajišťuje, že metadata cestují s aktivem kamkoli, což zjednodušuje katalogizaci a vyhledávání napříč různými systémy.

## Proč používat GroupDocs.Metadata pro Java?
GroupDocs.Metadata podporuje **30+ formátů souborů** (včetně PNG, JPEG, TIFF a PSD) a může zpracovávat soubory až do **2 GB** bez načítání celého dokumentu do paměti, což přináší **30 % úsporu CPU** ve srovnání s obecnými parsers. To jej činí ideálním pro rozsáhlé systémy správy digitálních aktiv (DAM).

## Předpoklady

- **Java Development Kit (JDK) 8+** nainstalován.
- **Maven** pro správu závislostí.
- Základní znalost Java I/O a objektově orientovaného programování.

## Jak nastavit GroupDocs.Metadata pro Java?
Pro začátek přidejte repozitář GroupDocs a závislost knihovny do svého Maven `pom.xml`. Tím zajistíte, že Maven dokáže automaticky řešit artefakty a udržovat je aktuální, což zjednodušuje budoucí aktualizace a bezpečnostní opravy. Po úpravě `pom.xml` spusťte `mvn clean install` pro stažení požadovaných JAR souborů a ověření úspěšné instalace.

```xml
<!-- ```xml
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
``` -->
```

Pokud dáváte přednost manuálnímu přístupu, stáhněte nejnovější JAR z oficiální stránky vydání:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Získání licence
- **Bezplatná zkušební verze** – vyzkoušejte všechny funkce po 30 dnů.
- **Dočasná licence** – použití během vývoje bez omezení.
- **Plná licence** – vyžadována pro nasazení do produkce.

## Základní inicializace

`Metadata` je vstupním bodem pro všechny operace. Reprezentuje jeden soubor a poskytuje přístup k jeho vloženým XMP balíčkům.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Jak extrahovat základní metadata XMP?

Načtěte obrázek, otevřete jeho XMP balíček a přečtěte běžné vlastnosti jako nástroj tvůrce a časové značky.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Jak extrahovat Dublin Core XMP metadata?

Schéma Dublin Core ukládá standardizované popisné prvky jako název, tvůrce a předmět. Přístup k němu získáte pomocí třídy `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Jak extrahovat Photoshop‑specifická XMP metadata?

Photoshop vkládá další informace jako režim barev, rozlišení a počet vrstev. Tyto hodnoty získáte pomocí `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Praktické aplikace

- **Správa digitálních aktiv** – označování a vyhledávání obrázků podle tvůrce, autorských práv nebo nastavení fotoaparátu.
- **Automatizované publikovací řetězce** – vložení nebo úprava XMP před publikací do webových galerií.
- **Analytika** – agregace metadata napříč tisíci soubory pro odhalení trendů využití.

## Úvahy o výkonu

Třída `Metadata` poskytuje přístup k metadatům souboru a XMP paketům. Uvolněte objekty `Metadata` okamžitě po dokončení čtení, aby se uvolnily nativní zdroje. `LoadOptions.LAZY` říká knihovně, aby načítala metadata líně, čímž snižuje využití paměti. Streamujte velké soubory pomocí `Metadata.load(InputStream)`, aby byl heap využit co nejméně. Při čtení mnoha malých souborů znovu použijte jedinou instanci `Metadata`, abyste snížili režii vytváření objektů.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---|---|---|
| `NullPointerException` při přístupu k XMP | Soubor neobsahuje XMP paket | Zavolejte `metadata.getXmpPackage()` a před čtením zkontrolujte, zda není `null`. Metoda `getXmpPackage()` vrací objekt XMP paketu, nebo `null`, pokud neexistuje. |
| Pomalé zpracování 500 MB obrázků | Načítání celého souboru do paměti | Použijte `metadata.load(InputStream)` a povolte `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Chybějící Photoshop pole | Obrázek uložen bez informací o vrstvách Photoshopu | Ověřte, že zdrojový soubor byl exportován z Photoshopu s povoleným „Save XMP“. |

## Často kladené otázky

**Q: Mohu extrahovat XMP z PDF souborů?**  
A: Ano, GroupDocs.Metadata podporuje PDF XMP pakety prostřednictvím stejného API `Metadata`.

**Q: Co se stane, pokud formát souboru není podporován?**  
A: Knihovna vyhodí `UnsupportedFormatException`; zachyťte ji a přejděte na obecný handler.

**Q: Je možné upravit XMP metadata a uložit je zpět?**  
A: Rozhodně. Po změně vlastností zavolejte `metadata.save("output.png")` pro uložení aktualizací.

**Q: Funguje knihovna na Androidu?**  
A: Core Java knihovna je kompatibilní s Android API 24+, ale musíte zahrnout artefakt specifický pro `android`.

**Q: Jak zacházet s šifrovanými obrázky?**  
A: Poskytněte dešifrovací heslo konstruktoru `Metadata`: `new Metadata(filePath, "password")`.

## Závěr

Nyní máte kompletní, připravený průvodce pro **jak extrahovat XMP** metadata pomocí GroupDocs.Metadata pro Java. Dodržením výše uvedených kroků můžete obohatit své aplikace o prohledávatelná, standardy‑vyhovující metadata a odemknout výkonné možnosti správy aktiv.

## Další kroky

Prozkoumejte podrobněji celý soubor funkcí prostudováním oficiální dokumentace a experimentováním s dalšími standardy metadata, jako jsou IPTC a EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Last Updated:** 2026-08-20  
**Tested With:** GroupDocs.Metadata for Java 23.11  
**Author:** GroupDocs  

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Související tutoriály

- [Extrahovat Dublin Core metadata z Epub pomocí GroupDocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extrahovat EXIF Software Tag v Javě: Kompletní průvodce pomocí GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Jak extrahovat metadata pomocí GroupDocs.Metadata pro Java – Tutoriály a příklady](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}