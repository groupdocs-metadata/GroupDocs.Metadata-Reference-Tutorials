---
date: '2026-06-22'
description: Lär dig hur du extraherar OpenType font signature och digital signature-detaljer
  från OpenType fonts med GroupDocs.Metadata för Java. Denna guide hjälper dig att
  säkra dina dokument.
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
title: Hur man extraherar OpenType font signature i Java med GroupDocs.Metadata
type: docs
url: /sv/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Hur man extraherar OpenType-typsnittssignatur i Java med GroupDocs.Metadata

I moderna applikationer är **extracting OpenType font signature**-data avgörande för att bekräfta typsnittets äkthet och skydda dina digitala tillgångar. Denna handledning visar dig steg för steg hur du hämtar både signaturflaggorna och de fullständiga kryptografiska detaljerna från ett OpenType-typsnitt med hjälp av **GroupDocs.Metadata for Java**. Oavsett om du bygger en säkerhetsfokuserad innehållspipeline eller bara behöver granska ett typsnittsbibliotek, kommer teknikerna nedan att göra ditt arbetsflöde pålitligt och snabbt.

## Snabba svar
- **Vilket bibliotek behövs?** GroupDocs.Metadata for Java (v24.12)  
- **Vilken Java-version krävs?** JDK 8 eller senare  
- **Behöver jag en licens?** En gratis provperiod fungerar för utvärdering; en full licens krävs för produktion  
- **Kan jag bearbeta flera typsnitt?** Ja – batch‑ eller samtidig bearbetning stöds  
- **Är koden trådsäker?** Skapa en ny `Metadata`‑instans per tråd; objektet i sig är inte trådsäkert  

## Vad är en OpenType-typsnittssignatur?
Den **OpenType font signature** är ett kryptografiskt block som är inbäddat i typsnittet och bevisar att filen inte har ändrats sedan den signerades. Den innehåller signeringstid, certifikatkedja, identifierare för hash‑algoritmer och valfri återkallningsinformation. Den inkluderar också en identifierare för signaturalgoritm, en signatörs certifikatkedja och valfria återkallningslistor, vilket möjliggör en omfattande verifiering av typsnittets integritet och ursprung.

## Varför använda GroupDocs.Metadata för Java?
GroupDocs.Metadata stöder **50+ input and output formats** (inklusive DOCX, PDF, PPTX, HTML och många bildtyper) och kan läsa OpenType‑signaturer utan att ladda hela filen i minnet, vilket gör att du kan bearbeta samlingar med hundratals typsnittssidor effektivt.

## Förutsättningar
- **Java Development Kit (JDK):** Version 8 eller nyare.  
- **IDE:** Valfri Java‑kompatibel IDE (IntelliJ IDEA, Eclipse, VS Code osv.).  
- **Maven:** För beroendehantering.  

### Nödvändiga bibliotek och beroenden
Lägg till GroupDocs.Metadata Maven‑koordinaterna i din `pom.xml`. Detta hämtar det exakta paketet som behövs för exemplen.

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

