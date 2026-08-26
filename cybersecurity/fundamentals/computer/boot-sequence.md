[<-- Back to Computer Menu](../computer/00-MENU.md)

# 📌 Boot Sequence – Quá trình khởi động máy tính

> Boot Sequence là chuỗi các bước mà máy tính thực hiện từ khi được cấp nguồn cho đến khi hệ điều hành được nạp và sẵn sàng hoạt động.

---

## 🎯 Mục tiêu

- Hiểu được **Boot Sequence** và các bước cơ bản trong quá trình khởi động máy tính.
- Phân biệt vai trò của **PSU, UEFI/BIOS, POST, Boot Device và Bootloader**.
- Hiểu cách **Operating System (OS)** được nạp vào **RAM**.
- Biết kiến thức nền tảng để phân tích các vấn đề liên quan đến **khởi động hệ thống**.

---

## 📖 Khái niệm

**Boot Sequence** là quá trình máy tính thực hiện sau khi được bật nguồn, nhằm kiểm tra phần cứng, xác định thiết bị khởi động và nạp hệ điều hành vào bộ nhớ.

Có thể hình dung quá trình này giống như việc con người thức dậy:

- Cơ thể được cung cấp năng lượng.
* Các cơ quan bắt đầu hoạt động.
* Kiểm tra xem cơ thể có hoạt động bình thường không.
* Xác định trạng thái cần thiết để bắt đầu ngày mới.
* Cuối cùng, "ý thức" được khởi động.

Trong máy tính, quá trình này diễn ra theo chuỗi:

**Power → Firmware → POST → Boot Device → Bootloader → Operating System**

---

## ⚙️ Cách hoạt động

### 1. Press the Power Button

Khi nhấn nút nguồn, máy tính gửi tín hiệu đến **PSU (Power Supply Unit)** để cho phép nguồn điện được cung cấp đến các linh kiện.

Các thành phần phần cứng bắt đầu nhận điện và hoạt động.

```text
Power Button
     ↓
    PSU
     ↓
Các linh kiện được cấp nguồn
```

---

### 2. Firmware Starts

Sau khi hệ thống được cấp nguồn, **firmware** bắt đầu hoạt động.

Firmware chịu trách nhiệm khởi tạo và quản lý các thành phần phần cứng ở giai đoạn đầu của quá trình boot.

Firmware phổ biến hiện nay là:

* **UEFI (Unified Extensible Firmware Interface)**
* **BIOS (Basic Input/Output System)**

> BIOS là firmware kiểu cũ và đã được UEFI thay thế phần lớn trên các hệ thống hiện đại. Trong nhiều tài liệu, thuật ngữ BIOS vẫn được sử dụng để chỉ firmware khởi động hệ thống.

```text
PSU
 ↓
Firmware
 ├── UEFI
 └── BIOS
```

---

### 3. Power-On Self Test (POST)

Một trong những routine được firmware thực hiện là **POST – Power-On Self Test**.

POST kiểm tra các thành phần phần cứng quan trọng để xác định:

* Thiết bị có tồn tại hay không.
* Phần cứng có được cấu hình phù hợp không.
* Phần cứng có hoạt động bình thường không.

Nếu phát hiện lỗi nghiêm trọng, hệ thống có thể phát ra **beep code**, hiển thị thông báo lỗi hoặc dừng quá trình khởi động.

```text
UEFI / BIOS
     ↓
    POST
     ↓
Kiểm tra phần cứng
     ↓
 ┌───────────────┐
 │     OK?       │
 └───────┬───────┘
       Yes ↓
     Tiếp tục Boot
```

---

### 4. Select Boot Device

Sau khi POST hoàn tất, firmware cần xác định **thiết bị nào sẽ được sử dụng để khởi động hệ điều hành**.

UEFI có **boot order** – thứ tự ưu tiên các thiết bị khởi động.

Ví dụ:

```text
Boot Order:

1. NVMe SSD
2. USB
3. Network
```

