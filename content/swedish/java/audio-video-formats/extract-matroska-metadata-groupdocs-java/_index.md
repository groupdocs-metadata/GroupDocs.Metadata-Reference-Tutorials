---
date: '2025-12-22'
description: Lär dig hur du extraherar mkv-metadata i Java med GroupDocs.Metadata
  för Java, inklusive EBML-huvuden, segmentinformation, taggar och spårdata.
keywords:
- extract mkv metadata java
- groupdocs.metadata java
- read matroska file
title: Extrahera MKV-metadata i Java – Guide med GroupDocs.Metadata
type: docs
url: /sv/java/audio-video-formats/extract-matroska-metadata-groupdocs-java/
weight: 1
---

# Extrahera MKV-metadata Java med GroupDocs.Metadata

Multimediabibliotek finns överallt, och att kunna läsa deras inre detaljer är avgörande för mediehantering, katalogisering och analys. I den här handledningen kommer du att lära dig **how to extract mkv metadata java** med det kraftfulla GroupDocs.Metadata‑biblioteket. Vi går igenom hur du installerar biblioteket, hämtar EBML‑rubriker, segmentinformation, taggar och spårdata från en MKV‑fil, och visar dig verkliga scenarier där denna kunskap lönar sig.

## Snabba svar
- **What does “extract mkv metadata java” mean?** Det är processen att programatiskt läsa metadata från MKV‑filer med Java.
- **Which library should I use?** GroupDocs.Metadata for Java tillhandahåller ett omfattande API för Matroska‑filer.
- **Do I need a license?** En gratis provversion fungerar för utvärdering; en licens tar bort användningsgränser.
- **Can I read other formats?** Ja, samma bibliotek stöder MP4, AVI, MP3 och många fler.
- **Is internet access required at runtime?** Nej, all extraktion sker lokalt efter att biblioteket har lagts till i ditt projekt.

## Vad är Matroska (MKV) metadata?
Matroska är ett öppet, flexibelt containerformat. Dess metadata inkluderar EBML‑rubriken (filversion, dokumenttyp), segmentdetaljer (längd, mux‑applikation), taggar (titlar, beskrivningar) och spårspecifikationer (audio/video‑codecs, språk). Att komma åt dessa data låter dig bygga mediakataloger, verifiera filintegritet eller automatiskt generera miniatyrbilder.

## Varför använda GroupDocs.Metadata för Java?
- **Full‑featured API** – Hanterar EBML, segment, taggar och spår utan låg‑nivå‑parsing.
- **Performance‑optimized** – Fungerar effektivt även med stora filer.
- **Cross‑format support** – Samma kodbas kan återanvändas för andra audio/video‑containrar.
- **Simple Maven integration** – Lägg till ett enda beroende och börja extrahera.

## Förutsättningar
- **GroupDocs.Metadata for Java** version 24.12 eller senare.  
- Java Development Kit (JDK) installerat.  
- Maven (eller manuell JAR‑hantering).  
- En MKV‑fil att experimentera med (placera den i `YOUR_DOCUMENT_DIRECTORY`).

## Installera GroupDocs.Metadata för Java
Lägg till biblioteket i ditt projekt med Maven eller ladda ner JAR‑filen direkt.

**Maven:**  
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

**Direct Download:**  
Om du föredrar att inte använda Maven, ladda ner den senaste versionen från [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licensanskaffning
Börja med en gratis provversion för att utforska funktionerna. För produktionsanvändning, köp en licens eller skaffa en tillfällig licens från [GroupDocs](https://purchase.groupdocs.com/temporary-license/) för att ta bort provbegränsningarna.

### Grundläggande initiering och konfiguration
Nedan är den minsta koden som behövs för att öppna en MKV‑fil med GroupDocs.Metadata.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class MetadataExtraction {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();
            // Access and manipulate metadata here
        }
    }
}
```

## Så extraherar du mkv metadata java med GroupDocs.Metadata
Nu dyker vi ner i varje metadata‑område du kan läsa.

### Läsa Matroska EBML‑rubrik
EBML‑rubriken lagrar grundläggande filinformation såsom version och dokumenttyp.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaEBMLHeader {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            String docType = root.getMatroskaPackage().getEbmlHeader().getDocType();
            String docTypeReadVersion = root.getMatroskaPackage().getEbmlHeader().getDocTypeReadVersion();
            String docTypeVersion = root.getMatroskaPackage().getEbmlHeader().getDocTypeVersion();
            String readVersion = root.getMatroskaPackage().getEbmlHeader().getReadVersion();
            String version = root.getMatroskaPackage().getEbmlHeader().getVersion();

            // Use the extracted header details as needed
        }
    }
}
```

**Key Points**
- `getRootPackageGeneric()` ger dig Matroska‑paketets ingångspunkt.  
- EBML‑egenskaper (`docType`, `version`, etc.) hjälper dig att verifiera filkompatibilitet.