### Direkt nedladdning
Alternativt, ladda ner den senaste versionen från [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licensanskaffning
- **Free Trial:** Börja med en gratis provperiod för att utforska funktionerna.  
- **Temporary License:** Skaffa en tillfällig licens via [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license).  
- **Purchase:** För produktionsbruk, köp en full licens.

## Hur man extraherar OpenType-typsnittssignatur med GroupDocs.Metadata
`Metadata`‑klassen är GroupDocs.Metadata:s kärn‑API för att komma åt dokumentmetadata utan att ladda hela filen.  
För att läsa ett typsnitts signatur, skapa ett `Metadata`‑objekt med sökvägen till .otf‑filen och få sedan åtkomst till dess `DigitalSignaturePackage`. Detta tillvägagångssätt laddar endast de nödvändiga metadata‑strukturerna, undviker fullständig typsnitts‑parsning och håller minnesanvändningen låg. `Metadata`‑instansen bör användas inom ett try‑with‑resources‑block för att säkerställa korrekt resurshantering.

Läs in din typsnittfil med `new Metadata("font.otf")` inom ett try‑with‑resources‑block. `Metadata`‑klassen är GroupDocs.Metadata:s ingångspunkt för att läsa alla stödda dokumenttyper, inklusive OpenType‑typsnitt. Objektet stängs automatiskt, vilket förhindrar resurssläpp.

### Hur man extraherar flaggor för digital signatur
`DigitalSignaturePackage`‑objektet samlar all signaturrelaterad information för typsnittet, inklusive flaggor och enskilda signaturer.  
**Direct answer:** Anropa `metadata.getDigitalSignaturePackage().getFlags()` efter att ha öppnat typsnittet; den returnerade flagguppsättningen visar om signaturen är giltig, återkallad eller har särskilda villkor. Detta enkla anrop ger dig en snabb hälsokontroll innan du går djupare in i detaljer. Flaggan representeras som en uppräkning som kan inspekteras för att avgöra signeringsstatus, närvaron av tidsstämpel och eventuella policyrestriktioner som tillämpats under signeringen.

1. Initiera `Metadata`‑instansen som pekar på din typsnittfil.  
2. Hämta `DigitalSignaturePackage`.  
3. Skriv ut eller logga flaggvärdena.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Förklaring**  
- `documentPath` – absolut eller relativ sökväg till OpenType‑typsnittet.  
- Try‑with‑resources‑blocket garanterar att `Metadata`‑objektet stängs automatiskt, vilket undviker minnesläckor.

### Hur man extraherar detaljerad digital signaturinformation
`CmsSignature` representerar en enskild CMS/PKCS#7‑signatur som är inbäddad i typsnittet och ger åtkomst till dess kryptografiska egenskaper.  
**Direct answer:** Iterera över `metadata.getDigitalSignaturePackage().getSignatures()`; varje `CmsSignature`‑objekt avslöjar signeringstid, digest‑algoritmer, inkapslat innehåll och certifikatinformation, vilket gör att du kan bygga en fullständig granskningsrapport. För varje signatur kan du hämta signatörens certifikatkedja, verifiera hash‑algoritmen och extrahera eventuella tidsstämpeltoken för att bekräfta när signaturen applicerades.

1. Återanvänd samma `Metadata`‑initiering som ovan.  
2. Loopa igenom varje `CmsSignature` i paketet.  
3. Extrahera egenskaper såsom `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()` och `getSignerInfo()`.

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

**Förklaring av nyckelsektioner**  
- **Sign Time:** Tidsstämpel när signaturen applicerades.  
- **Digest Algorithms & OIDs:** Hash‑algoritmer som används (t.ex. SHA‑256).  
- **Encapsulated Content:** Eventuell ytterligare data som är inbäddad i signaturen.  
- **Certificates:** Giltighetsdatum och rådatastorlek hjälper till att verifiera signatörens identitet.  
- **Signers:** Tillhandahåller varje signatörs algoritmval och signeringstidsstämplar.

#### Felsökningstips
- Om typsnittet saknar en digital signatur returnerar `getDigitalSignaturePackage()` `null`. Kontrollera alltid `null` innan du får åtkomst till flaggor eller signaturer.  
- Säkerställ att du använder samma **GroupDocs.Metadata**‑version som definierats i Maven‑beroendet för att undvika kompatibilitetsproblem.  

## Praktiska tillämpningar
Att extrahera OpenType‑typsnittssignaturer är värdefullt i många verkliga scenarier:

1. **Document Verification:** Automatisera kontroller av signerade typsnittsfiler i ett innehållshanteringssystem.  
2. **Digital Asset Management:** Validera typsnittets äkthet innan de distribueras i varumärkesprojekt.  
3. **Security Audits:** Granska signaturdetaljer för att säkerställa efterlevnad av interna säkerhetspolicys.

## Prestandaöverväganden
- **Resource Management:** Använd try‑with‑resources för att snabbt stänga `Metadata`‑objekt.  
- **Batch Processing:** Bearbeta typsnitt i grupper för att minimera I/O‑överhead; GroupDocs.Metadata kan hantera tusentals filer utan att ladda varje helt typsnitt i minnet.  
- **Concurrency:** Kör separata `Metadata`‑instanser i parallella trådar för storskaliga arbetsbelastningar; biblioteket är inte trådsäkert per instans, så isolera varje instans per tråd.

## Vanliga frågor
**Q:** Kan jag extrahera signaturer från ett typsnitt som saknar digital signatur?  
**A:** `DigitalSignaturePackage` kommer att vara `null`; kontrollera alltid detta villkor innan du får åtkomst till flaggor eller detaljer.

**Q:** Vilken version av GroupDocs.Metadata krävs?  
**A:** Exemplen är riktade mot version **24.12**, men nyare releaser är fortfarande bakåtkompatibla för OpenType‑typsnitt.

**Q:** Behöver jag en speciell licens för att läsa signaturer?  
**A:** En provlicens fungerar för utvärdering; en full licens krävs för produktionsbruk.

**Q:** Hur hanterar jag typsnitt lagrade i en molnbucket?  
**A:** Ladda ner typsnittet till en tillfällig lokal fil och skicka sedan dess sökväg till `Metadata`. Biblioteket fungerar med alla filer som är åtkomliga via en lokal sökväg.

**Q:** Är det möjligt att verifiera signaturens kryptografiska giltighet?  
**A:** GroupDocs.Metadata tillhandahåller rå signaturdata; du kan mata in certifikatkedjan och hash‑värdena i ett separat kryptobibliotek för att utföra en fullständig verifiering.

## Slutsats
Genom att följa den här guiden vet du nu **how to extract OpenType font signature**‑information och detaljerad digital signaturdata med **GroupDocs.Metadata for Java**. Att integrera dessa steg i dina applikationer stärker dokumentssäkerheten, förenklar validering av tillgångar och stödjer efterlevnadsinitiativ.

**Nästa steg**  
- Experimentera med batch‑behandling för att effektivt hantera stora typsnittsbibliotek.  
- Kombinera den extraherade datan med dina säkerhets‑audit‑verktyg för automatiserad efterlevnadsrapportering.  
- Utforska andra metadata‑funktioner i GroupDocs.Metadata, såsom redigering eller borttagning av signaturer när det är lämpligt.

---

**Senast uppdaterad:** 2026-06-22  
**Testad med:** GroupDocs.Metadata 24.12  
**Författare:** GroupDocs

## Relaterade handledningar

- [Åtkomst till Word-dokumentmetadata med GroupDocs i Java&#58; En omfattande guide](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Hur man extraherar anpassad metadata från PDF‑filer med GroupDocs.Metadata i Java&#58; En omfattande guide](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)