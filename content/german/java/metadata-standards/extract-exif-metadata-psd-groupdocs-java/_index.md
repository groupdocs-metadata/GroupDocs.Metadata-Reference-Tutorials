---
date: '2026-08-10'
description: Erfahren Sie, wie Sie EXIF-Metadaten aus PSD-Dateien mit GroupDocs.Metadata
  für Java extrahieren. Dieser Leitfaden behandelt die grundlegende Extraktion, IFD-Pakete,
  GPS-Daten und praxisnahe Anwendungsfälle.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Erfahren Sie, wie Sie EXIF-Metadaten aus PSD-Dateien mit GroupDocs.Metadata
  für Java extrahieren. Schritt‑für‑Schritt‑Anleitung, Code‑Beispiele und Fehlersuche‑Tipps
  für Entwickler.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: So extrahieren Sie EXIF-Metadaten aus PSD-Dateien mit GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: So extrahieren Sie EXIF-Metadaten aus PSD-Dateien mit GroupDocs.Metadata
type: docs
url: /de/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Wie man EXIF-Metadaten aus PSD-Dateien mit GroupDocs.Metadata extrahiert

Das Extrahieren von **EXIF-Metadaten** aus PSD-Dateien ist ein routinemäßiger, aber leistungsstarker Schritt, wenn Sie die Herkunft von Bildern prüfen, die automatische Kennzeichnung von Assets durchführen oder durchsuchbare Medienbibliotheken aufbauen müssen. In diesem Tutorial erfahren Sie, **wie man EXIF schnell extrahiert** mit GroupDocs.Metadata für Java, sehen die genauen API-Aufrufe und lernen, wie man erweiterte IFD-Pakete und GPS-Koordinaten verarbeitet. Am Ende sind Sie bereit, die Metadatenextraktion in jeden Java‑basierten Workflow zu integrieren.

## Schnelle Antworten

Die Klasse `Metadata` repräsentiert eine Datei und bietet Zugriff auf deren Metadaten.

- **Wie lautet die erste Codezeile?** `Metadata metadata = new Metadata("sample.psd");`
- **Welche Methode gibt den Künstlernamen zurück?** `metadata.getExif().getArtist();`
- **Kann ich GPS-Daten lesen?** Ja – verwenden Sie `metadata.getExif().getGpsInfo();`
- **Benötige ich eine Lizenz für die Produktion?** Eine gültige GroupDocs.Metadata-Lizenz ist nach dem Testzeitraum erforderlich.
- **Unterstützte Java-Version?** Java 8 oder neuer (bis Java 21).

## Was sind EXIF-Metadaten?

EXIF (Exchangeable Image File Format) Metadaten speichern Kameraeinstellungen, Erstellungszeitstempel und Standortdaten innerhalb von Bilddateien. GroupDocs.Metadata liest diese Informationen direkt aus der Binärstruktur von PSD-Dateien und stellt sie über eine saubere Java-API bereit. Sie ermöglicht Entwicklern, programmgesteuert Details wie Kameramodell, Belichtungszeit und GPS-Koordinaten abzurufen, ohne manuelle Inspektion.

## Warum GroupDocs.Metadata für Java verwenden?

GroupDocs.Metadata unterstützt **über 30 Dateiformate** (einschließlich PSD, JPEG, PNG, TIFF) und kann Dateien bis zu **2 GB** verarbeiten, ohne das gesamte Dokument in den Speicher zu laden. Die Bibliothek extrahiert **mehr als 150 verschiedene EXIF-Tags**, sodass Sie das vollständige Set an Kamera- und GPS-Attributen für Analysen oder Compliance erhalten.

## Voraussetzungen

- **Java Development Kit (JDK) 8** oder neuer auf Ihrem Rechner installiert.  
- **Maven** für die Abhängigkeitsverwaltung.  
- **GroupDocs.Metadata für Java Version 24.12** (oder neuer).  
- Grundlegende Kenntnisse in Java-Klassen, -Objekten und Ausnahmebehandlung.