### Läsa Matroska segmentinformation
Segment beskriver den övergripande mediatidslinjen och skapandeverktyg.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaSegmentInformation {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var segment : root.getMatroskaPackage().getSegments()) {
                String dateUtc = segment.getDateUtc();
                long duration = segment.getDuration();
                String muxingApp = segment.getMuxingApp();
                String segmentFilename = segment.getSegmentFilename();
                String segmentUid = segment.getSegmentUid();
                long timecodeScale = segment.getTimecodeScale();
                String title = segment.getTitle();
                String writingApp = segment.getWritingApp();

                // Process the extracted segment information as needed
            }
        }
    }
}
```

**Key Points**
- `getSegments()` returnerar en samling; varje segment kan ha sin egen titel, varaktighet och detaljer om skapandeapplikation.  
- Användbart för att bygga spellistor eller validera kodningsparametrar.

### Läsa Matroska tagg‑metadata
Taggar lagrar mänskligt läsbar information som titlar, artister eller anpassade anteckningar.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;
import com.groupdocs.metadata.core.MetadataProperty;

public class ReadMatroskaTagMetadata {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var tag : root.getMatroskaPackage().getTags()) {
                String targetType = tag.getTargetType();
                String targetTypeValue = tag.getTargetTypeValue();
                String tagTrackUid = tag.getTagTrackUid();

                for (MetadataProperty simpleTag : tag.getSimpleTags()) {
                    String name = simpleTag.getName();
                    String value = simpleTag.getValue();

                    // Utilize the extracted tag information as needed
                }
            }
        }
    }
}
```

**Key Points**
- Taggar är organiserade efter `targetType` (t.ex. `movie`, `track`).  
- `simpleTag`‑poster innehåller nyckel/värde‑par såsom `TITLE=My Video`.

### Läsa Matroska spår‑metadata
Spår representerar individuella audio-, video- eller undertextströmmar.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.MatroskaRootPackage;

public class ReadMatroskaTrackMetadata {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.mkv")) {
            MatroskaRootPackage root = metadata.getRootPackageGeneric();

            for (var track : root.getMatroskaPackage().getTracks()) {
                String trackType = track.getType();
                String codecId = track.getCodecId();
                String language = track.getLanguage();
                long duration = track.getDuration();
                
                // Process the extracted track information as needed
            }
        }
    }
}
```

**Key Points**
- `track.getType()` visar om det är video, audio eller undertexter.  
- `codecId` låter dig identifiera codec (t.ex. `V_MPEG4/ISO/AVC`).  
- Dessa data är avgörande för transkodningspipeline eller kvalitetskontroller.

## Vanliga problem & felsökning
| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-----|
| `NullPointerException` when accessing `getEbmlHeader()` | Filsökväg felaktig eller filen hittas inte | Verifiera sökvägen i `new Metadata("...")` och säkerställ att filen finns. |
| No tags returned | MKV‑filen saknar taggelement | Använd en mediFil som innehåller metadata‑taggar (t.ex. tillagda via MKVToolNix). |
| Slow processing on large files | Otillräckligt heap‑minne | Öka JVM‑heapen (`-Xmx2g` eller högre) eller bearbeta filen i delar om möjligt. |

## Vanliga frågor

**Q: Can I extract metadata from other video formats with the same library?**  
A: Ja, GroupDocs.Metadata stöder MP4, AVI, MOV och många fler. API‑mönstret är liknande—använd bara rätt rotpaket‑klass.

**Q: Is a license required for production use?**  
A: En licens tar bort provbegränsningar och ger full funktionalitet. Biblioteket fungerar i provläge för utvärdering.

**Q: Does the extraction happen offline?**  
A: Absolut. När JAR‑filen är på din classpath utförs alla metadata‑läsningar lokalt utan nätverksanrop.

**Q: How does this perform on very large MKV files (several GB)?**  
A: Biblioteket strömmar containerstrukturen, så minnesanvändningen förblir måttlig, men se till att din JVM har tillräckligt heap för eventuella stora tagg‑samlingar.

**Q: Can I modify the metadata and write it back to the file?**  
A: GroupDocs.Metadata fokuserar främst på läsning. Skrivfunktioner är begränsade; kontrollera den senaste API‑dokumentationen för eventuell skrivstöd.

## Slutsats
Du har nu en komplett, produktionsklar guide för **extracting mkv metadata java** med GroupDocs.Metadata. Genom att utnyttja EBML‑rubriker, segmentinformation, taggar och spårdetaljer kan du driva mediakataloger, automatisera kvalitetskontroller eller berika videoströmningstjänster. Experimentera med kodsnuttarna, anpassa dem till dina egna arbetsflöden och utforska bibliotekets bredare formatstöd för ännu fler möjligheter.

---

**Senast uppdaterad:** 2025-12-22  
**Testat med:** GroupDocs.Metadata 24.12 för Java  
**Författare:** GroupDocs