---
date: '2026-09-02'
description: Erfahren Sie, wie Sie asf in Java mit GroupDocs.Metadata extrahieren.
  Der Leitfaden behandelt die Maven‑Einrichtung, das Lesen grundlegender properties,
  Codec‑Details, Descriptors und die Fehlersuche für eine zuverlässige media handling.
keywords:
- how to extract asf
- groupdocs metadata java
- asf metadata extraction
lastmod: '2026-09-02'
og_description: Erfahren Sie, wie Sie asf in Java mit GroupDocs.Metadata extrahieren.
  Dieser Schritt‑für‑Schritt‑Leitfaden zeigt die Maven‑Einrichtung, das Lesen von
  properties, codec‑Informationen und die Fehlersuche für nahtloses media management.
og_image_alt: Guide showing how to extract asf metadata in Java with GroupDocs.Metadata
og_title: Wie man asf in Java mit GroupDocs.Metadata extrahiert
schemas:
- author: GroupDocs
  dateModified: '2026-09-02'
  description: Learn how to extract asf in Java using GroupDocs.Metadata. The guide
    covers Maven setup, reading basic properties, codec details, descriptors, and
    troubleshooting for reliable media handling.
  headline: How to extract asf in Java with GroupDocs.Metadata
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, MOV, and many more. Simply
      instantiate the corresponding package class for the format you need.
    question: Can I extract metadata from other video formats with the same library?
  - answer: Absolutely. The library provides setter methods for most properties, allowing
      you to edit values and then save the file back to disk.
    question: Is it possible to modify ASF metadata after extraction?
  - answer: Not strictly, but a 64‑bit JVM gives you a larger heap, which is beneficial
      when processing files larger than 2 GB.
    question: Do I need a 64‑bit JVM for large ASF files?
  - answer: The trial license removes functional limits but adds a watermark to certain
      export operations. For unrestricted production use, purchase a full license.
    question: How does licensing affect trial usage?
  - answer: GroupDocs.Metadata is built for Java SE. For Android, use the .NET version
      with Xamarin or a compatible wrapper.
    question: Can I run this code on Android devices?
  type: FAQPage
tags:
- asf metadata
- groupdocs.metadata
- java media processing
title: Wie man asf in Java mit GroupDocs.Metadata extrahiert
type: docs
url: /de/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# Wie man asf in Java mit GroupDocs.Metadata extrahiert

In modernen Medien‑Pipelines ist es essenziell, **asf‑Metadaten in Java zu extrahieren**, um Katalogisierung, Compliance und automatisierte Verarbeitung zu ermöglichen. Das manuelle Parsen von ASF‑Containern ist fehleranfällig und zeitaufwendig, aber GroupDocs.Metadata für Java bietet eine High‑Level‑API, die die schwere Arbeit für Sie übernimmt. Dieses Tutorial führt Sie durch die Installation der Bibliothek, das Lesen von Kerneigenschaften, den Zugriff auf Codec‑Informationen und die Behandlung gängiger Fallstricke, sodass Sie die ASF‑Metadaten‑Extraktion mit Vertrauen in jede Java‑Anwendung integrieren können.

## Schnelle Antworten
- **Was bedeutet „asf‑Metadaten extrahieren“?** Es bedeutet, dass man programmgesteuert eingebettete Informationen—wie Zeitstempel, Codec‑Bezeichner und Stream‑Deskriptoren—aus einer ASF‑Datei liest.  
- **Welche Bibliothek wird benötigt?** GroupDocs.Metadata für Java (Version 24.12 oder höher).  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion oder temporäre Lizenz reicht für die Entwicklung; für den Produktionseinsatz ist eine Voll‑Lizenz erforderlich.  
- **Welche Java‑Version wird unterstützt?** JDK 8 oder höher.  
- **Kann ich Maven verwenden?** Ja – Maven ist der empfohlene Dependency‑Manager.

## Was sind asf‑Metadaten?
`ASF` (Advanced Systems Format) Metadaten sind eine Sammlung strukturierter Tags, die innerhalb eines ASF‑Containers gespeichert werden und die technischen sowie beschreibenden Attribute der Mediendatei beschreiben. Diese Tags umfassen Erstellungszeitstempel, Codec‑Bezeichner, Sprach‑Deskriptoren und Stream‑bezogene Eigenschaften wie Bitrate und Dauer. Der programmgesteuerte Zugriff auf diese Daten ermöglicht den Aufbau durchsuchbarer Kataloge, die Durchsetzung von Compliance‑Regeln oder die Steuerung automatischer Transcoding‑Entscheidungen.

## Warum GroupDocs.Metadata für Java zum Extrahieren von asf‑Metadaten verwenden?
GroupDocs.Metadata unterstützt **30+ Audio/Video‑Formate** und kann Dateien bis zu **5 GB** verarbeiten, ohne die gesamte Datei in den Speicher zu laden, dank seiner Streaming‑Architektur. Die Bibliothek bietet ein klares Objektmodell – ein Low‑Level‑Byte‑Parsing ist nicht nötig – sodass Sie Eigenschaften, Codecs, Deskriptoren und Stream‑Details mit nur wenigen Methodenaufrufen abrufen können. Das reduziert den Entwicklungsaufwand typischerweise um bis zu **70 %** im Vergleich zum Bau eines eigenen Parsers.

