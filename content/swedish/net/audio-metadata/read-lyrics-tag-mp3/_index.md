---
title: Läs Lyrics Tag från MP3-filer i .NET
linktitle: Läs Lyrics Tag från MP3-filer i .NET
second_title: GroupDocs.Metadata .NET API
description: Lär dig hur du extraherar texttaggar från MP3-filer med GroupDocs.Metadata for .NET. Följ vår steg-för-steg handledning.
weight: 13
url: /sv/net/audio-metadata/read-lyrics-tag-mp3/
type: docs
---
# Läs Lyrics Tag från MP3-filer i .NET

## Introduktion
den här handledningen kommer vi att lära oss hur man extraherar och läser texttaggar från MP3-filer med hjälp av GroupDocs.Metadata API i .NET. GroupDocs.Metadata är ett kraftfullt bibliotek som låter utvecklare arbeta med metadata som är associerade med olika filformat, inklusive MP3-filer. Genom att följa dessa steg kommer du att effektivt kunna hämta textrelaterad information inbäddad i MP3-filer.
## Förutsättningar
Innan vi börjar, se till att du har ställt in följande förutsättningar:
- Visual Studio installerat på din dator.
- Grundläggande kunskaper i programmeringsspråket C#.
-  GroupDocs.Metadata-bibliotek för .NET. Du kan ladda ner den[här](https://releases.groupdocs.com/metadata/net/).
- Tillgång till en MP3-fil som innehåller texttaggar för testning.

## Importera namnområden
Inkludera först de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## Steg 1: Ladda MP3-filen
 Börja med att initiera a`Metadata` objekt med din indata MP3-filsökväg:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // Hämta rotpaketet för MP3-format
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## Steg 2: Få åtkomst till textetiketter
Kontrollera om MP3-filen innehåller Lyrics3V2-taggar och hämta tillhörande information:
```csharp
    if (root.Lyrics3V2 != null)
    {
        //Skriv ut specifika taggfält
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## Steg 3: Gå igenom alla taggfält
Alternativt kan du gå igenom alla tillgängliga taggfält inom Lyrics3V2:
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## Slutsats
I den här handledningen undersökte vi hur man extraherar och läser Lyrics-taggar från MP3-filer med GroupDocs.Metadata for .NET. Genom att följa dessa steg kan du effektivt hämta textrelaterad metadata inbäddad i dina MP3-filer för vidare bearbetning eller visning i dina applikationer.

## FAQ's
### Kan jag ändra eller uppdatera sångtexttaggarna med GroupDocs.Metadata?
Ja, GroupDocs.Metadata låter dig uppdatera och modifiera metadata i MP3-filer, inklusive sångtexttaggar.
### Stöder GroupDocs.Metadata andra ljudformat än MP3?
Ja, GroupDocs.Metadata stöder ett brett utbud av ljud- och videoformat för extrahering och manipulering av metadata.
### Var kan jag hitta mer detaljerad dokumentation för GroupDocs.Metadata?
 Du kan få tillgång till hela dokumentationen[här](https://tutorials.groupdocs.com/metadata/net/).
### Finns det en gratis testversion tillgänglig för GroupDocs.Metadata?
 Ja, du kan få en gratis testversion[här](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för GroupDocs.Metadata?
 För teknisk hjälp kan du besöka GroupDocs.Metadatas supportforum[här](https://forum.groupdocs.com/c/metadata/14).