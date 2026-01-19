---
date: '2026-01-19'
description: Aprenda como alterar o horário de criação e automatizar a atualização
  de metadados para arquivos de diagramas usando o GroupDocs.Metadata em Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Alterar a data de criação nos metadados do diagrama usando GroupDocs Java
type: docs
url: /pt/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

ar horamente **alterar a hora de criação** e outras propriedades internas em um único passo repetível. Este guia mostra como configurar a biblioteca, atualizar os metadados de diagramas e aplicar dicas de desempenho recomendadas para que seus documentos permaneçam consistentes e pesquisáveis.

## Respostas Rápidas
- **Qual é o objetivo principal?** Alterar a hora de criação e outros metadados em arquivos de diagrama.  
- **Qual biblioteca devo usar?** GroupDocs.Metadata para Java.  
- **Preciso de licença?** Um teste gratuito funciona para testes; uma licença completa é necessária para produção.  
- **Posso processar vários diagramas em lote?** Sim—use a mesma abordagem dentro de um loop ou stream paralelo.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.

## O que significa “alterar hora de criação” nos metadados de diagrama?
Alterar a hora de criação significa sobrescrever o carimbo de data/hora original armazenado dentro de um arquivo de diagrama (por exemplo, VDX, VSDX) com uma nova data. Isso é útil quando você precisa que os metadados do arquivo reflitam a data real de processamento, e não a data original de autoria.

## Por que automatizar a atualização de metadados para diagramas?
- **Consistência:** Garante que cada arquivo siga as mesmas regras de nomenclatura e categorização.  
- **Facilidade de busca:** Palavras‑chave e categorias atualizadas melhoram a descoberta de documentos em soluções DMS.  
- **Conformidade:** Ajuda a atender requisitos de auditoria ao garantir carimbos de data/hora precisos.  

## Pré‑requisitos
- **Java Development Kit (JDK) 8+** instalado.  
- **IDE** como IntelliJ IDEA ou Eclipse.  
- **Maven** (ou gerenciamento manual de JARs) para dependências.  
- Conhecimento básico de classes Java, métodos e tratamento de exceções.

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
Se preferir baixar diretamente, visite [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) para obter a versão mais recente.

### Configuração do Ambiente
- JDK 8 ou mais recente.  
- IntelliJ IDEA, Eclipse ou qualquer IDE compatível com Java.  

### Pré‑requisitos de Conhecimento
Entender a sintaxe Java e I/O básico de arquivos tornará o tutorial mais fluido, mas as etapas são explicadas em linguagem simples.

