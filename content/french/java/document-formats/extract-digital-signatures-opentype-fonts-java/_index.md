---
date: '2026-06-22'
description: Apprenez comment extraire la signature de police OpenType et les détails
  de la digital signature des polices OpenType en utilisant GroupDocs.Metadata pour
  Java. Ce guide aide à sécuriser vos documents.
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
title: Comment extraire la signature de police OpenType en Java avec GroupDocs.Metadata
type: docs
url: /fr/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Comment extraire la signature de police OpenType en Java avec GroupDocs.Metadata

Dans les applications modernes, **extraire les données de signature de police OpenType** est essentiel pour confirmer l’authenticité des polices et protéger vos actifs numériques. Ce tutoriel vous montre, étape par étape, comment récupérer à la fois les indicateurs de signature et les détails cryptographiques complets d’une police OpenType à l’aide de **GroupDocs.Metadata pour Java**. Que vous construisiez un pipeline de contenu axé sur la sécurité ou que vous ayez simplement besoin d’auditer une bibliothèque de polices, les techniques ci‑dessous rendront votre flux de travail fiable et rapide.

## Réponses rapides
- **Quelle bibliothèque faut‑il ?** GroupDocs.Metadata for Java (v24.12)  
- **Quelle version de Java est requise ?** JDK 8 ou ultérieure  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour l’évaluation ; une licence complète est requise pour la production  
- **Puis‑je traiter plusieurs polices ?** Oui – le traitement par lots ou concurrent est pris en charge  
- **Le code est‑il thread‑safe ?** Créez une nouvelle instance `Metadata` par thread ; l’objet lui‑même n’est pas thread‑safe  

## Qu’est-ce qu’une signature de police OpenType ?
La **signature de police OpenType** est un bloc cryptographique intégré dans la police qui prouve que le fichier n’a pas été modifié depuis sa signature. Elle contient l’heure de signature, la chaîne de certificats, les identifiants des algorithmes de hachage et des informations de révocation facultatives. Elle inclut également un identifiant d’algorithme de signature, la chaîne de certificats du signataire et des listes de révocation optionnelles, permettant une vérification complète de l’intégrité et de l’origine de la police.

## Pourquoi utiliser GroupDocs.Metadata pour Java ?
GroupDocs.Metadata prend en charge **plus de 50 formats d’entrée et de sortie** (y compris DOCX, PDF, PPTX, HTML et de nombreux types d’image) et peut lire les signatures OpenType sans charger le fichier complet en mémoire, vous permettant de traiter efficacement des collections de polices de plusieurs centaines de pages.

## Prérequis
- **Java Development Kit (JDK) :** Version 8 ou supérieure.  
- **IDE :** Tout IDE compatible Java (IntelliJ IDEA, Eclipse, VS Code, etc.).  
- **Maven :** Pour la gestion des dépendances.  

### Bibliothèques et dépendances requises
Ajoutez les coordonnées Maven de GroupDocs.Metadata à votre `pom.xml`. Cela récupère le package exact nécessaire aux exemples.

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

### Téléchargement direct
Alternativement, téléchargez la dernière version depuis [GroupDocs.Metadata pour Java – versions](https://releases.groupdocs.com/metadata/java/).

### Obtention de licence
- **Essai gratuit :** Commencez avec un essai gratuit pour explorer les fonctionnalités.  
- **Licence temporaire :** Obtenez une licence temporaire via la [page de licence GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **Achat :** Pour une utilisation en production, achetez une licence complète.

## Comment extraire la signature de police OpenType à l’aide de GroupDocs.Metadata
La classe `Metadata` est l’API centrale de GroupDocs.Metadata pour accéder aux métadonnées d’un document sans charger le fichier complet.  
Pour lire la signature d’une police, créez une instance `Metadata` avec le chemin du fichier .otf puis accédez à son `DigitalSignaturePackage`. Cette approche ne charge que les structures de métadonnées nécessaires, évitant l’analyse complète de la police et maintenant une faible utilisation de la mémoire. L’instance `Metadata` doit être utilisée dans un bloc try‑with‑resources pour garantir une libération correcte des ressources.

Chargez votre fichier de police avec `new Metadata("font.otf")` à l’intérieur d’un bloc try‑with‑resources. La classe `Metadata` est le point d’entrée de GroupDocs.Metadata pour lire tout type de document pris en charge, y compris les polices OpenType. L’objet se ferme automatiquement, évitant les fuites de ressources.

### Comment extraire les indicateurs de signature numérique
L’objet `DigitalSignaturePackage` regroupe toutes les informations liées à la signature pour la police, y compris les indicateurs et les signatures individuelles.  
**Réponse directe :** Appelez `metadata.getDigitalSignaturePackage().getFlags()` après avoir ouvert la police ; l’ensemble d’indicateurs retourné vous indique si la signature est valide, révoquée ou possède des conditions spéciales. Cet appel unique vous fournit un contrôle rapide de l’état avant d’approfondir les détails. Les indicateurs sont représentés sous forme d’énumération pouvant être inspectée pour déterminer le statut de la signature, la présence d’un horodatage et toute contrainte de politique appliquée lors de la signature.

1. Initialise l’instance `Metadata` pointant vers votre fichier de police.  
2. Récupère le `DigitalSignaturePackage`.  
3. Affiche ou consigne les valeurs des indicateurs.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Explication**  
- `documentPath` – chemin absolu ou relatif vers la police OpenType.  
- Le bloc try‑with‑resources garantit que l’objet `Metadata` est fermé automatiquement, évitant les fuites de mémoire.

### Comment extraire les informations détaillées de la signature numérique
`CmsSignature` représente une signature CMS/PKCS#7 individuelle intégrée dans la police, offrant l’accès à ses propriétés cryptographiques.  
**Réponse directe :** Parcourez `metadata.getDigitalSignaturePackage().getSignatures()` ; chaque objet `CmsSignature` expose l’heure de signature, les algorithmes de hachage, le contenu encapsulé et les détails du certificat, vous permettant de créer un rapport d’audit complet. Pour chaque signature, vous pouvez récupérer la chaîne de certificats du signataire, vérifier l’algorithme de hachage et extraire les jetons d’horodatage afin de confirmer le moment où la signature a été appliquée.

1. Réutilisez la même initialisation `Metadata` que ci‑dessus.  
2. Parcourez chaque `CmsSignature` du package.  
3. Extrayez les propriétés telles que `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()` et `getSignerInfo()`.

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

**Explication des sections clés**  
- **Heure de signature :** Horodatage de l’application de la signature.  
- **Algorithmes de hachage & OID :** Algorithmes de hachage utilisés (p. ex., SHA‑256).  
- **Contenu encapsulé :** Toute donnée supplémentaire encapsulée dans la signature.  
- **Certificats :** Dates de validité et taille des données brutes aident à vérifier l’identité du signataire.  
- **Signataires :** Fournit les choix d’algorithme de chaque signataire et les horodatages de signature.

#### Conseils de dépannage
- Si la police ne possède pas de signature numérique, `getDigitalSignaturePackage()` renvoie `null`. Vérifiez toujours la valeur `null` avant d’accéder aux indicateurs ou aux signatures.  
- Assurez‑vous d’utiliser la même version de **GroupDocs.Metadata** que celle définie dans la dépendance Maven afin d’éviter les problèmes de compatibilité.  

## Applications pratiques
L’extraction des signatures de polices OpenType est utile dans de nombreux scénarios réels :

1. **Vérification de documents :** Automatisez les contrôles des fichiers de police signés dans un système de gestion de contenu.  
2. **Gestion des actifs numériques :** Validez l’authenticité des polices avant de les déployer dans des projets de branding.  
3. **Audits de sécurité :** Examinez les détails de la signature pour garantir la conformité aux politiques de sécurité internes.

## Considérations de performance
- **Gestion des ressources :** Utilisez try‑with‑resources pour fermer rapidement les objets `Metadata`.  
- **Traitement par lots :** Traitez les polices par groupes afin de réduire la surcharge d’E/S ; GroupDocs.Metadata peut gérer des milliers de fichiers sans charger chaque police complète en mémoire.  
- **Concurrence :** Exécutez des instances `Metadata` distinctes dans des threads parallèles pour des charges de travail à grande échelle ; la bibliothèque n’est pas thread‑safe par instance, il faut donc isoler chaque instance par thread.  

## Questions fréquentes

**Q : Puis‑je extraire des signatures d’une police qui n’a pas de signature numérique ?**  
R : `DigitalSignaturePackage` sera `null` ; vérifiez toujours cette condition avant d’accéder aux indicateurs ou aux détails.

**Q : Quelle version de GroupDocs.Metadata est requise ?**  
R : Les exemples ciblent la version **24.12**, mais les versions plus récentes restent compatibles avec les polices OpenType.

**Q : Ai‑je besoin d’une licence spéciale pour lire les signatures ?**  
R : Une licence d’essai fonctionne pour l’évaluation ; une licence complète est requise pour une utilisation en production.

**Q : Comment gérer les polices stockées dans un bucket cloud ?**  
R : Téléchargez la police dans un fichier local temporaire, puis transmettez son chemin à `Metadata`. La bibliothèque fonctionne avec tout fichier accessible via un chemin local.

**Q : Est‑il possible de vérifier la validité cryptographique de la signature ?**  
R : GroupDocs.Metadata fournit les données brutes de la signature ; vous pouvez transmettre la chaîne de certificats et les valeurs de hachage à une bibliothèque cryptographique séparée pour effectuer une vérification complète.

## Conclusion
En suivant ce guide, vous savez maintenant **comment extraire les informations de signature de police OpenType** et les données détaillées de signature numérique à l’aide de **GroupDocs.Metadata pour Java**. Intégrer ces étapes dans vos applications renforce la sécurité des documents, rationalise la validation des actifs et soutient les initiatives de conformité.

**Prochaines étapes**  
- Expérimentez le traitement par lots pour gérer efficacement de grandes bibliothèques de polices.  
- Combinez les données extraites avec vos outils d’audit de sécurité pour des rapports de conformité automatisés.  
- Explorez d’autres capacités de métadonnées de GroupDocs.Metadata, comme la modification ou la suppression de signatures lorsque cela est approprié.

**Dernière mise à jour :** 2026-06-22  
**Testé avec :** GroupDocs.Metadata 24.12  
**Auteur :** GroupDocs

## Tutoriels associés

- [Accéder aux métadonnées de documents Word avec GroupDocs en Java : guide complet](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)  
- [Comment extraire les métadonnées personnalisées des PDF avec GroupDocs.Metadata en Java : guide complet](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)