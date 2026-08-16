---
date: '2026-08-10'
description: Aprenda a extrair metadados EXIF de arquivos PSD usando GroupDocs.Metadata
  para Java. Este guia cobre extração básica, pacotes IFD, dados GPS e casos de uso
  reais.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Aprenda a extrair metadados EXIF de arquivos PSD usando GroupDocs.Metadata
  para Java. Guia passo a passo, trechos de código e dicas de solução de problemas
  para desenvolvedores.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Como extrair metadados EXIF de arquivos PSD com GroupDocs.Metadata
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
title: Como extrair metadados EXIF de arquivos PSD com GroupDocs.Metadata
type: docs
url: /pt/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Como extrair metadados EXIF de arquivos PSD com GroupDocs.Metadata

Extrair **metadados EXIF** de arquivos PSD é uma etapa rotineira, porém poderosa, quando você precisa auditar a procedência das imagens, automatizar a rotulagem de ativos ou criar bibliotecas de mídia pesquisáveis. Neste tutorial você descobrirá **como extrair EXIF** rapidamente com o GroupDocs.Metadata para Java, verá as chamadas de API exatas e aprenderá a lidar com pacotes IFD avançados e coordenadas GPS. Ao final, você estará pronto para integrar a extração de metadados em qualquer fluxo de trabalho baseado em Java.

## Respostas rápidas
A classe `Metadata` representa um arquivo e fornece acesso aos seus metadados.

- **Qual é a primeira linha de código?** `Metadata metadata = new Metadata("sample.psd");`
- **Qual método retorna o nome do artista?** `metadata.getExif().getArtist();`
- **Posso ler dados GPS?** Sim – use `metadata.getExif().getGpsInfo();`
- **Preciso de licença para produção?** É necessária uma licença válida do GroupDocs.Metadata após o período de avaliação.
- **Versão Java suportada?** Java 8 ou posterior (até Java 21).

## O que são metadados EXIF?
Os metadados EXIF (Exchangeable Image File Format) armazenam configurações da câmera, carimbos de data/hora de criação e dados de localização dentro dos arquivos de imagem. O GroupDocs.Metadata lê essas informações diretamente da estrutura binária dos arquivos PSD, expondo-as por meio de uma API Java limpa. Ele permite que desenvolvedores recuperem programaticamente detalhes como modelo da câmera, tempo de exposição e coordenadas GPS sem inspeção manual.

## Por que usar GroupDocs.Metadata para Java?
O GroupDocs.Metadata suporta **mais de 30 formatos de arquivo** (incluindo PSD, JPEG, PNG, TIFF) e pode processar arquivos de até **2 GB** sem carregar todo o documento na memória. A biblioteca extrai **mais de 150 tags EXIF distintas**, garantindo que você tenha o conjunto completo de atributos de câmera e GPS necessários para análises ou conformidade.

## Pré-requisitos
- **Java Development Kit (JDK) 8** ou mais recente instalado na sua máquina.  
- **Maven** para gerenciamento de dependências.  
- **GroupDocs.Metadata para Java versão 24.12** (ou mais recente).  
- Familiaridade básica com classes Java, objetos e tratamento de exceções.

### Bibliotecas e dependências necessárias
| Dependência | Coordenadas Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Configuração do ambiente
Você deve ter uma IDE compatível com Maven, como IntelliJ IDEA ou Eclipse. Crie um novo projeto Maven ou adicione a dependência a um projeto existente.

## Como configurar o GroupDocs.Metadata para Java
O GroupDocs.Metadata pode ser adicionado a um projeto Maven com algumas linhas de configuração. Os passos a seguir mostram como incluir o repositório e a dependência para que a biblioteca esteja disponível no classpath.

### Configuração Maven
Adicione o trecho a seguir ao seu `pom.xml` dentro da seção `<dependencies>`:

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

### Download direto
Alternativamente, faça o download do JAR mais recente na página oficial de lançamentos: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Aquisição de licença
Para usar a biblioteca além do período de avaliação de 30 dias, obtenha uma licença temporária ou completa:

