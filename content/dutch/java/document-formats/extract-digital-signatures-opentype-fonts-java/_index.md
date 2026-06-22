---
date: '2026-06-22'
description: Leer hoe u de OpenType-fonthandtekening en digitale handtekeningdetails
  uit OpenType-lettertypen kunt extraheren met GroupDocs.Metadata voor Java. Deze
  gids helpt uw documenten te beveiligen.
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: Hoe OpenType-fonthandtekening te extraheren in Java met GroupDocs.Metadata
type: docs
url: /nl/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Hoe OpenType-fonthandtekening te extraheren in Java met GroupDocs.Metadata

In moderne toepassingen is **het extraheren van OpenType-fonthandtekening**-gegevens essentieel om de authenticiteit van lettertypen te bevestigen en uw digitale activa te beschermen. Deze tutorial laat u stap voor stap zien hoe u zowel de handtekening‑vlaggen als de volledige cryptografische details uit een OpenType-lettertype kunt halen met behulp van **GroupDocs.Metadata for Java**. Of u nu een op beveiliging gerichte content‑pipeline bouwt of eenvoudigweg een lettertypebibliotheek moet auditen, de onderstaande technieken maken uw workflow betrouwbaar en snel.

## Snelle antwoorden
- **Welke bibliotheek heb ik nodig?** GroupDocs.Metadata for Java (v24.12)  
- **Welke Java‑versie is vereist?** JDK 8 of later  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een volledige licentie is vereist voor productie  
- **Kan ik meerdere lettertypen verwerken?** Ja – batch‑ of gelijktijdige verwerking wordt ondersteund  
- **Is de code thread‑safe?** Maak per thread een nieuwe `Metadata`‑instantie; het object zelf is niet thread‑safe  

## Wat is een OpenType-fonthandtekening?
De **OpenType-fonthandtekening** is een cryptografisch blok dat in het lettertype is ingebed en bewijst dat het bestand niet is gewijzigd sinds het is ondertekend. Het bevat de ondertekeningtijd, certificaatketen, hash‑algoritme‑identifiers en optionele intrekkingsinformatie. Het bevat ook een handtekening‑algoritme‑identifier, de certificaatketen van de ondertekenaar en optionele intrekkingslijsten, waardoor een uitgebreide verificatie van de integriteit en herkomst van het lettertype mogelijk is.

## Waarom GroupDocs.Metadata voor Java gebruiken?
GroupDocs.Metadata ondersteunt **meer dan 50 invoer‑ en uitvoerformaten** (inclusief DOCX, PDF, PPTX, HTML en tal van afbeeldingsformaten) en kan OpenType‑handtekeningen lezen zonder het volledige bestand in het geheugen te laden, waardoor u efficiënt grote lettertypecollecties van honderden pagina's kunt verwerken.

## Voorvereisten
- **Java Development Kit (JDK):** Versie 8 of nieuwer.  
- **IDE:** Elke Java‑compatibele IDE (IntelliJ IDEA, Eclipse, VS Code, enz.).  
- **Maven:** Voor afhankelijkheidsbeheer.  