### Erforderliche Bibliotheken und Abhängigkeiten
| Abhängigkeit | Maven-Koordinaten |
|--------------|--------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Umgebung einrichten
Sie sollten eine Maven‑kompatible IDE wie IntelliJ IDEA oder Eclipse besitzen. Erstellen Sie ein neues Maven‑Projekt oder fügen Sie die Abhängigkeit zu einem bestehenden Projekt hinzu.

## Wie man GroupDocs.Metadata für Java einrichtet
GroupDocs.Metadata kann mit wenigen Konfigurationszeilen zu einem Maven‑Projekt hinzugefügt werden. Die folgenden Schritte zeigen, wie das Repository und die Abhängigkeit eingebunden werden, sodass die Bibliothek im Klassenpfad verfügbar ist.

### Maven‑Einrichtung
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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

### Direkter Download
Alternativ laden Sie das neueste JAR von der offiziellen Release‑Seite herunter: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Lizenzbeschaffung
Um die Bibliothek über die 30‑tägige Testphase hinaus zu nutzen, erhalten Sie eine temporäre oder vollständige Lizenz:

1. Besuchen Sie die [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Wählen Sie **temporary** für Tests oder **full** für die Produktion.  
3. Folgen Sie den Anweisungen auf dem Bildschirm, um die Lizenzdatei (`metadata.lic`) in Ihren Java‑Klassenpfad einzubetten.

### Grundlegende Initialisierung und Einrichtung
After the library is on the classpath, initialize it as shown below:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Wie man grundlegende EXIF-Metadaten‑Eigenschaften aus einem PSD‑Bild extrahiert
Dieser Abschnitt erklärt, wie man eine PSD‑Datei lädt, auf den EXIF‑Container zugreift und die gängigsten Tags wie **artist**, **copyright** und **software** liest. Der Vorgang beinhaltet das Erstellen einer `Metadata`‑Instanz, den Aufruf von `getExif()` und das Abrufen einzelner Eigenschaften mittels einfacher Getter‑Methoden.

### Schritt‑für‑Schritt‑Implementierung
1. **Erstellen Sie eine `Metadata`‑Instanz**, die auf Ihre PSD‑Datei zeigt.  
2. **Rufen Sie `getExif()`** auf, um den EXIF‑Container zu erhalten.  
3. **Lesen Sie einzelne Eigenschaften** wie `getArtist()`, `getCopyright()` und `getSoftware()`.  
4. **Geben Sie die Werte aus oder speichern Sie sie** gemäß Ihrer Anwendungslogik.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Pro Tipp:** Das `Metadata`‑Objekt erkennt das Dateiformat automatisch, sodass Sie denselben Code für JPEG‑ oder TIFF‑Dateien ohne Änderungen wiederverwenden können.

## Wie man EXIF‑IFD‑Paket‑Eigenschaften aus einem PSD‑Bild extrahiert
Der IFD (Image File Directory)-Abschnitt enthält tiefere technische Details wie **camera serial number**, **lens model** und **user comments**. `Ifd0` stellt das primäre Image File Directory dar, das grundlegende Kamerainformationen enthält. Das Extrahieren dieser Felder ist nützlich für forensische Analysen oder hochpräzise Katalogisierung.

### Implementierungsschritte
1. **Verwenden Sie die `Metadata`‑Instanz** aus dem vorherigen Abschnitt erneut.  
2. **Navigieren Sie zum IFD‑Container** über `metadata.getExif().getIfd0()`.  
3. **Lesen Sie Eigenschaften** wie `getBodySerialNumber()` und `getUserComment()`.  
4. **Geben Sie die Daten aus** oder ordnen Sie sie Ihrem Domänenmodell zu.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Wie man GPS-Daten (Breitengrad, Längengrad) aus einer PSD‑Datei abruft
Viele moderne Kameras betten GPS‑Koordinaten im EXIF‑Block ein. `GpsInfo` enthält geografische Koordinaten, die aus den EXIF‑Daten extrahiert wurden. Rufen Sie `metadata.getExif().getGpsInfo()` auf und verwenden Sie anschließend `getLatitude()`, `getLongitude()` und `getAltitude()`, um präzise Standortdaten zu erhalten – keine zusätzliche Analyse erforderlich.

### Detaillierte Schritte
1. **Erhalten Sie das GPS‑Info‑Objekt**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Lesen Sie Breitengrad und Längengrad**: `gps.getLatitude()` gibt ein `double` in Dezimalgrad zurück.  
3. **Fehlende Daten behandeln**: Die API gibt `null` zurück, wenn das Tag fehlt, daher sollten Sie `NullPointerException` vermeiden.

> **Häufiges Problem:** Einige PSD‑Dateien speichern GPS‑Koordinaten als rationale Zahlen; die Bibliothek normalisiert sie automatisch, aber ältere Dateien können eine manuelle Umwandlung erfordern.

## Häufige Probleme und Fehlersuche
| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| `Unsupported format` exception | Verwendung einer älteren GroupDocs.Metadata-Version, die PSD nicht erkennt | Auf Version 24.12 oder neuer aktualisieren |
| `NullPointerException` when calling `getArtist()` | EXIF‑Tag im Quellfile nicht vorhanden | Vor dem Lesen `metadata.getExif().hasArtist()` prüfen |
| License error after 30 days | Lizenzdatei nicht im Klassenpfad gefunden | `metadata.lic` in `src/main/resources` ablegen oder `Metadata.setLicense("path/to/license")` setzen |

## Häufig gestellte Fragen

**Q: Kann ich EXIF‑Metadaten aus einer passwortgeschützten PSD‑Datei extrahieren?**  
A: Ja. Laden Sie die Datei mit `new Metadata("file.psd", "password")` und greifen Sie anschließend wie üblich auf die EXIF‑Daten zu.

**Q: Unterstützt GroupDocs.Metadata die Stapelverarbeitung vieler PSD‑Dateien?**  
A: Absolut. Instanziieren Sie ein `Metadata`‑Objekt innerhalb einer Schleife oder verwenden Sie den `MetadataCollection`‑Helper, um Verzeichnisse effizient zu verarbeiten.

**Q: Welche Java‑Versionen werden offiziell unterstützt?**  
A: Java 8 bis Java 21 sind vollständig getestet. Die Bibliothek verwendet nur Standard‑APIs, sodass sie auf jeder konformen JVM funktioniert.

**Q: Ist es möglich, EXIF‑Daten zurück in eine PSD‑Datei zu schreiben?**  
A: Ja. Nachdem Sie Eigenschaften über das `Exif`‑Objekt geändert haben, rufen Sie `metadata.save("output.psd")` auf, um die Änderungen zu speichern.

**Q: Wie groß kann eine PSD‑Datei sein, die die Bibliothek verarbeiten kann, ohne dass der Speicher ausgeht?**  
A: GroupDocs.Metadata streamt Daten und kann Dateien bis zu **2 GB** auf einer typischen 8 GB‑RAM‑Maschine verarbeiten, dank seiner Low‑Memory‑Architektur.

## Fazit
Sie wissen jetzt, **wie man EXIF**‑Metadaten aus PSD‑Dateien mit GroupDocs.Metadata für Java extrahiert, von grundlegenden Tags bis zu fortgeschrittenen IFD‑ und GPS‑Informationen. Integrieren Sie diese Code‑Snippets in Ihre Bildverarbeitungspipeline, um Katalogisierung, Compliance‑Prüfungen oder standortbasierte Dienste zu automatisieren. Für weiterführende Untersuchungen versuchen Sie, Metadaten aus anderen unterstützten Formaten (JPEG, TIFF, PNG) zu extrahieren oder experimentieren Sie mit den Schreib‑Back‑Funktionen, um benutzerdefinierte Tags einzubetten.

---

**Zuletzt aktualisiert:** 2026-08-10  
**Getestet mit:** GroupDocs.Metadata 24.12 für Java  
**Autor:** GroupDocs

## Verwandte Tutorials

- [Bildressourcen aus PSD-Dateien mit GroupDocs.Metadata in Java extrahieren: Ein umfassender Leitfaden](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [PSD-Header und Ebeneninformationen mit GroupDocs.Metadata für Java extrahieren: Ein umfassender Leitfaden](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [MakerNote‑Eigenschaften als TIFF/EXIF‑Tags mit GroupDocs.Metadata in Java extrahieren](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)