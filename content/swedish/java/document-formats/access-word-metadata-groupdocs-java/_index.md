---
date: '2026-03-25'
description: Lär dig hur du hämtar skapad tid i Java och extraherar dokumentmetadata
  med GroupDocs.Metadata för Java. Denna guide täcker installation, läsning av egenskaper
  och praktiska tillämpningar.
keywords:
- access word document metadata
- groupdocs.metadata java
- read word metadata properties
title: Hämta skapad tid i Java från Word‑dokument med GroupDocs
type: docs
url: /sv/java/document-formats/access-word-metadata-groupdocs-java/
weight: 1
---

# hämta skapad tid java från Word-dokument med GroupDocs

## Hur man extraherar och manipulerar metadataegenskaper för ett Word-dokument med GroupDocs.Metadata Java

### Introduktion

Letar du efter att **hämta skapad tid java** eller på annat sätt **java extrahera dokumentmetadata** från dina Word-filer? Att känna till metadata som är inbäddad i ett dokument är avgörande för granskning, efterlevnad och intelligent innehållshantering. I den här handledningen går vi igenom hur du ställer in GroupDocs.Metadata, läser inbyggda egenskaper (inklusive Skapad tid) och använder informationen i verkliga scenarier.

Nedan hittar du allt du behöver för att komma igång—förutsättningar, Maven‑inställning, kodsnuttar och felsökningstips—allt skrivet i en vänlig, steg‑för‑steg‑stil.

## Snabba svar
- **Vad betyder “retrieve created time java”?** Det är processen att läsa dokumentets skapelsestämpel med Java‑kod.  
- **Vilket bibliotek hanterar detta?** GroupDocs.Metadata for Java tillhandahåller ett enkelt API för åtkomst till Word‑metadata.  
- **Behöver jag en licens?** En gratis provversion fungerar för utvärdering; en full licens krävs för produktionsanvändning.  
- **Kan jag läsa andra egenskaper samtidigt?** Ja—författare, företag, nyckelord och mer är tillgängliga via samma API.  
- **Är detta tillvägagångssätt prestandaeffektivt?** Ja, särskilt när du använder try‑with‑resources för att hantera minnet effektivt.

## Förutsättningar

Innan vi dyker ner i implementationen, se till att du har följande:

- **JDK** (Java Development Kit) installerat på din maskin.  
- **Maven** (eller ett annat byggverktyg) för att hantera beroenden.  
- Grundläggande kunskap om Java och en IDE som IntelliJ IDEA eller Eclipse.  

### Nödvändiga bibliotek och beroenden

För att arbeta med GroupDocs.Metadata, inkludera repot och beroendet i din `pom.xml`‑fil:

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

