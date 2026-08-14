---
date: '2026-06-17'
description: Lär dig hur du ändrar diagrammets skapelsestid och automatiserar metadatauppdatering
  för diagramfiler med GroupDocs.Metadata i Java.
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
title: Ändra diagrammets skapelsestid i metadata med GroupDocs Java
type: docs
url: /sv/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Ändra diagrammets skapandetid i metadata med GroupDocs Java

I den här steg‑för‑steg‑handledningen kommer du att upptäcka hur du **ändrar diagrammets skapandetid** och uppdaterar andra inbyggda egenskaper i diagramfiler med hjälp av GroupDocs.Metadata‑biblioteket för Java. Att automatisera dessa ändringar sparar timmar av manuellt arbete, garanterar konsekventa tidsstämplar i ditt arkiv och gör dina diagram omedelbart sökbara i alla dokumenthanteringssystem.

## Snabba svar
- **Vad är huvudmålet?** Ändra diagrammets skapandetid och annan metadata i diagramfiler.  
- **Vilket bibliotek ska jag använda?** GroupDocs.Metadata för Java.  
- **Behöver jag en licens?** En gratis provperiod räcker för testning; en full licens krävs för produktion.  
- **Kan jag batch‑processa många diagram?** Ja—omslut samma logik i en loop eller ett parallellt flöde.  
- **Vilken Java‑version krävs?** JDK 8 eller högre.

## Vad betyder “ändra diagrammets skapandetid” i diagrammetadata?
Att ändra skapandetiden skriver över den ursprungliga tidsstämpeln som lagras i en diagramfil (t.ex. VDX eller VSDX) med ett nytt datum‑tid‑värde. Detta låter dig anpassa filens metadata till det faktiska bearbetnings‑ eller arkiveringsdatumet istället för författarens ursprungliga tidsstämpel, vilket är viktigt för revisionsspår och korrekta sökresultat.

## Varför automatisera metadatauppdatering för diagram?
Att automatisera metadata säkerställer att varje diagram följer samma namn‑, kategoriserings‑ och tidsstämpelstandarder utan mänskliga fel. Det påskyndar också massmigreringar, minskar efterlevnadsrisker och förbättrar upptäckbarheten i företags‑DMS‑plattformar—och sparar upp till 70 % av manuellt arbete i storskaliga projekt.

## Förutsättningar
- **Java Development Kit (JDK) 8+** installerat på din maskin.  
- **IDE** såsom IntelliJ IDEA eller Eclipse.  
- **Maven** (eller manuell JAR‑hantering) för beroendehantering.  
- Grundläggande kunskap om Java‑klasser, metoder och undantagshantering.

### Nödvändiga bibliotek och beroenden
Lägg till följande förråd och beroende i din `pom.xml`‑fil om du använder Maven:

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
Om du föredrar att ladda ner direkt, besök [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) för att hämta den senaste versionen.

### Miljöinställning
- JDK 8 eller nyare.  
- IntelliJ IDEA, Eclipse eller någon Java‑kompatibel IDE.  

### Kunskapsförutsättningar
Förståelse för Java‑syntax och grundläggande fil‑I/O gör handledningen smidigare, men stegen förklaras i enkelt språk.

