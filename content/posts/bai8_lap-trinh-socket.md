---
title: "LẬP TRÌNH SOCKET"
date: 2025-10-23
draft: false
description: "Hướng dẫn lập trình mạng cơ bản với Socket, bao gồm ServerSocket, Socket Client và giao thức TCP."
tags: ["java", "socket", "networking", "tcp", "server", "client"]

---

### I. Giới Thiệu Lập Trình Mạng và Socket

Java hỗ trợ mạnh mẽ lập trình mạng thông qua **Socket API**.

- **Socket:** Là điểm cuối (endpoint) của một kết nối giao tiếp hai chiều (two-way communication link) giữa hai chương trình chạy trên mạng.
- **TCP (Transmission Control Protocol):** Là giao thức phổ biến nhất được sử dụng bởi Java Socket, đảm bảo dữ liệu được truyền đi **đáng tin cậy** và **theo đúng thứ tự** (Connection-Oriented).

### II. Phía Máy Chủ (Server)

Máy chủ phải chờ và lắng nghe các yêu cầu kết nối từ phía máy khách.

#### 1. Lớp `ServerSocket`

Lớp này dùng để tạo một Server Socket. Nó lắng nghe các yêu cầu kết nối từ Client trên một **cổng (Port)** cụ thể.

```java
import java.net.ServerSocket;
import java.net.Socket;
import java.io.IOException;

public class ServerCoBan {
    public static void main(String[] args) {
        int port = 6666; // Cổng lắng nghe

        try (ServerSocket serverSocket = new ServerSocket(port)) {
            System.out.println("Server đang lắng nghe trên cổng " + port);

            // serverSocket.accept() là lệnh chặn, chờ Client kết nối
            Socket clientSocket = serverSocket.accept();
            System.out.println("Client đã kết nối từ: " + clientSocket.getInetAddress());

            // Sau khi kết nối, Server và Client trao đổi dữ liệu qua clientSocket
            // ... (Code xử lý Input/Output)

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

#### 2. Xử lý Dữ liệu trên Server

Để gửi và nhận dữ liệu, chúng ta sử dụng các luồng I/O (Input/Output Streams) tương tự như làm việc với tệp.

| Lớp                | Mục đích                |
| :----------------- | :---------------------- |
| **`InputStream`**  | Nhận dữ liệu từ Client. |
| **`OutputStream`** | Gửi dữ liệu đến Client. |

### III. Phía Máy Khách (Client)

Máy khách chủ động tạo kết nối tới máy chủ.

#### 1. Lớp Socket

Lớp này được dùng để tạo một Socket Client. Nó cần địa chỉ IP hoặc tên máy chủ, và số cổng của máy chủ.

```java
import java.net.Socket;
import java.io.IOException;

public class ClientCoBan {
    public static void main(String[] args) {
        String serverAddress = "localhost"; // Địa chỉ máy chủ (có thể là IP)
        int port = 6666;

        try (Socket socket = new Socket(serverAddress, port)) {
            System.out.println("Đã kết nối tới Server: " + serverAddress + ":" + port);

            // Gửi dữ liệu đến Server (OutputStream)
            socket.getOutputStream().write("Xin chào Server!".getBytes());

            // Nhận dữ liệu từ Server (InputStream)
            // ... (Code đọc dữ liệu)

        } catch (IOException e) {
            System.out.println("Không thể kết nối tới Server.");
            e.printStackTrace();
        }
    }
}
```

### IV. Quy Trình Giao Tiếp TCP Cơ Bản

Giao tiếp bằng Socket thường tuân theo các bước sau:

| Bước                    | Server                                                 | Client                                           |
| :---------------------- | :----------------------------------------------------- | :----------------------------------------------- |
| **1. Khởi tạo**         | Tạo `ServerSocket` và lắng nghe Port.                  | Tạo `Socket` với IP và Port của Server.          |
| **2. Kết nối**          | Dùng `accept()` để chấp nhận kết nối.                  | Kết nối được thiết lập.                          |
| **3. Trao đổi Dữ liệu** | Lấy `InputStream` và `OutputStream` từ `clientSocket`. | Lấy `InputStream` và `OutputStream` từ `socket`. |
| **4. Đóng kết nối**     | Đóng `clientSocket` và `serverSocket`.                 | Đóng `socket`.                                   |

### V. Kết Luận

Lập trình Socket là bước đầu tiên và cơ bản nhất để xây dựng các ứng dụng client-server.
