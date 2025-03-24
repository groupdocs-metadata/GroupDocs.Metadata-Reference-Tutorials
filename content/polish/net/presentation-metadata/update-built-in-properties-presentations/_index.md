---
title: Zaktualizuj wbudowane właściwości w prezentacjach przy użyciu platformy .NET
linktitle: Zaktualizuj wbudowane właściwości w prezentacjach przy użyciu platformy .NET
second_title: GroupDocs.Metadata API .NET
description: Dowiedz się, jak aktualizować wbudowane właściwości w prezentacjach przy użyciu platformy .NET za pomocą GroupDocs.Metadata, wszechstronnej biblioteki do manipulacji metadanymi.
weight: 15
url: /pl/net/presentation-metadata/update-built-in-properties-presentations/
---
## Wstęp
tym samouczku zagłębimy się w potężne możliwości GroupDocs.Metadata dla .NET, kompleksowej biblioteki zaprojektowanej do manipulowania metadanymi w dokumentach przy użyciu platformy .NET. W szczególności skupimy się na programowej aktualizacji wbudowanych właściwości prezentacji (plików .PPT i .PPTX) przy użyciu języka C#.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
- Visual Studio: zainstalowany w twoim systemie.
-  GroupDocs.Metadata dla .NET: pobrano i zainstalowano z[Tutaj](https://releases.groupdocs.com/metadata/net/).
- Podstawowa znajomość języka C#: Znajomość języka programowania C#.

## Importuj przestrzenie nazw
Zacznij od zaimportowania niezbędnych przestrzeni nazw do projektu C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Krok 1: Załaduj plik prezentacji
 Najpierw utwórz nową instancję`Metadata` ładując plik prezentacji:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Krok 2: Zaktualizuj wbudowane właściwości
Teraz zaktualizuj żądane wbudowane właściwości prezentacji. Możesz na przykład zmodyfikować autora, datę utworzenia, firmę, kategorię, słowa kluczowe itp. Oto jak możesz to zrobić:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Krok 3: Zapisz zmiany
Po zaktualizowaniu właściwości zapisz zmiany z powrotem w pliku prezentacji:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Wniosek
tym samouczku omówiliśmy, jak używać GroupDocs.Metadata dla platformy .NET do programowego aktualizowania wbudowanych właściwości w plikach prezentacji. Wykonując poniższe kroki, możesz efektywnie zarządzać metadanymi i modyfikować je w aplikacjach .NET.

## Często zadawane pytania
### P: Co to jest GroupDocs.Metadata dla .NET?
O: GroupDocs.Metadata for .NET to potężna biblioteka do manipulacji metadanymi dla platformy .NET, umożliwiająca programistom odczytywanie, zapisywanie i edytowanie metadanych w różnych formatach dokumentów.
### P: Gdzie mogę znaleźć dokumentację GroupDocs.Metadata?
 Odp.: Możesz uzyskać dostęp do szczegółowej dokumentacji[Tutaj](https://tutorials.groupdocs.com/metadata/net/).
### P: Jak mogę uzyskać tymczasową licencję na GroupDocs.Metadata?
 Odpowiedź: Możesz nabyć licencję tymczasową[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### P: Czy GroupDocs.Metadata obsługuje inne formaty plików oprócz prezentacji?
O: Tak, GroupDocs.Metadata obsługuje szeroką gamę formatów, w tym dokumenty, arkusze kalkulacyjne, obrazy, filmy i inne.
### P: Gdzie mogę uzyskać pomoc lub zadać pytania dotyczące GroupDocs.Metadata?
 O: Aby uzyskać wsparcie i dyskusje, odwiedź stronę[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).