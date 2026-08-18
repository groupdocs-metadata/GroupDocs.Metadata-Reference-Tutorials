---
date: '2026-08-05'
description: Erfahren Sie, wie Sie die PDF-Version in Java erkennen und PDF-Metadaten
  mit GroupDocs.Metadata für Java aktualisieren. Enthält Versionserkennung, Auslesen
  von Eigenschaften und Metadatenbearbeitung.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Erkennen Sie die PDF-Version in Java und aktualisieren Sie PDF-Metadaten
  mit GroupDocs.Metadata. Schritt‑für‑Schritt‑Java‑Anleitung zeigt Versionserkennung,
  Auslesen von Eigenschaften und Metadatenbearbeitung.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: PDF-Version in Java erkennen und PDF-Metadaten aktualisieren
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: PDF-Version in Java erkennen und PDF-Metadaten aktualisieren
type: docs
url: /de/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# PDF-Version in Java erkennen und PDF-Metadaten aktualisieren

Die programmgesteuerte Verwaltung von PDF-Dateien bedeutet häufig, dass Sie **PDF-Version in Java erkennen** und **PDF-Metadaten aktualisieren** — Autor, Titel, Erstellungsdatum oder sogar die PDF-Version selbst. Inkonsistente Metadaten können Darstellungsfehler verursachen oder das Auffinden von Dokumenten in einem großen Repository erschweren. Dieses Tutorial führt Sie durch das Erkennen der PDF-Version und das Aktualisieren von PDF-Metadaten mit **GroupDocs.Metadata** für Java und bietet Ihnen eine zuverlässige Methode, Ihre PDFs ordentlich, durchsuchbar und mit jedem Viewer kompatibel zu halten.

## Schnelle Antworten
- **Was bedeutet „PDF-Metadaten aktualisieren“?** Hinzufügen, Ändern oder Entfernen von Informationen, die in einer PDF-Datei gespeichert sind.  
- **Welche Bibliothek unterstützt dies in Java?** GroupDocs.Metadata.  
- **Kann ich auch die PDF-Version erkennen?** Ja, dieselbe API bietet die Versionsdetektion.  
- **Brauche ich eine Lizenz?** Eine kostenlose Testversion ist für die Evaluierung ausreichend; für die Produktion ist eine kostenpflichtige Lizenz erforderlich.  
- **Welche Java-Version wird benötigt?** JDK 8 oder neuer.

## Was bedeutet das Aktualisieren von PDF-Metadaten?

Das Aktualisieren von PDF-Metadaten bedeutet, dass die beschreibenden Informationen, die in einer PDF-Datei eingebettet sind, programmgesteuert gelesen und geschrieben werden — wie Autor, Titel, Betreff und benutzerdefinierte Eigenschaften. Korrekte Metadaten verbessern die Durchsuchbarkeit, die Einhaltung von Vorschriften und die Versionskontrolle in Dokumentenmanagementsystemen. Präzise Metadaten ermöglichen zudem automatisches Indexieren, Compliance-Berichte und Versionsverfolgung in Dokumentenmanagementsystemen.

## Warum die PDF-Version in Java erkennen?

Das Erkennen der PDF-Version ermöglicht es Ihnen zu überprüfen, ob eine Datei im Ziel‑Viewer korrekt dargestellt wird und ob sie die Anforderungen nachgelagerter Verarbeitung erfüllt. Zu wissen, ob eine PDF-Version 1.4, 1.7 oder neuer ist, hilft Ihnen, Kompatibilitätsregeln vor dem Archivieren, Veröffentlichen oder Konvertieren des Dokuments durchzusetzen.

## Voraussetzungen

- **Java Development Kit (JDK)** 8 oder höher.  
- **Maven** für das Abhängigkeitsmanagement (oder Sie können das JAR direkt herunterladen).  
- Grundlegende Kenntnisse im Umgang mit Java‑Datei‑I/O.

## Einrichtung von GroupDocs.Metadata für Java

### Maven-Konfiguration
Fügen Sie das Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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
Alternativ können Sie das neueste JAR von der offiziellen Release‑Seite herunterladen: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Schritte zum Erwerb einer Lizenz
- **Kostenlose Testversion** – beginnen Sie mit dem Experimentieren ohne Kosten.  
- **Temporäre Lizenz** – verlängern Sie die Testphase bei Bedarf.  
- **Kauf** – erhalten Sie eine Voll‑Funktions‑Lizenz für den Produktionseinsatz.

## Grundlegende Initialisierung und Einrichtung

Die Klasse `Metadata` ist der Einstiegspunkt für die Arbeit mit PDF-Dateien in GroupDocs.Metadata. Sie stellt einen Container dar, der Ihnen Lese‑/Schreibzugriff auf Dokumenteneigenschaften, Versionsinformationen und benutzerdefinierte XMP‑Daten bietet.

Erstellen Sie eine `Metadata`‑Instanz, die auf Ihre PDF‑Datei verweist:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Jetzt sind Sie bereit, Eigenschaften zu lesen, die Version zu erkennen und Metadaten zu aktualisieren.

## Wie man die PDF-Version in Java erkennt

Laden Sie Ihre PDF mit `new Metadata("sample.pdf")` und rufen Sie `getRootPackage().getVersion()` auf — die Methode gibt die genaue PDF-Version (z. B. 1.4, 1.7) in einem einzigen Aufruf zurück. Diese direkte Antwort ermöglicht es Ihnen, die Kompatibilität schnell zu prüfen, bevor weitere Verarbeitungsschritte erfolgen. Der Versionsstring spiegelt das PDF‑Spezifikationsniveau wider, dem die Datei entspricht, was für Kompatibilitätsprüfungen entscheidend ist.  
`getVersion()` gibt die PDF-Version als Zeichenkette zurück, z. B. "1.4" oder "1.7".

### Schritt‑für‑Schritt‑Anleitung

1. **PDF öffnen** – instanziieren Sie das `Metadata`‑Objekt (siehe Initialisierung oben).  
2. **Zugriff auf das PDF‑spezifische Root‑Package** – rufen Sie `metadata.getRootPackage()` auf.  
3. **Version abrufen** – rufen Sie `pdfRoot.getVersion()` auf; die zurückgegebene Zeichenkette enthält die Versionsnummer.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Pro Tipp:** Verwenden Sie den `version`‑Wert, um Kompatibilitätsprüfungen vor der Verarbeitung einer PDF‑Charge durchzusetzen.

#### Fehlerbehebung
- Überprüfen Sie den Dateipfad; ein falscher Pfad löst `FileNotFoundException` aus.  
- Stellen Sie sicher, dass die GroupDocs.Metadata‑Version zu Ihrem JDK passt (im Beispiel wird 24.12 verwendet).

## Wie man PDF‑Eigenschaften in Java liest

`DocumentInfo` bietet Zugriff auf standardmäßige PDF‑Metadatenfelder, ohne das gesamte Dokument zu laden. Die Klasse `DocumentInfo` ermöglicht den Zugriff auf Standard‑PDF‑Eigenschaften wie Autor, Titel und Erstellungsdatum. Es ist ein leichtgewichtiger Wrapper, der Metadaten liest, ohne das gesamte Dokument in den Speicher zu laden.

Erstellen Sie eine `DocumentInfo`‑Instanz aus dem geöffneten `Metadata`‑Objekt:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

Sie können dann Getter wie `getAuthor()`, `getTitle()` und `getCreationDate()` aufrufen, um Werte abzurufen.

## Wie man PDF‑Metadaten in Java aktualisiert

Laden Sie die PDF (wie oben), erhalten Sie das `DocumentInfo`‑Package, ändern Sie die gewünschten Felder und speichern Sie die Änderungen. Der Vorgang überschreibt den bestehenden Metadaten‑Block, während der Rest des Dokuments erhalten bleibt. Nach dem Ändern der Felder schreibt ein Aufruf von `save()` die Änderungen zurück in die Datei und bewahrt die Inhaltsströme.

