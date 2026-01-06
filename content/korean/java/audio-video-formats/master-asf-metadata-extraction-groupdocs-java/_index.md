---
date: '2025-12-26'
description: GroupDocs.Metadata for Java를 사용하여 ASF 메타데이터를 추출하는 방법을 배웁니다. 이 가이드는 설정,
  속성 읽기 및 코덱 정보 액세스를 다룹니다.
keywords:
- ASF Metadata Extraction
- GroupDocs.Metadata for Java
- Java Media Management
title: Java용 GroupDocs.Metadata로 ASF 메타데이터 추출하는 방법
type: docs
url: /ko/java/audio-video-formats/master-asf-metadata-extraction-groupdocs-java/
weight: 1
---

# Java용 GroupDocs.Metadata를 사용하여 ASF 메타데이터 추출

**소개**

매우 중요한 디지털 환경에서는 컨텐츠를 관리하는 것이 매우 중요합니다. 미디어 파일에서 **ASF메모데이터를 추출해야 하는 경우** 수동으로 수행하면 시간이 많이 걸리고 오류가 발생하기 쉽습니다. 이 튜토리얼에서는 **GroupDocs.Metadata for Java**를 사용하여 다양한 ASF 속성을 이해하고 표시하는 방법을 점차적으로 안내합니다. 이를 통해 자산을 수집하고, 검색하며, 자신이 처리할 수 있습니다.

### 배우게 될 내용
- Java 프로젝트에 GroupDocs.Metadata를 설정하는 방법
- 생성 날짜, 파일 ID, 기호와 같은 **ASF 데이터를 추출**하는 방법
- ASF 파일에 포함된 정보를 읽는 방법
- 상세데이터 데이터 디스크립터와 스트리밍 속성을 표시하는 방법

반드시 사전 준비를 해주시기 바랍니다.

## 빠른 답변
- **“ASF 메타데이터 추출”은 무엇을 의미합니까?** 프로그래밍 방식으로 ASF 파일에서 임베드된 정보(예: 타임스탬프, 코덱, 디스크립터)를 읽는 것을 의미합니다.
- **어떤 라이브러리가 필요합니까?** GroupDocs.Metadata for Java (버전24.12 이상).
- **라이센스가 필요합니까?** 개발에서는 무료 체험 또는 임시 공간으로만 가능하지만, 내부적으로는 영역 클러스터가 필요합니다.
- **어떤 Java 버전을 지원하나요?** JDK8이상.
- **Maven을 사용할 수 있나요?** 예 – Maven이 권장되는 의존성 관리 도구입니다.

## 전제 조건

- **JDK(Java Development Kit)**8이상 설치
- **IDE**(IntelliJ IDEA 또는 Eclipse 등) 권장 권장
- **Maven**을 IDE에 설정(선택하시기 바랍니다)
- Java와 외부교육에 대한 기본 지식

## Java용 GroupDocs.Metadata 설정

### 메이븐 설치

`pom.xml`에 저장소와 의존성을 추가합니다:

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

Maven을 사용하지 않으려면 최신 JAR 파일을 [Java 릴리스용 GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)에서 다운로드하세요.

### 라이선스 개요

- **무료 평가판** – GroupDocs 웹사이트에서 평가용으로 제공
- **임시 라이센스** – 개발 중 모든 기능을 제한할 수 없습니다.
- **정규 라이선스** – 그리워·프로덕션 환경에 필요

### 기본 초기화

아래 코드는 GroupDocs.Metadata를 사용해 ASF 파일을 여는 최소 예제입니다:

```java
import com.groupdocs.metadata.Metadata;

class MetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            // Your code for accessing metadata properties will go here.
        }
    }
}
```

## ASF 메타데이터란 무엇입니까?

