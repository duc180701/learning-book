[<-- Back to Software Menu](../software/00-MENU.md)

# 📌 Data Encoding

> Tìm hiểu cách máy tính biểu diễn ký tự dưới dạng các bit và byte, từ tiêu chuẩn ASCII ban đầu đến Unicode và các phương thức mã hóa UTF-8, UTF-16, UTF-32.

---

## 📖 Khái niệm

### 1. Character Encoding là gì?

Máy tính chỉ xử lý dữ liệu dưới dạng các bit `0` và `1`. Để lưu trữ và hiển thị văn bản, chúng ta cần một quy tắc chung nhằm ánh xạ mỗi ký tự thành một chuỗi bit hoặc một giá trị số.

Ví dụ, nếu thống nhất biểu diễn chữ `T` bằng

```text
01010100
```

thì các hệ thống tuân theo cùng tiêu chuẩn sẽ hiểu chuỗi bit này là ký tự `T`.

Quy tắc ánh xạ giữa ký tự và dữ liệu số được gọi là **Character Encoding (mã hóa ký tự)**.

### 2. ASCII

**ASCII (American Standard Code for Information Interchange)** là một trong những tiêu chuẩn mã hóa ký tự đầu tiên dành cho tiếng Anh, ra đời năm 1963.

Đặc điểm:
- Sử dụng 7 bit.
- Biểu diễn 128 giá trị, từ `0` đến `127`.
- Bao gồm chữ cái tiếng Anh, chữ số, dấu câu và các ký tự điều khiển.
- Đóng vai trò như một bảng tra cứu giữa ký tự và mã số.

Ví dụ:

| Ký tự | Decimal | Hexadecimal | Binary |
|---|---:|---:|---|
| A | 65 | `41` | `01000001` |
| B | 66 | `42` | `01000010` |
| a | 97 | `61` | `01100001` |
| b | 98 | `62` | `01100010` |
| c | 99 | `63` | `01100011` |
| `[` | 91 | `5B` | `01011011` |
| T | 84 | `54` | `01010100` |

Một số đặc điểm quan trọng:
- Các chữ cái được sắp xếp theo thứ tự liên tiếp.
- Chữ thường `a–z`, chữ hoa `A–Z` và chữ số `0–9` đều có các mã liên tiếp.
- Mỗi ký tự có một mã ASCII riêng.
- Không phải mã ASCII nào cũng đại diện cho ký tự có thể in ra màn hình.

#### Control Characters

Các mã từ `0–31` và mã `127` là các ký tự điều khiển (Control Characters).

Chúng yêu cầu thiết bị thực hiện một hành động thay vì hiển thị một biểu tượng.

| Mã Decimal | Tên | Ý nghĩa |
|---:|---|---|
| 10 | LF (Line Feed) | Xuống dòng |
| 127 | DEL (Delete) | Ký tự điều khiển xóa |

Ví dụ, `LF` thường được biểu diễn bằng `\n` trong văn bản và ngôn ngữ lập trình.

### 3. Biểu diễn văn bản bằng Binary, Hexadecimal và Octal

Xét chuỗi văn bản:

```text
TryHackMe
```

Nếu sử dụng ASCII, mỗi ký tự được biểu diễn bằng một byte. Chuỗi nhị phân tương ứng, bao gồm thêm ký tự xuống dòng ở cuối, là:

```text
01010100 01110010 01111001 01001000 01100001
01100011 01101011 01001101 01100101 00001010
```

Khi trình soạn thảo đọc dữ liệu này theo ASCII, nội dung được hiển thị là:

```text
TryHackMe\n
```

Trong đó `\n` biểu thị ký tự xuống dòng.

Vì đọc Binary khá khó khăn và dễ nhầm lẫn, chúng ta thường sử dụng Hexadecimal để biểu diễn dữ liệu.

Cùng một chuỗi byte có thể được biểu diễn bằng nhiều hệ đếm:

| Hệ đếm | Biểu diễn |
|---|---|
| Binary | `01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101 00001010` |
| Hexadecimal | `54 72 79 48 61 63 6B 4D 65 0A` |
| Octal | `124 162 171 110 141 143 153 115 145 012` |
| Decimal | `84 114 121 72 97 99 107 77 101 10` |

**Ghi nhớ:**
- Binary: biểu diễn dữ liệu bằng `0` và `1`.
- Hexadecimal: cứ 4 bit tương ứng với 1 chữ số Hex.
- Octal: cứ 3 bit tương ứng với 1 chữ số Octal.
- Trong phân tích dữ liệu máy tính, Hexadecimal thường được sử dụng vì ngắn gọn và dễ đọc hơn Binary.

### 4. Extended ASCII và ISO/IEC 8859

ASCII ban đầu chỉ sử dụng 7 bit nên không thể biểu diễn đầy đủ các ký tự của nhiều ngôn ngữ khác.

Ví dụ:
- Tiếng Tây Ban Nha: `ñ`, `¿`.
- Tiếng Đức: `ß`, `ü`.
- Tiếng Ba Lan: `ł`, `ń`.
- Tiếng Séc: `č`, `ř`.
- Tiếng Romania: `ș`, `ț`.

