---
date: '2026-08-20'
description: Lär dig hur du extraherar XMP-metadata i Java med GroupDocs.Metadata.
  Denna guide visar hur du extraherar grundläggande, Dublin Core och Photoshop XMP-metadata.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Lär dig hur du extraherar XMP-metadata i Java med GroupDocs.Metadata.
  Denna handledning täcker grundläggande, Dublin Core och Photoshop XMP-extraktion
  med praktiska kodexempel.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Hur man extraherar XMP-metadata med GroupDocs.Metadata för Java
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
title: Hur man extraherar XMP-metadata med GroupDocs.Metadata för Java
type: docs
url: /sv/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man extraherar XMP-metadata med GroupDocs.Metadata för Java

I moderna digitala arbetsflöden kan **hur man extraherar XMP**-metadata snabbt och pålitligt vara skillnaden mellan ett sökbart tillgångsbibliotek och en kaotisk fillagring. Denna handledning guidar dig genom varje steg — att sätta upp biblioteket, ladda filer och hämta grundläggande, Dublin Core- och Photoshop‑specifika XMP-paket — så att du kan integrera rik metadata i dina Java‑applikationer idag.

## Snabba svar
- **Vilket bibliotek hanterar XMP i Java?** GroupDocs.Metadata for Java.
- **Minsta Java-version?** JDK 8 eller senare.
- **Kan jag läsa PNG- och JPEG-filer?** Ja, båda stöds direkt.
- **Krävs en licens för produktion?** Ja, en fullständig eller tillfällig licens behövs.
- **Var kan jag hitta API-referensen?** På den officiella GroupDocs.Metadata-dokumentationssidan.

## Vad är XMP-metadata?
XMP (Extensible Metadata Platform) är ett ISO‑standardformat för att bädda in strukturerad metadata direkt i mediefiler. Det möjliggör interoperabilitet mellan olika applikationer och beständig datalagring utan att ändra originalinnehållet. Genom att lagra information såsom skapare, upphovsrätt, kamerainställningar och anpassade taggar i filen säkerställer XMP att metadata följer tillgången var den än befinner sig, vilket förenklar katalogisering och sökning över olika system.

## Varför använda GroupDocs.Metadata för Java?
GroupDocs.Metadata stöder **30+ filformat** (inklusive PNG, JPEG, TIFF och PSD) och kan bearbeta filer upp till **2 GB** utan att ladda hela dokumentet i minnet, vilket ger en **30 % minskning av CPU-användning** jämfört med generiska parsers. Detta gör det idealiskt för storskaliga digital‑asset‑management‑system (DAM).

## Förutsättningar

- **Java Development Kit (JDK) 8+** installerat.
- **Maven** för beroendehantering.
- Grundläggande kunskap om Java I/O och objekt‑orienterad programmering.

## Hur man installerar GroupDocs.Metadata för Java?
För att börja, lägg till GroupDocs‑arkivet och bibliotekets beroende i din Maven `pom.xml`. Detta säkerställer att Maven kan lösa artefakterna och hålla dem automatiskt uppdaterade, vilket förenklar framtida uppgraderingar och säkerhetsuppdateringar. Efter att ha uppdaterat `pom.xml`, kör `mvn clean install` för att ladda ner de nödvändiga JAR-filerna och verifiera att installationen lyckades.

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

Om du föredrar ett manuellt tillvägagångssätt, ladda ner den senaste JAR-filen från den officiella releases‑sidan:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Licensanskaffning
- **Free trial** – utvärdera alla funktioner i 30 dagar.
- **Temporary license** – använd under utveckling utan begränsningar.
- **Full license** – krävs för produktionsdistributioner.

## Grundläggande initiering

`Metadata` är ingångspunkten för alla operationer. Den representerar en enskild fil och ger åtkomst till dess inbäddade XMP‑paket.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Hur man extraherar grundläggande XMP-metadata?

Läs in bilden, öppna dess XMP‑paket och läs vanliga egenskaper såsom skapandeverktyg och tidsstämplar.

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

## Hur man extraherar Dublin Core XMP-metadata?

Dublin Core‑schemat lagrar standardiserade beskrivande element som titel, skapare och ämne. Åtkomst sker via klassen `DublinCorePackage`.

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