ASF(Advanced Systems Format)는 Microsoft 스트리밍 수신으로 오디오, 비디오 및 메타데이터를 하나의 컨테이너에 저장합니다. 메타 데이터에는 생성 타임스탬프, 로그 세부 정보, 스트림 디스크립터 등이 포함되어 있습니다. **ASF 메타데이터를 추출하면**파일 원본, 요청하는 것, 콘텐츠 설명 캡슐에 대한 프로그래밍 적 인사이트를 얻을 수 있는 미디어, 전송코딩 파이프라인, 규정 준수 감사하는 파라입니다.

## GroupDocs.Metadata를 사용하여 ASF 메타데이터를 추출하는 이유는 무엇입니까?

- **제로 코드 구문 분석** – 저수준 ASF 문서를 직접 처리할 필요 없음
- **풍부한 개체 모델** – 축소인 Java 클래스를 통해 속성, 코덱, 디스크립터, 스트림 세부 정보를 향해 접근
- **크로스 플랫폼** – Java를 지원하는 모든 OS에서 동작
- **라이선스 유연성** – 체험판으로 조직이 필요하므로 배치로 전환 가능

## 구현 가이드

하단 섹션에서는 **ASF 감지 데이터를 추출**하는 흥미로운 스코드니펫을 좀 살펴봅니다.

### 기본 ASF 메타데이터 속성 읽기

**개요** – 생성 날짜, 파일 ID, 플래그와 같은 기본 정보를 가져오기입니다.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.AsfRootPackage;

class ReadBasicProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            System.out.println("Creation date: " + asfPackage.getCreationDate());
            System.out.println("File id: " + asfPackage.getFileID());
            System.out.println("Flags: " + asfPackage.getFlags());
        }
    }
}
```

*중요한 이유*: 날짜 생성을 알면 버전 관리를 용이하게 하고, 파일 ID는 시스템에서 자산을 고유하게 식별하는 데 도움이 됩니다.

### ASF 코덱 정보 표시

**개요** – 오디오 및 비디오 스트림을 사용하여 로그를 표시합니다.

```java
import com.groupdocs.metadata.core.AsfCodec;

class ReadCodecInformation {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfCodec codecInfo : asfPackage.getCodecInformation()) {
                System.out.println("Codec type: " + codecInfo.getCodecType());
                System.out.println("Description: " + codecInfo.getDescription());
                System.out.println("Codec information: " + codecInfo.getInformation());
                System.out.println(codecInfo.getName());
            }
        }
    }
}
```

*중요한 이유*: 로그 세부 정보는 게임 간의 호환성을 확인하거나 전송 코딩 여부를 구성할 때입니다.

### 메타데이터 설명자 표시

**개요** – 언어, 스트림 번호, 원본 제목 등 상세 디스크립터를 가져오기.

```java
import com.groupdocs.metadata.core.AsfBaseDescriptor;
import com.groupdocs.metadata.core.AsfMetadataDescriptor;

class ReadMetadataDescriptors {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseDescriptor descriptor : asfPackage.getMetadataDescriptors()) {
                System.out.println("Name: " + descriptor.getName());
                System.out.println("Value: " + descriptor.getValue());
                System.out.println("Content type: " + descriptor.getAsfContentType());

                if (descriptor instanceof AsfMetadataDescriptor) {
                    AsfMetadataDescriptor metadataDescriptor = (AsfMetadataDescriptor) descriptor;
                    System.out.println("Language: " + metadataDescriptor.getLanguage());
                    System.out.println("Stream number: " + metadataDescriptor.getStreamNumber());
                    System.out.println("Original name: " + metadataDescriptor.getOriginalName());
                }
            }
        }
    }
}
```

*중요한 이유*: 디스크립터는 자막 언어나 원본 파일명과 유사한 정보를 소수화에 유용합니다.

### 기본 스트림 속성 표시

**개요** – 각 스크립트 스트림의 비트레이트, 보호, 언어 정보를 접근합니다.

```java
import com.groupdocs.metadata.core.AsfBaseStreamProperty;

class ReadBaseStreamProperties {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.asf")) {
            AsfRootPackage root = metadata.getRootPackageGeneric();
            com.groupdocs.metadata.core.AsfPackage asfPackage = root.getAsfPackage();

