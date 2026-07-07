# 📌 Internet

> Một mạng lưới khổng lồ được tạo thành từ rất nhiều mạng nhỏ kết nối với nhau.

---

## 🎯 Mục tiêu
- Hiểu Internet được hình thành như thế nào.
- Phân biệt mạng riêng (Private Network) và mạng công cộng (Public Network).
- Biết Internet đóng vai trò kết nối các mạng nhỏ trên toàn thế giới.

---

## 📖 Khái niệm

Internet là một mạng rất lớn, được tạo thành từ vô số mạng nhỏ kết nối với nhau.

Có thể hình dung Internet giống như việc nhiều nhóm bạn được kết nối thông qua một người có thể giao tiếp với tất cả các nhóm. Trong ví dụ của bài học, Alice có thể nói được ngôn ngữ của cả hai nhóm nên trở thành cầu nối giúp mọi người giao tiếp với nhau, từ đó hình thành một mạng lớn hơn.

Phiên bản đầu tiên của Internet xuất hiện từ dự án **ARPANET** vào cuối những năm 1960. Đến năm **1989**, **Tim Berners-Lee** tạo ra **World Wide Web (WWW)**, giúp Internet trở thành nơi lưu trữ và chia sẻ thông tin như ngày nay.

Internet bao gồm:

- Nhiều **Private Network (Mạng riêng)**.
- Được kết nối với nhau thông qua **Public Network (Internet)**.

---

## ⚙️ Cách hoạt động

### Ví dụ minh họa

```text
Nhóm 1  ←→
             \
              \
               Alice
              /     \
             /       \
        Nhóm 2     Nhóm 3
```

Alice đóng vai trò trung gian giúp các nhóm có thể giao tiếp với nhau.

### Kiến trúc Internet

```text
Private Network #1
        │
        │
        ├────────────┐
        │            │
     The Internet (Public Network)
        │            │
        └────────────┤
                     │
             Private Network #2

                     │

             Private Network #3
```

Luồng hoạt động:

1. Mỗi tổ chức hoặc khu vực xây dựng một mạng riêng (Private Network).
2. Các mạng riêng kết nối vào Internet.
3. Internet trở thành cầu nối giúp các mạng này giao tiếp với nhau.
4. Thiết bị trên mạng sử dụng các nhãn (labels) để nhận diện lẫn nhau.

---

## 💡 Ví dụ

Ví dụ trong bài học:

- Bob và Jim không thể giao tiếp trực tiếp với Zayn và Toby.
- Alice hiểu ngôn ngữ của cả hai bên nên chuyển tiếp thông tin.
- Nhờ Alice, hai nhóm được kết nối và tạo thành một mạng lớn hơn.

Tương tự trong máy tính:

- Nhiều mạng nội bộ được kết nối thông qua Internet để các thiết bị ở các mạng khác nhau có thể trao đổi dữ liệu.

---

## 📝 Ghi nhớ

- Internet là tập hợp của rất nhiều mạng nhỏ.
- Các mạng nhỏ được gọi là **Private Network**.
- Internet đóng vai trò là **Public Network** kết nối các mạng riêng.
- ARPANET là nền tảng đầu tiên của Internet.
- World Wide Web (WWW) giúp Internet trở thành kho lưu trữ và chia sẻ thông tin.

---

## 🔗 Liên quan

- Network
- Private Network
- Public Network
- IP Address
- World Wide Web (WWW)

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/whatisnetworking)