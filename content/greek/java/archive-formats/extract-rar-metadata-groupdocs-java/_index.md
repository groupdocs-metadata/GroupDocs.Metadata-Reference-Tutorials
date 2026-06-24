---
date: '2026-06-22'
description: Μάθετε πώς να λάβετε το συμπιεσμένο μέγεθος σε Java κατά την εξαγωγή
  μεταδεδομένων RAR χρησιμοποιώντας το GroupDocs.Metadata για Java. Οδηγός βήμα προς
  βήμα, παραδείγματα κώδικα και βέλτιστες πρακτικές.
keywords:
- get compressed size java
- groupdocs metadata java
- extract rar metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  headline: Get Compressed Size Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  name: Get Compressed Size Java with GroupDocs.Metadata
  steps:
  - name: Initialize the Metadata object
    text: Create a `Metadata` instance by providing the path to the RAR file. This
      object represents the archive in memory and gives you access to its internal
      structure.
  - name: Obtain the root package of the RAR archive
    text: Call `metadata.getRootPackage()` to retrieve the top‑level package that
      contains all entries. The returned `ArchivePackage` lets you enumerate files
      and folders inside the archive.
  - name: Retrieve total entry count
    text: Use `archivePackage.getEntries().size()` to know how many items are stored.
      Knowing the count helps you allocate progress‑tracking structures for batch
      jobs.
  - name: Iterate over each file and read its properties
    text: Loop through `archivePackage.getEntries()`. For every entry that represents
      a file (not a folder), call `entry.getCompressedSize()` to obtain its compressed
      size in bytes. You can also read `entry.getOriginalSize()` if you need the uncompressed
      size for ratio calculations. **Troubleshooting Tips** -
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java is a library that enables reading, updating,
      and managing metadata across more than 50 file formats, including RAR, ZIP,
      and 7z, without requiring file extraction.
    question: What is GroupDocs.Metadata for Java?
  - answer: Visit the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)
      to acquire a temporary or permanent license; a free trial is available for development.
    question: How do I obtain a license for full access?
  - answer: Yes, the same API supports ZIP, 7z, and several other archive formats,
      allowing a unified codebase for all archive metadata tasks.
    question: Can I use GroupDocs.Metadata with other archive types besides RAR?
  - answer: The main issues are memory consumption and file‑handle limits; mitigate
      them by processing entries one‑by‑one and closing the `Metadata` object promptly.
    question: What are common pitfalls when handling large RAR files?
  - answer: The [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/)
      provides assistance from both the vendor’s engineers and the community.
    question: Where can I get support if I encounter problems?
  type: FAQPage
title: Λάβετε το Συμπιεσμένο Μέγεθος Java με το GroupDocs.Metadata
type: docs
url: /el/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# Λήψη Συμπιεσμένου Μεγέθους Java με το GroupDocs.Metadata

Σε σύγχρονες εφαρμογές που επικεντρώνονται στα δεδομένα, **get compressed size java** είναι συχνή απαίτηση όταν χρειάζεται να ελέγξετε το μέγεθος αρχείων που αποθηκεύονται μέσα σε αρχεία RAR χωρίς να τα εξάγετε. Είτε δημιουργείτε ένα εργαλείο επαλήθευσης αντιγράφων ασφαλείας, ένα σύστημα διαχείρισης ψηφιακών περιουσιακών στοιχείων, είτε μια πύλη κοινής χρήσης αρχείων, η ανάγνωση αυτών των μεταδεδομένων εξοικονομεί χρόνο και πόρους συστήματος. Αυτός ο οδηγός σας καθοδηγεί στη χρήση του GroupDocs.Metadata για Java ώστε να ανακτήσετε το συμπιεσμένο μέγεθος κάθε καταχώρησης γρήγορα, με ασφάλεια και με ελάχιστο κώδικα.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη απαιτείται;** GroupDocs.Metadata for Java  
- **Μπορώ να ανακτήσω τα συμπιεσμένα μεγέθη;** Ναι – καλέστε `rarFile.getCompressedSize()` σε κάθε καταχώρηση  
- **Χρειάζεται άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή  
- **Ποια έκδοση Java υποστηρίζεται;** Java 8+ (οποιοδήποτε περιβάλλον συμβατό με Maven)  
- **Είναι δυνατή η επεξεργασία σε παρτίδες;** Απόλυτα – κάντε βρόχο σε φάκελο αρχείων RAR και επαναχρησιμοποιήστε τον ίδιο κώδικα  
- **Πώς να διαχειριστώ μεγάλα αρχεία RAR;** Επεξεργαστείτε τις καταχωρήσεις μία‑μια και κλείστε το αντικείμενο μεταδεδομένων όταν τελειώσετε  

