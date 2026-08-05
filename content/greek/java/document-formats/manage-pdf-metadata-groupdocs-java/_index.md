---
date: '2026-08-05'
description: Μάθετε πώς να ανιχνεύσετε την έκδοση PDF java και να ενημερώσετε τα μεταδεδομένα
  PDF χρησιμοποιώντας το GroupDocs.Metadata για Java. Περιλαμβάνει ανίχνευση έκδοσης,
  ανάγνωση ιδιοτήτων και επεξεργασία μεταδεδομένων.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Ανίχνευση έκδοσης PDF java και ενημέρωση μεταδεδομένων PDF με το GroupDocs.Metadata.
  Οδηγός Java βήμα‑βήμα δείχνει την ανίχνευση έκδοσης, την ανάγνωση ιδιοτήτων και
  την επεξεργασία μεταδεδομένων.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: Ανίχνευση έκδοσης PDF java και ενημέρωση μεταδεδομένων PDF
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: Ανίχνευση έκδοσης PDF java και ενημέρωση μεταδεδομένων PDF
type: docs
url: /el/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Ανίχνευση έκδοσης PDF java και ενημέρωση μεταδεδομένων PDF

Διαχείριση αρχείων PDF προγραμματιστικά συχνά σημαίνει ότι πρέπει να **ανιχνεύσετε την έκδοση PDF java** και **ενημερώσετε τα μεταδεδομένα PDF** — συγγραφέας, τίτλος, ημερομηνία δημιουργίας ή ακόμη και η ίδια η έκδοση PDF. Ασυνεπή μεταδεδομένα μπορούν να προκαλέσουν προβλήματα απόδοσης ή να δυσκολεύουν την εύρεση εγγράφων σε μεγάλο αποθετήριο. Αυτό το εκπαιδευτικό υλικό σας καθοδηγεί στην ανίχνευση της έκδοσης PDF και την ενημέρωση των μεταδεδομένων PDF χρησιμοποιώντας το **GroupDocs.Metadata** για Java, παρέχοντάς σας έναν αξιόπιστο τρόπο να διατηρείτε τα PDF σας τακτοποιημένα, αναζητήσιμα και συμβατά με οποιονδήποτε προβολέα.

## Γρήγορες απαντήσεις
- **Τι σημαίνει “ενημέρωση μεταδεδομένων PDF”;** Προσθήκη, τροποποίηση ή αφαίρεση πληροφοριών που αποθηκεύονται μέσα σε ένα αρχείο PDF.  
- **Ποια βιβλιοθήκη βοηθά σε αυτό στο Java;** GroupDocs.Metadata.  
- **Μπορώ επίσης να ανιχνεύσω την έκδοση PDF;** Ναι, το ίδιο API παρέχει ανίχνευση έκδοσης.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται πληρωμένη άδεια για παραγωγή.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.

## Τι είναι η ενημέρωση μεταδεδομένων PDF;

Η ενημέρωση μεταδεδομένων PDF σημαίνει προγραμματιστική ανάγνωση και εγγραφή των περιγραφικών πληροφοριών που ενσωματώνονται σε ένα αρχείο PDF—όπως συγγραφέας, τίτλος, θέμα και προσαρμοσμένες ιδιότητες. Τα σωστά μεταδεδομένα βελτιώνουν την δυνατότητα αναζήτησης, τη συμμόρφωση και τον έλεγχο εκδόσεων σε συστήματα διαχείρισης εγγράφων. Ακριβή μεταδεδομένα επίσης επιτρέπουν αυτοματοποιημένη ευρετηρίαση, αναφορές συμμόρφωσης και παρακολούθηση εκδόσεων σε συστήματα διαχείρισης εγγράφων.

## Γιατί να ανιχνεύσετε την έκδοση PDF στο Java;

Η ανίχνευση της έκδοσης PDF σας επιτρέπει να επαληθεύσετε ότι ένα αρχείο θα αποδοθεί σωστά στον προορισμένο προβολέα και ότι πληροί τις απαιτήσεις επεξεργασίας. Η γνώση του αν ένα PDF είναι έκδοσης 1.4, 1.7 ή νεότερης βοηθά στην επιβολή κανόνων συμβατότητας πριν από την αρχειοθέτηση, τη δημοσίευση ή τη μετατροπή του εγγράφου.

## Προαπαιτούμενα

- **Java Development Kit (JDK)** 8 ή νεότερο.  
- **Maven** για διαχείριση εξαρτήσεων (ή μπορείτε να κατεβάσετε το JAR απευθείας).  
- Βασική εξοικείωση με το Java file I/O.  

## Ρύθμιση GroupDocs.Metadata για Java

### Ρύθμιση Maven
Add the repository and dependency to your `pom.xml`:

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

