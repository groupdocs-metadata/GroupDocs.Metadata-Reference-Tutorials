---
date: '2026-03-22'
description: Naučte se, jak změnit datum vytvoření souboru Excel a aktualizovat metadata
  Excelu pomocí GroupDocs.Metadata pro Javu. Postupujte podle tohoto krok‑za‑krokem
  průvodce, abyste přidali klíčová slova do Excelu a upravili vlastnosti dokumentu.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Změna data vytvoření Excelu pomocí GroupDocs.Metadata v Javě
type: docs
url: /cs/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Změna data vytvoření Excelu pomocí GroupDocs.Metadata v Javě

V moderních datově řízených prostředích může **změna data vytvoření Excelu** a udržování dalších metadat aktuálních dramaticky zlepšit organizaci dokumentů, vyhledatelnost a soulad s předpisy. Ať už pracujete s finančními zprávami, sledovači projektů nebo archivními daty, přesná metadata zajišťují, že správní lidé najdou správné soubory ve správný čas. Tento tutoriál vás provede používáním knihovny GroupDocs.Metadata k **změně data vytvoření Excelu**, **přidání klíčových slov do Excelu** a **úpravě vlastností dokumentu Excel** v Java aplikaci.

## Rychlé odpovědi
- **Mohu změnit datum vytvoření souboru Excel?** Ano, pomocí `setCreatedTime` z GroupDocs.Metadata.  
- **Která knihovna podporuje aktualizaci metadat Excelu v Javě?** GroupDocs.Metadata pro Javu.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro hodnocení; pro produkci je vyžadována trvalá licence.  
- **Jaká verze Javy je vyžadována?** JDK 8 nebo vyšší.  
- **Mohu přidat vlastní klíčová slova do sešitu Excel?** Rozhodně—použijte `setKeywords` na vlastnostech dokumentu.

## Co je „změna data vytvoření Excelu“?
Změna data vytvoření Excelu znamená aktualizaci vestavěné vlastnosti *Created* uložené uvnitř souboru sešitu. Tato vlastnost je součástí standardních metadat Office Open XML a lze ji programově upravit, aniž by se měnil skutečný obsah listu.

## Proč používat GroupDocs.Metadata pro metadata Excelu?
GroupDocs.Metadata nabízí vysoce úrovňové, typově bezpečné API, které abstrahuje nízkoúrovňové zpracování XML vyžadované formátem Office Open XML. Umožňuje vám:

- **Aktualizovat základní vlastnosti** jako autor, společnost a datum vytvoření jedním voláním.  
- **Přidat klíčová slova do Excelu** pro zlepšení výsledků vyhledávání v SharePointu, OneDrive nebo lokálních souborových systémech.  
- **Upravit vlastnosti dokumentu Excel** bez otevření sešitu v Excelu, což šetří čas a zdroje.  

## Prerequisites
- Java Development Kit (JDK) 8 nebo novější.  
- IDE jako IntelliJ IDEA nebo Eclipse.  
- Základní znalost práce se soubory v Javě.  

## Nastavení GroupDocs.Metadata pro Javu

### Installation

Přidejte Maven repozitář a závislost GroupDocs.Metadata do vašeho `pom.xml`:

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

