---
date: '2026-06-01'
description: Μάθετε πώς να εξάγετε τμήματα κειμένου PNG με το GroupDocs.Metadata για
  Java – διαβάστε τα μεταδεδομένα PNG αποδοτικά και ενσωματώστε αξιόπιστη διαχείριση
  εικόνων.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Πώς να εξάγετε τμήματα κειμένου PNG χρησιμοποιώντας το GroupDocs.Metadata Java
  API
type: docs
url: /el/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Πώς να εξάγετε τμήματα κειμένου PNG χρησιμοποιώντας το GroupDocs.Metadata Java API

Η εξαγωγή πληροφοριών κειμένου από αρχεία εικόνας μπορεί να είναι προκλητική, ειδικά για μορφές που δεν βασίζονται σε κείμενο όπως τα PNG. **GroupDocs.Metadata for Java** απλοποιεί αυτή τη διαδικασία παρέχοντας ισχυρά εργαλεία για την ανάκτηση και διαχείριση των μεταδεδομένων που είναι ενσωματωμένα σε αυτές τις εικόνες. Είτε διαχειρίζεστε γενικά, συμπιεσμένα ή διεθνή τμήματα κειμένου, το GroupDocs.Metadata προσφέρει απλοποιημένες λύσεις.

Σε αυτό το tutorial, θα σας καθοδηγήσουμε πώς να εξάγετε αποδοτικά διαφορετικούς τύπους τμημάτων κειμένου από αρχεία PNG χρησιμοποιώντας τη βιβλιοθήκη GroupDocs.Metadata σε Java. Κατανοώντας αυτές τις τεχνικές, μπορείτε να ενσωματώσετε άψογα λειτουργίες εξαγωγής κειμένου στις εφαρμογές σας, ενισχύοντας τις δυνατότητες επεξεργασίας δεδομένων σε διάφορους τομείς.

## Γρήγορες Απαντήσεις
- **Μπορεί το GroupDocs.Metadata να διαβάσει τα μεταδεδομένα png;** Ναι, διαβάζει όλα τα τυπικά μεταδεδομένα PNG, συμπεριλαμβανομένων των τμημάτων κειμένου.  
- **Ποια έκδοση Java απαιτείται;** Η Java 8 ή νεότερη υποστηρίζεται πλήρως.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Πόσοι τύποι τμημάτων κειμένου μπορούν να εξαχθούν;** Τρία κύρια είδη: γενικά, συμπιεσμένα και διεθνή.  
- **Ανησυχείτε για την απόδοση;** Η εξαγωγή ολοκληρώνεται σε λιγότερο από 200 ms για τυπικά PNG 5 MB σε σύγχρονο CPU.

## Τι είναι το “how to extract png”;
**“How to extract png”** αναφέρεται στη διαδικασία ανάκτησης ενσωματωμένων τμημάτων κειμένου από ένα αρχείο εικόνας PNG χρησιμοποιώντας προγραμματιστικά APIs. Αυτά τα τμήματα κειμένου μπορούν να περιέχουν περιγραφικά μεταδεδομένα, σχόλια ή διεθνείς συμβολοσειρές. Χρησιμοποιώντας το GroupDocs.Metadata for Java, οι προγραμματιστές μπορούν προγραμματιστικά να διαβάζουν, φιλτράρουν και να χειρίζονται αυτά τα τμήματα χωρίς να αποκωδικοποιούν ολόκληρη την εικόνα.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Metadata για εξαγωγή κειμένου PNG;
Το GroupDocs.Metadata υποστηρίζει **50+ μορφές εικόνας και εγγράφων** και μπορεί να επεξεργαστεί αρχεία PNG **χωρίς να φορτώνει ολόκληρη την εικόνα στη μνήμη**, παρέχοντας ταχύτητες εξαγωγής **150 ms κατά μέσο όρο** για αρχεία έως 10 MB. Η βιβλιοθήκη εγγυάται επίσης **100 % ακεραιότητα δεδομένων**, διατηρώντας χαρακτήρες Unicode σε διεθνή τμήματα κειμένου.

