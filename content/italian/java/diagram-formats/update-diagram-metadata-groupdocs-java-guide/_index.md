---
date: '2026-01-19'
description: Scopri come modificare la data di creazione e automatizzare l'aggiornamento
  dei metadati per i file di diagramma utilizzando GroupDocs.Metadata in Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Modifica l'ora di creazione nei metadati del diagramma con GroupDocs Java
type: docs
url: /it/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Modifica dell'ora di creazione nei metadati del diagramma con GroupDocs Java

Aggiornare manualmente le proprietà dei metadati come creatore, **ora di creazione**, e categoria può risultare noioso. Automatizza questo processo con la libreria GroupDocs.Metadata per Java e potrai **modificare l'ora di creazione** e altre proprietà integrate in un unico passaggio ripetibile. Questa guida ti mostra come configurare la libreria, aggiornare i metadati del diagramma e applicare consigli di performance per mantenere i documenti coerenti e ricercabili.

## Risposte rapide
- **Qual è l'obiettivo principale?** Modificare l'ora di creazione e altri metadati nei file di diagramma.  
- **Quale libreria devo usare?** GroupDocs.Metadata per Java.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per i test; è richiesta una licenza completa per la produzione.  
- **Posso elaborare in batch molti diagrammi?** Sì—usa lo stesso approccio all'interno di un ciclo o di uno stream parallelo.  
- **Quale versione di di diagram, VSDX) con una nuova data. Questo è utile quando è necessario che i metadati del file riflettano la data effettiva di elaborazione anziché la data originale di creazione.

## Perché automatizzare l'aggiornamento dei metadati per i diagrammi?
- **Coerenza:** Garantisce che ogni file segua le stesse regole di denominazione e categorizzazione.  
- **Ricercabilità:** Parole chiave e categorie aggiornate migliorano la scoperta dei documenti nelle soluzioni DMS.  
- **Conformità:** Aiuta a soddisfare i requisiti di audit assicurando timestamp accurati.  

## Prerequisiti
- **Java Development Kit (JDK) 8+** installato.  
- **IDE** come IntelliJ IDEA o Eclipse.  
- **Maven** (o gestione manuale dei JAR) per le dipendenze.  
- Conoscenza di base delle classi, dei metodi e della gestione delle eccezioni in Java.

### Librerie e dipendenze richieste
Aggiungi il repository e la dipendenza seguenti al tuo file `pom.xml` se usi Maven:

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
Se preferisci scaricare direttamente, visita [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) per ottenere l'ultima versione.

### Configurazione dell'ambiente
- JDK 8 o più recente.  
- IntelliJ IDEA, Eclipse o qualsiasi IDE compatibile con Java.  

### Prerequisiti di conoscenza
Comprendere la sintassi Java e le operazioni di I/O di base renderà il tutorial più fluido, ma i passaggi sono spiegati in linguaggio semplice.

