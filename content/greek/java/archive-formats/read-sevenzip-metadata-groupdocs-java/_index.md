---
date: '2026-06-22'
description: Μάθετε πώς να διαβάσετε τα μεταδεδομένα sevenzip java χρησιμοποιώντας
  το GroupDocs.Metadata για Java, συμπεριλαμβανομένου του πώς να λάβετε το compressed
  size java και άλλες archive properties.
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: Πώς να διαβάσετε τα μεταδεδομένα SevenZip Java με το GroupDocs.Metadata
type: docs
url: /el/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Πώς να Διαβάσετε Μεταδεδομένα SevenZip Java με το GroupDocs.Metadata

Αν χρειάζεστε **read sevenzip metadata java** από μια εφαρμογή Java, βρίσκεστε στο σωστό μέρος. Σε αυτό το σεμινάριο θα περάσουμε από τη χρήση του **GroupDocs.Metadata** για την εξαγωγή ονομάτων αρχείων, συμπιεσμένων μεγεθών, ασυμπίεστων μεγεθών, ημερομηνιών τροποποίησης και περισσότερων—ακριβώς των δεδομένων που χρειάζεστε για επικύρωση αντιγράφων ασφαλείας, συγχρονισμό ή βελτιστοποίηση αποθήκευσης.

## Εισαγωγή

Αντιμετωπίζετε δυσκολίες στην πρόσβαση και ανάγνωση των ιδιοτήτων μεταδεδομένων από αρχεία SevenZip χρησιμοποιώντας Java; Αυτό το σεμινάριο θα σας καθοδηγήσει στη διαδικασία χρήσης του **GroupDocs.Metadata**. Μια ισχυρή βιβλιοθήκη, απλοποιεί την εξαγωγή κρίσιμων πληροφοριών όπως ονόματα αρχείων, μεγέθη και ημερομηνίες τροποποίησης απευθείας από τα αρχεία σας.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη πρέπει να χρησιμοποιήσω;** GroupDocs.Metadata for Java – μια λύση single‑API για πάνω από 70 μορφές αρχείων και εγγράφων.  
- **Μπορώ να απαριθμήσω αρχεία μέσα σε ένα SevenZip αρχείο;** Ναι – καλέστε `getSevenZipPackage().getFiles()` μετά την αρχικοποίηση του αντικειμένου `Metadata`.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγή.  
- **Ποια έκδοση της Java υποστηρίζεται;** JDK 8 ή νεότερη (συμβατή με Java 17 LTS).  
- **Απαιτείται το Maven;** Δεν είναι υποχρεωτικό, αλλά το Maven διαχειρίζεται αυτόματα τις διαμεταβιβαστικές εξαρτήσεις.  

## Τι σημαίνει “πώς να διαβάσετε sevenzip” σε Java;

Η ανάγνωση μεταδεδομένων SevenZip σημαίνει το άνοιγμα του κοντέινερ `.7z`, η απαρίθμηση κάθε καταχώρησης και η λήψη ιδιοτήτων όπως **συμπιεσμένο μέγεθος**, **ασυμπίεστο μέγεθος**, **όνομα αρχείου** και **ημερομηνία τροποποίησης** χωρίς την εξαγωγή των πραγματικών αρχείων. Αυτή η διαδικασία σας παρέχει κατανόηση της σύνθεσης του αρχείου, επιτρέπει την επαλήθευση της ακεραιότητας του αντιγράφου ασφαλείας και σας δίνει τη δυνατότητα να λάβετε αποφάσεις για τη χωρητικότητα αποθήκευσης χωρίς το κόστος της πλήρους εξαγωγής.

## Διαβάστε μεταδεδομένα sevenzip java

Η χρήση της κύριας λέξης-κλειδί σε έναν αφιερωμένο τίτλο βοηθά τόσο τους αναγνώστες όσο και τις μηχανές αναζήτησης να κατανοήσουν το επίκεντρο αυτού του οδηγού. Παρακάτω θα εμβαθύνουμε στα ακριβή βήματα που χρειάζεστε για να **διαβάσετε μεταδεδομένα sevenzip java** αποδοτικά.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Metadata Java για την Εξαγωγή Μεταδεδομένων;

Το GroupDocs.Metadata διαβάζει μόνο τις πληροφορίες κεφαλίδας που απαιτούνται για την εξαγωγή μεταδεδομένων, έτσι η λειτουργία ολοκληρώνεται σε χιλιοστά του δευτερολέπτου ακόμη και για αρχεία πολλαπλών γιγαμπάιτ. Υποστηρίζει **70+** μορφές αρχείων και εγγράφων, επεξεργάζεται αρχεία έως **2 GB** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, και παρέχει ένα συνεπές API για όλους τους υποστηριζόμενους τύπους.

## Προαπαιτούμενα

Πριν εμβαθύνετε στο **GroupDocs.Metadata for Java**, βεβαιωθείτε ότι το περιβάλλον ανάπτυξής σας είναι σωστά ρυθμισμένο. Αυτό είναι που θα χρειαστείτε:

