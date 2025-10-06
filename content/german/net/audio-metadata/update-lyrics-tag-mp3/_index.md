---
title: Aktualisieren Sie den Lyrics-Tag in MP3-Dateien mit .NET
linktitle: Aktualisieren Sie den Lyrics-Tag in MP3-Dateien mit .NET
second_title: GroupDocs.Metadata .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Metadata für .NET Metadaten von MP3-Dateien, einschließlich Songtexten, Künstler- und Albumdetails programmgesteuert aktualisieren.
weight: 21
url: /de/net/audio-metadata/update-lyrics-tag-mp3/
type: docs
---
# Aktualisieren Sie den Lyrics-Tag in MP3-Dateien mit .NET

## Einführung
In diesem Tutorial zeigen wir, wie Sie die GroupDocs.Metadata for .NET-Bibliothek verwenden, um das Songtext-Tag in MP3-Dateien programmgesteuert zu aktualisieren. Dieser Prozess beinhaltet den Zugriff auf und die Änderung der Metadaten von MP3-Dateien, insbesondere auf die Liedtextinformationen.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Grundkenntnisse der C#-Programmierung.
- Visual Studio ist auf Ihrem Computer installiert.
-  GroupDocs.Metadata für .NET-Bibliothek installiert (siehe[Download-Link](https://releases.groupdocs.com/metadata/net/)).
- Eine MP3-Datei zu Testzwecken.

## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## Schritt 1: Laden Sie die MP3-Datei
 Laden Sie zunächst die MP3-Datei in ein`Metadata` Objekt mit GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Greifen Sie auf das Lyrics3V2-Tag zu
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## Schritt 2: Liedtextinformationen aktualisieren
Aktualisieren Sie als Nächstes die Liedtextinformationen zusammen mit anderen relevanten Details wie Interpret, Album und Titel:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## Schritt 3: Benutzerdefinierte Felder hinzufügen (optional)
Optional können Sie dem Tag benutzerdefinierte Felder hinzufügen:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## Schritt 4: Änderungen speichern
Speichern Sie abschließend die geänderten Metadaten wieder in der MP3-Datei:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## Abschluss
In diesem Tutorial haben wir untersucht, wie Sie das Liedtext-Tag in MP3-Dateien mithilfe von GroupDocs.Metadata für .NET aktualisieren. Wenn Sie die beschriebenen Schritte befolgen, können Sie Metadaten in MP3-Dateien effizient und programmgesteuert verwalten und ändern.

## Häufig gestellte Fragen
### Kann ich mit GroupDocs.Metadata für .NET neben Liedtexten auch andere Metadaten aktualisieren?
Ja, GroupDocs.Metadata für .NET ermöglicht Ihnen, mit verschiedenen Arten von Metadaten in unterschiedlichen Dateiformaten zu arbeiten.
### Ist GroupDocs.Metadata für .NET mit .NET Core kompatibel?
Ja, die Bibliothek unterstützt sowohl .NET Framework als auch .NET Core.
### Benötigt GroupDocs.Metadata für .NET eine Lizenz für die kommerzielle Nutzung?
 Ja, Sie können eine Lizenz erhalten bei[Gruppendokumente](https://purchase.groupdocs.com/buy) für den gewerblichen Gebrauch.
### Wie kann ich Support erhalten oder Fragen zu GroupDocs.Metadata für .NET stellen?
 Sie können die besuchen[GroupDocs.Metadata-Forum](https://forum.groupdocs.com/c/metadata/14) für Unterstützung und Diskussionen.
### Kann ich GroupDocs.Metadata für .NET kostenlos testen?
 Ja, Sie können eine[Kostenlose Testphase](https://releases.groupdocs.com/) um seine Funktionen zu erkunden.