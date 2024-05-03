---
title: .NET을 사용하여 프레젠테이션의 기본 제공 속성 업데이트
linktitle: .NET을 사용하여 프레젠테이션의 기본 제공 속성 업데이트
second_title: GroupDocs.메타데이터 .NET API
description: 다목적 메타데이터 조작 라이브러리인 GroupDocs.Metadata와 함께 .NET을 사용하여 프레젠테이션의 기본 제공 속성을 업데이트하는 방법을 알아보세요.
type: docs
weight: 15
url: /ko/net/presentation-metadata/update-built-in-properties-presentations/
---
## 소개
이 자습서에서는 .NET 프레임워크를 사용하여 문서 내의 메타데이터를 조작하도록 설계된 포괄적인 라이브러리인 GroupDocs.Metadata for .NET의 강력한 기능을 자세히 살펴보겠습니다. 특히 C#을 사용하여 프로그래밍 방식으로 프레젠테이션(.PPT 및 .PPTX 파일)의 기본 제공 속성을 업데이트하는 방법에 중점을 둘 것입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- Visual Studio: 시스템에 설치됩니다.
-  .NET용 GroupDocs.Metadata: 다음 위치에서 다운로드 및 설치됩니다.[여기](https://releases.groupdocs.com/metadata/net/).
- 기본 C# 지식: C# 프로그래밍 언어에 익숙합니다.

## 네임스페이스 가져오기
필요한 네임스페이스를 C# 프로젝트로 가져오는 것부터 시작하세요.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1단계: 프리젠테이션 파일 로드
 먼저 새 인스턴스를 만듭니다.`Metadata` 프리젠테이션 파일을 로드하여:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## 2단계: 내장 속성 업데이트
이제 프레젠테이션의 원하는 기본 제공 속성을 업데이트하세요. 예를 들어 작성자, 생성 날짜, 회사, 카테고리, 키워드 등을 수정할 수 있습니다. 방법은 다음과 같습니다.
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## 3단계: 변경 사항 저장
속성을 업데이트한 후 변경 사항을 프리젠테이션 파일에 다시 저장합니다.
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 프로그래밍 방식으로 프레젠테이션 파일의 기본 제공 속성을 업데이트하는 방법을 살펴보았습니다. 다음 단계를 수행하면 .NET 애플리케이션 내에서 메타데이터를 효율적으로 관리하고 수정할 수 있습니다.

## FAQ
### Q: .NET용 GroupDocs.Metadata란 무엇입니까?
A: .NET용 GroupDocs.Metadata는 .NET 프레임워크를 위한 강력한 메타데이터 조작 라이브러리로, 이를 통해 개발자는 다양한 문서 형식의 메타데이터를 읽고, 쓰고, 편집할 수 있습니다.
### Q: GroupDocs.Metadata에 대한 설명서는 어디에서 찾을 수 있습니까?
 A: 자세한 문서에 액세스할 수 있습니다.[여기](https://reference.groupdocs.com/metadata/net/).
### Q: GroupDocs.Metadata에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 A: 임시 라이센스를 취득할 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### Q: GroupDocs.Metadata는 프레젠테이션 외에 다른 파일 형식을 지원합니까?
A: 예, GroupDocs.Metadata는 문서, 스프레드시트, 이미지, 비디오 등을 포함한 광범위한 형식을 지원합니다.
### Q: GroupDocs.Metadata에 대한 지원을 받거나 질문을 할 수 있는 곳은 어디입니까?
 답변: 지원 및 토론을 원하시면 다음 사이트를 방문하세요.[GroupDocs.메타데이터 포럼](https://forum.groupdocs.com/c/metadata/14).