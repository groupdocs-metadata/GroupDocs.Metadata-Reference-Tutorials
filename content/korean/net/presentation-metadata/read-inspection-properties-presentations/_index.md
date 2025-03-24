---
title: .NET 프레젠테이션에서 검사 속성 읽기
linktitle: .NET 프레젠테이션에서 검사 속성 읽기
second_title: GroupDocs.메타데이터 .NET API
description: .NET용 GroupDocs.Metadata를 사용하여 프레젠테이션 메타데이터를 추출하는 방법을 알아보세요. 댓글, 숨겨진 슬라이드 등에 프로그래밍 방식으로 액세스하세요.
weight: 14
url: /ko/net/presentation-metadata/read-inspection-properties-presentations/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 프레젠테이션의 속성을 읽고 검사하는 방법을 살펴보겠습니다. GroupDocs.Metadata는 개발자가 프레젠테이션, PDF, 이미지 등과 같은 문서에 포함된 메타데이터로 작업할 수 있는 강력한 API입니다. 특히 프레젠테이션(PPTX 파일)에 중점을 두고 댓글, 숨겨진 슬라이드 등과 같은 정보를 추출하는 방법을 보여줍니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
- Visual Studio: Visual Studio 또는 .NET 개발용 호환 IDE를 설치합니다.
-  .NET용 GroupDocs.Metadata: 다음 위치에서 .NET용 GroupDocs.Metadata 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/metadata/net/).
- 입력 파일: 테스트할 샘플 프레젠테이션(PPTX 파일)을 준비합니다.
## 네임스페이스 가져오기
시작하려면 프로젝트에 필요한 네임스페이스를 포함하세요.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1단계: 프레젠테이션 메타데이터 로드 및 검사
프리젠테이션 파일을 로드하고 GroupDocs.Metadata를 사용하여 해당 루트 패키지에 액세스하는 것으로 시작합니다.
```csharp
using (Metadata metadata = new Metadata("Your Input File"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## 2단계: 프레젠테이션에서 주석 검색
다음으로 프레젠테이션에 포함된 주석을 검색하고 반복합니다.
```csharp
if (root.InspectionPackage.Comments != null)
{
    foreach (var comment in root.InspectionPackage.Comments)
    {
        Console.WriteLine(comment.Author);
        Console.WriteLine(comment.Text);
        Console.WriteLine(comment.CreatedTime);
        Console.WriteLine(comment.SlideNumber);
    }
}
```
## 3단계: 숨겨진 슬라이드 정보에 접근하기
이제 프레젠테이션의 숨겨진 슬라이드와 관련된 정보에 액세스하고 처리합니다.
```csharp
if (root.InspectionPackage.HiddenSlides != null)
{
    foreach (var slide in root.InspectionPackage.HiddenSlides)
    {
        Console.WriteLine(slide.Name);
        Console.WriteLine(slide.Number);
        Console.WriteLine(slide.SlideId);
    }
}
```
## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 프레젠테이션에서 메타데이터를 추출하는 방법을 보여주었습니다. 프로그래밍 방식으로 PPTX 파일 내의 주석과 숨겨진 슬라이드 정보에 액세스하는 방법을 배웠습니다. GroupDocs.Metadata는 문서 메타데이터 작업을 단순화하여 개발자에게 강력한 기능을 제공합니다.

## FAQ
### Q: .NET용 GroupDocs.Metadata란 무엇입니까?
A: .NET용 GroupDocs.Metadata는 개발자가 프로그래밍 방식으로 다양한 문서 형식의 메타데이터를 읽고, 편집하고, 제거하고, 조작할 수 있는 API입니다.
### Q: GroupDocs.Metadata에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 A: 다음에서 임시 라이센스를 취득할 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### Q: .NET용 GroupDocs.Metadata에 대한 설명서는 어디에서 찾을 수 있습니까?
 A: 문서를 참조할 수 있습니다.[여기](https://tutorials.groupdocs.com/metadata/net/).
### Q: GroupDocs.Metadata에 대한 지원을 받으려면 어떻게 해야 합니까?
 A: 지원 및 토론을 원하시면 GroupDocs.Metadata 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/metadata/14).
### 질문: .NET용 GroupDocs.Metadata 무료 평가판을 다운로드할 수 있습니까?
 A: 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).