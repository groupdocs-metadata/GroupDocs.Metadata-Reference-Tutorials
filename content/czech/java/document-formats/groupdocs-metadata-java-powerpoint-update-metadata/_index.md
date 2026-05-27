---
date: '2026-05-27'
description: Zjistěte, jak nastavit CreatedTime PPTX v Javě pomocí závislosti GroupDocs
  Maven pro aktualizaci metadat PowerPointu, včetně toho, jak změnit datum vytvoření
  PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Nastavte CreatedTime PPTX v Javě pomocí závislosti GroupDocs Maven
type: docs
url: /cs/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Nastavte CreatedTime PPTX v Javě pomocí GroupDocs.Metadata

Přesná metadata jsou nezbytná pro soulad a vyhledatelnost v moderních pracovních postupech s dokumenty. S **GroupDocs.Metadata** můžete programově **nastavit CreatedTime PPTX v Javě**, což vám umožní **změnit datum vytvoření PPTX** spolu s dalšími vestavěnými vlastnostmi, jako je autor nebo společnost. Tento tutoriál vás provede nastavením Maven, inicializací API, aktualizací metadat a uložením upravené prezentace — vše s jasným, připraveným k produkci kódem.

## Rychlé odpovědi
- **Která knihovna aktualizuje metadata PowerPoint v Javě?** GroupDocs.Metadata přes závislost GroupDocs Maven.  
- **Mohu nastavit vlastnost PPTX CreatedTime?** Ano — použijte `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Je pro produkci vyžadována licence?** Zkušební verze funguje pro hodnocení; komerční licence je povinná pro nasazení do produkce.  
- **Jaký nástroj pro sestavení příklad používá?** Maven (můžete také stáhnout JAR ručně).  
- **Podporuje API Java 8 a novější?** Rozhodně — GroupDocs.Metadata cílí na Java 8+.

## Co je GroupDocs Maven závislost?
**GroupDocs Maven závislost** je položka v Maven‑kompatibilním repozitáři, která stáhne nejnovější knihovnu GroupDocs.Metadata do vašeho Java projektu. Zjednodušuje správu závislostí automatickým řešením tranzitivních knihoven, zajišťuje, že vždy používáte nejnovější a nejbezpečnější verzi, a eliminuje potřebu ručního stahování JAR souborů nebo sledování verzí.

## Proč použít GroupDocs.Metadata ke změně data vytvoření PPTX?
GroupDocs.Metadata umožňuje automatizované, připravené na dávkové zpracování aktualizace časových razítek vytvoření PPTX, což zajišťuje, že každá prezentace splňuje firemní politiky nebo právní požadavky. Programovým nastavením vlastnosti CreatedTime se vyhnete ruční úpravě, snížíte lidské chyby a můžete změnu integrovat do CI/CD pipeline nebo migračních skriptů pro plynulou správu dokumentů.

## Předpoklady
- Nainstalována Java 8 nebo novější.  
- IDE jako IntelliJ IDEA nebo Eclipse.  
- Maven pro správu závislostí.  
- Přístup k zkušební verzi GroupDocs nebo zakoupené licenci.

## Jak nastavit PPTX CreatedTime v Javě?

Třída `Metadata` představuje dokument a poskytuje přístup k jeho vlastnostem metadat.

Načtěte svůj PowerPoint soubor pomocí `new Metadata("presentation.pptx")`, získejte kořenový balíček, zavolejte `setCreatedTime` s požadovaným `java.util.Date` a nakonec vyvolejte `save` pro zápis změn. Tento end‑to‑end tok upravuje datum vytvoření při zachování veškerého obsahu snímků a dalších vlastností.

### Nastavení Maven
Přidejte repozitář GroupDocs a závislost metadata do vašeho `pom.xml`:

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

> **Tip:** Udržování čísla verze aktuální zajišťuje, že získáte nejnovější opravy chyb a vylepšení výkonu.

### Přímé stažení (pokud nechcete používat Maven)

Alternativně stáhněte nejnovější JAR z [vydání GroupDocs.Metadata pro Java](https://releases.groupdocs.com/metadata/java/).

#### Získání licence

Začněte s bezplatnou zkušební verzí nebo požádejte o dočasnou licenci pro vyhodnocení GroupDocs.Metadata. Pro produkční použití zakupte licenci prostřednictvím [oficiálního webu GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Základní inicializace a nastavení

Jakmile je knihovna na classpath, můžete vytvořit instanci `Metadata`, která ukazuje na váš PowerPoint soubor:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

## Průvodce krok za krokem pro aktualizaci vestavěných metadat

### Krok 1: Načtení dokumentu prezentace

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Načtení souboru vytvoří spojení, které vám umožní číst nebo zapisovat metadata.

### Krok 2: Přístup ke kořenovému balíčku prezentace

Objekt `root` poskytuje přístup k hlavnímu balíčku prezentace a jejím vestavěným vlastnostem.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

### Krok 3: Aktualizace vestavěných vlastností dokumentu (včetně data vytvoření)

`setCreatedTime` přiřadí dokumentu nový časový razítko vytvoření.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

### Krok 4: Uložení aktualizované prezentace

`save` zapíše upravená metadata zpět do souboru.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

## Tipy pro řešení problémů
- **Soubor nenalezen:** Zkontrolujte znovu vstupní cestu a oprávnění k souboru.  
- **Neshoda verzí:** Ujistěte se, že verze `groupdocs-metadata` odpovídá vašemu Java runtime.  
- **Vlastnost se neaktualizuje:** Ověřte, že voláte `setCreatedTime` (nebo příslušný setter) před vyvoláním `save`.

## Praktické aplikace
1. **Firemní branding:** Automaticky vložte správný název společnosti a kategorii do všech prezentací před distribucí.  
2. **Systémy správy dokumentů:** Obohaťte soubory PPTX o prohledávatelná metadata pro rychlejší vyhledávání.  
3. **Vzdělávací materiály:** Udržujte informace o autorovi a osnovách aktuální napříč přednáškovými slajdy.  
4. **Sledování spolupráce:** Zaznamenávejte jména přispěvatelů pro zachování odpovědnosti.  
5. **Integrace CMS:** Synchronizujte změny metadat s vaší platformou pro správu obsahu v reálném čase.

## Úvahy o výkonu
- **Dávkové zpracování:** Procházejte seznam souborů a kde je to možné, znovu použijte jedinou instanci `Metadata`.  
- **Správa paměti:** Vždy používejte try‑with‑resources (jak je ukázáno) pro rychlé uvolnění nativních zdrojů.  
- **Efektivní datové struktury:** Uložte aktualizace metadat do mapy před jejich aplikací, aby se snížil počet opakovaných volání.

## Často kladené otázky
**Q: Jaký je hlavní účel GroupDocs Maven závislosti?**  
A: Poskytuje pohodlný způsob, jak zahrnout nejnovější knihovnu GroupDocs.Metadata do Maven‑založených Java projektů.

**Q: Jak mohu nastavit datum vytvoření PPTX, aniž by to ovlivnilo jiné vlastnosti?**  
A: Použijte `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` před voláním `metadata.save()`.

**Q: Potřebuji licenci pro spuštění tohoto kódu ve vývoji?**  
A: Dočasná zkušební licence stačí pro vývoj a testování; plná licence je vyžadována pro produkci.

**Q: Mohu také aktualizovat vlastní pole metadat?**  
A: Ano — GroupDocs.Metadata podporuje jak vestavěné, tak vlastní vlastnosti prostřednictvím svého API.

**Q: Existuje způsob, jak vrátit změny, pokud udělám chybu?**  
A: Uchovejte kopii originálního souboru nebo si přečtěte existující hodnoty vlastností před jejich přepsáním, a v případě potřeby je obnovte.

## Zdroje
- [Dokumentace](https://docs.groupdocs.com/metadata/java/)
- [Reference API](https://apireference.groupdocs.com/metadata/java/)

---

**Poslední aktualizace:** 2026-05-27  
**Testováno s:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs  

---

## Související tutoriály
- [Aktualizace vlastních metadat v PowerPoint pomocí GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Jak aktualizovat metadata Word dokumentu pomocí GroupDocs.Metadata Java: Kompletní průvodce](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Efektivní aktualizace PDF metadat pomocí GroupDocs.Metadata v Javě pro správu dokumentů](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)