---
date: '2026-06-22'
description: Узнайте, как извлечь подпись шрифта OpenType и детали цифровой подписи
  из шрифтов OpenType с использованием GroupDocs.Metadata для Java. Это руководство
  помогает защитить ваши документы.
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: Как извлечь подпись шрифта OpenType в Java с помощью GroupDocs.Metadata
type: docs
url: /ru/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Как извлечь подпись шрифта OpenType в Java с помощью GroupDocs.Metadata

В современных приложениях **извлечение подписи шрифта OpenType** является необходимым для подтверждения подлинности шрифта и защиты ваших цифровых активов. Этот учебник покажет вам шаг за шагом, как получить как флаги подписи, так и полные криптографические детали из шрифта OpenType с помощью **GroupDocs.Metadata for Java**. Независимо от того, создаёте ли вы ориентированный на безопасность конвейер контента или просто нужно провести аудит библиотеки шрифтов, приведённые ниже техники сделают ваш рабочий процесс надёжным и быстрым.

## Быстрые ответы
- **Какая библиотека нужна?** GroupDocs.Metadata for Java (v24.12)  
- **Какая версия Java требуется?** JDK 8 or later  
- **Нужна ли лицензия?** A free trial works for evaluation; a full license is required for production  
- **Можно ли обрабатывать несколько шрифтов?** Yes – batch or concurrent processing is supported  
- **Является ли код потокобезопасным?** Create a new `Metadata` instance per thread; the object itself isn’t thread‑safe  

## Что такое подпись шрифта OpenType?
**Подпись шрифта OpenType** — это криптографический блок, встроенный в шрифт, который подтверждает, что файл не был изменён после подписи. Он содержит время подписи, цепочку сертификатов, идентификаторы алгоритмов хеширования и необязательную информацию об отзывах. Также включён идентификатор алгоритма подписи, цепочка сертификатов подписанта и необязательные списки отзыва, что позволяет проводить всестороннюю проверку целостности и происхождения шрифта.

## Почему использовать GroupDocs.Metadata для Java?
GroupDocs.Metadata поддерживает **более 50 форматов ввода и вывода** (включая DOCX, PDF, PPTX, HTML и множество типов изображений) и может читать подписи OpenType без загрузки всего файла в память, что позволяет эффективно обрабатывать коллекции шрифтов, содержащие сотни страниц.

## Предварительные требования
- **Java Development Kit (JDK):** Версия 8 или новее.  
- **IDE:** Любая совместимая с Java IDE (IntelliJ IDEA, Eclipse, VS Code и т.д.).  
- **Maven:** Для управления зависимостями.  

### Требуемые библиотеки и зависимости
Добавьте координаты Maven GroupDocs.Metadata в ваш `pom.xml`. Это подтянет точный пакет, необходимый для примеров.

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

