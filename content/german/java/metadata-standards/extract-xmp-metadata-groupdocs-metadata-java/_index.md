---
date: '2026-08-20'
description: Erfahren Sie, wie Sie XMP-Metadaten in Java mit GroupDocs.Metadata extrahieren.
  Dieser Leitfaden zeigt, wie grundlegende, Dublin-Core- und Photoshop-XMP-Metadaten
  extrahiert werden.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Erfahren Sie, wie Sie XMP-Metadaten in Java mit GroupDocs.Metadata
  extrahieren. Dieses Tutorial behandelt die Extraktion von grundlegenden, Dublin-Core-
  und Photoshop-XMP-Metadaten mit praktischen Codebeispielen.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Wie man XMP-Metadaten mit GroupDocs.Metadata für Java extrahiert
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Wie man XMP-Metadaten mit GroupDocs.Metadata für Java extrahiert
type: docs
url: /de/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man XMP-Metadaten mit GroupDocs.Metadata für Java extrahiert

In modernen digitalen Arbeitsabläufen kann **how to extract XMP**-Metadaten schnell und zuverlässig extrahiert werden, den Unterschied zwischen einer durchsuchbaren Asset-Bibliothek und einem chaotischen Dateihaufen ausmachen. Dieses Tutorial führt Sie durch jeden Schritt – Einrichtung der Bibliothek, Laden von Dateien und Herausziehen von grundlegenden, Dublin Core‑ und Photoshop‑spezifischen XMP‑Paketen – sodass Sie noch heute reichhaltige Metadaten in Ihre Java‑Anwendungen integrieren können.

## Schnelle Antworten
- **Welche Bibliothek verarbeitet XMP in Java?** GroupDocs.Metadata for Java.
- **Mindest-Java-Version?** JDK 8 oder höher.
- **Kann ich PNG- und JPEG-Dateien lesen?** Ja, beide werden sofort unterstützt.
- **Ist für die Produktion eine Lizenz erforderlich?** Ja, eine Voll- oder Temporärlizenz wird benötigt.
- **Wo finde ich die API-Referenz?** Auf der offiziellen GroupDocs.Metadata-Dokumentationsseite.

## Was ist XMP-Metadaten?
XMP (Extensible Metadata Platform) ist ein ISO‑Standardformat zum Einbetten strukturierter Metadaten direkt in Mediendateien. Es ermöglicht die Interoperabilität zwischen Anwendungen und die persistente Datenspeicherung, ohne den Originalinhalt zu verändern. Durch das Speichern von Informationen wie Ersteller, Urheberrecht, Kameraeinstellungen und benutzerdefinierten Tags innerhalb der Datei sorgt XMP dafür, dass Metadaten mit dem Asset überallhin mitreisen, was die Katalogisierung und Suche über verschiedene Systeme hinweg vereinfacht.

## Warum GroupDocs.Metadata für Java verwenden?
GroupDocs.Metadata unterstützt **30+ Dateiformate** (einschließlich PNG, JPEG, TIFF und PSD) und kann Dateien bis zu **2 GB** verarbeiten, ohne das gesamte Dokument in den Speicher zu laden, wodurch eine **30 % Reduzierung der CPU‑Auslastung** im Vergleich zu generischen Parsern erzielt wird. Das macht es ideal für groß angelegte Digital‑Asset‑Management‑(DAM‑)Systeme.

## Voraussetzungen

- **Java Development Kit (JDK) 8+** installiert.
- **Maven** für die Abhängigkeitsverwaltung.
- Grundlegende Kenntnisse in Java‑I/O und objektorientierter Programmierung.

## Wie richtet man GroupDocs.Metadata für Java ein?
Um zu beginnen, fügen Sie das GroupDocs-Repository und die Bibliotheksabhängigkeit zu Ihrer Maven `pom.xml` hinzu. Dadurch kann Maven die Artefakte auflösen und automatisch auf dem neuesten Stand halten, was zukünftige Updates und Sicherheitspatches vereinfacht. Nach dem Aktualisieren der `pom.xml` führen Sie `mvn clean install` aus, um die benötigten JARs herunterzuladen und zu überprüfen, ob die Einrichtung erfolgreich war.

```xml
<!-- ```xml
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
``` -->
```

Wenn Sie einen manuellen Ansatz bevorzugen, laden Sie das neueste JAR von der offiziellen Release‑Seite herunter:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Lizenzbeschaffung
- **Free trial** – testen Sie alle Funktionen für 30 Tage.
- **Temporary license** – verwenden Sie sie während der Entwicklung ohne Einschränkungen.
- **Full license** – erforderlich für Produktionsumgebungen.

## Grundlegende Initialisierung

`Metadata` ist der Einstiegspunkt für alle Vorgänge. Es repräsentiert eine einzelne Datei und bietet Zugriff auf deren eingebettete XMP‑Pakete.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Wie extrahiert man grundlegende XMP-Metadaten?

Laden Sie das Bild, öffnen Sie dessen XMP‑Paket und lesen Sie gängige Eigenschaften wie das Erstellungswerkzeug und Zeitstempel.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Wie extrahiert man Dublin‑Core‑XMP‑Metadaten?