## Τι είναι το “get compressed size java” και γιατί είναι σημαντικό;
**Get compressed size java** διαβάζει το μέγεθος ενός αρχείου όπως αποθηκεύεται μέσα σε ένα κοντέινερ RAR. Αυτή η τιμή σας δείχνει πόσο χώρο καταλαμβάνει το αρχείο μετά τη συμπίεση, επιτρέποντάς σας να επαληθεύσετε τους λόγους συμπίεσης, να εκτιμήσετε χρόνους μεταφοράς και να παρουσιάσετε τόσο τα αρχικά όσο και τα συμπιεσμένα μεγέθη σε αναφορές απογραφής.

## Πώς να λάβετε το compressed size java από αρχεία RAR;
Φορτώστε το αρχείο RAR με το GroupDocs.Metadata, επαναλάβετε τις καταχωρήσεις του και καλέστε τη μέθοδο `getCompressedSize()` σε κάθε αρχείο. Αυτή η προσέγγιση διαβάζει μόνο την κεφαλίδα του αρχείου, οπότε δεν γίνεται εξαγωγή ή πλήρης φόρτωση του αρχείου, διατηρώντας τη χρήση μνήμης κάτω από 5 MB ακόμη και για αρχεία πολλών εκατοντάδων megabytes.

### Βήμα 1: Αρχικοποίηση του αντικειμένου Metadata
Δημιουργήστε ένα στιγμιότυπο `Metadata` παρέχοντας τη διαδρομή προς το αρχείο RAR. Αυτό το αντικείμενο αντιπροσωπεύει το αρχείο σε μνήμη και σας δίνει πρόσβαση στην εσωτερική του δομή.

### Βήμα 2: Απόκτηση του ριζικού πακέτου του αρχείου RAR
Καλέστε `metadata.getRootPackage()` για να λάβετε το πακέτο κορυφαίου επιπέδου που περιέχει όλες τις καταχωρήσεις. Το επιστρεφόμενο `ArchivePackage` σας επιτρέπει να απαριθμήσετε αρχεία και φακέλους μέσα στο αρχείο.

### Βήμα 3: Ανάκτηση του συνολικού αριθμού καταχωρήσεων
Χρησιμοποιήστε `archivePackage.getEntries().size()` για να μάθετε πόσα αντικείμενα είναι αποθηκευμένα. Η γνώση του αριθμού βοηθά στην κατανομή δομών παρακολούθησης προόδου για εργασίες σε παρτίδες.

### Βήμα 4: Επανάληψη σε κάθε αρχείο και ανάγνωση των ιδιοτήτων του
Κάντε βρόχο μέσω `archivePackage.getEntries()`. Για κάθε καταχώρηση που αντιπροσωπεύει αρχείο (όχι φάκελο), καλέστε `entry.getCompressedSize()` για να λάβετε το συμπιεσμένο μέγεθος σε bytes. Μπορείτε επίσης να διαβάσετε `entry.getOriginalSize()` εάν χρειάζεστε το ασυμπίεστο μέγεθος για υπολογισμούς λόγου.

