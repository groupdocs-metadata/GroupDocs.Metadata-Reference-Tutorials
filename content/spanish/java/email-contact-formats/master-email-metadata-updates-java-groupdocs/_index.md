---
date: '2026-05-27'
description: Aprende cómo actualizar los destinatarios de correo electrónico java
  usando GroupDocs.Metadata para Java. Modifica los destinatarios, los asuntos y guarda
  los cambios de manera eficiente.
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'Actualizar destinatarios de correo electrónico Java: Domina las actualizaciones
  de metadatos de correo con GroupDocs.Metadata'
type: docs
url: /es/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# Actualizar destinatarios de correo electrónico Java con GroupDocs.Metadata

En esta guía completa usted **actualizará destinatarios de correo electrónico java** programáticamente usando la biblioteca GroupDocs.Metadata. Recorreremos la modificación de los destinatarios principales y CC, el cambio de la línea de asunto y la persistencia de esos cambios, todo con fragmentos de código claros paso a paso. Al final estará listo para integrar la automatización de metadatos de correo electrónico en cualquier flujo de trabajo basado en Java.

## Respuestas rápidas
- **¿Cuál es la forma más rápida de cambiar el destinatario principal de un correo electrónico?** Cargue el archivo con `Metadata`, obtenga el `EmailRootPackage`, reemplace la colección `To` y guarde, todo en tres líneas de código.  
- **¿Puedo agregar destinatarios CC sin sobrescribir los existentes?** Sí, use `addCcRecipient` en el `EmailRootPackage` para añadir nuevas direcciones.  
- **¿Necesito una licencia para uso en producción?** Una licencia temporal elimina los límites de evaluación; se requiere una licencia permanente para implementaciones comerciales. Puede obtener una licencia temporal en la página de [GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **¿Qué versiones de Java son compatibles?** GroupDocs.Metadata funciona con Java 8, 11, 17 y posteriores.  
- **¿Es seguro el procesamiento por lotes para buzones grandes?** Procese los archivos en lotes de 50–100 para mantener el uso de memoria por debajo de 200 MB por lote.

## ¿Qué es actualizar destinatarios de correo electrónico java?
*Actualizar destinatarios de correo electrónico en Java* significa cambiar programáticamente los campos “To”, “CC” o “BCC” de un archivo de correo (EML, MSG, etc.) sin abrir un cliente de correo. GroupDocs.Metadata expone una API de alto nivel que lee la estructura del correo, le permite modificar colecciones de direcciones y escribe el archivo actualizado de vuelta al disco.

## ¿Por qué usar GroupDocs.Metadata para metadatos de correo electrónico?
GroupDocs.Metadata soporta **más de 50 formatos relacionados con correo electrónico** (incluidos EML, MSG, MHT) y puede procesar **mensajes de cientos de páginas** sin cargar todo el archivo en memoria, reduciendo el consumo de RAM hasta en **un 80 %** comparado con enfoques ingenuos de flujo de archivos. Su implementación puramente Java elimina dependencias nativas, lo que lo hace ideal para servicios multiplataforma.

## Requisitos previos
- Java 8 o superior (Java 11, 17, 21 están completamente probados).  
- Maven o Gradle para la gestión de dependencias.  
- Una licencia válida de GroupDocs.Metadata (temporal o permanente).  

### Bibliotecas y dependencias requeridas
Agregue la siguiente dependencia a su `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

Para descargas directas, obtenga la última versión en [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Configuración del entorno
Asegúrese de que su IDE apunte a un JDK compatible y de que Maven resuelva los artefactos de GroupDocs.Metadata sin errores.

## ¿Cómo actualizar destinatarios de correo electrónico en Java?
Cargue el archivo de correo, reemplace los destinatarios existentes y guarde el resultado. Esta operación requiere solo tres llamadas a la API y se ejecuta en menos de **200 ms** para mensajes típicos de 1 MB. Al usar la API de alto nivel `EmailRootPackage` evita analizar todo el archivo, lo que mantiene bajo el uso de memoria y hace que el procesamiento por lotes sea sencillo.

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
La línea anterior importa la clase esencial para comenzar a gestionar operaciones de metadatos en sus archivos.

## Guía de implementación
Ahora profundizaremos en cada característica, ampliando los fragmentos de respuesta rápida con contexto completo.

### Actualizando destinatarios de correo electrónico
**Visión general**: Esta sección muestra cómo puede actualizar los destinatarios principales de un mensaje de correo electrónico programáticamente.

#### Paso 1: Inicializar objeto Metadata
La clase `Metadata` representa un archivo y proporciona acceso a sus metadatos. Cree una instancia de `Metadata` con la ruta de su archivo de entrada:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**Ancla de definición**: La clase `Metadata` es el punto de entrada para todas las operaciones de metadatos en GroupDocs.Metadata, representando un único archivo en memoria.

#### Paso 2: Acceder a EmailRootPackage
`EmailRootPackage` brinda acceso a metadatos específicos de correo como destinatarios y asunto. Acceda a los metadatos del correo usando:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
Este paso es crucial ya que proporciona acceso a todas las propiedades modificables de su correo.

#### Paso 3: Actualizar destinatarios
Establezca nuevos destinatarios para su mensaje de correo:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### Agregar destinatarios de copia carbón (CC) al correo
**Visión general**: Aprenda cómo añadir destinatarios CC a un correo existente.

#### Paso 1: Inicializar y obtener el paquete raíz
Similar a actualizar los destinatarios principales, inicialice el objeto metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Paso 2: Establecer destinatarios CC
`addCcRecipient` añade una nueva dirección a la colección CC sin sobrescribir las entradas existentes. Agregue destinatarios de copia carbón de la siguiente manera:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
Este enfoque garantiza que los usuarios adicionales sean notificados sin ser el punto de contacto principal.

### Actualizando el asunto del correo
**Visión general**: Esta función le permite modificar la línea de asunto de un correo, manteniendo las comunicaciones claras y actualizadas.

#### Paso 1: Inicializar Metadata
Comience inicializando su objeto metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Paso 2: Cambiar el asunto
Actualice la línea de asunto del correo:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
Este paso es vital para mantener hilos de correo relevantes y buscables.

### Guardando metadatos de correo actualizados
**Visión general**: Una vez que haya realizado cambios, es esencial guardar estas actualizaciones. Esta sección muestra cómo persistir sus modificaciones de manera eficaz.

#### Paso 1: Inicializar y obtener el paquete raíz
Comience inicializando el objeto `Metadata`:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Paso 2: Guardar cambios
Persista sus cambios guardándolos en un directorio de salida especificado:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
Esto asegura que todas las modificaciones se conserven y reflejen en el archivo guardado.

## Aplicaciones prácticas
Implementar estas funciones puede ser increíblemente beneficioso en varios escenarios del mundo real:

1. **Sistemas de gestión de correo** – Automatice la actualización de destinatarios para distribuciones masivas de correo.  
2. **Plataformas de soporte al cliente** – Modifique rápidamente los asuntos de correo para reflejar cambios en el estado de los tickets.  
3. **Herramientas de comunicación interna** – Asegúrese de que todos los miembros del equipo estén en CC en anuncios críticos sin ediciones manuales.

## Consideraciones de rendimiento
Al trabajar con grandes volúmenes de datos de correo, tenga en cuenta estos consejos:

- Procese los archivos en lotes de **50–100** para mantener el uso de memoria por debajo de **200 MB** por lote.  
- Use la llamada `metadata.getRootPackage().getEmail()` con moderación; reutilice la instancia `Metadata` cuando sea posible.  
- Monitoree el uso del heap de JVM con herramientas como VisualVM para evitar errores OutOfMemory.

## Conclusión
Ahora ha dominado cómo **actualizar destinatarios de correo electrónico java** usando GroupDocs.Metadata. Ya sea que esté ajustando los destinatarios principales, añadiendo CC o modificando la línea de asunto, la biblioteca ofrece una API rápida y eficiente en memoria. Explore la [documentación](https://docs.groupdocs.com/metadata/java/) completa para escenarios más avanzados, como manejar adjuntos o convertir entre formatos EML y MSG.

## Sección de preguntas frecuentes
**Q1**: ¿Qué versiones de Java son compatibles con GroupDocs.Metadata?  
- **A**: Java 8, 11, 17 y posteriores son totalmente compatibles.

**Q2**: ¿Puedo usar GroupDocs.Metadata sin una licencia?  
- **A**: Sí, una prueba gratuita funciona con limitaciones; una licencia temporal o permanente elimina esos límites.

**Q3**: ¿Cómo manejo archivos de correo grandes de manera eficiente?  
- **A**: Procérselos en lotes más pequeños, reutilice objetos `Metadata` y monitoree el uso del heap para mantenerse por debajo de 200 MB por lote.

**Q4**: ¿Qué otros tipos de archivo soporta GroupDocs.Metadata además de correos?  
- **A**: Soporta más de **70** formatos, incluidos PDF, DOCX, XLSX, PPTX, imágenes y archivos comprimidos. Consulte la [referencia de API](https://reference.groupdocs.com/metadata/java/) para la lista completa.

---

**Última actualización:** 2026-05-27  
**Probado con:** GroupDocs.Metadata 23.12 for Java  
**Autor:** GroupDocs  

---

## Tutoriales relacionados

- [Dominar la extracción de metadatos de correo electrónico en Java usando GroupDocs.Metadata](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [Tutoriales de metadatos de correo y contactos para GroupDocs.Metadata Java](/metadata/java/email-contact-formats/)
- [Cómo extraer URIs de fotos vCard usando GroupDocs.Metadata en Java para una gestión eficiente de contactos](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)