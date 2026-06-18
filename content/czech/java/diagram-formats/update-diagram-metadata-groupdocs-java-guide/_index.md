---
date: '2026-06-17'
description: Zjistěte, jak změnit čas vytvoření diagramu a automatizovat aktualizaci
  metadat pro soubory diagramů pomocí GroupDocs.Metadata v Javě.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Změna času vytvoření diagramu v metadatech pomocí GroupDocs Java
type: docs
url: /cs/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Změna času vytvoření diagramu v metadatech pomocí GroupDocs Java

V tomto krok‑za‑krokem tutoriálu se dozvíte, jak **změnit čas vytvoření diagramu** a aktualizovat další vestavěné vlastnosti souborů diagramů pomocí knihovny GroupDocs.Metadata pro Java. Automatizace těchto změn šetří hodiny ruční úpravy, zajišťuje konzistentní časová razítka napříč vaším úložištěm a umožňuje okamžité vyhledávání diagramů v jakémkoli systému pro správu dokumentů.

## Rychlé odpovědi
- **Jaký je hlavní cíl?** Změnit čas vytvoření diagramu a další metadata v souborech diagramů.  
- **Kterou knihovnu mám použít?** GroupDocs.Metadata pro Java.  
- **Potřebuji licenci?** Bezplatná zkušební verze stačí pro testování; plná licence je vyžadována pro produkci.  
- **Mohu hromadně zpracovávat mnoho diagramů?** Ano – zabalte stejnou logiku do smyčky nebo paralelního proudu.  
- **Jaká verze Javy je požadována?** JDK 8 nebo vyšší.

## Co je „změna času vytvoření diagramu“ v metadatech diagramu?
Změna času vytvoření přepíše původní časové razítko uložené uvnitř souboru diagramu (např. VDX nebo VSDX) novou hodnotou data‑času. To vám umožní sladit metadata souboru se skutečným datem zpracování nebo archivace místo původního časového razítka autora, což je nezbytné pro auditní stopy a přesné výsledky vyhledávání.

## Proč automatizovat aktualizaci metadat pro diagramy?
Automatizace metadat zajišťuje, že každý diagram dodržuje stejné standardy pojmenování, kategorizace a časových razítek bez lidské chyby. Také urychluje hromadné migrace, snižuje riziko nesouladu a zlepšuje vyhledatelnost v podnikových DMS platformách – šetří až 70 % ruční práce ve velkých projektech.

## Požadavky
- **Java Development Kit (JDK) 8+** nainstalovaný na vašem počítači.  
- **IDE** jako IntelliJ IDEA nebo Eclipse.  
- **Maven** (nebo ruční správa JAR) pro správu závislostí.  
- Základní znalost Java tříd, metod a zpracování výjimek.

