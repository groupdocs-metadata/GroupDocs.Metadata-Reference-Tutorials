---
title: Lesen Sie den Liedtext-Tag aus MP3-Dateien in .NET
linktitle: Lesen Sie den Liedtext-Tag aus MP3-Dateien in .NET
second_title: GroupDocs.Metadata .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Metadata für .NET Liedtext-Tags aus MP3-Dateien extrahieren. Folgen Sie unserem Schritt-für-Schritt-Tutorial.
weight: 13
url: /de/net/audio-metadata/read-lyrics-tag-mp3/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie Liedtext-Tags aus MP3-Dateien mithilfe der GroupDocs.Metadata-API in .NET extrahieren und lesen. GroupDocs.Metadata ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, mit Metadaten zu arbeiten, die mit verschiedenen Dateiformaten, einschließlich MP3-Dateien, verknüpft sind. Wenn Sie diese Schritte befolgen, können Sie in MP3-Dateien eingebettete textbezogene Informationen effizient abrufen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Visual Studio ist auf Ihrem Computer installiert.
- Grundkenntnisse der Programmiersprache C#.
-  GroupDocs.Metadata-Bibliothek für .NET. Sie können es herunterladen[Hier](https://releases.groupdocs.com/metadata/net/).
- Zugriff auf eine MP3-Datei mit Liedtext-Tags zum Testen.

## Namespaces importieren
Fügen Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt ein:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## Schritt 1: Laden Sie die MP3-Datei
 Beginnen Sie mit der Initialisierung von a`Metadata` Objekt mit dem Pfad Ihrer eingegebenen MP3-Datei:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // Rufen Sie das Root-Paket für das MP3-Format ab
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## Schritt 2: Greifen Sie auf Songtext-Tags zu
Überprüfen Sie, ob die MP3-Datei Lyrics3V2-Tags enthält und rufen Sie die zugehörigen Informationen ab:
```csharp
    if (root.Lyrics3V2 != null)
    {
        //Spezifische Tag-Felder ausgeben
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## Schritt 3: Durchlaufen Sie alle Tag-Felder
Alternativ können Sie alle verfügbaren Tag-Felder in Lyrics3V2 durchlaufen:
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## Abschluss
In diesem Tutorial haben wir untersucht, wie man mithilfe von GroupDocs.Metadata für .NET Liedtext-Tags aus MP3-Dateien extrahiert und liest. Wenn Sie diese Schritte befolgen, können Sie in Ihren MP3-Dateien eingebettete textbezogene Metadaten effektiv zur weiteren Verarbeitung oder Anzeige in Ihren Anwendungen abrufen.

## Häufig gestellte Fragen
### Kann ich die Songtext-Tags mithilfe von GroupDocs.Metadata ändern oder aktualisieren?
Ja, mit GroupDocs.Metadata können Sie Metadaten in MP3-Dateien aktualisieren und ändern, einschließlich Liedtext-Tags.
### Unterstützt GroupDocs.Metadata neben MP3 auch andere Audioformate?
Ja, GroupDocs.Metadata unterstützt eine Vielzahl von Audio- und Videoformaten für die Metadatenextraktion und -bearbeitung.
### Wo finde ich eine ausführlichere Dokumentation zu GroupDocs.Metadata?
 Sie können auf die vollständige Dokumentation zugreifen[Hier](https://tutorials.groupdocs.com/metadata/net/).
### Gibt es eine kostenlose Testversion für GroupDocs.Metadata?
 Ja, Sie können eine kostenlose Testversion erhalten[Hier](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Metadata?
 Für technische Unterstützung können Sie das GroupDocs.Metadata-Supportforum besuchen[Hier](https://forum.groupdocs.com/c/metadata/14).