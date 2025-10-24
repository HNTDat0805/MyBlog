---
title: "XỬ LÝ NGOẠI LỆ"
date: 2025-10-23
draft: false
description: "Tìm hiểu cách quản lý lỗi bằng try-catch-finally, các loại ngoại lệ, và cách thao tác cơ bản với File I/O trong Java."
tags: ["java", "exception", "ngoại lệ", "try-catch", "file", "io"]
---

### I. Xử Lý Ngoại Lệ (Exception Handling)

Khi chương trình gặp lỗi trong quá trình thực thi, Java sinh ra **ngoại lệ (Exception)**. Xử lý ngoại lệ là kỹ thuật giúp chương trình không bị dừng đột ngột (crash).

#### 1. Khối `try-catch-finally`

Đây là cấu trúc cơ bản để quản lý ngoại lệ:

- **`try`:** Chứa đoạn code có khả năng sinh ra lỗi.
- **`catch`:** Bắt và xử lý loại ngoại lệ cụ thể nếu lỗi xảy ra.
- **`finally`:** Khối code **luôn luôn** được thực thi, dù ngoại lệ có xảy ra hay không (thường dùng để dọn dẹp tài nguyên).

```java
try {
    // Code có thể gây lỗi (ví dụ: chia cho 0)
    int ketQua = 10 / 0;
    System.out.println(ketQua);
} catch (ArithmeticException e) {
    // Bắt và xử lý ngoại lệ chia cho 0
    System.out.println("Lỗi: Không thể chia cho 0.");
} finally {
    // Luôn chạy
    System.out.println("Quá trình tính toán kết thúc.");
}
```

#### 2. Các Loại Ngoại Lệ Chính

Java phân loại ngoại lệ thành ba nhóm chính, tất cả đều là các lớp con của Throwable:

| Loại Ngoại Lệ | Mô tả                                                                       | Bắt buộc xử lý?                           | Ví dụ phổ biến                                |
| :------------ | :-------------------------------------------------------------------------- | :---------------------------------------- | :-------------------------------------------- |
| **Checked**   | Lỗi có thể phục hồi, thường liên quan đến môi trường bên ngoài (tệp, mạng). | **Bắt buộc** (`try-catch` hoặc `throws`). | `IOException`, `SQLException`                 |
| **Unchecked** | Lỗi lập trình (logic sai, dữ liệu không hợp lệ).                            | **Không bắt buộc** (Nên sửa code).        | `NullPointerException`, `ArithmeticException` |
| **Error**     | Lỗi nghiêm trọng ngoài tầm kiểm soát của ứng dụng.                          | Không (Không thể phục hồi).               | `OutOfMemoryError`, `StackOverflowError`      |

#### 3. Từ Khóa throws

Dùng để ủy quyền việc xử lý ngoại lệ cho phương thức gọi nó. Chỉ sử dụng cho Checked Exceptions.

```java
// Phương thức này thông báo nó có thể ném ra IOException
public void docTep() throws IOException {
    // Giả sử code đọc tệp ở đây
    throw new IOException("Không tìm thấy tệp.");
}
```

### II. Làm Việc Với Tệp (File I/O)

I/O (Input/Output) là quá trình chương trình tương tác với thế giới bên ngoài (tệp, mạng, console).

#### 1. Lớp File

Lớp java.io.File được dùng để đại diện cho một tệp hoặc thư mục trong hệ thống, chứ không phải nội dung bên trong tệp.

```java
import java.io.File;

// Tạo đối tượng đại diện cho tệp 'data.txt'
File tep = new File("data.txt");

// Các phương thức cơ bản
boolean tonTai = tep.exists();
boolean daTao = tep.createNewFile(); // Tạo tệp mới
```

#### 2. Đọc Dữ Liệu từ Tệp

Thường dùng lớp Scanner (cho văn bản đơn giản) hoặc BufferedReader (cho hiệu suất cao).

```java
import java.io.File;
import java.util.Scanner;

try {
    File myObj = new File("ten_tep.txt");
    Scanner myReader = new Scanner(myObj);

    while (myReader.hasNextLine()) {
        String data = myReader.nextLine();
        System.out.println(data);
    }
    myReader.close();
} catch (FileNotFoundException e) {
    System.out.println("Không tìm thấy tệp.");
}
```

#### 3. Ghi Dữ Liệu vào Tệp

Thường dùng lớp FileWriter hoặc PrintWriter.

```java
import java.io.FileWriter;
import java.io.IOException;

try {
    // Tham số 'true' nghĩa là ghi tiếp (append), nếu là 'false' sẽ ghi đè
    FileWriter writer = new FileWriter("ten_tep_ghi.txt", true);
    writer.write("Thêm dòng mới vào tệp.\n");
    writer.close(); // Quan trọng: Phải đóng tài nguyên
    System.out.println("Ghi tệp thành công.");
} catch (IOException e) {
    System.out.println("Xảy ra lỗi khi ghi tệp.");
}
```

#### III. Kết Luận

Xử lý ngoại lệ là bắt buộc để tạo ra các chương trình ổn định. Làm việc với tệp mở ra cánh cửa để chương trình tương tác với dữ liệu bên ngoài.