Hệ thống sẽ kiểm tra các thiết bị theo thứ tự này để tìm thành phần khởi động hợp lệ.

---

### 5. Initiate Bootloader

Sau khi xác định được boot device, firmware khởi chạy **bootloader**.

Bootloader có nhiệm vụ tiếp tục quá trình khởi động và nạp hệ điều hành.

Một cách đơn giản có thể mô tả:

```text
Boot Device
     ↓
Bootloader
     ↓
Load Operating System
     ↓
RAM
     ↓
Operating System
     ↓
User Interface
```

Sau khi hệ điều hành được nạp, quyền điều khiển hệ thống được chuyển từ firmware sang **Operating System**.

---

## 🔄 Tổng quan Boot Sequence

```text
┌─────────────────────┐
│  1. Power Button    │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  2. UEFI / BIOS      │
│     Firmware         │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  3. POST             │
│  Hardware Check      │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  4. Select Boot      │
│     Device            │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  5. Bootloader       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  Operating System    │
│       loaded         │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  Working Interface   │
└─────────────────────┘
```

---

## 💡 Ví dụ

### Ví dụ: Khởi động một máy tính Windows

Khi người dùng nhấn nút nguồn:

1. PSU cung cấp nguồn cho hệ thống.
2. UEFI bắt đầu chạy.
3. POST kiểm tra RAM, CPU, ổ lưu trữ và các phần cứng cần thiết.
4. UEFI kiểm tra **Boot Order** và tìm ổ SSD chứa hệ điều hành.
5. UEFI khởi chạy bootloader.
6. Bootloader nạp các thành phần cần thiết của Windows vào RAM.
7. Windows tiếp quản quyền điều khiển hệ thống.
8. Người dùng nhìn thấy màn hình đăng nhập hoặc giao diện Windows.

```text
Power On
   ↓
UEFI
   ↓
POST
   ↓
SSD
   ↓
Bootloader
   ↓
Windows
   ↓
Login Screen
```

### Ví dụ xử lý sự cố

Nếu máy tính bật nguồn nhưng không thể khởi động hệ điều hành, có thể kiểm tra từng giai đoạn:

```text
Có nguồn?
   ↓
UEFI hoạt động?
   ↓
POST thành công?
   ↓
Có nhận SSD/HDD?
   ↓
Có Boot Device hợp lệ?
   ↓
Bootloader hoạt động?
   ↓
OS khởi động?
```

Việc hiểu Boot Sequence giúp xác định **hệ thống gặp lỗi ở giai đoạn nào**, thay vì chỉ xác định chung chung rằng "máy không khởi động được".

---

## 📝 Ghi nhớ

* **PSU** cung cấp nguồn điện cho các thành phần của máy tính.
* **UEFI/BIOS** là firmware được chạy ở giai đoạn đầu của quá trình boot.
* **POST** kiểm tra phần cứng trước khi tiếp tục khởi động.
* **Boot Order** xác định thứ tự ưu tiên các thiết bị khởi động.
* **Bootloader** chịu trách nhiệm bắt đầu quá trình nạp hệ điều hành.
* **OS** được nạp vào **RAM** và sau đó tiếp quản quyền điều khiển hệ thống.
* Chuỗi cần nhớ:

```text
Power
  ↓
UEFI / BIOS
  ↓
POST
  ↓
Boot Device
  ↓
Bootloader
  ↓
Operating System
```

---

## 🔗 Liên quan

* **UEFI / BIOS**
* **POST (Power-On Self Test)**
* **Bootloader**
* **Boot Order**
* **Operating System**
* **RAM**
* **Storage Device**
* **MBR / GPT**
* **Secure Boot**

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/insideacomputer)
* UEFI Forum – UEFI Specification
* Microsoft Learn – Windows startup and boot process
* Linux documentation – Boot process
* Intel – Firmware and system boot concepts

---

## 📚 Nguồn tham khảo



[<-- Back to Computer Menu](../computer/00-MENU.md)