---
title: Mettre à jour les propriétés intégrées dans les feuilles de calcul à l'aide de .NET
linktitle: Mettre à jour les propriétés intégrées dans les feuilles de calcul à l'aide de .NET
second_title: API GroupDocs.Metadata .NET
description: Découvrez comment mettre à jour les propriétés des métadonnées intégrées dans les fichiers Excel à l'aide de GroupDocs.Metadata pour .NET. Modifiez l'auteur, l'heure de création, l'entreprise et bien plus encore avec C#.
weight: 14
url: /fr/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## Introduction
Dans ce didacticiel, nous explorerons comment utiliser GroupDocs.Metadata pour .NET pour mettre à jour les propriétés intégrées dans les feuilles de calcul à l'aide de C#. GroupDocs.Metadata est une API puissante qui permet aux développeurs de lire, modifier et supprimer les propriétés des métadonnées de divers formats de fichiers, y compris les feuilles de calcul. Nous nous concentrerons spécifiquement sur la modification des propriétés telles que l'auteur, l'heure de création, l'entreprise, la catégorie et les mots-clés dans les fichiers Excel.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio : installez la dernière version de Visual Studio.
-  GroupDocs.Metadata pour .NET : téléchargez et installez GroupDocs.Metadata pour .NET à partir du[page de téléchargement](https://releases.groupdocs.com/metadata/net/).
- Connaissances de base en C# : Compréhension du langage de programmation C# et du framework .NET.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Étape 1 : Charger le fichier de feuille de calcul
 Tout d'abord, initialisez un`Metadata` objet en chargeant le fichier de feuille de calcul d'entrée :
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Accéder aux propriétés du document à la racine
}
```
## Étape 2 : mettre à jour les propriétés intégrées
 Accédez aux propriétés intégrées du document via le`SpreadsheetRootPackage` et modifiez-les si nécessaire :
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Assurez-vous de remplacer les espaces réservés (`YourAuthorName`, `YourCompany`, `YourCategory`avec les valeurs réelles que vous souhaitez définir pour les propriétés.
## Étape 3 : Enregistrer les modifications
Après avoir mis à jour les propriétés, enregistrez les modifications dans le fichier de feuille de calcul :
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Conclusion
Dans ce didacticiel, nous avons montré comment utiliser GroupDocs.Metadata pour .NET pour mettre à jour les propriétés intégrées des fichiers de feuille de calcul par programme. En tirant parti de cette API, les développeurs peuvent gérer efficacement les métadonnées dans les documents Excel, améliorant ainsi l'organisation et l'accessibilité des données.

## FAQ
### Quels formats de fichiers GroupDocs.Metadata prend-il en charge ?
GroupDocs.Metadata prend en charge un large éventail de formats de fichiers, notamment les documents Microsoft Office, les PDF, les images, les fichiers audio, etc.
### Puis-je récupérer les propriétés de métadonnées existantes à partir de fichiers ?
Oui, vous pouvez extraire et lire les propriétés des métadonnées telles que l'auteur, la date de création, les mots-clés et les propriétés personnalisées à l'aide de GroupDocs.Metadata.
### GroupDocs.Metadata est-il compatible avec .NET Core ?
Oui, GroupDocs.Metadata est compatible avec .NET Framework et .NET Core.
### GroupDocs.Metadata propose-t-il un essai gratuit ?
 Oui, vous pouvez télécharger un essai gratuit de GroupDocs.Metadata à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de l’assistance pour GroupDocs.Metadata ?
 Pour obtenir de l'aide et des discussions, visitez le[Forum GroupDocs.Metadonnées](https://forum.groupdocs.com/c/metadata/14).