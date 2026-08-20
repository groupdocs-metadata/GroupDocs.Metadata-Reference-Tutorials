---
date: '2026-06-27'
description: Μάθετε πώς να εξάγετε μεταδεδομένα σε Excel χρησιμοποιώντας το GroupDocs.Metadata
  σε Java, να εξάγετε μεταδεδομένα από αρχεία και επίσης να δημιουργείτε XML ή CSV
  για αναφορές συμμόρφωσης.
keywords:
- export metadata excel java
- extract metadata files java
- groupdocs maven dependency
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to export metadata to Excel using GroupDocs.Metadata in Java,
    extract metadata from files, and also generate XML or CSV for compliance reporting.
  headline: Export Metadata Excel Java with GroupDocs.Metadata – A Step‑By‑Step Guide
  type: TechArticle
- description: Learn how to export metadata to Excel using GroupDocs.Metadata in Java,
    extract metadata from files, and also generate XML or CSV for compliance reporting.
  name: Export Metadata Excel Java with GroupDocs.Metadata – A Step‑By‑Step Guide
  steps:
  - name: '**Initialize Metadata Object:** Create a new `Metadata` instance using
      the path of your document.'
    text: '**Initialize Metadata Object:** Create a new `Metadata` instance using
      the path of your document.'
  - name: '**Check for Null:** Verify that the `RootMetadataPackage` is not null to
      avoid exceptions.'
    text: '**Check for Null:** Verify that the `RootMetadataPackage` is not null to
      avoid exceptions.'
  - name: '**Initialize ExportManager:** Set up the manager using the root metadata
      package.'
    text: '**Initialize ExportManager:** Set up the manager using the root metadata
      package.'
  - name: '**Export Metadata:** Use the `export` method to save metadata into an Excel
      file.'
    text: '**Export Metadata:** Use the `export` method to save metadata into an Excel
      file.'
  - name: '**Initialize ExportManager:** Similar to exporting to Excel, initialize
      the manager.'
    text: '**Initialize ExportManager:** Similar to exporting to Excel, initialize
      the manager.'
  - name: '**Export Metadata:** Call the `export` method to save metadata as an XML
      file.'
    text: '**Export Metadata:** Call the `export` method to save metadata as an XML
      file.'
  - name: '**Initialize ExportManager:** Set up the manager with your root package.'
    text: '**Initialize ExportManager:** Set up the manager with your root package.'
  - name: '**Export Metadata:** Use the `export` method to generate a CSV file.'
    text: '**Export Metadata:** Use the `export` method to generate a CSV file.'
  - name: '**Digital Asset Management:** Export metadata to Excel for fast categorization,
      tagging, and bulk updates of media libraries.'
    text: '**Digital Asset Management:** Export metadata to Excel for fast categorization,
      tagging, and bulk updates of media libraries.'
  - name: '**Regulatory Audits:** Generate XML reports that align with industry‑standard
      schemas, ensuring you meet GDPR, HIPAA, or SOX requirements.'
    text: '**Regulatory Audits:** Generate XML reports that align with industry‑standard
      schemas, ensuring you meet GDPR, HIPAA, or SOX requirements.'
  type: HowTo
- questions:
  - answer: It creates a structured spreadsheet that can be filtered, sorted, and
      shared with business users for reporting or compliance checks.
    question: What does “export metadata to excel” achieve?
  - answer: GroupDocs.Metadata also supports XML and CSV exports, giving you flexible
      options for data interchange.
    question: Which formats can I export besides Excel?
  - answer: Yes – a free 30‑day trial or a temporary license provides full feature
      access without restrictions.
    question: Do I need a license to try this out?
  - answer: JDK 8 or higher; the library is fully compatible with Java 11, 17, and
      newer LTS releases.
    question: What Java version is required?
  - answer: Absolutely – combine try‑with‑resources with batch or parallel processing
      to handle high‑volume scenarios efficiently.
    question: Can I process many documents at once?
  type: FAQPage
title: Εξαγωγή μεταδεδομένων σε Excel με Java χρησιμοποιώντας το GroupDocs.Metadata
  – Οδηγός βήμα‑βήμα
