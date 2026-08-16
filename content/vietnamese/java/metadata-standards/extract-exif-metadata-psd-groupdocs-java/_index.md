---
date: '2026-08-10'
description: Tìm hiểu cách trích xuất siêu dữ liệu EXIF từ tệp PSD bằng GroupDocs.Metadata
  cho Java. Hướng dẫn này bao gồm việc trích xuất cơ bản, các gói IFD, dữ liệu GPS
  và các trường hợp sử dụng thực tế.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Tìm hiểu cách trích xuất siêu dữ liệu EXIF từ tệp PSD bằng GroupDocs.Metadata
  cho Java. Hướng dẫn từng bước, đoạn mã mẫu và mẹo khắc phục sự cố dành cho nhà phát
  triển.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Cách trích xuất siêu dữ liệu EXIF từ tệp PSD bằng GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: Cách trích xuất siêu dữ liệu EXIF từ tệp PSD bằng GroupDocs.Metadata
type: docs
url: /vi/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Cách trích xuất siêu dữ liệu EXIF từ tệp PSD bằng GroupDocs.Metadata

Trích xuất **siêu dữ liệu EXIF** từ các tệp PSD là một bước thường xuyên nhưng mạnh mẽ khi bạn cần kiểm tra nguồn gốc hình ảnh, tự động gắn thẻ tài sản, hoặc xây dựng thư viện phương tiện có thể tìm kiếm. Trong hướng dẫn này, bạn sẽ khám phá **cách trích xuất EXIF** nhanh chóng với GroupDocs.Metadata cho Java, xem các lời gọi API chính xác, và học cách xử lý các gói IFD nâng cao và tọa độ GPS. Khi hoàn thành, bạn sẽ sẵn sàng tích hợp việc trích xuất siêu dữ liệu vào bất kỳ quy trình làm việc nào dựa trên Java.

## Câu trả lời nhanh
Lớp `Metadata` đại diện cho một tệp và cung cấp quyền truy cập vào siêu dữ liệu của nó.

- **Dòng mã đầu tiên là gì?** `Metadata metadata = new Metadata("sample.psd");`
- **Phương thức nào trả về tên nghệ sĩ?** `metadata.getExif().getArtist();`
- **Tôi có thể đọc dữ liệu GPS không?** Có – sử dụng `metadata.getExif().getGpsInfo();`
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép GroupDocs.Metadata hợp lệ sau thời gian dùng thử.
- **Phiên bản Java được hỗ trợ?** Java 8 hoặc mới hơn (tới Java 21).

## Siêu dữ liệu EXIF là gì?
Siêu dữ liệu EXIF (Exchangeable Image File Format) lưu trữ các cài đặt máy ảnh, thời gian tạo và dữ liệu vị trí bên trong các tệp hình ảnh. GroupDocs.Metadata đọc thông tin này trực tiếp từ cấu trúc nhị phân của các tệp PSD, cung cấp qua một API Java sạch sẽ. Nó cho phép các nhà phát triển lấy các chi tiết như mẫu máy ảnh, thời gian phơi sáng và tọa độ GPS một cách lập trình mà không cần kiểm tra thủ công.

## Tại sao nên sử dụng GroupDocs.Metadata cho Java?
GroupDocs.Metadata hỗ trợ **hơn 30 định dạng tệp** (bao gồm PSD, JPEG, PNG, TIFF) và có thể xử lý các tệp lên tới **2 GB** mà không cần tải toàn bộ tài liệu vào bộ nhớ. Thư viện trích xuất **hơn 150 thẻ EXIF riêng biệt**, đảm bảo bạn có đầy đủ các thuộc tính máy ảnh và GPS cần thiết cho phân tích hoặc tuân thủ.

## Yêu cầu trước
- **Java Development Kit (JDK) 8** hoặc mới hơn đã được cài đặt trên máy của bạn.  
- **Maven** để quản lý phụ thuộc.  
- **GroupDocs.Metadata cho Java phiên bản 24.12** (hoặc mới hơn).  
- Kiến thức cơ bản về các lớp Java, đối tượng và xử lý ngoại lệ.