Die Klasse `DocumentInfo` ist das Objekt von GroupDocs.Metadata zum Bearbeiten von PDF‑Ebene‑Eigenschaften wie Autor, Titel, Betreff und benutzerdefinierten XMP‑Feldern.

Aktualisieren Sie die Metadatenfelder:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Hinweis:** Die Setter‑Aufrufe folgen dem gleichen Muster wie die zuvor gezeigten Getter, wodurch die API intuitiv und konsistent ist.

#### Häufige Fallstricke
- Der Versuch, Metadaten in einer PDF zu ändern, die die Ziel‑Eigenschaft nicht enthält, gibt `null` zurück — prüfen Sie immer auf `null`, bevor Sie einen neuen Wert setzen.  
- Große PDFs können einen erhöhten JVM‑Heap benötigen; überwachen Sie die Speichernutzung während Batch‑Updates.

## Praktische Anwendungsfälle

1. **Compliance‑Audits** – Verifizieren Sie, dass alle PDFs vor der rechtlichen Einreichung eine Mindestversion (z. B. 1.7) erfüllen.  
2. **Automatisierte Archivierung** – Kennzeichnen Sie PDFs mit Autor, Abteilung und Erstellungsdatum für eine einfachere Wiederauffindung.  
3. **Integration in Dokumentenmanagement** – Bereichern Sie PDFs mit benutzerdefinierten Eigenschaften, die DMS‑Plattformen indexieren können.  
4. **Berichtserstellung** – Fügen Sie Versionsinformationen in automatisch generierte Berichte ein.  
5. **Cross‑Platform‑Testing** – Erkennen Sie Versionskonflikte, die auf älteren Viewern Darstellungsprobleme verursachen könnten.

## Leistungstipps

- **Verwenden Sie try‑with‑resources** (wie gezeigt), um `Metadata`‑Objekte automatisch zu schließen.  
- **Batch‑Verarbeitung** mehrerer Dateien in einer Schleife, um den Overhead zu reduzieren.  
- **Heap überwachen** bei sehr großen PDFs; erwägen Sie die Verarbeitung in Teilen, wenn Speichergrenzen erreicht werden.  
- **GroupDocs.Metadata unterstützt über 50 Eingabe‑ und Ausgabeformate** und kann Metadaten aus mehrseitigen PDFs lesen, ohne die gesamte Datei in den Speicher zu laden, und liefert schnelle Leistung auf Standard‑Serverhardware.

## Häufig gestellte Fragen

**Q: Kann ich Metadaten in passwortgeschützten PDFs aktualisieren?**  
A: Ja, Sie müssen jedoch das Passwort beim Erstellen des `Metadata`‑Objekts angeben.

**Q: Unterstützt GroupDocs.Metadata benutzerdefinierte XMP‑Eigenschaften?**  
A: Absolut. Sie können benutzerdefinierte XMP‑Felder über dieselbe API lesen und schreiben.

**Q: Ist es möglich, die PDF-Version selbst zu ändern?**  
A: Die Bibliothek kann die Version melden; das Ändern erfordert das Speichern des Dokuments mit einem anderen Versionsprofil, was über zusätzliche Speicheroptionen unterstützt wird.

**Q: Was passiert, wenn die PDF keine vorhandenen Metadaten hat?**  
A: Die Getter geben `null` zurück. Sie können die Setter sicher aufrufen, um neue Metadaten‑Einträge zu erstellen.

**Q: Gibt es Lizenzbeschränkungen für die kommerzielle Nutzung?**  
A: Für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich; die Testversion ist auf Evaluierungszwecke beschränkt.

---

**Zuletzt aktualisiert:** 2026-08-05  
**Getestet mit:** GroupDocs.Metadata 24.12 für Java  
**Autor:** GroupDocs

## Verwandte Tutorials

- [PDF-Metadaten effizient mit GroupDocs.Metadata in Java für das Dokumentenmanagement aktualisieren](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Metadata-Management meistern: Dokumenteigenschaften & Verschlüsselungsstatus mit GroupDocs.Metadata für Java erkennen](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Dokumentvorschau in Java erstellen – GroupDocs.Metadata Tutorials](/metadata/java/document-formats/)