Alternativt, ladda ner den senaste versionen direkt från [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Krav för miljöinställning

- **JDK** (Java 8 eller högre)  
- **Maven** (om du föredrar manuell JAR‑hantering, se avsnittet Direktnedladdning nedan)  

### Kunskapsförutsättningar

- Grundläggande Java‑syntax och objekt‑orienterade koncept.  
- Förståelse för hur man lägger till beroenden i ett Maven‑projekt.  

## Konfigurera GroupDocs.Metadata för Java

### Maven‑inställning

Om du använder Maven, kommer kodsnutten ovan att hämta biblioteket automatiskt.

### Direktnedladdning

För icke‑Maven‑projekt, besök [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) för att hämta JAR‑filen och lägga till den i ditt projekts byggsökväg.

### Licensanskaffning

1. **Free Trial** – Ladda ner en provversion från den officiella webbplatsen.  
2. **Temporary License** – Begär en tillfällig nyckel för förlängd utvärdering.  
3. **Full License** – Köp en kommersiell licens för produktionsdistributioner.

### Grundläggande initiering

När biblioteket är tillgängligt kan du instansiera `Metadata`‑klassen:

```java
import com.groupdocs.metadata.*;

// Initialize the Metadata class with the path to your document
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your-document.docx")) {
    // Your code here to work with metadata
}
```

## Implementeringsguide

### Åtkomst till dokumentegenskaper

#### Steg 1: Ladda Word‑dokumentet

```java
// Load the Word document from a specified path
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your-document.docx")) {
    // Proceed with accessing properties
}
```

#### Steg 2: Åtkomst till rotpaketet

```java
// Get the root package for Word Processing documents
WordProcessingRootPackage root = metadata.getRootPackageGeneric();
```

#### Steg 3: Läs och manipulera inbyggda dokumentegenskaper

```java
// Retrieve built-in properties
String author = root.getDocumentProperties().getAuthor();
java.util.Date createdTime = root.getDocumentProperties().getCreatedTime();
String company = root.getDocumentProperties().getCompany();
String category = root.getDocumentProperties().getCategory();
String keywords = root.getDocumentProperties().getKeywords();

// Print the retrieved properties
System.out.println("Author: " + author);
System.out.println("Created Time: " + createdTime);
System.out.println("Company: " + company);
System.out.println("Category: " + category);
System.out.println("Keywords: " + keywords);
```

Anropet `getCreatedTime()` är exakt vad du behöver för att **hämta skapad tid java**. Du kan nu lagra, visa eller bearbeta denna tidsstämpel enligt ditt programs krav.

### Felsökningstips

- **Document Path** – Dubbelkolla filplatsen; relativa sökvägar löses från projektets rot.  
- **Library Version** – Säkerställ att GroupDocs.Metadata‑versionen matchar din JDK‑nivå.  
- **Exception Handling** – Omge anrop med try‑catch‑block för att hantera `FileNotFoundException`, `MetadataException` osv. på ett smidigt sätt.  

## Praktiska tillämpningar

Att förstå och få åtkomst till metadata öppnar dörren till många scenarier:

1. **Document Auditing** – Verifiera vem som skapade en fil och när, för att uppfylla efterlevnadskontroller.  
2. **Organizational Tagging** – Använd kategorier och nyckelord för att driva sökning och klassificering i ett DMS.  
3. **Integration** – Mata metadata till arbetsflödesmotorer eller content‑management‑API:er för rikare automatisering.  

## Prestandaöverväganden

- Använd **try‑with‑resources** (som visas) för att automatiskt stänga `Metadata`‑objekt och frigöra inhemska resurser.  
- Bearbeta dokument i batcher endast om det behövs, för att hålla minnesanvändningen förutsägbar.  

## Slutsats

Du har nu en robust, produktionsklar metod för att **hämta skapad tid java** och annan metadata från Word‑dokument med GroupDocs.Metadata. Denna funktionalitet gör det möjligt att bygga revisionsspår, förbättra sökning och integrera dokumentegenskaper i bredare affärsprocesser.

### Nästa steg

- Experimentera med att uppdatera metadata (t.ex. `setAuthor`, `setKeywords`).  
- Utforska hela API:et för anpassade egenskaper och avancerad manipulation.  
- Kolla den officiella dokumentationen för djupare exempel.

### FAQ‑sektion

1. **What is GroupDocs.Metadata?**  
   - Ett Java‑bibliotek som möjliggör manipulation och hämtning av dokumentmetadata över olika format.  
2. **How do I get started with GroupDocs.Metadata in my project?**  
   - Ställ in Maven eller ladda ner JAR‑filen, och lägg sedan till beroendet som visas ovan.  
3. **Can I use GroupDocs.Metadata for free?**  
   - Ja, en provversion finns tillgänglig; en tillfällig licens låser upp avancerade funktioner.  
4. **What are some common errors when using this library?**  
   - Felaktiga dokumentvägar och felaktiga biblioteksversioner är de vanligaste.  
5. **How can I optimize performance when working with metadata in Java?**  
   - Följ bästa praxis för minneshantering, använd try‑with‑resources och undvik att ladda stora dokument onödigt.  

## Vanliga frågor

**Q: Stöder GroupDocs.Metadata andra filformat förutom Word?**  
A: Ja, det fungerar med PDF, Excel, PowerPoint och många fler format.

**Q: Kan jag redigera metadata efter att ha hämtat den?**  
A: Absolut. API:et tillhandahåller setter‑metoder som `setAuthor` och `setCreatedTime`.

**Q: Finns det ett sätt att ta bort metadata helt?**  
A: Du kan rensa enskilda egenskaper eller använda metoden `removeAllProperties` för att radera metadata.

**Q: Hur hanterar jag lösenordsskyddade dokument?**  
A: Skicka lösenordet till `Metadata`‑konstruktorn som har en överlagring som accepterar ett `LoadOptions`‑objekt.

**Q: Var kan jag hitta fler kodexempel?**  
A: Den officiella dokumentationen och GitHub‑repot innehåller omfattande exempel.

### Resurser
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download GroupDocs.Metadata for Java](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata)

---

**Last Updated:** 2026-03-25  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs