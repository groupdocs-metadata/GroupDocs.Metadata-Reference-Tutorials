---
title: Update de songteksttag in MP3-bestanden met .NET
linktitle: Update de songteksttag in MP3-bestanden met .NET
second_title: GroupDocs.Metadata .NET API
description: Leer hoe u metagegevens van MP3-bestanden, inclusief songteksten, artiest- en albumgegevens, programmatisch kunt bijwerken met GroupDocs.Metadata voor .NET.
type: docs
weight: 21
url: /nl/net/audio-metadata/update-lyrics-tag-mp3/
---
## Invoering
In deze zelfstudie laten we zien hoe u de GroupDocs.Metadata voor .NET-bibliotheek kunt gebruiken om de songteksttag in MP3-bestanden programmatisch bij te werken. Dit proces omvat het openen en wijzigen van de metagegevens van MP3-bestanden, met name gericht op de songtekstinformatie.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u begint:
- Basiskennis van programmeren in C#.
- Visual Studio is op uw computer geïnstalleerd.
-  GroupDocs.Metadata voor .NET-bibliotheek geïnstalleerd (zie[download link](https://releases.groupdocs.com/metadata/net/)).
- Een MP3-bestand voor testdoeleinden.

## Naamruimten importeren
Begin met het importeren van de benodigde naamruimten in uw C#-project:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## Stap 1: Laad het MP3-bestand
 Laad eerst het MP3-bestand in een`Metadata` object met GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Toegang tot de Lyrics3V2-tag
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## Stap 2: Update songtekstinformatie
Werk vervolgens de songtekstinformatie bij, samen met andere relevante details, zoals artiest, album en track:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## Stap 3: Aangepaste velden toevoegen (optioneel)
Optioneel kunt u aangepaste velden aan de tag toevoegen:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## Stap 4: Sla de wijzigingen op
Sla ten slotte de gewijzigde metadata terug naar het MP3-bestand:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## Conclusie
In deze zelfstudie hebben we onderzocht hoe u de songteksttag in MP3-bestanden kunt bijwerken met behulp van GroupDocs.Metadata voor .NET. Door de beschreven stappen te volgen, kunt u metagegevens binnen MP3-bestanden efficiënt programmatisch beheren en wijzigen.

## Veelgestelde vragen
### Kan ik naast songteksten ook andere metagegevens bijwerken met GroupDocs.Metadata voor .NET?
Ja, met GroupDocs.Metadata voor .NET kunt u met verschillende soorten metadata in verschillende bestandsformaten werken.
### Is GroupDocs.Metadata voor .NET compatibel met .NET Core?
Ja, de bibliotheek ondersteunt zowel .NET Framework als .NET Core.
### Is voor GroupDocs.Metadata voor .NET een licentie vereist voor commercieel gebruik?
 Ja, u kunt een licentie verkrijgen bij[Groepsdocumenten](https://purchase.groupdocs.com/buy) voor commercieel gebruik.
### Hoe kan ik ondersteuning krijgen of vragen stellen met betrekking tot GroupDocs.Metadata voor .NET?
 U kunt een bezoek brengen aan de[GroupDocs.Metadata-forum](https://forum.groupdocs.com/c/metadata/14) voor ondersteuning en discussies.
### Kan ik GroupDocs.Metadata voor .NET gratis uitproberen?
 Ja, je kunt een[gratis proefperiode](https://releases.groupdocs.com/) om de kenmerken ervan te verkennen.