---
date: '2026-06-17'
description: Μάθετε πώς να αλλάξετε τον χρόνο δημιουργίας διαγράμματος και να αυτοματοποιήσετε
  την ενημέρωση των metadata για αρχεία διαγράμματος χρησιμοποιώντας το GroupDocs.Metadata
  σε Java.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Αλλαγή χρόνου δημιουργίας διαγράμματος στα Metadata με το GroupDocs Java
type: docs
url: /el/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Αλλαγή χρόνου δημιουργίας διαγράμματος στα μεταδεδομένα με GroupDocs Java

Σε αυτό το βήμα‑βήμα tutorial θα ανακαλύψετε πώς να **αλλάξετε τον χρόνο δημιουργίας διαγράμματος** και να ενημερώσετε άλλες ενσωματωμένες ιδιότητες των αρχείων διαγράμματος χρησιμοποιώντας τη βιβλιοθήκη GroupDocs.Metadata για Java. Η αυτοματοποίηση αυτών των αλλαγών εξοικονομεί ώρες χειροκίνητης επεξεργασίας, εγγυάται συνεπή χρονικές σήμανση σε όλο το αποθετήριο σας και κάνει τα διαγράμματά σας άμεσα αναζητήσιμα σε οποιοδήποτε σύστημα διαχείρισης εγγράφων.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο κύριος στόχος;** Αλλαγή χρόνου δημιουργίας διαγράμματος και άλλων μεταδεδομένων σε αρχεία διαγράμματος.  
- **Ποια βιβλιοθήκη πρέπει να χρησιμοποιήσω;** GroupDocs.Metadata for Java.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή είναι αρκετή για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Μπορώ να επεξεργαστώ μαζικά πολλά διαγράμματα;** Ναι—τυλίξτε την ίδια λογική σε βρόχο ή σε παράλληλο stream.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.

## Τι είναι η «αλλαγή χρόνου δημιουργίας διαγράμματος» στα μεταδεδομένα διαγράμματος;
Η αλλαγή του χρόνου δημιουργίας αντικαθιστά το αρχικό χρονικό στίγμα που αποθηκεύεται μέσα σε ένα αρχείο διαγράμματος (όπως VDX ή VSDX) με μια νέα τιμή ημερομηνίας‑ώρας. Αυτό σας επιτρέπει να ευθυγραμμίσετε τα μεταδεδομένα του αρχείου με την πραγματική ημερομηνία επεξεργασίας ή αρχειοθέτησης αντί για το αρχικό στίγμα του δημιουργού, κάτι που είναι απαραίτητο για τα αρχεία ελέγχου και ακριβή αποτελέσματα αναζήτησης.

## Γιατί να αυτοματοποιήσετε την ενημέρωση μεταδεδομένων για διαγράμματα;
Η αυτοματοποίηση των μεταδεδομένων διασφαλίζει ότι κάθε διάγραμμα ακολουθεί τα ίδια πρότυπα ονομασίας, κατηγοριοποίησης και χρονικής σήμανσης χωρίς ανθρώπινα σφάλματα. Επίσης, επιταχύνει τις μαζικές μεταναστεύσεις, μειώνει τον κίνδυνο συμμόρφωσης και βελτιώνει την ανακάλυψη σε εταιρικές πλατφόρμες DMS—εξοικονομώντας έως και 70 % του χειροκίνητου κόστους σε μεγάλης κλίμακας έργα.

## Προαπαιτούμενα
- **Java Development Kit (JDK) 8+** εγκατεστημένο στο μηχάνημά σας.  
- **IDE** όπως IntelliJ IDEA ή Eclipse.  
- **Maven** (ή χειροκίνητη διαχείριση JAR) για διαχείριση εξαρτήσεων.  
- Βασική εξοικείωση με κλάσεις Java, μεθόδους και διαχείριση εξαιρέσεων.

