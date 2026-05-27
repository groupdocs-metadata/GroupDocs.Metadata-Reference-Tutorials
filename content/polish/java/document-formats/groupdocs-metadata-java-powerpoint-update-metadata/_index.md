---
date: '2026-05-27'
description: Dowiedz się, jak ustawić CreatedTime pliku pptx w Javie przy użyciu zależności
  GroupDocs Maven, aby zaktualizować metadane PowerPoint, w tym jak zmienić datę utworzenia
  pliku PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Ustaw CreatedTime pliku PPTX w Javie przy użyciu zależności GroupDocs Maven
type: docs
url: /pl/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Ustaw CreatedTime PPTX w Javie z GroupDocs.Metadata

Dokładne metadane są niezbędne dla zgodności i wykrywalności w nowoczesnych przepływach dokumentów. Dzięki **GroupDocs.Metadata** możesz programowo **ustawić CreatedTime PPTX w Javie**, co pozwala **zmienić datę utworzenia PPTX** wraz z innymi wbudowanymi właściwościami, takimi jak autor lub firma. Ten samouczek przeprowadzi Cię przez konfigurację Maven, inicjalizację API, aktualizację metadanych oraz zapis zmodyfikowanej prezentacji — wszystko przy użyciu przejrzystego, gotowego do produkcji kodu.

