---
date: '2026-08-05'
description: Zjistěte, jak detekovat verzi PDF v Javě a aktualizovat metadata PDF
  pomocí GroupDocs.Metadata for Java. Obsahuje detekci verze, čtení vlastností a úpravu
  metadat.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Detekujte verzi PDF v Javě a aktualizujte metadata PDF pomocí GroupDocs.Metadata.
  Podrobný průvodce pro Javu ukazuje detekci verze, čtení vlastností a úpravu metadat.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: Detekce verze PDF v Javě a aktualizace metadat PDF
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: Detekce verze PDF v Javě a aktualizace metadat PDF
type: docs
url: /cs/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Detekce verze PDF v Javě a aktualizace metadat PDF

Programatické spravování souborů PDF často znamená, že musíte **detect PDF version java** a **update PDF metadata** — autor, název, datum vytvoření nebo dokonce samotnou verzi PDF. Nekonzistentní metadata mohou způsobit problémy s vykreslováním nebo ztížit vyhledávání dokumentů ve velkém úložišti. Tento tutoriál vás provede detekcí verze PDF a aktualizací metadat PDF pomocí **GroupDocs.Metadata** pro Javu, což vám poskytne spolehlivý způsob, jak udržet vaše PDF přehledná, prohledávatelná a kompatibilní s jakýmkoli prohlížečem.

## Rychlé odpovědi
- **Co znamená „update PDF metadata“?** Přidávání, úprava nebo odstraňování informací uložených v souboru PDF.  
- **Která knihovna v Javě to umožňuje?** GroupDocs.Metadata.  
- **Mohu také detekovat verzi PDF?** Ano, stejná API poskytuje detekci verze.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro hodnocení; pro produkční nasazení je vyžadována placená licence.  
- **Jaká verze Javy je požadována?** JDK 8 nebo novější.  

## Co je aktualizace metadat PDF?
Aktualizace metadat PDF znamená programové čtení a zápis popisných informací vložených do souboru PDF — například autor, název, předmět a vlastní vlastnosti. Správná metadata zlepšují vyhledatelnost, shodu a správu verzí v systémech pro správu dokumentů. Přesná metadata také umožňují automatické indexování, reportování souladu a sledování verzí napříč systémy správy dokumentů.

## Proč detekovat verzi PDF v Javě?
Detekce verze PDF vám umožní ověřit, že soubor bude správně vykreslen v cílovém prohlížeči a že splňuje požadavky následného zpracování. Znalost, zda je PDF verze 1.4, 1.7 nebo novější, vám pomůže vynutit pravidla kompatibility před archivací, publikací nebo konverzí dokumentu.

## Požadavky
- **Java Development Kit (JDK)** 8 nebo vyšší.  
- **Maven** pro správu závislostí (nebo můžete JAR stáhnout přímo).  
- Základní znalost Java I/O souborů.  

## Nastavení GroupDocs.Metadata pro Javu

### Nastavení Maven
Přidejte úložiště a závislost do vašeho `pom.xml`:

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

#### Kroky získání licence
- **Free trial** – začněte experimentovat bez nákladů.  
- **Temporary license** – prodlužte zkušební verzi podle potřeby.  
- **Purchase** – získejte plnofunkční licenci pro produkční použití.  

## Základní inicializace a nastavení
Třída `Metadata` je vstupním bodem pro práci se soubory PDF v GroupDocs.Metadata. Reprezentuje kontejner, který vám poskytuje přístup ke čtení/zápisu vlastností dokumentu, informací o verzi a vlastních XMP dat.

Vytvořte instanci `Metadata`, která ukazuje na váš PDF soubor:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Nyní jste připraveni číst vlastnosti, detekovat verzi a aktualizovat metadata.

## Jak detekovat verzi PDF v Javě
Nahrajte svůj PDF pomocí `new Metadata("sample.pdf")` a zavolejte `getRootPackage().getVersion()` — metoda vrátí přesnou verzi PDF (např. 1.4, 1.7) v jediném volání. Tato přímá odpověď vám umožní rychle ověřit kompatibilitu před dalším zpracováním. Řetězec verze odráží úroveň specifikace PDF, kterou soubor dodržuje, což je klíčové pro kontrolu kompatibility.  
`getVersion()` vrací verzi PDF jako řetězec, např. „1.4“ nebo „1.7“.

### Průvodce krok za krokem
1. **Otevřete PDF** – vytvořte instanci objektu `Metadata` (viz inicializace výše).  
2. **Přístup k PDF‑specifickému kořenovému balíčku** – zavolejte `metadata.getRootPackage()`.  
3. **Získejte verzi** – zavolejte `pdfRoot.getVersion()`; vrácený řetězec obsahuje číslo verze.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Tip:** Použijte hodnotu `version` k vynucení kontrol kompatibility před zpracováním dávky PDF souborů.