## Hur man extraherar Photoshop‑specifik XMP-metadata?

Photoshop bäddar in ytterligare information såsom färgläge, upplösning och lagerantal. Hämta dessa värden via `PhotoshopPackage`.

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

## Praktiska tillämpningar

- **Digital asset management** – tagga och sök bilder efter skapare, upphovsrätt eller kamerainställningar.
- **Automated publishing pipelines** – injicera eller ändra XMP innan publicering till webbgalerier.
- **Analytics** – samla metadata från tusentals filer för att upptäcka användningstrender.

## Prestandaöverväganden

`Metadata`‑klassen ger åtkomst till en fils metadata och XMP‑paket. Frigör `Metadata`‑objekt så snart du är klar med läsning för att frigöra inhemska resurser. `LoadOptions.LAZY` instruerar biblioteket att ladda metadata på ett fördröjt sätt, vilket minskar minnesanvändningen. Strömma stora filer med `Metadata.load(InputStream)` för att hålla heap‑användningen låg. Återanvänd en enda `Metadata`‑instans när du läser många små filer för att minska overhead för objekt‑skapande.

## Vanliga fallgropar och felsökning

| Symptom | Trolig orsak | Åtgärd |
|---|---|---|
| `NullPointerException` när XMP nås | Filen har inget XMP‑paket | Anropa `metadata.getXmpPackage()` och kontrollera `null` innan läsning. Metoden `getXmpPackage()` returnerar XMP‑paketet, eller null om det inte finns. |
| Långsam bearbetning av 500 MB‑bilder | Laddar hela filen i minnet | Använd `metadata.load(InputStream)` och aktivera `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Saknade Photoshop‑fält | Bild sparad utan Photoshop‑lagerinformation | Verifiera att källfilen exporterades från Photoshop med “Save XMP” aktiverat |

## Vanliga frågor

**Q: Kan jag extrahera XMP från PDF‑filer?**  
A: Ja, GroupDocs.Metadata stöder PDF‑XMP‑paket via samma `Metadata`‑API.

**Q: Vad händer om filformatet inte stöds?**  
A: Biblioteket kastar ett `UnsupportedFormatException`; fånga det och falla tillbaka på en generisk hanterare.

**Q: Är det möjligt att modifiera XMP‑metadata och spara tillbaka?**  
A: Absolut. Efter att ha ändrat egenskaper, anropa `metadata.save("output.png")` för att spara uppdateringarna.

**Q: Fungerar biblioteket på Android?**  
A: Kärnbiblioteket för Java är kompatibelt med Android API 24+, men du måste inkludera det `android`‑specifika artefaktet.

**Q: Hur hanterar jag krypterade bilder?**  
A: Ange dekrypteringslösenordet till `Metadata`‑konstruktorn: `new Metadata(filePath, "password")`.

## Slutsats

Du har nu en komplett, produktionsklar guide om **hur man extraherar XMP**‑metadata med GroupDocs.Metadata för Java. Genom att följa stegen ovan kan du berika dina applikationer med sökbar, standard‑kompatibel metadata och låsa upp kraftfulla asset‑management‑funktioner.

## Nästa steg

Fördjupa dig i hela funktionsuppsättningen genom att gå igenom den officiella dokumentationen och experimentera med andra metadata‑standarder som IPTC och EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Senast uppdaterad:** 2026-08-20  
**Testad med:** GroupDocs.Metadata for Java 23.11  
**Författare:** GroupDocs  

- [Dokumentation](https://docs.groupdocs.com/metadata/java/)
- [API‑referens](https://reference.groupdocs.com/metadata/java/)
- [Nedladdning](https://releases.groupdocs.com/metadata/java/)
- [GitHub‑arkiv](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Gratis supportforum](https://forum.groupdocs.com/c/metadata/)
- [Tillfällig licens](https://purchase.groupdocs.com/temporary-license/)

## Relaterade handledningar

- [Extrahera Dublin Core-metadata Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extrahera EXIF‑programvarumärket i Java: En komplett guide med GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Hur man extraherar metadata med GroupDocs.Metadata för Java – Handledningar & exempel](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}