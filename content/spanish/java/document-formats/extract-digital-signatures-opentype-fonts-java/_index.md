---
date: '2026-06-22'
description: Aprenda cómo extraer la firma de fuente OpenType y los detalles de la
  firma digital de fuentes OpenType usando GroupDocs.Metadata para Java. Esta guía
  ayuda a proteger sus documentos.
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
title: Cómo extraer la firma de fuente OpenType en Java usando GroupDocs.Metadata
type: docs
url: /es/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Cómo extraer la firma de fuente OpenType en Java con GroupDocs.Metadata

En aplicaciones modernas, **extraer la firma de fuente OpenType** es esencial para confirmar la autenticidad de la fuente y proteger sus activos digitales. Este tutorial le muestra, paso a paso, cómo obtener tanto los indicadores de firma como los detalles criptográficos completos de una fuente OpenType usando **GroupDocs.Metadata para Java**. Ya sea que esté construyendo una canalización de contenido centrada en la seguridad o simplemente necesite auditar una biblioteca de fuentes, las técnicas a continuación harán que su flujo de trabajo sea fiable y rápido.

## Respuestas rápidas
- **¿Qué biblioteca necesito?** GroupDocs.Metadata para Java (v24.12)  
- **¿Qué versión de Java se requiere?** JDK 8 o posterior  
- **¿Necesito una licencia?** Una prueba gratuita funciona para evaluación; se requiere una licencia completa para producción  
- **¿Puedo procesar varias fuentes?** Sí – se admite el procesamiento por lotes o concurrente  
- **¿El código es thread‑safe?** Cree una nueva instancia `Metadata` por hilo; el objeto en sí no es thread‑safe  

## ¿Qué es una firma de fuente OpenType?
La **firma de fuente OpenType** es un bloque criptográfico incrustado dentro de la fuente que demuestra que el archivo no ha sido alterado desde que se firmó. Contiene la hora de la firma, la cadena de certificados, identificadores de algoritmos de hash e información opcional de revocación. También incluye un identificador de algoritmo de firma, la cadena de certificados del firmante y listas de revocación opcionales, lo que permite una verificación completa de la integridad y el origen de la fuente.

## ¿Por qué usar GroupDocs.Metadata para Java?
GroupDocs.Metadata admite **más de 50 formatos de entrada y salida** (incluidos DOCX, PDF, PPTX, HTML y numerosos tipos de imagen) y puede leer firmas OpenType sin cargar todo el archivo en memoria, lo que le permite procesar colecciones de fuentes de cientos de páginas de manera eficiente.

## Requisitos previos
- **Java Development Kit (JDK):** Versión 8 o más reciente.  
- **IDE:** Cualquier IDE compatible con Java (IntelliJ IDEA, Eclipse, VS Code, etc.).  
- **Maven:** Para la gestión de dependencias.  

