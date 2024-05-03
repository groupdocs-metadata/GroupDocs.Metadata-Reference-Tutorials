---
title: Leer propiedades integradas de hojas de cálculo en .NET
linktitle: Leer propiedades integradas de hojas de cálculo en .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a extraer metadatos de hojas de cálculo en .NET utilizando GroupDocs.Metadata, mejorando la gestión y organización de documentos en sus aplicaciones.
type: docs
weight: 10
url: /es/net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
---
## Introducción
En este tutorial, profundizaremos en cómo utilizar GroupDocs.Metadata para .NET para administrar y extraer metadatos de hojas de cálculo de manera eficiente. GroupDocs.Metadata para .NET es una potente API que permite a los desarrolladores trabajar con metadatos integrados en varios formatos de archivos, incluidas hojas de cálculo, presentaciones, documentos, imágenes y más. Esta guía se centra específicamente en extraer propiedades integradas de archivos de hojas de cálculo usando C#.
## Requisitos previos
Antes de comenzar, asegúrese de cumplir con los siguientes requisitos previos:
- Entorno de desarrollo: Visual Studio o cualquier IDE compatible con C#.
-  GroupDocs.Metadata para la biblioteca .NET: descargue e instale la biblioteca desde[sitio web](https://releases.groupdocs.com/metadata/net/).
- Archivo de entrada: prepare un archivo de hoja de cálculo de muestra (por ejemplo, Excel) del cual desea extraer metadatos.

## Importar espacios de nombres
Comience importando los espacios de nombres necesarios para acceder a las funcionalidades de GroupDocs.Metadata dentro de su proyecto C#.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: Inicializar metadatos y recuperar el paquete raíz de la hoja de cálculo
 Comience por inicializar el`Metadata` objeto con la ruta del archivo de entrada. Luego, obtenga el paquete raíz específico para hojas de cálculo.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    //Acceder y recuperar propiedades integradas
}
```
## Paso 2: acceda a las propiedades integradas
 Una vez que tenga el paquete raíz, puede acceder a varias propiedades integradas del archivo de hoja de cálculo usando`DocumentProperties`.
### Paso 2.1: Acceder a la propiedad del autor
Recupera el autor (creador) de la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### Paso 2.2: Acceder a la propiedad de hora creada
Obtenga la marca de tiempo de creación de la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### Paso 2.3: Acceda a la propiedad de la empresa
Obtenga el nombre de la empresa asociada con la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### Paso 2.4: Acceder a la propiedad de categoría
Obtener la información de categoría de la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### Paso 2.5: Acceder a la propiedad de palabras clave
Recupere las palabras clave asociadas con la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### Paso 2.6: Acceder a la propiedad del idioma
Recupera el idioma utilizado en la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### Paso 2.7: Acceder a la propiedad del tipo de contenido
Obtenga el tipo de contenido o tipo MIME de la hoja de cálculo.
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## Conclusión
En este tutorial, exploramos cómo usar GroupDocs.Metadata para .NET para extraer propiedades integradas de archivos de hojas de cálculo usando C#. Si sigue estos pasos, podrá integrar perfectamente la gestión de metadatos en sus aplicaciones .NET, mejorando la organización de archivos y las capacidades de recuperación.

## Preguntas frecuentes
### ¿GroupDocs.Metadata para .NET es compatible con varios formatos de archivo?
Sí, GroupDocs.Metadata admite una amplia gama de formatos de archivo, incluidas hojas de cálculo, documentos, presentaciones, imágenes y más.
### ¿Puedo modificar metadatos usando GroupDocs.Metadata para .NET?
Sí, no solo puedes leer sino también editar, actualizar y eliminar metadatos usando esta API.
### ¿Dónde puedo encontrar documentación detallada para GroupDocs.Metadata para .NET?
 La documentación detallada está disponible en[Documentación de GroupDocs.Metadata para .NET](https://reference.groupdocs.com/metadata/net/).
### ¿Cómo puedo obtener una licencia temporal para realizar pruebas?
 Puede solicitar una licencia temporal a[aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Existe un foro comunitario para soporte de GroupDocs.Metadata?
 Sí, puedes visitar el[Foro GroupDocs.Metadatos](https://forum.groupdocs.com/c/metadata/14) para apoyo y debates de la comunidad.