- **Java Development Kit (JDK):** Έκδοση 8 ή νεότερη.  
- **Maven:** Συνιστάται για τη διαχείριση εξαρτήσεων, αν και μπορείτε να προσθέσετε το JAR χειροκίνητα.  
- **Βασικές Γνώσεις Java:** Εξοικείωση με κλάσεις, μεθόδους και διαχείριση εξαιρέσεων.  

## Ρύθμιση του GroupDocs.Metadata για Java

Για να χρησιμοποιήσετε το GroupDocs.Metadata, συμπεριλάβετε το στο έργο σας μέσω Maven ή κατεβάζοντας τη βιβλιοθήκη απευθείας.

### Χρήση Maven

Προσθέστε την παρακάτω διαμόρφωση στο αρχείο `pom.xml`:

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

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από το [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Απόκτηση Άδειας

1. **Δωρεάν Δοκιμή:** Ξεκινήστε με μια δωρεάν δοκιμή για να δοκιμάσετε τις δυνατότητες του GroupDocs.Metadata.  
2. **Προσωρινή Άδεια:** Αιτηθείτε προσωρινή άδεια εάν χρειάζεστε εκτεταμένη πρόσβαση για σκοπούς αξιολόγησης.  
3. **Αγορά:** Για μακροπρόθεσμη χρήση, εξετάστε την αγορά πλήρους άδειας.  

Με την ολοκλήρωση της ρύθμισης, ας προχωρήσουμε στην υλοποίηση της λειτουργίας ανάγνωσης μεταδεδομένων.

## Οδηγός Υλοποίησης

### Πρόσβαση σε Μεταδεδομένα από Αρχεία SevenZip

Σε αυτήν την ενότητα, θα εξάγουμε και θα εκτυπώσουμε ιδιότητες μεταδεδομένων όπως ονόματα αρχείων και μεγέθη από ένα αρχείο SevenZip.

#### Βήμα 1: Αρχικοποίηση του Αντικειμένου Metadata

Η κλάση `Metadata` αντιπροσωπεύει το σημείο εισόδου για τη φόρτωση και αλληλεπίδραση με αρχεία αρχείων.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### Βήμα 2: Απόκτηση του Ριζικού Πακέτου

Η μέθοδος `getRootPackageGeneric()` επιστρέφει μια γενική προβολή του ριζικού πακέτου του αρχείου, επιτρέποντάς σας να εργάζεστε με τις καταχωρήσεις χωρίς να χρειάζεται κώδικας ειδικός για μορφή.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Γιατί να χρησιμοποιήσετε το `getRootPackageGeneric()`;** Παρέχει μια γενικευμένη προβολή του περιεχομένου του αρχείου, καθιστώντας πιο εύκολη την επανάληψη των καταχωρήσεων χωρίς να ανησυχείτε για συγκεκριμένες μορφές αρχείων.

#### Βήμα 3: Επανάληψη στις Καταχωρήσεις του Αρχείου

Η κλάση `SevenZipPackage` αντιπροσωπεύει το κοντέινερ SevenZip, και κάθε καταχώρηση εκτίθεται ως αντικείμενο `SevenZipFileInfo`. Η κλάση `SevenZipFileInfo` παρέχει άμεση πρόσβαση σε ιδιότητες όπως όνομα, συμπιεσμένο μέγεθος και ημερομηνία τροποποίησης.

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **Γιατί να εξάγετε αυτές τις ιδιότητες;** Η γνώση των μεγεθών των αρχείων βοηθά στη διαχείριση της αποθήκευσης, ενώ η ημερομηνία τροποποίησης μπορεί να είναι κρίσιμη για εργασίες συγχρονισμού. Η κλήση `getCompressedSize()` είναι ο τρόπος Java για **να λάβετε το συμπιεσμένο μέγεθος java** για κάθε καταχώρηση.

#### Βήμα 4: Καθαρισμός Πόρων

Καλώντας `close()` στο αντικείμενο `Metadata` απελευθερώνει τους εγγενείς πόρους και αποτρέπει διαρροές μνήμης σε υπηρεσίες μεγάλης διάρκειας.

```java
} finally {
    metadata.dispose();
}
```

- **Γιατί να απελευθερώσετε;** Η σωστή απελευθέρωση αντικειμένων βοηθά στην αποφυγή διαρροών μνήμης σε εφαρμογές μεγάλης διάρκειας.

## Πώς να Εξάγετε Μεταδεδομένα Αποδοτικά;

Φορτώστε το αρχείο SevenZip με ένα μόνο αντικείμενο `Metadata`, καλέστε `getRootPackageGeneric()` μία φορά και στη συνέχεια ρέξτε τις καταχωρήσεις χρησιμοποιώντας βρόχο `for‑each`. Αυτό το μοτίβο αποφεύγει επαναλαμβανόμενες I/O, μειώνει την πίεση του GC και ολοκληρώνεται σε χρόνο O(n) όπου *n* είναι ο αριθμός των καταχωρήσεων.

## Πρακτικές Εφαρμογές

Η κατανόηση του πώς να **διαβάσετε sevenzip metadata java** έχει πολλά πρακτικά οφέλη:

1. **Διαχείριση Αντιγράφων Ασφαλείας Δεδομένων:** Επαληθεύστε γρήγορα την ακεραιότητα και πληρότητα των αρχείων αντιγράφων ασφαλείας.  
2. **Εργαλεία Συγχρονισμού Αρχείων:** Χρησιμοποιήστε τις ημερομηνίες τροποποίησης για να αποφασίσετε ποια αρχεία χρειάζονται ενημέρωση.  
3. **Βελτιστοποίηση Αποθήκευσης:** Συγκρίνετε τα συμπιεσμένα και ασυμπίεστα μεγέθη για να προγραμματίσετε τη χωρητικότητα.  

Η ενσωμάτωση με άλλα συστήματα είναι δυνατή, επιτρέποντας την αυτοματοποιημένη εξαγωγή μεταδεδομένων ως μέρος μεγαλύτερων ροών εργασίας διαχείρισης δεδομένων.

## Σκέψεις για την Απόδοση

Κατά την εργασία με το GroupDocs.Metadata και μεγάλα αρχεία, λάβετε υπόψη τις παρακάτω συμβουλές:

- **Επεξεργασία σε Παρτίδες:** Επεξεργαστείτε τα αρχεία σε παρτίδες για να διαχειριστείτε αποτελεσματικά τη χρήση μνήμης.  
- **Αποτελεσματική Διαχείριση Εξαίρεσης:** Χρησιμοποιήστε try‑with‑resources για αυτόματη διαχείριση πόρων.  
- **Ασύγχρονη Επεξεργασία:** Εφαρμόστε ασύγχρονες τεχνικές για βαριά φορτία εργασίας.  

## Συνηθισμένα Προβλήματα και Λύσεις

| Issue | Solution |
|-------|----------|
| **`NullPointerException` κατά την πρόσβαση σε αρχείο** | Επαληθεύστε ότι η διαδρομή του αρχείου είναι σωστή και ότι το αρχείο δεν είναι κατεστραμμένο. |
| **Αιχμές μνήμης σε τεράστια αρχεία** | Ενεργοποιήστε την επεξεργασία σε παρτίδες ή αυξήστε το μέγεθος της μνήμης heap της JVM (`-Xmx`). |
| **Η άδεια δεν αναγνωρίζεται** | Βεβαιωθείτε ότι το αρχείο άδειας βρίσκεται στον κατάλογο εργασίας της εφαρμογής ή ορίστε το μέσω `License.setLicense(path)`. |

## Συχνές Ερωτήσεις

**Q:** Τι είναι το GroupDocs.Metadata;  
**A:** Είναι μια βιβλιοθήκη Java για τη διαχείριση μεταδεδομένων σε διάφορες μορφές αρχείων, συμπεριλαμβανομένων των αρχείων SevenZip.

**Q:** Μπορώ να χρησιμοποιήσω το GroupDocs.Metadata χωρίς Maven;  
**A:** Ναι, μπορείτε να κατεβάσετε το JAR από την επίσημη ιστοσελίδα και να το προσθέσετε στο classpath του έργου σας.

**Q:** Πώς να διαχειριστώ μεγάλα αρχεία αποδοτικά;  
**A:** Εφαρμόστε επεξεργασία σε παρτίδες ή χρησιμοποιήστε ασύγχρονα streams για να περιορίσετε την κατανάλωση μνήμης.

**Q:** Πού μπορώ να βρω πιο λεπτομερείς οδηγίες;  
**A:** Δείτε την [official documentation](https://docs.groupdocs.com/metadata/java/) για ολοκληρωμένες αναφορές API.

**Q:** Τι κάνω αν αντιμετωπίσω προβλήματα με τη βιβλιοθήκη;  
**A:** Ρωτήστε την κοινότητα στο [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/).

## Πόροι

- **Τεκμηρίωση:** Εξερευνήστε περισσότερα στο [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **Επίσημη τεκμηρίωση:** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **Αναφορά API:** Δείτε λεπτομερείς πληροφορίες API στο [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Λήψη:** Λάβετε την πιο πρόσφατη έκδοση από το [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **Αποθετήριο GitHub:** Πρόσβαση σε παραδείγματα κώδικα στο [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Δωρεάν Φόρουμ Υποστήριξης:** Συμμετέχετε σε συζητήσεις ή κάντε ερωτήσεις στο [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Τελευταία Ενημέρωση:** 2026-06-22  
**Δοκιμάστηκε Με:** GroupDocs.Metadata 24.12 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να Διαβάσετε Αρχεία TAR και να Εξάγετε Μεταδεδομένα με το GroupDocs.Metadata για Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)
- [Ενημέρωση Σχόλιου ZIP Java – Πώς να Ενημερώσετε Σχόλια Αρχείων ZIP Χρησιμοποιώντας το GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Εξαγωγή Μεταδεδομένων Βίντεο Java: Πώς να Διαβάσετε Αρχεία AVI με το GroupDocs.Metadata](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)