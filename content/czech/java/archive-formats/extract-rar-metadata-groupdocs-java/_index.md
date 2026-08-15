---
date: '2026-06-22'
description: Zjistěte, jak získat komprimovanou velikost v Java při extrahování metadat
  RAR pomocí GroupDocs.Metadata pro Java. Průvodce krok za krokem, ukázky kódu a osvědčené
  postupy.
keywords:
- get compressed size java
- groupdocs metadata java
- extract rar metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  headline: Get Compressed Size Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  name: Get Compressed Size Java with GroupDocs.Metadata
  steps:
  - name: Initialize the Metadata object
    text: Create a `Metadata` instance by providing the path to the RAR file. This
      object represents the archive in memory and gives you access to its internal
      structure.
  - name: Obtain the root package of the RAR archive
    text: Call `metadata.getRootPackage()` to retrieve the top‑level package that
      contains all entries. The returned `ArchivePackage` lets you enumerate files
      and folders inside the archive.
  - name: Retrieve total entry count
    text: Use `archivePackage.getEntries().size()` to know how many items are stored.
      Knowing the count helps you allocate progress‑tracking structures for batch
      jobs.
  - name: Iterate over each file and read its properties
    text: Loop through `archivePackage.getEntries()`. For every entry that represents
      a file (not a folder), call `entry.getCompressedSize()` to obtain its compressed
      size in bytes. You can also read `entry.getOriginalSize()` if you need the uncompressed
      size for ratio calculations. **Troubleshooting Tips** -
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java is a library that enables reading, updating,
      and managing metadata across more than 50 file formats, including RAR, ZIP,
      and 7z, without requiring file extraction.
    question: What is GroupDocs.Metadata for Java?
  - answer: Visit the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)
      to acquire a temporary or permanent license; a free trial is available for development.
    question: How do I obtain a license for full access?
  - answer: Yes, the same API supports ZIP, 7z, and several other archive formats,
      allowing a unified codebase for all archive metadata tasks.
    question: Can I use GroupDocs.Metadata with other archive types besides RAR?
  - answer: The main issues are memory consumption and file‑handle limits; mitigate
      them by processing entries one‑by‑one and closing the `Metadata` object promptly.
    question: What are common pitfalls when handling large RAR files?
  - answer: The [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/)
      provides assistance from both the vendor’s engineers and the community.
    question: Where can I get support if I encounter problems?
  type: FAQPage
title: Získání komprimované velikosti v Java pomocí GroupDocs.Metadata
type: docs
url: /cs/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# Získání komprimované velikosti v Javě pomocí GroupDocs.Metadata

V moderních datově‑centrických aplikacích je **get compressed size java** častým požadavkem, když potřebujete zkontrolovat velikost souborů uložených uvnitř archivů RAR, aniž byste je rozbalovali. Ať už vytváříte nástroj pro ověřování záloh, systém pro správu digitálních aktiv nebo portál pro sdílení souborů, čtení těchto metadat šetří čas i systémové zdroje. Tento průvodce vás provede používáním GroupDocs.Metadata pro Javu k rychlému, bezpečnému a s minimálním kódem získání komprimované velikosti každé položky.

## Rychlé odpovědi
- **Jaká knihovna je potřeba?** GroupDocs.Metadata for Java  
- **Mohu získat komprimované velikosti?** Ano – zavolejte `rarFile.getCompressedSize()` na každém záznamu  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována plná licence  
- **Která verze Javy je podporována?** Java 8+ (jakékoli prostředí kompatibilní s Mavenem)  
- **Je možný hromadný (batch) processing?** Rozhodně – projděte složku s RAR soubory a znovu použijte stejný kód  
- **Jak zacházet s velkými archivy?** Zpracovávejte položky po jedné a po dokončení zavřete objekt metadata  

## Co je “get compressed size java” a proč je důležité?
**Get compressed size java** čte velikost souboru tak, jak je uložena uvnitř kontejneru RAR. Tato hodnota vám říká, kolik místa soubor po kompresi zabírá, což vám umožní ověřovat kompresní poměry, odhadovat časy přenosu a v inventárních zprávách uvádět jak původní, tak komprimovanou velikost.

## Jak získat komprimovanou velikost v Javě z archivů RAR?
Načtěte archiv RAR pomocí GroupDocs.Metadata, projděte jeho položky a na každém souboru zavolejte metodu `getCompressedSize()`. Tento přístup čte pouze hlavičku archivu, takže nedochází k rozbalování ani načítání celého souboru, což udržuje využití paměti pod 5 MB i u archivů o velikosti stovek megabajtů.

### Krok 1: Inicializace objektu Metadata
Vytvořte instanci `Metadata` zadáním cesty k souboru RAR. Tento objekt představuje archiv v paměti a poskytuje vám přístup k jeho vnitřní struktuře.

### Krok 2: Získání kořenového balíčku archivu RAR
Zavolejte `metadata.getRootPackage()` pro získání balíčku nejvyšší úrovně, který obsahuje všechny položky. Vrácený `ArchivePackage` vám umožní vyjmenovat soubory a složky uvnitř archivu.

### Krok 3: Získání celkového počtu položek
Použijte `archivePackage.getEntries().size()` k zjištění, kolik položek je uloženo. Znalost počtu vám pomůže alokovat struktury pro sledování postupu u hromadných úloh.

### Krok 4: Procházení každého souboru a čtení jeho vlastností
Projděte `archivePackage.getEntries()`. Pro každou položku, která představuje soubor (ne složku), zavolejte `entry.getCompressedSize()` a získáte jeho komprimovanou velikost v bajtech. Pokud potřebujete nekomprimovanou velikost pro výpočet poměru, můžete také přečíst `entry.getOriginalSize()`.