#### Řešení problémů
- Ověřte cestu k souboru; nesprávná cesta vyvolá `FileNotFoundException`.  
- Ujistěte se, že verze GroupDocs.Metadata odpovídá vaší JDK (příklad používá 24.12).  

## Jak číst vlastnosti PDF v Javě
`DocumentInfo` poskytuje přístup k standardním polím metadat PDF bez načítání celého dokumentu. Třída `DocumentInfo` poskytuje přístup k standardním vlastnostem PDF, jako jsou autor, název a datum vytvoření. Jedná se o lehký obal, který čte metadata bez načítání celého dokumentu do paměti.

Vytvořte instanci `DocumentInfo` z otevřeného objektu `Metadata`:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

Poté můžete volat gettery jako `getAuthor()`, `getTitle()` a `getCreationDate()`, abyste získali hodnoty.

## Jak aktualizovat metadata PDF v Javě
Nahrajte PDF (stejně jako výše), získejte balíček `DocumentInfo`, upravte požadovaná pole a uložte změny. Operace přepíše existující blok metadat a zároveň zachová zbytek dokumentu. Po úpravě polí volání `save()` zapíše změny zpět do souboru a zachová obsahové streamy.

Třída `DocumentInfo` je objektem GroupDocs.Metadata pro úpravu vlastností na úrovni PDF, jako jsou autor, název, předmět a vlastní XMP pole.

Aktualizujte pole metadat:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Poznámka:** Volání setterů následují stejný vzor jako dříve ukázané gettery, což činí API intuitivním a konzistentním.

#### Časté úskalí
- Pokud se pokusíte upravit metadata v PDF, který nemá cílovou vlastnost, vrátí se `null` — vždy před nastavením nové hodnoty zkontrolujte, zda není `null`.  
- Velké PDF mohou vyžadovat zvýšenou velikost haldy JVM; sledujte využití paměti během dávkových aktualizací.

## Praktické příklady použití
1. **Compliance audits** – Ověřte, že všechny PDF splňují minimální verzi (např. 1.7) před právním podáním.  
2. **Automated archiving** – Označte PDF autorem, oddělením a datem vytvoření pro snadnější vyhledávání.  
3. **Document management integration** – Obohaťte PDF o vlastní vlastnosti, které mohou indexovat platformy DMS.  
4. **Report generation** – Vložte informaci o verzi do automaticky generovaných reportů.  
5. **Cross‑platform testing** – Detekujte nesoulady verzí, které mohou způsobit problémy s vykreslováním ve starších prohlížečích.  

## Tipy pro výkon
- **Use try‑with‑resources** (jak je ukázáno) k automatickému uzavření objektů `Metadata`.  
- **Batch process** více souborů ve smyčce pro snížení režie.  
- **Monitor heap** u velmi velkých PDF; zvažte zpracování po částech, pokud narazíte na limity paměti.  
- **GroupDocs.Metadata supports 50+ input and output formats** a může číst metadata z PDF s několika stovkami stránek bez načítání celého souboru do paměti, což poskytuje vysoký výkon na standardním serverovém hardware.  

## Často kladené otázky
**Q: Mohu aktualizovat metadata v PDF chráněných heslem?**  
A: Ano, ale musíte při vytváření objektu `Metadata` zadat heslo.

**Q: Podporuje GroupDocs.Metadata vlastní XMP vlastnosti?**  
A: Rozhodně. Můžete číst a zapisovat vlastní XMP pole pomocí stejného API.

**Q: Je možné změnit samotnou verzi PDF?**  
A: Knihovna může verzi zobrazit; její změna vyžaduje uložení dokumentu s jiným profilovým nastavením verze, což je podporováno pomocí dalších možností uložení.

**Q: Co se stane, pokud PDF nemá žádná existující metadata?**  
A: Gettery vrátí `null`. Můžete bezpečně volat settery k vytvoření nových záznamů metadat.

**Q: Existují nějaká omezení licence pro komerční použití?**  
A: Pro produkční nasazení je vyžadována komerční licence; zkušební verze je omezena na evaluační účely.

---
**Poslední aktualizace:** 2026-08-05  
**Testováno s:** GroupDocs.Metadata 24.12 pro Javu  
**Autor:** GroupDocs

## Související tutoriály
- [Efektivní aktualizace metadat PDF pomocí GroupDocs.Metadata v Javě pro správu dokumentů](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Mistrovství správy metadat: Detekce vlastností dokumentu a stavu šifrování s GroupDocs.Metadata pro Javu](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Vytvoření náhledu dokumentu v Javě – tutoriály GroupDocs.Metadata](/metadata/java/document-formats/)