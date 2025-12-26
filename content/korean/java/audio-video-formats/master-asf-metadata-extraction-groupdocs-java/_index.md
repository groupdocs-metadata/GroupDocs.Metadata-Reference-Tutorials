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

# Extract ASF Metadata with GroupDocs.Metadata for Java

**Introduction**

오늘날 디지털 환경에서는 멀티미디어 콘텐츠를 효율적으로 관리하는 것이 매우 중요합니다. 미디어 파일에서 **ASF 메타데이터를 추출**해야 할 경우, 수동으로 수행하면 시간도 많이 걸리고 오류가 발생하기 쉽습니다. 이 튜토리얼에서는 **GroupDocs.Metadata for Java**를 사용하여 다양한 ASF 속성을 읽고 표시하는 방법을 단계별로 안내합니다. 이를 통해 자산을 체계적으로 정리하고, 검색하며, 자신 있게 처리할 수 있습니다.

### What You’ll Learn
- Java 프로젝트에 GroupDocs.Metadata를 설정하는 방법  
- 생성 날짜, 파일 ID, 플래그와 같은 **ASF 메타데이터를 추출**하는 방법  
- ASF 파일에 포함된 코덱 정보를 읽는 방법  
- 상세 메타데이터 디스크립터와 베이스 스트림 속성을 표시하는 방법  

필수 사전 준비 사항을 확인해 보겠습니다.

## Quick Answers
- **What does “extract ASF metadata” mean?** 프로그래밍 방식으로 ASF 파일에서 임베드된 정보(예: 타임스탬프, 코덱, 디스크립터)를 읽는 것을 의미합니다.  
- **Which library is required?** GroupDocs.Metadata for Java (버전 24.12 이상).  
- **Do I need a license?** 개발 단계에서는 무료 체험 또는 임시 라이선스로 충분하지만, 프로덕션에서는 정식 라이선스가 필요합니다.  
- **What Java version is supported?** JDK 8 이상.  
- **Can I use Maven?** 예 – Maven이 권장되는 의존성 관리 도구입니다.

## Prerequisites

- **Java Development Kit (JDK)** 8 이상 설치  
- **IDE**(IntelliJ IDEA 또는 Eclipse 등) 사용 권장  
- **Maven**을 IDE에 설정(선택 사항이지만 권장)  
- Java와 외부 라이브러리에 대한 기본 지식

## Setting Up GroupDocs.Metadata for Java

### Maven Installation

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

### Direct Download

Maven을 사용하지 않으려면 최신 JAR 파일을 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)에서 다운로드하십시오.

### Licensing Overview

- **Free Trial** – GroupDocs 웹사이트에서 평가용으로 제공  
- **Temporary License** – 개발 중 모든 기능을 제한 없이 사용할 수 있음  
- **Full License** – 상업적·프로덕션 환경에 필요

### Basic Initialization

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

## What Is ASF Metadata?

ASF(Advanced Systems Format)는 Microsoft 스트리밍 포맷으로 오디오, 비디오 및 메타데이터를 하나의 컨테이너에 저장합니다. 메타데이터에는 생성 타임스탬프, 코덱 세부 정보, 스트림 디스크립터 등이 포함됩니다. **ASF 메타데이터를 추출**하면 파일 출처, 인코딩 파라미터, 콘텐츠 설명 등에 대한 프로그래밍적 인사이트를 얻을 수 있어 미디어 라이브러리, 트랜스코딩 파이프라인, 규정 준수 감사 등에 필수적입니다.

## Why Extract ASF Metadata with GroupDocs.Metadata?

- **Zero‑code parsing** – 저수준 ASF 파서를 직접 구현할 필요 없음  
- **Rich object model** – 직관적인 Java 클래스를 통해 속성, 코덱, 디스크립터, 스트림 세부 정보를 손쉽게 접근  
- **Cross‑platform** – Java를 지원하는 모든 OS에서 동작  
- **License flexibility** – 체험판으로 시작해 필요에 따라 정식 라이선스로 전환 가능

## Implementation Guide

아래 섹션에서는 **ASF 메타데이터를 추출**하는 구체적인 코드 스니펫을 단계별로 살펴봅니다.

### Reading Basic ASF Metadata Properties

**Overview** – 생성 날짜, 파일 ID, 플래그와 같은 기본 정보를 가져옵니다.

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

*Why it matters*: 생성 날짜를 알면 버전 관리를 용이하게 하고, 파일 ID는 시스템 전반에서 자산을 고유하게 식별하는 데 도움이 됩니다.

### Displaying ASF Codec Information

**Overview** – 오디오 및 비디오 스트림에 사용된 코덱을 열거합니다.

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

*Why it matters*: 코덱 세부 정보는 재생 장치와의 호환성을 확인하거나 트랜스코딩 여부를 판단할 때 필수적입니다.

### Displaying Metadata Descriptors

**Overview** – 언어, 스트림 번호, 원본 제목 등 상세 디스크립터를 가져옵니다.

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

*Why it matters*: 디스크립터는 자막 언어나 원본 파일명과 같은 컨텍스트 정보를 제공해 카탈로그화에 유용합니다.

### Displaying Base Stream Properties

**Overview** – 각 베이스 스트림의 비트레이트, 타이밍, 언어 정보를 접근합니다.

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

*Why it matters*: 스트림 속성은 품질(비트레이트) 평가와 오디오/비디오 동기화에 도움이 됩니다.

## Common Issues & Troubleshooting

| 증상 | 가능한 원인 | 해결 방법 |
|------|-------------|----------|
| `getAsfPackage()` 호출 시 `NullPointerException` 발생 | 파일 경로가 잘못되었거나 파일이 유효한 ASF 컨테이너가 아닙니다. | 경로를 확인하고 파일이 올바른 ASF 파일인지 확인하십시오. |
| 코덱 정보가 표시되지 않음 | ASF 파일이 라이브러리 버전에서 인식하지 못하는 독점 코덱을 사용합니다. | GroupDocs.Metadata를 최신 버전으로 업데이트하거나 사용자 정의 코덱 파서를 사용하십시오. |
| 디스크립터 목록이 비어 있음 | 파일에 메타데이터 디스크립터가 없으며(예: 인코딩 중 제거됨) | 메타데이터가 포함된 원본 파일을 사용하거나 메타데이터 보존 옵션으로 다시 인코딩하십시오. |

## Frequently Asked Questions

**Q: Can I extract metadata from other video formats with the same library?**  
A: Yes, GroupDocs.Metadata supports MP4, MKV, AVI, and many more. Just instantiate the appropriate package class.

**Q: Is it possible to modify ASF metadata after extraction?**  
A: Absolutely. The library provides setter methods for most properties, allowing you to edit and then save the file.

**Q: Do I need a 64‑bit JVM for large ASF files?**  
A: Not necessarily, but a 64‑bit JVM gives you more heap space, which helps when processing very large media files.

**Q: How does licensing affect trial usage?**  
A: The trial license removes all functional limits but adds a watermark to certain outputs. For production, purchase a full license.

**Q: Can I run this code on Android?**  
A: GroupDocs.Metadata is built for Java SE; for Android you’d need to use the .NET version or a compatible wrapper.

## Conclusion

By following this guide, you now know how to **extract ASF metadata** using GroupDocs.Metadata for Java. You can read basic properties, codec information, detailed descriptors, and stream attributes—giving you full visibility into your media assets. Next steps include integrating this extraction into batch processing pipelines, building searchable metadata databases, or extending the code to modify and re‑save ASF files.

---

**Last Updated:** 2025-12-26  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs