---
date: '2026-06-12'
description: Zjistěte, jak vytvořit vlastní XMP balíčky, spravovat metadata souborů
  a přidávat vlastní metadata do PDF pomocí GroupDocs.Metadata pro Java.
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
title: Vytvořte vlastní XMP balíček pomocí GroupDocs.Metadata pro Java
type: docs
url: /cs/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# Vytvořte vlastní XMP balíček pomocí GroupDocs.Metadata pro Java

V moderních digitálních pracovních postupech je **vytváření vlastních XMP balíčků** nezbytné pro vložení bohatých, prohledávatelných metadat přímo do souborů. Ať už pracujete s obrázky, PDF nebo multimediálními aktivy, GroupDocs.Metadata pro Java vám poskytuje spolehlivý způsob, jak **spravovat metadata souborů** a **přidávat vlastní metadata do PDF** bez externích databází. V tomto tutoriálu vás provedeme celým procesem – od nastavení knihovny po vložení plně vybaveného XMP paketu – abyste mohli ještě dnes začít obohacovat své dokumenty.

## Rychlé odpovědi
- **Jaký je první krok?** Přidejte GroupDocs.Metadata jako Maven závislost nebo stáhněte JAR.  
- **Kolik řádků kódu?** K vytvoření a připojení vlastního XMP balíčku stačí pouze tři stručná příkazy.  
- **Jaké formáty souborů jsou podporovány?** Více než 50 formátů, včetně JPEG, PNG, PDF, DOCX a TIFF.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována trvalá licence.  
- **Mohu to použít s Java 11+?** Ano, knihovna je kompatibilní s Java 8 až Java 21.

## Co je „vytvořit vlastní XMP balíček“?
*Vytvoření vlastního XMP balíčku* znamená vytvořit XMP paket, který obsahuje uživatelem definovaná metadata pole, a vložit jej do podporovaného souboru. Tento paket je uložen uvnitř XMP sekce souboru, což činí metadata přenosná a prohledávatelná jakoukoli aplikací podporující XMP.

## Proč použít GroupDocs.Metadata pro Java pro správu metadat souborů?
GroupDocs.Metadata podporuje **více než 50 vstupních a výstupních formátů** a může zpracovávat soubory až do **2 GB** bez načítání celého dokumentu do paměti, což snižuje spotřebu RAM až o **80 %** u velkých aktiv. API také poskytuje vlákny‑bezpečné operace, což umožňuje vysokokapacitní dávkové zpracování v podnikovém prostředí.

## Požadavky
- **Java Development Kit** 8 nebo novější (doporučeno Java 11+).  
- IDE jako **IntelliJ IDEA** nebo **Eclipse**.  
- Maven nainstalovaný pro správu závislostí.  
- Základní pochopení Java tříd a konceptů metadat.

## Nastavení GroupDocs.Metadata pro Java
### Nastavení Maven
Přidejte následující závislost do souboru `pom.xml`, abyste zahrnuli GroupDocs.Metadata:

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

