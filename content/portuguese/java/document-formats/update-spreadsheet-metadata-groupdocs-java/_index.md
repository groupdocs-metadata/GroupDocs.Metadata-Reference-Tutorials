---
date: '2026-03-22'
description: Aprenda como alterar a data de criação do Excel e atualizar os metadados
  do Excel usando o GroupDocs.Metadata para Java. Siga este guia passo a passo para
  adicionar palavras‑chave ao Excel e modificar as propriedades do documento.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Alterar a data de criação do Excel usando GroupDocs.Metadata em Java
type: docs
url: /pt/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Alterar a Data de Criação do Excel Usando GroupDocs.Metadata em Java

Em ambientes modernos orientados a dados, **alterar a data de criação do Excel** e manter outros metadados atualizados pode melhorar drasticamente a organização de documentos, a capacidade de busca e a conformidade. Seja lidando com relatórios financeiros, rastreadores de projetos ou dados de arquivo, metadados precisos garantem que as pessoas certas encontrem os arquivos corretos no momento certo. Este tutorial orienta você a usar a biblioteca GroupDocs.Metadata para **alterar a data de criação do Excel**, **adicionar palavras‑chave ao Excel** e **modificar as propriedades do documento Excel** em uma aplicação Java.

## Respostas Rápidas
- **Posso alterar a data de criação de um arquivo Excel?** Sim, usando `setCreatedTime` do GroupDocs.Metadata.  
- **Qual biblioteca suporta a atualização de metadados do Excel em Java?** GroupDocs.Metadata para Java.  
- **Preciso de uma licença?** Uma avaliação gratuita funciona para testes; uma licença permanente é necessária para produção.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.  
- **Posso adicionar palavras‑chave personalizadas a uma pasta de trabalho Excel?** Absolutamente—use `setKeywords` nas propriedades do documento.

## O que significa “alterar a data de criação do Excel”?
Alterar a data de criação do Excel significa atualizar a propriedade *Created* incorporada armazenada dentro do arquivo da pasta de trabalho. Essa propriedade faz parte dos metadados padrão do Office Open XML e pode ser editada programaticamente sem alterar o conteúdo real das planilhas.

## Por que usar GroupDocs.Metadata para metadados do Excel?
GroupDocs.Metadata oferece uma API de alto nível e tipada que abstrai o manuseio de XML de baixo nível exigido pelo formato Office Open XML. Ela permite:

- **Atualizar propriedades principais** como autor, empresa e data de criação em uma única chamada.  
- **Adicionar palavras‑chave ao Excel** para melhorar os resultados de busca no SharePoint, OneDrive ou sistemas de arquivos locais.  
- **Modificar propriedades do documento Excel** sem abrir a pasta de trabalho no Excel, economizando tempo e recursos.  

## Pré‑requisitos
- Java Development Kit (JDK) 8 ou mais recente.  
- Uma IDE como IntelliJ IDEA ou Eclipse.  
- Familiaridade básica com I/O de arquivos em Java.  

## Configurando GroupDocs.Metadata para Java

### Instalação

Adicione o repositório Maven do GroupDocs.Metadata e a dependência ao seu `pom.xml`:

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

