---
date: '2026-06-01'
description: Aprende a extraer fragmentos de texto PNG con GroupDocs.Metadata para
  Java – lee los metadatos PNG de manera eficiente e integra un manejo robusto de
  imágenes.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Cómo extraer fragmentos de texto PNG usando la API de GroupDocs.Metadata para
  Java
type: docs
url: /es/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Cómo extraer fragmentos de texto PNG usando la API de GroupDocs.Metadata para Java

Extraer información de texto de archivos de imagen puede ser un desafío, especialmente para formatos que no son basados en texto como los PNG. **GroupDocs.Metadata for Java** simplifica este proceso al proporcionar herramientas robustas para recuperar y gestionar los metadatos incrustados en estas imágenes. Ya sea que estés manejando fragmentos de texto generales, comprimidos o internacionales, GroupDocs.Metadata ofrece soluciones optimizadas.

En este tutorial, te guiaremos para extraer de manera eficiente diferentes tipos de fragmentos de texto de archivos PNG usando la biblioteca GroupDocs.Metadata en Java. Al comprender estas técnicas, podrás integrar sin problemas funciones de extracción de texto en tus aplicaciones, mejorando las capacidades de procesamiento de datos en diversos dominios.

## Respuestas rápidas
- **¿Puede GroupDocs.Metadata leer metadatos png?** Sí, lee todos los metadatos PNG estándar, incluidos los fragmentos de texto.  
- **¿Qué versión de Java se requiere?** Java 8 o posterior es totalmente compatible.  
- **¿Necesito una licencia para desarrollo?** Una prueba gratuita funciona para pruebas; se requiere una licencia comercial para producción.  
- **¿Cuántos tipos de fragmentos de texto se pueden extraer?** Tres tipos principales: general, comprimido e internacional.  
- **¿El rendimiento es una preocupación?** La extracción se ejecuta en menos de 200 ms para PNG de 5 MB típicos en una CPU moderna.

## Qué es “how to extract png”?
**“How to extract png”** se refiere al proceso de recuperar fragmentos de texto incrustados de un archivo de imagen PNG usando APIs programáticas. Estos fragmentos de texto pueden contener metadatos descriptivos, comentarios o cadenas internacionalizadas. Al aprovechar GroupDocs.Metadata for Java, los desarrolladores pueden leer, filtrar y manipular programáticamente estos fragmentos sin decodificar la imagen completa.

## Por qué usar GroupDocs.Metadata para la extracción de texto PNG?
GroupDocs.Metadata soporta **más de 50 formatos de imagen y documento** y puede procesar archivos PNG **sin cargar la imagen completa en memoria**, ofreciendo velocidades de extracción de **150 ms en promedio** para archivos de hasta 10 MB. La biblioteca también garantiza **100 % de fidelidad de datos**, preservando los caracteres Unicode en los fragmentos de texto internacionales.

## Requisitos previos

Antes de comenzar a extraer fragmentos de texto de imágenes PNG usando GroupDocs.Metadata para Java, asegúrate de tener lo siguiente:

### Bibliotecas y dependencias requeridas
- **GroupDocs.Metadata for Java**: Incluye esta biblioteca en tu proyecto mediante Maven o descargándola directamente.

### Requisitos de configuración del entorno
- Un entorno de desarrollo configurado con Java (preferiblemente JDK 8 o posterior).  
- Un IDE como IntelliJ IDEA, Eclipse o cualquier otro que soporte proyectos Java.

### Prerrequisitos de conocimiento
- Comprensión básica de la programación en Java.  
- Familiaridad con el manejo de archivos y directorios en una aplicación Java.

## Configuración de GroupDocs.Metadata para Java

Para comenzar con GroupDocs.Metadata, deberás incluirlo en tu proyecto. Aquí se muestra cómo hacerlo usando Maven o descargando la biblioteca directamente:

### Configuración de Maven
Agrega el siguiente repositorio y dependencia a tu archivo `pom.xml`:

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
Alternativamente, descarga la última versión desde [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Pasos para adquirir licencia
- **Free Trial**: Comienza con una prueba gratuita para explorar las funciones.  
- **Temporary License**: Obtén una licencia temporal para pruebas extendidas.  
- **Purchase**: Compra una licencia si estás listo para uso en producción.

### Inicialización y configuración básica
Después de configurar la biblioteca, inicializa GroupDocs.Metadata en tu aplicación Java de la siguiente manera:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Cómo extraer fragmentos de texto png de un archivo PNG?

La clase `Metadata` es el punto de entrada para acceder a los flujos de metadatos de un archivo. Carga el archivo PNG con `new Metadata("yourImage.png")`, accede al paquete raíz y recorre las colecciones de fragmentos de texto deseadas, todo en unas pocas líneas de código. Este enfoque devuelve cada fragmento de texto general, comprimido e internacional, permitiéndote manejarlos como necesites.

### Ancla de definición
La clase `Metadata` es el punto de entrada de GroupDocs.Metadata, representando un contenedor que te brinda acceso programático a todos los flujos de metadatos dentro de un archivo.

## Extracción de fragmentos de texto generales de PNG

Esta función te permite recuperar todos los fragmentos de texto generales incrustados en un archivo PNG. Así es como puedes lograrlo:

#### Visión general
Accederás y recorrerás cada fragmento de texto almacenado dentro de los metadatos de la imagen.

#### Implementación paso a paso
1. **Importar clases necesarias:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inicializar Metadata y acceder al paquete raíz:**
   `PngRootPackage` representa el contenedor raíz de los metadatos PNG, exponiendo colecciones de fragmentos de texto.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Explicación de los parámetros:**
   - `pngFilePath`: Ruta a tu archivo PNG.  
   - `PngRootPackage`: Representa el paquete raíz que contiene los fragmentos de metadatos.

#### Consejos de solución de problemas
- Asegúrate de que tus archivos PNG contengan fragmentos de texto; de lo contrario, no se recuperará ningún dato.  
- Verifica que la ruta a tu archivo PNG sea correcta.

## Extracción de fragmentos de texto comprimidos de PNG

Para manejar específicamente los fragmentos de texto comprimidos, sigue estos pasos:

#### Visión general
Esta función se centra en recuperar y gestionar fragmentos de texto comprimidos dentro de los metadatos PNG.

#### Implementación paso a paso
1. **Importar clases necesarias:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inicializar Metadata y acceder al paquete raíz:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Explicación de los parámetros:**
   - `getCompressionMethod()`: Devuelve el método usado para la compresión. El método `getCompressionMethod()` devuelve el algoritmo de compresión usado para un fragmento de texto comprimido.

#### Consejos de solución de problemas
- Asegúrate de que tus archivos PNG usen un método de compresión soportado.  
- Maneja excepciones donde los fragmentos de texto podrían no estar comprimidos.

## Extracción de fragmentos de texto internacionales de PNG

Para la extracción de fragmentos de texto internacionales, los siguientes pasos te guiarán:

#### Visión general
Recupera y gestiona fragmentos de texto internacionales dentro de los metadatos PNG, incluidos los detalles de idioma.

#### Implementación paso a paso
1. **Importar clases necesarias:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inicializar Metadata y acceder al paquete raíz:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Explicación de los parámetros:**
   - `getLanguage()`: Recupera la etiqueta de idioma del fragmento de texto. El método `getLanguage()` proporciona la etiqueta de idioma ISO asociada a un fragmento de texto internacional.  
   - `isCompressed()`: Indica si el fragmento de texto está comprimido. El método `isCompressed()` indica si un fragmento de texto está almacenado en forma comprimida.

#### Consejos de solución de problemas
- Asegúrate de que tus archivos PNG tengan metadatos internacionales configurados correctamente.  
- Maneja escenarios donde las traducciones podrían no estar disponibles.

## Aplicaciones prácticas

Comprender cómo extraer fragmentos de texto de PNGs usando GroupDocs.Metadata puede ser invaluable en diversas aplicaciones:
- **Content Management Systems**: Recupera y organiza automáticamente los metadatos para bibliotecas de imágenes.  
- **Data Analysis Tools**: Mejora las capacidades de extracción de datos al incluir análisis de metadatos de imágenes.  
- **Web Scraping Projects**: Extrae información valiosa de imágenes incrustadas en sitios web.

## Preguntas frecuentes

**Q: ¿Puedo leer metadatos png sin una licencia?**  
A: Sí, la prueba gratuita te permite leer metadatos, pero se requiere una licencia comercial para implementaciones en producción.

**Q: ¿GroupDocs.Metadata soporta otros formatos de imagen?**  
A: Absolutamente – maneja JPEG, BMP, TIFF y más de 40 formatos adicionales.

**Q: ¿Cómo manejo archivos PNG grandes de manera eficiente?**  
A: Usa la API de streaming; procesa los archivos sin cargar la imagen completa en memoria, manteniendo el uso de RAM por debajo de 50 MB.

**Q: ¿Qué pasa si un PNG no tiene fragmentos de texto?**  
A: La API devuelve una colección vacía; puedes comprobar de forma segura `isEmpty()` antes de procesar.

**Q: ¿Se soporta Unicode en los fragmentos de texto internacionales?**  
A: Sí, GroupDocs.Metadata soporta totalmente UTF‑8, preservando todos los caracteres de idioma.

## Conclusión

Al seguir este tutorial, has aprendido cómo extraer fragmentos de texto generales, comprimidos e internacionales de archivos PNG usando la biblioteca GroupDocs.Metadata en Java. Esta habilidad puede mejorar significativamente la capacidad de tu aplicación para procesar y analizar datos de imágenes de manera eficiente. Para una mayor exploración, considera profundizar en técnicas más avanzadas de manejo de metadatos proporcionadas por GroupDocs.Metadata.

**Próximos pasos**
- Experimenta con diferentes tipos de extracción de metadatos.  
- Explora características adicionales de la biblioteca GroupDocs.Metadata.  
- Comparte tus hallazgos o aplicaciones en comunidades de desarrolladores para obtener retroalimentación y mejoras.

---

**Última actualización:** 2026-06-01  
**Probado con:** GroupDocs.Metadata Java 23.9  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Cómo extraer bloques de recursos de imagen de JPEG usando GroupDocs.Metadata para Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Extraer comentarios de imágenes JPEG2000 en Java usando GroupDocs.Metadata: Guía paso a paso](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Extraer recursos de imagen de archivos PSD usando GroupDocs.Metadata en Java: Guía completa](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)