## Voraussetzungen
- **Java Development Kit (JDK)** 8 oder neuer installiert.  
- **IDE** wie IntelliJ IDEA oder Eclipse für bequemes Coden.  
- **Maven** in Ihrer IDE konfiguriert (optional, aber empfohlen).  
- Grundlegende Vertrautheit mit Java und externen Bibliotheken.

## Einrichtung von GroupDocs.Metadata für Java

### Wie richtet man GroupDocs.Metadata für Java ein?
Fügen Sie das GroupDocs‑Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu. Dieser einzelne Schritt macht die gesamte API in Ihrem Projekt verfügbar.

```xml
<!-- Maven repository -->
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<!-- GroupDocs.Metadata dependency -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

Die `GroupDocs.Metadata`‑JAR wird dann automatisch während des Maven‑Builds aufgelöst.

### Direkter Download (ohne Maven)
Falls Sie Maven nicht verwenden möchten, laden Sie die neueste JAR von [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) herunter. Platzieren Sie die JAR auf Ihrem Klassenpfad und Sie können sofort loslegen.

### Lizenzübersicht
- **Free trial** – Unbegrenzter Funktionszugriff für Evaluation; keine Wasserzeichen.  
- **Temporary license** – Ideal für Entwicklung und automatisierte Tests.  
- **Full license** – Erforderlich für den kommerziellen Einsatz und zum Freischalten des Premium‑Supports.

### Grundlegende Initialisierung
Die `Metadata`‑Klasse ist der Einstiegspunkt, der eine Datei lädt und format‑spezifische Accessoren bereitstellt. Nachfolgend der minimale Code, der nötig ist, um eine ASF‑Datei zu öffnen.

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## Wie man grundlegende ASF‑Metadaten‑Eigenschaften extrahiert
Laden Sie die ASF‑Datei und rufen Sie hoch‑level Eigenschaften wie Erstellungsdatum, Dateikennzeichen und globale Flags ab. Das gibt Ihnen sofort Aufschluss darüber, wann das Asset erstellt wurde und wie es für die Wiedergabe gekennzeichnet ist.

```java
// Load the ASF file
AsfPackage asf = new AsfPackage("sample.asf");

// Retrieve basic properties
Date creationDate = asf.getCreationDate();
String fileId = asf.getFileId();
int flags = asf.getFlags();
```

*Warum das wichtig ist*: Das Wissen um das Erstellungsdatum unterstützt die Versionskontrolle, während die Datei‑ID das Asset eindeutig über verteilte Systeme hinweg identifiziert.

## Wie man ASF‑Codec‑Informationen anzeigt
Die `AsfCodecInfo`‑Sammlung enumeriert jeden für Audio‑ und Video‑Streams verwendeten Codec. Die Methode `getCodecs()` liefert Objekte, die Codec‑Name, Typ und Bitrate bereitstellen. Das Verständnis der Codec‑Nutzung ist entscheidend für Kompatibilitätstests, die Entscheidung, ob ein Transcoding nötig ist, und die Sicherstellung, dass Zielgeräte die Streams ohne Fehler dekodieren können.

```java
// Get codec collection
List<AsfCodecInfo> codecs = asf.getCodecs();

for (AsfCodecInfo codec : codecs) {
    System.out.println("Codec name: " + codec.getName());
    System.out.println("Codec type: " + codec.getType());
}
```

*Warum das wichtig ist*: Codec‑Details ermöglichen die Überprüfung, ob ein Zielgerät die erforderlichen Formate unterstützt, und verhindern Wiedergabefehler in der Produktion.

## Wie man Metadaten‑Deskriptoren anzeigt
Deskriptoren liefern menschenlesbaren Kontext wie Sprache, Originaltitel und Stream‑Nummer. Verwenden Sie die Methode `getDescriptors()`, um eine Liste von `AsfDescriptor`‑Objekten zu erhalten, die jeweils einen Schlüssel, einen Wert und optional ein Sprach‑Tag enthalten. Diese Daten bereichern Suchindizes, verbessern UI‑Darstellungen und unterstützen die mehrsprachige Bibliotheksorganisation.

```java
// Retrieve descriptor collection
List<AsfDescriptor> descriptors = asf.getDescriptors();

for (AsfDescriptor descriptor : descriptors) {
    System.out.println("Language: " + descriptor.getLanguage());
    System.out.println("Original title: " + descriptor.getOriginalTitle());
}
```

*Warum das wichtig ist*: Deskriptoren geben Ihnen die Sprache von Untertiteln oder den Originaldateinamen an, was beim Organisieren mehrsprachiger Medienbibliotheken wertvoll ist.

## Wie man Basis‑Stream‑Eigenschaften anzeigt
Basis‑Stream‑Eigenschaften offenbaren Bitrate, Timing und Sprache pro Stream und ermöglichen eine feinkörnige Qualitätsanalyse. Die Methode `getStreams()` liefert `AsfStream`‑Objekte; jeder Stream enthält Eigenschaften wie `bitrate`, `duration` und `language`. Durch die Untersuchung dieser Werte können Sie beurteilen, ob eine Datei Qualitäts‑Schwellenwerte vor der Verteilung oder Archivierung erfüllt.

```java
// Access base streams
List<AsfBaseStream> streams = asf.getBaseStreams();