## Konfigurera GroupDocs.Metadata för Java
### Installationsinstruktioner
**Maven‑användare:** Kodsnutten ovan lägger automatiskt till förrådet och den nödvändiga JAR‑filen.  
**Användare som laddar ner direkt:** Efter att ha laddat ner JAR‑filen från [GroupDocs](https://releases.groupdocs.com/metadata/java/), lägg till den i ditt projekts klassväg.

### Licensanskaffning
- **Gratis provperiod:** Utforska biblioteket utan kostnad.  
- **Tillfällig licens:** Skaffa en tillfällig licens för utökad testning [här](https://purchase.groupdocs.com/temporary-license/).  
- **Köp:** Skaffa en full licens för produktionsmiljöer.

### Grundläggande initiering
`Metadata` är kärnklassen som representerar ett dokuments metadata‑behållare och ger läs‑/skriv‑åtkomst till alla inbyggda egenskaper. För att börja använda GroupDocs.Metadata, importera klassen och öppna en diagramfil:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Med biblioteket initierat kan du nu ändra vilken inbyggd egenskap som helst, inklusive skapandetiden.

## Implementeringsguide
### Hur man ändrar skapandetid i diagramfiler
I det här avsnittet går vi igenom varje steg som krävs för att **ändra diagrammets skapandetid** och uppdatera andra vanliga egenskaper såsom författare, företag och kategori. Processen innebär att ladda diagrammet med Metadata‑API:t, komma åt dess rotpaket, sätta önskade fält och slutligen spara ändringarna till en ny fil, så att originalet förblir orört.

#### Steg 1: Ladda diagramdokumentet
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Förklaring:* `Metadata`‑konstruktorn tar emot sökvägen till din diagramfil. `try‑with‑resources`‑blocket säkerställer att filen stängs korrekt efter operationen.

#### Steg 2: Åtkomst till rotpaketet
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Förklaring:* Rotpaketet ger dig direkt åtkomst till alla inbyggda metadatafält för diagrammet.

#### Steg 3: Ställ in skaparegenskapen
```java
root.getDocumentProperties().setCreator("test author");
```  
*Förklaring:* Tilldelar ett nytt författarnamn. Ersätt `"test author"` med den faktiska skaparen.

#### Steg 4: Ändra skapandetid
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Förklaring:* Denna rad **ändrar skapandetiden** till systemets aktuella datum och tid. Du kan också ange en specifik `Date`‑instans om du behöver en anpassad tidsstämpel.

#### Steg 5: Definiera företagsinformation
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Förklaring:* Lagrar företagsnamnet som är kopplat till diagrammet—användbart för företags‑spårning.

#### Steg 6: Ställ in dokumentkategori
```java
root.getDocumentProperties().setCategory("test category");
```  
*Förklaring:* Kategoriserar filen, vilket hjälper dig att **uppdatera diagramkategorin** konsekvent i hela ditt förråd.

#### Steg 7: Lägg till nyckelord
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Förklaring:* Nyckelord förbättrar sökbarheten; du kan lista alla termer som är relevanta för diagrammets innehåll.

#### Steg 8: Spara ändringar
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Förklaring:* Sparar alla ändringar till en ny fil, så att originalet förblir orört.

### Vanliga fallgropar & felsökning
- **Fil ej hittad:** Verifiera inmatningssökvägen och säkerställ att filändelsen matchar det faktiska formatet.  
- **Åtkomst nekad:** Kontrollera läs‑/skrivrättigheter för både in‑ och ut‑kataloger.  
- **Ogiltigt datumformat:** Använd `java.util.Date` eller `java.time`‑objekt som är kompatibla med API:t.  

## Praktiska tillämpningar
1. **Automatisering av dokumentarkivering** – När gamla diagram flyttas till ett arkiv, ändra automatiskt **diagrammets skapandetid** till arkiveringsdatumet och sätt en enhetlig kategori.  
2. **Integration med versionskontroll** – Håll tidsstämplar i synk med Git‑commits genom att uppdatera skapandetiden vid varje release.  
3. **Standardisering av företags‑DMS** – Tvinga igenom en företagsomfattande policy för författare, företag och nyckelord för alla diagramtillgångar.

## Prestandaöverväganden
- **Batch‑behandling:** Omslut stegen ovan i en loop för att hantera dussintals filer i ett körning.  
- **Minneshantering:** Frigör varje `Metadata`‑instans omedelbart (`try‑with‑resources`‑blocket gör detta automatiskt).  
- **Asynkron körning:** För stora batcher, överväg `CompletableFuture` för att köra uppdateringar parallellt utan att blockera huvudtråden.  
- **Kvantifierad kapacitet:** GroupDocs.Metadata stödjer över 30 diagramformat och kan bearbeta filer upp till 500 MB utan att ladda hela dokumentet i minnet, vilket levererar uppdateringar på under 200 ms per fil på vanlig serverhårdvara.

## Slutsats
Du vet nu hur du **ändrar diagrammets skapandetid** och uppdaterar andra inbyggda metadataegenskaper för diagramdokument med hjälp av GroupDocs.Metadata i Java. Genom att automatisera dessa steg kan du upprätthålla konsekvent, sökbar och efterlevnadssäker dokumentation i hela din organisation.

**Nästa steg**
- Experimentera med andra filformat som stödjs av GroupDocs.Metadata (PDF, DOCX, etc.).  
- Integrera koden i en CI/CD‑pipeline för att upprätthålla metadata‑standarder i varje bygg.

Klar att prova? Gå till [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) och börja implementera din egen metadata‑automatisering idag.

---

**Senast uppdaterad:** 2026-06-17  
**Testat med:** GroupDocs.Metadata 24.12  
**Författare:** GroupDocs  

## Vanliga frågor

**Q: Kan jag använda detta tillvägagångssätt med andra diagramformat som VSDX?**  
A: Ja, samma API fungerar för alla diagramformat som stödjs av GroupDocs.Metadata.

**Q: Behöver jag en licens för utvecklingsbyggen?**  
A: En gratis provperiod räcker för utveckling och testning; en full licens krävs för produktionsdistributioner.

**Q: Hur kan jag uppdatera flera egenskaper i ett anrop?**  
A: Sätt varje egenskap på `DocumentProperties`‑objektet innan du anropar `metadata.save(...)`; biblioteket skriver dem alla på en gång.

**Q: Är det säkert att skriva över originalfilen?**  
A: Det rekommenderas att spara till en ny fil (som visat) och ersätta originalet först efter att ha bekräftat att uppdateringen lyckades.

**Q: Vad händer om jag behöver ange ett anpassat skapelsedatum istället för aktuell tid?**  
A: Skapa ett `java.util.Date` (eller `java.time`‑instans) med önskad tidsstämpel och skicka det till `setTimeCreated`.

## Relaterade handledningar

- [Hur man uppdaterar diagrammetadata Java med GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Hur man uppdaterar DXF‑författarmetadata med GroupDocs.Metadata för Java – En komplett guide](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Automatisera Java‑metadatauppdateringar efter datum med GroupDocs.Metadata för effektiv filhantering](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)