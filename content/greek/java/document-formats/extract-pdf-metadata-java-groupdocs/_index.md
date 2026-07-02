---
date: '2026-07-02'
description: Μάθετε πώς να διαβάζετε μεταδεδομένα PDF Java χρησιμοποιώντας το GroupDocs.Metadata.
  Ανακτήστε την ημερομηνία δημιουργίας του PDF, τον συγγραφέα, τις λέξεις-κλειδιά
  και άλλες ιδιότητες αποδοτικά.
keywords:
- read pdf metadata java
- retrieve pdf creation date
- java extract pdf properties
schemas:
- author: GroupDocs
  dateModified: '2026-07-02'
  description: Learn how to read PDF metadata Java using GroupDocs.Metadata. Retrieve
    PDF creation date, author, keywords and other properties efficiently.
  headline: Read PDF metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read PDF metadata Java using GroupDocs.Metadata. Retrieve
    PDF creation date, author, keywords and other properties efficiently.
  name: Read PDF metadata Java with GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems:** Auto‑categorize files by author or subject.'
    text: '**Document Management Systems:** Auto‑categorize files by author or subject.'
  - name: '**Archiving Solutions:** Organize archives using the creation date extracted
      from PDFs.'
    text: '**Archiving Solutions:** Organize archives using the creation date extracted
      from PDFs.'
  - name: '**Content Analysis & SEO:** Pull keywords from PDFs to enrich search‑engine
      metadata.'
    text: '**Content Analysis & SEO:** Pull keywords from PDFs to enrich search‑engine
      metadata.'
  type: HowTo
- questions:
  - answer: Iterate over a collection of file paths and apply the same extraction
      logic inside the loop.
    question: How do I handle multiple PDF files in one run?
  - answer: Yes—GroupDocs.Metadata provides methods to enumerate and read custom dictionary
      entries.
    question: Can I extract custom metadata fields that are not part of the standard
      set?
  - answer: Load the document with the appropriate password using the `Metadata` constructor
      overload that accepts credentials.
    question: What if my PDF is password‑protected?
  - answer: Absolutely. The API allows you to set new values and then call `metadata.save()`
      to persist changes.
    question: Is it possible to modify metadata after extraction?
  - answer: Yes, it works seamlessly in servlet containers, Spring Boot, or any Java‑based
      server environment.
    question: Can this library be used in a Java web application?
  type: FAQPage
title: Ανάγνωση μεταδεδομένων PDF Java με GroupDocs.Metadata
type: docs
url: /el/java/document-formats/extract-pdf-metadata-java-groupdocs/
weight: 1
---

# Ανάγνωση μεταδεδομένων PDF Java με το GroupDocs.Metadata

Η εξαγωγή μεταδεδομένων PDF σε Java μπορεί να φαίνεται δύσκολη, ειδικά όταν πρέπει να αντλήσετε ιδιότητες όπως Author, Created Date ή Keywords από δεκάδες αρχεία. Σε αυτό το tutorial θα μάθετε **πώς να διαβάζετε μεταδεδομένα PDF Java** γρήγορα και αξιόπιστα χρησιμοποιώντας τη βιβλιοθήκη GroupDocs.Metadata. Θα περάσουμε από τη ρύθμιση του Maven, την αρχικοποίηση της βιβλιοθήκης και τον ακριβή κώδικα που χρειάζεστε για την ανάκτηση κάθε ιδιότητας — συμπεριλαμβανομένου του πώς να **ανακτήσετε την ημερομηνία δημιουργίας PDF** — ώστε να μπορείτε να αυτοματοποιήσετε εργασίες διαχείρισης εγγράφων με σιγουριά.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη απλοποιεί την εξαγωγή μεταδεδομένων PDF σε Java;** GroupDocs.Metadata for Java.  
- **Μπορώ να προσθέσω τη βιβλιοθήκη μέσω Maven;** Ναι – δείτε το απόσπασμα Maven παρακάτω.  
- **Ποια ιδιότητα μου δίνει την χρονική σήμανση δημιουργίας του εγγράφου;** `getCreatedDate()` ανακτά την ημερομηνία δημιουργίας του PDF.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται μόνιμη άδεια για παραγωγή.  
- **Είναι η λύση κατάλληλη για μεγάλα PDF;** Ναι, χρησιμοποιήστε try‑with‑resources και επεξεργασία ροής για να διατηρήσετε τη χρήση μνήμης χαμηλή.