Khi sử dụng thêm bit thứ 8, chúng ta có thể biểu diễn thêm 128 giá trị. Tuy nhiên, số lượng này vẫn không đủ để bao phủ tất cả ký tự của các ngôn ngữ châu Âu.

Các tiêu chuẩn thuộc họ **ISO/IEC 8859** được phát triển để hỗ trợ những nhóm ngôn ngữ khác nhau.

| Encoding | Tên | Phạm vi hỗ trợ |
|---|---|---|
| ISO-8859-1 | Latin-1 | Tây Âu: Đức, Pháp, Tây Ban Nha, Ý, Bồ Đào Nha và các ngôn ngữ Bắc Âu |
| ISO-8859-2 | Latin-2 | Trung và Đông Âu: Ba Lan, Séc, Hungary, Croatia, Romania và Slovakia |

#### Vấn đề không tương thích Encoding

Nếu một tài liệu được lưu bằng ISO-8859-1 nhưng lại được mở bằng ISO-8859-2, các ký tự ngoài ASCII có thể bị hiển thị sai.

Ví dụ:

```text
Ký tự gốc: Ø
Encoding khi lưu: ISO-8859-1
Encoding khi đọc: ISO-8859-2
Kết quả hiển thị: Ř
```

Điều này cho thấy hệ thống đọc cần sử dụng đúng encoding đã được dùng khi lưu dữ liệu. Nếu không, ký tự có thể bị thay thế hoặc hiển thị sai.

#### Giới hạn của các Encoding cũ

Vấn đề càng trở nên phức tạp khi xét đến các hệ chữ viết khác:

- Tiếng Anh có 26 chữ cái, cần biểu diễn chữ hoa và chữ thường.
- Tiếng Ả Rập cần hơn 250 ký tự để thể hiện các dạng chữ và dấu.
- Tiếng Nhật có 2.136 Kanji được xem là ký tự sử dụng hằng ngày; JIS X 0208 định nghĩa 6.879 ký tự.
- Tiếng Trung có khoảng 8.000 ký tự mà người bản ngữ có học thức nhận biết; GB 18030-2022 định nghĩa hơn 87.887 Hanzi.
- Ngoài ra còn có emoji và nhiều hệ thống chữ viết khác.

Các encoding riêng biệt theo khu vực không thể giải quyết tốt nhu cầu trao đổi văn bản đa ngôn ngữ.

### 5. Unicode

**Unicode** là tiêu chuẩn mã hóa ký tự phổ quát, được xây dựng để gán một mã định danh duy nhất cho các ký tự thuộc nhiều ngôn ngữ và hệ thống chữ viết.

Mỗi ký tự được gán một giá trị gọi là **Code Point**.

Ví dụ:

| Ký tự | Unicode Code Point | Mô tả |
|---|---|---|
| A | `U+0041` | Chữ Latin A |
| Ω | `U+03A9` | Chữ cái Hy Lạp Omega |
| あ | `U+3042` | Hiragana tiếng Nhật |
| 🔥 | `U+1F525` | Emoji ngọn lửa |

Lợi ích của Unicode:
- Hỗ trợ nhiều ngôn ngữ trong cùng một tài liệu.
- Hạn chế vấn đề không tương thích giữa các encoding theo khu vực.
- Cho phép trao đổi, xử lý và hiển thị văn bản đa ngôn ngữ.
- Cung cấp nền tảng chung cho việc biểu diễn ký tự trên các hệ thống máy tính.

Theo nội dung bài học, Unicode 17.0 định nghĩa gần 157.000 ký tự, trong đó có gần 4.000 emoji sequences.

**Lưu ý:** Unicode là tiêu chuẩn gán Code Point cho ký tự. UTF-8, UTF-16 và UTF-32 là các phương thức mã hóa những Code Point đó thành byte.

### 6. UTF-8, UTF-16 và UTF-32

Ba phương thức mã hóa Unicode thường gặp là UTF-8, UTF-16 và UTF-32.

#### 6.1. UTF-8

UTF-8 là phương thức mã hóa Unicode rất phổ biến trên Internet và Web hiện đại.

Đặc điểm:
- Sử dụng từ 1 đến 4 byte cho mỗi Code Point.
- Số byte thay đổi tùy theo giá trị của ký tự.
- Các ký tự ASCII từ `U+0000` đến `U+007F` sử dụng đúng 1 byte.
- Tương thích ngược với ASCII ban đầu.

Ví dụ:

| Ký tự | Code Point | Số byte UTF-8 |
|---|---|---:|
| A | `U+0041` | 1 |
| Ω | `U+03A9` | 2 |
| あ | `U+3042` | 3 |
| 🔥 | `U+1F525` | 4 |

UTF-8 có khả năng biểu diễn toàn bộ phạm vi Unicode mà không cần sử dụng 4 byte cố định cho mọi ký tự.

#### 6.2. UTF-16

