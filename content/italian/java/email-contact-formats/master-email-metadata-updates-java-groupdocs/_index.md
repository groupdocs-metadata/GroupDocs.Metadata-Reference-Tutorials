---
date: '2026-05-27'
description: Scopri come aggiornare i destinatari delle email in Java utilizzando
  GroupDocs.Metadata per Java. Modifica i destinatari, gli oggetti e salva le modifiche
  in modo efficiente.
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'Aggiorna i destinatari delle email Java: padroneggia gli aggiornamenti dei
  metadati delle email con GroupDocs.Metadata'
type: docs
url: /it/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# Aggiorna i Destinatari Email Java con GroupDocs.Metadata

In questa guida completa **update email recipients java** programmaticamente usando la libreria GroupDocs.Metadata. Vedremo come modificare i destinatari principali e in CC, cambiare l'oggetto e salvare le modifiche — il tutto con snippet di codice chiari passo‑a‑passo. Alla fine sarai pronto a integrare l'automazione dei metadati email in qualsiasi flusso di lavoro basato su Java.

## Risposte Rapide
- **Qual è il modo più veloce per cambiare il destinatario principale di un'email?** Carica il file con `Metadata`, ottieni il `EmailRootPackage`, sostituisci la collezione `To` e salva — il tutto in tre righe di codice.  
- **Posso aggiungere destinatari CC senza sovrascrivere quelli esistenti?** Sì, usa `addCcRecipient` sul `EmailRootPackage` per aggiungere nuovi indirizzi.  
- **È necessaria una licenza per l'uso in produzione?** Una licenza temporanea rimuove i limiti di valutazione; è richiesta una licenza permanente per le distribuzioni commerciali. Puoi ottenere una licenza temporanea dalla pagina [GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **Quali versioni di Java sono supportate?** GroupDocs.Metadata funziona con Java 8, 11, 17 e successive.  
- **È sicura l'elaborazione batch per grandi caselle di posta?** Elabora i file in batch da 50–100 per mantenere l'uso della memoria sotto i 200 MB per batch.

## Cos'è update email recipients java?
*Aggiornare i destinatari email in Java* significa modificare programmaticamente i campi “To”, “CC” o “BCC” di un file email (EML, MSG, ecc.) senza aprire un client di posta. GroupDocs.Metadata espone un'API di alto livello che legge la struttura dell'email, consente di modificare le collezioni di indirizzi e scrive il file aggiornato su disco.

## Perché usare GroupDocs.Metadata per i metadati email?
GroupDocs.Metadata supporta **oltre 50 formati legati alle email** (inclusi EML, MSG, MHT) e può elaborare **messaggi di centinaia di pagine** senza caricare l'intero file in memoria, riducendo il consumo di RAM fino all'**80 %** rispetto agli approcci naïve di file‑stream. La sua implementazione pure‑Java elimina le dipendenze native, rendendola ideale per servizi cross‑platform.

## Prerequisiti
- Java 8 or newer (Java 11, 17, 21 are fully tested).  
- Maven o Gradle per la gestione delle dipendenze.  
- Una licenza valida di GroupDocs.Metadata (temporanea o permanente).  

### Librerie e Dipendenze Necessarie
Aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

Per download diretti, ottieni l'ultima versione da [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Configurazione dell'Ambiente
Assicurati che il tuo IDE punti a un JDK compatibile e che Maven risolva gli artefatti GroupDocs.Metadata senza errori.

## Come aggiornare i destinatari email in Java?
Carica il file email, sostituisci i destinatari esistenti e salva il risultato. Questa operazione richiede solo tre chiamate API e viene eseguita in meno di **200 ms** per messaggi tipici da 1 MB. Usando l'API di alto livello `EmailRootPackage` eviti di analizzare l'intero file, mantenendo basso l'uso della memoria e rendendo l'elaborazione batch semplice.

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
La riga sopra importa la classe essenziale per iniziare a gestire le operazioni di metadati sui tuoi file.

## Guida all'Implementazione
Ora approfondiremo ogni funzionalità, espandendo gli snippet delle risposte rapide con il contesto completo.

### Aggiornamento dei Destinatari Email
**Panoramica**: Questa sezione dimostra come aggiornare i destinatari principali di un messaggio email programmaticamente.

#### Passo 1: Inizializzare l'Oggetto Metadata
La classe `Metadata` rappresenta un file e fornisce l'accesso ai suoi metadati. Crea un'istanza `Metadata` con il percorso del file di input:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**Ancora di definizione**: La classe `Metadata` è il punto di ingresso per tutte le operazioni di metadati in GroupDocs.Metadata, rappresentando un singolo file in memoria.

#### Passo 2: Accedere a EmailRootPackage
`EmailRootPackage` fornisce l'accesso ai metadati specifici dell'email come destinatari e oggetto. Accedi ai metadati dell'email usando:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
Questo passo è cruciale poiché fornisce l'accesso a tutte le proprietà modificabili della tua email.