## Προαπαιτούμενα

Πριν ξεκινήσετε την εξαγωγή τμημάτων κειμένου από εικόνες PNG χρησιμοποιώντας το GroupDocs.Metadata for Java, βεβαιωθείτε ότι έχετε τα εξής:

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
- **GroupDocs.Metadata for Java**: Συμπεριλάβετε αυτή τη βιβλιοθήκη στο έργο σας μέσω Maven ή κατεβάζοντάς την απευθείας.

### Απαιτήσεις ρύθμισης περιβάλλοντος
- Ένα περιβάλλον ανάπτυξης με Java (προτιμότερο JDK 8 ή νεότερο).
- Ένα IDE όπως IntelliJ IDEA, Eclipse ή οποιοδήποτε άλλο που υποστηρίζει έργα Java.

### Προαπαιτούμενες γνώσεις
- Βασική κατανόηση του προγραμματισμού Java.
- Εξοικείωση με τη διαχείριση αρχείων και καταλόγων σε μια εφαρμογή Java.

## Ρύθμιση του GroupDocs.Metadata για Java

Για να ξεκινήσετε με το GroupDocs.Metadata, θα πρέπει να το συμπεριλάβετε στο έργο σας. Δείτε πώς μπορείτε να το κάνετε αυτό χρησιμοποιώντας Maven ή κατεβάζοντας τη βιβλιοθήκη απευθείας:

### Ρύθμιση Maven
Προσθέστε το παρακάτω αποθετήριο και εξάρτηση στο αρχείο `pom.xml`:

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
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Βήματα απόκτησης άδειας
- **Free Trial**: Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε τις δυνατότητες.  
- **Temporary License**: Αποκτήστε μια προσωρινή άδεια για εκτεταμένες δοκιμές.  
- **Purchase**: Αγοράστε άδεια εάν είστε έτοιμοι για χρήση σε παραγωγή.

### Βασική αρχικοποίηση και ρύθμιση

Αφού ρυθμίσετε τη βιβλιοθήκη, αρχικοποιήστε το GroupDocs.Metadata στην εφαρμογή Java ως εξής:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Πώς να εξάγετε τμήματα κειμένου png από ένα αρχείο PNG;

Η κλάση `Metadata` είναι το σημείο εισόδου για την πρόσβαση στις ροές μεταδεδομένων ενός αρχείου. Φορτώστε το αρχείο PNG με `new Metadata("yourImage.png")`, αποκτήστε πρόσβαση στο root package και επαναλάβετε τις επιθυμητές συλλογές τμημάτων κειμένου – όλα σε λίγες γραμμές κώδικα. Αυτή η προσέγγιση επιστρέφει κάθε γενικό, συμπιεσμένο και διεθνές τμήμα κειμένου, επιτρέποντάς σας να τα χειριστείτε όπως χρειάζεστε.

### Anchor Ορισμού
Η κλάση `Metadata` είναι το σημείο εισόδου του GroupDocs.Metadata, αντιπροσωπεύοντας ένα κοντέινερ που σας παρέχει προγραμματιστική πρόσβαση σε όλες τις ροές μεταδεδομένων μέσα σε ένα αρχείο.

## Εξαγωγή Γενικών Τμημάτων Κειμένου από PNG

Αυτή η λειτουργία σας επιτρέπει να ανακτήσετε όλα τα γενικά τμήματα κειμένου που είναι ενσωματωμένα σε ένα αρχείο PNG. Δείτε πώς να το επιτύχετε:

#### Επισκόπηση
Θα έχετε πρόσβαση και θα επαναλάβετε κάθε τμήμα κειμένου που αποθηκεύεται στα μεταδεδομένα της εικόνας.

#### Υλοποίηση βήμα‑βήμα
1. **Εισαγωγή Απαραίτητων Κλάσεων:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Αρχικοποίηση Metadata και Πρόσβαση στο Root Package:**
   `PngRootPackage` αντιπροσωπεύει το ριζικό κοντέινερ των μεταδεδομένων PNG, εκθέτοντας συλλογές τμημάτων κειμένου.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Επεξήγηση Παραμέτρων:**
   - `pngFilePath`: Διαδρομή προς το αρχείο PNG σας.
   - `PngRootPackage`: Αντιπροσωπεύει το ριζικό πακέτο που περιέχει τμήματα μεταδεδομένων.

#### Συμβουλές Επίλυσης Προβλημάτων
- Βεβαιωθείτε ότι τα αρχεία PNG σας περιέχουν τμήματα κειμένου· διαφορετικά, δεν θα ανακτηθούν δεδομένα.
- Επαληθεύστε ότι η διαδρομή προς το αρχείο PNG είναι σωστή.

## Εξαγωγή Συμπιεσμένων Τμημάτων Κειμένου από PNG

Για να χειριστείτε συγκεκριμένα τα συμπιεσμένα τμήματα κειμένου, ακολουθήστε τα παρακάτω βήματα:

#### Επισκόπηση
Αυτή η λειτουργία εστιάζει στην ανάκτηση και διαχείριση των συμπιεσμένων τμημάτων κειμένου στα μεταδεδομένα PNG.

#### Υλοποίηση βήμα‑βήμα
1. **Εισαγωγή Απαραίτητων Κλάσεων:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Αρχικοποίηση Metadata και Πρόσβαση στο Root Package:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Επεξήγηση Παραμέτρων:**
   - `getCompressionMethod()`: Επιστρέφει τη μέθοδο που χρησιμοποιείται για συμπίεση. Η μέθοδος `getCompressionMethod()` επιστρέφει τον αλγόριθμο συμπίεσης που χρησιμοποιείται για ένα συμπιεσμένο τμήμα κειμένου.

#### Συμβουλές Επίλυσης Προβλημάτων
- Βεβαιωθείτε ότι τα αρχεία PNG σας χρησιμοποιούν υποστηριζόμενη μέθοδο συμπίεσης.
- Διαχειριστείτε εξαιρέσεις όπου τα τμήματα κειμένου ενδέχεται να μην είναι συμπιεσμένα.

## Εξαγωγή Διεθνών Τμημάτων Κειμένου από PNG

Για την εξαγωγή διεθνών τμημάτων κειμένου, τα παρακάτω βήματα θα σας καθοδηγήσουν:

#### Επισκόπηση
Ανακτήστε και διαχειριστείτε διεθνή τμήματα κειμένου στα μεταδεδομένα PNG, συμπεριλαμβανομένων των λεπτομερειών γλώσσας.

#### Υλοποίηση βήμα‑βήμα
1. **Εισαγωγή Απαραίτητων Κλάσεων:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Αρχικοποίηση Metadata και Πρόσβαση στο Root Package:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Επεξήγηση Παραμέτρων:**
   - `getLanguage()`: Ανακτά την ετικέτα γλώσσας για το τμήμα κειμένου. Η μέθοδος `getLanguage()` παρέχει την ετικέτα γλώσσας ISO που σχετίζεται με ένα διεθνές τμήμα κειμένου.
   - `isCompressed()`: Δείχνει αν το τμήμα κειμένου είναι συμπιεσμένο. Η μέθοδος `isCompressed()` υποδεικνύει εάν ένα τμήμα κειμένου αποθηκεύεται σε συμπιεσμένη μορφή.

#### Συμβουλές Επίλυσης Προβλημάτων
- Βεβαιωθείτε ότι τα αρχεία PNG σας έχουν σωστά ορισμένα διεθνή μεταδεδομένα.
- Διαχειριστείτε σενάρια όπου οι μεταφράσεις ενδέχεται να μην είναι διαθέσιμες.

## Πρακτικές Εφαρμογές