## Τι είναι η ανάγνωση μεταδεδομένων PDF Java;
Η πράξη του **reading PDF metadata Java** σημαίνει την προγραμματιστική πρόσβαση στις ενσωματωμένες πληροφορίες που αποθηκεύονται μέσα σε ένα αρχείο PDF — όπως author, title, creation date και προσαρμοσμένες ετικέτες — ώστε να μπορείτε να ευρετηριάσετε, να αναζητήσετε ή να κατηγοριοποιήσετε έγγραφα χωρίς να τα ανοίξετε χειροκίνητα. Αυτά τα μεταδεδομένα μπορούν να εξαχθούν χωρίς απόδοση του εγγράφου, καθιστώντας τα ιδανικά για μαζική επεξεργασία και ευρετηρίαση αναζήτησης.

## Γιατί να επιλέξετε το GroupDocs.Metadata για την εξαγωγή μεταδεδομένων PDF σε Java;
Το GroupDocs.Metadata υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί PDF έως **2 GB** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Το type‑safe API του εξαλείφει την ανάγκη για χαμηλού επιπέδου ανάλυση, παρέχοντας **μείωση 30 % του χρόνου ανάπτυξης** σε σύγκριση με τις χειροκίνητες βιβλιοθήκες διαχείρισης PDF.

## Προαπαιτούμενα
- **Java Development Kit (JDK) 8** ή νεότερο.  
- **Maven** για διαχείριση εξαρτήσεων (συνιστάται έντονα).  
- Ένα IDE όπως **IntelliJ IDEA** ή **Eclipse**.  
- Βασική εξοικείωση με τον προγραμματισμό Java.

## Ρύθμιση του GroupDocs.Metadata για Java

### Εξαγωγή μεταδεδομένων με Maven
Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση metadata στο `pom.xml`:

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

### Άμεση Λήψη
Αν προτιμάτε να μην χρησιμοποιήσετε Maven, μπορείτε να αποκτήσετε το πιο πρόσφατο JAR από τη σελίδα επίσημων εκδόσεων: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Βήματα Απόκτησης Άδειας
- **Free Trial:** Κατεβάστε μια δοκιμαστική έκδοση για να εξερευνήσετε όλες τις δυνατότητες.  
- **Temporary License:** Ενεργοποιήστε ένα προσωρινό κλειδί για πλήρη λειτουργικότητα κατά τη διάρκεια της αξιολόγησης.  
- **Purchase:** Αποκτήστε μόνιμη άδεια για χρήση σε παραγωγή.

### Βασική Αρχικοποίηση και Ρύθμιση
Η κλάση `Metadata` είναι το κύριο αντικείμενο που χρησιμοποιείται για το άνοιγμα ενός PDF και την ερώτηση των μεταδεδομένων του. Μonce η βιβλιοθήκη είναι διαθέσιμη στο classpath, αρχικοποιήστε την στον κώδικα Java:

```java
import com.groupdocs.metadata.Metadata;

public class PdfMetadataExtractor {
    public static void main(String[] args) {
        // Initialize metadata object with a PDF file path
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Proceed with extraction steps below
        }
    }
}
```

