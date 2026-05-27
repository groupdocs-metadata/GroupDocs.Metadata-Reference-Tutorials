---
date: '2026-05-27'
description: GroupDocs Maven 의존성을 사용하여 Java에서 pptx CreatedTime을 설정하고 PowerPoint 메타데이터를
  업데이트하는 방법을 배우세요. 여기에는 PPTX 생성 날짜를 변경하는 방법도 포함됩니다.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Java에서 GroupDocs Maven 의존성을 사용하여 PPTX CreatedTime 설정하기
type: docs
url: /ko/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Java에서 GroupDocs.Metadata를 사용하여 PPTX CreatedTime 설정

정확한 메타데이터는 현대 문서 워크플로우에서 규정 준수와 검색 가능성을 위해 필수적입니다. **GroupDocs.Metadata**를 사용하면 **Java에서 PPTX CreatedTime을 프로그래밍 방식으로 설정**할 수 있어, 저자나 회사와 같은 다른 기본 속성과 함께 **PPTX 생성 날짜를 변경**할 수 있습니다. 이 튜토리얼은 Maven 설정, API 초기화, 메타데이터 업데이트 및 수정된 프레젠테이션 저장 과정을 단계별로 안내하며, 명확하고 프로덕션 준비된 코드를 제공합니다.

## 빠른 답변
- **Java에서 PowerPoint 메타데이터를 업데이트하는 라이브러리는 무엇인가요?** GroupDocs Maven 의존성을 통한 GroupDocs.Metadata.  
- **PPTX CreatedTime 속성을 설정할 수 있나요?** 예—`root.getDocumentProperties().setCreatedTime(yourDate)`를 사용하세요.  
- **프로덕션에 라이선스가 필요합니까?** 평가용으로는 체험판을 사용할 수 있지만, 프로덕션 배포에는 상용 라이선스가 필수입니다.  
- **예제에서 사용하는 빌드 도구는 무엇인가요?** Maven(수동으로 JAR을 다운로드할 수도 있습니다).  
- **API가 Java 8 및 그 이후 버전을 지원하나요?** 물론입니다—GroupDocs.Metadata는 Java 8+을 대상으로 합니다.

## GroupDocs Maven 의존성이란?
**GroupDocs Maven 의존성**은 최신 GroupDocs.Metadata 라이브러리를 Java 프로젝트에 가져오는 Maven 호환 저장소 항목입니다. 전이 종속성을 자동으로 해결하여 의존성 관리를 단순화하고, 항상 최신 및 보안이 강화된 버전을 사용하도록 보장하며, 수동 JAR 다운로드나 버전 추적이 필요 없게 합니다.

## PPTX 생성 날짜를 변경하기 위해 GroupDocs.Metadata를 사용하는 이유
GroupDocs.Metadata는 PPTX 생성 타임스탬프를 자동화하고 배치 처리할 수 있게 업데이트하도록 지원하여, 모든 프레젠테이션이 기업 정책이나 법적 요구사항을 준수하도록 보장합니다. CreatedTime 속성을 프로그래밍 방식으로 설정함으로써 수동 편집을 피하고 인적 오류를 줄이며, CI/CD 파이프라인이나 마이그레이션 스크립트에 변화를 통합하여 원활한 문서 관리를 구현할 수 있습니다.

## 사전 요구 사항
- Java 8 이상이 설치되어 있어야 합니다.  
- IntelliJ IDEA 또는 Eclipse와 같은 IDE.  
- 의존성 관리를 위한 Maven.  
- GroupDocs 체험판 또는 구매 라이선스에 대한 접근 권한.

## Java에서 PPTX CreatedTime을 설정하는 방법?

`Metadata` 클래스는 문서를 나타내며 메타데이터 속성에 접근할 수 있게 합니다.

`new Metadata("presentation.pptx")`로 PowerPoint 파일을 로드하고, 루트 패키지를 가져온 뒤, 원하는 `java.util.Date`와 함께 `setCreatedTime`을 호출하고, 마지막으로 `save`를 호출하여 변경 사항을 기록합니다. 이 엔드‑투‑엔드 흐름은 슬라이드 내용 및 기타 속성을 모두 보존하면서 생성 날짜를 수정합니다.

### Maven 설정
GroupDocs 저장소와 메타데이터 의존성을 `pom.xml`에 추가합니다:

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

> **프로 팁:** 버전 번호를 최신 상태로 유지하면 최신 버그 수정 및 성능 향상의 혜택을 받을 수 있습니다.

### 직접 다운로드 (Maven을 사용하지 않으려는 경우)
또는 최신 JAR를 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)에서 다운로드하십시오.

