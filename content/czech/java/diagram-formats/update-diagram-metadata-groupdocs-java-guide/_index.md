---
date: '2026-01-19'
description: Naučte se, jak změnit čas vytvoření a automatizovat aktualizaci metadat
  pro soubory diagramů pomocí GroupDocs.Metadata v Javě.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Změna času vytvoření v metadatech diagramu pomocí GroupDocs Java
type: docs
url: /cs/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

 Změnaření** a další vestavěné vlastnosti v jediném opakovatelném kroku. Tento průvodce vás provede nastavením knihovny, aktualizací metadat diagramu a aplikací osvědčených tipů pro výkon, abyste mohli udržet své dokumenty konzistentní a vyhledávatelné.

## Quick Answers
- **Jaký je hlavní cíl?** Změnit čas vytvoření a další metadata v soubterou knihovnu mám použít?** GroupDocs.Metadata pro Java.  
- **Potřebuji licenci?** Bezplatná zkušební verze stačí pro testování; plná licence je vyžadována pro produkci.  
- **Mohu zpracovávat hromadně mnoho diagramů?** Ano – použijte stejný přístup uvnitř smyčky nebo paralelního proudu.  
- **Jaká verze Javy je požadována?** JDK 8 nebo vyšší.

## Co znamená „změnit čas vytvoření“ v metadatech diagramu?
Změna času vytvoření znamená přepsání původního časového razítka uloženého uvnitř souboru diagramu (např. VDX, VSDX) novým datem. To je užitečné, když potřebujete, aby metadata souboru odrážela skutečné datum zpracování místo původního data vytvoření.

## Proč automatizovat aktualizaci metadat pro diagramy?
- **Konzistence:** Zajišťuje, že každý soubor dodržuje stejné pravidla pojmenování a kategorizace.  
- **Vyhledatelnost:** Aktualizované klíčová slova a kategorie zlepšují vyhledávání dokumentů v DMS řešeních.  
- **Soulad:** Pomáhá splnit požadavky auditu tím, že zajišťuje přesné časové razítka.

## Prerequisites
- **Java Development Kit (JDK) 8+** nainstalován.  
- **IDE** jako IntelliJ IDEA nebo Eclipse.  
- **Maven** (nebo ruční správa JAR) pro správu závislostí.  
- Základní znalost Java tříd, metod a zpracování výjimek.

