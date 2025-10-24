---
title: "GIỚI THIỆU VỀ JAVA"
date: 2025-10-23
draft: false
description: "Khám phá Java, cơ chế WORA, Bytecode, JVM và cách viết chương trình đầu tiên."
tags: ["java", "jvm", "wora", "lập trình", "main"]
---

### I. Java Là Gì? Định Nghĩa Cốt Lõi

**Java** là ngôn ngữ lập trình **hướng đối tượng (OOP)**, được phát triển bởi **James Gosling** tại Sun Microsystems. Java nổi tiếng với sự ổn định, mạnh mẽ và khả năng **độc lập nền tảng** tuyệt đối thông qua triết lý: **WORA (Write Once, Run Anywhere)**.

---

### II. Cơ Chế WORA: Bộ Ba Thần Thánh

Bí quyết để Java chạy được trên mọi nền tảng (Windows, macOS, Linux,...) mà không cần biên dịch lại mã nguồn là cơ chế thực thi đặc biệt của nó:

#### 1. JDK (Java Development Kit)

Bộ công cụ dành cho lập trình viên để **viết và biên dịch** code. Nó chứa trình biên dịch (`javac`) và môi trường chạy (JRE).

#### 2. Bytecode (Mã Trung Gian)

Khi bạn biên dịch file Java (`.java`), nó tạo ra mã trung gian gọi là **Bytecode** (file `.class`). Bytecode này độc lập với hệ điều hành.

#### 3. JVM (Java Virtual Machine)

**JVM** là chương trình giả lập máy tính. Chính JVM sẽ **đọc và thực thi Bytecode** trên bất kỳ hệ điều hành nào nó được cài đặt.

> **Quy trình tóm tắt:** Code Java → **_JDK/javac_** → Bytecode → **_JVM_** → Chạy trên mọi nền tảng!

### III. Đặc Điểm Quan Trọng

- **Hướng Đối Tượng (OOP):** Tổ chức code theo các đối tượng, giúp code dễ bảo trì và mở rộng.
- **Garbage Collection:** Java tự động quản lý bộ nhớ, giải phóng vùng nhớ không còn sử dụng, giúp ngăn chặn lỗi rò rỉ bộ nhớ.
- **Đa Luồng (Multithreading):** Hỗ trợ chạy nhiều tác vụ song song, tối ưu hóa hiệu năng.

---

### IV. Chương Trình Đầu Tiên: Cấu Trúc Cốt Lõi

Mọi chương trình Java độc lập đều bắt đầu tại một phương thức đặc biệt, nơi JVM tìm đến để bắt đầu thực thi: **phương thức `main`**.

#### 1. Cài Đặt và Kiểm tra

Đảm bảo bạn đã cài đặt JDK và kiểm tra phiên bản:

```bash
java -version
```

#### 2. Code "Hello World!"

Tạo một file có tên XinChao.java:

Java

// Tên file phải trùng với tên Class: XinChao.java
public class XinChao {

    // Phương thức main: Điểm khởi đầu của chương trình
    public static void main(String[] args) {

        // System.out.println là lệnh để in ra console
        System.out.println("Xin Chào, Thế Giới Java!");

        // Ví dụ một lệnh đơn giản:
        int namHienTai = 2024;
        System.out.println("Năm hiện tại: " + namHienTai);
    }

}

#### 3. Chạy Chương Trình (Trong Terminal/CMD)

Biên dịch:

Bash

```java
javac XinChao.java
```

Thực thi:

Bash

```java
java XinChao
```

#### V. Kết Luận

Bạn đã nắm được sức mạnh cốt lõi của Java: sự kết hợp giữa Bytecode và JVM tạo nên tính độc lập nền tảng, cùng với kiến trúc OOP vững chắc.
