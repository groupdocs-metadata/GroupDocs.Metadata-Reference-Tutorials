---
date: '2026-04-26'
description: Scopri come estrarre i livelli PSD e le informazioni dell'intestazione
  con GroupDocs.Metadata per Java. Questa guida copre l'installazione, esempi di codice
  e consigli per l'elaborazione batch.
keywords:
- extract psd layers
- how to extract psd
- groupdocs metadata java
title: Estrai i livelli PSD usando GroupDocs.Metadata per Java
type: docs
url: /it/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/
weight: 1
---

# Estrarre i livelli psd usando GroupDocs.Metadata per Java

Nelle moderne pipeline di progettazione, la possibilità di **extract psd layers** programmaticamente consente di risparmiare innumerevoli ore di lavoro manuale. Che tu debba esaminare grandi librerie di design, integrare risorse PSD in un CMS o generare report sull'uso dei livelli, GroupDocs.Metadata per Java ti offre un'API pulita e type‑safe per estrarre sia i dettagli dell'intestazione sia le informazioni sui singoli livelli dai file Photoshop.

## Risposte rapide
- **Cosa posso estrarre?** Campi dell'intestazione PSD (modalità colore, numero di canali, ecc.) e metadati completi dei livelli (nome, dimensione, visibilità).  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per la valutazione; è necessaria una licenza permanente per la produzione.  
- **Posso elaborare molti file contemporaneamente?** Sì – combina le chiamate API con gli stream di Java per elaborare in batch i file PSD.  
- **Quale versione di Java è supportata?** Java 8 + (la libreria è costruita per JDK moderni).  
- **Maven è l'unico modo per installare?** No – è possibile scaricare il JAR direttamente dalla pagina di rilascio di GroupDocs.

## Cos'è “extract psd layers”?
Estrarre i livelli PSD significa leggere programmaticamente gli attributi di ogni livello — come nome, dimensioni, profondità di bit e flag di visibilità — senza aprire Photoshop. Questo consente flussi di lavoro automatizzati, indicizzazione delle risorse e analisi di massa.

## Perché usare GroupDocs.Metadata per Java?
- **Zero‑install Photoshop dependency:** La libreria analizza i file PSD direttamente.  
- **Rich object model:** Accedi ai dati dell'intestazione e dei livelli tramite getter intuitivi.  
- **Performance‑focused:** Funziona con file di grandi dimensioni quando chiudi rapidamente gli oggetti `Metadata`.  
- **Batch‑ready:** Combina con gli stream paralleli di Java per un'elaborazione ad alta velocità.

## Prerequisiti
- JDK 8 o versioni successive installato.  
- Un IDE (IntelliJ IDEA, Eclipse o VS Code) per scrivere ed eseguire codice Java.  
- Maven (opzionale) se preferisci la gestione delle dipendenze.  

## Configurazione di GroupDocs.Metadata per Java

### Configurazione Maven
Se gestisci le dipendenze con Maven, aggiungi il repository e la dipendenza al tuo `pom.xml`:

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
In alternativa, scarica l'ultima versione di GroupDocs.Metadata per Java da [GroupDocs Metadata Releases](https://releases.groupdocs.com/metadata/java/).

#### Passaggi per l'acquisizione della licenza
- **Free Trial:** Inizia con una prova per esplorare l'API.  
- **Temporary License:** Ottieni una chiave temporanea per una valutazione estesa.  
- **Purchase:** Acquista una licenza completa per l'uso in produzione senza restrizioni.

### Inizializzazione di base
Una volta che la libreria è nel tuo classpath, puoi creare un'istanza `Metadata` e puntarla a un file PSD:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class SetupGroupDocs {
    public static void main(String[] args) {
        // Basic initialization of Metadata object with a PSD file path
        try (Metadata metadata = new Metadata("path/to/your/file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            System.out.println("Setup complete! Ready to explore PSD features.");
        }
    }
}
```

## Guida all'implementazione

### Lettura delle informazioni dell'intestazione PSD

#### Passo 1: Apri il file PSD
Per prima cosa, apri il file con la classe `Metadata`:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ReadPsdHeader {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/psd_file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
```

#### Passo 2: Estrai le informazioni dell'intestazione
Ora estrai i campi dell'intestazione di tuo interesse:

```java
            System.out.println(root.getPsdPackage().getChannelCount()); // Number of channels in the image
            System.out.println(root.getPsdPackage().getColorMode());    // Color mode (e.g., RGB, Grayscale)
            System.out.println(root.getPsdPackage().getCompression());  // Compression method used
            System.out.println(root.getPsdPackage().getPhotoshopVersion()); // Photoshop version metadata
        }
    }
}
```

**Spiegazione dei getter chiave**
- `getChannelCount()` – numero totale di canali immagine (RGB, alfa, ecc.).  
- `getColorMode()` – spazio colore come RGB o CMYK.  
- `getCompression()` – algoritmo usato (es. RLE, ZIP).  
- `getPhotoshopVersion()` – la versione di Photoshop che ha creato il file.

### Estrazione delle informazioni sui livelli PSD