### Required Libraries and Dependencies
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
Pokud dáváte přednost přímému stažení, navštivte [vydání GroupDocs.Metadata pro Java](https://releases.groupdocs.com/metadata/java/), abyste získali nejnovější verzi.

### Environment Setup
- JDK 8 nebo novější.  
- IntelliJ IDEA, Eclipse nebo jakékoli Java‑kompatibilní IDE.  

### Knowledge Prerequisites
Porozumění syntaxi Javy a základnímu souborovému I/O usnadní tutoriál, ale kroky jsou vysvětleny jednoduchým jazykem.

## Setting Up GroupDocs.Metadata for Java
### Installation Instructions
**Maven Users:** Výše uvedený úryvek přidá repozitář a požadovaný JAR automaticky.  
**Direct Download Users:** Po stažení JARu z [GroupDocs](https://releases.groupdocs.com/metadata/java/), přidejte jej do classpath vašeho projektu.

### License Acquisition
- **Bezplatná zkušební verze:** Prozkoumejte knihovnu bez nákladů.  
- **Dočasná licence:** Získejte dočasnou licenci pro rozšířené testování [zde](https://purchase.groupdocs.com/temporary-license/).  
- **Nákup:** Získejte plnou licenci pro produkční prostředí.

### Basic Initialization
Chcete‑li začít používat GroupDocs.Metadata, importujte třídu a otevřete soubor diagramu:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Po inicializaci knihovny můžete nyní upravit libovolnou vestavěnou vlastnost, včetně času vytvoření.

## Implementation Guide
### How to change creation time in diagram files
V této sekci projdeme každý krok potřebný k **změně času vytvoření** a aktualizaci dalších běžných vlastností, jako je autor, společnost a kategorie.

#### Step 1: Load the Diagram Document
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*Explanation:* Konstruktor `Metadata` přijímá cestu k vašemu souboru diagramu. Blok try‑with‑resources zajišťuje, že soubor bude po operaci řádně uzavřen.

#### Step 2: Access the Root Package
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*Explanation:* Kořenový balíček poskytuje přímý přístup ke všem vestavěným polím metadat diagramu.

#### Step 3: Set the Creator Property
```java
root.getDocumentProperties().setCreator("test author");
```
*Explanation:* Přiřadí nový název autora. Nahraďte `"test author"` skutečným tvůrcem.

#### Step 4: **Change Creation Time**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Explanation:* Tento řádek **změní čas vytvoření** na aktuální datum a čas systému. Můžete také předat konkrétní instanci `Date`, pokud potřebujete vlastní časové razítko.

#### Step 5: Define Company Information
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Explanation:* Ukládá název společnosti spojené s diagramem – užitečné pro sledování v podniku.

#### Step 6: Set Document Category
```java
root.getDocumentProperties().setCategory("test category");
```
*Explanation:* Kategorizuje soubor, což vám pomáhá **aktualizovat kategorii diagramu** konzistentně napříč repozitářem.

#### Step 7: Add Keywords
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Explanation:* Klíčová slova zlepšují vyhledatelnost; můžete uvést libovolné termíny související s obsahem diagramu.

#### Step 8: Save Changes
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Explanation:* Uloží všechny úpravy do nového souboru, přičemž originál zůstane nedotčen.

### Common Pitfalls & Troubleshooting
- **Soubor nenalezen:** Ověřte vstupní cestu a ujistěte se, že přípona souboru odpovídá skutečnému formátu.  
- **Přístup odepřen:** Zkontrolujte oprávnění pro čtení/zápis v obou vstupních a výstupních adresářích.  
- **Neplatný formát data:** Použijte objekty `java.util.Date` nebo `java.time` kompatibilní s API.  

## Practical Applications
1. **Automatizace archivace dokumentů** – Při přesunu starých diagramů do archivu automaticky **změní čas vytvoření** na datum archivace a nastaví jednotnou kategorii.  
2. **Integrace s verzovacím systémem** – Udržujte časová razítka v souladu s Git commity aktualizací času vytvoření při každém vydání.  
3. **Standardizace podnikového DMS** – Vynutí firemní politiku pro autora, společnost a klíčová slova napříč všemi diagramovými aktivy.  

## Performance Considerations
- **Dávkové zpracování:** Zabalte výše uvedené kroky do smyčky pro zpracování desítek souborů najednou.  
- **Správa paměti:** Uvolněte každou instanci `Metadata` okamžitě (blok try‑with‑resources to provádí automaticky).  
- **Asynchronní provádění:** Pro velké dávky zvažte `CompletableFuture` pro paralelní spuštění aktualizací bez blokování hlavního vlákna.  

## Conclusion
Nyní víte, jak **změnit čas vytvoření** a aktualizovat další vestavěné vlastnosti metadat pro diagramové dokumenty pomocí GroupDocs.Metadata v Javě. Automatizací těchto kroků můžete udržet konzistentní, vyhledávatelnou a souladnou dokumentaci napříč celou organizací.

**Další kroky**
- Experimentujte s dalšími formáty souborů podporovanými GroupDocs.Metadata (PDF, DOCX, atd.).  
- Integrujte kód do CI/CD pipeline pro vynucení standardů metadat při každém sestavení.  

Jste připraveni to vyzkoušet? Navštivte [vydání GroupDocs.Metadata pro Java](https://releases.groupdocs.com/metadata/java/) a začněte ještě dnes implementovat vlastní automatizaci metadat.

---

**Last Updated:** 2026-01-19  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs  

## Frequently Asked Questions

**Q:** Mohu tento přístup použít s jinými formáty diagramů, jako je VSDX?  
**A:** Ano, stejné API funguje pro všechny formáty diagramů podporované GroupDocs.Metadata.

**Q:** Potřebuji licenci pro vývojové sestavení?  
**A:** Bezplatná zkušební verze stačí pro vývoj a testování; plná licence je vyžadována pro produkční nasazení.

**Q:** Jak mohu aktualizovat více vlastností najednou?  
**A:** Nastavte každou vlastnost na objektu `DocumentProperties` před voláním `metadata.save(...)`; knihovna zapíše všechny najednou.

**Q:** Je bezpečné přepsat původní soubor?  
**A:** Doporučuje se uložit do nového souboru (jak je ukázáno), aby nedošlo ke ztrátě dat, a poté případně nahradit originál.

**Q:** Co když potřebuji nastavit vlastní datum vytvoření místo aktuálního času?  
**A:** Vytvořte `java.util.Date` (nebo `java.time` instanci) s požadovaným časovým razítkem a předávejte ji metod