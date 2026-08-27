[<-- Back to Computer Menu](../computer/00-MENU.md)

# 📌 Virtualisation - Ảo hóa

---

## 📖 Khái niệm

### 1. Hypervisor

**Hypervisor** là phần mềm hoặc lớp hệ thống chịu trách nhiệm **tạo, quản lý và phân bổ tài nguyên cho các máy ảo (VM)** trên một máy tính vật lý.

Hypervisor có thể:

- Chia sẻ CPU, RAM và Storage của máy vật lý cho nhiều VM.
- Tạo và quản lý nhiều máy ảo.
- Cô lập các VM với nhau.
- Quản lý vòng đời VM: **Start, Stop, Pause, Clone, Delete**.

Có hai loại Hypervisor chính:

| Loại       | Đặc điểm                               | Môi trường phù hợp              |
| ---------- | -------------------------------------- | ------------------------------- |
| **Type 1** | Chạy trực tiếp trên phần cứng vật lý   | Server, Production, Data Center |
| **Type 2** | Chạy bên trong một hệ điều hành có sẵn | Learning, Testing, Home Lab     |

---

### 2. Virtual Machine (VM)

**Virtual Machine (VM)** là một máy tính ảo được tạo và quản lý bởi Hypervisor.

Mặc dù là máy ảo, VM hoạt động tương tự một máy tính vật lý và có:

- Virtual CPU
- Virtual RAM
- Virtual Storage
- Virtual Network
- Operating System riêng

Một VM bị lỗi hoặc gặp sự cố thông thường không làm các VM khác bị ảnh hưởng nhờ cơ chế **isolation**.

---

### 3. Container

**Container** là một môi trường cô lập, nhẹ, được sử dụng để chạy một ứng dụng cùng các dependency cần thiết.

Khác với VM, container **không mang theo một hệ điều hành hoàn chỉnh**. Container sử dụng chung **kernel của hệ điều hành host**.

Container thường bao gồm:

- Application
- Libraries
- Dependencies
- Configuration cần thiết

Do sử dụng chung kernel nên container:

- Khởi động rất nhanh.
- Sử dụng ít tài nguyên hơn VM.
- Dễ triển khai và mở rộng.
- Phù hợp với Development, Testing và Scalable Deployment.

**Docker** là một nền tảng mã nguồn mở phổ biến giúp xây dựng, triển khai và chạy container.

---

## ⚙️ Cách hoạt động

### 1. Type 1 Hypervisor

Type 1 Hypervisor chạy **trực tiếp trên phần cứng vật lý**.

```text
┌─────────────────────────────┐
│       Virtual Machines      │
│  ┌────────┐   ┌────────┐    │
│  │ VM 1   │   │ VM 2   │    │
│  │ Linux  │   │Windows │    │
│  └────────┘   └────────┘    │ 
├─────────────────────────────┤
│       Physical Hardware     │
│   CPU | RAM | Storage | NIC │
└─────────────────────────────┘
```

Do không cần một Operating System trung gian, Type 1 thường có hiệu năng và hiệu quả sử dụng tài nguyên tốt.

---

### 2. Type 2 Hypervisor

Type 2 Hypervisor chạy **trên một Operating System có sẵn**.

```text
┌─────────────────────────────┐
│       Virtual Machines      │
│  ┌────────┐   ┌────────┐    │
│  │ Kali   │   │Windows │    │
│  │ Linux  │   │  VM    │    │
│  └────────┘   └────────┘    │
├─────────────────────────────┤
│      Host Operating System  │
├─────────────────────────────┤
│       Physical Hardware     │
└─────────────────────────────┘
```

---

### 3. VM hoạt động như một "căn hộ"

Có thể hình dung:

```text
Physical Computer
       │
       ▼
  Hypervisor
       │
 ┌─────┴─────┐
 ▼           ▼
 VM 1       VM 2
 │           │
OS riêng    OS riêng
 │           │
Apps        Apps
```

---

### 4. Container hoạt động như "căn phòng"

Container nhẹ hơn VM vì không cần một OS hoàn chỉnh.

```text
┌────────────────────────────────┐
│          Host OS               │
│          Kernel                │
├────────────────────────────────┤
│ Docker / Container Runtime     │
├───────────────┬────────────────┤
│  Container 1  │  Container 2   │
│  Application  │  Application   │
│  Dependencies │  Dependencies  │
└───────────────┴────────────────┘
```

VM mang theo hệ điều hành riêng, trong khi container sử dụng chung kernel của hệ điều hành host.

---

### 5. VM và Container

| Đặc điểm      | VM                        | Container                     |
| ------------- | ------------------------- | ----------------------------- |
| Mức độ ảo hóa | Hardware/System           | Application                   |
| OS            | Mỗi VM có OS riêng        | Chia sẻ host kernel           |
| Tài nguyên    | Nhiều hơn                 | Ít hơn                        |
| Khởi động     | Chậm hơn                  | Rất nhanh                     |
| Isolation     | Cao                       | Nhẹ hơn VM                    |
| Flexibility   | Cao                       | Thấp hơn VM                   |
| Phù hợp       | Lab, Server, OS khác nhau | App, Dev, Testing, Deployment |

---

## 📝 Ghi nhớ

* **Hypervisor** tạo và quản lý Virtual Machine.
* **Type 1** chạy trực tiếp trên phần cứng → phù hợp với **Server và Data Center**.
* **Type 2** chạy trên Host OS → phù hợp với **Learning, Testing và Home Lab**.
* **VM** có Operating System riêng và cung cấp mức độ isolation cao.
* **Container** nhẹ hơn VM vì **chia sẻ kernel của Host OS**.
* **Docker** là nền tảng phổ biến để xây dựng và chạy container.
* Có thể nhớ bằng mô hình:

### Câu nhớ nhanh

> **VM = Full Computer**
> **Container = Application Environment**
> **Hypervisor = Manager của các VM**

---

## 🔗 Liên quan

* **Virtualization**
* **Virtual Machine (VM)**
* **Hypervisor**
* **Type 1 Hypervisor**
* **Type 2 Hypervisor**
* **Docker**
* **Containerization**
* **Operating System Kernel**
* **Kali Linux**
* **Malware Analysis**
* **Home Lab**
* **Cloud Computing**
* **Data Center**

---

## 📚 Nguồn tham khảo

- [TryHackMe](https://tryhackme.com/room/virtualisationbasics)

[<-- Back to Computer Menu](../computer/00-MENU.md)