#### 라이선스 획득
무료 체험판으로 시작하거나 임시 라이선스를 요청하여 GroupDocs.Metadata를 평가하십시오. 프로덕션 사용을 위해서는 [GroupDocs 공식 웹사이트](https://purchase.groupdocs.com/temporary-license/)를 통해 라이선스를 구매하십시오.

## 기본 초기화 및 설정

라이브러리가 클래스패스에 추가되면, PowerPoint 파일을 가리키는 `Metadata` 인스턴스를 생성할 수 있습니다:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

이 코드는 try‑with‑resources 블록에서 프레젠테이션을 열어 파일 핸들이 자동으로 해제되도록 보장합니다.

## 기본 메타데이터 업데이트 단계별 가이드

### 단계 1: 프레젠테이션 문서 로드
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

파일을 로드하면 메타데이터를 읽거나 쓸 수 있는 연결이 설정됩니다.

### 단계 2: 프레젠테이션 루트 패키지 접근
`root` 객체는 프레젠테이션의 핵심 패키지와 기본 속성에 접근할 수 있게 합니다.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` 객체는 모든 기본 문서 속성을 노출합니다.

### 단계 3: 기본 문서 속성 업데이트 (생성 날짜 포함)
`setCreatedTime`은 문서에 새로운 생성 타임스탬프를 할당합니다.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

여기서는 새로운 `Date` 객체를 `CreatedTime`에 할당하여 **PPTX CreatedTime**을 설정하는 방법을 보여줍니다. `new Date()`를 원하는 특정 타임스탬프로 교체하십시오.

### 단계 4: 업데이트된 프레젠테이션 저장
`save`는 수정된 메타데이터를 파일에 기록합니다.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` 호출은 수정된 메타데이터를 새로운 PowerPoint 파일에 기록하고 원본 파일은 그대로 둡니다.

## 문제 해결 팁
- **File Not Found:** 입력 경로와 파일 권한을 다시 확인하십시오.  
- **Version Mismatch:** `groupdocs-metadata` 버전이 Java 런타임과 일치하는지 확인하십시오.  
- **Property Not Updating:** `save`를 호출하기 전에 `setCreatedTime`(또는 해당 setter)을 호출했는지 확인하십시오.

## 실용적인 적용 사례
1. **Corporate Branding:** 배포 전에 모든 슬라이드 데크에 올바른 회사 이름과 카테고리를 자동으로 삽입합니다.  
2. **Document Management Systems:** PPTX 파일에 검색 가능한 메타데이터를 추가하여 빠른 검색을 가능하게 합니다.  
3. **Educational Resources:** 강의 슬라이드 전반에 걸쳐 저자 및 커리큘럼 정보를 최신 상태로 유지합니다.  
4. **Collaboration Tracking:** 기여자 이름을 기록하여 책임성을 유지합니다.  
5. **CMS Integration:** 메타데이터 변경을 실시간으로 콘텐츠 관리 플랫폼과 동기화합니다.

## 성능 고려 사항
- **Batch Processing:** 가능한 경우 파일 목록을 순회하면서 단일 `Metadata` 인스턴스를 재사용합니다.  
- **Memory Management:** 항상 try‑with‑resources(예시와 같이)를 사용하여 네이티브 리소스를 즉시 해제합니다.  
- **Efficient Data Structures:** 반복 호출을 줄이기 위해 메타데이터 업데이트를 맵에 저장한 후 적용합니다.

## 자주 묻는 질문

**Q: GroupDocs Maven 의존성의 주요 목적은 무엇인가요?**  
A: 최신 GroupDocs.Metadata 라이브러리를 Maven 기반 Java 프로젝트에 편리하게 포함할 수 있는 방법을 제공합니다.

**Q: 다른 속성에 영향을 주지 않고 PPTX 생성 날짜를 설정하려면 어떻게 해야 하나요?**  
A: `metadata.save()`를 호출하기 전에 `root.getDocumentProperties().setCreatedTime(yourDesiredDate)`를 사용하십시오.

**Q: 개발 환경에서 이 코드를 실행하려면 라이선스가 필요합니까?**  
A: 개발 및 테스트에는 임시 체험 라이선스로 충분하지만, 프로덕션에는 정식 라이선스가 필요합니다.

**Q: 사용자 정의 메타데이터 필드도 업데이트할 수 있나요?**  
A: 예—GroupDocs.Metadata는 API를 통해 기본 및 사용자 정의 속성을 모두 지원합니다.

**Q: 실수로 변경했을 경우 되돌릴 방법이 있나요?**  
A: 원본 파일을 복사해 두거나 기존 속성 값을 읽어 두었다가 덮어쓰기 전에 필요 시 복원하십시오.

## 리소스
- [문서](https://docs.groupdocs.com/metadata/java/)
- [API 레퍼런스](https://apireference.groupdocs.com/metadata/java/)

---

**마지막 업데이트:** 2026-05-27  
**테스트 환경:** GroupDocs.Metadata 24.12 for Java  
**작성자:** GroupDocs  

---

## 관련 튜토리얼
- [GroupDocs.Metadata Java API를 사용하여 PowerPoint에서 사용자 정의 메타데이터 업데이트](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [GroupDocs.Metadata Java를 사용하여 Word 문서 메타데이터 업데이트 방법: 완전 가이드](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Document Management를 위한 Java에서 GroupDocs.Metadata로 PDF 메타데이터 효율적으로 업데이트](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)