### Άμεση λήψη
Εναλλακτικά, κατεβάστε το πιο πρόσφατο JAR από τη σελίδα επίσημων εκδόσεων: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Βήματα απόκτησης άδειας
- **Free trial** – ξεκινήστε τη δοκιμή χωρίς κόστος.  
- **Temporary license** – επεκτείνετε τη δοκιμή αν χρειαστεί.  
- **Purchase** – αποκτήστε πλήρη άδεια για χρήση σε παραγωγή.

## Βασική αρχικοποίηση και ρύθμιση

Η κλάση `Metadata` είναι το σημείο εισόδου για εργασία με αρχεία PDF στο GroupDocs.Metadata. Αντιπροσωπεύει ένα κοντέινερ που σας παρέχει πρόσβαση ανάγνωσης/εγγραφής στις ιδιότητες του εγγράφου, τις πληροφορίες έκδοσης και τα προσαρμοσμένα δεδομένα XMP.

Create a `Metadata` instance that points to your PDF file:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Τώρα είστε έτοιμοι να διαβάσετε τις ιδιότητες, να ανιχνεύσετε την έκδοση και να ενημερώσετε τα μεταδεδομένα.

## Πώς να ανιχνεύσετε την έκδοση PDF java

Φορτώστε το PDF σας με `new Metadata("sample.pdf")` και καλέστε `getRootPackage().getVersion()` — η μέθοδος επιστρέφει την ακριβή έκδοση PDF (π.χ., 1.4, 1.7) σε μία κλήση. Αυτή η άμεση απάντηση σας επιτρέπει να επικυρώσετε γρήγορα τη συμβατότητα πριν από οποιαδήποτε περαιτέρω επεξεργασία. Η συμβολοσειρά έκδοσης αντανακλά το επίπεδο προδιαγραφής PDF στο οποίο τηρείται το αρχείο, κάτι που είναι κρίσιμο για ελέγχους συμβατότητας.  
`getVersion()` επιστρέφει την έκδοση PDF ως συμβολοσειρά, π.χ., "1.4" ή "1.7".

### Οδηγός βήμα‑βήμα
1. **Open the PDF** – δημιουργήστε το αντικείμενο `Metadata` (δείτε την αρχικοποίηση παραπάνω).  
2. **Access the PDF‑specific root package** – καλέστε `metadata.getRootPackage()`.  
3. **Retrieve the version** – εκτελέστε `pdfRoot.getVersion()`· η επιστρεφόμενη συμβολοσειρά περιέχει τον αριθμό έκδοσης.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Pro tip:** Χρησιμοποιήστε την τιμή `version` για να επιβάλετε ελέγχους συμβατότητας πριν την επεξεργασία μιας δέσμης PDF.

#### Αντιμετώπιση προβλημάτων
- Επαληθεύστε τη διαδρομή του αρχείου· λανθασμένη διαδρομή προκαλεί `FileNotFoundException`.  
- Βεβαιωθείτε ότι η έκδοση του GroupDocs.Metadata ταιριάζει με το JDK σας (το παράδειγμα χρησιμοποιεί 24.12).

## Πώς να διαβάσετε τις ιδιότητες PDF στο Java

Το `DocumentInfo` παρέχει πρόσβαση στα τυπικά πεδία μεταδεδομένων PDF χωρίς τη φόρτωση ολόκληρου του εγγράφου. Η κλάση `DocumentInfo` παρέχει πρόσβαση σε τυπικές ιδιότητες PDF όπως συγγραφέας, τίτλος και ημερομηνία δημιουργίας. Είναι ένας ελαφρύς wrapper που διαβάζει τα μεταδεδομένα χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη.

Create a `DocumentInfo` instance from the opened `Metadata` object:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

Μπορείτε στη συνέχεια να καλέσετε getters όπως `getAuthor()`, `getTitle()` και `getCreationDate()` για να λάβετε τις τιμές.

## Πώς να ενημερώσετε τα μεταδεδομένα PDF στο Java

Φορτώστε το PDF (όπως παραπάνω), αποκτήστε το πακέτο `DocumentInfo`, τροποποιήστε τα επιθυμητά πεδία και αποθηκεύστε τις αλλαγές. Η λειτουργία αντικαθιστά το υπάρχον μπλοκ μεταδεδομένων διατηρώντας το υπόλοιπο του εγγράφου. Μετά την τροποποίηση των πεδίων, η κλήση `save()` γράφει τις αλλαγές πίσω στο αρχείο διατηρώντας τις ροές περιεχομένου.

Η κλάση `DocumentInfo` είναι το αντικείμενο του GroupDocs.Metadata για επεξεργασία ιδιοτήτων επιπέδου PDF όπως συγγραφέας, τίτλος, θέμα και προσαρμοσμένα πεδία XMP.

