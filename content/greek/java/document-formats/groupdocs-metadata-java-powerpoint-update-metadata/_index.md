---
date: '2026-05-27'
description: Μάθετε πώς να ορίσετε το CreatedTime του pptx σε Java χρησιμοποιώντας
  την εξάρτηση GroupDocs Maven για την ενημέρωση των metadata του PowerPoint, συμπεριλαμβανομένου
  του πώς να αλλάξετε την ημερομηνία δημιουργίας του PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Ορισμός CreatedTime του PPTX σε Java με την εξάρτηση GroupDocs Maven
type: docs
url: /el/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Ορίστε το CreatedTime του PPTX σε Java με το GroupDocs.Metadata

Ακριβή μεταδεδομένα είναι απαραίτητα για τη συμμόρφωση και την ανακάλυψη σε σύγχρονα ροές εργασίας εγγράφων. Με το **GroupDocs.Metadata** μπορείτε προγραμματιστικά **να ορίσετε το CreatedTime του PPTX σε Java**, επιτρέποντάς σας **να αλλάξετε την ημερομηνία δημιουργίας του PPTX** μαζί με άλλες ενσωματωμένες ιδιότητες όπως ο συγγραφέας ή η εταιρεία. Αυτό το εκπαιδευτικό υλικό σας καθοδηγεί μέσω της ρύθμισης του Maven, της αρχικοποίησης του API, της ενημέρωσης των μεταδεδομένων και της αποθήκευσης της τροποποιημένης παρουσίασης—όλα με σαφή, έτοιμο για παραγωγή κώδικα.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη ενημερώνει τα μεταδεδομένα PowerPoint σε Java;** GroupDocs.Metadata μέσω της εξάρτησης Maven του GroupDocs.  
- **Μπορώ να ορίσω την ιδιότητα CreatedTime του PPTX;** Ναι—χρησιμοποιήστε `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Απαιτείται άδεια για παραγωγή;** Μια δοκιμαστική έκδοση λειτουργεί για αξιολόγηση· μια εμπορική άδεια είναι υποχρεωτική για παραγωγικές εγκαταστάσεις.  
- **Ποιο εργαλείο κατασκευής χρησιμοποιεί το παράδειγμα;** Maven (μπορείτε επίσης να κατεβάσετε το JAR χειροκίνητα).  
- **Υποστηρίζει το API τη Java 8 και νεότερες;** Απόλυτα—το GroupDocs.Metadata στοχεύει στη Java 8+.

## Τι είναι η εξάρτηση Maven του GroupDocs;
Η **εξάρτηση Maven του GroupDocs** είναι μια καταχώρηση αποθετηρίου συμβατή με Maven που φέρνει τη νεότερη βιβλιοθήκη GroupDocs.Metadata στο έργο Java σας. Απλοποιεί τη διαχείριση εξαρτήσεων επιλύοντας αυτόματα τις διαμεταβιβαστικές βιβλιοθήκες, εγγυάται ότι χρησιμοποιείτε πάντα την πιο πρόσφατη και ασφαλή έκδοση, και εξαλείφει την ανάγκη για χειροκίνητες λήψεις JAR ή παρακολούθηση εκδόσεων.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Metadata για την αλλαγή της ημερομηνίας δημιουργίας PPTX;
Το GroupDocs.Metadata επιτρέπει αυτοματοποιημένες, έτοιμες για παρτίδες ενημερώσεις των χρονικών σημάνσεων δημιουργίας PPTX, διασφαλίζοντας ότι κάθε παρουσίαση συμμορφώνεται με τις εταιρικές πολιτικές ή τις νομικές απαιτήσεις. Προγραμματιστικά ορίζοντας την ιδιότητα CreatedTime αποφεύγετε την χειροκίνητη επεξεργασία, μειώνετε τα ανθρώπινα λάθη και μπορείτε να ενσωματώσετε την αλλαγή σε CI/CD pipelines ή scripts μετεγκατάστασης για απρόσκοπτη διαχείριση εγγράφων.

## Προαπαιτούμενα
- Java 8 ή νεότερη εγκατεστημένη.  
- Ένα IDE όπως το IntelliJ IDEA ή το Eclipse.  
- Maven για διαχείριση εξαρτήσεων.  
- Πρόσβαση σε δοκιμαστική έκδοση ή αγορασμένη άδεια του GroupDocs.

## Πώς να ορίσετε το CreatedTime του PPTX σε Java;

Η κλάση `Metadata` αντιπροσωπεύει ένα έγγραφο και παρέχει πρόσβαση στις ιδιότητες των μεταδεδομένων του.

Φορτώστε το αρχείο PowerPoint με `new Metadata("presentation.pptx")`, ανακτήστε το ριζικό πακέτο, καλέστε `setCreatedTime` με το επιθυμητό `java.util.Date`, και τέλος εκτελέστε `save` για να γράψετε τις αλλαγές. Αυτή η ροή από την αρχή μέχρι το τέλος τροποποιεί την ημερομηνία δημιουργίας διατηρώντας όλο το περιεχόμενο των διαφανειών και άλλες ιδιότητες.

### Ρύθμιση Maven
Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση metadata στο `pom.xml` σας:

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

> **Συμβουλή:** Η διατήρηση του αριθμού έκδοσης ενημερωμένου εξασφαλίζει ότι επωφελείστε από τις τελευταίες διορθώσεις σφαλμάτων και βελτιώσεις απόδοσης.

### Άμεση Λήψη (αν προτιμάτε να μην χρησιμοποιήσετε Maven)

Εναλλακτικά, κατεβάστε το πιο πρόσφατο JAR από [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Απόκτηση Άδειας

Ξεκινήστε με μια δωρεάν δοκιμαστική έκδοση ή ζητήστε προσωρινή άδεια για να αξιολογήσετε το GroupDocs.Metadata. Για παραγωγική χρήση, αγοράστε άδεια μέσω του [επίσημου ιστότοπου του GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Βασική Αρχικοποίηση και Ρύθμιση

Μόλις η βιβλιοθήκη βρίσκεται στο classpath, μπορείτε να δημιουργήσετε μια παρουσία `Metadata` που δείχνει στο αρχείο PowerPoint σας:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Αυτός ο κώδικας ανοίγει την παρουσίαση σε ένα μπλοκ try‑with‑resources, εξασφαλίζοντας ότι ο χειριστής του αρχείου απελευθερώνεται αυτόματα.

## Οδηγός Βήμα‑βήμα για την Ενημέρωση Ενσωματωμένων Μεταδεδομένων

### Βήμα 1: Φόρτωση του Εγγράφου Παρουσίασης

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Η φόρτωση του αρχείου δημιουργεί μια σύνδεση που σας επιτρέπει να διαβάζετε ή να γράφετε μεταδεδομένα.

### Βήμα 2: Πρόσβαση στο Ριζικό Πακέτο της Παρουσίασης

Το αντικείμενο `root` παρέχει πρόσβαση στο βασικό πακέτο της παρουσίασης και στις ενσωματωμένες ιδιότητές του.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Το αντικείμενο `root` εκθέτει όλες τις ενσωματωμένες ιδιότητες του εγγράφου.

### Βήμα 3: Ενημέρωση Ενσωματωμένων Ιδιοτήτων Εγγράφου (συμπεριλαμβανομένης της ημερομηνίας δημιουργίας)

`setCreatedTime` εκχωρεί ένα νέο χρονικό σήμα δημιουργίας στο έγγραφο.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Εδώ δείχνουμε πώς να **ορίσετε το CreatedTime του PPTX** εκχωρώντας ένα νέο αντικείμενο `Date` στο `CreatedTime`. Αντικαταστήστε το `new Date()` με οποιοδήποτε συγκεκριμένο χρονικό σήμα χρειάζεστε.

### Βήμα 4: Αποθήκευση της Ενημερωμένης Παρουσίασης

`save` γράφει τα τροποποιημένα μεταδεδομένα πίσω σε ένα αρχείο.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Η κλήση `save` γράφει τα τροποποιημένα μεταδεδομένα σε ένα νέο αρχείο PowerPoint, αφήνοντας το αρχικό ανέπαφο.

## Συμβουλές Επίλυσης Προβλημάτων
- **Αρχείο Δεν Βρέθηκε:** Ελέγξτε ξανά τη διαδρομή εισόδου και τα δικαιώματα του αρχείου.  
- **Ασυμφωνία Έκδοσης:** Βεβαιωθείτε ότι η έκδοση `groupdocs-metadata` ταιριάζει με το περιβάλλον Java σας.  
- **Η Ιδιότητα Δεν Ενημερώνεται:** Επαληθεύστε ότι καλείτε το `setCreatedTime` (ή το σχετικό setter) πριν καλέσετε το `save`.

## Πρακτικές Εφαρμογές

1. **Εταιρική Επωνυμία:** Αυτόματη εισαγωγή του σωστού ονόματος εταιρείας και κατηγορίας σε όλα τα slide decks πριν τη διανομή.  
2. **Συστήματα Διαχείρισης Εγγράφων:** Εμπλουτίστε τα αρχεία PPTX με μεταδεδομένα αναζητήσιμα για ταχύτερη ανάκτηση.  
3. **Εκπαιδευτικούς Πόρους:** Διατηρήστε τις πληροφορίες συγγραφέα και προγράμματος ενημερωμένες σε όλα τα διαφάνειες.  
4. **Παρακολούθηση Συνεργασίας:** Καταγράψτε τα ονόματα των συντελεστών για διατήρηση λογοδοσίας.  
5. **Ενσωμάτωση CMS:** Συγχρονίστε τις αλλαγές μεταδεδομένων με την πλατφόρμα διαχείρισης περιεχομένου σε πραγματικό χρόνο.

## Σκέψεις Απόδοσης
- **Επεξεργασία Παρτίδας:** Επανάληψη πάνω σε λίστα αρχείων και επαναχρησιμοποίηση μιας μόνο παρουσίασης `Metadata` όπου είναι δυνατόν.  
- **Διαχείριση Μνήμης:** Πάντα χρησιμοποιείτε try‑with‑resources (όπως φαίνεται) για άμεση απελευθέρωση των εγγενών πόρων.  
- **Αποτελεσματικές Δομές Δεδομένων:** Αποθηκεύστε τις ενημερώσεις μεταδεδομένων σε έναν χάρτη πριν τις εφαρμόσετε για μείωση επαναλαμβανόμενων κλήσεων.

## Συχνές Ερωτήσεις

**Q:** Ποιος είναι ο κύριος σκοπός της εξάρτησης Maven του GroupDocs;  
A: Παρέχει έναν βολικό τρόπο για την ενσωμάτωση της πιο πρόσφατης βιβλιοθήκης GroupDocs.Metadata σε έργα Java βασισμένα σε Maven.

**Q:** Πώς μπορώ να ορίσω την ημερομηνία δημιουργίας του PPTX χωρίς να επηρεάσω άλλες ιδιότητες;  
A: Χρησιμοποιήστε `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` πριν καλέσετε `metadata.save()`.

**Q:** Χρειάζομαι άδεια για την εκτέλεση αυτού του κώδικα στην ανάπτυξη;  
A: Μια προσωρινή δοκιμαστική άδεια είναι επαρκής για ανάπτυξη και δοκιμές· πλήρης άδεια απαιτείται για παραγωγή.

**Q:** Μπορώ επίσης να ενημερώσω προσαρμοσμένα πεδία μεταδεδομένων;  
A: Ναι—το GroupDocs.Metadata υποστηρίζει τόσο ενσωματωμένες όσο και προσαρμοσμένες ιδιότητες μέσω του API του.

**Q:** Υπάρχει τρόπος να επαναφέρω τις αλλαγές αν κάνω λάθος;  
A: Διατηρήστε ένα αντίγραφο του αρχικού αρχείου ή διαβάστε τις υπάρχουσες τιμές ιδιοτήτων πριν τις αντικαταστήσετε, και στη συνέχεια επαναφέρετε αν χρειαστεί.

## Πόροι

- [Τεκμηρίωση](https://docs.groupdocs.com/metadata/java/)
- [Αναφορά API](https://apireference.groupdocs.com/metadata/java/)

---

**Τελευταία Ενημέρωση:** 2026-05-27  
**Δοκιμή Με:** GroupDocs.Metadata 24.12 for Java  
**Συγγραφέας:** GroupDocs  

## Σχετικά Μαθήματα

- [Ενημέρωση Προσαρμοσμένων Μεταδεδομένων σε PowerPoint Χρησιμοποιώντας το GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Πώς να Ενημερώσετε τα Μεταδεδομένα Εγγράφου Word Χρησιμοποιώντας το GroupDocs.Metadata Java: Ένας Πλήρης Οδηγός](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Αποτελεσματική Ενημέρωση Μεταδεδομένων PDF με το GroupDocs.Metadata σε Java για Διαχείριση Εγγράφων](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)