### Bibliotecas y dependencias requeridas
Agregue las coordenadas de Maven de GroupDocs.Metadata a su `pom.xml`. Esto descargará el paquete exacto necesario para los ejemplos.

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
Alternativamente, descargue la última versión desde [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Obtención de licencia
- **Prueba gratuita:** Comience con una prueba gratuita para explorar las funciones.  
- **Licencia temporal:** Obtenga una licencia temporal a través de la [página de licencias de GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **Compra:** Para uso en producción, adquiera una licencia completa.

## Cómo extraer la firma de fuente OpenType usando GroupDocs.Metadata
La clase `Metadata` es la API central de GroupDocs.Metadata para acceder a los metadatos del documento sin cargar el archivo completo.  
Para leer la firma de una fuente, instancie un objeto `Metadata` con la ruta al archivo .otf y luego acceda a su `DigitalSignaturePackage`. Este enfoque carga solo las estructuras de metadatos necesarias, evitando el análisis completo de la fuente y manteniendo bajo el uso de memoria. La instancia `Metadata` debe usarse dentro de un bloque try‑with‑resources para garantizar una eliminación adecuada.

Cargue su archivo de fuente con `new Metadata("font.otf")` dentro de un bloque try‑with‑resources. La clase `Metadata` es el punto de entrada de GroupDocs.Metadata para leer cualquier tipo de documento compatible, incluidas las fuentes OpenType. El objeto se cierra automáticamente, evitando fugas de recursos.

### Cómo extraer los indicadores de firma digital
El objeto `DigitalSignaturePackage` agrupa toda la información relacionada con la firma de la fuente, incluidos los indicadores y las firmas individuales.  
**Respuesta directa:** Llame a `metadata.getDigitalSignaturePackage().getFlags()` después de abrir la fuente; el conjunto de indicadores devuelto le indica si la firma es válida, está revocada o tiene condiciones especiales. Esta única llamada le brinda una verificación rápida antes de profundizar en detalles. Los indicadores se representan como una enumeración que puede inspeccionarse para determinar el estado de la firma, la presencia de marca de tiempo y cualquier restricción de política aplicada durante la firma.

1. Inicialice la instancia `Metadata` apuntando a su archivo de fuente.  
2. Obtenga el `DigitalSignaturePackage`.  
3. Imprima o registre los valores de los indicadores.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Explicación**  
- `documentPath` – ruta absoluta o relativa al archivo de fuente OpenType.  
- El bloque try‑with‑resources garantiza que el objeto `Metadata` se cierre automáticamente, evitando fugas de memoria.

### Cómo extraer información detallada de la firma digital
`CmsSignature` representa una firma CMS/PKCS#7 individual incrustada en la fuente, proporcionando acceso a sus propiedades criptográficas.  
**Respuesta directa:** Itere sobre `metadata.getDigitalSignaturePackage().getSignatures()`; cada objeto `CmsSignature` expone la hora de la firma, algoritmos de digest, contenido encapsulado y detalles de los certificados, lo que le permite crear un informe de auditoría completo. Para cada firma puede obtener la cadena de certificados del firmante, verificar el algoritmo de hash y extraer cualquier token de marca de tiempo para confirmar cuándo se aplicó la firma.

1. Reutilice la misma inicialización de `Metadata` descrita arriba.  
2. Recorra cada `CmsSignature` en el paquete.  
3. Extraiga propiedades como `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()` y `getSignerInfo()`.

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

**Explicación de secciones clave**  
- **Sign Time:** Marca de tiempo cuando se aplicó la firma.  
- **Digest Algorithms & OIDs:** Algoritmos de hash utilizados (p. ej., SHA‑256).  
- **Encapsulated Content:** Cualquier dato adicional envuelto dentro de la firma.  
- **Certificates:** Fechas de validez y tamaño de datos sin procesar que ayudan a verificar la identidad del firmante.  
- **Signers:** Proporciona las opciones de algoritmo de cada firmante y sus marcas de tiempo.

#### Consejos de solución de problemas
- Si la fuente no tiene una firma digital, `getDigitalSignaturePackage()` devuelve `null`. Siempre verifique `null` antes de acceder a indicadores o firmas.  
- Asegúrese de usar la misma versión **GroupDocs.Metadata** que la definida en la dependencia Maven para evitar problemas de compatibilidad.  

## Aplicaciones prácticas
Extraer firmas de fuentes OpenType es valioso en muchos escenarios del mundo real:

1. **Verificación de documentos:** Automatice la comprobación de archivos de fuentes firmados en un sistema de gestión de contenido.  
2. **Gestión de activos digitales:** Valide la autenticidad de las fuentes antes de desplegarlas en proyectos de branding.  
3. **Auditorías de seguridad:** Revise los detalles de la firma para garantizar el cumplimiento de políticas internas de seguridad.  

## Consideraciones de rendimiento
- **Gestión de recursos:** Use try‑with‑resources para cerrar los objetos `Metadata` rápidamente.  
- **Procesamiento por lotes:** Procese fuentes en grupos para minimizar la sobrecarga de I/O; GroupDocs.Metadata puede manejar miles de archivos sin cargar cada fuente completa en memoria.  
- **Concurrencia:** Ejecute instancias separadas de `Metadata` en hilos paralelos para cargas de trabajo a gran escala; la biblioteca no es thread‑safe por instancia, por lo que cada hilo debe aislar su propia instancia.  

## Preguntas frecuentes

**P: ¿Puedo extraer firmas de una fuente que no tiene firma digital?**  
R: `DigitalSignaturePackage` será `null`; siempre verifique esta condición antes de acceder a indicadores o detalles.

**P: ¿Qué versión de GroupDocs.Metadata se requiere?**  
R: Los ejemplos están dirigidos a la versión **24.12**, pero las versiones más recientes siguen siendo compatibles con fuentes OpenType.

**P: ¿Necesito una licencia especial para leer firmas?**  
R: Una licencia de prueba funciona para evaluación; se requiere una licencia completa para uso en producción.

**P: ¿Cómo manejo fuentes almacenadas en un bucket de la nube?**  
R: Descargue la fuente a un archivo temporal local y luego pase su ruta a `Metadata`. La biblioteca funciona con cualquier archivo accesible mediante una ruta local.

**P: ¿Es posible verificar la validez criptográfica de la firma?**  
R: GroupDocs.Metadata suministra los datos crudos de la firma; puede pasar la cadena de certificados y los valores de hash a una biblioteca criptográfica separada para realizar una verificación completa.

## Conclusión
Al seguir esta guía, ahora sabe **cómo extraer la firma de fuente OpenType** y los datos detallados de la firma digital usando **GroupDocs.Metadata para Java**. Integrar estos pasos en sus aplicaciones refuerza la seguridad de los documentos, agiliza la validación de activos y respalda iniciativas de cumplimiento.

**Próximos pasos**  
- Experimente con el procesamiento por lotes para manejar bibliotecas de fuentes grandes de manera eficiente.  
- Combine los datos extraídos con sus herramientas de auditoría de seguridad para informes de cumplimiento automatizados.  
- Explore otras capacidades de metadatos de GroupDocs.Metadata, como la edición o eliminación de firmas cuando sea apropiado.

---

**Última actualización:** 2026-06-22  
**Probado con:** GroupDocs.Metadata 24.12  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Access Word Document Metadata with GroupDocs in Java&#58; A Comprehensive Guide](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [How to Extract Custom Metadata from PDFs Using GroupDocs.Metadata in Java&#58; A Comprehensive Guide](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)