## Πώς να διαβάσετε μεταδεδομένα PDF Java με το GroupDocs.Metadata;
Φορτώστε το PDF με την κλάση `Metadata` και καλέστε τα κατάλληλα getters—`getAuthor()`, `getCreatedDate()`, `getKeywords()`, κ.λπ.—για να ανακτήσετε κάθε πληροφορία σε λίγες μόνο γραμμές κώδικα. Αυτή η προσέγγιση λειτουργεί για μεμονωμένα αρχεία καθώς και για σενάρια επεξεργασίας δέσμης, διατηρώντας τη χρήση μνήμης χαμηλή αξιοποιώντας το construct try‑with‑resources της Java.

Η κλάση `Metadata` είναι το κύριο αντικείμενο του GroupDocs.Metadata για το άνοιγμα και την αλληλεπίδραση με αρχεία PDF. Μετά τη δημιουργία μιας παρουσίας, μπορείτε να ερωτήσετε το root package για πρόσβαση σε τυπικές και προσαρμοσμένες καταχωρήσεις μεταδεδομένων.

## Ποιες είναι οι βασικές ιδιότητες μεταδεδομένων PDF που μπορείτε να εξάγετε;
Μπορείτε να εξάγετε τα πιο κοινά πεδία μεταδεδομένων PDF—author, creation date, subject, producer και keywords—χρησιμοποιώντας ειδικές μεθόδους getter. Κάθε κλήση επιστρέφει την ακριβή τιμή που είναι αποθηκευμένη στο εσωτερικό λεξικό του PDF, έτοιμη για ευρετηρίαση ή αναφορά. Αυτές οι τιμές μπορούν στη συνέχεια να αποθηκευτούν σε βάση δεδομένων ή να χρησιμοποιηθούν για τη δημιουργία αναφορών διακυβέρνησης εγγράφων.

## Οδηγός Υλοποίησης

### Εξαγωγή Ιδιοτήτων Μεταδεδομένων

#### Επισκόπηση
Εδώ θα εξάγουμε τα πιο κοινά πεδία μεταδεδομένων PDF—author, creation date, subject, producer και keywords—χρησιμοποιώντας το API του GroupDocs.Metadata.

#### Υλοποίηση Βήμα‑βήμα

**1. Ανοίξτε το PDF Έγγραφο**

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

// Define your PDF file path
String filePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";

