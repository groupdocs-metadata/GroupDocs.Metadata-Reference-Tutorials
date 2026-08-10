---
date: '2026-08-10'
description: Aprenda cómo extraer metadatos EXIF de archivos PSD usando GroupDocs.Metadata
  para Java. Esta guía cubre la extracción básica, paquetes IFD, datos GPS y casos
  de uso del mundo real.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Aprenda cómo extraer metadatos EXIF de archivos PSD usando GroupDocs.Metadata
  para Java. Esta guía cubre la extracción básica, paquetes IFD, datos GPS y casos
  de uso del mundo real.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Cómo extraer metadatos EXIF de archivos PSD con GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: Cómo extraer metadatos EXIF de archivos PSD con GroupDocs.Metadata
type: docs
url: /es/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Cómo extraer metadatos EXIF de archivos PSD con GroupDocs.Metadata

Extraer **metadatos EXIF** de archivos PSD es un paso rutinario pero poderoso cuando necesitas auditar la procedencia de imágenes, automatizar el etiquetado de activos o crear bibliotecas de medios buscables. En este tutorial descubrirás **cómo extraer EXIF** rápidamente con GroupDocs.Metadata para Java, verás las llamadas exactas a la API y aprenderás a manejar paquetes IFD avanzados y coordenadas GPS. Al final estarás listo para integrar la extracción de metadatos en cualquier flujo de trabajo basado en Java.

## Respuestas rápidas
La clase `Metadata` representa un archivo y proporciona acceso a sus metadatos.

- **¿Cuál es la primera línea de código?** `Metadata metadata = new Metadata("sample.psd");`
- **¿Qué método devuelve el nombre del artista?** `metadata.getExif().getArtist();`
- **¿Puedo leer datos GPS?** Yes – use `metadata.getExif().getGpsInfo();`
- **¿Necesito una licencia para producción?** A valid GroupDocs.Metadata license is required beyond the trial period.
- **¿Versión de Java compatible?** Java 8 o posterior (hasta Java 21).

## Qué son los metadatos EXIF?
Los metadatos EXIF (Exchangeable Image File Format) almacenan la configuración de la cámara, marcas de tiempo de creación y datos de ubicación dentro de los archivos de imagen. GroupDocs.Metadata lee esta información directamente de la estructura binaria de los archivos PSD, exponiéndola a través de una API Java limpia. Permite a los desarrolladores recuperar programáticamente detalles como el modelo de cámara, tiempo de exposición y coordenadas GPS sin inspección manual.

## ¿Por qué usar GroupDocs.Metadata para Java?
GroupDocs.Metadata admite **más de 30 formatos de archivo** (incluidos PSD, JPEG, PNG, TIFF) y puede procesar archivos de hasta **2 GB** sin cargar todo el documento en memoria. La biblioteca extrae **más de 150 etiquetas EXIF distintas**, garantizando que dispones del conjunto completo de atributos de cámara y GPS necesarios para análisis o cumplimiento.

## Requisitos previos
- **Java Development Kit (JDK) 8** o una versión más reciente instalada en tu máquina.  
- **Maven** para la gestión de dependencias.  
- **GroupDocs.Metadata para Java versión 24.12** (o más reciente).  
- Familiaridad básica con clases, objetos y manejo de excepciones en Java.

### Bibliotecas y dependencias requeridas
| Dependencia | Coordenadas Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Configuración del entorno
Debes contar con un IDE compatible con Maven, como IntelliJ IDEA o Eclipse. Crea un nuevo proyecto Maven o agrega la dependencia a uno existente.

## Cómo configurar GroupDocs.Metadata para Java
GroupDocs.Metadata puede agregarse a un proyecto Maven con unas pocas líneas de configuración. Los pasos siguientes muestran cómo incluir el repositorio y la dependencia para que la biblioteca esté disponible en el classpath.

### Configuración de Maven
Agrega el siguiente fragmento a tu `pom.xml` dentro de la sección `<dependencies>`:

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

### Descarga directa
Alternatively, download the latest JAR from the official releases page: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Obtención de licencia
To run the library beyond the 30‑day trial, obtain a temporary or full license:

1. Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Choose **temporary** for testing or **full** for production.  
3. Follow the on‑screen instructions to embed the license file (`metadata.lic`) in your Java classpath.

### Inicialización y configuración básica
After the library is on the classpath, initialize it as shown below:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Cómo extraer propiedades básicas de metadatos EXIF de una imagen PSD
Esta sección explica cómo cargar un archivo PSD, acceder al contenedor EXIF y leer las etiquetas más comunes como **artist**, **copyright** y **software**. El proceso implica crear una instancia `Metadata`, llamar a `getExif()` y luego obtener propiedades individuales con simples métodos getter.