## Szybkie odpowiedzi
- **Która biblioteka aktualizuje metadane PowerPoint w Javie?** GroupDocs.Metadata poprzez zależność Maven GroupDocs.  
- **Czy mogę ustawić właściwość CreatedTime PPTX?** Tak — użyj `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Czy licencja jest wymagana w produkcji?** Wersja próbna działa w ocenie; licencja komercyjna jest obowiązkowa przy wdrożeniach produkcyjnych.  
- **Jakie narzędzie budowania używa przykład?** Maven (można także pobrać plik JAR ręcznie).  
- **Czy API obsługuje Javę 8 i nowsze?** Zdecydowanie — GroupDocs.Metadata jest przeznaczony dla Javy 8+.

## Czym jest zależność Maven GroupDocs?
**GroupDocs Maven dependency** to wpis w repozytorium kompatybilny z Maven, który pobiera najnowszą bibliotekę GroupDocs.Metadata do Twojego projektu Java. Uproszcza zarządzanie zależnościami poprzez automatyczne rozwiązywanie zależności tranzytywnych, zapewnia, że zawsze używasz najnowszej i najbezpieczniejszej wersji, oraz eliminuje potrzebę ręcznego pobierania plików JAR lub śledzenia wersji.

## Dlaczego używać GroupDocs.Metadata do zmiany daty utworzenia PPTX?
GroupDocs.Metadata umożliwia automatyczne, gotowe do przetwarzania wsadowego aktualizacje znaczników czasu utworzenia PPTX, zapewniając, że każda prezentacja spełnia polityki korporacyjne lub wymogi prawne. Programowo ustawiając właściwość CreatedTime, unikasz ręcznej edycji, zmniejszasz ryzyko błędów ludzkich i możesz zintegrować tę zmianę z pipeline'ami CI/CD lub skryptami migracyjnymi, co zapewnia płynne zarządzanie dokumentami.

## Wymagania wstępne
- Zainstalowana Java 8 lub nowsza.  
- IDE, takie jak IntelliJ IDEA lub Eclipse.  
- Maven do obsługi zależności.  
- Dostęp do wersji próbnej GroupDocs lub zakupionej licencji.

## Jak ustawić CreatedTime PPTX w Javie?

Klasa `Metadata` reprezentuje dokument i zapewnia dostęp do jego właściwości metadanych.

Załaduj plik PowerPoint przy użyciu `new Metadata("presentation.pptx")`, pobierz pakiet główny, wywołaj `setCreatedTime` z żądaną `java.util.Date`, a na końcu wywołaj `save`, aby zapisać zmiany. Ten kompletny przepływ modyfikuje datę utworzenia, zachowując całą zawartość slajdów i inne właściwości.

### Konfiguracja Maven
Dodaj repozytorium GroupDocs oraz zależność metadata do swojego `pom.xml`:

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

> **Wskazówka:** Utrzymywanie numeru wersji aktualnym zapewnia korzyści z najnowszych poprawek błędów i ulepszeń wydajności.

### Bezpośrednie pobranie (jeśli nie chcesz używać Maven)
Alternatywnie, pobierz najnowszy plik JAR z [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Uzyskanie licencji
Rozpocznij od darmowej wersji próbnej lub poproś o tymczasową licencję, aby ocenić GroupDocs.Metadata. Do użytku produkcyjnego zakup licencję poprzez [oficjalną stronę GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Podstawowa inicjalizacja i konfiguracja

Gdy biblioteka znajduje się na classpath, możesz utworzyć instancję `Metadata`, która wskazuje na Twój plik PowerPoint:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Ten kod otwiera prezentację w bloku try‑with‑resources, zapewniając automatyczne zwolnienie uchwytu pliku.

## Przewodnik krok po kroku po aktualizacji wbudowanych metadanych

### Krok 1: Załaduj dokument prezentacji

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Załadowanie pliku ustanawia połączenie, które umożliwia odczyt lub zapis metadanych.

### Krok 2: Uzyskaj dostęp do pakietu głównego prezentacji

Obiekt `root` zapewnia dostęp do podstawowego pakietu prezentacji oraz jej wbudowanych właściwości.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Obiekt `root` udostępnia wszystkie wbudowane właściwości dokumentu.

### Krok 3: Zaktualizuj wbudowane właściwości dokumentu (w tym datę utworzenia)

`setCreatedTime` przypisuje nowy znacznik czasu utworzenia do dokumentu.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Tutaj pokazujemy, jak **ustawić CreatedTime PPTX** przypisując nowy obiekt `Date` do `CreatedTime`. Zastąp `new Date()` dowolnym konkretnym znacznikiem czasu, którego potrzebujesz.

### Krok 4: Zapisz zaktualizowaną prezentację

`save` zapisuje zmodyfikowane metadane z powrotem do pliku.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Wywołanie `save` zapisuje zmodyfikowane metadane do nowego pliku PowerPoint, pozostawiając oryginał nietknięty.

## Wskazówki rozwiązywania problemów
- **Plik nie znaleziony:** Sprawdź dokładnie ścieżkę wejściową i uprawnienia do pliku.  
- **Niezgodność wersji:** Upewnij się, że wersja `groupdocs-metadata` odpowiada Twojemu środowisku Java.  
- **Właściwość nie jest aktualizowana:** Zweryfikuj, że wywołujesz `setCreatedTime` (lub odpowiedni setter) przed wywołaniem `save`.

## Praktyczne zastosowania
1. **Branding korporacyjny:** Automatycznie wstaw prawidłową nazwę firmy i kategorię do wszystkich zestawów slajdów przed dystrybucją.  
2. **Systemy zarządzania dokumentami:** Wzbogacaj pliki PPTX o przeszukiwalne metadane, aby przyspieszyć ich odnajdywanie.  
3. **Zasoby edukacyjne:** Utrzymuj aktualne informacje o autorze i programie nauczania we wszystkich slajdach wykładów.  
4. **Śledzenie współpracy:** Rejestruj nazwiska współtwórców, aby zapewnić odpowiedzialność.  
5. **Integracja z CMS:** Synchronizuj zmiany metadanych z platformą zarządzania treścią w czasie rzeczywistym.

## Rozważania dotyczące wydajności
- **Przetwarzanie wsadowe:** Iteruj po liście plików i w miarę możliwości ponownie używaj jednej instancji `Metadata`.  
- **Zarządzanie pamięcią:** Zawsze używaj try‑with‑resources (jak pokazano), aby szybko zwalniać zasoby natywne.  
- **Efektywne struktury danych:** Przechowuj aktualizacje metadanych w mapie przed ich zastosowaniem, aby zredukować powtarzalne wywołania.

## Najczęściej zadawane pytania

**Q:** Jaki jest główny cel zależności Maven GroupDocs?  
**A:** Zapewnia wygodny sposób włączenia najnowszej biblioteki GroupDocs.Metadata w projektach Java opartych na Maven.

**Q:** Jak mogę ustawić datę utworzenia PPTX bez wpływu na inne właściwości?  
**A:** Użyj `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` przed wywołaniem `metadata.save()`.

**Q:** Czy potrzebuję licencji, aby uruchomić ten kod w środowisku deweloperskim?  
**A:** Tymczasowa licencja próbna wystarczy do rozwoju i testów; pełna licencja jest wymagana w produkcji.

**Q:** Czy mogę również aktualizować niestandardowe pola metadanych?  
**A:** Tak — GroupDocs.Metadata obsługuje zarówno wbudowane, jak i niestandardowe właściwości za pośrednictwem swojego API.

**Q:** Czy istnieje sposób na cofnięcie zmian, jeśli popełnię błąd?  
**A:** Zachowaj kopię oryginalnego pliku lub odczytaj istniejące wartości właściwości przed ich nadpisaniem, a następnie przywróć je w razie potrzeby.

## Zasoby

- [Dokumentacja](https://docs.groupdocs.com/metadata/java/)
- [Referencja API](https://apireference.groupdocs.com/metadata/java/)

---

**Ostatnia aktualizacja:** 2026-05-27  
**Testowano z:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs  

## Powiązane samouczki

- [Aktualizuj niestandardowe metadane w PowerPoint przy użyciu GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Jak zaktualizować metadane dokumentu Word przy użyciu GroupDocs.Metadata Java: Kompletny przewodnik](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Efektywna aktualizacja metadanych PDF przy użyciu GroupDocs.Metadata w Javie dla zarządzania dokumentami](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)