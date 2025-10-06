---
title: Aktualizujte vestavěné vlastnosti v souborech PDF pomocí .NET
linktitle: Aktualizujte vestavěné vlastnosti v souborech PDF pomocí .NET
second_title: GroupDocs.Metadata .NET API
description: Přečtěte si, jak aktualizovat vlastnosti dokumentu PDF pomocí C# a GroupDocs.Metadata pro .NET. Programově upravujte autora, název, klíčová slova a další.
weight: 15
url: /cs/net/pdf-metadata/update-built-in-properties-pdfs/
type: docs
---
# Aktualizujte vestavěné vlastnosti v souborech PDF pomocí .NET

## Úvod
V tomto tutoriálu se naučíme, jak používat GroupDocs.Metadata pro .NET k aktualizaci vestavěných vlastností dokumentů PDF. Tato knihovna poskytuje výkonnou sadu nástrojů pro manipulaci s metadaty v rámci různých formátů dokumentů. Projdeme si nezbytné kroky k úpravě vlastností, jako je autor, název, datum vytvoření, klíčová slova, tvůrce a producent v souboru PDF pomocí C#.
## Předpoklady
Než začneme, ujistěte se, že máte na svém místě následující:
-  GroupDocs.Metadata for .NET Library: Stáhněte si knihovnu z[tady](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Nainstalujte Visual Studio, abyste mohli psát a spouštět kód C#.
- Základní znalost C#: Doporučuje se znalost programovacího jazyka C#.

## Import jmenných prostorů
Začněte tím, že do svého projektu C# zahrnete potřebné jmenné prostory:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Krok 1: Inicializujte objekt metadat
 Začněte inicializací a`Metadata`objekt s cestou k vašemu souboru PDF:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Váš kód půjde sem
}
```
## Krok 2: Přístup ke kořenovému balíčku PDF
 Dále načtěte kořenový balíček speciálně pro použití PDF`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Krok 3: Aktualizujte vlastnosti dokumentu
 Nyní aktualizujte požadované vlastnosti dokumentu PDF v rámci`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Krok 4: Uložte změny
Po úpravě vlastností uložte změny zpět do souboru PDF:
```csharp
metadata.Save("Your Output File Path");
```
## Krok 5: Načtení aktualizovaných vlastností
Chcete-li ověřit změny, znovu načtěte metadata a načtěte aktualizované vlastnosti:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Závěr
V tomto tutoriálu jsme prozkoumali, jak využít GroupDocs.Metadata pro .NET k programové aktualizaci vestavěných vlastností dokumentů PDF. Podle nastíněných kroků můžete efektivně spravovat a upravovat metadata v souborech PDF pomocí C#. Neváhejte a prozkoumejte další funkce a možnosti, které nabízí GroupDocs.Metadata pro komplexní manipulaci s metadaty.

## FAQ
### Otázka: Co je GroupDocs.Metadata pro .NET?
Odpověď: GroupDocs.Metadata for .NET je knihovna, která umožňuje vývojářům programově číst, upravovat, odstraňovat a manipulovat s metadaty v různých formátech dokumentů.
### Otázka: Kde najdu dokumentaci k GroupDocs.Metadata pro .NET?
 Odpověď: Máte přístup k dokumentaci[tady](https://tutorials.groupdocs.com/metadata/net/).
### Otázka: Jak si mohu stáhnout GroupDocs.Metadata pro .NET?
 Odpověď: GroupDocs.Metadata pro .NET si můžete stáhnout z[tento odkaz](https://releases.groupdocs.com/metadata/net/).
### Otázka: Je k dispozici bezplatná zkušební verze?
 Odpověď: Ano, můžete získat bezplatnou zkušební verzi[tady](https://releases.groupdocs.com/).
### Otázka: Kde mohu získat podporu pro GroupDocs.Metadata pro .NET?
 Odpověď: Podporu získáte na fóru GroupDocs.Metadata[tady](https://forum.groupdocs.com/c/metadata/14).