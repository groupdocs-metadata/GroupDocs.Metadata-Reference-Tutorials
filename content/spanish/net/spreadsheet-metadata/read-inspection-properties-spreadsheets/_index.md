---
title: Leer propiedades de inspección de hojas de cálculo en .NET
linktitle: Leer propiedades de inspección de hojas de cálculo en .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a leer propiedades de inspección de hojas de cálculo utilizando GroupDocs.Metadata para .NET. Acceda a comentarios, firmas digitales y hojas ocultas sin esfuerzo.
weight: 13
url: /es/net/spreadsheet-metadata/read-inspection-properties-spreadsheets/
type: docs
---
# Leer propiedades de inspección de hojas de cálculo en .NET

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Metadata para .NET para inspeccionar propiedades de hojas de cálculo. GroupDocs.Metadata para .NET es una potente biblioteca que permite a los desarrolladores leer, editar y eliminar metadatos asociados con varios formatos de archivos, incluidas las hojas de cálculo. Este tutorial se centra específicamente en la lectura de propiedades de inspección de archivos de hojas de cálculo utilizando C#.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio: asegúrese de tener Visual Studio instalado en su máquina de desarrollo.
-  GroupDocs.Metadata para .NET: descargue e instale GroupDocs.Metadata para .NET desde[aquí](https://releases.groupdocs.com/metadata/net/).
- Archivo de entrada: Prepare un archivo de hoja de cálculo de muestra (por ejemplo, un archivo Excel) para inspeccionar sus propiedades.

## Importar espacios de nombres
Comience importando los espacios de nombres necesarios a su proyecto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: cargar los metadatos
Comience cargando los metadatos desde su archivo de hoja de cálculo de entrada:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
```
## Paso 2: Acceder a las propiedades de inspección
Ahora, accedamos a varias propiedades de inspección, como comentarios, firmas digitales y hojas ocultas.
### Leer comentarios
Recuperar y mostrar comentarios presentes en la hoja de cálculo:
```csharp
if (root.InspectionPackage.Comments != null)
{
    foreach (var comment in root.InspectionPackage.Comments)
    {
        Console.WriteLine("Author: " + comment.Author);
        Console.WriteLine("Comment Text: " + comment.Text);
        Console.WriteLine("Sheet Number: " + comment.SheetNumber);
        Console.WriteLine("Row: " + comment.Row);
        Console.WriteLine("Column: " + comment.Column);
        Console.WriteLine();
    }
}
```
### Lectura de firmas digitales
Extraiga y muestre firmas digitales asociadas a la hoja de cálculo:
```csharp
if (root.InspectionPackage.DigitalSignatures != null)
{
    foreach (var signature in root.InspectionPackage.DigitalSignatures)
    {
        Console.WriteLine("Certificate Subject: " + signature.CertificateSubject);
        Console.WriteLine("Comments: " + signature.Comments);
        Console.WriteLine("Sign Time: " + signature.SignTime);
        Console.WriteLine();
    }
}
```
### Leer hojas ocultas
Recupere y enumere hojas ocultas dentro de la hoja de cálculo:
```csharp
if (root.InspectionPackage.HiddenSheets != null)
{
    foreach (var sheet in root.InspectionPackage.HiddenSheets)
    {
        Console.WriteLine("Sheet Name: " + sheet.Name);
        Console.WriteLine("Sheet Number: " + sheet.Number);
        Console.WriteLine();
    }
}
```

## Conclusión
En este tutorial, exploramos cómo usar GroupDocs.Metadata para .NET para inspeccionar varias propiedades de las hojas de cálculo. Puede ampliar aún más esta funcionalidad para manipular, actualizar o eliminar metadatos según sus requisitos.

## Preguntas frecuentes
### ¿GrupoDocs.Metadata puede leer metadatos de otros formatos de archivo además de las hojas de cálculo?
Sí, GroupDocs.Metadata admite una amplia gama de formatos de documentos e imágenes.
### ¿GroupDocs.Metadata es compatible con .NET Core?
Sí, GroupDocs.Metadata es compatible tanto con .NET Framework como con .NET Core.
### ¿Cómo puedo editar metadatos usando GroupDocs.Metadata?
Puede modificar las propiedades de los metadatos utilizando los métodos API GroupDocs.Metadata.
### ¿GroupDocs.Metadata proporciona soporte para documentos cifrados?
Sí, GroupDocs.Metadata puede manejar metadatos en archivos cifrados y protegidos con contraseña.
### ¿Puedo eliminar metadatos de archivos usando GroupDocs.Metadata?
Sí, puede eliminar metadatos de archivos utilizando la biblioteca GroupDocs.Metadata.