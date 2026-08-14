---
date: '2026-06-17'
description: Aprenda como alterar o horário de criação do diagrama e automatizar a
  atualização de metadados para arquivos de diagrama usando GroupDocs.Metadata em
  Java.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Alterar o horário de criação do diagrama nos metadados com GroupDocs Java
type: docs
url: /pt/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Alterar o Horário de Criação do Diagrama nos Metadados com GroupDocs Java

Neste tutorial passo a passo, você descobrirá como **alterar o horário de criação do diagrama** e atualizar outras propriedades internas de arquivos de diagrama usando a biblioteca GroupDocs.Metadata para Java. Automatizar essas alterações economiza horas de edição manual, garante timestamps consistentes em todo o seu repositório e torna seus diagramas instantaneamente pesquisáveis em qualquer sistema de gerenciamento de documentos.

## Respostas Rápidas
- **Qual é o objetivo principal?** Alterar o horário de criação do diagrama e outros metadados em arquivos de diagrama.  
- **Qual biblioteca devo usar?** GroupDocs.Metadata para Java.  
- **Preciso de uma licença?** Um teste gratuito é suficiente para testes; uma licença completa é necessária para produção.  
- **Posso processar em lote muitos diagramas?** Sim—envolva a mesma lógica em um loop ou em um stream paralelo.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.

## O que é “alterar o horário de criação do diagrama” nos metadados do diagrama?
Alterar o horário de criação substitui o timestamp original armazenado dentro de um arquivo de diagrama (como VDX ou VSDX) por um novo valor de data‑hora. Isso permite alinhar os metadados do arquivo com a data real de processamento ou arquivamento, em vez do timestamp original do autor, o que é essencial para trilhas de auditoria e resultados de busca precisos.

## Por que automatizar a atualização de metadados para diagramas?
Automatizar os metadados garante que cada diagrama siga os mesmos padrões de nomenclatura, categorização e timestamps sem erro humano. Também acelera migrações em massa, reduz o risco de conformidade e melhora a descoberta em plataformas DMS corporativas—economizando até 70 % do esforço manual em projetos de grande escala.

## Pré-requisitos
- **Java Development Kit (JDK) 8+** instalado na sua máquina.  
- **IDE** como IntelliJ IDEA ou Eclipse.  
- **Maven** (ou manipulação manual de JARs) para gerenciamento de dependências.  
- Familiaridade básica com classes Java, métodos e tratamento de exceções.