### Απαιτούμενες Βιβλιοθήκες και Εξαρτήσεις
Προσθέστε το παρακάτω αποθετήριο και την εξάρτηση στο αρχείο `pom.xml` εάν χρησιμοποιείτε Maven:

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
Αν προτιμάτε να κατεβάσετε απευθείας, επισκεφθείτε [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) για να λάβετε την πιο πρόσφατη έκδοση.

### Ρύθμιση Περιβάλλοντος
- JDK 8 ή νεότερο.  
- IntelliJ IDEA, Eclipse ή οποιοδήποτε IDE συμβατό με Java.  

### Προαπαιτούμενες Γνώσεις
Η κατανόηση της σύνταξης Java και των βασικών λειτουργιών αρχείων I/O θα κάνει το tutorial πιο ομαλό, αλλά τα βήματα εξηγούνται με απλή γλώσσα.

## Ρύθμιση GroupDocs.Metadata για Java
### Οδηγίες Εγκατάστασης
**Χρήστες Maven:** Το παραπάνω απόσπασμα προσθέτει το αποθετήριο και το απαιτούμενο JAR αυτόματα.  
**Χρήστες Άμεσης Λήψης:** Αφού κατεβάσετε το JAR από [GroupDocs](https://releases.groupdocs.com/metadata/java/), προσθέστε το στην κλάση‑διαδρομή του έργου σας.

### Απόκτηση Άδειας
- **Δωρεάν Δοκιμή:** Εξερευνήστε τη βιβλιοθήκη χωρίς κόστος.  
- **Προσωρινή Άδεια:** Αποκτήστε προσωρινή άδεια για εκτεταμένες δοκιμές [εδώ](https://purchase.groupdocs.com/temporary-license/).  
- **Αγορά:** Αποκτήστε πλήρη άδεια για περιβάλλοντα παραγωγής.

### Βασική Αρχικοποίηση
`Metadata` είναι η κεντρική κλάση που αντιπροσωπεύει το κοντέινερ μεταδεδομένων ενός εγγράφου και παρέχει πρόσβαση ανάγνωσης/εγγραφής σε όλες τις ενσωματωμένες ιδιότητες. Για να αρχίσετε να χρησιμοποιείτε το GroupDocs.Metadata, εισάγετε την κλάση και ανοίξτε ένα αρχείο διαγράμματος:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Με τη βιβλιοθήκη αρχικοποιημένη, μπορείτε τώρα να τροποποιήσετε οποιαδήποτε ενσωματωμένη ιδιότητα, συμπεριλαμβανομένου του χρόνου δημιουργίας.

## Οδηγός Υλοποίησης
### Πώς να αλλάξετε τον χρόνο δημιουργίας σε αρχεία διαγράμματος
Σε αυτήν την ενότητα θα περάσουμε από κάθε βήμα που απαιτείται για να **αλλάξετε τον χρόνο δημιουργίας διαγράμματος** και να ενημερώσετε άλλες κοινές ιδιότητες όπως συγγραφέας, εταιρεία και κατηγορία. Η διαδικασία περιλαμβάνει τη φόρτωση του διαγράμματος με το Metadata API, την πρόσβαση στο ριζικό πακέτο, τον ορισμό των επιθυμητών πεδίων και, τέλος, την αποθήκευση των αλλαγών σε νέο αρχείο, διασφαλίζοντας ότι το αρχικό παραμένει ανέπαφο.

#### Βήμα 1: Φόρτωση του Εγγράφου Διαγράμματος
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Επεξήγηση:* Ο κατασκευαστής `Metadata` λαμβάνει τη διαδρομή του αρχείου διαγράμματος. Το μπλοκ try‑with‑resources εξασφαλίζει ότι το αρχείο κλείνει σωστά μετά τη λειτουργία.

#### Βήμα 2: Πρόσβαση στο Ριζικό Πακέτο
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Επεξήγηση:* Το ριζικό πακέτο σας δίνει άμεση πρόσβαση σε όλα τα ενσωματωμένα πεδία μεταδεδομένων του διαγράμματος.

#### Βήμα 3: Ορισμός Ιδιότητας Δημιουργού
```java
root.getDocumentProperties().setCreator("test author");
```  
*Επεξήγηση:* Ορίζει ένα νέο όνομα συγγραφέα. Αντικαταστήστε το `"test author"` με τον πραγματικό δημιουργό.

#### Βήμα 4: Αλλαγή Χρόνου Δημιουργίας
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Επεξήγηση:* Αυτή η γραμμή **αλλάζει τον χρόνο δημιουργίας** στην τρέχουσα ημερομηνία και ώρα του συστήματος. Μπορείτε επίσης να περάσετε μια συγκεκριμένη实例 `Date` εάν χρειάζεστε προσαρμοσμένο στίγμα.

#### Βήμα 5: Ορισμός Πληροφοριών Εταιρείας
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Επεξήγηση:* Αποθηκεύει το όνομα της εταιρείας που συνδέεται με το διάγραμμα—χρήσιμο για εταιρική παρακολούθηση.

#### Βήμα 6: Ορισμός Κατηγορίας Εγγράφου
```java
root.getDocumentProperties().setCategory("test category");
```  
*Επεξήγηση:* Κατηγοριοποιεί το αρχείο, βοηθώντας σας να **ενημερώσετε την κατηγορία διαγράμματος** σταθερά σε όλο το αποθετήριο.

#### Βήμα 7: Προσθήκη Λέξεων-Κλειδιών
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Επεξήγηση:* Οι λέξεις‑κλειδιά βελτιώνουν την αναζητησιμότητα· μπορείτε να καταγράψετε όρους σχετικούς με το περιεχόμενο του διαγράμματος.

#### Βήμα 8: Αποθήκευση Αλλαγών
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Επεξήγηση:* Εφαρμόζει όλες τις τροποποιήσεις σε νέο αρχείο, αφήνοντας το αρχικό ανέπαφο.

### Συνηθισμένα Προβλήματα & Αντιμετώπιση
- **Αρχείο Δεν Βρέθηκε:** Επαληθεύστε τη διαδρομή εισόδου και βεβαιωθείτε ότι η επέκταση αρχείου ταιριάζει με την πραγματική μορφή.  
- **Πρόσβαση Απορρίφθηκε:** Ελέγξτε τα δικαιώματα ανάγνωσης/εγγραφής για τους καταλόγους εισόδου και εξόδου.  
- **Μη Έγκυρη Μορφή Ημερομηνίας:** Χρησιμοποιήστε αντικείμενα `java.util.Date` ή `java.time` συμβατά με το API.  

## Πρακτικές Εφαρμογές
1. **Αυτοματοποίηση Αρχειοθέτησης Εγγράφων** – Κατά τη μεταφορά παλαιών διαγραμμάτων σε αρχείο, αυτόματα **αλλάξτε τον χρόνο δημιουργίας του διαγράμματος** στην ημερομηνία αρχειοθέτησης και ορίστε μια ενιαία κατηγορία.  
2. **Ενσωμάτωση Ελέγχου Εκδόσεων** – Διατηρήστε τα χρονικά σήματα συγχρονισμένα με τις δεσμεύσεις Git ενημερώνοντας τον χρόνο δημιουργίας σε κάθε έκδοση.  
3. **Τυποποίηση Εταιρικού DMS** – Επιβάλλετε μια πολιτική σε όλη την εταιρεία για συγγραφέα, εταιρεία και λέξεις‑κλειδιά σε όλα τα διαγράμματα.

## Σκέψεις Απόδοσης
- **Μαζική Επεξεργασία:** Τυλίξτε τα παραπάνω βήματα μέσα σε βρόχο για να επεξεργαστείτε δεκάδες αρχεία σε μία εκτέλεση.  
- **Διαχείριση Μνήμης:** Απελευθερώστε άμεσα κάθε αντικείμενο `Metadata` (το μπλοκ try‑with‑resources το κάνει αυτό αυτόματα).  
- **Ασύγχρονη Εκτέλεση:** Για μεγάλα παρτίδες, εξετάστε το `CompletableFuture` για να τρέξετε ενημερώσεις παράλληλα χωρίς να μπλοκάρετε το κύριο νήμα.  
- **Ποσοτική Δυνατότητα:** Το GroupDocs.Metadata υποστηρίζει πάνω από 30 μορφές διαγράμματος και μπορεί να επεξεργαστεί αρχεία έως 500 MB χωρίς να φορτώσει ολόκληρο το έγγραφο στη μνήμη, παρέχοντας ενημερώσεις κάτω από 200 ms ανά αρχείο σε τυπικό εξοπλισμό διακομιστή.

## Συμπέρασμα
Τώρα γνωρίζετε πώς να **αλλάξετε τον χρόνο δημιουργίας διαγράμματος** και να ενημερώσετε άλλες ενσωματωμένες ιδιότητες μεταδεδομένων για έγγραφα διαγράμματος χρησιμοποιώντας το GroupDocs.Metadata σε Java. Με την αυτοματοποίηση αυτών των βημάτων, μπορείτε να διατηρήσετε συνεπή, αναζητήσιμη και συμμορφωμένη τεκμηρίωση σε όλη την οργάνωσή σας.

**Επόμενα Βήματα**
- Πειραματιστείτε με άλλες μορφές αρχείων που υποστηρίζονται από το GroupDocs.Metadata (PDF, DOCX, κ.λπ.).  
- Ενσωματώστε τον κώδικα σε μια γραμμή CI/CD για να επιβάλλετε πρότυπα μεταδεδομένων σε κάθε build.  

Έτοιμοι να το δοκιμάσετε; Μεταβείτε στα [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) και ξεκινήστε να υλοποιείτε τη δική σας αυτοματοποίηση μεταδεδομένων σήμερα.

---

**Τελευταία Ενημέρωση:** 2026-06-17  
**Δοκιμή Με:** GroupDocs.Metadata 24.12  
**Συγγραφέας:** GroupDocs  

## Συχνές Ερωτήσεις

**Q: Μπορώ να χρησιμοποιήσω αυτήν την προσέγγιση με άλλες μορφές διαγράμματος όπως VSDX;**  
A: Ναι, το ίδιο API λειτουργεί για όλες τις μορφές διαγράμματος που υποστηρίζονται από το GroupDocs.Metadata.

**Q: Χρειάζομαι άδεια για εκδόσεις ανάπτυξης;**  
A: Μια δωρεάν δοκιμή είναι επαρκής για ανάπτυξη και δοκιμές· απαιτείται πλήρης άδεια για παραγωγικές εγκαταστάσεις.

**Q: Πώς μπορώ να ενημερώσω πολλαπλές ιδιότητες σε μία κλήση;**  
A: Ορίστε κάθε ιδιότητα στο αντικείμενο `DocumentProperties` πριν καλέσετε `metadata.save(...)`; η βιβλιοθήκη τις γράφει όλες ταυτόχρονα.

**Q: Είναι ασφαλές να αντικαταστήσω το αρχικό αρχείο;**  
A: Συνιστάται η αποθήκευση σε νέο αρχείο (όπως φαίνεται) και η αντικατάσταση του αρχικού μόνο μετά την επιβεβαίωση ότι η ενημέρωση ολοκληρώθηκε με επιτυχία.

**Q: Τι γίνεται αν χρειαστεί να ορίσω προσαρμοσμένη ημερομηνία δημιουργίας αντί για την τρέχουσα ώρα;**  
A: Δημιουργήστε ένα `java.util.Date` (ή αντικείμενο `java.time`) με το επιθυμητό στίγμα και περάστε το στη μέθοδο `setTimeCreated`.

## Σχετικά Μαθήματα

- [How to Update Diagram Metadata Java with GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [How to Update DXF Author Metadata with GroupDocs.Metadata for Java – A Complete Guide](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Automate Java Metadata Updates by Date Using GroupDocs.Metadata for Efficient File Management](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)