            for (AsfBaseStreamProperty property : asfPackage.getStreamProperties()) {
                System.out.println("Alternate bitrate: " + property.getAlternateBitrate());
                System.out.println("Average bitrate: " + property.getAverageBitrate());
                System.out.println("Average time per frame: " + property.getAverageTimePerFrame());
                System.out.println("Bitrate: " + property.getBitrate());
                System.out.println("Stream end time: " + property.getEndTime());
                System.out.println("Stream flags: " + property.getFlags());
                System.out.println("Stream language: " + property.getLanguage());
                System.out.println("Stream start time: " + property.getStartTime());
                System.out.println("Stream number: " + property.getStreamNumber());
            }
        }
    }
}
```

*중요한 이유*: 스트리밍 속성은 품질(비트율) 평가와 오디오/비디오 킹에 도움이 됩니다.

## 일반적인 문제 및 문제 해결

| 증상 | 원인 | 처리 방법 |
|------|-------------|----------|
| `getAsfPackage()` 호출 시 `NullPointerException` 발생 | 파일 오류가 잘못된 오류라면 ASF 오류가 아닙니다. | 영어를 확인하고 파일이 올바른 ASF 파일인지 확인하십시오. |
| 코덱 정보가 표시되지 않습니다 | ASF 파일이 리뷰어에서 인식하지 않는 독점적인 코덱을 사용합니다. | GroupDocs.Metadata를 최신 버전으로 업데이트하거나 사용자 정의 문서를 작성하는 것을 권장합니다. |
| 디스크립터 목록이 비어 있음 | 파일에 데이터 디스크가 저장되어 있지 않습니다(예: 세션 중 제거됨) | 메타데이터가 포함된 원본 파일을 사용하거나 데이터를 삭제하도록 옵션으로 다시 사용하세요. |

## 자주 묻는 질문

**Q: 동일한 라이브러리로 다른 비디오 형식의 메타데이터도 추출할 수 있나요?**
A: 네, GroupDocs.Metadata는 MP4, MKV, AVI 등 다양한 형식을 지원합니다. 해당 패키지 클래스를 인스턴스화하기만 하면 됩니다.

**Q: 추출 후 ASF 메타데이터를 수정할 수 있나요?**
A: 물론입니다. 이 라이브러리는 대부분의 속성에 대한 setter 메서드를 제공하므로 파일을 편집하고 저장할 수 있습니다.

**Q: 대용량 ASF 파일을 처리하려면 64비트 JVM이 필요한가요?**
A: 반드시 필요한 것은 아니지만, 64비트 JVM은 더 많은 힙 공간을 제공하여 대용량 미디어 파일을 처리할 때 도움이 됩니다.

**Q: 라이선스는 평가판 사용에 어떤 영향을 미치나요?**
A: 평가판 라이선스는 모든 기능 제한을 해제하지만 특정 출력물에 워터마크가 추가됩니다. 실제 사용 환경에서는 정식 라이선스를 구매하세요.

**Q: 이 코드를 Android에서 실행할 수 있나요?**
A: GroupDocs.Metadata는 Java SE용으로 개발되었습니다. Android의 경우 .NET 버전 또는 호환되는 래퍼를 사용해야 합니다.

## 결론

이 가이드를 통해 GroupDocs.Metadata for Java를 사용하여 **ASF 메타데이터를 추출**하는 방법을 알게 되었습니다. 기본 속성, 코덱 정보, 상세 설명자 및 스트림 속성을 읽어 미디어 자산에 대한 완벽한 가시성을 확보할 수 있습니다. 다음 단계로는 이 추출 기능을 일괄 처리 파이프라인에 통합하거나, 검색 가능한 메타데이터 데이터베이스를 구축하거나, 코드를 확장하여 ASF 파일을 수정하고 다시 저장하는 작업을 진행할 수 있습니다.

---

**최종 업데이트:** 2025년 12월 26일
**테스트 환경:** GroupDocs.Metadata 24.12 for Java
**작성자:** GroupDocs