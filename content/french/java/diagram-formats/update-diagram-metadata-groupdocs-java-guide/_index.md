---
date: '2026-06-17'
description: Apprenez comment modifier l'heure de création du diagramme et automatiser
  la mise à jour des métadonnées des fichiers de diagramme en utilisant GroupDocs.Metadata
  en Java.
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
title: Modifier l'heure de création du diagramme dans les métadonnées avec GroupDocs
  Java
type: docs
url: /fr/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Modifier l'heure de création du diagramme dans les métadonnées avec GroupDocs Java

Dans ce tutoriel étape par étape, vous découvrirez comment **modifier l'heure de création du diagramme** et mettre à jour d'autres propriétés intégrées des fichiers de diagramme en utilisant la bibliothèque GroupDocs.Metadata pour Java. L'automatisation de ces modifications permet d'économiser des heures de travail manuel, garantit des horodatages cohérents dans tout votre référentiel et rend vos diagrammes immédiatement recherchables dans tout système de gestion de documents.

## Réponses rapides
- **Quel est l'objectif principal ?** Modifier l'heure de création du diagramme et d'autres métadonnées dans les fichiers de diagramme.  
- **Quelle bibliothèque dois-je utiliser ?** GroupDocs.Metadata for Java.  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour les tests ; une licence complète est requise pour la production.  
- **Puis-je traiter en lot de nombreux diagrammes ?** Oui—encapsulez la même logique dans une boucle ou un flux parallèle.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.

## Qu'est-ce que « modifier l'heure de création du diagramme » dans les métadonnées du diagramme ?
Modifier l'heure de création remplace l'horodatage original stocké à l'intérieur d'un fichier de diagramme (tel que VDX ou VSDX) par une nouvelle valeur de date‑heure. Cela vous permet d'aligner les métadonnées du fichier avec la date réelle de traitement ou d'archivage plutôt qu'avec l'horodatage original de l'auteur, ce qui est essentiel pour les pistes d'audit et des résultats de recherche précis.

## Pourquoi automatiser la mise à jour des métadonnées pour les diagrammes ?
L'automatisation des métadonnées garantit que chaque diagramme suit les mêmes normes de nommage, de catégorisation et d'horodatage sans erreur humaine. Elle accélère également les migrations en masse, réduit les risques de conformité et améliore la découvrabilité sur les plateformes DMS d'entreprise — économisant jusqu'à 70 % d'effort manuel dans les projets à grande échelle.

## Prérequis
- **Java Development Kit (JDK) 8+** installé sur votre machine.  
- **IDE** tel qu'IntelliJ IDEA ou Eclipse.  
- **Maven** (ou gestion manuelle des JAR) pour la gestion des dépendances.  
- Familiarité de base avec les classes Java, les méthodes et la gestion des exceptions.

### Bibliothèques et dépendances requises
Ajoutez le dépôt et la dépendance suivants à votre fichier `pom.xml` si vous utilisez Maven :

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
Si vous préférez télécharger directement, rendez‑vous sur [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) pour obtenir la dernière version.

### Configuration de l'environnement
- JDK 8 ou version supérieure.  
- IntelliJ IDEA, Eclipse ou tout IDE compatible Java.  

### Prérequis de connaissances
Comprendre la syntaxe Java et les bases des entrées‑sorties de fichiers facilitera le suivi du tutoriel, mais les étapes sont expliquées en langage clair.