### Implementación paso a paso
1. **Create a `Metadata` instance** pointing at your PSD file.  
2. **Call `getExif()`** to obtain the EXIF container.  
3. **Read individual properties** like `getArtist()`, `getCopyright()`, and `getSoftware()`.  
4. **Print or store** the values according to your application logic.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Consejo profesional:** El objeto `Metadata` detecta automáticamente el formato del archivo, por lo que puedes reutilizar el mismo código para archivos JPEG o TIFF sin modificaciones.

## Cómo extraer propiedades del paquete EXIF IFD de una imagen PSD
La sección IFD (Image File Directory) contiene detalles técnicos más profundos como **camera serial number**, **lens model** y **user comments**. `Ifd0` representa el directorio de archivo de imagen primario que contiene información básica de la cámara. Extraer estos campos es útil para análisis forense o catalogación de alta precisión.

### Pasos de implementación
1. **Reuse the `Metadata` instance** from the previous section.  
2. **Navigate to the IFD container** via `metadata.getExif().getIfd0()`.  
3. **Read properties** like `getBodySerialNumber()` and `getUserComment()`.  
4. **Output the data** or map it to your domain model.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Cómo obtener datos GPS (latitud, longitud) de un archivo PSD
Many modern cameras embed GPS coordinates in the EXIF block. `GpsInfo` holds geographic coordinates extracted from EXIF data. Call `metadata.getExif().getGpsInfo()` and then use `getLatitude()`, `getLongitude()`, and `getAltitude()` to obtain precise location data—no additional parsing required.

### Pasos detallados
1. **Obtain the GPS info object**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Read latitude and longitude**: `gps.getLatitude()` returns a `double` in decimal degrees.  
3. **Handle missing data**: The API returns `null` if the tag is absent, so guard against `NullPointerException`.  

> **Trampa común:** Algunos archivos PSD almacenan coordenadas GPS en números racionales; la biblioteca los normaliza automáticamente, pero los archivos más antiguos pueden requerir conversión manual.

## Problemas comunes y solución de errores

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| `Unsupported format` exception | Using an older GroupDocs.Metadata version that doesn’t recognise PSD | Upgrade to version 24.12 or later |
| `NullPointerException` when calling `getArtist()` | EXIF tag not present in the source file | Check `metadata.getExif().hasArtist()` before reading |
| License error after 30 days | License file not found on the classpath | Place `metadata.lic` in `src/main/resources` or set `Metadata.setLicense("path/to/license")` |

## Preguntas frecuentes

**Q: ¿Puedo extraer metadatos EXIF de un archivo PSD protegido con contraseña?**  
A: Sí. Carga el archivo con `new Metadata("file.psd", "password")` y luego accede a los datos EXIF como de costumbre.

**Q: ¿GroupDocs.Metadata admite el procesamiento por lotes de muchos archivos PSD?**  
A: Absolutamente. Instancia un objeto `Metadata` dentro de un bucle, o usa el asistente `MetadataCollection` para procesar directorios de forma eficiente.

**Q: ¿Qué versiones de Java son oficialmente compatibles?**  
A: Java 8 through Java 21 are fully tested. The library uses only standard APIs, so it works on any compliant JVM.

**Q: ¿Es posible escribir datos EXIF de vuelta en un archivo PSD?**  
A: Sí. After modifying properties via the `Exif` object, call `metadata.save("output.psd")` to persist changes.

**Q: ¿Qué tamaño de archivo PSD puede manejar la biblioteca sin quedarse sin memoria?**  
A: GroupDocs.Metadata streams data and can process files up to **2 GB** on a typical 8 GB RAM machine, thanks to its low‑memory architecture.

## Conclusión
Ahora sabes **cómo extraer EXIF** metadata from PSD files using GroupDocs.Metadata for Java, from basic tags to advanced IFD and GPS information. Integrate these snippets into your image‑processing pipeline to automate cataloguing, compliance checks, or location‑based services. For deeper exploration, try extracting metadata from other supported formats (JPEG, TIFF, PNG) or experiment with the write‑back capabilities to embed custom tags.

---

**Última actualización:** 2026-08-10  
**Probado con:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Extraer recursos de imagen de archivos PSD usando GroupDocs.Metadata en Java: Guía completa](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Extraer encabezado y información de capas PSD usando GroupDocs.Metadata para Java: Guía completa](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Extraer propiedades MakerNote como etiquetas TIFF/EXIF usando GroupDocs.Metadata en Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)