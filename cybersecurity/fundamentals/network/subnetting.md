# 📌 Subnetting

> Kỹ thuật chia một mạng lớn thành nhiều mạng nhỏ (Subnet) để quản lý, tăng hiệu quả và nâng cao bảo mật.

---

## 🎯 Mục tiêu

- Hiểu Subnetting là gì và tại sao cần sử dụng.
- Biết vai trò của Subnet Mask.
- Phân biệt Network Address, Host Address và Default Gateway.
- Hiểu những lợi ích cơ bản của Subnetting.

---

## 📖 Khái niệm

Subnetting là quá trình chia một mạng lớn thành nhiều mạng nhỏ hơn (**Subnet**).

Có thể hình dung Subnetting giống như việc chia một chiếc bánh thành nhiều phần cho các nhóm khác nhau. Trong mạng máy tính, mỗi subnet đại diện cho một nhóm thiết bị hoặc một bộ phận riêng biệt.

Ví dụ trong một doanh nghiệp:

- Accounting
- Human Resources
- Finance

Mỗi phòng ban có thể được đặt trong một subnet riêng để dễ quản lý và kiểm soát lưu lượng mạng.

Việc chia mạng được thực hiện bằng **Subnet Mask**, giúp xác định phạm vi của từng subnet.

---

## ⚙️ Cách hoạt động

### Ví dụ mô hình

```text
              Internet
                  │
               Router
                  │
               Switch
      ┌───────────┼───────────┐
      │           │           │
 Accounting      HR       Finance
 (Subnet 1)   (Subnet 2) (Subnet 3)
```

Mỗi phòng ban được tách thành một subnet riêng nhưng vẫn có thể kết nối ra Internet thông qua Router.

---

### Subnet Mask

Địa chỉ IP gồm **4 Octet**.

```text
192.168.1.1

┌────┬────┬────┬────┐
│192 │168 │ 1  │ 1  │
└────┴────┴────┴────┘
```

Subnet Mask cũng gồm **4 Byte (32 bit)** và được dùng để chia mạng thành các subnet.

---

### Thành phần của một Subnet

#### 1. Network Address

- Xác định chính subnet.
- Đại diện cho sự tồn tại của mạng.

Ví dụ:

```text
192.168.1.0
```

Nếu một thiết bị có địa chỉ:

```text
192.168.1.100
```

thì thiết bị thuộc mạng:

```text
192.168.1.0
```

---

#### 2. Host Address

- Định danh từng thiết bị trong subnet.

Ví dụ:

```text
192.168.1.100
```

---

#### 3. Default Gateway

- Địa chỉ của thiết bị có khả năng chuyển dữ liệu sang mạng khác.
- Khi thiết bị cần gửi dữ liệu ra ngoài subnet, dữ liệu sẽ được gửi đến Default Gateway.

Ví dụ:

```text
192.168.1.254
```

Thông thường Default Gateway sử dụng địa chỉ host đầu tiên hoặc cuối cùng của subnet.

---

## 💡 Ví dụ

### Mạng doanh nghiệp

```text
Internet
    │
 Router
    │
 Switch
 ┌──┼──┐
 │  │  │
HR ACC FIN
```

Mỗi phòng ban sử dụng một subnet riêng để dễ quản lý.

---

### Mạng gia đình

Một mạng gia đình thường chỉ có một subnet vì số lượng thiết bị không vượt quá khoảng 254 thiết bị.

---

### Mạng quán cà phê

Quán cà phê có thể tách thành hai subnet:

- Subnet dành cho nhân viên, máy POS và thiết bị nội bộ.
- Subnet dành cho khách sử dụng Wi-Fi công cộng.

Việc tách subnet giúp cô lập hai nhóm thiết bị nhưng cả hai vẫn có thể truy cập Internet.

---

## 📝 Ghi nhớ

- Subnetting là kỹ thuật chia mạng lớn thành nhiều subnet nhỏ.
- Việc chia subnet được thực hiện bằng Subnet Mask.
- Mỗi subnet gồm:
  - Network Address
  - Host Address
  - Default Gateway
- Subnetting mang lại các lợi ích:
  - Tăng hiệu quả.
  - Tăng bảo mật.
  - Kiểm soát mạng tốt hơn.
- Các tổ chức lớn thường sử dụng nhiều subnet để tách các phòng ban hoặc nhóm thiết bị.

---

## 🔗 Liên quan

- IP Address
- Subnet Mask
- Default Gateway
- Router
- Switch
- LAN

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/whatisnetworking)