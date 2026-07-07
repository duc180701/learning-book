# 📌 Switch

> Thiết bị mạng dùng để kết nối nhiều thiết bị trong cùng một mạng LAN và chuyển tiếp dữ liệu đến đúng thiết bị đích.

---

## 🎯 Mục tiêu

- Hiểu Switch là gì và vai trò của nó trong mạng LAN.
- Biết cách Switch chuyển tiếp dữ liệu.
- Phân biệt Switch với Hub.
- Hiểu mối quan hệ giữa Switch và Router.

---

## 📖 Khái niệm

Switch là thiết bị mạng chuyên dụng được thiết kế để kết nối nhiều thiết bị như:

- Máy tính
- Máy in
- Các thiết bị hỗ trợ Ethernet

Mỗi thiết bị sẽ kết nối vào một **port** trên Switch.

Switch thường xuất hiện trong các mạng có nhiều thiết bị như:

- Doanh nghiệp
- Trường học
- Văn phòng

Một Switch có thể cung cấp nhiều cổng kết nối, phổ biến như:

- 4 Ports
- 8 Ports
- 16 Ports
- 24 Ports
- 32 Ports
- 64 Ports

---

## ⚙️ Cách hoạt động

### Kiến trúc

```text
                Internet
                    │
                 Router
               ┌────┴────┐
               │         │
           Switch      Switch
          ┌──┼──┐      ┌──┼──┐
         PC PC PC      PC PC PC
```

---

### Luồng hoạt động

```text
PC A
   │
   ▼
Switch
   │
   ▼
PC B
```

Khi Switch nhận được một gói tin:

1. Xác định thiết bị đích được kết nối với cổng nào.
2. Chỉ chuyển gói tin đến đúng cổng đó.
3. Không phát gói tin đến toàn bộ các cổng như Hub.

Điều này giúp giảm lưu lượng mạng và tăng hiệu suất truyền dữ liệu.

---

## 💡 Ví dụ

### Ví dụ 1

Một văn phòng có 20 máy tính.

```text
20 PCs
   │
24-Port Switch
   │
Router
   │
Internet
```

Toàn bộ máy tính kết nối vào Switch để giao tiếp với nhau và truy cập Internet thông qua Router.

---

### Ví dụ 2

PC A gửi dữ liệu cho PC B.

```text
PC A
   │
Switch
   │
PC B
```

Switch chỉ gửi dữ liệu đến cổng của **PC B**, thay vì gửi đến tất cả các thiết bị trong mạng.

---

### Ví dụ 3

Nhiều Switch có thể kết nối với nhau thông qua Router.

```text
Internet
    │
 Router
 ┌──┴──┐
 │     │
SW1   SW2
```

Việc này giúp tăng tính sẵn sàng của mạng bằng cách tạo thêm các đường truyền dữ liệu. Nếu một đường truyền gặp sự cố, dữ liệu có thể đi theo đường khác, mặc dù thời gian truyền có thể lâu hơn.

---

## 📝 Ghi nhớ

- Switch kết nối nhiều thiết bị trong cùng một mạng LAN.
- Mỗi thiết bị kết nối vào một port trên Switch.
- Switch chỉ chuyển dữ liệu đến đúng thiết bị đích.
- Switch hoạt động hiệu quả hơn Hub vì không phát dữ liệu đến mọi cổng.
- Switch có thể kết nối với Router hoặc các Switch khác để mở rộng mạng.

---

## 🔗 Liên quan

- Router
- Hub
- Ethernet
- LAN
- MAC Address

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/whatisnetworking)