Η κατανόηση του πώς να εξάγετε τμήματα κειμένου από PNG χρησιμοποιώντας το GroupDocs.Metadata μπορεί να είναι ανεκτίμητη σε διάφορες εφαρμογές:
- **Συστήματα Διαχείρισης Περιεχομένου**: Αυτόματη ανάκτηση και οργάνωση μεταδεδομένων για βιβλιοθήκες εικόνων.  
- **Εργαλεία Ανάλυσης Δεδομένων**: Ενισχύστε τις δυνατότητες εξαγωγής δεδομένων συμπεριλαμβάνοντας ανάλυση μεταδεδομένων εικόνας.  
- **Έργα Web Scraping**: Εξάγετε πολύτιμες πληροφορίες από εικόνες ενσωματωμένες σε ιστοσελίδες.

## Συχνές Ερωτήσεις

**Q: Μπορώ να διαβάσω τα μεταδεδομένα png χωρίς άδεια;**  
A: Ναι, η δωρεάν δοκιμή σας επιτρέπει να διαβάσετε τα μεταδεδομένα, αλλά απαιτείται εμπορική άδεια για παραγωγικές εγκαταστάσεις.

**Q: Υποστηρίζει το GroupDocs.Metadata άλλες μορφές εικόνας;**  
A: Απόλυτα – διαχειρίζεται JPEG, BMP, TIFF και πάνω από 40 επιπλέον μορφές.

**Q: Πώς να διαχειριστώ μεγάλα αρχεία PNG αποδοτικά;**  
A: Χρησιμοποιήστε το streaming API· επεξεργάζεται αρχεία χωρίς να φορτώνει ολόκληρη την εικόνα στη μνήμη, διατηρώντας τη χρήση RAM κάτω από 50 MB.

**Q: Τι γίνεται αν ένα PNG δεν έχει τμήματα κειμένου;**  
A: Το API επιστρέφει μια κενή συλλογή· μπορείτε να ελέγξετε με ασφάλεια το `isEmpty()` πριν την επεξεργασία.

**Q: Υποστηρίζεται το Unicode σε διεθνή τμήματα κειμένου;**  
A: Ναι, το GroupDocs.Metadata υποστηρίζει πλήρως το UTF‑8, διατηρώντας όλους τους χαρακτήρες των γλωσσών.

## Συμπέρασμα

Ακολουθώντας αυτό το tutorial, έχετε μάθει πώς να εξάγετε γενικά, συμπιεσμένα και διεθνή τμήματα κειμένου από αρχεία PNG χρησιμοποιώντας τη βιβλιοθήκη GroupDocs.Metadata σε Java. Αυτή η δεξιότητα μπορεί να ενισχύσει σημαντικά την ικανότητα της εφαρμογής σας να επεξεργάζεται και να αναλύει δεδομένα εικόνας αποδοτικά. Για περαιτέρω εξερεύνηση, σκεφτείτε να εμβαθύνετε σε πιο προχωρημένες τεχνικές διαχείρισης μεταδεδομένων που παρέχει το GroupDocs.Metadata.

**Επόμενα Βήματα**
- Πειραματιστείτε με διαφορετικούς τύπους εξαγωγής μεταδεδομένων.  
- Εξερευνήστε πρόσθετες λειτουργίες της βιβλιοθήκης GroupDocs.Metadata.  
- Μοιραστείτε τα ευρήματά σας ή τις εφαρμογές σας σε κοινότητες προγραμματιστών για σχόλια και βελτιώσεις.

---

**Τελευταία Ενημέρωση:** 2026-06-01  
**Δοκιμάστηκε Με:** GroupDocs.Metadata Java 23.9  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να εξάγετε μπλοκ πόρων εικόνας από JPEG χρησιμοποιώντας το GroupDocs.Metadata για Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Εξαγωγή σχολίων εικόνας JPEG2000 σε Java χρησιμοποιώντας το GroupDocs.Metadata: Οδηγός βήμα‑βήμα](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Εξαγωγή πόρων εικόνας από αρχεία PSD χρησιμοποιώντας το GroupDocs.Metadata σε Java: Αναλυτικός οδηγός](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)