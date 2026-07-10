[<-- Back to Network Menu](../network/00-MENU.md)

# 📌 Router

> Thiết bị mạng dùng để kết nối các mạng khác nhau và định tuyến dữ liệu giữa chúng.

---

## 🎯 Mục tiêu

- Hiểu Router là gì và vai trò của nó trong mạng máy tính.
- Biết Routing là gì.
- Hiểu cách Router lựa chọn đường đi để truyền dữ liệu giữa các mạng.

---

## 📖 Khái niệm

Router là thiết bị mạng có nhiệm vụ **kết nối nhiều mạng với nhau** và **chuyển tiếp dữ liệu giữa các mạng đó**.

Để thực hiện việc này, Router sử dụng **Routing**.

**Routing** là quá trình xác định đường đi để dữ liệu có thể di chuyển từ mạng nguồn đến mạng đích một cách thành công.

Khi giữa hai mạng tồn tại nhiều đường truyền, Router sẽ lựa chọn một đường phù hợp để chuyển tiếp dữ liệu.

---

## ⚙️ Cách hoạt động

### Kiến trúc

```text
Computer A
     │
  Router
   ╱   ╲
Router Router
   ╲   ╱
  Router
     │
Computer B
```

---

### Luồng hoạt động

```text
Computer A
      │
      ▼
Source Router
      │
      ▼
Các Router trung gian
      │
      ▼
Destination Router
      │
      ▼
Computer B
```

Quá trình:

1. Computer A gửi dữ liệu đến Router.
2. Router xác định mạng đích.
3. Router lựa chọn một đường truyền (Route).
4. Dữ liệu được chuyển qua các Router trung gian.
5. Router cuối cùng chuyển dữ liệu đến Computer B.

Khi có nhiều đường kết nối giữa các mạng, Router sẽ thực hiện **Routing** để đưa dữ liệu đến đúng đích.

---

## 💡 Ví dụ

### Ví dụ

Computer A cần gửi dữ liệu đến Computer B.

```text
Computer A
     │
  Router
   ╱   ╲
Route 1 Route 2
   ╲   ╱
  Router
     │
Computer B
```

Router sẽ xác định một đường đi giữa hai mạng để dữ liệu đến được Computer B.

---

## 📝 Ghi nhớ

- Router dùng để kết nối các mạng khác nhau.
- Router chuyển tiếp dữ liệu giữa các mạng.
- Quá trình lựa chọn đường đi của dữ liệu gọi là **Routing**.
- Routing đặc biệt hữu ích khi giữa các mạng tồn tại nhiều đường truyền.

---

## 🔗 Liên quan

- Switch
- Routing
- Network
- Internet
- IP Address

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/whatisnetworking)

[<-- Back to Network Menu](../network/00-MENU.md)