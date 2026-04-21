---
date: '2026-01-24'
description: Leer hoe u handtekening- en digitale handtekeninggegevens uit OpenType-lettertypen
  kunt extraheren met GroupDocs.Metadata voor Java. Deze stapsgewijze gids verbetert
  de documentbeveiliging.
keywords:
- extract digital signatures OpenType fonts Java
- digital signature flags OpenType fonts
- GroupDocs Metadata Java
title: Hoe handtekening uit OpenType-lettertypen te extraheren in Java met GroupDocs.Metadata
type: docs
url: /nl/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

ahereniteit extraheren van digitale handtekening‑vlaggen en gedetailleerde handtekeninggegevens uit OpenType‑lettertypen met behulp van **GroupDocs.Metadata for Java**. Of je nu een document‑beheersysteem bouwt, een beveiligings‑gerichte applicatie, of simpelweg font‑activa moet auditen, het beheersen van dit proces maakt je workflow betrouwbaarder en veiliger.

**Wat je zult leren**
- Hoe digitale handtekening‑vlaggen uit OpenType‑lettertypen te extraheren  
- Hoe gedetailleerde informatie over elke digitale handtekening op te halen  
- Hoe GroupDocs.Metadata in een Java‑project
- **Welke bibliotheek heb ik nodig?** GroupDocs.Metadata for Java (v24.12 code‑object is wegwerpbaar; maak per thread een nieuwe instantie aan  

## Vereisten
Voordat je digitale handtekeninggegevens extraheert, zorg ervoor dat je configuratie aan deze eisen voldoet:

### Vereiste bibliotheken en afhankelijkheden
Om met GroupDocs.Metadata for Java te werken, voeg je de Maven‑repository en afhankelijkheid toe zoals hieronder weergegeven.

### Omgevingsinstellingen
- **Java Development Kit (JDK):** Installeer JDK 8 of hoger.  
- **IDE:** Elke Java‑compatibele IDE (IntelliJ IDEA, Eclipse, VS Code, enz.).

### Kennisvereisten
Basiskennis van Java en een begrip van digitale handtekeningen zijn nuttig, maar de gids bevat duidelijke uitleg voor beginners.

## GroupDocs.Metadata voor Java instellen
### Maven‑installatie
Voeg de volgende configuratie toe aan je `pom.xml`‑bestand. Hiermee wordt het **groupdocs metadata java**‑pakket opgehaald dat nodig is voor de voorbeelden.

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

### Directe download
Download anders de nieuwste versie vanaf [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licentie‑acquisitie
- **Gratis proefversie:** Begin met een gratis proefversie om de functionaliteit te verkennen.  
- **Tijdelijke licentie:** Verkrijg een tijdelijke licentie indien nodig via de [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license).  
- **Aankoop bevat cryptaten en
Het extraheren van digitale handtekening‑vlaggen stelt je in staat snel de status en eigenschappen van een handtekening te identificeren (bijv. of deze geldig, ingetrokken of onder speciale voorwaarden staat).

### Implementatiestappen
1. **Metadata initialiseren:** Maak een `Metadata`‑instantie die naar je lettertype‑bestand wijst.  
2. **Vlaggen lezen:** Toegang krijgen tot de `DigitalSignaturePackage` en de vlaggen afdrukken.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Uitleg**
- `documentPath` – absolute of relatieve pad naar het OpenType‑lettertype.  
- Het `try‑with‑resources`‑blok zorgt ervoor dat het `Metadata`‑object automatisch wordt gesloten, waardoor resource‑lekken worden voorkomen.

## Hoe gedetailleerde digitale handtekeninginformatie te extraheren
### Overzicht
Naast vlaggen moet je vaak de metadata van elke handtekening inspecteren – ondertekeningtijd, algoritmen, certificaten en ingesloten inhoud.

### Implementatiestappen
1. **Metadata initialiseren** (zoals hierboven).  
2. **Itereren over handtekeningen:** Voor elke `CmsSignature` de relevante eigenschappen afdrukken.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**Uitleg van belangrijke secties**
- **Sign Time:** Wanneer de handtekening is toegepast.  
- **Digest Algorithms & OIDs:** Gebruikte hash‑algoritmen (bijv. SHA‑256).  
- **Encapsulated Content:** Eventuele extra gegevens die in de handtekening zijn verpakt.  
- **Certificates:** Geldigheidsdatums en ruwe gegevensgrootte helpen de identiteit van de ondertekenaar te verifiëren.  
- **Signers:** Biedt de algoritmekeuzes en ondertekeningtijdstempels van elke ondertekenaar.

### Probleemoplossende tips
- Zorg ervoor dat het lettertype daadwerkelijk een digitale handtekening bevat; anders retourneert `getDigitalSignaturePackage()` `null`.  
- Controleer of je dezelfde **GroupDocs.Metadata**‑versie gebruikt als in de Maven‑afhankelijkheid staat om compatibiliteitsproblemen te vermijden.

## Praktische toepassingen
Het extraheren van digitale handtekeninggegevens uit OpenType‑lettertypen is nuttig in vele scenario's:
1. **Documentverificatie:** Automatiseer controles op ondertekende lettertype‑bestanden in een content‑management‑systeem.  
2. **Digital Asset Management:** Valideer de authenticiteit van lettertypen voordat je ze inzet in branding‑projecten.  
3. **Beveiligingsaudits:** Beoordeel handtekeningdetails om te voldoen aan interne beveiligingsrichtlijnen.

## Prestatie‑overwegingen
- **Resourcebeheer:** Gebruik altijd `try‑with‑resources` om `Metadata`‑objecten snel te sluiten.  
- **Batchverwerking:** Verwerk bij veel lettertypen ze in batches om I/O‑overhead te verminderen.  
- **Concurrency:** Voor grootschalige workloads kun je aparte `Metadata`‑instanties in parallelle threads draaien; de bibliotheek zelf is per instantie niet thread‑safe.

## Veelgestelde vragen

**Q: Kan ik handtekeningen extraheren uit een lettertype dat geen digitale handtekening heeft?**  
A: Het `DigitalSignaturePackage` zal `null` zijn; je moet deze situatie controleren voordat je vlaggen of details benadert.

**Q: Welke versie van GroupDocs.Metadata is vereist?**  
A: De voorbeelden gebruiken versie **24.12**, maar nieuwere versies zijn achterwaarts compatibel voor OpenType‑lettertypen.

**Q: Heb ik een speciale licentie nodig om handtekeningen te lezen?**  
A: Een proeflicentie werkt voor evaluatie; een volledige licentie is vereist voor productiegebruik.

**Q: Hoe ga ik om met lettertypen die in een cloud‑bucket zijn opgeslagen?**  
A: Download het lettertype naar een tijdelijk lokaal bestand en geef vervolgens het pad door aan `Metadata`. De bibliotheek werkt met elk bestand dat via een lokaal pad toegankelijk is.

**Q: Is het mogelijk de cryptografische geldigheid van de handtekening te verifiëren?**  
A: GroupDocs.Metadata levert de ruwe gegevens; je kunt de certificaatketen en hash‑waarden aan een aparte cryptobibliotheek doorgeven voor volledige verificatie.

## Conclusie
Door deze gids te volgen, weet je nu **hoe handtekening te extraheren** informatie en gedetailleerde digitale handtekeninggegevens uit OpenType‑lettertypen met **GroupDocs.Metadata for Java**. Het toepassen van deze technieken in je applicaties versterkt de documentbeveiliging, stroomlijnt asset‑validatie en ondersteunt compliance‑initiatieven.

**Volgende stappen**
- Experimenteer met batchverwerking om grote lettertype‑bibliotheken te behandelen.  
- Combineer de geëxtraheerde gegevens met je beveiligings‑audit‑tools voor geautomatiseerde compliance‑rapportage.  
- Ontdek andere metadata‑mogelijkheden van GroupDocs.Metadata, zoals het bewerken of verwijderen van handtekeningen wanneer dat gepast is.

---

**Laatst bijgewerkt:** 2026-01-24  
**Getest met:** GroupDocs.Metadata 24.12  
**Auteur:** GroupDocs