type: docs
url: /el/java/document-formats/export-document-metadata-groupdocs-metadata-java/
weight: 1
---

# Εξαγωγή Μεταδεδομένων Excel Java με GroupDocs.Metadata – Ένας Οδηγός Βήμα‑Βήμα

Σε σύγχρονες επιχειρηματικές εφαρμογές, **export metadata excel java** αποτελεί βασική δυνατότητα που σας επιτρέπει να μετατρέψετε κρυφές ιδιότητες εγγράφων σε ένα αναζητήσιμο φύλλο εργασίας. Είτε χρειάζεστε να ελέγξετε χιλιάδες συμβάσεις, να τροφοδοτήσετε μια αποθήκη δεδομένων, είτε απλώς να παρέχετε στους επιχειρηματικούς χρήστες μια καθαρή προβολή των χαρακτηριστικών των αρχείων, αυτός ο οδηγός σας δείχνει ακριβώς πώς να διαβάσετε τα μεταδεδομένα εγγράφων με το GroupDocs.Metadata και να τα εξάγετε σε Excel, XML ή CSV χρησιμοποιώντας Java.

## Γρήγορες Απαντήσεις
- **Τι επιτυγχάνει η “εξαγωγή μεταδεδομένων σε excel”;**  
  Δημιουργεί ένα δομημένο φύλλο εργασίας που μπορεί να φιλτραριστεί, να ταξινομηθεί και να μοιραστεί με τους επιχειρηματικούς χρήστες για αναφορές ή ελέγχους συμμόρφωσης.  
- **Ποιοι μορφές μπορώ να εξάγω εκτός από το Excel;**  
  Το GroupDocs.Metadata υποστηρίζει επίσης εξαγωγές σε XML και CSV, παρέχοντάς σας ευέλικτες επιλογές για ανταλλαγή δεδομένων.  
- **Χρειάζομαι άδεια για να δοκιμάσω αυτό;**  
  Ναι – μια δωρεάν δοκιμή 30 ημερών ή μια προσωρινή άδεια παρέχει πλήρη πρόσβαση σε όλες τις λειτουργίες χωρίς περιορισμούς.  
- **Ποια έκδοση της Java απαιτείται;**  
  JDK 8 ή νεότερη· η βιβλιοθήκη είναι πλήρως συμβατή με Java 11, 17 και νεότερες εκδόσεις LTS.  
- **Μπορώ να επεξεργαστώ πολλά έγγραφα ταυτόχρονα;**  
  Απόλυτα – συνδυάστε το try‑with‑resources με επεξεργασία παρτίδας ή παράλληλη επεξεργασία για να διαχειριστείτε αποδοτικά σενάρια υψηλού όγκου.

## Τι Θα Μάθετε

- Φορτώστε και αρχικοποιήστε τα μεταδεδομένα εγγράφου χρησιμοποιώντας το GroupDocs.Metadata  
- Εξάγετε τα μεταδεδομένα σε αρχεία Excel, XML και CSV  
- Πρακτικά παραδείγματα του **extract metadata from files** για αναφορές συμμόρφωσης  
- Συμβουλές επικεντρωμένες στην απόδοση για προγραμματιστές Java που διαχειρίζονται μεγάλα σύνολα εγγράφων  
- Πραγματικές περιπτώσεις χρήσης όπως η διαχείριση ψηφιακών περιουσιακών στοιχείων, τα ίχνη ελέγχου και η μετανάστευση δεδομένων  

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- **Java Development Kit (JDK):** Έκδοση 8 ή νεότερη.  
- **GroupDocs.Metadata Library:** Προσθέστε τη μέσω Maven ή κατεβάστε το JAR απευθείας.  
- **IDE:** IntelliJ IDEA, Eclipse, NetBeans ή οποιονδήποτε επεξεργαστή προτιμάτε.  

### Απαιτούμενες Βιβλιοθήκες και Εξαρτήσεις

Για απρόσκοπτη ενσωμάτωση με το GroupDocs.Metadata:

#### Ρύθμιση Maven

Προσθέστε την παρακάτω διαμόρφωση στο αρχείο `pom.xml` σας:

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

#### Άμεση Λήψη

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση απευθείας από [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Απόκτηση Άδειας

Για πλήρη αξιοποίηση του GroupDocs.Metadata:

- **Free Trial:** Πρόσβαση σε όλες τις λειτουργίες κατά τη διάρκεια μιας δοκιμής 30 ημερών.  
- **Temporary License:** Αποκτήστε μια προσωρινή άδεια για να δοκιμάσετε το προϊόν χωρίς περιορισμούς.  
- **Purchase License:** Για μακροπρόθεσμη χρήση και υποστήριξη επιχειρήσεων.  

## Ρύθμιση GroupDocs.Metadata για Java

Ξεκινήστε προσθέτοντας τις απαραίτητες εξαρτήσεις. Μόλις ρυθμιστεί, αρχικοποιήστε το έργο σας:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY";
        try (Metadata metadata = new Metadata(documentPath)) {
            // Basic initialization complete
        }
    }
}
```

## Οδηγός Υλοποίησης

Θα αναλύσουμε την υλοποίηση σε συγκεκριμένα χαρακτηριστικά για σαφήνεια.

### Φόρτωση και Αρχικοποίηση Μεταδεδομένων

**Επισκόπηση:**  
Το πρώτο βήμα είναι η φόρτωση των μεταδεδομένων του εγγράφου σας ώστε να μπορείτε να **read document metadata java** με τρόπο Java και να τα επεξεργαστείτε.

**Αγκύρωση ορισμού:**  
Η κλάση `Metadata` είναι το σημείο εισόδου του GroupDocs.Metadata που αντιπροσωπεύει το πακέτο μεταδεδομένων ενός μεμονωμένου αρχείου στη μνήμη.

**Βήματα:**  

1. **Initialize Metadata Object:** Δημιουργήστε ένα νέο αντικείμενο `Metadata` χρησιμοποιώντας τη διαδρομή του εγγράφου σας.

    ```java
    import com.groupdocs.metadata.Metadata;
    import com.groupdocs.metadata.core.RootMetadataPackage;

    String documentPath = "YOUR_DOCUMENT_DIRECTORY";
    try (Metadata metadata = new Metadata(documentPath)) {
        RootMetadataPackage root = metadata.getRootPackage();
        if (root != null) {
            // Proceed with further operations...
        }
    }
    ```

2. **Check for Null:** Επαληθεύστε ότι το `RootMetadataPackage` δεν είναι null για να αποφύγετε εξαιρέσεις.

### Εξαγωγή Μεταδεδομένων σε Excel

**Επισκόπηση:**  
Εξάγετε τα μεταδεδομένα του εγγράφου σας σε αρχείο Excel για λειτουργίες όπως ταξινόμηση, φιλτράρισμα και ανάλυση πινάκων pivot—ιδανικό για αναφορές **metadata export for compliance**.

**Αγκύρωση ορισμού:**  
`ExportManager` είναι η βοηθητική κλάση που οργανώνει τη μετατροπή ενός `RootMetadataPackage` σε διάφορες μορφές εξόδου όπως XLSX, XML ή CSV.  
RootMetadataPackage αντιπροσωπεύει τη ιεραρχική συλλογή ιδιοτήτων μεταδεδομένων που εξάγονται από ένα έγγραφο.  
ExportFormat είναι μια απαρίθμηση που ορίζει τους υποστηριζόμενους τύπους εξόδου όπως XLSX, XML και CSV.

**Πώς να Εξάγετε Μεταδεδομένα σε Excel με Java;**  
Φορτώστε το έγγραφο με `new Metadata("file.docx")`, αποκτήστε το root package, δημιουργήστε ένα `ExportManager` με αυτό το πακέτο και καλέστε τη μέθοδο `export` καθορίζοντας `ExportFormat.XLSX`. Αυτή η τριβήμα ροή γράφει ένα πλήρως μορφοποιημένο φύλλο εργασίας που διατηρεί τα ονόματα ιδιοτήτων, τις τιμές και τους τύπους δεδομένων, έτοιμο για άμεση ανάλυση.

**Βήματα:**  

1. **Initialize ExportManager:** Ρυθμίστε τον διαχειριστή χρησιμοποιώντας το root metadata package.

    ```java
    import com.groupdocs.metadata.export.ExportManager;
    import com.groupdocs.metadata.export.ExportFormat;

    String outputPathXls = "YOUR_OUTPUT_DIRECTORY/output.xls";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathXls, ExportFormat.Xls);
    }
    ```

2. **Export Metadata:** Χρησιμοποιήστε τη μέθοδο `export` για να αποθηκεύσετε τα μεταδεδομένα σε αρχείο Excel.

### Εξαγωγή Μεταδεδομένων σε XML

**Επισκόπηση:**  
Το XML είναι ιδανικό για ανταλλαγή δεδομένων· αυτό το βήμα δείχνει πώς να **export metadata to xml** για συστήματα που καταναλώνουν δομημένη σήμανση.

**Πώς να Εξάγετε Μεταδεδομένα σε XML με Java;**  
Δημιουργήστε ένα `ExportManager` με το root package, στη συνέχεια καλέστε `export` με `ExportFormat.XML`. Το παραγόμενο αρχείο XML περιέχει μια ιεραρχική αναπαράσταση όλων των τυπικών και προσαρμοσμένων ιδιοτήτων, καθιστώντας εύκολη την ενσωμάτωση με web services ή παλαιά συστήματα.

**Βήματα:**  

1. **Initialize ExportManager:** Παρόμοια με την εξαγωγή σε Excel, αρχικοποιήστε τον διαχειριστή.

    ```java
    String outputPathXml = "YOUR_OUTPUT_DIRECTORY/output.xml";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathXml, ExportFormat.Xml);
    }
    ```

2. **Export Metadata:** Καλέστε τη μέθοδο `export` για να αποθηκεύσετε τα μεταδεδομένα ως αρχείο XML.

### Εξαγωγή Μεταδεδομένων σε CSV

**Επισκόπηση:**  
Τα αρχεία CSV είναι ιδανικά για γρήγορη ανάλυση και μπορούν να εισαχθούν σε εργαλεία BI—αυτό δείχνει πώς να **export metadata to csv** για ελαφριές αναφορές.

**Πώς να Εξάγετε Μεταδεδομένα σε CSV με Java;**  
Δημιουργήστε ένα `ExportManager` με το root package, στη συνέχεια καλέστε `export` με `ExportFormat.CSV`. Η έξοδος CSV επίπεδωση τα μεταδεδομένα σε σειρές ζευγών “Ιδιότητα, Τιμή”, επιτρέποντας γρήγορη φόρτωση σε φύλλα εργασίας ή εργαλεία αγωγών δεδομένων.

**Βήματα:**  

1. **Initialize ExportManager:** Ρυθμίστε τον διαχειριστή με το root package σας.

    ```java
    String outputPathCsv = "YOUR_OUTPUT_DIRECTORY/output.csv";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathCsv, ExportFormat.Csv);
    }
    ```

2. **Export Metadata:** Χρησιμοποιήστε τη μέθοδο `export` για να δημιουργήσετε ένα αρχείο CSV.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Metadata για Εξαγωγή Μεταδεδομένων;

Το GroupDocs.Metadata υποστηρίζει **πάνω από 70 μορφές εισόδου και εξόδου**, συμπεριλαμβανομένων των DOCX, XLSX, PPTX, PDF και περισσότερων από 30 τύπων εικόνας. Μπορεί να επεξεργαστεί αρχεία έως **2 GB** χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη, προσφέροντας **μείωση 30 % στη χρήση CPU** σε σύγκριση με γενικούς αναλυτές. Αυτές οι ποσοτικοποιημένες δυνατότητες το καθιστούν αξιόπιστη επιλογή για μεγάλης κλίμακας έργα συμμόρφωσης.

## Πρακτικές Εφαρμογές

Ακολουθούν μερικά πραγματικά σενάρια όπου **metadata export for compliance** και **extract metadata from files** είναι ωφέλιμα:

1. **Digital Asset Management:** Εξάγετε μεταδεδομένα σε Excel για γρήγορη κατηγοριοποίηση, ετικετοθέτηση και μαζικές ενημερώσεις βιβλιοθηκών μέσων.  
2. **Regulatory Audits:** Δημιουργήστε αναφορές XML που ευθυγραμμίζονται με τα πρότυπα του κλάδου, διασφαλίζοντας τη συμμόρφωση με τις απαιτήσεις GDPR, HIPAA ή SOX.  
3. **Data Migration Projects:** Διατηρήστε τις ιδιότητες του αρχικού αρχείου κατά τη μεταφορά περιεχομένου μεταξύ συστημάτων διαχείρισης περιεχομένου, μειώνοντας τον κίνδυνο απώλειας δεδομένων.

## Παράγοντες Απόδοσης

Για βελτιστοποίηση της απόδοσης κατά τη χρήση του GroupDocs.Metadata σε Java:

- **Efficient Memory Management:** Χρησιμοποιήστε try‑with‑resources (όπως φαίνεται) για αυτόματο κλείσιμο πόρων και απελευθέρωση μνήμης.  
- **Batch Processing:** Επεξεργαστείτε μεγάλες συλλογές εγγράφων σε τμήματα αντί να φορτώνετε τα πάντα ταυτόχρονα.  
- **Parallel Processing:** Εκμεταλλευτείτε το `ExecutorService` της Java για ταυτόχρονη διαχείριση πολλαπλών αρχείων, επιτυγχάνοντας έως και 2× επιτάχυνση σε διακομιστές πολλαπλών πυρήνων.

## Συμπέρασμα

Αυτό το σεμινάριο εξερεύνησε πώς να χρησιμοποιήσετε τη βιβλιοθήκη GroupDocs.Metadata Java για **export metadata to excel**, καθώς και για XML και CSV, και πώς να **read document metadata java** με τρόπο για συμμόρφωση και ανάλυση. Ακολουθώντας αυτά τα βήματα, μπορείτε να διαχειρίζεστε και να αξιοποιείτε αποτελεσματικά τα μεταδεδομένα εγγράφων σε πραγματικές εφαρμογές, από ίχνη ελέγχου έως ενσωμάτωση σε αποθήκες δεδομένων.

**Επόμενα Βήματα:**  
- Πειραματιστείτε με διαφορετικούς τύπους αρχείων και εξερευνήστε πρόσθετες λειτουργίες όπως η διαχείριση προσαρμοσμένων ιδιοτήτων και η υποστήριξη κρυπτογράφησης.  
- Συμμετέχετε στο [GroupDocs forum](https://forum.groupdocs.com/c/metadata/) για να συνδεθείτε με άλλους χρήστες και να μοιραστείτε ιδέες.  

## Τμήμα Συχνών Ερωτήσεων

1. **Τι είναι το GroupDocs.Metadata;**  
   Το GroupDocs.Metadata είναι μια βιβλιοθήκη Java που παρέχει προγραμματιστική πρόσβαση στα μεταδεδομένα σε περισσότερα από 70 μορφές εγγράφων, επιτρέποντας λειτουργίες ανάγνωσης, εγγραφής και εξαγωγής.  

2. **Μπορώ να εξάγω μεταδεδομένα από οποιαδήποτε μορφή εγγράφου;**  
   Ναι, η βιβλιοθήκη υποστηρίζει ένα ευρύ φάσμα μορφών, συμπεριλαμβανομένων των Word, Excel, PowerPoint, PDF, εικόνων και πολλών τύπων αρχείων συμπίεσης.  

3. **Πώς να διαχειριστώ μεγάλους όγκους εγγράφων;**  
   Εφαρμόστε επεξεργασία παρτίδας ή παράλληλη εκτέλεση χρησιμοποιώντας τα εργαλεία ταυτόχρονης εκτέλεσης της Java· αυτό μειώνει το συνολικό χρόνο επεξεργασίας και διατηρεί τη χρήση μνήμης χαμηλή.  

4. **Υπάρχει τεκμηρίωση για προχωρημένα χαρακτηριστικά;**  
   Ναι, η λεπτομερής τεκμηρίωση API είναι διαθέσιμη στη διεύθυνση [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/).  

5. **Πού μπορώ να λάβω υποστήριξη αν αντιμετωπίσω προβλήματα;**  
   Επισκεφθείτε το [free support forum](https://forum.groupdocs.com/c/metadata/) για βοήθεια από ειδικούς του GroupDocs και την κοινότητα.  

## Συχνές Ερωτήσεις

**Q:** *Μπορώ να χρησιμοποιήσω αυτήν την προσέγγιση σε μια εφαρμογή Spring Boot;*  
**A:** Απολύτως. Προσθέστε την εξάρτηση Maven στο `pom.xml`, ενσωματώστε την υπηρεσία `Metadata` ως bean του Spring, και καλέστε τις μεθόδους εξαγωγής από οποιοδήποτε controller ή service layer.  

**Q:** *Τι γίνεται αν τα έγγραφά μου είναι προστατευμένα με κωδικό;*  
**A:** Περνάτε τον κωδικό στον κατασκευαστή `Metadata`; η βιβλιοθήκη θα αποκρυπτογραφήσει το αρχείο πριν εξάγει τα μεταδεδομένα, διατηρώντας τη συμμόρφωση ασφαλείας.  

**Q:** *Υπάρχει όριο στο μέγεθος ενός εγγράφου που μπορώ να επεξεργαστώ;*  
**A:** Η βιβλιοθήκη διαχειρίζεται μεγάλα αρχεία έως 2 GB, αλλά θα πρέπει να παρακολουθείτε τη χρήση heap της JVM και να εξετάζετε τη ροή μεγάλων δυαδικών αρχείων για να αποφύγετε σφάλματα OutOfMemory.  

**Q:** *Πώς να συμπεριλάβω προσαρμοσμένα πεδία μεταδεδομένων στην εξαγωγή;*  
**A:** Χρησιμοποιήστε το API `RootMetadataPackage` για να απαριθμήσετε τις προσαρμοσμένες ιδιότητες· προστίθενται αυτόματα στην έξοδο Excel, XML ή CSV χωρίς επιπλέον ρύθμιση.  

**Q:** *Λειτουργεί το GroupDocs.Metadata σε Linux containers;*  
**A:** Ναι, η βιβλιοθήκη είναι ανεξάρτητη από την πλατφόρμα και λειτουργεί ομαλά μέσα σε Docker containers σε Linux, Windows ή macOS hosts.  

## Πόροι

- **Τεκμηρίωση:** [GroupDocs.Metadata Java Docs](https://docs.groupdocs.com/metadata/java/)
- **Αναφορά API:** [Java API Reference](https://reference.groupdocs.com/metadata/java/)
- **Λήψη:** [Latest Release](https://releases.groupdocs.com/metadata/java/)
- **Αποθετήριο GitHub:** [GroupDocs.Metadata for Java on GitHub](https://github.com/groupdocs-metadata)

---

**Τελευταία Ενημέρωση:** 2026-06-27  
**Δοκιμάστηκε Με:** GroupDocs.Metadata 24.12  
**Συγγραφέας:** GroupDocs  

---

## Σχετικά Μαθήματα

- [Εξαγωγή Μεταδεδομένων σε CSV με Java χρησιμοποιώντας GroupDocs.Metadata: Πλήρης Οδηγός](/metadata/java/working-with-metadata/export-metadata-csv-groupdocs-metadata-java/)
- [Πρόσβαση στα Μεταδεδομένα Εγγράφου Word με GroupDocs σε Java: Αναλυτικός Οδηγός](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Πώς να Εξάγετε Προσαρμοσμένα Μεταδεδομένα από PDF χρησιμοποιώντας GroupDocs.Metadata σε Java: Αναλυτικός Οδηγός](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)