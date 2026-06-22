---
date: '2026-06-22'
description: Μάθετε πώς να εξάγετε την υπογραφή γραμματοσειράς OpenType και τις λεπτομέρειες
  της ψηφιακής υπογραφής από γραμματοσειρές OpenType χρησιμοποιώντας το GroupDocs.Metadata
  για Java. Αυτός ο οδηγός βοηθά στην ασφάλεια των εγγράφων σας.
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: Πώς να εξάγετε την υπογραφή γραμματοσειράς OpenType σε Java χρησιμοποιώντας
  το GroupDocs.Metadata
type: docs
url: /el/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Πώς να εξάγετε την υπογραφή γραμματοσειράς OpenType σε Java με το GroupDocs.Metadata

Σ στις σύγχρονες εφαρμογές, η **εξαγωγή δεδομένων υπογραφής γραμματοσειράς OpenType** είναι απαραίτητη για την επιβεβαίωση της αυθεντικότητας της γραμματοσειράς και την προστασία των ψηφιακών σας περιουσιακών στοιχείων. Αυτό το εκπαιδευτικό υλικό σας δείχνει, βήμα προς βήμα, πώς να ανακτήσετε τόσο τις σημαίες υπογραφής όσο και τις πλήρεις κρυπτογραφικές λεπτομέρειες από μια γραμματοσειρά OpenType χρησιμοποιώντας το **GroupDocs.Metadata for Java**. Είτε δημιουργείτε μια αλυσίδα περιεχομένου με έμφαση στην ασφάλεια είτε απλώς χρειάζεστε να ελέγξετε μια βιβλιοθήκη γραμματοσειρών, οι παρακάτω τεχνικές θα κάνουν τη ροή εργασίας σας αξιόπιστη και γρήγορη.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη χρειάζομαι;** GroupDocs.Metadata for Java (v24.12)  
- **Ποια έκδοση της Java απαιτείται;** JDK 8 ή νεότερη  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγή  
- **Μπορώ να επεξεργαστώ πολλαπλές γραμματοσειρές;** Ναι – υποστηρίζεται επεξεργασία παρτίδας ή ταυτόχρονη επεξεργασία  
- **Είναι ο κώδικας ασφαλής για νήματα;** Δημιουργήστε ένα νέο αντικείμενο `Metadata` ανά νήμα· το αντικείμενο από μόνο του δεν είναι ασφαλές για νήματα  

## Τι είναι η υπογραφή γραμματοσειράς OpenType;
Η **υπογραφή γραμματοσειράς OpenType** είναι ένα κρυπτογραφικό τμήμα ενσωματωμένο μέσα στη γραμματοσειρά που αποδεικνύει ότι το αρχείο δεν έχει τροποποιηθεί από τη στιγμή που υπογράφηκε. Περιλαμβάνει την ώρα υπογραφής, την αλυσίδα πιστοποιητικών, τα αναγνωριστικά αλγορίθμων κατακερματισμού και προαιρετικές πληροφορίες ανάκλησης. Επίσης περιλαμβάνει αναγνωριστικό αλγορίθμου υπογραφής, την αλυσίδα πιστοποιητικών του υπογράφοντα και προαιρετικές λίστες ανάκλησης, επιτρέποντας ολοκληρωμένη επαλήθευση της ακεραιότητας και της προέλευσης της γραμματοσειράς.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Metadata για Java;
Το GroupDocs.Metadata υποστηρίζει **50+ μορφές εισόδου και εξόδου** (συμπεριλαμβανομένων DOCX, PDF, PPTX, HTML και πολλών τύπων εικόνων) και μπορεί να διαβάσει υπογραφές OpenType χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, επιτρέποντάς σας να επεξεργαστείτε συλλογές γραμματοσειρών εκατοντάδων σελίδων αποδοτικά.

## Προαπαιτούμενα
- **Java Development Kit (JDK):** Έκδοση 8 ή νεότερη.  
- **IDE:** Οποιοδήποτε IDE συμβατό με Java (IntelliJ IDEA, Eclipse, VS Code κ.λπ.).  
- **Maven:** Για διαχείριση εξαρτήσεων.  

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Προσθέστε τις συντεταγμένες Maven του GroupDocs.Metadata στο `pom.xml`. Αυτό θα κατεβάσει το ακριβές πακέτο που χρειάζονται τα παραδείγματα.

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

