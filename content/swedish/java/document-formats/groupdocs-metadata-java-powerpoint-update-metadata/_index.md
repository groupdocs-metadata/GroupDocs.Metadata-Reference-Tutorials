---
date: '2026-05-27'
description: Lär dig hur du ställer in pptx CreatedTime i Java med hjälp av GroupDocs
  Maven-beroendet för att uppdatera PowerPoint-metadata, inklusive hur du ändrar PPTX:s
  skapelsedatum.
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
title: Ställ in PPTX CreatedTime i Java med GroupDocs Maven-beroende
type: docs
url: /sv/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Ställ in PPTX CreatedTime i Java med GroupDocs.Metadata

Korrekt metadata är avgörande för efterlevnad och upptäckbarhet i moderna dokumentarbetsflöden. Med **GroupDocs.Metadata** kan du programatiskt **ställa in PPTX CreatedTime i Java**, vilket gör att du kan **ändra PPTX:s skapelsedatum** tillsammans med andra inbyggda egenskaper som författare eller företag. Denna handledning guidar dig genom Maven‑inställning, initiering av API:et, uppdatering av metadata och sparande av den modifierade presentationen — allt med tydlig, produktionsklar kod.

## Snabba svar
- **Vilket bibliotek uppdaterar PowerPoint-metadata i Java?** GroupDocs.Metadata via GroupDocs Maven‑beroendet.  
- **Kan jag ställa in PPTX CreatedTime‑egenskapen?** Ja — använd `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Krävs en licens för produktion?** En provlicens fungerar för utvärdering; en kommersiell licens är obligatorisk för produktionsdistributioner.  
- **Vilket byggverktyg använder exemplet?** Maven (du kan också ladda ner JAR‑filen manuellt).  
- **Stöder API:et Java 8 och nyare?** Absolut — GroupDocs.Metadata riktar sig mot Java 8+.

## Vad är GroupDocs Maven‑beroendet?
**GroupDocs Maven‑beroendet** är en Maven‑kompatibel repository‑post som hämtar det senaste GroupDocs.Metadata‑biblioteket till ditt Java‑projekt. Det förenklar beroendehantering genom att automatiskt lösa transitiva bibliotek, garanterar att du alltid använder den senaste och säkraste versionen, och eliminerar behovet av manuella JAR‑nedladdningar eller versionsspårning.

## Varför använda GroupDocs.Metadata för att ändra PPTX:s skapelsedatum?
GroupDocs.Metadata möjliggör automatiserade, batch‑klara uppdateringar av PPTX:s skapelsestämplar, vilket säkerställer att varje presentation följer företagspolicyer eller lagkrav. Genom att programatiskt ställa in CreatedTime‑egenskapen undviker du manuell redigering, minskar mänskliga fel och kan integrera förändringen i CI/CD‑pipelines eller migrationsskript för sömlös dokumenthantering.

## Förutsättningar
- Java 8 eller högre installerat.  
- En IDE som IntelliJ IDEA eller Eclipse.  
- Maven för beroendehantering.  
- Tillgång till en GroupDocs‑prov eller köpt licens.

## Hur man ställer in PPTX CreatedTime i Java?

`Metadata`‑klassen representerar ett dokument och ger åtkomst till dess metadataegenskaper.

Läs in din PowerPoint‑fil med `new Metadata("presentation.pptx")`, hämta root‑paketet, anropa `setCreatedTime` med önskat `java.util.Date`, och slutligen anropa `save` för att skriva ändringarna. Detta end‑to‑end‑flöde ändrar skapelsedatumet samtidigt som allt bildinnehåll och andra egenskaper bevaras.

### Maven‑inställning
Lägg till GroupDocs‑repositoryn och metadata‑beroendet i din `pom.xml`:

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

> **Proffstips:** Att hålla versionsnumret uppdaterat säkerställer att du drar nytta av de senaste buggfixarna och prestandaförbättringarna.

### Direkt nedladdning (om du föredrar att inte använda Maven)

Alternativt, ladda ner den senaste JAR‑filen från [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Licensanskaffning

Börja med en gratis provlicens eller begär en tillfällig licens för att utvärdera GroupDocs.Metadata. För produktionsanvändning, köp en licens via [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/).

## Grundläggande initiering och inställning

När biblioteket finns på classpath kan du skapa en `Metadata`‑instans som pekar på din PowerPoint‑fil:

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

Denna kod öppnar presentationen i ett try‑with‑resources‑block, vilket garanterar att filhandtaget frigörs automatiskt.

## Steg‑för‑steg‑guide för att uppdatera inbyggd metadata

### Steg 1: Läs in presentationsdokumentet

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Att läsa in filen etablerar en anslutning som låter dig läsa eller skriva metadata.

### Steg 2: Åtkomst till presentationens root‑paket

`root`‑objektet ger åtkomst till presentationens kärnpaket och dess inbyggda egenskaper.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root`‑objektet exponerar alla inbyggda dokumentegenskaper.