1. Visite a [Página de Compra de Licença](https://purchase.groupdocs.com/temporary-license).  
2. Escolha **temporary** para teste ou **full** para produção.  
3. Siga as instruções na tela para incorporar o arquivo de licença (`metadata.lic`) ao classpath do seu Java.

### Inicialização e configuração básicas
Depois que a biblioteca estiver no classpath, inicialize-a como mostrado abaixo:

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

## Como extrair propriedades básicas de metadados EXIF de uma imagem PSD
Esta seção explica como carregar um arquivo PSD, acessar o contêiner EXIF e ler as tags mais comuns, como **artist**, **copyright** e **software**. O processo envolve criar uma instância `Metadata`, chamar `getExif()` e, em seguida, recuperar propriedades individuais com métodos getter simples.

### Implementação passo a passo
1. **Crie uma instância `Metadata`** apontando para o seu arquivo PSD.  
2. **Chame `getExif()`** para obter o contêiner EXIF.  
3. **Leia propriedades individuais** como `getArtist()`, `getCopyright()` e `getSoftware()`.  
4. **Imprima ou armazene** os valores de acordo com a lógica da sua aplicação.

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

> **Dica profissional:** O objeto `Metadata` detecta automaticamente o formato do arquivo, portanto você pode reutilizar o mesmo código para arquivos JPEG ou TIFF sem modificação.

## Como extrair propriedades do pacote EXIF IFD de uma imagem PSD
A seção IFD (Image File Directory) contém detalhes técnicos mais profundos, como **camera serial number**, **lens model** e **user comments**. `Ifd0` representa o diretório de arquivo de imagem primário que contém informações básicas da câmera. Extrair esses campos é útil para análise forense ou catalogação de alta precisão.

### Etapas de implementação
1. **Reutilize a instância `Metadata`** da seção anterior.  
2. **Navegue até o contêiner IFD** via `metadata.getExif().getIfd0()`.  
3. **Leia propriedades** como `getBodySerialNumber()` e `getUserComment()`.  
4. **Saída dos dados** ou mapeie-os para o seu modelo de domínio.

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

## Como recuperar dados GPS (latitude, longitude) de um arquivo PSD
Muitas câmeras modernas incorporam coordenadas GPS no bloco EXIF. `GpsInfo` contém coordenadas geográficas extraídas dos dados EXIF. Chame `metadata.getExif().getGpsInfo()` e então use `getLatitude()`, `getLongitude()` e `getAltitude()` para obter dados de localização precisos — sem necessidade de parsing adicional.

### Etapas detalhadas
1. **Obtenha o objeto de informações GPS**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Leia latitude e longitude**: `gps.getLatitude()` retorna um `double` em graus decimais.  
3. **Trate dados ausentes**: A API retorna `null` se a tag estiver ausente, portanto proteja contra `NullPointerException`.  

> **Armadilha comum:** Alguns arquivos PSD armazenam coordenadas GPS em números racionais; a biblioteca os normaliza automaticamente, mas arquivos mais antigos podem exigir conversão manual.  

## Problemas comuns e solução de problemas

| Sintoma | Causa provável | Correção |
|---------|----------------|----------|
| `Unsupported format` exception | Usando uma versão mais antiga do GroupDocs.Metadata que não reconhece PSD | Atualize para a versão 24.12 ou posterior |
| `NullPointerException` when calling `getArtist()` | Tag EXIF não presente no arquivo de origem | Verifique `metadata.getExif().hasArtist()` antes de ler |
| Erro de licença após 30 dias | Arquivo de licença não encontrado no classpath | Coloque `metadata.lic` em `src/main/resources` ou defina `Metadata.setLicense("path/to/license")` |

## Perguntas frequentes

**Q: Posso extrair metadados EXIF de um arquivo PSD protegido por senha?**  
A: Sim. Carregue o arquivo com `new Metadata("file.psd", "password")` e então acesse os dados EXIF normalmente.

**Q: O GroupDocs.Metadata suporta processamento em lote de muitos arquivos PSD?**  
A: Absolutamente. Instancie um objeto `Metadata` dentro de um loop, ou use o auxiliar `MetadataCollection` para processar diretórios de forma eficiente.

**Q: Quais versões do Java são oficialmente suportadas?**  
A: Java 8 até Java 21 são totalmente testadas. A biblioteca usa apenas APIs padrão, portanto funciona em qualquer JVM compatível.

**Q: É possível gravar dados EXIF de volta em um arquivo PSD?**  
A: Sim. Após modificar as propriedades via o objeto `Exif`, chame `metadata.save("output.psd")` para persistir as alterações.

**Q: Qual o tamanho máximo de um arquivo PSD que a biblioteca pode manipular sem ficar sem memória?**  
A: O GroupDocs.Metadata transmite dados e pode processar arquivos de até **2 GB** em uma máquina típica com 8 GB de RAM, graças à sua arquitetura de baixa memória.

## Conclusão
Agora você sabe **como extrair EXIF** metadados de arquivos PSD usando o GroupDocs.Metadata para Java, desde tags básicas até informações avançadas de IFD e GPS. Integre esses trechos ao seu pipeline de processamento de imagens para automatizar catalogação, verificações de conformidade ou serviços baseados em localização. Para uma exploração mais profunda, experimente extrair metadados de outros formatos suportados (JPEG, TIFF, PNG) ou experimente as capacidades de gravação para incorporar tags personalizadas.

---

**Last Updated:** 2026-08-10  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs

## Tutoriais Relacionados

- [Extrair recursos de imagem de arquivos PSD usando GroupDocs.Metadata em Java: Um guia abrangente](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Extrair cabeçalho PSD e informações de camada usando GroupDocs.Metadata para Java: Um guia abrangente](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Extrair propriedades MakerNote como tags TIFF/EXIF usando GroupDocs.Metadata em Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)