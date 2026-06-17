---
date: '2026-03-22'
description: Dowiedz się, jak zmienić datę utworzenia pliku Excel i zaktualizować
  metadane Excela przy użyciu GroupDocs.Metadata dla Javy. Postępuj zgodnie z tym
  przewodnikiem krok po kroku, aby dodać słowa kluczowe do Excela i zmodyfikować właściwości
  dokumentu.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Zmień datę utworzenia pliku Excel przy użyciu GroupDocs.Metadata w Javie
type: docs
url: /pl/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Zmiana daty utworzenia pliku Excel przy użyciu GroupDocs.Metadata w Javie

W nowoczesnych środowiskach opartych na danych, **zmiana daty utworzenia pliku Excel** i utrzymywanie innych metadanych w aktualności może znacząco poprawić organizację dokumentów, ich wyszukiwalność i zgodność. Niezależnie od tego, czy obsługujesz raporty finansowe, śledzenie projektów czy dane archiwalne, dokładne metadane zapewniają, że odpowiednie osoby znajdą właściwe pliki w odpowiednim czasie. Ten samouczek przeprowadzi Cię przez użycie biblioteki GroupDocs.Metadata do **zmiany daty utworzenia pliku Excel**, **dodawania słów kluczowych do Excela** oraz **modyfikacji właściwości dokumentu Excel** w aplikacji Java.

## Szybkie odpowiedzi
- **Czy mogę zmienić datę utworzenia pliku Excel?** Tak, używając `setCreatedTime` z GroupDocs.Metadata.  
- **Która biblioteka obsługuje aktualizację metadanych Excel w Javie?** GroupDocs.Metadata for Java.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa w celach oceny; stała licencja jest wymagana w produkcji.  
- **Jaka wersja Javy jest wymagana?** JDK 8 lub wyższa.  
- **Czy mogę dodać własne słowa kluczowe do skoroszytu Excel?** Oczywiście — użyj `setKeywords` na właściwościach dokumentu.

## Co oznacza „zmiana daty utworzenia pliku Excel”?
Zmiana daty utworzenia pliku Excel oznacza aktualizację wbudowanej właściwości *Created* przechowywanej wewnątrz pliku skoroszytu. Właściwość ta jest częścią standardowych metadanych Office Open XML i może być edytowana programowo bez zmiany rzeczywistej zawartości arkusza.

## Dlaczego warto używać GroupDocs.Metadata do metadanych Excel?
GroupDocs.Metadata oferuje wysokopoziomowe, typowo‑bezpieczne API, które abstrahuje niskopoziomową obsługę XML wymaganą przez format Office Open XML. Umożliwia ono:
- **Aktualizację podstawowych właściwości** takich jak autor, firma i data utworzenia w jednym wywołaniu.  
- **Dodawanie słów kluczowych do Excela**, aby poprawić wyniki wyszukiwania w SharePoint, OneDrive lub lokalnych systemach plików.  
- **Modyfikację właściwości dokumentu Excel** bez otwierania skoroszytu w Excelu, co oszczędza czas i zasoby.  

## Prerequisites
- Java Development Kit (JDK) 8 lub nowszy.  
- IDE, takie jak IntelliJ IDEA lub Eclipse.  
- Podstawowa znajomość operacji I/O w Javie.  

## Konfiguracja GroupDocs.Metadata dla Javy

### Installation

Dodaj repozytorium Maven GroupDocs.Metadata oraz zależność do swojego `pom.xml`:

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

