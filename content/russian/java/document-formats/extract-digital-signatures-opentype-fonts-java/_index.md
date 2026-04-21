---
date: '2026-01-24'
description: Узнайте, как извлекать сведения о подписи и цифровой подписи из шрифтов
  OpenType с помощью GroupDocs.Metadata для Java. Этот пошаговый руководствo повышает
  безопасность документов.
keywords:
- extract digital signatures OpenType fonts Java
- digital signature flags OpenType fonts
- GroupDocs Metadata Java
title: Как извлечь подпись из шрифтов OpenType в Java с помощью GroupDocs.Metadata
type: docs
url: /ru/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Как извлечь подпись из шрифтов OpenType в Java с помощью GroupDocs.Metadata

## Введение
В современную цифровую эпоху **как извлечь подпись** из файлов шрифтов — частая потребность разработчиков, которым необходимо проверять подлинность и поддерживать целостность. Этот учебник проведёт вас через процесс извлечения флагов цифровой подписи и подробных данных подписи из шрифтов OpenType с использованием **GroupDocs.Metadata for Java**. Независимо от того, создаёте ли вы систему управления документами, приложение, ориентированное на безопасность, или просто хотите провести аудит шрифтовых ресурсов, освоение этого процесса сделает ваш рабочий процесс более надёжным и защищённым.

**Что вы узнаете**
- Как извлечь флаги цифровой подписи из шрифтов OpenType  
- Как получить подробную информацию о каждой цифровой подписи  
- Как настроить и использовать GroupDocs.Metadata в Java‑проекте  

Перейдём к предварительным требованиям и подготовим вашу среду.

## Быстрые ответы
- **Какая библиотека нужна?** GroupDocs.Metadata for Java (v24.12)  
- **Какая версия Java требуется?** JDK 8 или новее  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для оценки; полная лицензия требуется для продакшн‑использования  
- **Можно ли обрабатывать несколько шрифтов?** Да — используйте пакетную или параллельную обработку для больших наборов  
- **Безопасен ли код для многопоточного использования?** Объект `Metadata` одноразовый; создавайте новый экземпляр для каждого потока  

## Предварительные требования
Прежде чем извлекать данные цифровой подписи, убедитесь, что ваша настройка соответствует следующим требованиям:

### Необходимые библиотеки и зависимости
Для работы с GroupDocs.Metadata for Java включите репозиторий Maven и зависимость, показанные ниже.

### Требования к настройке среды
- **Java Development Kit (JDK):** Установите JDK 8 или новее.  
- **IDE:** Любая совместимая с Java IDE (IntelliJ IDEA, Eclipse, VS Code и т.д.).

### Требования к знаниям
Базовое знакомство с Java и понимание цифровых подписей будет полезным, но руководство содержит понятные объяснения для новичков.

