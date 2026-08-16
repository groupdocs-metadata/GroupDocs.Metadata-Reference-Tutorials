---
date: '2026-08-10'
description: Dowiedz się, jak wyodrębnić EXIF metadata z plików PSD przy użyciu GroupDocs.Metadata
  dla Java. Ten przewodnik obejmuje podstawowe wyodrębnianie, pakiety IFD, dane GPS
  oraz praktyczne przykłady zastosowań.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Dowiedz się, jak wyodrębnić EXIF metadata z plików PSD przy użyciu
  GroupDocs.Metadata dla Java. Przewodnik krok po kroku, fragmenty kodu oraz wskazówki
  rozwiązywania problemów dla programistów.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Jak wyodrębnić EXIF metadata z plików PSD za pomocą GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: Jak wyodrębnić EXIF metadata z plików PSD za pomocą GroupDocs.Metadata
type: docs
url: /pl/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Jak wyodrębnić metadane EXIF z plików PSD przy użyciu GroupDocs.Metadata

Wyodrębnianie **metadanych EXIF** z plików PSD jest rutynowym, ale potężnym krokiem, gdy musisz audytować pochodzenie obrazów, automatyzować tagowanie zasobów lub budować przeszukiwalne biblioteki mediów. W tym samouczku odkryjesz **jak wyodrębnić EXIF** szybko przy użyciu GroupDocs.Metadata dla Javy, zobaczysz dokładne wywołania API i nauczysz się obsługiwać zaawansowane pakiety IFD oraz współrzędne GPS. Po zakończeniu będziesz gotowy zintegrować wyodrębnianie metadanych z dowolnym przepływem pracy opartym na Javie.

## Szybkie odpowiedzi

Klasa `Metadata` reprezentuje plik i zapewnia dostęp do jego metadanych.

- **Jaka jest pierwsza linia kodu?** `Metadata metadata = new Metadata("sample.psd");`
- **Która metoda zwraca nazwę artysty?** `metadata.getExif().getArtist();`
- **Czy mogę odczytać dane GPS?** Tak – użyj `metadata.getExif().getGpsInfo();`
- **Czy potrzebna jest licencja do produkcji?** Wymagana jest ważna licencja GroupDocs.Metadata po okresie próbnym.
- **Obsługiwana wersja Javy?** Java 8 lub nowsza (do Java 21).

## Czym są metadane EXIF?

Metadane EXIF (Exchangeable Image File Format) przechowują ustawienia aparatu, znaczniki czasu utworzenia oraz dane lokalizacyjne wewnątrz plików obrazów. GroupDocs.Metadata odczytuje te informacje bezpośrednio ze struktury binarnej plików PSD, udostępniając je poprzez przejrzyste API w Javie. Umożliwia programistom programowe pobieranie szczegółów, takich jak model aparatu, czas naświetlania i współrzędne GPS, bez ręcznej inspekcji.

## Dlaczego warto używać GroupDocs.Metadata dla Javy?

GroupDocs.Metadata obsługuje **ponad 30 formatów plików** (w tym PSD, JPEG, PNG, TIFF) i może przetwarzać pliki do **2 GB** bez ładowania całego dokumentu do pamięci. Biblioteka wyodrębnia **ponad 150 różnych tagów EXIF**, zapewniając pełny zestaw atrybutów aparatu i GPS potrzebnych do analiz lub zgodności.

## Wymagania wstępne

- **Java Development Kit (JDK) 8** lub nowszy zainstalowany na twoim komputerze.  
- **Maven** do zarządzania zależnościami.  
- **GroupDocs.Metadata for Java w wersji 24.12** (lub nowszej).  
- Podstawowa znajomość klas Javy, obiektów i obsługi wyjątków.

### Wymagane biblioteki i zależności

| Zależność | Współrzędne Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Konfiguracja środowiska

Powinieneś mieć IDE kompatybilne z Maven, takie jak IntelliJ IDEA lub Eclipse. Utwórz nowy projekt Maven lub dodaj zależność do istniejącego.

## Jak skonfigurować GroupDocs.Metadata dla Javy

GroupDocs.Metadata można dodać do projektu Maven za pomocą kilku linii konfiguracji. Poniższe kroki pokazują, jak dodać repozytorium i zależność, aby biblioteka była dostępna w classpath.

### Konfiguracja Maven

Dodaj poniższy fragment do swojego `pom.xml` wewnątrz sekcji `<dependencies>`:

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

### Bezpośrednie pobranie

Alternatywnie, pobierz najnowszy plik JAR ze strony oficjalnych wydań: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Uzyskanie licencji

Aby uruchomić bibliotekę po okresie próbnym 30 dni, uzyskaj tymczasową lub pełną licencję:

1. Odwiedź [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Wybierz **temporary** do testów lub **full** do produkcji.  
3. Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby osadzić plik licencji (`metadata.lic`) w classpath Javy.

### Podstawowa inicjalizacja i konfiguracja

Po dodaniu biblioteki do classpath, zainicjalizuj ją jak pokazano poniżej:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Jak wyodrębnić podstawowe właściwości metadanych EXIF z obrazu PSD

Ta sekcja wyjaśnia, jak załadować plik PSD, uzyskać dostęp do kontenera EXIF i odczytać najczęstsze tagi, takie jak **artist**, **copyright** i **software**. Proces polega na utworzeniu instancji `Metadata`, wywołaniu `getExif()`, a następnie pobraniu poszczególnych właściwości przy użyciu prostych metod getter.

### Implementacja krok po kroku

1. **Utwórz instancję `Metadata`** wskazującą na twój plik PSD.  
2. **Wywołaj `getExif()`** aby uzyskać kontener EXIF.  
3. **Odczytaj poszczególne właściwości** takie jak `getArtist()`, `getCopyright()` i `getSoftware()`.  
4. **Wydrukuj lub zapisz** wartości zgodnie z logiką aplikacji.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Wskazówka:** Obiekt `Metadata` automatycznie wykrywa format pliku, więc możesz ponownie używać tego samego kodu dla plików JPEG lub TIFF bez modyfikacji.

## Jak wyodrębnić właściwości pakietu EXIF IFD z obrazu PSD

Sekcja IFD (Image File Directory) zawiera bardziej szczegółowe informacje techniczne, takie jak **camera serial number**, **lens model** i **user comments**. `Ifd0` reprezentuje główny katalog plików obrazu zawierający podstawowe informacje o aparacie. Wyodrębnianie tych pól jest przydatne do analizy kryminalistycznej lub precyzyjnego katalogowania.

### Kroki implementacji

1. **Użyj ponownie instancji `Metadata`** z poprzedniej sekcji.  
2. **Przejdź do kontenera IFD** za pomocą `metadata.getExif().getIfd0()`.  
3. **Odczytaj właściwości** takie jak `getBodySerialNumber()` i `getUserComment()`.  
4. **Wyświetl dane** lub zmapuj je do swojego modelu domenowego.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Jak pobrać dane GPS (szerokość, długość geograficzna) z pliku PSD

Wiele nowoczesnych aparatów osadza współrzędne GPS w bloku EXIF. `GpsInfo` przechowuje współrzędne geograficzne wyodrębnione z danych EXIF. Wywołaj `metadata.getExif().getGpsInfo()`, a następnie użyj `getLatitude()`, `getLongitude()` i `getAltitude()`, aby uzyskać precyzyjne dane lokalizacyjne — bez dodatkowego parsowania.

### Szczegółowe kroki

1. **Uzyskaj obiekt informacji GPS**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Odczytaj szerokość i długość geograficzną**: `gps.getLatitude()` zwraca `double` w stopniach dziesiętnych.  
3. **Obsłuż brakujące dane**: API zwraca `null`, jeśli tag jest nieobecny, więc zabezpiecz się przed `NullPointerException`.

> **Typowy problem:** Niektóre pliki PSD przechowują współrzędne GPS w liczbach wymiernych; biblioteka normalizuje je automatycznie, ale starsze pliki mogą wymagać ręcznej konwersji.

## Typowe problemy i rozwiązywanie

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| `Unsupported format` exception | Używanie starszej wersji GroupDocs.Metadata, która nie rozpoznaje PSD | Uaktualnij do wersji 24.12 lub nowszej |
| `NullPointerException` przy wywoływaniu `getArtist()` | Tag EXIF nie jest obecny w pliku źródłowym | Sprawdź `metadata.getExif().hasArtist()` przed odczytem |
| Błąd licencji po 30 dniach | Plik licencji nie został znaleziony w classpath | Umieść `metadata.lic` w `src/main/resources` lub ustaw `Metadata.setLicense("path/to/license")` |

## Najczęściej zadawane pytania

**P: Czy mogę wyodrębnić metadane EXIF z pliku PSD chronionego hasłem?**  
O: Tak. Załaduj plik przy użyciu `new Metadata("file.psd", "password")`, a następnie uzyskaj dostęp do danych EXIF jak zwykle.

**P: Czy GroupDocs.Metadata obsługuje przetwarzanie wsadowe wielu plików PSD?**  
O: Zdecydowanie tak. Utwórz obiekt `Metadata` w pętli lub użyj pomocnika `MetadataCollection` do efektywnego przetwarzania katalogów.

**P: Jakie wersje Javy są oficjalnie wspierane?**  
O: Java 8 do Java 21 są w pełni przetestowane. Biblioteka używa wyłącznie standardowych API, więc działa na każdej zgodnej JVM.

**P: Czy można zapisać dane EXIF z powrotem do pliku PSD?**  
O: Tak. Po modyfikacji właściwości za pomocą obiektu `Exif`, wywołaj `metadata.save("output.psd")`, aby zachować zmiany.

**P: Jak duży plik PSD może obsłużyć biblioteka bez wyczerpania pamięci?**  
O: GroupDocs.Metadata strumieniuje dane i może przetwarzać pliki do **2 GB** na typowej maszynie z 8 GB RAM, dzięki swojej niskopamięciowej architekturze.

## Podsumowanie

Teraz wiesz **jak wyodrębnić metadane EXIF** z plików PSD przy użyciu GroupDocs.Metadata dla Javy, od podstawowych tagów po zaawansowane informacje IFD i GPS. Zintegruj te fragmenty kodu w swoim potoku przetwarzania obrazów, aby automatyzować katalogowanie, kontrole zgodności lub usługi oparte na lokalizacji. Aby zgłębić temat, spróbuj wyodrębnić metadane z innych obsługiwanych formatów (JPEG, TIFF, PNG) lub eksperymentuj z możliwościami zapisu, aby osadzić własne tagi.

---

**Ostatnia aktualizacja:** 2026-08-10  
**Testowano z:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs

## Powiązane samouczki

- [Wyodrębnianie zasobów obrazu z plików PSD przy użyciu GroupDocs.Metadata w Javie: Kompletny przewodnik](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Wyodrębnianie nagłówka PSD i informacji o warstwach przy użyciu GroupDocs.Metadata dla Javy: Kompletny przewodnik](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Wyodrębnianie właściwości MakerNote jako tagi TIFF/EXIF przy użyciu GroupDocs.Metadata w Javie](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)