Alternativně můžete [stáhnout nejnovější verzi přímo](https://releases.groupdocs.com/metadata/java/), pokud dáváte přednost manuálnímu nastavení.

### License Acquisition

GroupDocs nabízí bezplatnou zkušební verzi pro hodnocení. Pro produkční použití získáte dočasnou nebo trvalou licenci od dodavatele. Navštivte [stránku nákupu GroupDocs](https://purchase.groupdocs.com/temporary-license/) pro podrobnosti.

#### Základní inicializace

Importujte potřebné třídy ve vašem Java zdrojovém souboru:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implementace krok za krokem

### Krok 1: Otevřít sešit Excel

Zadejte cestu ke zdrojovému sešitu a vytvořte instanci `Metadata`. Blok `try‑with‑resources` zajistí automatické uzavření souborového handle.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Krok 2: Aktualizovat vestavěné vlastnosti metadat

Nyní můžete **změnit datum vytvoření Excelu**, nastavit autora, společnost, kategorii a **přidat klíčová slova do Excelu**. Volání `new Date()` zachytí aktuální časové razítko, ale můžete poskytnout libovolný `java.util.Date`, který potřebujete.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Tip:** Používejte konzistentní pojmenovací konvenci pro klíčová slova (např. `project:Q2, finance, confidential`), aby byly budoucí vyhledávání efektivnější.

### Krok 3: Uložit aktualizovaný sešit

Zadejte výstupní cestu a uložte změny. Původní soubor zůstane nedotčený, což je užitečné pro auditní stopy.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Časté problémy a řešení

| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| **Chyby cesty k souboru** | Nesprávné relativní/absolutní cesty | Zkontrolujte `inputFilePath` a `outputFilePath`. Použijte `Paths.get(...)` pro platformově nezávislé cesty. |
| **Nekompatibilní verze knihovny** | Používáte starší verzi GroupDocs.Metadata, která nepodporuje metodu `setCreatedTime` | Aktualizujte na nejnovější verzi (jak je uvedeno v Maven úryvku). |
| **Chybějící licence** | Vypršela zkušební doba | Použijte dočasnou licenci nebo zakupte plnou licenci přes stránku nákupu. |
| **Vysoká spotřeba paměti při velkém sešitu** | Načítání obrovských souborů Excel spotřebovává haldu | Zpracovávejte soubory po dávkách a v případě potřeby zvyšte haldu JVM (`-Xmx`). |

## Často kladené otázky

**Q: Jaké verze Javy jsou podporovány GroupDocs.Metadata?**  
A: Java 8 a novější jsou plně podporovány.

**Q: Jak mám zacházet s výjimkami při aktualizaci metadat?**  
A: Zabalte kód do bloku `try‑catch` a zaznamenejte `MetadataException` pro zachycení jakýchkoli I/O nebo formátových chyb.

**Q: Mohu aktualizovat více souborů Excel najednou?**  
A: Ano, projděte kolekci cest k souborům, ale sledujte využití paměti při velkých dávkách.

**Q: Je možné vrátit změny provedené v metadatech?**  
A: Uchovejte zálohu původního sešitu před aplikací aktualizací a v případě potřeby jej obnovte.

**Q: Kde mohu najít podrobnější dokumentaci?**  
A: Viz oficiální příručka na [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Praktické aplikace

1. **Finanční audity** – Zaznamenávejte, kdo a kdy upravil sešit, čímž vytvoříte auditní stopu.  
2. **Projektové řízení** – Označte tabulky projektovými klíčovými slovy pro rychlé vyhledání.  
3. **Archivace dat** – Zachovejte původní data vytvoření a informace o společnosti pro soulad s předpisy.

## Tipy pro výkon

- Omezte operace s metadaty na běh, aby nedošlo k nadměrné spotřebě paměti.  
- Okamžitě uzavřete objekt `Metadata` (vzor `try‑with‑resources` to provádí automaticky).  
- U velmi velkých sešitů zvažte jejich zpracování na pozadí, aby UI zůstalo responzivní.

## Závěr

Nyní víte, jak **změnit datum vytvoření Excelu**, **přidat klíčová slova do Excelu** a **upravit vlastnosti dokumentu Excel** pomocí GroupDocs.Metadata v Javě. Tato schopnost vám umožní udržovat vaše tabulky dobře organizované, vyhledatelné a v souladu s interními zásadami správy. Dalším krokem je prozkoumat další funkce metadat, jako jsou vlastní vlastnosti nebo dávkové zpracování, abyste dále zefektivnili workflow správy dokumentů.

---

**Poslední aktualizace:** 2026-03-22  
**Testováno s:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs  

**Zdroje**
- [Dokumentace](https://docs.groupdocs.com/metadata/java/)
- [Reference API](https://reference.groupdocs.com/metadata/java/)
- [Stáhnout GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [GitHub repozitář](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/metadata/)
- [Dočasná licence](https://purchase.groupdocs.com/temporary-license/)