## Configurando GroupDocs.Metadata para Java
### Instruções de Instalação
**Usuários Maven:** O trecho acima adiciona o repositório e o JAR necessário automaticamente.  
**Usuários de Download Direto:** Após baixar o JAR em [GroupDocs](https://releases.groupdocs.com/metadata/java/), adicione‑o ao classpath do seu projeto.

### Aquisição de Licença
- **Teste Gratuito:** Explore a biblioteca sem custo.  
- **Licença Temporária:** Obtenha uma licença temporária para testes prolongados [aqui](https://purchase.groupdocs.com/temporary-license/).  
- **Compra:** Adquira uma licença completa para ambientes de produção.

### Inicialização Básica
Para começar a usar o GroupDocs.Metadata, importe a classe e abra um arquivo de diagrama:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Com a biblioteca inicializada, você pode agora modificar qualquer propriedade interna, incluindo a hora de criação.

## Guia de Implementação
### Como alterar a hora de criação em arquivos de diagrama
Nesta seção percorreremos cada passo necessário para **alterar a hora de criação** e atualizar outras propriedades comuns, como autor, empresa e categoria.

#### Etapa 1: Carregar o Documento de Diagrama
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

#### Etapa 3: Definir a Propriedade de Criador
```java
root.getDocumentProperties().setCreator("test author");
```
*Explicação:* Atribui um novo nome de autor. Substitua `"test author"` pelo criador real.

#### Etapa 4: **Alterar Hora de Criação**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Explicação:* Esta linha **altera a hora de criação** para a data e hora atuais do sistema. Você também pode fornecer uma instância específica de `Date` se precisar de um carimbo personalizado.

#### Etapa 5: Definir Informações da Empresa
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Explicação:* Armazena o nome da empresa associado ao diagrama—útil para rastreamento corporativo.

#### Etapa 6: Definir a Categoria do Documento
```java
root.getDocumentProperties().setCategory("test category");
```
*Explicação:* Categoriza o arquivo, ajudando a **atualizar a categoria do diagrama** de forma consistente em todo o repositório.

#### Etapa 7: Adicionar Palavras‑Chave
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Explicação:* Palavras‑chave melhoram a pesquisabilidade; você pode listar quaisquer termos relevantes ao conteúdo do diagrama.

#### Etapa 8: Salvar Alterações
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Explicação:* Persiste todas as modificações em um novo arquivo, mantendo o original intacto.

### Armadilhas Comuns & Solução de Problemas
- **Arquivo Não Encontrado:** Verifique o caminho de entrada e assegure que a extensão do arquivo corresponda ao formato real.  
- **Acesso Negado:** Verifique permissões de leitura/escrita nos diretórios de entrada e saída.  
- **Formato de Data Inválido:** Use objetos `java.util.Date` ou `java.time` compatíveis com a API.  

## Aplicações Práticas
1. **Automatização de Arquivamento de Documentos** – Ao mover diagramas antigos para um arquivo, altere automaticamente a **hora de criação** para a data de arquivamento e defina uma categoria uniforme.  
2. **Integração com Controle de Versão** – Mantenha os carimbos sincronizados com commits Git atualizando a hora de criação a cada release.  
3. **Padronização de DMS Corporativo** – Imponha uma política empresarial para autor, empresa e palavras‑chave em todos os ativos de diagrama.

## Considerações de Desempenho
- **Processamento em Lote:** Envolva as etapas acima dentro de um loop para tratar dezenas de arquivos em uma única execução.  
- **Gerenciamento de Memória:** Libere cada instância `Metadata` prontamente (o bloco try‑with‑resources faz isso automaticamente).  
- **Execução Assíncrona:** Para lotes grandes, considere `CompletableFuture` para executar atualizações em paralelo sem bloquear a thread principal.

## Conclusão
Agora você sabe como **alterar a hora de criação** e atualizar outras propriedades internas de metadados para documentos de diagrama usando GroupDocs.Metadata em Java. Ao automatizar essas etapas, você pode manter documentação consistente, pesquisável e em conformidade em toda a sua organização.

**Próximos Passos**
- Experimente outros formatos de arquivo suportados pelo GroupDocs.Metadata (PDF, DOCX, etc.).  
- Integre o código em um pipeline CI/CD para impor padrões de metadados em cada build.  

Pronto para experimentar? Acesse [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) e comece a implementar sua própria automação de metadados hoje.

---

**Última Atualização:** 2026-01-19  
**Testado Com:** GroupDocs.Metadata 24.12  
**Autor:** GroupDocs  

## Perguntas Frequentes

**Q: Posso usar esta abordagem com outros formatos de diagrama como VSDX?**  
A: Sim, a mesma API funciona para todos os formatos de diagrama suportados pelo GroupDocs.Metadata.

**Q: Preciso de licença para builds de desenvolvimento?**  
A: Um teste gratuito é suficiente para desenvolvimento e testes; uma licença completa é necessária para implantações em produção.

**Q: Como posso atualizar múltiplas propriedades em uma única chamada?**  
A: Defina cada propriedade no objeto `DocumentProperties` antes de chamar `metadata.save(...)`; a biblioteca grava todas de uma vez.

**Q: É seguro sobrescrever o arquivo original?**  
A: Recomenda‑se salvar em um novo arquivo (conforme demonstrado) para evitar perda de dados, substituindo o original somente se necessário.

**Q: E se eu precisar definir uma data de criação personalizada em vez da hora atual?**  
A: Crie um `java.util.Date` (ou instância `java.time`) com o carimbo desejado e passe‑o para `setTimeCreated`.