### Απόκτηση άδειας
- **Δωρεάν δοκιμή:** Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε τις δυνατότητες.  
- **Προσωρινή άδεια:** Αποκτήστε μια προσωρινή άδεια μέσω της [σελίδας αδειοδότησης GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **Αγορά:** Για παραγωγική χρήση, αγοράστε πλήρη άδεια.  

## Πώς να εξάγετε την υπογραφή γραμματοσειράς OpenType χρησιμοποιώντας το GroupDocs.Metadata
Η κλάση `Metadata` είναι ο πυρήνας του API του GroupDocs.Metadata για πρόσβαση στα μεταδεδομένα εγγράφων χωρίς τη φόρτωση ολόκληρου του αρχείου.  
Για να διαβάσετε την υπογραφή μιας γραμματοσειράς, δημιουργήστε ένα αντικείμενο `Metadata` με τη διαδρομή προς το αρχείο .otf και έπειτα αποκτήστε το `DigitalSignaturePackage`. Αυτή η προσέγγιση φορτώνει μόνο τις απαραίτητες δομές μεταδεδομένων, αποφεύγοντας την πλήρη ανάλυση της γραμματοσειράς και διατηρώντας τη χρήση μνήμης χαμηλή. Το αντικείμενο `Metadata` πρέπει να χρησιμοποιείται μέσα σε μπλοκ try‑with‑resources για να εξασφαλιστεί η σωστή απελευθέρωση πόρων.

Φορτώστε το αρχείο γραμματοσειράς με `new Metadata("font.otf")` μέσα σε μπλοκ try‑with‑resources. Η κλάση `Metadata` είναι το σημείο εισόδου του GroupDocs.Metadata για ανάγνωση οποιουδήποτε υποστηριζόμενου τύπου εγγράφου, συμπεριλαμβανομένων των γραμματοσειρών OpenType. Το αντικείμενο κλείνει αυτόματα, αποτρέποντας διαρροές πόρων.

### Πώς να εξάγετε τις σημαίες ψηφιακής υπογραφής
Το αντικείμενο `DigitalSignaturePackage` συγκεντρώνει όλες τις πληροφορίες σχετικές με την υπογραφή για τη γραμματοσειρά, συμπεριλαμβανομένων των σημαίων και των μεμονωμένων υπογραφών.  
**Άμεση απάντηση:** Καλέστε `metadata.getDigitalSignaturePackage().getFlags()` μετά το άνοιγμα της γραμματοσειράς· το σύνολο σημαίων που επιστρέφεται σας ενημερώνει εάν η υπογραφή είναι έγκυρη, αν έχει ανακληθεί ή αν έχει ειδικές συνθήκες. Αυτή η ενιαία κλήση παρέχει έναν γρήγορο έλεγχο υγείας πριν προχωρήσετε σε λεπτομερέστερες πληροφορίες. Τα σημαία είναι αναπαριστώνται ως αρίθμηση που μπορεί να εξεταστεί για τον καθορισμό της κατάστασης υπογραφής, παρουσίας χρονικής σήμανσης και τυχόν περιορισμών πολιτικής που εφαρμόστηκαν κατά την υπογραφή.

1. Αρχικοποιήστε το αντικείμενο `Metadata` που δείχνει στο αρχείο γραμματοσειράς σας.  
2. Ανακτήστε το `DigitalSignaturePackage`.  
3. Εκτυπώστε ή καταγράψτε τις τιμές των σημαίων.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Επεξήγηση**  
- `documentPath` – απόλυτη ή σχετική διαδρομή προς τη γραμματοσειρά OpenType.  
- Το μπλοκ try‑with‑resources εγγυάται ότι το αντικείμενο `Metadata` κλείνει αυτόματα, αποφεύγοντας διαρροές μνήμης.

### Πώς να εξάγετε λεπτομερείς πληροφορίες ψηφιακής υπογραφής
`CmsSignature` αντιπροσωπεύει μια μεμονωμένη υπογραφή CMS/PKCS#7 ενσωματωμένη στη γραμματοσειρά, παρέχοντας πρόσβαση στις κρυπτογραφικές της ιδιότητες.  
**Άμεση απάντηση:** Επανάληψη πάνω από `metadata.getDigitalSignaturePackage().getSignatures()`· κάθε αντικείμενο `CmsSignature` εκθέτει την ώρα υπογραφής, τους αλγόριθμους κατακερματισμού, το ενσωματωμένο περιεχόμενο και τις λεπτομέρειες πιστοποιητικού, επιτρέποντάς σας να δημιουργήσετε πλήρη αναφορά ελέγχου. Για κάθε υπογραφή μπορείτε να ανακτήσετε την αλυσίδα πιστοποιητικών του υπογράφοντα, να επαληθεύσετε τον αλγόριθμο κατακερματισμού και να εξάγετε τυχόν διακριτικά χρονικής σήμανσης για να επιβεβαιώσετε πότε εφαρμόστηκε η υπογραφή.

1. Επαναχρησιμοποιήστε την ίδια αρχικοποίηση `Metadata` όπως παραπάνω.  
2. Περάστε από κάθε `CmsSignature` στο πακέτο.  
3. Εξάγετε ιδιότητες όπως `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`, και `getSignerInfo()`.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**Επεξήγηση βασικών τμημάτων**  
- **Χρόνος υπογραφής:** Χρονική σήμανση όταν εφαρμόστηκε η υπογραφή.  
- **Αλγόριθμοι κατακερματισμού & OIDs:** Οι αλγόριθμοι κατακερματισμού που χρησιμοποιήθηκαν (π.χ., SHA‑256).  
- **Ενσωματωμένο περιεχόμενο:** Οποιοδήποτε επιπλέον δεδομένο που είναι ενσωματωμένο στην υπογραφή.  
- **Πιστοποιητικά:** Οι ημερομηνίες ισχύος και το μέγεθος των ακατέργαστων δεδομένων βοηθούν στην επαλήθευση της ταυτότητας του υπογράφοντα.  
- **Υπογράφοντες:** Παρέχει τις επιλογές αλγορίθμου κάθε υπογράφοντος και τις χρονικές σήμανσεις υπογραφής.

#### Συμβουλές αντιμετώπισης προβλημάτων
- Αν η γραμματοσειρά δεν διαθέτει ψηφιακή υπογραφή, η `getDigitalSignaturePackage()` επιστρέφει `null`. Πάντα ελέγχετε για `null` πριν αποκτήσετε πρόσβαση σε σημαίες ή υπογραφές.  
- Βεβαιωθείτε ότι χρησιμοποιείτε την ίδια έκδοση **GroupDocs.Metadata** όπως ορίζεται στην εξάρτηση Maven για να αποφύγετε προβλήματα συμβατότητας.  

## Πρακτικές Εφαρμογές
Η εξαγωγή υπογραφών γραμματοσειρών OpenType είναι πολύτιμη σε πολλές πραγματικές περιπτώσεις:

1. **Επαλήθευση εγγράφων:** Αυτοματοποιήστε ελέγχους για υπογεγραμμένα αρχεία γραμματοσειρών σε σύστημα διαχείρισης περιεχομένου.  
2. **Διαχείριση ψηφιακών περιουσιακών στοιχείων:** Επικυρώστε την αυθεντικότητα των γραμματοσειρών πριν τις αναπτύξετε σε έργα branding.  
3. **Ασφαλιστικές επιθεωρήσεις:** Εξετάστε τις λεπτομέρειες της υπογραφής για να διασφαλίσετε τη συμμόρφωση με τις εσωτερικές πολιτικές ασφαλείας.  

## Σκέψεις για την απόδοση
- **Διαχείριση πόρων:** Χρησιμοποιήστε try‑with‑resources για να κλείνετε άμεσα τα αντικείμενα `Metadata`.  
- **Επεξεργασία παρτίδας:** Επεξεργαστείτε τις γραμματοσειρές σε ομάδες για να ελαχιστοποιήσετε το κόστος I/O· το GroupDocs.Metadata μπορεί να διαχειριστεί χιλιάδες αρχεία χωρίς να φορτώνει ολόκληρη τη γραμματοσειρά στη μνήμη.  
- **Συγχρονισμός:** Εκτελέστε ξεχωριστά στιγμιότυπα `Metadata` σε παράλληλα νήματα για μεγάλης κλίμακας φορτία εργασίας· η βιβλιοθήκη δεν είναι ασφαλής για νήματα ανά στιγμιότυπο, επομένως απομονώστε κάθε στιγμιότυπο ανά νήμα.  

## Συχνές Ερωτήσεις

**Ε: Μπορώ να εξάγω υπογραφές από μια γραμματοσειρά που δεν έχει ψηφιακή υπογραφή;**  
Α: Η `DigitalSignaturePackage` θα είναι `null`; πάντα ελέγχετε αυτήν την κατάσταση πριν προσπαθήσετε να προσπελάσετε σημαίες ή λεπτομέρειες.

**Ε: Ποια έκδοση του GroupDocs.Metadata απαιτείται;**  
Α: Τα παραδείγματα στοχεύουν στην έκδοση **24.12**, αλλά οι νεότερες εκδόσεις παραμένουν συμβατές με γραμματοσειρές OpenType.

**Ε: Χρειάζομαι ειδική άδεια για την ανάγνωση υπογραφών;**  
Α: Μια δοκιμαστική άδεια λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγική χρήση.

**Ε: Πώς να διαχειριστώ γραμματοσειρές που αποθηκεύονται σε cloud bucket;**  
Α: Κατεβάστε τη γραμματοσειρά σε ένα προσωρινό τοπικό αρχείο, έπειτα περάστε τη διαδρομή του στο `Metadata`. Η βιβλιοθήκη λειτουργεί με οποιοδήποτε αρχείο προσβάσιμο μέσω τοπικής διαδρομής.

**Ε: Είναι δυνατόν να επαληθεύσω την κρυπτογραφική εγκυρότητα της υπογραφής;**  
Α: Το GroupDocs.Metadata παρέχει ακατέργαστα δεδομένα υπογραφής· μπορείτε να τα περάσετε σε ξεχωριστή κρυπτογραφική βιβλιοθήκη για πλήρη επαλήθευση.

## Συμπέρασμα
Ακολουθώντας αυτόν τον οδηγό, γνωρίζετε πλέον **πώς να εξάγετε πληροφορίες υπογραφής γραμματοσειράς OpenType** και λεπτομερή δεδομένα ψηφιακής υπογραφής χρησιμοποιώντας το **GroupDocs.Metadata for Java**. Η ενσωμάτωση αυτών των βημάτων στις εφαρμογές σας ενισχύει την ασφάλεια των εγγράφων, βελτιστοποιεί την επικύρωση περιουσιακών στοιχείων και υποστηρίζει πρωτοβουλίες συμμόρφωσης.

**Επόμενα Βήματα**  
- Δοκιμάστε την επεξεργασία παρτίδας για να διαχειριστείτε αποδοτικά μεγάλες βιβλιοθήκες γραμματοσειρών.  
- Συνδυάστε τα εξαγόμενα δεδομένα με τα εργαλεία ασφαλείας‑επιθεώρησης για αυτοματοποιημένη αναφορά συμμόρφωσης.  
- Εξερευνήστε άλλες δυνατότητες μεταδεδομένων του GroupDocs.Metadata, όπως η επεξεργασία ή η αφαίρεση υπογραφών όταν είναι κατάλληλο.

---

**Τελευταία ενημέρωση:** 2026-06-22  
**Δοκιμή με:** GroupDocs.Metadata 24.12  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πρόσβαση σε μεταδεδομένα εγγράφου Word με το GroupDocs σε Java&#58; Ένας ολοκληρωμένος οδηγός](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Πώς να εξάγετε προσαρμοσμένα μεταδεδομένα από PDF χρησιμοποιώντας το GroupDocs.Metadata σε Java&#58; Ένας ολοκληρωμένος οδηγός](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)