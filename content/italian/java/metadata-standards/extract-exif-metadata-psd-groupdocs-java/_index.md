---
date: '2026-08-10'
description: Scopri come estrarre i metadati EXIF dai file PSD utilizzando GroupDocs.Metadata
  per Java. Questa guida copre l'estrazione di base, i pacchetti IFD, i dati GPS e
  casi d'uso reali.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Scopri come estrarre i metadati EXIF dai file PSD utilizzando GroupDocs.Metadata
  per Java. Guida passo‑passo, esempi di codice e consigli di risoluzione dei problemi
  per gli sviluppatori.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Come estrarre i metadati EXIF dai file PSD con GroupDocs.Metadata
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
title: Come estrarre i metadati EXIF dai file PSD con GroupDocs.Metadata
type: docs
url: /it/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Come estrarre i metadati EXIF da file PSD con GroupDocs.Metadata

Estrarre i **metadati EXIF** dai file PSD è un passaggio di routine ma potente quando è necessario verificare la provenienza delle immagini, automatizzare l’etichettatura delle risorse o creare librerie multimediali ricercabili. In questo tutorial scoprirai **come estrarre EXIF** rapidamente con GroupDocs.Metadata per Java, vedrai le chiamate API esatte e imparerai a gestire pacchetti IFD avanzati e coordinate GPS. Alla fine sarai pronto a integrare l'estrazione dei metadati in qualsiasi flusso di lavoro basato su Java.

## Risposte rapide
La classe `Metadata` rappresenta un file e fornisce l'accesso ai suoi metadati.

- **Qual è la prima riga di codice?** `Metadata metadata = new Metadata("sample.psd");`
- **Quale metodo restituisce il nome dell'artista?** `metadata.getExif().getArtist();`
- **Posso leggere i dati GPS?** Sì – usa `metadata.getExif().getGpsInfo();`
- **È necessaria una licenza per la produzione?** È richiesta una licenza valida di GroupDocs.Metadata oltre il periodo di prova.
- **Versione Java supportata?** Java 8 o successive (fino a Java 21).

## Cos'è il metadato EXIF?
I metadati EXIF (Exchangeable Image File Format) memorizzano le impostazioni della fotocamera, i timestamp di creazione e i dati di posizione all'interno dei file immagine. GroupDocs.Metadata legge queste informazioni direttamente dalla struttura binaria dei file PSD, esponendole tramite una pulita API Java. Consente agli sviluppatori di recuperare programmaticamente dettagli come modello della fotocamera, tempo di esposizione e coordinate GPS senza ispezione manuale.

## Perché usare GroupDocs.Metadata per Java?
GroupDocs.Metadata supporta **oltre 30 formati di file** (inclusi PSD, JPEG, PNG, TIFF) e può elaborare file fino a **2 GB** senza caricare l'intero documento in memoria. La libreria estrae **più di 150 tag EXIF distinti**, garantendo di avere l'intero set di attributi della fotocamera e GPS necessari per analisi o conformità.

## Prerequisiti
- **Java Development Kit (JDK) 8** o più recente installato sulla tua macchina.  
- **Maven** per la gestione delle dipendenze.  
- **GroupDocs.Metadata per Java versione 24.12** (o più recente).  
- Familiarità di base con classi Java, oggetti e gestione delle eccezioni.

### Librerie e dipendenze richieste
| Dependency | Maven coordinates |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Configurazione dell'ambiente
Dovresti avere un IDE compatibile con Maven, come IntelliJ IDEA o Eclipse. Crea un nuovo progetto Maven o aggiungi la dipendenza a uno esistente.

## Come configurare GroupDocs.Metadata per Java
GroupDocs.Metadata può essere aggiunto a un progetto Maven con poche righe di configurazione. I passaggi seguenti mostrano come includere il repository e la dipendenza affinché la libreria sia disponibile nel classpath.

### Configurazione Maven
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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

### Download diretto
In alternativa, scarica l'ultimo JAR dalla pagina ufficiale delle release: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Acquisizione della licenza
Per eseguire la libreria oltre il periodo di prova di 30 giorni, ottieni una licenza temporanea o completa:

1. Visita la [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Scegli **temporary** per i test o **full** per la produzione.  
3. Segui le istruzioni a schermo per incorporare il file di licenza (`metadata.lic`) nel classpath Java.

### Inizializzazione e configurazione di base
After the library is on the classpath, initialize it as shown below:

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

## Come estrarre le proprietà di base dei metadati EXIF da un'immagine PSD
Questa sezione spiega come caricare un file PSD, accedere al contenitore EXIF e leggere i tag più comuni come **artist**, **copyright** e **software**. Il processo prevede la creazione di un'istanza `Metadata`, la chiamata a `getExif()` e poi il recupero delle singole proprietà con semplici metodi getter.

### Implementazione passo‑passo
1. **Crea un'istanza `Metadata`** che punti al tuo file PSD.  
2. **Chiama `getExif()`** per ottenere il contenitore EXIF.  
3. **Leggi le proprietà individuali** come `getArtist()`, `getCopyright()` e `getSoftware()`.  
4. **Stampa o memorizza** i valori secondo la logica della tua applicazione.

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

> **Consiglio:** L'oggetto `Metadata` rileva automaticamente il formato del file, quindi puoi riutilizzare lo stesso codice per file JPEG o TIFF senza modifiche.

## Come estrarre le proprietà del pacchetto EXIF IFD da un'immagine PSD
La sezione IFD (Image File Directory) contiene dettagli tecnici più approfonditi come **camera serial number**, **lens model** e **user comments**. `Ifd0` rappresenta il principale Image File Directory contenente le informazioni di base della fotocamera. Estrarre questi campi è utile per analisi forense o catalogazione ad alta precisione.

### Passaggi di implementazione
1. **Riutilizza l'istanza `Metadata`** dalla sezione precedente.  
2. **Naviga al contenitore IFD** tramite `metadata.getExif().getIfd0()`.  
3. **Leggi le proprietà** come `getBodySerialNumber()` e `getUserComment()`.  
4. **Emetti i dati** o mappali al tuo modello di dominio.

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

## Come recuperare i dati GPS (latitudine, longitudine) da un file PSD
Molte fotocamere moderne incorporano le coordinate GPS nel blocco EXIF. `GpsInfo` contiene le coordinate geografiche estratte dai dati EXIF. Chiama `metadata.getExif().getGpsInfo()` e poi usa `getLatitude()`, `getLongitude()` e `getAltitude()` per ottenere dati di posizione precisi—nessuna ulteriore analisi è necessaria.

### Passaggi dettagliati
1. **Ottieni l'oggetto GPS info**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Leggi latitudine e longitudine**: `gps.getLatitude()` restituisce un `double` in gradi decimali.  
3. **Gestisci dati mancanti**: l'API restituisce `null` se il tag è assente, quindi proteggi il codice da `NullPointerException`.  

> **Errore comune:** Alcuni file PSD memorizzano le coordinate GPS in numeri razionali; la libreria le normalizza automaticamente, ma i file più vecchi potrebbero richiedere una conversione manuale.

## Problemi comuni e risoluzione
| Sintomo | Causa probabile | Soluzione |
|---------|-----------------|-----------|
| `Unsupported format` exception | Utilizzo di una versione più vecchia di GroupDocs.Metadata che non riconosce PSD | Aggiorna alla versione 24.12 o successiva |
| `NullPointerException` durante la chiamata a `getArtist()` | Tag EXIF non presente nel file sorgente | Verifica `metadata.getExif().hasArtist()` prima di leggere |
| Errore di licenza dopo 30 giorni | File di licenza non trovato nel classpath | Posiziona `metadata.lic` in `src/main/resources` o imposta `Metadata.setLicense("path/to/license")` |

## Domande frequenti

**Q: Posso estrarre i metadati EXIF da un file PSD protetto da password?**  
A: Sì. Carica il file con `new Metadata("file.psd", "password")` e poi accedi ai dati EXIF come al solito.

**Q: GroupDocs.Metadata supporta l'elaborazione batch di molti file PSD?**  
A: Assolutamente. Istanzia un oggetto `Metadata` all'interno di un ciclo, o utilizza l'helper `MetadataCollection` per elaborare le directory in modo efficiente.

**Q: Quali versioni Java sono ufficialmente supportate?**  
A: Java 8 fino a Java 21 sono completamente testate. La libreria utilizza solo API standard, quindi funziona su qualsiasi JVM conforme.

**Q: È possibile scrivere i dati EXIF nuovamente in un file PSD?**  
A: Sì. Dopo aver modificato le proprietà tramite l'oggetto `Exif`, chiama `metadata.save("output.psd")` per persistere le modifiche.

**Q: Qual è la dimensione massima di un file PSD che la libreria può gestire senza esaurire la memoria?**  
A: GroupDocs.Metadata trasmette i dati in streaming e può elaborare file fino a **2 GB** su una macchina tipica con 8 GB di RAM, grazie alla sua architettura a basso consumo di memoria.

## Conclusione
Ora sai **come estrarre i metadati EXIF** dai file PSD usando GroupDocs.Metadata per Java, dai tag di base a informazioni IFD e GPS avanzate. Integra questi snippet nella tua pipeline di elaborazione delle immagini per automatizzare la catalogazione, i controlli di conformità o i servizi basati sulla posizione. Per un'esplorazione più approfondita, prova a estrarre i metadati da altri formati supportati (JPEG, TIFF, PNG) o sperimenta le capacità di scrittura per inserire tag personalizzati.

---

**Ultimo aggiornamento:** 2026-08-10  
**Testato con:** GroupDocs.Metadata 24.12 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Estrai le risorse immagine dai file PSD usando GroupDocs.Metadata in Java: Guida completa](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Estrai l'intestazione PSD e le informazioni dei layer usando GroupDocs.Metadata per Java: Guida completa](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Estrai le proprietà MakerNote come tag TIFF/EXIF usando GroupDocs.Metadata in Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)