Update the metadata fields:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Σημείωση:** Οι κλήσεις setter ακολουθούν το ίδιο πρότυπο με τα getters που εμφανίστηκαν προηγουμένως, καθιστώντας το API διαισθητικό και συνεπές.

#### Συνηθισμένα προβλήματα
- Η προσπάθεια τροποποίησης μεταδεδομένων σε PDF που δεν διαθέτει την επιθυμητή ιδιότητα επιστρέφει `null`—πάντα ελέγξτε για `null` πριν ορίσετε νέα τιμή.  
- Τα μεγάλα PDF μπορεί να απαιτούν αυξημένο heap JVM· παρακολουθήστε τη χρήση μνήμης κατά τις ενημερώσεις δέσμης.

## Πρακτικές περιπτώσεις χρήσης
1. **Compliance audits** – Επαληθεύστε ότι όλα τα PDF πληρούν μια ελάχιστη έκδοση (π.χ., 1.7) πριν από τη νομική κατάθεση.  
2. **Automated archiving** – Ετικετοποιήστε τα PDF με συγγραφέα, τμήμα και ημερομηνία δημιουργίας για ευκολότερη ανάκτηση.  
3. **Document management integration** – Εμπλουτίστε τα PDF με προσαρμοσμένες ιδιότητες που μπορούν να ευρετηριαστούν από πλατφόρμες DMS.  
4. **Report generation** – Εισάγετε πληροφορίες έκδοσης σε αυτόματα παραγόμενες αναφορές.  
5. **Cross‑platform testing** – Ανιχνεύστε ασυμφωνίες έκδοσης που θα μπορούσαν να προκαλέσουν προβλήματα απόδοσης σε παλαιότερους προβολείς.

## Συμβουλές απόδοσης
- **Use try‑with‑resources** (όπως φαίνεται) για αυτόματο κλείσιμο των αντικειμένων `Metadata`.  
- **Batch process** πολλά αρχεία σε βρόχο για μείωση του κόστους.  
- **Monitor heap** για πολύ μεγάλα PDF· σκεφτείτε την επεξεργασία τους σε τμήματα αν φτάσετε τα όρια μνήμης.  
- **GroupDocs.Metadata supports 50+ input and output formats** και μπορεί να διαβάσει μεταδεδομένα από PDF πολλών εκατοντάδων σελίδων χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, παρέχοντας γρήγορη απόδοση σε τυπικό εξοπλισμό διακομιστή.

## Συχνές ερωτήσεις

**Q: Μπορώ να ενημερώσω τα μεταδεδομένα σε PDF προστατευμένα με κωδικό;**  
A: Ναι, αλλά πρέπει να παρέχετε τον κωδικό κατά τη δημιουργία του αντικειμένου `Metadata`.

**Q: Υποστηρίζει το GroupDocs.Metadata προσαρμοσμένες ιδιότητες XMP;**  
A: Απόλυτα. Μπορείτε να διαβάσετε και να γράψετε προσαρμοσμένα πεδία XMP μέσω του ίδιου API.

**Q: Είναι δυνατόν να αλλάξετε την ίδια την έκδοση PDF;**  
A: Η βιβλιοθήκη μπορεί να αναφέρει την έκδοση· η αλλαγή της απαιτεί αποθήκευση του εγγράφου με διαφορετικό προφίλ έκδοσης, το οποίο υποστηρίζεται μέσω πρόσθετων επιλογών αποθήκευσης.

**Q: Τι συμβαίνει αν το PDF δεν έχει υπάρχοντα μεταδεδομένα;**  
A: Οι getters θα επιστρέψουν `null`. Μπορείτε με ασφάλεια να καλέσετε τους setters για να δημιουργήσετε νέες εγγραφές μεταδεδομένων.

**Q: Υπάρχουν περιορισμοί άδειας για εμπορική χρήση;**  
A: Απαιτείται εμπορική άδεια για παραγωγικές εγκαταστάσεις· η δοκιμαστική έκδοση περιορίζεται σε σκοπούς αξιολόγησης.

---

**Τελευταία ενημέρωση:** 2026-08-05  
**Δοκιμή με:** GroupDocs.Metadata 24.12 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά μαθήματα

- [Αποτελεσματική ενημέρωση μεταδεδομένων PDF με το GroupDocs.Metadata σε Java για διαχείριση εγγράφων](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Αριστεία στη διαχείριση μεταδεδομένων: Ανίχνευση ιδιοτήτων εγγράφου & κατάστασης κρυπτογράφησης με το GroupDocs.Metadata για Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Δημιουργία προεπισκόπησης εγγράφου Java – Μαθήματα GroupDocs.Metadata](/metadata/java/document-formats/)