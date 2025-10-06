---
title: .NET의 PDF에서 내장 속성 읽기
linktitle: .NET의 PDF에서 내장 속성 읽기
second_title: GroupDocs.메타데이터 .NET API
description: GroupDocs.Metadata를 사용하여 .NET에서 PDF 메타데이터를 읽는 방법을 알아보세요. C# 코드를 사용하여 작성자 이름, 작성 날짜, 주제 등에 액세스하세요.
weight: 10
url: /ko/net/pdf-metadata/read-built-in-properties-pdfs/
type: docs
---
# .NET의 PDF에서 내장 속성 읽기

## 소개
이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 PDF 파일에서 기본 제공 속성을 읽는 방법을 살펴보겠습니다. GroupDocs.Metadata는 개발자가 PDF, Microsoft Office 문서, 이미지 등을 포함한 다양한 문서 형식과 관련된 메타데이터로 작업할 수 있는 강력한 라이브러리입니다. 이 라이브러리를 사용하면 작성자 이름, 생성 날짜, 주제 등과 같이 PDF 파일에 포함된 메타데이터 속성에 쉽게 액세스하고 조작할 수 있습니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- Visual Studio: 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요.
-  .NET용 GroupDocs.Metadata: 다음에서 .NET용 GroupDocs.Metadata를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/metadata/net/).
- C#에 대한 기본 지식: C# 프로그래밍 언어 및 .NET 프레임워크에 대한 지식.

## 네임스페이스 가져오기
C# 프로젝트에 필요한 네임스페이스를 추가하는 것부터 시작하세요.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1단계: PDF 메타데이터 로드
먼저 PDF 파일을 로드하고 GroupDocs.Metadata를 사용하여 해당 메타데이터를 추출합니다.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // PDF 파일의 루트 패키지에 액세스
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // 내장 속성 검색 및 표시
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // 추가 속성에도 비슷하게 액세스할 수 있습니다.
    // ...
}
```
메타데이터 읽기 외에도 GroupDocs.Metadata를 사용하면 프로그래밍 방식으로 PDF 파일에 새 메타데이터 속성을 편집, 제거 또는 추가하는 등의 고급 작업을 수행할 수 있습니다. 이러한 유연성을 통해 .NET 애플리케이션 내에서 문서 메타데이터를 포괄적으로 관리할 수 있습니다.
## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 C#을 사용하여 PDF 파일에서 기본 제공 속성을 추출하는 방법을 다루었습니다. 이 라이브러리를 프로젝트에 통합하면 문서 메타데이터 작업을 원활하게 처리하고 향상된 문서 관리 기능을 제공할 수 있습니다.

## FAQ
### GroupDocs.Metadata를 다른 문서 형식과 함께 사용할 수 있나요?
예, GroupDocs.Metadata는 DOCX, XLSX, PPTX, PDF, JPG, PNG 등과 같은 다양한 문서 형식을 지원합니다.
### GroupDocs.Metadata에 대한 무료 평가판이 있습니까?
예, 다음에서 GroupDocs.Metadata 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Metadata를 사용하여 메타데이터 속성을 수정하려면 어떻게 해야 합니까?
해당 문서 패키지에 액세스하고 새 값을 설정하여 프로그래밍 방식으로 메타데이터 속성을 수정할 수 있습니다.
### GroupDocs.Metadata는 .NET Core를 지원하나요?
예, GroupDocs.Metadata는 .NET Framework 및 .NET Core 모두와 호환됩니다.
### GroupDocs.Metadata와 관련된 지원을 찾거나 질문을 할 수 있는 곳은 어디입니까?
 지원 및 토론을 원하시면 다음 사이트를 방문하세요.[GroupDocs.메타데이터 포럼](https://forum.groupdocs.com/c/metadata/14).