### Bibliotecas e Dependências Necessárias
Adicione o repositório e a dependência a seguir ao seu arquivo `pom.xml` se estiver usando Maven:

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
Se preferir baixar diretamente, visite [Lançamentos do GroupDocs.Metadata para Java](https://releases.groupdocs.com/metadata/java/) para obter a versão mais recente.

### Configuração do Ambiente
- JDK 8 ou mais recente.  
- IntelliJ IDEA, Eclipse ou qualquer IDE compatível com Java.  

### Pré-requisitos de Conhecimento
Compreender a sintaxe Java e I/O básico de arquivos tornará o tutorial mais fluido, mas as etapas são explicadas em linguagem simples.

## Configurando o GroupDocs.Metadata para Java
### Instruções de Instalação
**Usuários Maven:** O trecho acima adiciona o repositório e o JAR necessário automaticamente.  
**Usuários de Download Direto:** Após baixar o JAR de [GroupDocs](https://releases.groupdocs.com/metadata/java/), adicione-o ao classpath do seu projeto.

### Aquisição de Licença
- **Teste Gratuito:** Explore a biblioteca sem custo.  
- **Licença Temporária:** Obtenha uma licença temporária para testes estendidos [aqui](https://purchase.groupdocs.com/temporary-license/).  
- **Compra:** Adquira uma licença completa para ambientes de produção.

### Inicialização Básica
`Metadata` é a classe central que representa o contêiner de metadados de um documento e fornece acesso de leitura/escrita a todas as propriedades internas. Para começar a usar o GroupDocs.Metadata, importe a classe e abra um arquivo de diagrama:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```
Com a biblioteca inicializada, você pode agora modificar qualquer propriedade interna, incluindo o horário de criação.

## Guia de Implementação
### Como alterar o horário de criação em arquivos de diagrama
Nesta seção, percorreremos cada etapa necessária para **alterar o horário de criação do diagrama** e atualizar outras propriedades comuns, como autor, empresa e categoria. O processo envolve carregar o diagrama com a API Metadata, acessar seu pacote raiz, definir os campos desejados e, finalmente, salvar as alterações em um novo arquivo, garantindo que o original permaneça intacto.

#### Etapa 1: Carregar o Documento do Diagrama
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Explicação:* O construtor `Metadata` recebe o caminho para o seu arquivo de diagrama. O bloco try‑with‑resources garante que o arquivo seja fechado corretamente após a operação.

#### Etapa 2: Acessar o Pacote Raiz
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Explicação:* O pacote raiz fornece acesso direto a todos os campos de metadados internos do diagrama.

#### Etapa 3: Definir a Propriedade Criador
```java
root.getDocumentProperties().setCreator("test author");
```  
*Explicação:* Atribui um novo nome de autor. Substitua `"test author"` pelo criador real.

#### Etapa 4: Alterar o Horário de Criação
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Explicação:* Esta linha **altera o horário de criação** para a data e hora atuais do sistema. Você também pode fornecer uma instância `Date` específica se precisar de um timestamp personalizado.

#### Etapa 5: Definir Informação da Empresa
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Explicação:* Armazena o nome da empresa associado ao diagrama—útil para rastreamento empresarial.

#### Etapa 6: Definir a Categoria do Documento
```java
root.getDocumentProperties().setCategory("test category");
```  
*Explicação:* Categoriza o arquivo, ajudando você a **atualizar a categoria do diagrama** de forma consistente em todo o repositório.

#### Etapa 7: Adicionar Palavras‑Chave
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Explicação:* Palavras‑chave melhoram a capacidade de busca; você pode listar quaisquer termos relevantes ao conteúdo do diagrama.

#### Etapa 8: Salvar Alterações
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Explicação:* Persiste todas as modificações em um novo arquivo, deixando o original intacto.

### Armadilhas Comuns & Solução de Problemas
- **Arquivo Não Encontrado:** Verifique o caminho de entrada e assegure que a extensão do arquivo corresponda ao formato real.  
- **Acesso Negado:** Verifique as permissões de leitura/escrita para os diretórios de entrada e saída.  
- **Formato de Data Inválido:** Use objetos `java.util.Date` ou `java.time` compatíveis com a API.  

## Aplicações Práticas
1. **Automatização de Arquivamento de Documentos** – Ao mover diagramas antigos para um arquivo, altere automaticamente o **horário de criação do diagrama** para a data de arquivamento e defina uma categoria uniforme.  
2. **Integração com Controle de Versão** – Mantenha os timestamps sincronizados com commits do Git atualizando o horário de criação a cada release.  
3. **Padronização de DMS Corporativo** – Imponha uma política empresarial para autor, empresa e palavras‑chave em todos os ativos de diagramas.

## Considerações de Desempenho
- **Processamento em Lote:** Envolva as etapas acima dentro de um loop para lidar com dezenas de arquivos em uma única execução.  
- **Gerenciamento de Memória:** Libere cada instância `Metadata` prontamente (o bloco try‑with‑resources faz isso automaticamente).  
- **Execução Assíncrona:** Para lotes grandes, considere `CompletableFuture` para executar atualizações em paralelo sem bloquear a thread principal.  
- **Capacidade Quantificada:** O GroupDocs.Metadata suporta mais de 30 formatos de diagrama e pode processar arquivos de até 500 MB sem carregar o documento inteiro na memória, entregando atualizações em menos de 200 ms por arquivo em hardware de servidor típico.

## Conclusão
Agora você sabe como **alterar o horário de criação do diagrama** e atualizar outras propriedades internas de metadados para documentos de diagrama usando o GroupDocs.Metadata em Java. Ao automatizar essas etapas, você pode manter documentação consistente, pesquisável e em conformidade em toda a sua organização.

**Próximos Passos**
- Experimente outros formatos de arquivo suportados pelo GroupDocs.Metadata (PDF, DOCX, etc.).  
- Integre o código em um pipeline CI/CD para impor padrões de metadados em cada build.

Pronto para experimentar? Acesse [Lançamentos do GroupDocs.Metadata para Java](https://releases.groupdocs.com/metadata/java/) e comece a implementar sua própria automação de metadados hoje.

---

**Última Atualização:** 2026-06-17  
**Testado com:** GroupDocs.Metadata 24.12  
**Autor:** GroupDocs  

## Perguntas Frequentes

**Q: Posso usar esta abordagem com outros formatos de diagrama como VSDX?**  
A: Sim, a mesma API funciona para todos os formatos de diagrama suportados pelo GroupDocs.Metadata.

**Q: Preciso de uma licença para builds de desenvolvimento?**  
A: Um teste gratuito é suficiente para desenvolvimento e testes; uma licença completa é necessária para implantações em produção.

**Q: Como posso atualizar várias propriedades em uma única chamada?**  
A: Defina cada propriedade no objeto `DocumentProperties` antes de invocar `metadata.save(...)`; a biblioteca grava todas de uma vez.

**Q: É seguro sobrescrever o arquivo original?**  
A: Recomenda‑se salvar em um novo arquivo (conforme mostrado) e substituir o original somente após confirmar que a atualização foi bem‑sucedida.

**Q: E se eu precisar definir uma data de criação personalizada em vez da hora atual?**  
A: Crie um `java.util.Date` (ou instância `java.time`) com o timestamp desejado e passe‑o para `setTimeCreated`.

## Tutoriais Relacionados

- [Como Atualizar Metadados de Diagrama Java com GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Como Atualizar Metadados de Autor DXF com GroupDocs.Metadata para Java – Um Guia Completo](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Automatizar Atualizações de Metadados Java por Data Usando GroupDocs.Metadata para Gerenciamento Eficiente de Arquivos](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)