**Συμβουλές Επίλυσης Προβλημάτων**  
- Βεβαιωθείτε ότι το `rarFilePath` δείχνει σε υπάρχον αρχείο RAR.  
- Εξασφαλίστε ότι η εφαρμογή έχει δικαιώματα ανάγνωσης για το αρχείο.  
- Εάν αντιμετωπίσετε σφάλματα “unsupported format”, επιβεβαιώστε ότι η έκδοση RAR είναι συμβατή με το GroupDocs.Metadata (υποστηρίζει RAR 4 και RAR 5).  

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Metadata για Αρχεία RAR;
Το GroupDocs.Metadata παρέχει ένα υψηλού επιπέδου API που διαβάζει τις κεφαλίδες των αρχείων χωρίς εξαγωγή, προσφέροντας γρήγορη πρόσβαση σε ιδιότητες όπως το συμπιεσμένο μέγεθος, το αρχικό μέγεθος και τις χρονικές σήμανσεις. Λειτουργεί με μορφές RAR 4 και RAR 5, διαχειρίζεται μεγάλα αρχεία αποδοτικά και αφαιρεί τις λεπτομέρειες μορφής ώστε οι προγραμματιστές να γράφουν ενιαίο κώδικα για διαφορετικούς τύπους αρχείων.

## Συνηθισμένες Περιπτώσεις Χρήσης
1. **Συστήματα Διαχείρισης Δεδομένων** – αυτόματη καταγραφή του περιεχομένου των αρχείων για αναζητήσιμες απογραφές.  
2. **Διαχείριση Ψηφιακών Περιουσιακών Στοιχείων** – εμπλουτισμός βιβλιοθηκών πολυμέσων με λεπτομέρειες επιπέδου αρχείου όπως το συμπιεσμένο μέγεθος.  
3. **Επαλήθευση Αντιγράφων Ασφαλείας** – σύγκριση των αποθηκευμένων συμπιεσμένων μεγεθών με τις αναμενόμενες τιμές για εντοπισμό φθορών.  
4. **Πλατφόρμες Κοινής Χρήσης Αρχείων** – εμφάνιση περιλήψεων αρχείων χωρίς πλήρη εξαγωγή, βελτιώνοντας την εμπειρία χρήστη.  

## Σκέψεις για την Απόδοση
- **Πρόσβαση μόνο στις απαιτούμενες ιδιότητες** – αποφύγετε την κλήση βαριών μεθόδων εάν χρειάζεστε μόνο ονόματα αρχείων και μεγέθη.  
- **Απόρριψη αντικειμένων μεταδεδομένων** – καλέστε `metadata.close()` μετά την επεξεργασία για απελευθέρωση εγγενών πόρων.  
- **Επεξεργασία σε παρτίδες** – επεξεργαστείτε πολλαπλά αρχεία RAR σε βρόχο, επαναχρησιμοποιώντας το ίδιο JVM για μείωση του χρόνου εκκίνησης.  

## Συχνές Ερωτήσεις

**Q: Τι είναι το GroupDocs.Metadata για Java;**  
A: Το GroupDocs.Metadata για Java είναι μια βιβλιοθήκη που επιτρέπει την ανάγνωση, ενημέρωση και διαχείριση μεταδεδομένων σε περισσότερα από 50 μορφές αρχείων, συμπεριλαμβανομένων των RAR, ZIP και 7z, χωρίς να απαιτείται εξαγωγή αρχείων.