#### Passo 1: Apri il file PSD (di nuovo per chiarezza)
Riutilizziamo lo stesso schema per accedere ai dati dei livelli:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdLayer;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractPsdLayers {
    public static void run() {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/psd_file.psd")) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
```

#### Passo 2: Itera attraverso i livelli
Itera su ogni `PsdLayer` e stampa le sue proprietà:

```java
            for (PsdLayer layer : root.getPsdPackage().getLayers()) {
                System.out.println(layer.getName());         // Layer name
                System.out.println(layer.getBitsPerPixel());  // Bits per pixel of the layer
                System.out.println(layer.getChannelCount()); // Number of channels in the layer
                System.out.println(layer.getFlags());        // Flags set for the layer (e.g., visible, locked)
                System.out.println(layer.getHeight());       // Layer height
                System.out.println(layer.getWidth());        // Layer width
            }
        }
    }
}
```

**Getter chiave dei livelli**
- `getName()` – etichetta del livello leggibile dall'uomo.  
- `getBitsPerPixel()` – profondità di colore del livello.  
- `getChannelCount()` – quanti canali contiene questo livello.  
- `getFlags()` – visibilità, protezione e altri bit di stato.  
- `getHeight()` / `getWidth()` – dimensioni in pixel della tela del livello.

## Applicazioni pratiche
Ecco cinque scenari reali in cui **extract psd layers** brilla:

1. **Analisi automatizzata dei file** – Scansiona un repository di design, categorizza i file per modalità colore o numero di livelli e genera report di inventario.  
2. **Gestione delle risorse di design** – Memorizza i metadati dei livelli in un database per alimentare la ricerca e il riutilizzo nei progetti.  
3. **Integrazione CMS** – Estrai i nomi e le dimensioni dei livelli per creare automaticamente miniature o gallerie di anteprima.  
4. **Audit del controllo versione** – Traccia le modifiche della versione di Photoshop tra le risorse per conformità e strategie di rollback.  
5. **Strumenti di reporting personalizzati** – Costruisci dashboard che visualizzano la distribuzione dei livelli (es. quanti file contengono livelli di regolazione).

## Considerazioni sulle prestazioni
Quando si gestiscono collezioni di PSD su scala gigabyte, tieni presenti questi consigli:

- **Ottimizza l'uso della memoria:** Usa sempre try‑with‑resources (`try (Metadata …)`) per chiudere gli oggetti rapidamente.  
- **Elaborazione batch:** Usa gli stream di Java o i servizi executor per processare i file in parallelo, riducendo il tempo totale.  
- **Profilazione:** Strumenti come VisualVM o YourKit possono rivelare picchi di memoria; concentrati sul ciclo di vita di `Metadata`.

## Problemi comuni e soluzioni

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| `java.lang.NoClassDefFoundError` for `org.apache.commons.io.IOUtils` | Dipendenza transitiva mancante | Aggiungi Apache Commons IO alle tue `dependencies` Maven. |
| Il conteggio dei livelli restituisce 0 | File aperto in modalità sola lettura con permessi limitati | Assicurati che il file PSD sia accessibile e non corrotto. |
| `null` inatteso per `getColorMode()` | Uso di una versione PSD più vecchia non completamente supportata | Aggiorna alla versione più recente di GroupDocs.Metadata (24.12) che aggiunge il supporto legacy. |

## Domande frequenti

**Q: Come posso elaborare in batch decine di file PSD per estrarre i livelli?**  
A: Combina la chiamata `Metadata` all'interno di uno stream `Files.list(Paths.get("folder"))` e raccogli i risultati in un CSV o in un database.

**Q: Posso estrarre livelli nascosti o bloccati?**  
A: Sì. Il metodo `getFlags()` indica visibilità e stato di blocco, consentendoti di filtrare o includerli secondo necessità.

**Q: La libreria supporta file PSD più grandi di 2 GB?**  
A: L'API funziona con file fino al limite di memoria indirizzabile della JVM; per file molto grandi, aumenta l'heap (`-Xmx`) e processa a blocchi.

**Q: Esiste un modo per esportare le miniature dei livelli?**  
A: Sebbene GroupDocs.Metadata si concentri sui metadati, puoi recuperare i dati pixel grezzi tramite l'API `PsdLayer` e poi usare una libreria di immagini (es. TwelveMonkeys) per generare le miniature.

**Q: Quale licenza è necessaria per l'uso commerciale?**  
A: È necessaria una licenza a pagamento di GroupDocs.Metadata per le distribuzioni in produzione. Una chiave di prova funziona solo per sviluppo e test.

## Conclusione
Ora disponi di un esempio completo, end‑to‑end, su come **extract psd layers** e le informazioni dell'intestazione usando GroupDocs.Metadata per Java. Integrando questi snippet nel tuo flusso di lavoro, puoi automatizzare l'analisi delle risorse, aumentare la produttività e mantenere un inventario di design pulito.

**Prossimi passi**
- Sperimenta con l'API per estrarre proprietà PSD aggiuntive (es., contenuti dei livelli di testo).  
- Combina questa estrazione di metadati con un database o Elasticsearch per risorse di design ricercabili.  
- Esplora i pattern di elaborazione batch per gestire migliaia di file in modo efficiente.

---

**Ultimo aggiornamento:** 2026-04-26  
**Testato con:** GroupDocs.Metadata 24.12  
**Autore:** GroupDocs  

---