### Vereiste bibliotheken en afhankelijkheden
Voeg de GroupDocs.Metadata Maven‑coördinaten toe aan uw `pom.xml`. Hiermee wordt het exacte pakket opgehaald dat nodig is voor de voorbeelden.

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
U kunt ook de nieuwste versie downloaden van [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licentie‑acquisitie
- **Gratis proefversie:** Begin met een gratis proefversie om de functies te verkennen.  
- **Tijdelijke licentie:** Verkrijg een tijdelijke licentie via de [GroupDocs licentiepagina](https://purchase.groupdocs.com/temporary-license).  
- **Aankoop:** Voor productiegebruik koopt u een volledige licentie.  

## Hoe OpenType-fonthandtekening te extraheren met GroupDocs.Metadata
De `Metadata`‑klasse is de kern‑API van GroupDocs.Metadata voor het benaderen van documentmetadata zonder het volledige bestand te laden.  
Om de handtekening van een lettertype te lezen, maakt u een `Metadata`‑object aan met het pad naar het .otf‑bestand en krijgt u vervolgens toegang tot de `DigitalSignaturePackage`. Deze aanpak laadt alleen de noodzakelijke metadata‑structuren, vermijdt volledige lettertype‑parsing en houdt het geheugenverbruik laag. De `Metadata`‑instantie moet binnen een try‑with‑resources‑blok worden gebruikt om een correcte opruiming te garanderen.

Laad uw lettertypebestand met `new Metadata("font.otf")` binnen een try‑with‑resources‑blok. De `Metadata`‑klasse is het toegangspunt van GroupDocs.Metadata voor het lezen van elk ondersteund documenttype, inclusief OpenType‑lettertypen. Het object sluit automatisch, waardoor resource‑lekken worden voorkomen.

### Hoe digitale handtekening‑vlaggen te extraheren
Het `DigitalSignaturePackage`‑object verzamelt alle handtekening‑gerelateerde informatie voor het lettertype, inclusief vlaggen en individuele handtekeningen.  
**Direct antwoord:** Roep `metadata.getDigitalSignaturePackage().getFlags()` aan na het openen van het lettertype; de geretourneerde vlagset vertelt u of de handtekening geldig, ingetrokken of onder speciale voorwaarden staat. Deze enkele aanroep geeft u een snelle statuscontrole voordat u dieper ingaat op details. De vlaggen worden weergegeven als een enumeratie die kan worden geïnspecteerd om de ondertekeningsstatus, aanwezigheid van een tijdstempel en eventuele beleidsbeperkingen tijdens het ondertekenen te bepalen.

1. Initialiseer de `Metadata`‑instantie die naar uw lettertypebestand wijst.  
2. Haal de `DigitalSignaturePackage` op.  
3. Print of log de vlagwaarden.

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
- Het try‑with‑resources‑blok garandeert dat het `Metadata`‑object automatisch wordt gesloten, waardoor geheugenlekken worden voorkomen.

### Hoe gedetailleerde digitale handtekening‑informatie te extraheren
`CmsSignature` vertegenwoordigt een individuele CMS/PKCS#7‑handtekening die in het lettertype is ingebed en biedt toegang tot de cryptografische eigenschappen.  
**Direct antwoord:** Iterate over `metadata.getDigitalSignaturePackage().getSignatures()`; elk `CmsSignature`‑object toont ondertekeningtijd, digest‑algoritmen, ingesloten inhoud en certificaatdetails, waardoor u een volledig audit‑rapport kunt samenstellen. Voor elke handtekening kunt u de certificaatketen van de ondertekenaar ophalen, het hash‑algoritme verifiëren en eventuele tijdstempel‑tokens extraheren om te bevestigen wanneer de handtekening is toegepast.

1. Gebruik dezelfde `Metadata`‑initialisatie als hierboven opnieuw.  
2. Loop door elke `CmsSignature` in het pakket.  
3. Haal eigenschappen op zoals `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()` en `getSignerInfo()`.

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
- **Sign Time:** Tijdstempel wanneer de handtekening werd toegepast.  
- **Digest Algorithms & OIDs:** Gebruikte hash‑algoritmen (bijv. SHA‑256).  
- **Encapsulated Content:** Eventuele extra gegevens die in de handtekening zijn ingesloten.  
- **Certificates:** Geldigheidsdatums en ruwe gegevensgrootte helpen de identiteit van de ondertekenaar te verifiëren.  
- **Signers:** Biedt de algoritmekeuzes en ondertekeningtijdstempels van elke ondertekenaar.

#### Probleemoplossingstips
- Als het lettertype geen digitale handtekening heeft, retourneert `getDigitalSignaturePackage()` `null`. Controleer altijd op `null` voordat u vlaggen of handtekeningen benadert.  
- Zorg ervoor dat u dezelfde **GroupDocs.Metadata**‑versie gebruikt als gedefinieerd in de Maven‑afhankelijkheid om compatibiliteitsproblemen te voorkomen.  

## Praktische toepassingen
Het extraheren van OpenType‑fonthandtekeningen is waardevol in veel praktische scenario's:

1. **Documentverificatie:** Automatiseer controles op ondertekende lettertypebestanden in een content‑managementsysteem.  
2. **Digital Asset Management:** Valideer de authenticiteit van lettertypen voordat u ze inzet in branding‑projecten.  
3. **Beveiligingsaudits:** Beoordeel handtekeningdetails om te zorgen voor naleving van interne beveiligingsbeleid.  

## Prestatie‑overwegingen
- **Resource‑beheer:** Gebruik try‑with‑resources om `Metadata`‑objecten snel te sluiten.  
- **Batchverwerking:** Verwerk lettertypen in groepen om I/O‑overhead te minimaliseren; GroupDocs.Metadata kan duizenden bestanden aan zonder elk volledig lettertype in het geheugen te laden.  
- **Concurrency:** Voer afzonderlijke `Metadata`‑instanties uit in parallelle threads voor grootschalige workloads; de bibliotheek zelf is per instantie niet thread‑safe, dus isoleer elke instantie per thread.  

## Veelgestelde vragen

**Q: Kun ik handtekeningen extraheren uit een lettertype dat geen digitale handtekening heeft?**  
A: `DigitalSignaturePackage` zal `null` zijn; controleer altijd op deze voorwaarde voordat u vlaggen of details benadert.

**Q: Welke versie van GroupDocs.Metadata is vereist?**  
A: De voorbeelden richten zich op versie **24.12**, maar nieuwere releases blijven achterwaarts compatibel voor OpenType‑lettertypen.

**Q: Heb ik een speciale licentie nodig om handtekeningen te lezen?**  
A: Een proeflicentie werkt voor evaluatie; een volledige licentie is vereist voor productiegebruik.

**Q: Hoe ga ik om met lettertypen die in een cloud‑bucket zijn opgeslagen?**  
A: Download het lettertype naar een tijdelijk lokaal bestand en geef vervolgens het pad door aan `Metadata`. De bibliotheek werkt met elk bestand dat toegankelijk is via een lokaal pad.

**Q: Is het mogelijk om de cryptografische geldigheid van de handtekening te verifiëren?**  
A: GroupDocs.Metadata levert ruwe handtekeninggegevens; u kunt de certificaatketen en hash‑waarden in een aparte cryptobibliotheek voeren om een volledige verificatie uit te voeren.

## Conclusie
Door deze gids te volgen, weet u nu **hoe u OpenType-fonthandtekening**‑informatie en gedetailleerde digitale handtekeninggegevens kunt extraheren met **GroupDocs.Metadata for Java**. Het integreren van deze stappen in uw applicaties versterkt de documentbeveiliging, stroomlijnt de validatie van assets en ondersteunt nalevingsinitiatieven.

**Volgende stappen**  
- Experimenteer met batchverwerking om grote lettertypebibliotheken efficiënt te verwerken.  
- Combineer de geëxtraheerde gegevens met uw beveiligings‑audittools voor geautomatiseerde nalevingsrapportage.  
- Ontdek andere metadata‑mogelijkheden van GroupDocs.Metadata, zoals het bewerken of verwijderen van handtekeningen wanneer dat gepast is.

---

**Laatst bijgewerkt:** 2026-06-22  
**Getest met:** GroupDocs.Metadata 24.12  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Toegang tot Word-documentmetadata met GroupDocs in Java: een uitgebreide gids](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Hoe aangepaste metadata uit PDF's te extraheren met GroupDocs.Metadata in Java: een uitgebreide gids](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)