Como alternativa, você pode [baixar a versão mais recente diretamente](https://releases.groupdocs.com/metadata/java/) se preferir uma configuração manual.

### Aquisição de Licença

GroupDocs oferece uma avaliação gratuita para testes. Para uso em produção, obtenha uma licença temporária ou permanente do fornecedor. Visite a [página de compra da GroupDocs](https://purchase.groupdocs.com/temporary-license/) para mais detalhes.

#### Inicialização Básica

Importe as classes necessárias no seu arquivo fonte Java:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implementação Passo a Passo

### Etapa 1: Abrir a Pasta de Trabalho Excel

Forneça o caminho para a pasta de trabalho de origem e crie uma instância `Metadata`. O bloco `try‑with‑resources` garante que o manipulador de arquivo seja fechado automaticamente.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Etapa 2: Atualizar Propriedades de Metadados Incorporadas

Agora você pode **alterar a data de criação do Excel**, definir autor, empresa, categoria e **adicionar palavras‑chave ao Excel**. A chamada `new Date()` captura o timestamp atual, mas você pode fornecer qualquer `java.util.Date` que precisar.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Dica profissional:** Use uma convenção de nomenclatura consistente para palavras‑chave (por exemplo, `project:Q2, finance, confidential`) para tornar buscas futuras mais eficazes.

### Etapa 3: Salvar a Pasta de Trabalho Atualizada

Especifique um caminho de saída e persista as alterações. O arquivo original permanece intacto, o que é útil para trilhas de auditoria.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Problemas Comuns e Soluções

| Problema | Por que Acontece | Solução |
|----------|------------------|---------|
| **Erros de caminho de arquivo** | Caminhos relativos/absolutos incorretos | Verifique `inputFilePath` e `outputFilePath`. Use `Paths.get(...)` para caminhos independentes da plataforma. |
| **Versão incompatível da biblioteca** | Uso de uma versão antiga do GroupDocs.Metadata que não suporta o método `setCreatedTime` | Atualize para a versão mais recente (conforme o snippet Maven). |
| **Licença ausente** | Período de avaliação expirado | Aplique uma licença temporária ou adquira uma licença completa via página de compra. |
| **Uso excessivo de memória em pastas de trabalho grandes** | Carregar arquivos Excel massivos consome heap | Processar arquivos em lotes e aumentar o heap da JVM (`-Xmx`) se necessário. |

## Perguntas Frequentes

**P: Quais versões do Java são suportadas pelo GroupDocs.Metadata?**  
R: Java 8 e versões posteriores são totalmente suportadas.

**P: Como devo tratar exceções ao atualizar metadados?**  
R: Envolva o código em um bloco `try‑catch` e registre `MetadataException` para capturar erros de I/O ou de formato.

**P: Posso atualizar vários arquivos Excel em uma única execução?**  
R: Sim, itere sobre uma coleção de caminhos de arquivo, mas monitore o uso de memória para lotes grandes.

**P: É possível reverter as alterações feitas nos metadados?**  
R: Mantenha um backup da pasta de trabalho original antes de aplicar as atualizações e restaure‑o se necessário.

**P: Onde posso encontrar documentação mais detalhada?**  
R: Consulte o guia oficial em [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Aplicações Práticas

1. **Auditorias Financeiras** – Registre quem modificou a planilha e quando, fornecendo uma trilha de auditoria.  
2. **Gestão de Projetos** – Marque planilhas com palavras‑chave específicas do projeto para recuperação rápida.  
3. **Arquivamento de Dados** – Preserve datas de criação originais e informações da empresa para conformidade.

## Dicas de Performance

- Limite as operações de metadados por execução para evitar consumo excessivo de memória.  
- Feche o objeto `Metadata` prontamente (o padrão `try‑with‑resources` faz isso automaticamente).  
- Para pastas de trabalho muito grandes, considere processá‑las em uma thread em segundo plano para manter a UI responsiva.

## Conclusão

Agora você sabe como **alterar a data de criação do Excel**, **adicionar palavras‑chave ao Excel** e **modificar as propriedades do documento Excel** usando GroupDocs.Metadata em Java. Essa capacidade permite que suas planilhas fiquem bem organizadas, pesquisáveis e em conformidade com políticas internas de governança. Como próximo passo, explore outros recursos de metadados, como propriedades personalizadas ou processamento em lote, para otimizar ainda mais seu fluxo de gerenciamento de documentos.

---

**Última atualização:** 2026-03-22  
**Testado com:** GroupDocs.Metadata 24.12 para Java  
**Autor:** GroupDocs  

**Recursos**
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)