---
title: "LẬP TRÌNH ĐA LUỒNG (MULTITHREADING)"
date: 2025-10-23
draft: false
description: "Tìm hiểu về Luồng (Thread), cách tạo luồng bằng Runnable và Thread Class, và khái niệm đồng bộ hóa (Synchronization)."
tags: ["java", "multithreading", "thread", "concurrent", "đồng bộ hóa"]
---

### I. Giới Thiệu Đa Luồng (Multithreading)

Trong thực tế, nhiều chương trình cần xử lý đồng thời nhiều tác vụ (ví dụ: vừa tải ảnh, vừa phát nhạc, vừa phản hồi thao tác người dùng). **Đa luồng** là khả năng cho phép chương trình thực thi nhiều phần của code (gọi là **luồng - Thread**) một cách đồng thời (concurrently).

- **Process (Tiến trình):** Một ứng dụng hoặc chương trình đang chạy. Mỗi tiến trình có không gian bộ nhớ riêng.
- **Thread (Luồng):** Một đơn vị thực thi nhỏ nhất trong một Process. Các luồng trong cùng một Process chia sẻ cùng không gian bộ nhớ.

### II. Các Cách Tạo Luồng (Threads)

Có hai cách chính để tạo và chạy một luồng trong Java:

#### 1. Triển khai Giao diện `Runnable`

Đây là cách được khuyến khích vì nó cho phép lớp của bạn kế thừa các lớp khác nếu cần (Java không đa kế thừa).

1.  Định nghĩa một lớp triển khai giao diện `Runnable`.
2.  Triển khai phương thức `run()`.
3.  Tạo đối tượng `Thread` và truyền đối tượng `Runnable` vào.
4.  Gọi phương thức `start()` của đối tượng `Thread`.

```java
public class TaskA implements Runnable {
    @Override
    public void run() {
        System.out.println("Luồng Task A đang chạy...");
    }
}

public static void main(String[] args) {
    TaskA task = new TaskA();
    Thread luongMoi = new Thread(task);
    luongMoi.start(); // Gọi start() để JVM tạo luồng và gọi run()
}
```

#### 2. Kế thừa Lớp Thread

1. Định nghĩa một lớp kế thừa lớp Thread.

2. Ghi đè phương thức run().

3 .Tạo đối tượng của lớp đó và gọi start().

```java
public class TaskB extends Thread {
    @Override
    public void run() {
        System.out.println("Luồng Task B đang chạy...");
    }
}

public static void main(String[] args) {
    TaskB luongB = new TaskB();
    luongB.start();
}
```

### III. Các Phương Thức Điều Khiển Luồng

| Phương thức     | Công dụng                                             |
| :-------------- | :---------------------------------------------------- |
| **`start()`**   | Bắt đầu thực thi luồng bằng cách gọi `run()`.         |
| **`run()`**     | Chứa logic chính của luồng.                           |
| **`sleep(ms)`** | Tạm dừng luồng trong một khoảng thời gian (miligiây). |
| **`join()`**    | Chờ luồng khác kết thúc công việc của nó.             |
| **`isAlive()`** | Kiểm tra xem luồng còn đang hoạt động hay không.      |

```java
public static void main(String[] args) {
    Thread luong = new TaskB();
    luong.start();

    try {
        // Main thread sẽ chờ luong kết thúc
        luong.join();
        System.out.println("Luồng Task B đã hoàn thành.");
    } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
    }
}
```

### IV. Đồng Bộ Hóa (Synchronization)

Khi nhiều luồng cùng truy cập và thay đổi cùng một tài nguyên (ví dụ: một biến chung), có thể dẫn đến **điều kiện chạy đua (Race Condition)** và dữ liệu không nhất quán. **Đồng bộ hóa** giải quyết vấn đề này.

Từ khóa **synchronized**: Khi áp dụng cho một phương thức hoặc khối lệnh, nó đảm bảo rằng tại một thời điểm, chỉ có duy nhất một luồng được phép truy cập khối code đó.

```java
public class Counter {
    private int count = 0;

    // Phương thức được đồng bộ hóa
    public synchronized void tangGiaTri() {
        count++; // Đảm bảo việc tăng giá trị diễn ra nguyên tử (atomic)
    }

    // ...
}
```

### V. Kết Luận

Lập trình đa luồng là một chủ đề phức tạp nhưng cần thiết để xây dựng các ứng dụng hiện đại, phản hồi nhanh. Nắm vững việc tạo luồng và đồng bộ hóa là chìa khóa.
