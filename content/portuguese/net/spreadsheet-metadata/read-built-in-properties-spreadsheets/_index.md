---
title: Leia propriedades integradas de planilhas em .NET
linktitle: Leia propriedades integradas de planilhas em .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda como extrair metadados de planilhas em .NET usando GroupDocs.Metadata, aprimorando o gerenciamento e a organização de documentos em seus aplicativos.
type: docs
weight: 10
url: /pt/net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
---
## Introdução
Neste tutorial, nos aprofundaremos em como utilizar GroupDocs.Metadata for .NET para gerenciar e extrair metadados de planilhas com eficiência. GroupDocs.Metadata for .NET é uma API poderosa que permite aos desenvolvedores trabalhar com metadados incorporados em vários formatos de arquivo, incluindo planilhas, apresentações, documentos, imagens e muito mais. Este guia se concentra especificamente na extração de propriedades integradas de arquivos de planilha usando C#.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos em vigor:
- Ambiente de Desenvolvimento: Visual Studio ou qualquer IDE compatível com C#.
-  Biblioteca GroupDocs.Metadata for .NET: Baixe e instale a biblioteca do[local na rede Internet](https://releases.groupdocs.com/metadata/net/).
- Arquivo de entrada: Prepare um arquivo de planilha de exemplo (por exemplo, Excel) do qual deseja extrair metadados.

## Importar namespaces
Comece importando os namespaces necessários para acessar as funcionalidades GroupDocs.Metadata em seu projeto C#.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Etapa 1: inicializar metadados e recuperar o pacote raiz da planilha
 Comece inicializando o`Metadata` objeto com o caminho do arquivo de entrada. Em seguida, obtenha o pacote raiz específico para planilhas.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    //Acesse e recupere propriedades integradas
}
```
## Etapa 2: acessar as propriedades integradas
 Depois de obter o pacote raiz, você poderá acessar várias propriedades integradas do arquivo de planilha usando`DocumentProperties`.
### Etapa 2.1: acessar a propriedade do autor
Recuperar o autor (criador) da planilha.
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### Etapa 2.2: Acesse a propriedade de tempo criado
Obtenha o carimbo de data/hora de criação da planilha.
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### Etapa 2.3: acessar a propriedade da empresa
Busque o nome da empresa associado à planilha.
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### Etapa 2.4: Acessar propriedade da categoria
Obtenha as informações da categoria da planilha.
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### Etapa 2.5: acessar a propriedade de palavras-chave
Recupere as palavras-chave associadas à planilha.
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### Etapa 2.6: Acessar propriedade de idioma
Recupere o idioma usado na planilha.
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### Etapa 2.7: Acesse a propriedade do tipo de conteúdo
Obtenha o tipo de conteúdo ou tipo MIME da planilha.
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## Conclusão
Neste tutorial, exploramos como usar GroupDocs.Metadata for .NET para extrair propriedades integradas de arquivos de planilha usando C#. Seguindo essas etapas, você pode integrar perfeitamente o gerenciamento de metadados em seus aplicativos .NET, aprimorando a organização de arquivos e os recursos de recuperação.

## Perguntas frequentes
### O GroupDocs.Metadata for .NET é compatível com vários formatos de arquivo?
Sim, GroupDocs.Metadata oferece suporte a uma ampla variedade de formatos de arquivo, incluindo planilhas, documentos, apresentações, imagens e muito mais.
### Posso modificar metadados usando GroupDocs.Metadata for .NET?
Sim, você pode não apenas ler, mas também editar, atualizar e remover metadados usando esta API.
### Onde posso encontrar documentação detalhada para GroupDocs.Metadata for .NET?
 A documentação detalhada está disponível em[Documentação do GroupDocs.Metadata para .NET](https://reference.groupdocs.com/metadata/net/).
### Como posso obter uma licença temporária para fins de teste?
 Você pode solicitar uma licença temporária de[aqui](https://purchase.groupdocs.com/temporary-license/).
### Existe um fórum da comunidade para suporte ao GroupDocs.Metadata?
 Sim, você pode visitar o[Fórum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14) para apoio e discussões da comunidade.