try (Metadata metadata = new Metadata(filePath)) {
    // Access the root package and proceed with extraction steps below
}
```

**2. Πρόσβαση στο Root Package**

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

Η μέθοδος `getRootPackageGeneric()` σας δίνει πρόσβαση στις βασικές ιδιότητες του PDF.

**3. Εξαγωγή και Εκτύπωση Ιδιοτήτων Μεταδεδομένων**

- **Συγγραφέας:**  
  ```java
  System.out.println("Author: " + root.getDocumentProperties().getAuthor());
  ```

- **Created Date (ανακτήστε την ημερομηνία δημιουργίας PDF):**  
  ```java
  System.out.println("Created Date: " + root.getDocumentProperties().getCreatedDate());
  ```

- **Θέμα:**  
  ```java
  System.out.println("Subject: " + root.getDocumentProperties().getSubject());
  ```

- **Παραγωγός:**  
  ```java
  System.out.println("Producer: " + root.getDocumentProperties().getProducer());
  ```

- **Λέξεις-κλειδιά:**  
  ```java
  System.out.println("Keywords: " + root.getDocumentProperties().getKeywords());
  ```

### Συμβουλές Επίλυσης Προβλημάτων
- Επαληθεύστε ότι η διαδρομή του αρχείου PDF είναι σωστή και το αρχείο είναι προσβάσιμο.  
- Βεβαιωθείτε ότι το Maven έχει επιλύσει την εξάρτηση `groupdocs-metadata` χωρίς συγκρούσεις εκδόσεων.  
- Εάν αντιμετωπίσετε `LicenseException`, επιβεβαιώστε ότι έχει φορτωθεί μια έγκυρη δοκιμαστική ή μόνιμη άδεια πριν χρησιμοποιήσετε το API.

## Πρακτικές Εφαρμογές
1. **Document Management Systems:** Αυτόματη κατηγοριοποίηση αρχείων κατά συγγραφέα ή θέμα.  
2. **Archiving Solutions:** Οργάνωση αρχείων χρησιμοποιώντας την ημερομηνία δημιουργίας που εξάγεται από PDF.  
3. **Content Analysis & SEO:** Ανάκτηση λέξεων-κλειδιά από PDF για εμπλουτισμό μεταδεδομένων μηχανών αναζήτησης.

## Σκέψεις Απόδοσης
- Χρησιμοποιήστε **try‑with‑resources** (όπως φαίνεται) για να εγγυηθείτε ότι το αντικείμενο `Metadata` κλείνει άμεσα.  
- Για τεράστια PDF, επεξεργαστείτε τα σε ροές ή εργασίες δέσμης για να διατηρήσετε τη χρήση μνήμης χαμηλή.  
- Κάντε profiling την εφαρμογή Java με εργαλεία όπως το VisualVM για να εντοπίσετε τυχόν bottlenecks.

## Συχνές Ερωτήσεις

**Q: Πώς να διαχειριστώ πολλαπλά αρχεία PDF σε μία εκτέλεση;**  
A: Επανάληψη πάνω σε μια συλλογή διαδρομών αρχείων και εφαρμογή της ίδιας λογικής εξαγωγής μέσα στον βρόχο.

**Q: Μπορώ να εξάγω προσαρμοσμένα πεδία μεταδεδομένων που δεν ανήκουν στο τυπικό σύνολο;**  
A: Ναι—το GroupDocs.Metadata παρέχει μεθόδους για απαρίθμηση και ανάγνωση προσαρμοσμένων εγγραφών λεξικού.

**Q: Τι γίνεται αν το PDF είναι προστατευμένο με κωδικό;**  
A: Φορτώστε το έγγραφο με τον κατάλληλο κωδικό χρησιμοποιώντας την υπερφόρτωση του κατασκευαστή `Metadata` που δέχεται διαπιστευτήρια.

**Q: Είναι δυνατόν να τροποποιήσετε τα μεταδεδομένα μετά την εξαγωγή;**  
A: Απόλυτα. Το API επιτρέπει τον ορισμό νέων τιμών και στη συνέχεια την κλήση του `metadata.save()` για την αποθήκευση των αλλαγών.

**Q: Μπορεί αυτή η βιβλιοθήκη να χρησιμοποιηθεί σε εφαρμογή web Java;**  
A: Ναι, λειτουργεί απρόσκοπτα σε servlet containers, Spring Boot ή οποιοδήποτε περιβάλλον διακομιστή βασισμένο σε Java.

## Πόροι
- [Τεκμηρίωση](https://docs.groupdocs.com/metadata/java/)  
- [Αναφορά API](https://reference.groupdocs.com/metadata/java/)  
- [Λήψη](https://releases.groupdocs.com/metadata/java/)  
- [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- [Δωρεάν Υποστήριξη](https://forum.groupdocs.com/c/metadata/)  
- [φόρουμ δωρεάν υποστήριξης](https://forum.groupdocs.com/c/metadata/)  
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία Ενημέρωση:** 2026-07-02  
**Δοκιμάστηκε Με:** GroupDocs.Metadata 24.12 for Java  
**Συγγραφέας:** GroupDocs  

## Σχετικά Μαθήματα
- [Αποτελεσματική Ενημέρωση Μεταδεδομένων PDF με το GroupDocs.Metadata σε Java για Διαχείριση Εγγράφων](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Πώς να Εξάγετε Δεδομένα PDF σε Java με το GroupDocs.Metadata](/metadata/java/document-formats/groupdocs-metadata-java-pdf-inspection/)
- [Εξαγωγή Ιδιοτήτων Word Java με το GroupDocs.Metadata](/metadata/java/document-formats/groupdocs-metadata-java-word-properties-extraction/)