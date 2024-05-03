---
title: Actualizar propiedades integradas en hojas de cálculo usando .NET
linktitle: Actualizar propiedades integradas en hojas de cálculo usando .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a actualizar las propiedades de metadatos integradas en archivos de Excel usando GroupDocs.Metadata para .NET. Modifique el autor, la hora de creación, la empresa y más con C#.
type: docs
weight: 14
url: /es/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## Introducción
En este tutorial, exploraremos cómo utilizar GroupDocs.Metadata para .NET para actualizar las propiedades integradas en archivos de hojas de cálculo usando C#. GroupDocs.Metadata es una potente API que permite a los desarrolladores leer, editar y eliminar propiedades de metadatos de varios formatos de archivos, incluidas las hojas de cálculo. Nos centraremos específicamente en modificar propiedades como autor, hora de creación, empresa, categoría y palabras clave dentro de archivos de Excel.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio: instale la última versión de Visual Studio.
-  GroupDocs.Metadata para .NET: descargue e instale GroupDocs.Metadata para .NET desde[pagina de descarga](https://releases.groupdocs.com/metadata/net/).
- Conocimientos básicos de C#: comprensión del lenguaje de programación C# y el marco .NET.

## Importar espacios de nombres
Comience importando los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: cargue el archivo de hoja de cálculo
 Primero, inicialice un`Metadata` objeto cargando el archivo de hoja de cálculo de entrada:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Acceder a las propiedades del documento desde la raíz
}
```
## Paso 2: actualizar las propiedades integradas
 Acceda a las propiedades integradas del documento a través del`SpreadsheetRootPackage` y modifíquelos según sea necesario:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Asegúrese de reemplazar los marcadores de posición (`YourAuthorName`, `YourCompany`, `YourCategory`con los valores reales que desea establecer para las propiedades.
## Paso 3: guardar cambios
Después de actualizar las propiedades, guarde los cambios en el archivo de hoja de cálculo:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Conclusión
En este tutorial, hemos demostrado cómo usar GroupDocs.Metadata para .NET para actualizar las propiedades integradas de los archivos de hojas de cálculo mediante programación. Al aprovechar esta API, los desarrolladores pueden administrar metadatos de manera eficiente dentro de documentos de Excel, mejorando la organización y accesibilidad de los datos.

## Preguntas frecuentes
### ¿Qué formatos de archivo admite GroupDocs.Metadata?
GroupDocs.Metadata admite una amplia gama de formatos de archivo, incluidos documentos de Microsoft Office, PDF, imágenes, archivos de audio y más.
### ¿Puedo recuperar propiedades de metadatos existentes de archivos?
Sí, puede extraer y leer propiedades de metadatos como autor, fecha de creación, palabras clave y propiedades personalizadas utilizando GroupDocs.Metadata.
### ¿GroupDocs.Metadata es compatible con .NET Core?
Sí, GroupDocs.Metadata es compatible tanto con .NET Framework como con .NET Core.
### ¿GroupDocs.Metadata ofrece una prueba gratuita?
 Sí, puede descargar una prueba gratuita de GroupDocs.Metadata desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar soporte para GroupDocs.Metadata?
 Para soporte y debates, visite el[Foro GroupDocs.Metadatos](https://forum.groupdocs.com/c/metadata/14).