Alternatywnie możesz [pobrać najnowszą wersję bezpośrednio](https://releases.groupdocs.com/metadata/java/), jeśli wolisz ręczną konfigurację.

### License Acquisition

GroupDocs oferuje darmową wersję próbną do oceny. Do użytku produkcyjnego uzyskaj tymczasową lub stałą licencję od dostawcy. Odwiedź [stronę zakupu GroupDocs](https://purchase.groupdocs.com/temporary-license/), aby uzyskać szczegóły.

#### Basic Initialization

Zaimportuj niezbędne klasy w swoim pliku źródłowym Java:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implementacja krok po kroku

### Krok 1: Otwórz skoroszyt Excel

Podaj ścieżkę do źródłowego skoroszytu i utwórz instancję `Metadata`. Blok `try‑with‑resources` zapewnia automatyczne zamknięcie uchwytu pliku.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Krok 2: Aktualizacja wbudowanych właściwości metadanych

Teraz możesz **zmienić datę utworzenia pliku Excel**, ustawić autora, firmę, kategorię oraz **dodać słowa kluczowe do Excela**. Wywołanie `new Date()` pobiera bieżący znacznik czasu, ale możesz podać dowolny `java.util.Date`, którego potrzebujesz.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Porada:** Używaj spójnej konwencji nazewnictwa dla słów kluczowych (np. `project:Q2, finance, confidential`), aby przyszłe wyszukiwania były bardziej efektywne.

### Krok 3: Zapisz zaktualizowany skoroszyt

Określ ścieżkę wyjściową i zachowaj zmiany. Oryginalny plik pozostaje niezmieniony, co jest przydatne w ścieżkach audytu.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Częste problemy i rozwiązania

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| **Błędy ścieżki pliku** | Nieprawidłowe ścieżki względne/absolutne | Sprawdź ponownie `inputFilePath` i `outputFilePath`. Użyj `Paths.get(...)` dla ścieżek niezależnych od platformy. |
| **Niekompatybilna wersja biblioteki** | Używanie starszej wersji GroupDocs.Metadata, która nie obsługuje metody `setCreatedTime` | Uaktualnij do najnowszej wersji (jak pokazano w fragmencie Maven). |
| **Brak licencji** | Okres próbny wygasł | Zastosuj tymczasową licencję lub zakup pełną licencję poprzez stronę zakupu. |
| **Wysokie zużycie pamięci przy dużym skoroszycie** | Ładowanie ogromnych plików Excel zużywa pamięć sterty | Przetwarzaj pliki w partiach i zwiększ pamięć sterty JVM (`-Xmx`) w razie potrzeby. |

## Najczęściej zadawane pytania

**P: Jakie wersje Javy są obsługiwane przez GroupDocs.Metadata?**  
O: Java 8 i nowsze są w pełni obsługiwane.

**P: Jak powinienem obsługiwać wyjątki przy aktualizacji metadanych?**  
O: Owiń kod w blok `try‑catch` i loguj `MetadataException`, aby przechwycić wszelkie błędy I/O lub formatowania.

**P: Czy mogę zaktualizować wiele plików Excel w jednym uruchomieniu?**  
O: Tak, iteruj po kolekcji ścieżek plików, ale monitoruj zużycie pamięci przy dużych partiach.

**P: Czy można przywrócić zmiany wprowadzone w metadanych?**  
O: Zachowaj kopię zapasową oryginalnego skoroszytu przed zastosowaniem aktualizacji, a następnie przywróć ją w razie potrzeby.

**P: Gdzie mogę znaleźć bardziej szczegółową dokumentację?**  
O: Zobacz oficjalny przewodnik pod adresem [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Praktyczne zastosowania

1. **Audyt finansowy** – Rejestruj, kto i kiedy zmodyfikował skoroszyt, zapewniając ścieżkę audytu.  
2. **Zarządzanie projektami** – Oznacz arkusze słowami kluczowymi specyficznymi dla projektu, aby szybko je odnaleźć.  
3. **Archiwizacja danych** – Zachowaj oryginalne daty utworzenia i informacje o firmie w celu zapewnienia zgodności.  

## Wskazówki dotyczące wydajności

- Ogranicz operacje na metadanych w jednym uruchomieniu, aby uniknąć nadmiernego zużycia pamięci.  
- Zamykaj obiekt `Metadata` niezwłocznie (wzorzec `try‑with‑resources` robi to automatycznie).  
- W przypadku bardzo dużych skoroszytów rozważ przetwarzanie ich w wątku tła, aby interfejs użytkownika pozostał responsywny.

## Podsumowanie

Teraz wiesz, jak **zmienić datę utworzenia pliku Excel**, **dodać słowa kluczowe do Excela** oraz **modyfikować właściwości dokumentu Excel** przy użyciu GroupDocs.Metadata w Javie. Ta możliwość pozwala utrzymać Twoje arkusze kalkulacyjne dobrze zorganizowane, łatwe do wyszukania i zgodne z wewnętrznymi politykami zarządzania. Następnym krokiem jest eksploracja innych funkcji metadanych, takich jak własne właściwości czy przetwarzanie wsadowe, aby jeszcze bardziej usprawnić przepływ pracy zarządzania dokumentami.

---

**Ostatnia aktualizacja:** 2026-03-22  
**Testowano z:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs  

**Zasoby**
- [Dokumentacja](https://docs.groupdocs.com/metadata/java/)
- [Referencja API](https://reference.groupdocs.com/metadata/java/)
- [Pobierz GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [Repozytorium GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Darmowe forum wsparcia](https://forum.groupdocs.com/c/metadata/)
- [Licencja tymczasowa](https://purchase.groupdocs.com/temporary-license/)