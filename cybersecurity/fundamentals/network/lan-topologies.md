[<-- Back to Network Menu](../network/00-MENU.md)

# 📌 LAN Topologies

> Topology là cách bố trí và kết nối các thiết bị trong một mạng LAN.

---

## 🎯 Mục tiêu

- Hiểu khái niệm Network Topology.
- Biết đặc điểm của Star, Bus và Ring Topology.
- So sánh ưu điểm và nhược điểm của từng mô hình.

---

## 📖 Khái niệm

Network Topology là cách thiết kế hoặc bố trí các thiết bị trong mạng máy tính.

Mỗi topology có cách kết nối thiết bị khác nhau, dẫn đến sự khác biệt về:

- Hiệu năng
- Chi phí
- Khả năng mở rộng
- Khả năng chịu lỗi
- Độ khó khi bảo trì

Ba topology phổ biến được giới thiệu gồm:

- Star Topology
- Bus Topology
- Ring Topology

---

## ⚙️ Cách hoạt động

### ⭐ Star Topology

Các thiết bị kết nối riêng lẻ đến một thiết bị trung tâm (Switch hoặc Hub).

```text
      PC
       |
PC --- Switch --- PC
       |
      PC
```

Luồng truyền:

```text
PC A
   │
Switch/Hub
   │
PC B
```

**Ưu điểm**

- Độ tin cậy cao.
- Dễ mở rộng.
- Dễ thêm thiết bị mới.

**Nhược điểm**

- Chi phí cao do cần nhiều dây cáp và thiết bị mạng.
- Cần bảo trì thiết bị trung tâm.
- Nếu Switch/Hub hỏng, các thiết bị sẽ không thể giao tiếp.

---

### 🚌 Bus Topology

Tất cả thiết bị cùng kết nối vào một đường truyền chính (Backbone Cable).

```text
PC    PC    PC
 |     |     |
==================
```

Luồng truyền:

```text
PC A
   │
Backbone Cable
   │
PC B
```

**Ưu điểm**

- Chi phí thấp.
- Dễ triển khai.
- Ít cần thiết bị mạng.

**Nhược điểm**

- Dễ xảy ra nghẽn mạng khi nhiều thiết bị truyền dữ liệu.
- Khó xác định vị trí lỗi.
- Nếu Backbone Cable bị đứt, toàn bộ mạng sẽ ngừng hoạt động.

---

### 🔄 Ring Topology

Các thiết bị kết nối thành một vòng khép kín.

```text
PC ── PC
│      │
PC ── PC
```

Luồng truyền:

```text
PC A
 ↓
PC B
 ↓
PC C
 ↓
PC D
 ↓
PC A
```

Dữ liệu được truyền lần lượt qua từng thiết bị cho đến khi tới đích.

**Ưu điểm**

- Ít xảy ra nghẽn mạng.
- Ít phụ thuộc vào thiết bị trung tâm.
- Dễ xác định hướng truyền dữ liệu.

**Nhược điểm**

- Dữ liệu có thể phải đi qua nhiều thiết bị.
- Nếu một thiết bị hoặc đường truyền bị lỗi, toàn bộ vòng có thể bị gián đoạn.

---

## 💡 Ví dụ

| Topology | Ví dụ |
|-----------|--------|
| Star | Văn phòng sử dụng Switch kết nối tất cả máy tính |
| Bus | Mạng cũ dùng chung một cáp Backbone |
| Ring | Mạng các thiết bị kết nối thành vòng để truyền dữ liệu |

---

## 📝 Ghi nhớ

- **Star**: Thiết bị kết nối qua Switch/Hub, dễ mở rộng nhưng phụ thuộc thiết bị trung tâm.
- **Bus**: Mọi thiết bị dùng chung Backbone Cable, rẻ nhưng có một điểm lỗi duy nhất.
- **Ring**: Thiết bị kết nối thành vòng, dữ liệu truyền tuần tự, ít nghẽn nhưng dễ bị ảnh hưởng nếu vòng bị đứt.

---

## 🔗 Liên quan

- LAN
- Switch
- Hub
- Network Design
- Ethernet

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/whatisnetworking)

[<-- Back to Network Menu](../network/00-MENU.md)