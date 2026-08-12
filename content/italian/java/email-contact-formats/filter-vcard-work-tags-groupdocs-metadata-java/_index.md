---
date: '2026-04-04'
description: Scopri come filtrare i tag di lavoro vCard usando GroupDocs.Metadata
  per Java. Questa guida mostra passo passo come filtrare i dati vCard in modo efficiente
  per una migliore gestione dei contatti.
keywords:
- how to filter vcard
- vCard work tags
- GroupDocs.Metadata Java
title: Come filtrare i tag di lavoro vCard con GroupDocs.Metadata per Java
type: docs
url: /it/java/email-contact-formats/filter-vcard-work-tags-groupdocs-metadata-java/
weight: 1
---

# Come filtrare i tag di lavoro vCard con GroupDocs.Metadata per Java

Gestire i contatti digitali in modo efficace è fondamentale nel mondo degli affari odierno, veloce e dinamico. In questo tutorial, **imparerai a filtrare i tag di lavoro vCard** usando GroupDocs.Metadata per Java, consentendoti di estrarre rapidamente e in modo affidabile solo le informazioni di contatto professionali più rilevanti.

## Risposte rapide
- **Cosa significa “filter vCard work tags”?** Rimuove i campi non legati al business, lasciando solo i dati specifici del lavoro.  
- **Quale libreria gestisce il filtraggio?** GroupDocs.Metadata per Java fornisce i metodi integrati `filterWorkTags()` e `filterPreferred()`.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per la valutazione; è richiesta una licenza permanente per la produzione.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore.  
- **È possibile integrarlo con un CRM?** Sì—i dati filtrati possono essere inviati direttamente alla maggior parte delle piattaforme CRM.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- **GroupDocs.Metadata per Java** (24.12 o più recente).  
- JDK 8 + e un IDE come IntelliJ IDEA o Eclipse.  
- Conoscenze di base di Java e familiarità con il formato vCard.

## Configurazione di GroupDocs.Metadata per Java

### Configurazione Maven
Aggiungi il repository e la dipendenza al tuo `pom.xml`:

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
In alternativa, scarica l'ultima versione di GroupDocs.Metadata da [Versioni di GroupDocs.Metadata per Java](https://releases.groupdocs.com/metadata/java/).

### Acquisizione della licenza
- **Prova gratuita** – esplora tutte le funzionalità senza costi.  
- **Licenza temporanea** – periodo di test esteso.  
- **Acquisto** – supporto completo per la produzione.

Con la libreria pronta, passiamo al codice di filtraggio effettivo.

## Come filtrare i tag di lavoro vCard in Java

### Passo 1: Carica il file vCard
Sostituisci il percorso segnaposto con la posizione del tuo file `.vcf`:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your_vcard_file.vcf")) {
    // Code continues...
}
```

### Passo 2: Accedi al pacchetto radice
Recupera il pacchetto radice per lavorare con la struttura vCard sottostante:

```java
VCardRootPackage root = metadata.getRootPackageGeneric();
```

### Passo 3: Itera attraverso ogni scheda
Scorri ogni record di contatto nel contenitore vCard:

```java
for (VCardCard vCard : root.getVCardPackage().getCards()) {
    // Further processing...
}
```

### Passo 4: Applica i filtri
Usa i metodi di filtro integrati per mantenere solo i tag relativi al lavoro e i dettagli di contatto preferiti:

```java
VCardCard filtered = vCard.filterWorkTags().filterPreferred();
```

### Passo 5: Stampa i dati filtrati
Stampa i numeri di telefono e gli indirizzi email filtrati per verificare il risultato:

```java
printArray(filtered.getCommunicationRecordset().getTelephones());
printArray(filtered.getCommunicationRecordset().getEmails());

private static void printArray(String[] values) {
    if (values != null) {
        for (String value : values) {
            System.out.println(value);
        }
    }
}
```

### Esempio aggiuntivo: Ricarica il file vCard
Puoi ricaricare lo stesso file per eseguire altre operazioni, se necessario:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your_vcard_file.vcf")) {
    // Code continues...
}
```

## Applicazioni pratiche

Filtrare i tag di lavoro vCard è particolarmente utile per:

1. **Networking aziendale** – estrai solo i campi di contatto professionali da grandi rubriche.  
2. **Integrazione CRM** – alimenta dati puliti e focalizzati sul lavoro direttamente nei sistemi di gestione delle relazioni con i clienti.  
3. **Flussi di lavoro automatizzati** – alimenta script che richiedono solo numeri di telefono o email aziendali.

## Considerazioni sulle prestazioni

- **Gestione della memoria** – elabora file vCard di grandi dimensioni in streaming per evitare errori OOM.  
- **Profilazione** – utilizza profiler Java per individuare colli di bottiglia quando gestisci migliaia di contatti.  
- **Garbage Collection** – chiudi gli oggetti `Metadata` tempestivamente (come mostrato con try‑with‑resources) per liberare le risorse native.

## Domande frequenti

**D: Cos'è GroupDocs.Metadata?**  
R: GroupDocs.Metadata è una libreria Java che semplifica la lettura, la modifica e il filtraggio dei metadati in molti formati di file, inclusi i vCard.

**D: Posso usare questa libreria con Spring Boot?**  
R: Assolutamente. Basta aggiungere la dipendenza Maven e iniettare il servizio dove necessario.

**D: Come gestisce la libreria file vCard molto grandi?**  
R: Esegue lo streaming dei dati internamente, ma è consigliabile processare i record in batch per mantenere basso l'utilizzo della memoria.

**D: È necessaria una licenza per lo sviluppo?**  
R: Una prova gratuita è sufficiente per sviluppo e test; è richiesta una licenza commerciale per le distribuzioni in produzione.

**D: Dove posso trovare altri esempi?**  
R: Visita la [documentazione di GroupDocs](https://docs.groupdocs.com/metadata/java/) per ulteriori esempi di codice e riferimenti API.

---

**Ultimo aggiornamento:** 2026-04-04  
**Testato con:** GroupDocs.Metadata 24.12 per Java  
**Autore:** GroupDocs  

---