### Požadované knihovny a závislosti
Přidejte následující repozitář a závislost do souboru `pom.xml`, pokud používáte Maven:

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
Pokud dáváte přednost přímému stažení, navštivte [GroupDocs.Metadata pro Java – vydání](https://releases.groupdocs.com/metadata/java/) a získejte nejnovější verzi.

### Nastavení prostředí
- JDK 8 nebo novější.  
- IntelliJ IDEA, Eclipse nebo jakékoli Java‑kompatibilní IDE.  

### Předpokládané znalosti
Porozumění syntaxi Javy a základnímu souborovému I/O usnadní tutoriál, ale kroky jsou vysvětleny jednoduchým jazykem.

## Nastavení GroupDocs.Metadata pro Java
### Pokyny k instalaci
**Uživatelé Maven:** Výše uvedený úryvek automaticky přidá repozitář a požadovaný JAR.  
**Uživatelé přímého stažení:** Po stažení JAR z [GroupDocs](https://releases.groupdocs.com/metadata/java/), přidejte jej do classpath vašeho projektu.

### Získání licence
- **Bezplatná zkušební verze:** Prozkoumejte knihovnu zdarma.  
- **Dočasná licence:** Získejte dočasnou licenci pro rozšířené testování [zde](https://purchase.groupdocs.com/temporary-license/).  
- **Koupě:** Získejte plnou licenci pro produkční prostředí.

### Základní inicializace
`Metadata` je hlavní třída představující kontejner metadat dokumentu a poskytuje čtení/zápis ke všem vestavěným vlastnostem. Pro zahájení používání GroupDocs.Metadata importujte třídu a otevřete soubor diagramu:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Po inicializaci knihovny můžete nyní upravit libovolnou vestavěnou vlastnost, včetně času vytvoření.

## Průvodce implementací
### Jak změnit čas vytvoření v souborech diagramů
V této sekci projdeme každý krok potřebný k **změně času vytvoření diagramu** a aktualizaci dalších běžných vlastností, jako jsou autor, společnost a kategorie. Proces zahrnuje načtení diagramu pomocí Metadata API, přístup k jeho kořenovému balíčku, nastavení požadovaných polí a nakonec uložení změn do nového souboru, aby originál zůstal nedotčený.

#### Krok 1: Načtení dokumentu diagramu
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Vysvětlení:* Konstruktor `Metadata` přijímá cestu k vašemu souboru diagramu. Blok try‑with‑resources zajišťuje, že soubor je po operaci řádně uzavřen.

#### Krok 2: Přístup ke kořenovému balíčku
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Vysvětlení:* Kořenový balíček poskytuje přímý přístup ke všem vestavěným polím metadat diagramu.

#### Krok 3: Nastavení vlastnosti Tvůrce
```java
root.getDocumentProperties().setCreator("test author");
```  
*Vysvětlení:* Přiřadí nové jméno autora. Nahraďte `"test author"` skutečným tvůrcem.

#### Krok 4: Změna času vytvoření
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Vysvětlení:* Tento řádek **mění čas vytvoření** na aktuální datum a čas systému. Můžete také zadat konkrétní instanci `Date`, pokud potřebujete vlastní časové razítko.

#### Krok 5: Definice informací o společnosti
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Vysvětlení:* Ukládá název společnosti spojený s diagramem – užitečné pro sledování v podniku.

#### Krok 6: Nastavení kategorie dokumentu
```java
root.getDocumentProperties().setCategory("test category");
```  
*Vysvětlení:* Kategorizuje soubor, pomáhá vám **aktualizovat kategorii diagramu** konzistentně napříč vaším úložištěm.

#### Krok 7: Přidání klíčových slov
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Vysvětlení:* Klíčová slova zlepšují vyhledatelnost; můžete uvést jakékoli termíny související s obsahem diagramu.

#### Krok 8: Uložení změn
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Vysvětlení:* Ukládá všechny úpravy do nového souboru, přičemž originál zůstane nedotčen.

### Časté problémy a řešení
- **Soubor nenalezen:** Ověřte vstupní cestu a ujistěte se, že přípona souboru odpovídá skutečnému formátu.  
- **Přístup odepřen:** Zkontrolujte oprávnění čtení/zápisu pro vstupní i výstupní adresáře.  
- **Neplatný formát data:** Použijte objekty `java.util.Date` nebo `java.time` kompatibilní s API.  

## Praktické aplikace
1. **Automatizace archivace dokumentů** – Při přesunu starých diagramů do archivu automaticky **změníte čas vytvoření diagramu** na datum archivace a nastavíte jednotnou kategorii.  
2. **Integrace se systémem správy verzí** – Udržujte časová razítka v souladu s commity v Gitu aktualizací času vytvoření při každém vydání.  
3. **Standardizace podnikového DMS** – Vynucujte firemní politiku pro autora, společnost a klíčová slova napříč všemi diagramovými aktivy.

## Úvahy o výkonu
- **Dávkové zpracování:** Zabalte výše uvedené kroky do smyčky pro zpracování desítek souborů v jednom běhu.  
- **Správa paměti:** Uvolněte každou instanci `Metadata` okamžitě (blok try‑with‑resources to provádí automaticky).  
- **Asynchronní provádění:** Pro velké dávky zvažte `CompletableFuture` pro paralelní provádění aktualizací bez blokování hlavního vlákna.  
- **Měřená schopnost:** GroupDocs.Metadata podporuje více než 30 formátů diagramů a může zpracovávat soubory až do 500 MB bez načítání celého dokumentu do paměti, poskytuje aktualizace za méně než 200 ms na soubor na typickém serverovém hardware.

## Závěr
Nyní víte, jak **změnit čas vytvoření diagramu** a aktualizovat další vestavěné vlastnosti metadat pro diagramové dokumenty pomocí GroupDocs.Metadata v Javě. Automatizací těchto kroků můžete udržovat konzistentní, vyhledatelnou a souladnou dokumentaci napříč vaší organizací.

**Další kroky**
- Experimentujte s dalšími formáty souborů podporovanými GroupDocs.Metadata (PDF, DOCX atd.).  
- Integrovat kód do CI/CD pipeline pro vynucení standardů metadat při každém sestavení.  

Připraveno to vyzkoušet? Navštivte [GroupDocs.Metadata pro Java – vydání](https://releases.groupdocs.com/metadata/java/) a začněte dnes implementovat vlastní automatizaci metadat.

---

**Poslední aktualizace:** 2026-06-17  
**Testováno s:** GroupDocs.Metadata 24.12  
**Autor:** GroupDocs  

## Často kladené otázky

**Q:** Mohu použít tento přístup s jinými formáty diagramů, jako je VSDX?  
**A:** Ano, stejné API funguje pro všechny formáty diagramů podporované GroupDocs.Metadata.

**Q:** Potřebuji licenci pro vývojové sestavení?  
**A:** Bezplatná zkušební verze stačí pro vývoj a testování; plná licence je vyžadována pro produkční nasazení.

**Q:** Jak mohu aktualizovat více vlastností najednou?  
**A:** Nastavte každou vlastnost na objekt `DocumentProperties` před voláním `metadata.save(...)`; knihovna je zapíše všechny najednou.

**Q:** Je bezpečné přepsat původní soubor?  
**A:** Doporučuje se uložit do nového souboru (jak je ukázáno) a nahradit originál až po potvrzení úspěšné aktualizace.

**Q:** Co když potřebuji nastavit vlastní datum vytvoření místo aktuálního času?  
**A:** Vytvořte `java.util.Date` (nebo `java.time` instanci) s požadovaným časovým razítkem a předávejte ji metodě `setTimeCreated`.

## Související tutoriály

- [Jak aktualizovat metadata diagramu v Javě pomocí GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Jak aktualizovat metadata autora DXF pomocí GroupDocs.Metadata pro Java – Kompletní průvodce](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Automatizujte aktualizace metadat v Javě podle data pomocí GroupDocs.Metadata pro efektivní správu souborů](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)