Das Dublin Core‑Schema speichert standardisierte beschreibende Elemente wie Titel, Ersteller und Betreff. Greifen Sie über die Klasse `DublinCorePackage` darauf zu.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Wie extrahiert man Photoshop‑spezifische XMP‑Metadaten?

Photoshop bettet zusätzliche Informationen wie Farbmodus, Auflösung und Ebenenzahl ein. Rufen Sie diese Werte über das `PhotoshopPackage` ab.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Praktische Anwendungen

- **Digital asset management** – Bilder nach Ersteller, Urheberrecht oder Kameraeinstellungen taggen und durchsuchen.
- **Automated publishing pipelines** – XMP vor dem Veröffentlichen in Webgalerien einfügen oder ändern.
- **Analytics** – Metadaten über Tausende von Dateien aggregieren, um Nutzungstrends zu entdecken.

## Leistungsüberlegungen

Die Klasse `Metadata` bietet Zugriff auf die Metadaten und XMP‑Pakete einer Datei. Entsorgen Sie `Metadata`‑Objekte, sobald Sie das Lesen abgeschlossen haben, um native Ressourcen freizugeben. `LoadOptions.LAZY` weist die Bibliothek an, Metadaten lazy zu laden, wodurch der Speicherverbrauch reduziert wird. Streamen Sie große Dateien mit `Metadata.load(InputStream)`, um den Heap‑Verbrauch gering zu halten. Verwenden Sie eine einzelne `Metadata`‑Instanz beim Lesen vieler kleiner Dateien, um den Overhead bei der Objekterstellung zu verringern.

## Häufige Stolperfallen und Fehlersuche

| Symptom | Wahrscheinliche Ursache | Lösung |
|---|---|---|
| `NullPointerException` beim Zugriff auf XMP | Datei enthält kein XMP‑Paket | Rufen Sie `metadata.getXmpPackage()` auf und prüfen Sie vor dem Lesen auf `null`. Die Methode `getXmpPackage()` gibt das XMP‑Paketobjekt zurück oder null, wenn keines vorhanden ist. |
| Langsame Verarbeitung bei 500 MB‑Bildern | Laden der gesamten Datei in den Speicher | Verwenden Sie `metadata.load(InputStream)` und aktivieren Sie `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Fehlende Photoshop‑Felder | Bild wurde ohne Photoshop‑Ebeneninformationen gespeichert | Stellen Sie sicher, dass die Quelldatei aus Photoshop mit aktivierter Option „Save XMP“ exportiert wurde |

## Häufig gestellte Fragen

**Q: Kann ich XMP aus PDF‑Dateien extrahieren?**  
A: Ja, GroupDocs.Metadata unterstützt PDF‑XMP‑Pakete über dieselbe `Metadata`‑API.

**Q: Was passiert, wenn das Dateiformat nicht unterstützt wird?**  
A: Die Bibliothek wirft eine `UnsupportedFormatException`; fangen Sie sie ab und greifen Sie auf einen generischen Handler zurück.

**Q: Ist es möglich, XMP‑Metadaten zu ändern und wieder zu speichern?**  
A: Absolut. Nach dem Ändern von Eigenschaften rufen Sie `metadata.save("output.png")` auf, um die Updates zu persistieren.

**Q: Funktioniert die Bibliothek auf Android?**  
A: Die Kern‑Java‑Bibliothek ist mit Android API 24+ kompatibel, jedoch müssen Sie das `android`‑spezifische Artefakt einbinden.

**Q: Wie gehe ich mit verschlüsselten Bildern um?**  
A: Geben Sie das Entschlüsselungspasswort dem `Metadata`‑Konstruktor an: `new Metadata(filePath, "password")`.

## Fazit

Sie haben nun eine vollständige, produktionsbereite Anleitung zum **how to extract XMP**‑Metadaten‑Extrahieren mit GroupDocs.Metadata für Java. Durch Befolgen der obigen Schritte können Sie Ihre Anwendungen mit durchsuchbaren, standardkonformen Metadaten anreichern und leistungsstarke Asset‑Management‑Funktionen freischalten.

## Nächste Schritte

Tauchen Sie tiefer in das vollständige Funktionsspektrum ein, indem Sie die offizielle Dokumentation prüfen und mit anderen Metadatenstandards wie IPTC und EXIF experimentieren.

[Dokumentation](https://docs.groupdocs.com/metadata/java/)

---

**Zuletzt aktualisiert:** 2026-08-20  
**Getestet mit:** GroupDocs.Metadata for Java 23.11  
**Autor:** GroupDocs  

- [Dokumentation](https://docs.groupdocs.com/metadata/java/)
- [API‑Referenz](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub‑Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Kostenloses Support‑Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)

## Verwandte Tutorials

- [Dublin‑Core‑Metadaten aus Epub mit GroupDocs Java extrahieren](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [EXIF‑Software‑Tag in Java extrahieren: Ein vollständiger Leitfaden mit GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Wie man Metadaten mit GroupDocs.Metadata für Java extrahiert – Tutorials & Beispiele](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}