### Прямая загрузка
Либо скачайте последнюю версию с [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Приобретение лицензии
- **Free Trial:** Начните с бесплатной пробной версии, чтобы изучить возможности.  
- **Temporary License:** Получите временную лицензию через [страницу лицензирования GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **Purchase:** Для использования в продакшене приобретите полную лицензию.

## Как извлечь подпись шрифта OpenType с помощью GroupDocs.Metadata
`Metadata` — основной API GroupDocs.Metadata для доступа к метаданным документа без загрузки полного файла.  
Чтобы прочитать подпись шрифта, создайте объект `Metadata`, указав путь к файлу .otf, а затем получите его `DigitalSignaturePackage`. Такой подход загружает только необходимые структуры метаданных, избегая полного парсинга шрифта и экономя память. Экземпляр `Metadata` следует использовать внутри блока try‑with‑resources, чтобы обеспечить правильное освобождение ресурсов.

Загрузите ваш шрифт с помощью `new Metadata("font.otf")` внутри блока try‑with‑resources. Класс `Metadata` является точкой входа GroupDocs.Metadata для чтения любого поддерживаемого типа документа, включая шрифты OpenType. Объект автоматически закрывается, предотвращая утечки ресурсов.

### Как извлечь флаги цифровой подписи
Объект `DigitalSignaturePackage` собирает всю информацию, связанную с подписью шрифта, включая флаги и отдельные подписи.  
**Прямой ответ:** Вызовите `metadata.getDigitalSignaturePackage().getFlags()` после открытия шрифта; возвращённый набор флагов указывает, действительна ли подпись, отозвана ли она или имеет специальные условия. Этот один вызов даёт быструю проверку состояния перед углублением в детали. Флаги представлены как перечисление, которое можно проанализировать для определения статуса подписи, наличия метки времени и любых ограничений политики, применённых при подписи.

1. Инициализируйте экземпляр `Metadata`, указывающий на ваш файл шрифта.  
2. Получите `DigitalSignaturePackage`.  
3. Выведите или запишите значения флагов.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Объяснение**  
- `documentPath` – абсолютный или относительный путь к шрифту OpenType.  
- Блок try‑with‑resources гарантирует автоматическое закрытие объекта `Metadata`, предотвращая утечки памяти.

### Как извлечь подробную информацию о цифровой подписи
`CmsSignature` представляет отдельную подпись CMS/PKCS#7, встроенную в шрифт, предоставляя доступ к её криптографическим свойствам.  
**Прямой ответ:** Пройдитесь по `metadata.getDigitalSignaturePackage().getSignatures()`; каждый объект `CmsSignature` раскрывает время подписи, алгоритмы хеширования, инкапсулированное содержимое и детали сертификата, позволяя сформировать полный отчёт аудита. Для каждой подписи можно получить цепочку сертификатов подписанта, проверить алгоритм хеша и извлечь любые токены метки времени, чтобы подтвердить момент применения подписи.

1. Повторно используйте ту же инициализацию `Metadata`, как выше.  
2. Пройдитесь по каждому `CmsSignature` в пакете.  
3. Извлеките свойства, такие как `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()` и `getSignerInfo()`.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**Объяснение ключевых разделов**  
- **Sign Time:** Временная метка, когда подпись была применена.  
- **Digest Algorithms & OIDs:** Используемые алгоритмы хеширования (например, SHA‑256).  
- **Encapsulated Content:** Любые дополнительные данные, заключённые в подпись.  
- **Certificates:** Даты действия и размер необработанных данных помогают проверить личность подписанта.  
- **Signers:** Предоставляет выбор алгоритмов каждого подписанта и метки времени подписи.

#### Советы по устранению неполадок
- Если у шрифта отсутствует цифровая подпись, `getDigitalSignaturePackage()` возвращает `null`. Всегда проверяйте `null` перед доступом к флагам или подписям.  
- Убедитесь, что используете ту же версию **GroupDocs.Metadata**, указанную в зависимости Maven, чтобы избежать проблем совместимости.  

## Практические применения
Извлечение подписей шрифтов OpenType ценно во многих реальных сценариях:

1. **Document Verification:** Автоматизировать проверку подписанных файлов шрифтов в системе управления контентом.  
2. **Digital Asset Management:** Проверять подлинность шрифтов перед их использованием в проектах брендинга.  
3. **Security Audits:** Анализировать детали подписи для обеспечения соответствия внутренним политикам безопасности.

## Соображения по производительности
- **Resource Management:** Используйте try‑with‑resources для быстрого закрытия объектов `Metadata`.  
- **Batch Processing:** Обрабатывайте шрифты группами, чтобы минимизировать нагрузку ввода‑вывода; GroupDocs.Metadata может работать с тысячами файлов, не загружая каждый шрифт полностью в память.  
- **Concurrency:** Запускайте отдельные экземпляры `Metadata` в параллельных потоках для масштабных задач; библиотека не является потокобезопасной на уровне экземпляра, поэтому каждый поток должен иметь свой отдельный экземпляр.

## Часто задаваемые вопросы

**Q: Можно ли извлечь подписи из шрифта, у которого нет цифровой подписи?**  
A: `DigitalSignaturePackage` будет `null`; always check for this condition before accessing flags or details.

**Q: Какая версия GroupDocs.Metadata требуется?**  
A: The examples target version **24.12**, but newer releases remain backward compatible for OpenType fonts.

**Q: Нужна ли специальная лицензия для чтения подписей?**  
A: A trial license works for evaluation; a full license is required for production use.

**Q: Как работать со шрифтами, хранящимися в облачном бакете?**  
A: Download the font to a temporary local file, then pass its path to `Metadata`. The library works with any file accessible via a local path.

**Q: Можно ли проверить криптографическую валидность подписи?**  
A: GroupDocs.Metadata provides raw signature data; you can feed the certificate chain and hash values into a separate crypto library to perform full verification.

## Заключение
Следуя этому руководству, вы теперь знаете **как извлечь информацию о подписи шрифта OpenType** и подробные данные цифровой подписи с помощью **GroupDocs.Metadata for Java**. Интеграция этих шагов в ваши приложения усиливает безопасность документов, упрощает проверку активов и поддерживает инициативы по соблюдению требований.

**Следующие шаги**  
- Поэкспериментируйте с пакетной обработкой для эффективного управления большими библиотеками шрифтов.  
- Скомбинируйте извлечённые данные с вашими инструментами аудита безопасности для автоматической отчётности о соответствии.  
- Исследуйте другие возможности работы с метаданными в GroupDocs.Metadata, такие как редактирование или удаление подписей при необходимости.

---

**Последнее обновление:** 2026-06-22  
**Тестировано с:** GroupDocs.Metadata 24.12  
**Автор:** GroupDocs

## Связанные руководства

- [Доступ к метаданным Word‑документов с GroupDocs в Java&#58; Полное руководство](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Как извлечь пользовательские метаданные из PDF с помощью GroupDocs.Metadata в Java&#58; Полное руководство](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)