## Configuration de GroupDocs.Metadata pour Java
### Instructions d'installation
**Utilisateurs Maven :** L'extrait ci‑dessus ajoute le dépôt et le JAR requis automatiquement.  
**Utilisateurs de téléchargement direct :** Après avoir téléchargé le JAR depuis [GroupDocs](https://releases.groupdocs.com/metadata/java/), ajoutez‑le au classpath de votre projet.

### Acquisition de licence
- **Essai gratuit :** Explorez la bibliothèque gratuitement.  
- **Licence temporaire :** Obtenez une licence temporaire pour des tests prolongés [ici](https://purchase.groupdocs.com/temporary-license/).  
- **Achat :** Obtenez une licence complète pour les environnements de production.

### Initialisation de base
`Metadata` est la classe principale qui représente le conteneur de métadonnées d'un document et fournit un accès en lecture/écriture à toutes les propriétés intégrées. Pour commencer à utiliser GroupDocs.Metadata, importez la classe et ouvrez un fichier de diagramme :

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

## Guide de mise en œuvre
### Comment modifier l'heure de création dans les fichiers de diagramme
Dans cette section, nous parcourrons chaque étape nécessaire pour **modifier l'heure de création du diagramme** et mettre à jour d'autres propriétés courantes telles que l'auteur, l'entreprise et la catégorie. Le processus consiste à charger le diagramme avec l'API Metadata, accéder à son package racine, définir les champs souhaités, puis enregistrer les modifications dans un nouveau fichier, en veillant à ce que l'original reste intact.

#### Étape 1 : Charger le document de diagramme
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Explication :* Le constructeur `Metadata` reçoit le chemin de votre fichier de diagramme. Le bloc try‑with‑resources garantit que le fichier est correctement fermé après l'opération.

#### Étape 2 : Accéder au package racine
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Explication :* Le package racine vous donne un accès direct à tous les champs de métadonnées intégrés du diagramme.

#### Étape 3 : Définir la propriété Créateur
```java
root.getDocumentProperties().setCreator("test author");
```  
*Explication :* Assigne un nouveau nom d'auteur. Remplacez `"test author"` par le créateur réel.

#### Étape 4 : Modifier l'heure de création
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Explication :* Cette ligne **modifie l'heure de création** à la date et l'heure système actuelles. Vous pouvez également fournir une instance `Date` spécifique si vous avez besoin d'un horodatage personnalisé.

#### Étape 5 : Définir les informations de l'entreprise
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Explication :* Enregistre le nom de l'entreprise associé au diagramme — utile pour le suivi en entreprise.

#### Étape 6 : Définir la catégorie du document
```java
root.getDocumentProperties().setCategory("test category");
```  
*Explication :* Catégorise le fichier, vous aidant à **mettre à jour la catégorie du diagramme** de manière cohérente dans tout votre référentiel.

#### Étape 7 : Ajouter des mots‑clés
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Explication :* Les mots‑clés améliorent la recherchabilité ; vous pouvez lister tous les termes pertinents au contenu du diagramme.

#### Étape 8 : Enregistrer les modifications
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Explication :* Enregistre toutes les modifications dans un nouveau fichier, en laissant l'original intact.

### Problèmes courants et dépannage
- **Fichier non trouvé :** Vérifiez le chemin d'entrée et assurez‑vous que l'extension du fichier correspond au format réel.  
- **Accès refusé :** Vérifiez les permissions de lecture/écriture pour les répertoires d'entrée et de sortie.  
- **Format de date invalide :** Utilisez des objets `java.util.Date` ou `java.time` compatibles avec l'API.  

## Applications pratiques
1. **Automatisation de l'archivage des documents** – Lors du déplacement d'anciens diagrammes vers une archive, **modifier l'heure de création du diagramme** automatiquement à la date d'archivage et définir une catégorie uniforme.  
2. **Intégration du contrôle de version** – Gardez les horodatages synchronisés avec les commits Git en mettant à jour l'heure de création à chaque version.  
3. **Standardisation DMS d'entreprise** – Appliquez une politique d'entreprise pour l'auteur, l'entreprise et les mots‑clés sur tous les actifs de diagrammes.  

## Considérations de performance
- **Traitement par lots :** Encapsulez les étapes ci‑dessus dans une boucle pour traiter des dizaines de fichiers en une exécution.  
- **Gestion de la mémoire :** Libérez chaque instance `Metadata` rapidement (le bloc try‑with‑resources le fait automatiquement).  
- **Exécution asynchrone :** Pour de gros lots, envisagez `CompletableFuture` pour exécuter les mises à jour en parallèle sans bloquer le thread principal.  
- **Capacité quantifiée :** GroupDocs.Metadata prend en charge plus de 30 formats de diagramme et peut traiter des fichiers jusqu'à 500 Mo sans charger l'intégralité du document en mémoire, livrant les mises à jour en moins de 200 ms par fichier sur du matériel serveur typique.  

## Conclusion
Vous savez maintenant comment **modifier l'heure de création du diagramme** et mettre à jour d'autres propriétés de métadonnées intégrées pour les documents de diagramme en utilisant GroupDocs.Metadata en Java. En automatisant ces étapes, vous pouvez maintenir une documentation cohérente, recherchable et conforme dans toute votre organisation.

**Prochaines étapes**
- Expérimentez avec d'autres formats de fichiers pris en charge par GroupDocs.Metadata (PDF, DOCX, etc.).  
- Intégrez le code dans un pipeline CI/CD pour appliquer les normes de métadonnées à chaque build.  

Prêt à l'essayer ? Rendez‑vous sur [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) et commencez dès aujourd'hui à implémenter votre propre automatisation des métadonnées.

---

**Dernière mise à jour :** 2026-06-17  
**Testé avec :** GroupDocs.Metadata 24.12  
**Auteur :** GroupDocs  

## Questions fréquentes

**Q : Puis‑je utiliser cette approche avec d'autres formats de diagramme comme VSDX ?**  
R : Oui, la même API fonctionne pour tous les formats de diagramme pris en charge par GroupDocs.Metadata.

**Q : Ai‑je besoin d'une licence pour les builds de développement ?**  
R : Un essai gratuit suffit pour le développement et les tests ; une licence complète est requise pour les déploiements en production.

**Q : Comment puis‑je mettre à jour plusieurs propriétés en un seul appel ?**  
R : Définissez chaque propriété sur l'objet `DocumentProperties` avant d'appeler `metadata.save(...)` ; la bibliothèque les écrit toutes en une fois.

**Q : Est‑il sûr d'écraser le fichier original ?**  
R : Il est recommandé d'enregistrer dans un nouveau fichier (comme indiqué) et de remplacer l'original uniquement après avoir confirmé que la mise à jour a réussi.

**Q : Que faire si je dois définir une date de création personnalisée au lieu de l'heure actuelle ?**  
R : Créez une `java.util.Date` (ou une instance `java.time`) avec l'horodatage souhaité et transmettez‑la à `setTimeCreated`.

## Tutoriels associés

- [How to Update Diagram Metadata Java with GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [How to Update DXF Author Metadata with GroupDocs.Metadata for Java – A Complete Guide](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Automate Java Metadata Updates by Date Using GroupDocs.Metadata for Efficient File Management](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)