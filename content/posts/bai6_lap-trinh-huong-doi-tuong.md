---
title: "LẬP TRÌNH HƯỚNG ĐỐI TƯỢNG - OOP"
date: 2025-10-23
draft: false
description: "Tìm hiểu các khái niệm cơ bản về OOP (Class, Object), bốn trụ cột của OOP (Kế thừa, Đa hình, Trừu tượng, Đóng gói), và tại sao OOP lại quan trọng trong Java."
tags:
  ["java", "oop", "hướng đối tượng", "class", "object", "kế thừa", "đa hình"]
---

### I. OOP Là Gì? Tư Duy Lập Trình Mới

**Lập trình Hướng Đối Tượng (Object-Oriented Programming - OOP)** là một mô hình lập trình dựa trên khái niệm **Đối tượng (Object)**, trong đó dữ liệu (thuộc tính) và code (phương thức) được đóng gói lại với nhau.

OOP là nền tảng quan trọng nhất của Java, giúp chúng ta mô hình hóa các thực thể trong thế giới thực vào code, làm cho chương trình trở nên dễ quản lý, linh hoạt và tái sử dụng hơn.

#### 1. Class và Object (Ôn lại)

- **Lớp (Class):** Một bản thiết kế (Blueprint) định nghĩa cấu trúc của các đối tượng.
- **Đối Tượng (Object):** Một thể hiện thực tế của Lớp, chứa dữ liệu (trạng thái) và hành vi (phương thức).

```java
// Lớp (Class)
public class DongVat {
    String ten; // Thuộc tính

    // Phương thức
    public void keu() {
        System.out.println("Động vật đang kêu.");
    }
}

// Tạo Đối tượng (Object) trong phương thức main
public static void main(String[] args) {
    // meoA là một Đối tượng của lớp DongVat
    DongVat meoA = new DongVat();
    meoA.ten = "Kitty";
    meoA.keu(); // Kết quả: Động vật đang kêu.
}
```

### II. Bốn Trụ Cột Cơ Bản của OOP

Bốn nguyên tắc chính làm nên sức mạnh của OOP:

#### 1. Đóng Gói (Encapsulation)

- **Khái niệm**: Là cơ chế buộc dữ liệu (thuộc tính) và code (phương thức) lại với nhau thành một đơn vị duy nhất (Class).

- **Mục đích**: Ẩn chi tiết triển khai (implementation details) khỏi người dùng. Dữ liệu thường được khai báo là private và chỉ được truy cập thông qua các phương thức public (Getter/Setter).

```java
public class TaiKhoan {
    private double soDu; // Thuộc tính private (Đóng gói)

    // Getter (Truy cập dữ liệu)
    public double getSoDu() {
        return soDu;
    }

    // Setter (Thay đổi dữ liệu có kiểm soát)
    public void setSoDu(double soTien) {
        if (soTien > 0) {
            this.soDu = soTien;
        }
    }
}
```

#### 2. Kế Thừa (Inheritance)

- **Khái niệm**: Cho phép một lớp (lớp con, Subclass) kế thừa các thuộc tính và phương thức từ một lớp khác (lớp cha, Superclass).

- **Mục đích**: Tái sử dụng code và tạo mối quan hệ "là một" (Is-a relationship). Dùng từ khóa extends.

```java
// Lớp cha
public class HinhHoc {
    public void ve() {
        System.out.println("Vẽ hình học.");
    }
}

// Lớp con kế thừa từ HinhHoc
public class HinhTron extends HinhHoc {
    // HinhTron tự động có phương thức ve() của lớp cha
}
```

#### 3. Đa Hình (Polymorphism)

- **Khái niệm**: Nghĩa là "đa dạng hình thái". Cho phép một hành vi (phương thức) có thể được thực hiện theo nhiều cách khác nhau.

Ví dụ phổ biến:

**Overloading (Nạp chồng phương thức)**:Nhiều phương thức cùng tên nhưng khác tham số.

**Overriding (Ghi đè phương thức)**: Lớp con định nghĩa lại phương thức của lớp cha.

#### 4. Trừu Tượng (Abstraction)

- **Khái niệm**: Chỉ hiển thị những thông tin cần thiết và ẩn đi những chi tiết phức tạp, không liên quan.

- **Thực hiện**: Thông qua Abstract Classes (Lớp Trừu Tượng) và Interfaces (Giao diện).

### III. Tóm Tắt Vai Trò

| Trụ cột        | Mục đích chính                                      | Cơ chế trong Java                            |
| :------------- | :-------------------------------------------------- | :------------------------------------------- |
| **Đóng Gói**   | Bảo vệ và kiểm soát dữ liệu.                        | `private` variables, `public` Getter/Setter. |
| **Kế Thừa**    | Tái sử dụng code, tạo cấu trúc phân cấp.            | Từ khóa `extends`.                           |
| **Đa Hình**    | Linh hoạt, cho phép một giao diện nhiều triển khai. | Overloading, Overriding.                     |
| **Trừu Tượng** | Đơn giản hóa sự phức tạp, tập trung vào chức năng.  | `abstract class`, `interface`.               |

### IV. Kết Luận

OOP là trọng tâm của Java. Nắm vững bốn trụ cột này là chìa khóa để viết code chuyên nghiệp, dễ bảo trì.
