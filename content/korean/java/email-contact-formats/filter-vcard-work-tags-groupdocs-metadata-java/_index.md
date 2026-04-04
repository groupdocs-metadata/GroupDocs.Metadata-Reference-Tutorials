---
date: '2026-04-04'
description: GroupDocs.Metadata for Java를 사용하여 vCard 작업 태그를 필터링하는 방법을 배워보세요. 이 가이드는
  연락처 관리를 개선하기 위해 vCard 데이터를 효율적으로 필터링하는 단계별 방법을 보여줍니다.
keywords:
- how to filter vcard
- vCard work tags
- GroupDocs.Metadata Java
title: GroupDocs.Metadata for Java로 vCard 작업 태그 필터링하는 방법
type: docs
url: /ko/java/email-contact-formats/filter-vcard-work-tags-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata for Java를 사용하여 vCard 작업 태그 필터링하는 방법

## 빠른 답변
- **“vCard 작업 태그 필터링”이 의미하는 것은 무엇인가요?** 비즈니스와 관련 없는 필드를 제거하고 작업에 특화된 데이터만 남깁니다.  
- **어떤 라이브러리가 필터링을 담당하나요?** GroupDocs.Metadata for Java는 내장된 `filterWorkTags()` 및 `filterPreferred()` 메서드를 제공합니다.  
- **라이선스가 필요합니까?** 평가용으로는 무료 체험판을 사용할 수 있으며, 프로덕션에서는 영구 라이선스가 필요합니다.  
- **필요한 Java 버전은 무엇인가요?** JDK 8 이상.  
- **CRM과 통합할 수 있나요?** 예, 필터링된 데이터를 대부분의 CRM 플랫폼에 직접 전달할 수 있습니다.

## 전제 조건

- **GroupDocs.Metadata for Java** (버전 24.12 이상).  
- JDK 8 이상 및 IntelliJ IDEA 또는 Eclipse와 같은 IDE.  
- 기본 Java 지식 및 vCard 형식에 대한 이해.

## GroupDocs.Metadata for Java 설정

### Maven 구성
다음 저장소와 의존성을 `pom.xml`에 추가하세요:

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

### 직접 다운로드
또는 최신 버전의 GroupDocs.Metadata를 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)에서 다운로드하십시오.

### 라이선스 획득
- **무료 체험** – 비용 없이 모든 기능을 탐색할 수 있습니다.  
- **임시 라이선스** – 연장된 테스트 기간.  
- **구매** – 전체 프로덕션 지원.

라이브러리가 준비되었으니 실제 필터링 코드로 넘어가겠습니다.

## Java에서 vCard 작업 태그를 필터링하는 방법

### 1단계: vCard 파일 로드
플레이스홀더 경로를 `.vcf` 파일이 위치한 경로로 교체하십시오:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your_vcard_file.vcf")) {
    // Code continues...
}
```

### 2단계: 루트 패키지에 접근
기본 vCard 구조와 작업하기 위해 루트 패키지를 가져옵니다:

```java
VCardRootPackage root = metadata.getRootPackageGeneric();
```

### 3단계: 각 카드 반복
vCard 컨테이너의 모든 연락처 레코드를 순회합니다:

```java
for (VCardCard vCard : root.getVCardPackage().getCards()) {
    // Further processing...
}
```

### 4단계: 필터 적용
내장된 필터 메서드를 사용하여 작업 관련 태그와 선호하는 연락처 세부 정보를 유지합니다:

```java
VCardCard filtered = vCard.filterWorkTags().filterPreferred();
```

### 5단계: 필터링된 데이터 출력
필터링된 전화번호와 이메일 주소를 출력하여 결과를 확인합니다:

```java
printArray(filtered.getCommunicationRecordset().getTelephones());
printArray(filtered.getCommunicationRecordset().getEmails());

private static void printArray(String[] values) {
    if (values != null) {
        for (String value : values) {
            System.out.println(value);
        }
    }
}
```

### 추가 예제: vCard 파일 다시 로드
필요에 따라 동일한 파일을 다시 로드하여 다른 작업을 수행할 수 있습니다:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your_vcard_file.vcf")) {
    // Code continues...
}
```

## 실용적인 적용 사례

vCard 작업 태그 필터링은 특히 다음에 유용합니다:

1. **비즈니스 네트워킹** – 대규모 주소록에서 전문 연락처 필드만 추출합니다.  
2. **CRM 통합** – 정제된 작업 중심 데이터를 고객 관계 시스템에 직접 전달합니다.  
3. **자동화 워크플로** – 비즈니스 전화번호나 이메일만 필요한 스크립트를 구동합니다.

## 성능 고려 사항

- **메모리 관리** – 대용량 vCard 파일을 스트림으로 처리하여 OOM 오류를 방지합니다.  
- **프로파일링** – 수천 개의 연락처를 처리할 때 병목 현상을 찾기 위해 Java 프로파일러를 사용합니다.  
- **가비지 컬렉션** – `Metadata` 객체를 즉시 닫아(try‑with‑resources 사용 예시와 같이) 네이티브 리소스를 해제합니다.

## 자주 묻는 질문

**Q: GroupDocs.Metadata란 무엇인가요?**  
A: GroupDocs.Metadata는 vCard를 포함한 다양한 파일 형식의 메타데이터를 읽고, 편집하고, 필터링하는 작업을 단순화하는 Java 라이브러리입니다.

**Q: 이 라이브러리를 Spring Boot와 함께 사용할 수 있나요?**  
A: 물론입니다. Maven 의존성을 추가하고 필요한 곳에 서비스를 주입하면 됩니다.

**Q: 라이브러리는 매우 큰 vCard 파일을 어떻게 처리하나요?**  
A: 내부적으로 데이터를 스트리밍하지만 메모리 사용량을 낮게 유지하기 위해 레코드를 배치로 처리하는 것이 좋습니다.

**Q: 개발에 라이선스가 필요합니까?**  
A: 개발 및 테스트에는 무료 체험판이면 충분하며, 프로덕션 배포에는 상용 라이선스가 필요합니다.

**Q: 더 많은 예제를 어디서 찾을 수 있나요?**  
A: 추가 코드 샘플 및 API 레퍼런스는 [GroupDocs documentation](https://docs.groupdocs.com/metadata/java/)를 참고하십시오.

---

**마지막 업데이트:** 2026-04-04  
**테스트 환경:** GroupDocs.Metadata 24.12 for Java  
**작성자:** GroupDocs  

---