### Steg 3: Uppdatera inbyggda dokumentegenskaper (inklusive skapelsedatum)

`setCreatedTime` tilldelar ett nytt skapelsestämpel till dokumentet.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Här demonstrerar vi hur man **ställer in PPTX CreatedTime** genom att tilldela ett nytt `Date`‑objekt till `CreatedTime`. Ersätt `new Date()` med någon specifik tidsstämpel du behöver.

### Steg 4: Spara den uppdaterade presentationen

`save` skriver den modifierade metadata tillbaka till en fil.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save`‑anropet skriver den modifierade metadata tillbaka till en ny PowerPoint‑fil, medan originalet lämnas orört.

## Felsökningstips
- **Fil ej hittad:** Dubbelkolla inmatningssökvägen och filbehörigheterna.  
- **Versionskonflikt:** Säkerställ att `groupdocs-metadata`‑versionen matchar din Java‑runtime.  
- **Egenskap uppdateras inte:** Verifiera att du anropar `setCreatedTime` (eller motsvarande setter) innan du anropar `save`.

## Praktiska tillämpningar
1. **Företagsvarumärke:** Automatiskt infoga rätt företagsnamn och kategori i alla bildspel innan distribution.  
2. **Dokumenthanteringssystem:** Berika PPTX‑filer med sökbar metadata för snabbare återhämtning.  
3. **Utbildningsresurser:** Håll författar- och läroplaninformation uppdaterad i föreläsningsbilder.  
4. **Samarbetsspårning:** Registrera medarbetares namn för att upprätthålla ansvar.  
5. **CMS‑integration:** Synkronisera metadataändringar med din innehållshanteringsplattform i realtid.

## Prestandaöverväganden
- **Batch‑behandling:** Iterera över en lista med filer och återanvänd en enda `Metadata`‑instans där det är möjligt.  
- **Minneshantering:** Använd alltid try‑with‑resources (som visas) för att snabbt frigöra inhemska resurser.  
- **Effektiva datastrukturer:** Lagra metadatauppdateringar i en karta innan du tillämpar dem för att minska repetitiva anrop.

## Vanliga frågor

**Q: Vad är huvudsyftet med GroupDocs Maven‑beroendet?**  
A: Det ger ett bekvämt sätt att inkludera det senaste GroupDocs.Metadata‑biblioteket i Maven‑baserade Java‑projekt.

**Q: Hur kan jag ställa in PPTX:s skapelsedatum utan att påverka andra egenskaper?**  
A: Använd `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` innan du anropar `metadata.save()`.

**Q: Behöver jag en licens för att köra denna kod i utveckling?**  
A: En tillfällig provlicens räcker för utveckling och testning; en full licens krävs för produktion.

**Q: Kan jag också uppdatera anpassade metadatafält?**  
A: Ja — GroupDocs.Metadata stöder både inbyggda och anpassade egenskaper via sitt API.

**Q: Finns det ett sätt att återställa ändringar om jag gör ett misstag?**  
A: Behåll en kopia av originalfilen eller läs de befintliga egenskapsvärdena innan du skriver över dem, återställ sedan vid behov.

## Resurser

- [Dokumentation](https://docs.groupdocs.com/metadata/java/)
- [API‑referens](https://apireference.groupdocs.com/metadata/java/)

---

**Senast uppdaterad:** 2026-05-27  
**Testat med:** GroupDocs.Metadata 24.12 for Java  
**Författare:** GroupDocs  

## Relaterade handledningar

- [Uppdatera anpassad metadata i PowerPoint med GroupDocs.Metadata Java‑API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Hur man uppdaterar Word‑dokumentmetadata med GroupDocs.Metadata Java: En komplett guide](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Effektiv uppdatering av PDF‑metadata med GroupDocs.Metadata i Java för dokumenthantering](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)