### Thư viện và phụ thuộc cần thiết
| Phụ thuộc | Tọa độ Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Cài đặt môi trường
Bạn nên có một IDE tương thích Maven như IntelliJ IDEA hoặc Eclipse. Tạo một dự án Maven mới hoặc thêm phụ thuộc vào dự án hiện có.

## Cách thiết lập GroupDocs.Metadata cho Java
GroupDocs.Metadata có thể được thêm vào dự án Maven với một vài dòng cấu hình. Các bước sau cho thấy cách bao gồm kho lưu trữ và phụ thuộc để thư viện có sẵn trên classpath.

### Cấu hình Maven
Thêm đoạn mã sau vào `pom.xml` của bạn trong phần `<dependencies>`:

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

### Tải trực tiếp
Ngoài ra, tải JAR mới nhất từ trang phát hành chính thức: [GroupDocs.Metadata cho Java - trang phát hành](https://releases.groupdocs.com/metadata/java/).

### Nhận giấy phép
Để chạy thư viện vượt quá thời gian dùng thử 30 ngày, hãy lấy giấy phép tạm thời hoặc đầy đủ:

1. Truy cập [Trang mua giấy phép](https://purchase.groupdocs.com/temporary-license).  
2. Chọn **temporary** để thử nghiệm hoặc **full** cho môi trường sản xuất.  
3. Thực hiện các hướng dẫn trên màn hình để nhúng tệp giấy phép (`metadata.lic`) vào classpath Java của bạn.

### Khởi tạo và cài đặt cơ bản
Sau khi thư viện đã có trên classpath, khởi tạo nó như sau:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Cách trích xuất các thuộc tính siêu dữ liệu EXIF cơ bản từ hình ảnh PSD
Phần này giải thích cách tải tệp PSD, truy cập container EXIF và đọc các thẻ phổ biến nhất như **artist**, **copyright**, và **software**. Quá trình bao gồm tạo một thể hiện `Metadata`, gọi `getExif()`, và sau đó lấy các thuộc tính riêng lẻ bằng các phương thức getter đơn giản.

### Triển khai từng bước
1. **Tạo một thể hiện `Metadata`** trỏ tới tệp PSD của bạn.  
2. **Gọi `getExif()`** để lấy container EXIF.  
3. **Đọc các thuộc tính riêng lẻ** như `getArtist()`, `getCopyright()`, và `getSoftware()`.  
4. **In ra hoặc lưu** các giá trị theo logic ứng dụng của bạn.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Mẹo chuyên nghiệp:** Đối tượng `Metadata` tự động phát hiện định dạng tệp, vì vậy bạn có thể tái sử dụng cùng một đoạn mã cho các tệp JPEG hoặc TIFF mà không cần sửa đổi.

## Cách trích xuất các thuộc tính gói EXIF IFD từ hình ảnh PSD
Phần IFD (Image File Directory) chứa các chi tiết kỹ thuật sâu hơn như **camera serial number**, **lens model**, và **user comments**. `Ifd0` đại diện cho Image File Directory chính chứa thông tin cơ bản về máy ảnh. Việc trích xuất các trường này hữu ích cho phân tích pháp y hoặc lập danh mục độ chính xác cao.

### Các bước triển khai
1. **Tái sử dụng thể hiện `Metadata`** từ phần trước.  
2. **Điều hướng tới container IFD** qua `metadata.getExif().getIfd0()`.  
3. **Đọc các thuộc tính** như `getBodySerialNumber()` và `getUserComment()`.  
4. **Xuất dữ liệu** hoặc ánh xạ chúng vào mô hình miền của bạn.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Cách lấy dữ liệu GPS (vĩ độ, kinh độ) từ tệp PSD
Nhiều máy ảnh hiện đại nhúng tọa độ GPS trong khối EXIF. `GpsInfo` chứa các tọa độ địa lý được trích xuất từ dữ liệu EXIF. Gọi `metadata.getExif().getGpsInfo()` và sau đó sử dụng `getLatitude()`, `getLongitude()`, và `getAltitude()` để lấy dữ liệu vị trí chính xác—không cần phân tích thêm.

### Các bước chi tiết
1. **Lấy đối tượng GPS**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Đọc vĩ độ và kinh độ**: `gps.getLatitude()` trả về `double` ở độ thập phân.  
3. **Xử lý dữ liệu thiếu**: API trả về `null` nếu thẻ không tồn tại, vì vậy cần kiểm tra tránh `NullPointerException`.  

> **Cạm bẫy thường gặp:** Một số tệp PSD lưu tọa độ GPS dưới dạng số hữu tỉ; thư viện sẽ tự động chuẩn hoá chúng, nhưng các tệp cũ hơn có thể cần chuyển đổi thủ công.  

## Các vấn đề thường gặp và khắc phục
| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|--------------------|----------------|
| `Unsupported format` exception | Sử dụng phiên bản GroupDocs.Metadata cũ không nhận diện PSD | Nâng cấp lên phiên bản 24.12 hoặc mới hơn |
| `NullPointerException` khi gọi `getArtist()` | Thẻ EXIF không có trong tệp nguồn | Kiểm tra `metadata.getExif().hasArtist()` trước khi đọc |
| Lỗi giấy phép sau 30 ngày | Không tìm thấy tệp giấy phép trên classpath | Đặt `metadata.lic` trong `src/main/resources` hoặc gọi `Metadata.setLicense("path/to/license")` |

## Câu hỏi thường gặp

**Q: Tôi có thể trích xuất siêu dữ liệu EXIF từ tệp PSD được bảo vệ bằng mật khẩu không?**  
A: Có. Tải tệp bằng `new Metadata("file.psd", "password")` và sau đó truy cập dữ liệu EXIF như bình thường.

**Q: GroupDocs.Metadata có hỗ trợ xử lý hàng loạt nhiều tệp PSD không?**  
A: Hoàn toàn có. Tạo một đối tượng `Metadata` trong vòng lặp, hoặc sử dụng trợ giúp `MetadataCollection` để xử lý thư mục một cách hiệu quả.

**Q: Các phiên bản Java nào được hỗ trợ chính thức?**  
A: Java 8 đến Java 21 đều được kiểm tra đầy đủ. Thư viện chỉ sử dụng các API chuẩn, vì vậy hoạt động trên bất kỳ JVM tuân thủ nào.

**Q: Có thể ghi lại dữ liệu EXIF vào tệp PSD không?**  
A: Có. Sau khi chỉnh sửa các thuộc tính qua đối tượng `Exif`, gọi `metadata.save("output.psd")` để lưu thay đổi.

**Q: Thư viện có thể xử lý tệp PSD lớn bao nhiêu mà không hết bộ nhớ?**  
A: GroupDocs.Metadata truyền dữ liệu theo luồng và có thể xử lý các tệp lên tới **2 GB** trên máy có RAM khoảng 8 GB, nhờ kiến trúc tiêu thụ bộ nhớ thấp.

## Kết luận
Bạn hiện đã biết **cách trích xuất EXIF** từ các tệp PSD bằng GroupDocs.Metadata cho Java, từ các thẻ cơ bản đến IFD nâng cao và thông tin GPS. Tích hợp các đoạn mã này vào quy trình xử lý hình ảnh của bạn để tự động hoá việc lập danh mục, kiểm tra tuân thủ, hoặc cung cấp dịch vụ dựa trên vị trí. Để khám phá sâu hơn, hãy thử trích xuất siêu dữ liệu từ các định dạng hỗ trợ khác (JPEG, TIFF, PNG) hoặc thử nghiệm khả năng ghi lại để nhúng các thẻ tùy chỉnh.

---

**Cập nhật lần cuối:** 2026-08-10  
**Kiểm tra với:** GroupDocs.Metadata 24.12 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Trích xuất tài nguyên hình ảnh từ tệp PSD bằng GroupDocs.Metadata trong Java: Hướng dẫn toàn diện](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Trích xuất tiêu đề và thông tin lớp PSD bằng GroupDocs.Metadata cho Java: Hướng dẫn toàn diện](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Trích xuất thuộc tính MakerNote dưới dạng thẻ TIFF/EXIF bằng GroupDocs.Metadata trong Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)