**Q: Πώς μπορώ να αποκτήσω άδεια για πλήρη πρόσβαση;**  
A: Επισκεφθείτε τη [σελίδα αγοράς του GroupDocs](https://purchase.groupdocs.com/temporary-license/) για να αποκτήσετε προσωρινή ή μόνιμη άδεια· υπάρχει δωρεάν δοκιμή για ανάπτυξη.

**Q: Μπορώ να χρησιμοποιήσω το GroupDocs.Metadata με άλλους τύπους αρχείων εκτός του RAR;**  
A: Ναι, το ίδιο API υποστηρίζει ZIP, 7z και αρκετές άλλες μορφές αρχείων, επιτρέποντας έναν ενοποιημένο κώδικα για όλες τις εργασίες μεταδεδομένων αρχείων.

**Q: Ποια είναι τα κοινά προβλήματα όταν διαχειρίζεστε μεγάλα αρχεία RAR;**  
A: Τα κύρια ζητήματα είναι η κατανάλωση μνήμης και τα όρια χειριστών αρχείων· αντιμετωπίστε τα επεξεργαζόμενοι τις καταχωρήσεις μία‑μία και κλείνοντας άμεσα το αντικείμενο `Metadata`.

**Q: Πού μπορώ να λάβω υποστήριξη εάν αντιμετωπίσω προβλήματα;**  
A: Το [δωρεάν φόρουμ υποστήριξης του GroupDocs](https://forum.groupdocs.com/c/metadata/) παρέχει βοήθεια από τους μηχανικούς του προμηθευτή και την κοινότητα.

## Πόροι
- **Τεκμηρίωση**: [Τεκμηρίωση GroupDocs Metadata Java](https://docs.groupdocs.com/metadata/java/)  
- **Αναφορά API**: [Αναφορά API GroupDocs](https://reference.groupdocs.com/metadata/java/)  
- **Λήψη**: [Λήψη Τελευταίας Έκδοσης](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [Κώδικας Πηγής στο GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Δωρεάν Υποστήριξη**: [Φόρουμ GroupDocs](https://forum.groupdocs.com/c/metadata/)  
- **Εκδόσεις**: [Εκδόσεις GroupDocs.Metadata για Java](https://releases.groupdocs.com/metadata/java/)  
- **Πλήρης Τεκμηρίωση**: [πλήρης τεκμηρίωση](https://docs.groupdocs.com/metadata/java/)

## Συμπέρασμα
Τώρα γνωρίζετε **πώς να χρησιμοποιήσετε το GroupDocs.Metadata** για την εξαγωγή πλήρων μεταδεδομένων από αρχεία RAR, συμπεριλαμβανομένου του **get compressed size java** για κάθε καταχώρηση. Ενσωματώστε αυτό το μοτίβο στα έργα σας για να ενισχύσετε τις δυνατότητες διαχείρισης δεδομένων, να βελτιώσετε την επαλήθευση αντιγράφων ασφαλείας και να εμπλουτίσετε τις εμπειρίες αναζήτησης αρχείων χωρίς το βάρος της πλήρους εξαγωγής.

### Επόμενα Βήματα
Εξερευνήστε πρόσθετες δυνατότητες όπως η ενημέρωση σχολίων καταχώρησης ή η εξαγωγή πληροφοριών ελέγχου ακεραιότητας στην επίσημη τεκμηρίωση, και σκεφτείτε τον συνδυασμό αυτής της εξαγωγής μεταδεδομένων με την υπάρχουσα διαδικασία ευρετηρίου σας για ένα πλήρως αναζητήσιμο αποθετήριο αρχείων.

**Τελευταία Ενημέρωση:** 2026-06-22  
**Δοκιμή Με:** GroupDocs.Metadata 24.12 for Java  
**Συγγραφέας:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata object
        Metadata metadata = new Metadata("path/to/your/document");
        System.out.println("Metadata initialized successfully.");
    }
}
```

```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

```java
// Iterate over each file within the RAR archive
for (RarFile rarFile : root.getRarPackage().getFiles()) {
    // Print file name, compressed size, modification date time, and uncompressed size
    System.out.println("File Name: " + rarFile.getName());
    System.out.println("Compressed Size: " + rarFile.getCompressedSize());
    System.out.println("Modification Date Time: " + rarFile.getModificationDateTime());
    System.out.println("Uncompressed Size: " + rarFile.getUncompressedSize());
}
```

## Σχετικά Μαθήματα

- [Εξαγωγή σχολίων zip java χρησιμοποιώντας το GroupDocs.Metadata – Οδηγός](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)
- [Ενημέρωση Σχολίου ZIP Java – Πώς να Ενημερώσετε Σχόλια Αρχείων ZIP Χρησιμοποιώντας το GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Πώς να Διαβάσετε Αρχεία TAR και να Εξάγετε Μεταδεδομένα με το GroupDocs.Metadata για Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)