Odkazujte na [API dokumentaci](https://reference.groupdocs.com/metadata/java/) pro úplné podpisy metod.  
Pro podrobnou referenci API viz [GroupDocs.Metadata Java dokumentace](https://docs.groupdocs.com/metadata/java/).

**Přímé stažení** – Pokud dáváte přednost ručnímu nastavení, získáte nejnovější JAR z [GroupDocs.Metadata pro Java vydání](https://releases.groupdocs.com/metadata/java/). Také můžete zobrazit stránku [Nejnovější vydání](https://releases.groupdocs.com/metadata/java/) pro podrobnosti o změnách.

### Získání licence
- **Bezplatná zkušební verze** – Vyzkoušejte všechny funkce zdarma.  
- **Dočasná licence** – Získejte časově omezený klíč pro testování vývoje. ([Získat dočasnou licenci](https://purchase.groupdocs.com/temporary-license/))  
- **Koupit** – Získejte trvalou licenci pro produkční použití.

Zdrojový kód a příklady jsou k dispozici na [GroupDocs Metadata na GitHubu](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## Průvodce implementací
Níže je krok‑za‑krokem průvodce, který přesně ukazuje, jak **vytvořit vlastní XMP balíček** a vložit jej do souboru.

### Jak vytvořit vlastní XMP balíček a připojit jej k souboru?
Načtěte cílový soubor pomocí třídy `Metadata`, vytvořte `XmpPacketWrapper`, definujte vlastní XMP pole a nakonec uložte změny. Tento end‑to‑end tok vyžaduje po inicializaci pouze tři volání metod. Proces zajišťuje, že XMP paket je správně vložen a soubor zůstává plně funkční ve všech podporovaných aplikacích.

### Inicializace objektu Metadata
`Metadata` je hlavní třída, která představuje soubor a poskytuje metody pro čtení a zápis jeho metadat.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### Vytvoření nového XmpPacketWrapper
`XmpPacketWrapper` funguje jako kontejner pro jeden nebo více XMP paketů, umožňující dávkové aktualizace před uložením.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### Definice a konfigurace vlastního XMP balíčku
`IXmp` rozhraní vám umožňuje definovat vlastní XMP schémata a nastavit hodnoty vlastností v rámci paketu.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### Uložení aktualizovaných metadat
`Metadata.save()` zapíše upravená metadata zpět do původního souboru a zachová všechny přidané XMP pakety.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### Vysvětlení klíčových komponent
- **Metadata Object** – Centrální uzel pro přístup k metadatům souboru.  
- **IXmp Interface** – Poskytuje metody pro čtení/zápis XMP‑specifických polí.  
- **XmpPacketWrapper** – Uchovává jeden nebo více XMP paketů, umožňuje dávkové aktualizace.  
- **Custom XMP Package** – Vaše uživatelem definované schéma, které ukládá doplňující informace.

## Časté problémy a řešení
- **Unsupported File Format** – Ověřte, že typ cílového souboru je uveden v oficiálním seznamu formátů (více než 50 podporovaných formátů).  
- **License Not Found** – Ujistěte se, že soubor licence je umístěn v kořenovém adresáři aplikace nebo nastaven pomocí `License.setLicense("license_path")`.  
- **Memory Exhaustion on Large Files** – Použijte `metadata.setLoadOptions(LoadOptions.lazyLoad())` pro zpracování metadat líně a udržení nízké spotřeby paměti.

Pro další pomoc navštivte fórum [GroupDocs podpora](https://forum.groupdocs.com/c/metadata/).

## Praktické aplikace
1. **Digitální správa aktiv** – Vložte licenční a uživatelská práva přímo do obrázků a PDF.  
2. **Personalizace obsahu** – Připojte uživatelsky specifické identifikátory k dokumentům pro cílené doručení.  
3. **Regulační soulad** – Uložte auditní stopy a zásady uchovávání přímo v souboru, což zjednodušuje audity správy.

## Úvahy o výkonu
- **Optimalizace zdrojů** – Zpracovávejte metadata ve streamovacím režimu, aby spotřeba RAM zůstala pod **100 MB** u souborů větších než **1 GB**.  
- **Aktualizace verzí** – Udržujte knihovnu aktuální; každé hlavní vydání přidává podporu nových formátů a zvyšuje rychlost zpracování až o **30 %**.

## Závěr
Díky tomuto průvodci nyní víte, jak **vytvořit vlastní XMP balíčky** pomocí GroupDocs.Metadata pro Java, což vám umožní **efektivně spravovat metadata souborů** a **přidávat vlastní metadata do PDF** a mnoha dalších formátů. Experimentujte s dalšími XMP schématy, integrujte pracovní postup do vašeho CI pipeline nebo jej kombinujte s GroupDocs.Viewer pro end‑to‑end zpracování dokumentů.

## Často kladené otázky

**Q: Jaké formáty souborů podporují vlastní XMP balíčky?**  
A: Více než 50 formátů – včetně JPEG, PNG, PDF, DOCX a TIFF – podporuje injekci XMP paketu. Kompletní seznam najdete v [dokumentaci GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**Q: Mohu upravit existující XMP metadata pomocí GroupDocs.Metadata?**  
A: Ano, knihovna vám umožní číst, měnit a mazat jakoukoli XMP vlastnost pomocí rozhraní `IXmp`.

**Q: Jak zacházet se soubory, které nativně nepodporují XMP?**  
A: Pro nepodporované formáty zvažte zabalení souboru do kontejneru, který XMP podporuje (např. konverze do PDF), nebo použijte alternativní úložiště metadat.

**Q: Je knihovna kompatibilní s Java 17 LTS?**  
A: Naprosto – GroupDocs.Metadata je testována s Java 8 až Java 21, včetně všech LTS verzí.

**Q: Jaké jsou typické chyby při přidávání XMP balíčků?**  
A: Běžné úskalí zahrnují použití nesprávného URI jmenného prostoru, překročení maximální velikosti paketu (≈ 2 MB) nebo pokus o zápis do souboru jen pro čtení. Zajistěte správná oprávnění a před uložením ověřte svůj XML schéma.

**Poslední aktualizace:** 2026-06-12  
**Testováno s:** GroupDocs.Metadata 23.12 for Java  
**Autor:** GroupDocs  

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

## Související tutoriály

- [Přidání vlastních XMP metadat do souborů pomocí GroupDocs.Metadata Java: Kompletní průvodce](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [Jak přidat metadata do PDF pomocí GroupDocs.Metadata pro Java – Průvodce pro vývojáře](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [Jak extrahovat vlastní metadata z PDF pomocí GroupDocs.Metadata v Java: Kompletní průvodce](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)