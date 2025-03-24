---
title: .NET을 사용하여 PDF의 내장 속성 업데이트
linktitle: .NET을 사용하여 PDF의 내장 속성 업데이트
second_title: GroupDocs.메타데이터 .NET API
description: .NET용 C# 및 GroupDocs.Metadata를 사용하여 PDF 문서 속성을 업데이트하는 방법을 알아보세요. 저자, 제목, 키워드 등을 프로그래밍 방식으로 수정합니다.
weight: 15
url: /ko/net/pdf-metadata/update-built-in-properties-pdfs/
---

# .NET을 사용하여 PDF의 내장 속성 업데이트

## 소개
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 PDF 문서의 기본 제공 속성을 업데이트하는 방법을 알아봅니다. 이 라이브러리는 다양한 문서 형식 내에서 메타데이터를 조작할 수 있는 강력한 도구 세트를 제공합니다. C#을 사용하여 PDF 파일에서 작성자, 제목, 생성 날짜, 키워드, 작성자 및 제작자와 같은 속성을 수정하는 데 필요한 단계를 살펴보겠습니다.
## 전제 조건
시작하기 전에 다음 사항이 준비되어 있는지 확인하세요.
-  .NET 라이브러리용 GroupDocs.Metadata: 다음에서 라이브러리를 다운로드하세요.[여기](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Visual Studio를 설치하여 C# 코드를 작성하고 실행합니다.
- C#에 대한 기본 이해: C# 프로그래밍 언어에 익숙한 것이 좋습니다.

## 네임스페이스 가져오기
C# 프로젝트에 필요한 네임스페이스를 포함하는 것부터 시작하세요.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1단계: 메타데이터 개체 초기화
 초기화부터 시작하세요.`Metadata`PDF 파일 경로가 포함된 개체:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // 귀하의 코드는 여기에 저장됩니다
}
```
## 2단계: PDF 루트 패키지에 액세스
 다음으로, 다음을 사용하여 PDF 전용 루트 패키지를 검색합니다.`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## 3단계: 문서 속성 업데이트
 이제 PDF 문서의 원하는 속성을 업데이트하십시오.`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## 4단계: 변경 사항 저장
속성을 수정한 후 변경 사항을 PDF 파일에 다시 저장합니다.
```csharp
metadata.Save("Your Output File Path");
```
## 5단계: 업데이트된 속성 검색
변경 사항을 확인하려면 메타데이터를 다시 로드하고 업데이트된 속성을 검색합니다.
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 PDF 문서의 기본 제공 속성을 프로그래밍 방식으로 업데이트하는 방법을 살펴보았습니다. 설명된 단계를 따르면 C#을 사용하여 PDF 파일 내의 메타데이터를 효율적으로 관리하고 수정할 수 있습니다. 포괄적인 메타데이터 조작을 위해 GroupDocs.Metadata에서 제공하는 더 많은 기능을 자유롭게 탐색해 보세요.

## FAQ
### Q: .NET용 GroupDocs.Metadata란 무엇입니까?
A: .NET용 GroupDocs.Metadata는 개발자가 프로그래밍 방식으로 다양한 문서 형식의 메타데이터를 읽고, 편집하고, 제거하고, 조작할 수 있는 라이브러리입니다.
### Q: .NET용 GroupDocs.Metadata 설명서는 어디에서 찾을 수 있습니까?
 A: 문서에 액세스할 수 있습니다.[여기](https://tutorials.groupdocs.com/metadata/net/).
### Q: .NET용 GroupDocs.Metadata를 어떻게 다운로드할 수 있나요?
 A: 다음에서 .NET용 GroupDocs.Metadata를 다운로드할 수 있습니다.[이 링크](https://releases.groupdocs.com/metadata/net/).
### Q: 무료 평가판이 제공됩니까?
 A: 예, 무료 평가판을 받을 수 있습니다.[여기](https://releases.groupdocs.com/).
### Q: .NET용 GroupDocs.Metadata에 대한 지원은 어디서 받을 수 있습니까?
 A: 지원이 필요하면 GroupDocs.Metadata 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/metadata/14).