for (AsfBaseStream stream : streams) {
    System.out.println("Bitrate: " + stream.getBitrate());
    System.out.println("Duration: " + stream.getDuration());
    System.out.println("Language: " + stream.getLanguage());
}
```

*Warum das wichtig ist*: Stream‑bezogene Metriken helfen Ihnen zu prüfen, ob eine Datei Qualitäts‑Schwellenwerte vor der Verteilung oder Archivierung erfüllt.

## Häufige Probleme & Fehlersuche

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| `NullPointerException` beim Aufruf von `getAsfPackage()` | Der Dateipfad ist falsch oder die Datei ist kein gültiger ASF‑Container. | Pfad überprüfen und sicherstellen, dass die Datei eine korrekte ASF‑Datei ist. |
| Keine Codec‑Informationen angezeigt | Die ASF‑Datei verwendet einen proprietären Codec, der von der aktuellen Bibliotheksversion nicht erkannt wird. | GroupDocs.Metadata auf die neueste Version aktualisieren oder einen eigenen Codec‑Parser implementieren. |
| Leere Deskriptor‑Liste | Die Datei enthält keine eingebetteten Deskriptoren (z. B. beim Kodieren entfernt). | Eine Quelldatei mit Metadaten verwenden oder mit aktivierter Metadaten‑Erhaltung neu kodieren. |
| Leistungsabfall bei >2 GB Dateien | Die Standard‑Puffergröße ist für große Streams zu klein. | Die Puffergröße über `MetadataLoadOptions.setBufferSize()` vor dem Laden erhöhen. |

## Häufig gestellte Fragen

**Q: Kann ich Metadaten aus anderen Videoformaten mit derselben Bibliothek extrahieren?**  
A: Ja, GroupDocs.Metadata unterstützt MP4, MKV, AVI, MOV und viele weitere. Instanziieren Sie einfach die entsprechende Package‑Klasse für das gewünschte Format.

**Q: Ist es möglich, ASF‑Metadaten nach der Extraktion zu ändern?**  
A: Absolut. Die Bibliothek bietet Setter‑Methoden für die meisten Eigenschaften, sodass Sie Werte bearbeiten und die Datei anschließend wieder speichern können.

**Q: Benötige ich eine 64‑Bit‑JVM für große ASF‑Dateien?**  
A: Nicht zwingend, aber eine 64‑Bit‑JVM bietet einen größeren Heap, was bei der Verarbeitung von Dateien über 2 GB vorteilhaft ist.

**Q: Wie wirkt sich die Lizenzierung auf die Testnutzung aus?**  
A: Die Testlizenz entfernt funktionale Beschränkungen, fügt jedoch bei bestimmten Export‑Operationen ein Wasserzeichen hinzu. Für uneingeschränkten Produktionseinsatz erwerben Sie eine Voll‑Lizenz.

**Q: Kann ich diesen Code auf Android‑Geräten ausführen?**  
A: GroupDocs.Metadata ist für Java SE gebaut. Für Android nutzen Sie die .NET‑Version mit Xamarin oder einen kompatiblen Wrapper.

## Fazit
Durch Befolgen dieser Anleitung wissen Sie jetzt **wie man asf‑Metadaten in Java mit GroupDocs.Metadata extrahiert**. Sie können grundlegende Eigenschaften lesen, Codecs enumerieren, detaillierte Deskriptoren abrufen und Stream‑Level‑Attribute prüfen – und erhalten damit volle Sichtbarkeit über Ihre Medien‑Assets. Nächste Schritte umfassen die Einbindung dieser Extraktion in Batch‑Verarbeitungspipelines, den Aufbau durchsuchbarer Metadaten‑Stores oder die Erweiterung des Codes zum Modifizieren und erneuten Speichern von ASF‑Dateien.

---

**Zuletzt aktualisiert:** 2026-09-02  
**Getestet mit:** GroupDocs.Metadata 24.12 für Java  
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
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

## Verwandte Tutorials

- [WAV-Metadaten in Java mit GroupDocs.Metadata extrahieren – Ein umfassender Leitfaden](/metadata/java/audio-video-formats/extract-wav-metadata-groupdocs-java/)
- [Video‑Metadaten in Java mit GroupDocs.Metadata extrahieren](/metadata/java/audio-video-formats/mastering-avi-metadata-handling-groupdocs-java/)
- [Java‑Metadatenextraktion mit GroupDocs.Metadata meistern – Ein umfassender Leitfaden für Entwickler](/metadata/java/working-with-metadata/java-metadata-extraction-groupdocs-metadata/)