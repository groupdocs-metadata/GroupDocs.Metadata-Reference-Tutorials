---
title: Mettre à jour les propriétés intégrées dans les PDF à l'aide de .NET
linktitle: Mettre à jour les propriétés intégrées dans les PDF à l'aide de .NET
second_title: API GroupDocs.Metadata .NET
description: Découvrez comment mettre à jour les propriétés d'un document PDF à l'aide de C# et GroupDocs.Metadata pour .NET. Modifiez l'auteur, le titre, les mots-clés et bien plus encore par programmation.
type: docs
weight: 15
url: /fr/net/pdf-metadata/update-built-in-properties-pdfs/
---
## Introduction
Dans ce didacticiel, nous apprendrons comment utiliser GroupDocs.Metadata pour .NET pour mettre à jour les propriétés intégrées des documents PDF. Cette bibliothèque fournit un ensemble d'outils puissants pour manipuler les métadonnées dans différents formats de documents. Nous passerons en revue les étapes nécessaires pour modifier les propriétés telles que l'auteur, le titre, la date de création, les mots-clés, le créateur et le producteur dans un fichier PDF à l'aide de C#.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir mis en place les éléments suivants :
-  GroupDocs.Metadata pour la bibliothèque .NET : téléchargez la bibliothèque à partir de[ici](https://releases.groupdocs.com/metadata/net/).
- Visual Studio : installez Visual Studio pour écrire et exécuter le code C#.
- Compréhension de base de C# : Une connaissance du langage de programmation C# est recommandée.

## Importer des espaces de noms
Commencez par inclure les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Étape 1 : initialiser l'objet de métadonnées
 Commencez par initialiser un`Metadata`objet avec le chemin d'accès à votre fichier PDF :
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Votre code ira ici
}
```
## Étape 2 : Accéder au package racine PDF
 Ensuite, récupérez le package racine spécifiquement pour PDF en utilisant`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Étape 3 : mettre à jour les propriétés du document
 Maintenant, mettez à jour les propriétés souhaitées du document PDF dans le`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Étape 4 : Enregistrer les modifications
Après avoir modifié les propriétés, enregistrez les modifications dans le fichier PDF :
```csharp
metadata.Save("Your Output File Path");
```
## Étape 5 : Récupérer les propriétés mises à jour
Pour vérifier les modifications, rechargez les métadonnées et récupérez les propriétés mises à jour :
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Conclusion
Dans ce didacticiel, nous avons exploré comment exploiter GroupDocs.Metadata pour .NET pour mettre à jour les propriétés intégrées des documents PDF par programme. En suivant les étapes décrites, vous pouvez gérer et modifier efficacement les métadonnées dans les fichiers PDF à l'aide de C#. N'hésitez pas à explorer davantage de fonctionnalités et de capacités offertes par GroupDocs.Metadata pour une manipulation complète des métadonnées.

## FAQ
### Q : Qu'est-ce que GroupDocs.Metadata pour .NET ?
: GroupDocs.Metadata pour .NET est une bibliothèque qui permet aux développeurs de lire, modifier, supprimer et manipuler par programme des métadonnées dans divers formats de documents.
### Q : Où puis-je trouver la documentation de GroupDocs.Metadata pour .NET ?
 R : Vous pouvez accéder à la documentation[ici](https://reference.groupdocs.com/metadata/net/).
### Q : Comment puis-je télécharger GroupDocs.Metadata pour .NET ?
 R : Vous pouvez télécharger GroupDocs.Metadata pour .NET à partir de[ce lien](https://releases.groupdocs.com/metadata/net/).
### Q : Existe-t-il un essai gratuit ?
 R : Oui, vous pouvez obtenir une version d'essai gratuite[ici](https://releases.groupdocs.com/).
### Q : Où puis-je obtenir de l'assistance pour GroupDocs.Metadata pour .NET ?
 R : Pour obtenir de l'aide, visitez le forum GroupDocs.Metadata[ici](https://forum.groupdocs.com/c/metadata/14).