**Tipy pro řešení problémů**  
- Ověřte, že `rarFilePath` ukazuje na existující soubor RAR.  
- Ujistěte se, že aplikace má oprávnění ke čtení archivu.  
- Pokud narazíte na chybu „nepodporovaný formát“, ověřte, že verze RAR je kompatibilní s GroupDocs.Metadata (podporuje RAR 4 a RAR 5).  

## Proč používat GroupDocs.Metadata pro soubory RAR?
GroupDocs.Metadata poskytuje vysoceúrovňové API, které čte hlavičky archivů bez rozbalování souborů, a poskytuje rychlý přístup k vlastnostem jako komprimovaná velikost, původní velikost a časová razítka. Funguje s formáty RAR 4 a RAR 5, efektivně pracuje s velkými archivy a abstrahuje formátově specifické detaily, takže vývojáři mohou psát jednotný kód napříč typy archivů.

## Běžné případy použití
1. **Systémy správy dat** – automaticky katalogizovat obsah archivů pro prohledávatelné inventáře.  
2. **Správa digitálních aktiv** – obohatit mediální knihovny o podrobnosti na úrovni archivu, jako je komprimovaná velikost.  
3. **Ověřování záloh** – porovnat uložené komprimované velikosti s očekávanými hodnotami pro detekci poškození.  
4. **Platformy pro sdílení souborů** – zobrazit souhrny archivů bez úplného rozbalení souborů, což zlepšuje uživatelský zážitek.  

## Úvahy o výkonu
- **Přistupujte jen k potřebným vlastnostem** – vyhněte se volání těžkých metod, pokud potřebujete jen názvy souborů a velikosti.  
- **Uvolněte objekty metadata** – po zpracování zavolejte `metadata.close()`, aby se uvolnily nativní zdroje.  
- **Hromadné zpracování** – zpracovávejte více souborů RAR ve smyčce, opakovaně používejte stejnou JVM pro snížení režie při spuštění.  

## Často kladené otázky

**Q: Co je GroupDocs.Metadata pro Javu?**  
A: GroupDocs.Metadata pro Javu je knihovna, která umožňuje číst, aktualizovat a spravovat metadata ve více než 50 formátech souborů, včetně RAR, ZIP a 7z, aniž by bylo nutné soubory rozbalovat.

**Q: Jak získám licenci pro plný přístup?**  
A: Navštivte [stránku nákupu GroupDocs](https://purchase.groupdocs.com/temporary-license/), kde si můžete zakoupit dočasnou nebo trvalou licenci; pro vývoj je k dispozici bezplatná zkušební verze.

**Q: Mohu používat GroupDocs.Metadata i s jinými typy archivů než RAR?**  
A: Ano, stejné API podporuje ZIP, 7z a několik dalších formátů archivů, což umožňuje jednotnou kódovou základnu pro všechny úkoly související s metadaty archivů.

**Q: Jaké jsou běžné úskalí při práci s velkými soubory RAR?**  
A: Hlavními problémy jsou spotřeba paměti a limity počtu otevřených souborových deskriptorů; zmírněte je zpracováním položek po jedné a včasným uzavřením objektu `Metadata`.

**Q: Kde mohu získat podporu, pokud narazím na problémy?**  
A: [Bezplatné fórum podpory GroupDocs](https://forum.groupdocs.com/c/metadata/) poskytuje pomoc jak od inženýrů dodavatele, tak od komunity.

## Zdroje
- **Dokumentace**: [GroupDocs Metadata Java Documentation](https://docs.groupdocs.com/metadata/java/)  
- **API Reference**: [GroupDocs API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Stáhnout**: [Latest Version Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [Source Code on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Bezplatná podpora**: [GroupDocs Forum](https://forum.groupdocs.com/c/metadata/)  
- **Vydání**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)  
- **Komplexní dokumentace**: [comprehensive documentation](https://docs.groupdocs.com/metadata/java/)  

## Závěr
Nyní víte, **jak používat GroupDocs.Metadata** k extrakci komplexních metadat z archivů RAR, včetně toho, **jak získat komprimovanou velikost v Javě** pro každou položku. Začleňte tento postup do svých projektů, abyste zvýšili možnosti správy dat, zlepšili ověřování záloh a obohatili vyhledávání souborů bez nutnosti úplného rozbalení.

### Další kroky
Prozkoumejte další funkce, jako je aktualizace komentářů položek nebo extrakce kontrolních součtů v oficiální dokumentaci, a zvažte kombinaci tohoto získávání metadat s vaším stávajícím indexovacím procesem pro plně prohledávatelný archivní repozitář.

**Poslední aktualizace:** 2026-06-22  
**Testováno s:** GroupDocs.Metadata 24.12 for Java  
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

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata object
        Metadata metadata = new Metadata("path/to/your/document");
        System.out.println("Metadata initialized successfully.");
    }
}
```

```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

```java
// Iterate over each file within the RAR archive
for (RarFile rarFile : root.getRarPackage().getFiles()) {
    // Print file name, compressed size, modification date time, and uncompressed size
    System.out.println("File Name: " + rarFile.getName());
    System.out.println("Compressed Size: " + rarFile.getCompressedSize());
    System.out.println("Modification Date Time: " + rarFile.getModificationDateTime());
    System.out.println("Uncompressed Size: " + rarFile.getUncompressedSize());
}
```

## Související tutoriály

- [Extrahovat zip komentáře java pomocí GroupDocs.Metadata – Průvodce](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)
- [Aktualizovat ZIP komentář Java – Jak aktualizovat komentáře ZIP archivu pomocí GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Jak číst soubory TAR a extrahovat metadata pomocí GroupDocs.Metadata pro Javu](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)