## Настройка GroupDocs.Metadata для Java
### Установка через Maven
Добавьте следующую конфигурацию в ваш файл `pom.xml`. Это подтянет пакет **groupdocs metadata java**, необходимый для примеров.

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
Либо скачайте последнюю версию по ссылке [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Приобретение лицензии
- **Бесплатная пробная версия:** Начните с пробного периода, чтобы изучить возможности.  
- **Временная лицензия:** При необходимости получите временную лицензию, посетив [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license).  
- **Покупка:** Для полного доступа рассмотрите покупку лицензии.

После установки библиотеки и получения лицензии вы можете приступить к извлечению подписей.

## Что такое цифровая подпись в шрифте OpenType?
Цифровая подпись, встроенная в шрифт OpenType, гарантирует, что файл шрифта не был изменён после подписания. Подпись содержит криптографическую информацию, такую как время подписи, сертификаты и алгоритмы хеширования, которые можно программно прочитать с помощью GroupDocs.Metadata.

## Как извлечь флаги цифровой подписи
### Обзор
Извлечение флагов цифровой подписи позволяет быстро определить статус и свойства подписи (например, действительна ли она, отозвана или имеет специальные условия).

### Шаги реализации
1. **Инициализировать Metadata:** Создайте экземпляр `Metadata`, указывающий на ваш файл шрифта.  
2. **Прочитать флаги:** Получите `DigitalSignaturePackage` и выведите его флаги.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Пояснение**
- `documentPath` – абсолютный или относительный путь к шрифту OpenType.  
- Блок `try‑with‑resources` гарантирует автоматическое закрытие объекта `Metadata`, предотвращая утечки ресурсов.

## Как извлечь подробную информацию о цифровой подписи
### Обзор
Помимо флагов, часто требуется изучить метаданные каждой подписи — время подписи, алгоритмы, сертификаты и инкапсулированное содержимое.

### Шаги реализации
1. **Инициализировать Metadata** (как выше).  
2. **Итерировать подписи:** Для каждой `CmsSignature` выведите соответствующие свойства.

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

**Пояснение ключевых разделов**
- **Sign Time:** Когда была применена подпись.  
- **Digest Algorithms & OIDs:** Используемые алгоритмы хеширования (например, SHA‑256).  
- **Encapsulated Content:** Любые дополнительные данные, упакованные внутри подписи.  
- **Certificates:** Даты действия и размер необработанных данных помогают проверить подлинность подписанта.  
- **Signers:** Предоставляет информацию о выбранных подписантом алгоритмах и времени подписи.

### Советы по устранению неполадок
- Убедитесь, что шрифт действительно содержит цифровую подпись; иначе `getDigitalSignaturePackage()` вернёт `null`.  
- Проверьте, что вы используете ту же версию **GroupDocs.Metadata**, что указана в зависимости Maven, чтобы избежать проблем совместимости.  

## Практические применения
Извлечение данных цифровой подписи из шрифтов OpenType полезно в различных сценариях:
1. **Проверка документов:** Автоматизируйте проверку подписанных файлов шрифтов в системе управления контентом.  
2. **Управление цифровыми активами:** Валидируйте подлинность шрифтов перед их использованием в брендинговых проектах.  
3. **Аудит безопасности:** Анализируйте детали подписи, чтобы обеспечить соответствие внутренним политикам безопасности.

## Соображения по производительности
- **Управление ресурсами:** Всегда используйте `try‑with‑resources` для своевременного закрытия объектов `Metadata`.  
- **Пакетная обработка:** При работе с большим количеством шрифтов обрабатывайте их пакетами, чтобы снизить нагрузку ввода‑вывода.  
- **Параллелизм:** Для масштабных нагрузок запускайте отдельные экземпляры `Metadata` в параллельных потоках; библиотека не является потокобезопасной для одного экземпляра.

## Часто задаваемые вопросы

**В: Можно ли извлечь подписи из шрифта, у которого нет цифровой подписи?**  
О: `DigitalSignaturePackage` будет `null`; перед доступом к флагам или деталям необходимо проверять это условие.

**В: Какая версия GroupDocs.Metadata требуется?**  
О: Примеры используют версию **24.12**, но более новые версии совместимы с шрифтами OpenType.

**В: Нужна ли специальная лицензия для чтения подписей?**  
О: Пробная лицензия подходит для оценки; полная лицензия требуется для продакшн‑использования.

**В: Какранящимися в облачном бакете?**  
О: Скачайте шрифт во временный локальный файл, затем передайте его путь в `Metadata`. Библиотека работает с любым файлом, доступным по локальному пути.

**В: Можно ли проверить криптографическую валидность подписи?**  
О: GroupDocs.Metadata предоставляет необработанные данные; их можно передать в отдельную криптографическую библиотеку вместе с цепочкой сертификатов и хеш‑значениями для полной проверки.

## Заключение
Следуя этому руководству, вы теперь знаете **как извлечь подпись** и подробные данные цифровой подписи из шрифтов OpenType с помощью **GroupDocs.Metadata for Java**. Интеграция этих техник в ваши приложения усилит безопасность документов, упростит проверку активов и поддержит инициативы по соответствию требованиям.

**Следующие шаги**
- Поэкспериментируйте с пакетной обработкой для работы с большими библиотеками шрифтов.  
- Скомбинируйте извлечённые данные с вашими инструментами аудита безопасности для автоматизированного отчётности о соответствии.  
- Исследуйте другие возможности GroupDocs.Metadata, такие как редактирование или удаление подписей при необходимости.

---

**Последнее обновление:** 2026-01-24  
**Тестировано с:** GroupDocs.Metadata 24.12