UTF-16 sử dụng một hoặc hai đơn vị mã 16 bit để biểu diễn một Code Point.

- Ký tự thông thường sử dụng 1 đơn vị 16 bit, tương đương 2 byte.
- Một số ký tự nằm ngoài Basic Multilingual Plane (BMP), chẳng hạn nhiều emoji, cần 2 đơn vị 16 bit.
- Cặp hai đơn vị này được gọi là **Surrogate Pair**, tổng cộng 4 byte.

Ví dụ:

| Ký tự | Code Point | UTF-16 |
|---|---|---|
| A | `U+0041` | `0041` |
| 🔥 | `U+1F525` | `D83D DD25` |

Đối với emoji 🔥, `D83D` và `DD25` là hai đơn vị 16 bit tạo thành một Surrogate Pair. Mỗi đơn vị riêng lẻ không đại diện cho toàn bộ ký tự 🔥.

#### 6.3. UTF-32

UTF-32 là phương thức đơn giản nhất về độ dài vì luôn sử dụng đúng 4 byte (32 bit) cho mỗi Unicode Code Point.

Ví dụ:

| Ký tự | Code Point | UTF-32 |
|---|---|---|
| A | `U+0041` | `00000041` |
| 🔥 | `U+1F525` | `0001F525` |

Ưu điểm:
- Mỗi Code Point có độ dài cố định 4 byte.
- Việc xác định vị trí Code Point trong chuỗi đơn giản hơn.
l
Nhược điểm:
- Tốn nhiều dung lượng hơn UTF-8 đối với phần lớn văn bản thông thường.

### 7. So sánh UTF-8, UTF-16 và UTF-32

| Tiêu chí | UTF-8 | UTF-16 | UTF-32 |
|---|---|---|---|
| Độ dài | 1–4 byte | 2 hoặc 4 byte | Luôn 4 byte |
| ASCII | 1 byte | 2 byte | 4 byte |
| Ký tự A | 1 byte | 2 byte | 4 byte |
| Emoji 🔥 | 4 byte | 4 byte | 4 byte |
| Tương thích ASCII | Có | Không theo cách biểu diễn byte | Không theo cách biểu diễn byte |
| Dung lượng | Linh hoạt, thường tiết kiệm | Trung gian | Thường lớn nhất |

---

## 📝 Ghi nhớ

- **Character Encoding** là quy tắc chuyển đổi ký tự thành dữ liệu số để máy tính lưu trữ và xử lý.
- **ASCII** ra đời năm 1963, sử dụng 7 bit và biểu diễn 128 giá trị.
- Các mã ASCII từ `0–31` và mã `127` là Control Characters.
- `LF` có mã Decimal `10` và thường được biểu diễn bằng `\n`.
- Hexadecimal thường được dùng để đọc dữ liệu byte vì ngắn gọn hơn Binary.
- **Extended ASCII** sử dụng 8 bit và từng được mở rộng bằng nhiều encoding theo khu vực.
- **ISO-8859-1** và **ISO-8859-2** hỗ trợ các nhóm ngôn ngữ khác nhau.
- Đọc dữ liệu bằng encoding không khớp với encoding khi lưu có thể khiến ký tự hiển thị sai.
- **Unicode** gán Code Point duy nhất cho các ký tự trong nhiều hệ thống chữ viết.
- **UTF-8** sử dụng 1–4 byte, phổ biến trên Web và tương thích ngược với ASCII.
- **UTF-16** sử dụng 2 hoặc 4 byte; một số ký tự cần Surrogate Pair.
- **UTF-32** luôn sử dụng 4 byte cho mỗi Code Point.
- Unicode là tiêu chuẩn ký tự; UTF-8, UTF-16 và UTF-32 là các cách mã hóa Unicode thành byte.

### Bảng tổng hợp nhanh

| Thuật ngữ | Ý nghĩa |
|---|---|
| ASCII | Tiêu chuẩn mã hóa ký tự 7 bit |
| Extended ASCII | Các cách mở rộng biểu diễn ký tự bằng 8 bit |
| ISO-8859 | Họ tiêu chuẩn encoding theo nhóm ngôn ngữ |
| Unicode | Tiêu chuẩn gán Code Point cho ký tự |
| Code Point | Mã định danh của một ký tự trong Unicode |
| UTF-8 | Mã hóa Unicode bằng 1–4 byte |
| UTF-16 | Mã hóa Unicode bằng 2 hoặc 4 byte |
| UTF-32 | Mã hóa Unicode bằng 4 byte cố định |
| Surrogate Pair | Cặp hai đơn vị 16 bit trong UTF-16 |

---

## 🔗 Liên quan

- Binary, Decimal, Hexadecimal & Octal
- Color Representation & Number Systems
- Data Encoding
- File Signatures / Magic Bytes
- Packet Analysis
- Memory Dump Analysis
- Malware Analysis

---

## 📚 Nguồn tham khảo

* [TryHackMe – Data Encoding](https://tryhackme.com/room/dataencoding)

[<-- Back to Software Menu](../software/00-MENU.md)