## Configurazione di GroupDocs.Metadata per Java
### Istruzioni di installazione
**Utenti Maven:** Lo snippet sopra aggiunge il repository e il JAR necessario automaticamente.  
**Utenti download diretto:** Dopo aver scaricato il JAR da [GroupDocs](https://releases.groupdocs.com/metadata/java/), aggiungilo al classpath del tuo progetto.

### Acquisizione della licenza
- **Prova gratuita:** Esplora la libreria senza costi.  
- **Licenza temporanea:** Ottieni una licenza temporanea per test estesi [qui](https://purchase.groupdocs.com/temporary-license/).  
- **Acquisto:** Acquista una licenza completa per gli ambienti di produzione.

### Inizializzazione di base
Per iniziare a usare GroupDocs.Metadata, importa la classe e apri un file di diagramma:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Con la libreria inizializzata, ora puoi modificare qualsiasi proprietà integrata, inclusa l'ora di creazione.

## Guida all'implementazione
### Come cambiare passo come'ora di creazione** e aggiornare altre proprietà comuni come autore, azienda e categoria.

#### Passo 1: Carica il documento diagramma
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*Spiegazione:* Il costruttore `Metadata` riceve il percorso del tuo file diagramma. Il blocco try‑with‑resources garantisce che il file venga chiuso correttamente dopo l'operazione.

#### Passo 2: Accedi al pacchetto radice
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*Spiegazione:* Il pacchetto radice ti dà accesso diretto a tutti i campi di metadati integrati per il diagramma.

#### Passo 3: Imposta la proprietà Creator
```java
root.getDocumentProperties().setCreator("test author");
```
*Spiegazione:* Assegna un nuovo nome autore. Sostituisci `"test author"` con il creatore reale.

#### Passo 4: **Cambia l'ora di creazione**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Spiegazione:* Questa riga **cambia l'ora di creazione** alla data e ora corrente del sistema. Puoi anche fornire un'istanza `Date` specifica se ti serve un timestamp personalizzato.

#### Passo 5: Definisci le informazioni aziendali
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Spiegazione:* Memorizza il nome dell'azienda associata al diagramma—utile per il tracciamento aziendale.

#### Passo 6: Imposta la categoria del documento
```java
root.getDocumentProperties().setCategory("test category");
```
*Spiegazione:* Categorizza il file, aiutandoti a **aggiornare la categoria del diagramma** in modo coerente nell'intero repository.

#### Passo 7: Aggiungi parole chiave
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Spiegazione:* Le parole chiave migliorano la ricercabilità; puoi elencare tutti i termini rilevanti per il contenuto del diagramma.

#### Passo 8: Salva le modifiche
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Spiegazione:* Persiste tutte le modifiche in un nuovo file, lasciando intatto l'originale.

### Problemi comuni e risoluzione
- **File non trovato:** Verifica il percorso di input e assicurati che l'estensione del file corrisponda al formato reale.  
- **Accesso negato:** Controlla i permessi di lettura/scrittura per le directory di input e output.  
- **Formato data non valido:** Usa oggetti `java.util.Date` o `java.time` compatibili con l'API.  

## Applicazioni pratiche
1. **Automazione dell'archiviazione dei documenti** – Quando sposti vecchi diagrammi in archivio, cambia automaticamente **l'ora di creazione** alla data di archiviazione e imposta una categoria uniforme.  
2. **Integrazione con il version control** – Mantieni i timestamp sincronizzati con i commit Git aggiornando l'ora di creazione ad ogni rilascio.  
3. **Standardizzazione DMS aziendale** – Applica una politica aziendale per autore, azienda e parole chiave su tutti gli asset di diagrammi.

## Considerazioni sulle prestazioni
- **Elaborazione batch:** Avvolgi i passaggi sopra in un ciclo per gestire decine di file in un'unica esecuzione.  
- **Gestione della memoria:** Rilascia prontamente ogni istanza `Metadata` (il blocco try‑with‑resources lo fa automaticamente).  
- **Esecuzione asincrona:** Per batch di grandi dimensioni, considera `CompletableFuture` per eseguire gli aggiornamenti in parallelo senza bloccare il thread principale.

## Conclusione
Ora sai come **cambiare l'ora di creazione** e aggiornare altre proprietà di metadati integrate per i documenti diagramma usando GroupDocs.Metadata in Java. Automatizzando questi passaggi, potrai mantenere documentazione coerente, ricercabile e conforme in tutta l'organizzazione.

**Passi successivi**
- Sperimenta con altri formati supportati da GroupDocs.Metadata (PDF, DOCX, ecc.).  
- Integra il codice in una pipeline CI/CD per imporre standard di metadati ad ogni build.  

Pronto a provarlo? Vai su [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) e inizia a implementare la tua automazione dei metadati oggi.

---

**Ultimo aggiornamento:** 2026-01-19  
**Testato con:** GroupDocs.Metadata 24.12  
**Autore:** GroupDocs  

## Domande frequenti

**D: Posso usare questo approccio con altri formati di diagramma come VSDX?**  
R: Sì, la stessa API funziona per tutti i formati di diagramma supportati da GroupDocs.Metadata.

**D: È necessaria una licenza per le build di sviluppo?**  
R: Una prova gratuita è sufficiente per sviluppo e test; è richiesta una licenza completa per le distribuzioni in produzione.

**D: Come posso aggiornare più proprietà in una sola chiamata?**  
R: Imposta ogni proprietà sull'oggetto `DocumentProperties` prima di chiamare `metadata.save(...)`; la libreria le scrive tutte in una volta.

**D: È sicuro sovrascrivere il file originale?**  
R: È consigliabile salvare in un nuovo file (come mostrato) per evitare perdite di dati, quindi sostituire l'originale se necessario.

**D: E se devo impostare una data di creazione personalizzata invece dell'ora corrente?**  
R: Crea un'istanza `java.util.Date` (o `java.time`) con il timestamp desiderato e passala a `setTimeCreated`.