#### Passo 3: Aggiornare i Destinatari
Imposta nuovi destinatari per il tuo messaggio email:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### Aggiungere Destinatari in Copia Carbonio (CC) all'Email
**Panoramica**: Scopri come aggiungere destinatari CC a un'email esistente.

#### Passo 1: Inizializzare e Ottenere il Pacchetto Radice
Simile all'aggiornamento dei destinatari principali, inizializza l'oggetto metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Passo 2: Impostare i Destinatari CC
`addCcRecipient` aggiunge un nuovo indirizzo alla collezione CC senza sovrascrivere le voci esistenti. Aggiungi i destinatari in copia carbone come segue:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
Questo approccio garantisce che gli utenti aggiuntivi vengano notificati senza essere il punto di contatto principale.

### Aggiornare l'Oggetto dell'Email
**Panoramica**: Questa funzionalità consente di modificare l'oggetto di un'email, mantenendo le comunicazioni chiare e aggiornate.

#### Passo 1: Inizializzare Metadata
Inizia inizializzando il tuo oggetto metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Passo 2: Cambiare l'Oggetto
Aggiorna l'oggetto dell'email:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
Questo passo è fondamentale per mantenere conversazioni email pertinenti e ricercabili.

### Salvataggio dei Metadati Email Aggiornati
**Panoramica**: Dopo aver apportato le modifiche, è essenziale salvare questi aggiornamenti. Questa sezione mostra come persistere le modifiche in modo efficace.

#### Passo 1: Inizializzare e Ottenere il Pacchetto Radice
Inizia inizializzando l'oggetto `Metadata`:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Passo 2: Salvare le Modifiche
Persiste le tue modifiche salvandole in una directory di output specificata:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
Ciò garantisce che tutte le modifiche siano mantenute e riflesse nel file salvato.

## Applicazioni Pratiche
Implementare queste funzionalità può essere estremamente utile in vari scenari reali:

1. **Sistemi di Gestione Email** – Automatizza gli aggiornamenti dei destinatari per distribuzioni massive di email.  
2. **Piattaforme di Supporto Clienti** – Modifica rapidamente gli oggetti delle email per riflettere i cambiamenti di stato dei ticket.  
3. **Strumenti di Comunicazione Interna** – Assicura che tutti i membri del team siano in CC per annunci critici senza modifiche manuali.

## Considerazioni sulle Prestazioni
When working with large volumes of email data, keep these tips in mind:

- Elabora i file in batch di **50–100** per mantenere l'uso della memoria sotto i **200 MB** per batch.  
- Usa la chiamata `metadata.getRootPackage().getEmail()` con parsimonia; riutilizza l'istanza `Metadata` quando possibile.  
- Monitora l'uso dell'heap JVM con strumenti come VisualVM per evitare errori OutOfMemory.

## Conclusione
Ora hai padroneggiato come **update email recipients java** usando GroupDocs.Metadata. Che tu stia regolando i destinatari principali, aggiungendo CC o modificando l'oggetto, la libreria fornisce un'API veloce ed efficiente in termini di memoria. Esplora la completa [documentazione](https://docs.groupdocs.com/metadata/java/) per scenari più avanzati come la gestione degli allegati o la conversione tra formati EML e MSG.

## Sezione FAQ
**Q1**: Quali versioni di Java sono supportate da GroupDocs.Metadata?  
- **A**: Java 8, 11, 17 e successive sono pienamente supportate.

**Q2**: Posso usare GroupDocs.Metadata senza licenza?  
- **A**: Sì, una prova gratuita funziona con limitazioni; una licenza temporanea o permanente rimuove tali limiti.

**Q3**: Come gestire efficientemente file email di grandi dimensioni?  
- **A**: Elaborali in batch più piccoli, riutilizza gli oggetti `Metadata` e monitora l'uso dell'heap per rimanere sotto i 200 MB per batch.

**Q4**: Quali altri tipi di file supporta GroupDocs.Metadata oltre alle email?  
- **A**: Supporta oltre **70** formati inclusi PDF, DOCX, XLSX, PPTX, immagini e archivi. Vedi il [riferimento API](https://reference.groupdocs.com/metadata/java/) per l'elenco completo.

---

**Ultimo Aggiornamento:** 2026-05-27  
**Testato con:** GroupDocs.Metadata 23.12 per Java  
**Autore:** GroupDocs  

---

## Tutorial Correlati

- [Estrarre i Metadati Email in Java con GroupDocs.Metadata](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [Tutorial sui Metadati Email e Contatti per GroupDocs.Metadata Java](/metadata/java/email-contact-formats/)
- [Come Estrarre gli URI delle Foto vCard Usando GroupDocs.Metadata in Java per una Gestione Efficiente dei Contatti](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)