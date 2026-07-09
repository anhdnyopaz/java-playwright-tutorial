# ☕ Giai đoạn 1 — Java Cơ Bản Cho Tester (3 Tuần)

> **Học liệu chính thức — Giai đoạn 1** của giáo trình *Automation Test với Java + Playwright*.
> **Đối tượng:** Bạn là tester manual, **chưa từng viết code** (hoặc mới bập bẹ). Không sao cả — học liệu này được viết để cầm tay chỉ việc.
> **Mục tiêu sau 3 tuần:** Đọc, viết và **debug** được code Java ở mức đủ để bắt đầu học Playwright. Đặc biệt là **hiểu Lambda** — thứ Playwright dùng ở khắp nơi.

---

## 📑 Mục Lục

- [🧭 Cách dùng học liệu này](#-cách-dùng-học-liệu-này-đọc-kỹ-trước-khi-bắt-đầu)
- [🛠️ Chuẩn bị: Tạo nơi để viết code](#️-chuẩn-bị-tạo-nơi-để-viết-code)
- **📅 TUẦN 1 — Nền tảng cú pháp**
  - 1.1 Biến & kiểu dữ liệu · 1.2 Toán tử · 1.3 `if/else` & `switch` · 1.4 Vòng lặp · 1.5 Mảng · 1.6 `List` · 1.7 `Map` · 1.8 Method
  - ⚠️ Lỗi thường gặp · Bài tập (8 bài) · ✅ Checklist · 📖 Đáp án Tuần 1
- **📅 TUẦN 2 — Lập trình hướng đối tượng (OOP)**
  - 2.1 Class & Object · 2.2 Method · 2.3 Constructor · 2.4 Encapsulation · 2.5 Inheritance · 2.6 Interface & Abstract class · 2.7 `static`
  - ⚠️ Lỗi thường gặp · Bài tập (7 bài) · ✅ Checklist · 📖 Đáp án Tuần 2
- **📅 TUẦN 3 — Java thực dụng cho automation**
  - 3.1 ⭐ **Lambda & Functional Interface (trọng tâm)** · 3.2 Generics · 3.3 Enum · 3.4 Exception · 3.5 File I/O · 3.6 Stream API · 3.7 Annotation · 3.8 🐞 Debug bằng IntelliJ
  - ⚠️ Lỗi thường gặp · Bài tập (8 bài) · ✅ Checklist · 📖 Đáp án Tuần 3
- **🎯 Bài kiểm tra tổng** (20 câu quiz + 2 bài code) — có đáp án
- **🏁 Checklist Milestone** · Đọc hiểu Stack Trace
- **📚 Tài nguyên tham khảo**

---

## 🧭 Cách dùng học liệu này (đọc kỹ trước khi bắt đầu)

Học lập trình **không giống** đọc tài liệu manual test. Bạn không thể "đọc hiểu" là xong. Quy tắc vàng:

> **Gõ lại từng dòng code bằng tay, chạy nó, cố tình làm nó lỗi, rồi sửa.** Đọc 10 ví dụ không bằng tự tay gõ 1 ví dụ và làm nó chạy.

**Chuẩn bị (đã làm ở Giai đoạn 0):**
- Đã cài **JDK 17+** và **IntelliJ IDEA Community**.
- Mở được IntelliJ và tạo được project "Hello World".

**Cách học mỗi khái niệm trong tài liệu:**
1. Đọc phần **giải thích** (có ví von đời thường cho dễ nhớ).
2. Gõ lại **ví dụ code** vào IntelliJ (đừng copy-paste — gõ tay giúp nhớ).
3. **Chạy** (nút ▶ màu xanh) và xem kết quả có khớp không.
4. Đọc phần **giải thích từng dòng**.
5. **Nghịch phá:** đổi giá trị, xóa dấu chấm phẩy, đổi kiểu dữ liệu... xem lỗi gì xảy ra. Lỗi là bạn của người học.

**Cấu trúc mỗi tuần:**
- Phần **lý thuyết + ví dụ** (dạy từng khái niệm).
- Mục **⚠️ Lỗi thường gặp của người mới** (những cái bẫy kinh điển).
- **Bài tập thực hành** (5–8 bài, tăng dần độ khó) — hãy **tự làm trước**.
- **✅ Checklist tự kiểm tra**.
- **📖 Đáp án** (đặt cuối mỗi tuần — đừng nhìn trước khi tự làm!).

Cuối Giai đoạn 1 có **bài kiểm tra tổng** (quiz + 2 bài code) và **checklist milestone**.

---

## 🛠️ Chuẩn bị: Tạo nơi để viết code

Trước khi vào Tuần 1, tạo một project để chứa code luyện tập:

1. Mở IntelliJ → **New Project** → chọn **Java**, JDK 17+ → đặt tên `java-luyen-tap` → **Create**.
2. Trong thư mục `src`, chuột phải → **New → Java Class** → đặt tên `Main`.
3. Gõ chương trình đầu tiên:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Xin chào, tôi là tester đang học Java!");
    }
}
```

4. Nhấn nút ▶ màu xanh bên trái dòng `public static void main` → chọn **Run 'Main.main()'**.
5. Nhìn xuống khung **Run** ở dưới — bạn sẽ thấy dòng chữ vừa in ra. 🎉

**Giải thích khung xương một chương trình Java:**

| Thành phần | Ý nghĩa (ví von) |
|-----------|------------------|
| `public class Main { ... }` | Mọi code Java phải nằm trong một **class**. Coi class như "cái hộp" chứa code. Tên class = tên file (`Main.java`). |
| `public static void main(String[] args)` | **Điểm bắt đầu** chương trình. Java luôn chạy từ đây. Cứ coi như "cửa vào nhà". Tạm chấp nhận cú pháp này, tuần 2–3 sẽ hiểu dần. |
| `System.out.println("...")` | **In một dòng ra màn hình** (console). `println` = "print line". Đây sẽ là công cụ số 1 để bạn xem code đang chạy tới đâu. |
| `;` (dấu chấm phẩy) | Kết thúc **một câu lệnh**. Quên nó là lỗi kinh điển của người mới. |
| `{ }` (ngoặc nhọn) | Bao một **khối code**. Mở `{` thì phải có đóng `}`. |

> 💡 **Mẹo:** Trong tài liệu này, mỗi khối `java` là một chương trình hoặc đoạn code hoàn chỉnh. Nếu chỉ thấy vài dòng lẻ, bạn có thể bọc chúng trong `public static void main` để chạy thử.

---

# 📅 TUẦN 1 — Nền Tảng Cú Pháp

**Mục tiêu tuần này:** Sau tuần 1 bạn sẽ đọc hiểu và tự viết được: khai báo biến, tính toán, câu điều kiện, vòng lặp, danh sách (`List`), từ điển (`Map`), và tự viết được **hàm (method)**. Đây là "bảng chữ cái" của lập trình.

---

## 1.1. Biến và Kiểu Dữ Liệu

### Biến là gì?

**Biến (variable)** là một "cái hộp có dán nhãn" để lưu dữ liệu. Bạn đặt tên cho hộp, bỏ giá trị vào, rồi lấy ra dùng sau.

Ví von: khi test, bạn hay ghi chú "username = admin", "password = 123456", "số lần thử = 3". Mỗi thứ đó chính là một **biến**.

Trong Java, khi tạo biến bạn phải nói rõ **kiểu dữ liệu** (hộp này chứa loại gì: số nguyên, chữ, đúng/sai...). Java là ngôn ngữ **strongly typed** (kiểu chặt) — khai báo sai kiểu là báo lỗi ngay.

### 4 kiểu dữ liệu cơ bản nhất

```java
public class BienCoBan {
    public static void main(String[] args) {
        int soLanThuLogin = 3;              // số nguyên
        double giaSanPham = 29.99;          // số thực (có phần thập phân)
        boolean dangNhapThanhCong = true;   // đúng/sai (true/false)
        String tenNguoiDung = "admin";      // chuỗi ký tự (chữ)

        System.out.println("Tên đăng nhập: " + tenNguoiDung);
        System.out.println("Số lần thử: " + soLanThuLogin);
        System.out.println("Giá: " + giaSanPham);
        System.out.println("Đăng nhập thành công? " + dangNhapThanhCong);
    }
}
```

**Giải thích từng dòng:**
- `int soLanThuLogin = 3;` → khai báo biến tên `soLanThuLogin`, kiểu `int` (số nguyên), gán giá trị `3`. Cú pháp chung: `KiểuDữLiệu tênBiến = giáTrị;`
- `double giaSanPham = 29.99;` → kiểu `double` cho **số thực** (có thập phân). Dùng cho giá tiền, tỉ lệ, thời gian giây...
- `boolean dangNhapThanhCong = true;` → kiểu `boolean` chỉ nhận **2 giá trị**: `true` hoặc `false`. Cực kỳ quan trọng trong test (element có hiển thị không? login có pass không?).
- `String tenNguoiDung = "admin";` → kiểu `String` cho **chuỗi ký tự**. Chuỗi luôn nằm trong dấu **nháy kép** `"..."`. Lưu ý `String` viết **hoa chữ S**.
- `+` trong `println` là **nối chuỗi** (ghép chữ lại với nhau).

### Bảng các kiểu dữ liệu hay dùng

| Kiểu | Dùng cho | Ví dụ giá trị | Ghi chú |
|------|----------|---------------|---------|
| `int` | Số nguyên | `0`, `42`, `-7` | Phổ biến nhất cho đếm, index |
| `double` | Số thực | `29.99`, `3.14`, `0.5` | Giá tiền, tỉ lệ |
| `boolean` | Đúng/sai | `true`, `false` | Kết quả kiểm tra (assert) |
| `String` | Chuỗi ký tự | `"admin"`, `"Xin chào"` | Chữ S hoa, dùng nháy kép |
| `char` | Một ký tự | `'A'`, `'x'` | Dùng nháy **đơn** `'...'` |
| `long` | Số nguyên **rất lớn** | `10000000000L` | Timestamp, id lớn (có `L` ở cuối) |

> 📝 **Quy tắc đặt tên biến (camelCase):** bắt đầu bằng chữ thường, từ thứ hai trở đi viết hoa chữ cái đầu: `tenNguoiDung`, `soLanThu`, `giaSanPham`. Tên phải **có nghĩa** — đừng đặt `a`, `x`, `temp1`.

### Nháy kép vs nháy đơn (bẫy hay gặp)

```java
String chu = "A";   // ĐÚNG — String dùng nháy kép, dù chỉ 1 ký tự
char kyTu = 'A';    // ĐÚNG — char dùng nháy đơn
// char sai = "A";  // ❌ SAI — nháy kép không gán được cho char
// String sai = 'A';// ❌ SAI — nháy đơn không gán được cho String
```

### `var` — để Java tự đoán kiểu (Java 10+)

```java
var ten = "admin";     // Java tự hiểu đây là String
var tuoi = 25;         // Java tự hiểu đây là int
System.out.println(ten + " - " + tuoi);
```

`var` giúp viết ngắn gọn, nhưng người mới nên **viết rõ kiểu** một thời gian để quen. Sau này đọc code framework bạn sẽ gặp `var` nhiều.

---

## 1.2. Toán Tử (Operators)

Toán tử là các "phép" bạn làm với biến. Java có 4 nhóm chính.

### Toán tử số học (tính toán)

```java
public class ToanTuSoHoc {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;

        System.out.println("Cộng: " + (a + b));   // 13
        System.out.println("Trừ: " + (a - b));    // 7
        System.out.println("Nhân: " + (a * b));   // 30
        System.out.println("Chia: " + (a / b));   // 3  ⚠️ chia nguyên!
        System.out.println("Dư (chia lấy dư): " + (a % b)); // 1
    }
}
```

**Giải thích quan trọng:**
- `a / b` với hai số `int` cho kết quả `3`, **không phải 3.333**. Vì hai số nguyên chia nhau → Java cắt bỏ phần thập phân. Đây là **bẫy kinh điển** (xem mục Lỗi thường gặp).
- `a % b` (**modulo**) = phần **dư** của phép chia. `10 % 3 = 1`. Rất hay dùng để kiểm tra chẵn/lẻ: `n % 2 == 0` nghĩa là `n` chẵn.

Để chia ra số thực, cần ít nhất một số là `double`:

```java
double ketQua = 10.0 / 3;   // 3.3333...
System.out.println(ketQua);
```

### Toán tử tăng/giảm

```java
int demSoTest = 5;
demSoTest++;   // tăng 1 → thành 6 (viết tắt của demSoTest = demSoTest + 1)
demSoTest--;   // giảm 1 → về 5
demSoTest += 10; // cộng dồn 10 → 15
demSoTest -= 3;  // trừ đi 3 → 12
System.out.println(demSoTest); // 12
```

### Toán tử so sánh (trả về boolean)

```java
int tuoi = 20;
System.out.println(tuoi == 20);  // true  (bằng nhau)
System.out.println(tuoi != 18);  // true  (khác nhau)
System.out.println(tuoi > 18);   // true  (lớn hơn)
System.out.println(tuoi < 18);   // false (nhỏ hơn)
System.out.println(tuoi >= 20);  // true  (lớn hơn hoặc bằng)
System.out.println(tuoi <= 19);  // false (nhỏ hơn hoặc bằng)
```

> ⚠️ **Cực kỳ quan trọng:** `==` là **so sánh**, còn `=` là **gán**. Nhầm hai cái này là lỗi số 1 của người mới. `tuoi = 20` là "đặt tuổi bằng 20", còn `tuoi == 20` là "hỏi tuổi có bằng 20 không?".

### Toán tử logic (kết hợp điều kiện)

```java
boolean coUsername = true;
boolean coPassword = false;

System.out.println(coUsername && coPassword); // false — AND: cả hai phải đúng
System.out.println(coUsername || coPassword); // true  — OR: chỉ cần một cái đúng
System.out.println(!coPassword);              // true  — NOT: đảo ngược
```

| Toán tử | Tên | Đúng khi |
|---------|-----|----------|
| `&&` | AND (và) | **Cả hai** vế đều `true` |
| `\|\|` | OR (hoặc) | **Ít nhất một** vế `true` |
| `!` | NOT (phủ định) | Đảo `true`↔`false` |

Ví dụ testing: `if (usernameHopLe && passwordHopLe)` → chỉ login khi **cả** username **và** password hợp lệ.

---

## 1.3. Câu Điều Kiện: `if / else` và `switch`

Điều kiện = "nếu... thì... không thì...". Đây là cách chương trình **ra quyết định**.

### `if / else if / else`

```java
public class KiemTraDiem {
    public static void main(String[] args) {
        int diem = 75;

        if (diem >= 90) {
            System.out.println("Xuất sắc");
        } else if (diem >= 70) {
            System.out.println("Khá");        // ← in ra dòng này
        } else if (diem >= 50) {
            System.out.println("Trung bình");
        } else {
            System.out.println("Chưa đạt");
        }
    }
}
```

**Giải thích:**
- Java kiểm tra **lần lượt từ trên xuống**. Gặp điều kiện `true` đầu tiên thì chạy khối đó rồi **thoát** (không kiểm tra tiếp).
- `diem = 75`: `75 >= 90`? Không → `75 >= 70`? Có → in "Khá" → dừng.
- `else` (không có điều kiện) là "trường hợp còn lại", chạy khi mọi `if` phía trên đều sai.
- Điều kiện trong `( )` phải cho ra **boolean** (`true`/`false`).

### Ví dụ testing thực tế: quyết định kết quả test

```java
int httpStatus = 200;

if (httpStatus == 200) {
    System.out.println("PASS — request thành công");
} else if (httpStatus == 404) {
    System.out.println("FAIL — không tìm thấy trang");
} else if (httpStatus >= 500) {
    System.out.println("FAIL — lỗi server");
} else {
    System.out.println("Cần kiểm tra: status = " + httpStatus);
}
```

### Toán tử ba ngôi (ternary) — viết `if/else` gọn

```java
int soLoi = 0;
String ketQua = (soLoi == 0) ? "PASS" : "FAIL";
System.out.println(ketQua); // PASS
```

Đọc là: "nếu `soLoi == 0` thì `ketQua` = `PASS`, ngược lại = `FAIL`". Cú pháp: `điều_kiện ? giá_trị_nếu_đúng : giá_trị_nếu_sai`.

### `switch` — chọn theo nhiều trường hợp cụ thể

Khi cần so sánh **một biến** với **nhiều giá trị cố định**, `switch` gọn hơn `if` dài:

```java
public class ChonBrowser {
    public static void main(String[] args) {
        String browser = "firefox";

        switch (browser) {
            case "chrome":
                System.out.println("Khởi động Chromium");
                break;
            case "firefox":
                System.out.println("Khởi động Firefox");  // ← chạy dòng này
                break;
            case "webkit":
                System.out.println("Khởi động WebKit (Safari)");
                break;
            default:
                System.out.println("Browser không hỗ trợ: " + browser);
        }
    }
}
```

**Giải thích:**
- `switch (browser)` → lấy giá trị của `browser` rồi tìm `case` khớp.
- `break;` → **bắt buộc** ở cuối mỗi case, nếu quên thì code sẽ "rơi" xuống case kế tiếp (bug khó hiểu).
- `default:` → trường hợp không khớp case nào (giống `else`).

### `switch` kiểu mũi tên (Java 14+, gọn và an toàn hơn)

```java
String browser = "firefox";
String ketQua = switch (browser) {
    case "chrome" -> "Khởi động Chromium";
    case "firefox" -> "Khởi động Firefox";
    case "webkit" -> "Khởi động WebKit";
    default -> "Không hỗ trợ";
};
System.out.println(ketQua); // Khởi động Firefox
```

Kiểu `->` **không cần `break`** (không bị "rơi" xuống dưới) và có thể trả về giá trị trực tiếp. Bạn sẽ gặp cả hai kiểu trong thực tế.

---

## 1.4. Vòng Lặp: `for`, `while`, `for-each`

Vòng lặp = "làm đi làm lại một việc". Ví dụ trong test: kiểm tra **từng** sản phẩm trong giỏ, thử login **nhiều** lần, duyệt **từng** dòng của bảng.

### Vòng lặp `for`

Dùng khi biết **số lần lặp**:

```java
public class VongLapFor {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println("Lần thử login thứ " + i);
        }
    }
}
```

**Giải thích cấu trúc `for (khởi_tạo; điều_kiện; cập_nhật)`:**
1. `int i = 1` → **khởi tạo** biến đếm `i` (chạy 1 lần lúc đầu).
2. `i <= 5` → **điều kiện** kiểm tra trước mỗi vòng. Còn `true` thì còn lặp.
3. `i++` → **cập nhật** sau mỗi vòng (tăng `i` lên 1).

Kết quả in ra "Lần thử login thứ 1" đến "...thứ 5".

> 💡 Lập trình viên thường đếm từ `0`. Với mảng/list (mục sau), index bắt đầu từ `0`, nên hay viết `for (int i = 0; i < n; i++)`.

### Vòng lặp `while`

Dùng khi **không biết trước** số lần, chỉ biết **điều kiện dừng**:

```java
int soLanThu = 0;
boolean loginThanhCong = false;

while (!loginThanhCong && soLanThu < 3) {
    soLanThu++;
    System.out.println("Đang thử login lần " + soLanThu);
    // giả sử lần thứ 2 thì thành công
    if (soLanThu == 2) {
        loginThanhCong = true;
    }
}
System.out.println("Kết quả: " + (loginThanhCong ? "Thành công" : "Thất bại"));
```

**Giải thích:** lặp **chừng nào** (`while`) chưa login thành công **và** chưa quá 3 lần. Đây là mẫu "retry" rất hay gặp trong automation. ⚠️ Nhớ **cập nhật biến điều kiện** bên trong vòng lặp (`soLanThu++`), nếu không sẽ **lặp vô tận** (chương trình treo).

### `do-while` — chạy ít nhất 1 lần

```java
int n = 10;
do {
    System.out.println("Chạy ít nhất một lần dù điều kiện sai");
} while (n < 5);  // điều kiện sai ngay, nhưng thân đã chạy 1 lần
```

Khác `while` ở chỗ: kiểm tra điều kiện **sau** khi chạy thân, nên thân **luôn chạy tối thiểu 1 lần**.

### `for-each` — duyệt từng phần tử (dùng nhiều nhất!)

Khi có một **danh sách** và muốn duyệt **từng phần tử** mà không quan tâm index:

```java
public class DuyetDanhSach {
    public static void main(String[] args) {
        String[] danhSachSanPham = {"Áo thun", "Quần jean", "Giày", "Mũ"};

        for (String sanPham : danhSachSanPham) {
            System.out.println("Kiểm tra sản phẩm: " + sanPham);
        }
    }
}
```

Đọc là: "**với mỗi** `sanPham` **trong** `danhSachSanPham`, làm...". Gọn hơn `for` thường và tránh lỗi index. Đây là kiểu vòng lặp bạn sẽ dùng nhiều nhất khi duyệt list element trong Playwright.

### `break` và `continue`

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;      // THOÁT hẳn vòng lặp khi i = 5
    }
    if (i % 2 == 0) {
        continue;   // BỎ QUA phần còn lại, sang vòng kế (bỏ số chẵn)
    }
    System.out.println(i); // in 1, 3 (rồi break ở 5)
}
```

- `break` → **thoát hẳn** vòng lặp.
- `continue` → **bỏ qua** phần còn lại của vòng hiện tại, nhảy sang vòng tiếp theo.

---

## 1.5. Mảng (Array)

**Mảng** là một dãy nhiều giá trị **cùng kiểu**, có **kích thước cố định**. Ví von: một dãy tủ khóa đánh số từ 0.

```java
public class MangCoBan {
    public static void main(String[] args) {
        // Cách 1: khai báo và gán giá trị luôn
        String[] usernames = {"admin", "user01", "guest"};

        // Cách 2: tạo mảng rỗng cỡ 3 rồi gán từng phần tử
        int[] diemTest = new int[3];
        diemTest[0] = 90;   // phần tử đầu tiên có index 0
        diemTest[1] = 75;
        diemTest[2] = 60;

        System.out.println("Username đầu tiên: " + usernames[0]); // admin
        System.out.println("Số phần tử: " + usernames.length);    // 3

        // Duyệt mảng bằng for thường (dùng index)
        for (int i = 0; i < diemTest.length; i++) {
            System.out.println("Điểm thứ " + i + " = " + diemTest[i]);
        }
    }
}
```

**Giải thích quan trọng:**
- **Index bắt đầu từ 0!** Mảng 3 phần tử có index `0, 1, 2`. `usernames[0]` là phần tử **đầu tiên**.
- `usernames.length` → số phần tử (chú ý: **không có** dấu ngoặc `()`, khác với `String`).
- `new int[3]` → tạo mảng 3 số nguyên, tự khởi tạo giá trị `0`.
- Truy cập index không tồn tại (vd `usernames[3]`) → lỗi `ArrayIndexOutOfBoundsException`.

> Mảng có kích thước **cố định** — không thêm/bớt phần tử được. Khi cần danh sách "co giãn", ta dùng `List` (mục kế tiếp).

---

## 1.6. `List` — Danh Sách Co Giãn

`List` giống mảng nhưng **thêm/xóa phần tử thoải mái**. Đây là collection bạn sẽ dùng **nhiều nhất** trong automation (danh sách sản phẩm, danh sách link, danh sách element...).

```java
import java.util.ArrayList;
import java.util.List;

public class DanhSachList {
    public static void main(String[] args) {
        // Tạo một List chứa các String
        List<String> gioHang = new ArrayList<>();

        gioHang.add("Áo thun");      // thêm phần tử
        gioHang.add("Quần jean");
        gioHang.add("Giày");

        System.out.println("Số sản phẩm: " + gioHang.size());     // 3
        System.out.println("Sản phẩm đầu: " + gioHang.get(0));    // Áo thun
        System.out.println("Có 'Giày' không? " + gioHang.contains("Giày")); // true

        gioHang.remove("Quần jean"); // xóa phần tử

        // Duyệt bằng for-each
        for (String sp : gioHang) {
            System.out.println("Trong giỏ: " + sp);
        }
    }
}
```

**Giải thích từng phần:**
- `import java.util.List;` và `import java.util.ArrayList;` → **khai báo dùng** thư viện có sẵn. Đặt ở **đầu file**. IntelliJ thường tự thêm giúp (nhấn `Alt+Enter` khi báo lỗi thiếu import).
- `List<String>` → danh sách chứa các `String`. Phần `<String>` gọi là **generics** — nói "list này chỉ chứa String". Sẽ học kỹ ở Tuần 3.
- `new ArrayList<>()` → tạo một list rỗng. `List` là "bản thiết kế", `ArrayList` là "loại cụ thể" ta dùng.
- Các method quan trọng:

| Method | Tác dụng |
|--------|----------|
| `.add(x)` | Thêm `x` vào cuối list |
| `.get(i)` | Lấy phần tử ở vị trí `i` (từ 0) |
| `.size()` | Số phần tử (có `()`, khác `array.length`) |
| `.remove(x)` | Xóa phần tử `x` |
| `.contains(x)` | Kiểm tra list có chứa `x` không (trả về boolean) |
| `.isEmpty()` | List rỗng không? |
| `.set(i, x)` | Thay phần tử ở vị trí `i` bằng `x` |

> 💡 **Mảng vs List:** Mảng cố định kích thước, cú pháp `[]`. List co giãn, dùng method `.add()/.get()`. Trong automation, gần như luôn dùng **List**.

---

## 1.7. `Map` — Từ Điển Khóa → Giá Trị

`Map` lưu các cặp **khóa (key) → giá trị (value)**. Ví von: một cuốn từ điển — tra "từ" (key) ra "nghĩa" (value). Hoặc: danh bạ — tra "tên" ra "số điện thoại".

Trong testing rất hay dùng: map `username → password`, map `tên → tuổi`, map `mã lỗi → mô tả`.

```java
import java.util.HashMap;
import java.util.Map;

public class TuDienMap {
    public static void main(String[] args) {
        // Map từ tên người dùng (String) sang tuổi (Integer)
        Map<String, Integer> tuoiNguoiDung = new HashMap<>();

        tuoiNguoiDung.put("admin", 30);   // thêm cặp key -> value
        tuoiNguoiDung.put("user01", 25);
        tuoiNguoiDung.put("guest", 18);

        // Lấy value theo key
        System.out.println("Tuổi của admin: " + tuoiNguoiDung.get("admin")); // 30

        // Kiểm tra có key không
        System.out.println("Có 'guest'? " + tuoiNguoiDung.containsKey("guest")); // true

        // Duyệt toàn bộ map
        for (Map.Entry<String, Integer> entry : tuoiNguoiDung.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue() + " tuổi");
        }
    }
}
```

**Giải thích:**
- `Map<String, Integer>` → key kiểu `String`, value kiểu `Integer` (số nguyên dạng object — xem mục lỗi thường gặp về `int` vs `Integer`).
- `.put(key, value)` → thêm/cập nhật một cặp. Nếu key đã tồn tại thì **ghi đè** value.
- `.get(key)` → lấy value theo key. Nếu key không tồn tại, trả về `null`.
- `.containsKey(key)` → kiểm tra có key đó không.
- `.entrySet()` → lấy tất cả các cặp để duyệt bằng for-each. `entry.getKey()` và `entry.getValue()` lấy key/value từng cặp.

| Method | Tác dụng |
|--------|----------|
| `.put(k, v)` | Thêm/cập nhật cặp key→value |
| `.get(k)` | Lấy value theo key (null nếu không có) |
| `.containsKey(k)` | Có key này không? |
| `.remove(k)` | Xóa cặp có key `k` |
| `.size()` | Số cặp |
| `.keySet()` | Tập tất cả key |
| `.values()` | Tập tất cả value |

---

## 1.8. Method (Hàm)

**Method** là một "khối code có tên" làm **một việc cụ thể**, có thể gọi lại nhiều lần. Ví von: một công thức nấu ăn — đưa nguyên liệu (tham số) vào, nhận món ăn (giá trị trả về) ra.

Lợi ích: **tránh lặp code**, code gọn, dễ đọc, dễ sửa. Trong automation, mỗi thao tác (login, thêm giỏ hàng, kiểm tra tiêu đề) sẽ là một method.

### Cấu trúc một method

```java
public class ViduMethod {

    // Method có tham số và trả về giá trị
    public static boolean laSoChan(int so) {
        return so % 2 == 0;
    }

    // Method có tham số nhưng KHÔNG trả về (void)
    public static void inLoiChao(String ten) {
        System.out.println("Xin chào, " + ten);
    }

    // Method trả về String
    public static String taoLoiChao(String ten) {
        return "Xin chào, " + ten;
    }

    public static void main(String[] args) {
        System.out.println(laSoChan(4));   // true
        System.out.println(laSoChan(7));   // false

        inLoiChao("Lan");                  // Xin chào, Lan

        String loi = taoLoiChao("Minh");
        System.out.println(loi);           // Xin chào, Minh
    }
}
```

**Giải thích cấu trúc `public static KiểuTrảVề tênMethod(tham_số)`:**
- `public static` → cứ tạm giữ nguyên cụm này cho các method trong `Main` (sẽ hiểu rõ `static` ở Tuần 2–3).
- **Kiểu trả về:** `boolean`, `String`, `int`... là loại giá trị method **trả ra**. Nếu method **không trả gì**, dùng `void`.
- **Tham số** `(int so)` → "nguyên liệu" đưa vào. Có thể nhiều tham số, cách nhau bằng dấu phẩy: `(String user, String pass)`.
- `return giá_trị;` → **trả kết quả** ra và **kết thúc** method. `void` thì không cần `return` (hoặc `return;` để thoát sớm).

### Method nhiều tham số — ví dụ testing

```java
public class KiemTraLogin {

    // Trả về true nếu đăng nhập hợp lệ
    public static boolean kiemTraLogin(String username, String password) {
        return username.equals("admin") && password.equals("123456");
    }

    public static void main(String[] args) {
        System.out.println(kiemTraLogin("admin", "123456")); // true
        System.out.println(kiemTraLogin("admin", "sai"));    // false
        System.out.println(kiemTraLogin("hacker", "123456"));// false
    }
}
```

> ⚠️ Chú ý `username.equals("admin")` — so sánh **chuỗi** bằng `.equals()`, **KHÔNG** dùng `==`. Đây là bẫy quan trọng nhất Tuần 1, xem ngay mục dưới.

### Method overloading (cùng tên, khác tham số)

Java cho phép nhiều method **trùng tên** nếu **khác danh sách tham số**:

```java
public static int cong(int a, int b) {
    return a + b;
}
public static int cong(int a, int b, int c) {   // cùng tên, 3 tham số
    return a + b + c;
}
// gọi: cong(2, 3) → 5 ;  cong(2, 3, 4) → 9
```

Java tự chọn method đúng dựa trên số/kiểu tham số bạn truyền vào. (Playwright dùng overloading rất nhiều — cùng một `click()` có nhiều biến thể.)

---

## ⚠️ Lỗi Thường Gặp Của Người Mới — Tuần 1

### 1. So sánh String bằng `==` thay vì `.equals()` (bẫy SỐ 1!)

```java
String a = "admin";
String b = "ad" + "min";  // cũng là "admin"
String c = new String("admin");

System.out.println(a == c);        // ❌ có thể là false! (so sánh "ô nhớ")
System.out.println(a.equals(c));   // ✅ true (so sánh nội dung)
```

**Vì sao:** với `String`, `==` so sánh xem hai biến có **cùng ô nhớ** không, chứ **không** so sánh nội dung chữ. Muốn so sánh **nội dung** phải dùng `.equals()`. Đây là lỗi khiến vô số test "login đúng mà báo sai".
👉 **Quy tắc:** so sánh chữ (`String`) → **luôn** dùng `.equals()`. So sánh số (`int`) → dùng `==`.

### 2. Chia số nguyên mất phần thập phân

```java
double tiLe = 3 / 4;        // ❌ = 0.0 (vì 3 và 4 đều là int → chia nguyên = 0)
double tiLeDung = 3.0 / 4;  // ✅ = 0.75
```

Muốn ra số thực, ít nhất một vế phải là `double` (thêm `.0`).

### 3. `NullPointerException` (NPE) — lỗi khét tiếng nhất

```java
String ten = null;
System.out.println(ten.length()); // ❌ NullPointerException!
```

`null` nghĩa là "chưa trỏ tới gì cả" (hộp rỗng). Gọi method trên `null` → NPE. Trong Playwright, gọi thao tác trên một element chưa tìm thấy hay gây NPE. 👉 Kiểm tra `null` trước khi dùng, hoặc đảm bảo biến đã được gán.

### 4. Truy cập index ngoài phạm vi

```java
int[] arr = {10, 20, 30};   // index hợp lệ: 0, 1, 2
System.out.println(arr[3]); // ❌ ArrayIndexOutOfBoundsException
```

Mảng 3 phần tử thì index cuối là `2`, không phải `3`. Nhớ: **index từ 0 tới length-1**.

### 5. Nhầm `int` với `Integer`

- `int` là kiểu **nguyên thủy** (primitive) — chỉ chứa số, không bao giờ `null`.
- `Integer` là kiểu **object** (bao bọc `int`) — có thể `null`, dùng trong `List<Integer>`, `Map<..., Integer>`.

```java
List<int> sai;         // ❌ SAI — generics không nhận primitive
List<Integer> dung;    // ✅ ĐÚNG — dùng Integer trong List/Map
```

Java tự chuyển qua lại (`int` ↔ `Integer`) trong hầu hết trường hợp (gọi là auto-boxing), nhưng khi dùng với `List`/`Map` bắt buộc viết `Integer`, `Double`, `Boolean`.

### 6. Quên `break` trong `switch` (kiểu cổ điển)

Quên `break` khiến code "rơi" xuống case dưới, chạy cả những nhánh không mong muốn. Dùng `switch` kiểu `->` (Java 14+) để tránh hẳn lỗi này.

### 7. Vòng lặp vô tận (quên cập nhật biến)

```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    // ❌ quên i++ → i mãi = 0 → lặp vô tận, chương trình treo
}
```

Nhớ luôn có cách để điều kiện dừng **trở thành false**.

### 8. Quên dấu `;` hoặc lệch ngoặc `{ }`

Mỗi câu lệnh kết thúc bằng `;`. Mỗi `{` phải có `}` tương ứng. IntelliJ sẽ gạch đỏ báo lỗi — hãy đọc thông báo, đừng hoảng.

---

## Bài Tập Thực Hành — Tuần 1

> Hãy **tự làm trước** trong IntelliJ, chạy thử, rồi mới xem Đáp án ở cuối tuần. Gõ tay, đừng copy.

**Bài 1.1 (Dễ) — Chào hỏi.**
Khai báo biến `String hoTen` chứa tên bạn và `int tuoi` chứa tuổi. In ra: `Tôi tên là <hoTen>, <tuoi> tuổi.`

**Bài 1.2 (Dễ) — Số chẵn/lẻ.**
Viết method `public static String chanLe(int n)` trả về `"Chẵn"` nếu `n` chẵn, `"Lẻ"` nếu lẻ. Test với `4`, `7`, `0`, `-3`.

**Bài 1.3 (Dễ–TB) — Phân loại HTTP status.**
Viết method `public static String phanLoaiStatus(int code)`:
- `200–299` → `"Thành công"`
- `400–499` → `"Lỗi phía client"`
- `500–599` → `"Lỗi phía server"`
- còn lại → `"Không xác định"`
Test với `200`, `404`, `500`, `302`.

**Bài 1.4 (TB) — Lọc tên dài.**
Cho `List<String> ten = List.of("An", "Hoang", "Nguyen", "Le", "Phamphong");`. Duyệt và **in ra những tên có độ dài > 5 ký tự**. (Gợi ý: `ten.length()` cho độ dài chuỗi.)

**Bài 1.5 (TB) — Map tên → tuổi.**
Tạo `Map<String, Integer>` chứa: `"An" → 25`, `"Bình" → 30`, `"Cường" → 22`. In ra tuổi của `"Bình"`. Sau đó duyệt in ra tất cả theo dạng `Tên: tuổi`. Cuối cùng in ra **tổng tuổi** của cả ba người.

**Bài 1.6 (TB) — Đếm số lần login thành công.**
Cho mảng kết quả login: `boolean[] ketQua = {true, false, true, true, false};`. Dùng vòng lặp đếm xem **có bao nhiêu lần thành công** và **bao nhiêu lần thất bại**, rồi in ra.

**Bài 1.7 (TB–Khó) — FizzBuzz (bài phỏng vấn kinh điển).**
In các số từ 1 đến 20. Nhưng:
- Số chia hết cho 3 → in `"Fizz"` thay vì số.
- Số chia hết cho 5 → in `"Buzz"`.
- Chia hết cho **cả** 3 và 5 → in `"FizzBuzz"`.

**Bài 1.8 (Khó) — Tìm sản phẩm đắt nhất.**
Cho hai mảng song song:
```java
String[] tenSP = {"Áo", "Quần", "Giày", "Mũ"};
double[] gia   = {150.0, 300.0, 500.0, 80.0};
```
Viết code tìm và in ra **tên sản phẩm có giá cao nhất** cùng mức giá của nó. (Gợi ý: duyệt, giữ lại index của giá lớn nhất.)

---

## ✅ Checklist Tự Kiểm Tra — Tuần 1

Đánh dấu khi bạn tự tin làm được **không cần nhìn tài liệu**:

- [ ] Khai báo được biến 4 kiểu: `int`, `double`, `boolean`, `String`.
- [ ] Biết vì sao `10 / 3 = 3` chứ không phải `3.33`.
- [ ] Phân biệt được `=` (gán) và `==` (so sánh).
- [ ] **Biết so sánh String bằng `.equals()`, KHÔNG dùng `==`.**
- [ ] Viết được `if / else if / else` và `switch`.
- [ ] Viết được cả 3 loại vòng lặp `for`, `while`, `for-each`.
- [ ] Biết index mảng/list bắt đầu từ `0`.
- [ ] Dùng được `List`: `add`, `get`, `size`, `contains`.
- [ ] Dùng được `Map`: `put`, `get`, `containsKey`, duyệt bằng `entrySet`.
- [ ] Viết được method có tham số và giá trị trả về.
- [ ] Hiểu `void` nghĩa là method không trả về gì.
- [ ] Đọc hiểu được thông báo lỗi `NullPointerException` và `ArrayIndexOutOfBoundsException`.

Nếu còn ô nào chưa chắc, đọc lại mục tương ứng và **gõ lại ví dụ**. Đừng vội sang Tuần 2.


## 📖 Đáp Án — Tuần 1

> Đừng nhìn trước khi tự làm! So sánh cách nghĩ của bạn với lời giải. Có thể có nhiều cách đúng khác nhau.

**Đáp án 1.1 — Chào hỏi.**
```java
public class Bai1_1 {
    public static void main(String[] args) {
        String hoTen = "Nguyễn Văn A";
        int tuoi = 25;
        System.out.println("Tôi tên là " + hoTen + ", " + tuoi + " tuổi.");
    }
}
```

**Đáp án 1.2 — Số chẵn/lẻ.**
```java
public class Bai1_2 {
    public static String chanLe(int n) {
        if (n % 2 == 0) {
            return "Chẵn";
        } else {
            return "Lẻ";
        }
        // Cách gọn: return (n % 2 == 0) ? "Chẵn" : "Lẻ";
    }

    public static void main(String[] args) {
        System.out.println(chanLe(4));  // Chẵn
        System.out.println(chanLe(7));  // Lẻ
        System.out.println(chanLe(0));  // Chẵn (0 chia hết cho 2)
        System.out.println(chanLe(-3)); // Lẻ
    }
}
```
> Lưu ý: `0 % 2 == 0` nên 0 được coi là chẵn. Với số âm, `-3 % 2` bằng `-1` (khác 0) nên là lẻ — vẫn đúng.

**Đáp án 1.3 — Phân loại HTTP status.**
```java
public class Bai1_3 {
    public static String phanLoaiStatus(int code) {
        if (code >= 200 && code <= 299) {
            return "Thành công";
        } else if (code >= 400 && code <= 499) {
            return "Lỗi phía client";
        } else if (code >= 500 && code <= 599) {
            return "Lỗi phía server";
        } else {
            return "Không xác định";
        }
    }

    public static void main(String[] args) {
        System.out.println(phanLoaiStatus(200)); // Thành công
        System.out.println(phanLoaiStatus(404)); // Lỗi phía client
        System.out.println(phanLoaiStatus(500)); // Lỗi phía server
        System.out.println(phanLoaiStatus(302)); // Không xác định
    }
}
```

**Đáp án 1.4 — Lọc tên dài.**
```java
import java.util.List;

public class Bai1_4 {
    public static void main(String[] args) {
        List<String> ten = List.of("An", "Hoang", "Nguyen", "Le", "Phamphong");

        for (String t : ten) {
            if (t.length() > 5) {
                System.out.println(t); // Nguyen, Phamphong
            }
        }
    }
}
```
> `"Hoang".length()` = 5, **không** lớn hơn 5 nên bị loại. Chỉ `"Nguyen"` (6) và `"Phamphong"` (9) được in.

**Đáp án 1.5 — Map tên → tuổi.**
```java
import java.util.HashMap;
import java.util.Map;

public class Bai1_5 {
    public static void main(String[] args) {
        Map<String, Integer> tuoi = new HashMap<>();
        tuoi.put("An", 25);
        tuoi.put("Bình", 30);
        tuoi.put("Cường", 22);

        System.out.println("Tuổi của Bình: " + tuoi.get("Bình")); // 30

        int tong = 0;
        for (Map.Entry<String, Integer> e : tuoi.entrySet()) {
            System.out.println(e.getKey() + ": " + e.getValue());
            tong += e.getValue();  // cộng dồn tuổi
        }
        System.out.println("Tổng tuổi: " + tong); // 77
    }
}
```

**Đáp án 1.6 — Đếm login thành công.**
```java
public class Bai1_6 {
    public static void main(String[] args) {
        boolean[] ketQua = {true, false, true, true, false};
        int thanhCong = 0;
        int thatBai = 0;

        for (boolean kq : ketQua) {
            if (kq) {
                thanhCong++;
            } else {
                thatBai++;
            }
        }
        System.out.println("Thành công: " + thanhCong); // 3
        System.out.println("Thất bại: " + thatBai);     // 2
    }
}
```
> Chú ý `if (kq)` — vì `kq` đã là `boolean` rồi nên **không cần** viết `if (kq == true)` (dù viết vậy cũng đúng, chỉ là thừa).

**Đáp án 1.7 — FizzBuzz.**
```java
public class Bai1_7 {
    public static void main(String[] args) {
        for (int i = 1; i <= 20; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                System.out.println("FizzBuzz");   // phải kiểm tra cả 3&5 TRƯỚC
            } else if (i % 3 == 0) {
                System.out.println("Fizz");
            } else if (i % 5 == 0) {
                System.out.println("Buzz");
            } else {
                System.out.println(i);
            }
        }
    }
}
```
> **Bẫy quan trọng:** phải kiểm tra điều kiện "chia hết cả 3 và 5" **ĐẦU TIÊN**. Nếu để `i % 3 == 0` lên trước, số 15 sẽ in "Fizz" và không bao giờ ra "FizzBuzz". Đây là điểm bài phỏng vấn hay bắt lỗi.

**Đáp án 1.8 — Tìm sản phẩm đắt nhất.**
```java
public class Bai1_8 {
    public static void main(String[] args) {
        String[] tenSP = {"Áo", "Quần", "Giày", "Mũ"};
        double[] gia   = {150.0, 300.0, 500.0, 80.0};

        int indexMax = 0;   // giả sử phần tử đầu là lớn nhất
        for (int i = 1; i < gia.length; i++) {
            if (gia[i] > gia[indexMax]) {
                indexMax = i;   // tìm thấy giá lớn hơn → cập nhật index
            }
        }
        System.out.println("Đắt nhất: " + tenSP[indexMax]
                + " với giá " + gia[indexMax]); // Giày với giá 500.0
    }
}
```
> Kỹ thuật "giữ index lớn nhất": bắt đầu giả định phần tử 0 là max, duyệt từ 1, gặp cái lớn hơn thì cập nhật. Nhờ giữ **index** (chứ không chỉ giá trị) mà lấy được cả tên tương ứng.


---

# 📅 TUẦN 2 — Lập Trình Hướng Đối Tượng (OOP)

**Vì sao tuần này QUAN TRỌNG NHẤT:** Mọi framework automation (kể cả Page Object Model bạn sẽ học ở Giai đoạn 5) đều **xây trên OOP**. `BasePage`, `LoginPage extends BasePage`, class `User`, class `Product`... tất cả là OOP. Hiểu tuần này = hiểu được **kiến trúc** của mọi framework test.

**OOP là gì (nói đơn giản):** Thay vì viết code rời rạc, ta **gom dữ liệu + hành động liên quan vào chung một "đối tượng"**. Ví dụ: một `User` có dữ liệu (tên, tuổi, email) và hành động (đăng nhập, đổi mật khẩu). Gom chung lại giống như đời thật: một chiếc xe có thuộc tính (màu, tốc độ) và hành động (chạy, phanh).

---

## 2.1. Class và Object

- **Class** = **bản thiết kế** (khuôn). Ví dụ: bản vẽ thiết kế một chiếc xe.
- **Object** = **sản phẩm cụ thể** tạo ra từ bản thiết kế. Ví dụ: chiếc xe màu đỏ biển số 51A-123 của bạn.

Từ **một** class (`User`), ta tạo được **nhiều** object (user admin, user guest, user test01...).

```java
// FILE: User.java — định nghĩa bản thiết kế
public class User {
    // Field (thuộc tính) — dữ liệu mà mỗi User có
    String username;
    String email;
    int tuoi;
}
```

```java
// FILE: Main.java — tạo và dùng object
public class Main {
    public static void main(String[] args) {
        // Tạo object từ class bằng từ khóa "new"
        User user1 = new User();
        user1.username = "admin";       // gán giá trị cho field
        user1.email = "admin@test.com";
        user1.tuoi = 30;

        User user2 = new User();        // một object khác, độc lập
        user2.username = "guest";
        user2.tuoi = 18;

        System.out.println(user1.username); // admin
        System.out.println(user2.username); // guest
    }
}
```

**Giải thích:**
- `public class User { ... }` → định nghĩa class `User`, đặt trong file `User.java`.
- **Field** (`username`, `email`, `tuoi`) → các "ô dữ liệu" mà **mỗi** object `User` sẽ có riêng.
- `new User()` → **tạo một object** thật từ class. Từ khóa `new` là "sản xuất một cái mới". **Quên `new` là lỗi rất hay gặp** → biến bị `null`.
- `user1.username = "admin"` → **truy cập field** bằng dấu chấm `.`, rồi gán giá trị.
- `user1` và `user2` là **hai object độc lập** — đổi cái này không ảnh hưởng cái kia.

> 💡 Trong IntelliJ, mỗi class `public` nên nằm ở **một file riêng** cùng tên (`User.java`, `Main.java`). Tạo file mới: chuột phải thư mục `src` → New → Java Class.

---

## 2.2. Method Trong Class (Hành Động Của Object)

Object không chỉ có dữ liệu, còn có **hành động**. Ta thêm method vào class:

```java
public class User {
    String username;
    String email;
    int tuoi;

    // Method: hành động của User
    public void gioiThieu() {
        System.out.println("Tôi là " + username + ", " + tuoi + " tuổi.");
    }

    public boolean laNguoiLon() {
        return tuoi >= 18;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        User u = new User();
        u.username = "admin";
        u.tuoi = 30;

        u.gioiThieu();                 // Tôi là admin, 30 tuổi.
        System.out.println(u.laNguoiLon()); // true
    }
}
```

**Giải thích:**
- Method `gioiThieu()` nằm **trong** class `User`, nên nó dùng thẳng được các field `username`, `tuoi` của **chính object** đang gọi nó.
- `u.gioiThieu()` → gọi method trên object `u`. Bên trong, `username` chính là `u.username`.
- Chú ý: các method này **không có** `static` (khác với method trong `Main` ở Tuần 1). `static` sẽ giải thích ở mục 2.8. Nhớ: method của object thì **không** `static`.

---

## 2.3. Constructor — "Nhà Máy" Tạo Object

Ở ví dụ trên, ta phải gán field từng dòng rất phiền. **Constructor** là method đặc biệt chạy **ngay khi tạo object**, giúp gán giá trị luôn.

```java
public class User {
    String username;
    String email;
    int tuoi;

    // Constructor — TÊN TRÙNG với tên class, KHÔNG có kiểu trả về
    public User(String username, String email, int tuoi) {
        this.username = username;   // this.username = field; username = tham số
        this.email = email;
        this.tuoi = tuoi;
    }

    public void gioiThieu() {
        System.out.println(username + " (" + email + ") - " + tuoi + " tuổi");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        // Truyền dữ liệu ngay khi tạo — gọn hơn hẳn
        User admin = new User("admin", "admin@test.com", 30);
        User guest = new User("guest", "guest@test.com", 18);

        admin.gioiThieu();  // admin (admin@test.com) - 30 tuổi
        guest.gioiThieu();  // guest (guest@test.com) - 18 tuổi
    }
}
```

**Giải thích:**
- Constructor **trùng tên class** (`User`) và **không có kiểu trả về** (không `void`, không `int`...). Đây là dấu hiệu nhận biết constructor.
- `this.username` → **`this`** nghĩa là "object hiện tại". `this.username` là **field**, còn `username` (không `this`) là **tham số**. Khi tên trùng nhau, `this` giúp phân biệt: "gán tham số `username` vào field `username` của object này".
- `new User("admin", "admin@test.com", 30)` → constructor chạy, gán 3 giá trị vào 3 field cùng lúc.

### Nhiều constructor (overloading)

```java
public class User {
    String username;
    int tuoi;

    public User(String username, int tuoi) {   // constructor đầy đủ
        this.username = username;
        this.tuoi = tuoi;
    }

    public User(String username) {              // constructor rút gọn
        this.username = username;
        this.tuoi = 18;                         // mặc định 18
    }
}
// new User("admin", 30)  hoặc  new User("guest")  đều được
```

> ⚠️ **Lưu ý:** Nếu bạn **tự viết** một constructor, Java **không còn** tự tạo constructor rỗng `new User()` nữa. Muốn vẫn dùng `new User()`, phải tự thêm constructor rỗng.

---

## 2.4. Encapsulation — Đóng Gói (private + getter/setter)

**Vấn đề:** để field `public`, ai cũng sửa lung tung được — kể cả gán giá trị vô lý:

```java
user.tuoi = -999;   // vô lý nhưng không ai ngăn!
```

**Encapsulation (đóng gói)** = **giấu** field đi (dùng `private`), chỉ cho truy cập qua **method có kiểm soát** (getter/setter). Ví von: bạn không cho người lạ thò tay vào ví (private), mà đưa/nhận tiền qua "cửa sổ giao dịch" có kiểm tra (getter/setter).

```java
public class User {
    private String username;   // private = chỉ dùng được BÊN TRONG class
    private int tuoi;

    public User(String username, int tuoi) {
        this.username = username;
        setTuoi(tuoi);          // dùng setter để được kiểm tra
    }

    // GETTER — đọc giá trị
    public String getUsername() {
        return username;
    }
    public int getTuoi() {
        return tuoi;
    }

    // SETTER — ghi giá trị (có kiểm tra hợp lệ)
    public void setTuoi(int tuoi) {
        if (tuoi < 0) {
            System.out.println("Tuổi không hợp lệ, đặt về 0");
            this.tuoi = 0;
        } else {
            this.tuoi = tuoi;
        }
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        User u = new User("admin", 30);

        // u.tuoi = -5;  // ❌ KHÔNG được — 'tuoi' là private
        u.setTuoi(-5);   // ✅ đi qua setter → bị chặn, đặt về 0
        System.out.println(u.getTuoi());     // 0
        System.out.println(u.getUsername()); // admin
    }
}
```

**Giải thích:**
- `private` → field chỉ truy cập được **bên trong** class `User`. Bên ngoài (như `Main`) **không** đọc/ghi thẳng được.
- **Getter** `getTuoi()` → method `public` để **đọc** field từ bên ngoài.
- **Setter** `setTuoi(...)` → method `public` để **ghi** field, kèm **kiểm tra hợp lệ** (chặn tuổi âm).
- Nhờ đóng gói, dữ liệu luôn **hợp lệ và an toàn**.

> 💡 **Mẹo IntelliJ:** viết field `private` xong, nhấn `Alt+Insert` (Windows) / `Cmd+N` (Mac) → chọn **Getter and Setter** → IntelliJ tự sinh. Không phải gõ tay!

---

## 2.5. Inheritance — Kế Thừa (Nền Tảng Của BasePage)

**Kế thừa** = một class **thừa hưởng** field và method của class khác, rồi **thêm/sửa** cái riêng. Ví von: "Chó" và "Mèo" đều là "Động vật" — chúng thừa hưởng đặc điểm chung (ăn, ngủ) rồi thêm cái riêng (sủa / kêu meo).

Đây chính là mô hình **`LoginPage extends BasePage`** bạn sẽ dùng mỗi ngày trong automation: mọi trang đều có thao tác chung (click, nhập text, chụp màn hình) đặt ở `BasePage`, mỗi trang cụ thể thêm thao tác riêng.

```java
// FILE: BasePage.java — class CHA (cha chung cho mọi trang)
public class BasePage {
    protected String url;   // protected = con dùng được, ngoài thì không

    public void moTrang() {
        System.out.println("Điều hướng tới: " + url);
    }

    public void chupManHinh() {
        System.out.println("Đã chụp màn hình trang hiện tại");
    }
}
```

```java
// FILE: LoginPage.java — class CON, kế thừa BasePage
public class LoginPage extends BasePage {

    public LoginPage() {
        this.url = "https://www.saucedemo.com";  // dùng field kế thừa từ cha
    }

    // Method RIÊNG của LoginPage
    public void dangNhap(String user, String pass) {
        System.out.println("Nhập username: " + user);
        System.out.println("Nhập password: " + pass);
        System.out.println("Click nút Login");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        LoginPage loginPage = new LoginPage();

        loginPage.moTrang();                       // ← kế thừa từ BasePage
        loginPage.dangNhap("admin", "123456");     // ← method riêng của LoginPage
        loginPage.chupManHinh();                    // ← kế thừa từ BasePage
    }
}
```

**Giải thích:**
- `class LoginPage extends BasePage` → `LoginPage` **kế thừa** (`extends`) mọi thứ `public`/`protected` từ `BasePage`. Nên `loginPage` gọi được cả `moTrang()`, `chupManHinh()` (của cha) lẫn `dangNhap()` (của mình).
- `protected` → như `private` nhưng **class con vẫn dùng được**. Field `url` khai báo ở cha, con `LoginPage` gán được.
- **Lợi ích:** thao tác chung viết **một lần** ở `BasePage`, mọi trang con dùng lại. Sửa một chỗ, cả framework hưởng lợi. Đây là "code không lặp lại" — trụ cột của framework tốt.

### `super` và Override (ghi đè)

Class con có thể **ghi đè** (override) method của cha để làm khác đi, và dùng `super` để gọi bản của cha:

```java
public class BasePage {
    public void moTrang() {
        System.out.println("BasePage: mở trang");
    }
}

public class LoginPage extends BasePage {
    @Override                      // annotation: báo "đây là ghi đè"
    public void moTrang() {
        super.moTrang();           // gọi lại phiên bản của cha (tùy chọn)
        System.out.println("LoginPage: chờ nút Login hiện ra");
    }
}
```

**Giải thích:**
- `@Override` → **annotation** đánh dấu "method này ghi đè method cùng tên của cha". Không bắt buộc, nhưng **nên** viết: nếu bạn gõ sai tên, Java sẽ báo lỗi ngay (rất hữu ích).
- `super.moTrang()` → gọi bản `moTrang()` **của class cha**. `super` = "cha của tôi". Dùng khi muốn giữ hành vi cha rồi bổ sung thêm.
- Khi gọi `loginPage.moTrang()`, Java chạy bản **của con** (bản đã override).

> Trong Playwright, bạn sẽ override `@Override` method `@BeforeMethod` để mỗi loại test setup khác nhau. Hiểu override từ bây giờ là rất đáng.

---

## 2.6. Interface và Abstract Class

Cả hai đều là cách định nghĩa **"khuôn hợp đồng"** — quy định class phải có những method gì, nhưng chưa (hoặc chưa hẳn) viết nội dung.

### Interface — "Hợp đồng thuần"

**Interface** liệt kê các method mà class thực thi nó **phải có**, nhưng **không** viết nội dung (chỉ khai báo). Ví von: một "chuẩn phích cắm điện" — bất cứ thiết bị nào muốn cắm được đều phải theo chuẩn đó.

```java
// FILE: Browser.java
public interface Browser {
    void moTrang(String url);   // chỉ khai báo, KHÔNG có thân {}
    void dongTrinhDuyet();
}
```

```java
// FILE: ChromeBrowser.java — "implements" = cam kết thực thi interface
public class ChromeBrowser implements Browser {
    @Override
    public void moTrang(String url) {
        System.out.println("Chrome mở: " + url);
    }
    @Override
    public void dongTrinhDuyet() {
        System.out.println("Đóng Chrome");
    }
}

// FILE: FirefoxBrowser.java
public class FirefoxBrowser implements Browser {
    @Override
    public void moTrang(String url) {
        System.out.println("Firefox mở: " + url);
    }
    @Override
    public void dongTrinhDuyet() {
        System.out.println("Đóng Firefox");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        // Biến kiểu Browser có thể trỏ tới BẤT KỲ class nào implements nó
        Browser b1 = new ChromeBrowser();
        Browser b2 = new FirefoxBrowser();

        b1.moTrang("https://saucedemo.com");  // Chrome mở: ...
        b2.moTrang("https://saucedemo.com");  // Firefox mở: ...
    }
}
```

**Giải thích:**
- `interface Browser` → định nghĩa **hợp đồng**: bất kỳ browser nào cũng phải biết `moTrang` và `dongTrinhDuyet`.
- Method trong interface **không có thân** (`;` luôn thay vì `{}`).
- `class ChromeBrowser implements Browser` → cam kết thực thi. **Bắt buộc** viết đầy đủ mọi method trong interface, nếu không sẽ báo lỗi.
- **Điểm mạnh (polymorphism):** biến kiểu `Browser` có thể trỏ tới `ChromeBrowser` hay `FirefoxBrowser` — cùng cách gọi `moTrang()`, khác nhau ở nội dung. Đây là nền tảng của **Factory Pattern** (chọn browser lúc chạy) ở Giai đoạn 5.

### Abstract Class — "Nửa khuôn, nửa thật"

**Abstract class** ở giữa class thường và interface: có thể có **một số method viết sẵn** (chung) và **một số method để trống** (bắt con tự viết). Không thể tạo object trực tiếp từ nó.

```java
public abstract class BaseTest {
    // Method viết sẵn — dùng chung cho mọi test
    public void setup() {
        System.out.println("Khởi tạo browser, mở trang chủ");
    }
    public void teardown() {
        System.out.println("Đóng browser, dọn dẹp");
    }

    // Method abstract — CHƯA viết, bắt class con phải viết
    public abstract void chayTest();
}
```

```java
public class LoginTest extends BaseTest {
    @Override
    public void chayTest() {   // bắt buộc viết vì cha để abstract
        System.out.println("Chạy kịch bản: đăng nhập");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        // BaseTest bt = new BaseTest(); // ❌ KHÔNG được — abstract không tạo object
        LoginTest test = new LoginTest();
        test.setup();     // kế thừa sẵn từ BaseTest
        test.chayTest();  // bản riêng của LoginTest
        test.teardown();  // kế thừa sẵn
    }
}
```

**Giải thích:**
- `abstract class BaseTest` → không tạo object trực tiếp được; chỉ để class con kế thừa.
- `public abstract void chayTest();` → method **abstract** (chưa có thân) → **bắt buộc** class con viết.
- `setup()`, `teardown()` → viết sẵn, con dùng chung.

### Khi nào Interface, khi nào Abstract Class?

| | **Interface** | **Abstract class** |
|---|---|---|
| Chứa gì | Chủ yếu khai báo method (hợp đồng) | Có cả method viết sẵn lẫn abstract, có field |
| Kế thừa | Một class `implements` **nhiều** interface | Chỉ `extends` **một** abstract class |
| Dùng khi | Nhiều class không liên quan cùng "có khả năng" X | Các class **cùng họ** chia sẻ code chung |
| Ví dụ automation | `Browser`, `Comparable` | `BasePage`, `BaseTest` |

Người mới chưa cần phân biệt tinh vi — chỉ cần **nhận ra** hai khái niệm này khi đọc code framework. Trong thực tế, `BasePage`/`BaseTest` thường là class thường hoặc abstract; interface hay gặp ở callback của Playwright (chính là functional interface — Tuần 3!).

---

## 2.7. `static` — Thuộc Về Class, Không Thuộc Object

Bình thường, field/method **thuộc về object** — mỗi object có bản riêng. Còn `static` thì **thuộc về class** — **dùng chung** cho tất cả, gọi thẳng qua tên class **không cần tạo object**.

Ví von: `soLuongUser` (đếm tổng số user) nên là `static` — vì nó là con số chung của cả "loài User", không riêng của user nào.

```java
public class User {
    private String username;
    public static int soLuongUser = 0;   // static: dùng chung cho MỌI User

    public User(String username) {
        this.username = username;
        soLuongUser++;                    // mỗi lần tạo User, tăng biến chung
    }

    // Method static: gọi được KHÔNG cần object
    public static boolean usernameHopLe(String u) {
        return u != null && u.length() >= 3;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        // Gọi method static qua TÊN CLASS, không cần new
        System.out.println(User.usernameHopLe("ad"));    // false
        System.out.println(User.usernameHopLe("admin")); // true

        new User("admin");
        new User("guest");
        System.out.println(User.soLuongUser);            // 2 (biến chung)
    }
}
```

**Giải thích:**
- `static int soLuongUser` → **một** biến duy nhất dùng chung cho mọi object `User`. Mỗi lần `new User(...)` đều tăng cùng một biến này → đếm được tổng số.
- `User.usernameHopLe("admin")` → gọi method `static` **qua tên class**, không cần `new`. Nó là "hàm tiện ích" không phụ thuộc dữ liệu object cụ thể.
- **Đây chính là lý do** `main` phải là `static`: Java gọi `main` khi **chưa có** object nào cả.
- Các method tiện ích bạn viết ở Tuần 1 (`chanLe`, `laSoChan`...) đều là `static` — chúng là hàm độc lập, không gắn với object.

> ⚠️ **Quy tắc dễ nhớ:** method của **object** (dùng field object) → **không** static. Hàm **tiện ích** không phụ thuộc object cụ thể → **static**. Method `static` **không** truy cập được field/method không-static (vì chưa chắc có object nào).

---

## ⚠️ Lỗi Thường Gặp Của Người Mới — Tuần 2

### 1. Quên `new` → NullPointerException

```java
User u;              // mới khai báo, CHƯA tạo object → u = null
u.gioiThieu();       // ❌ NPE! vì u chưa trỏ tới object nào
```
Phải `User u = new User(...)`. **Quên `new` là nguyên nhân NPE phổ biến nhất** trong OOP.

### 2. Nhầm Overload với Override

- **Overload:** cùng tên, **khác tham số**, trong **cùng** class (hoặc chỗ khác). VD hai `cong(int,int)` và `cong(int,int,int)`.
- **Override:** cùng tên, **cùng tham số**, ở class **con** ghi đè class **cha**.

Luôn viết `@Override` khi ghi đè — Java sẽ báo lỗi nếu bạn tưởng override nhưng thực ra chỉ overload (do gõ sai chữ ký).

### 3. Quên `this` khi tên tham số trùng field

```java
public User(String username) {
    username = username;   // ❌ gán tham số cho chính nó! field không đổi
}
```
Phải `this.username = username;`. Không có `this`, Java hiểu cả hai là **tham số**, field vẫn rỗng.

### 4. Cố tạo object từ abstract class / interface

```java
BaseTest t = new BaseTest();  // ❌ không được — abstract
Browser b = new Browser();    // ❌ không được — interface
```
Chỉ tạo object từ **class con cụ thể**: `new LoginTest()`, `new ChromeBrowser()`.

### 5. Gọi field/method non-static từ `main` (static)

```java
public class Main {
    String ten = "abc";     // non-static
    public static void main(String[] args) {
        System.out.println(ten); // ❌ lỗi: main là static, ten là non-static
    }
}
```
Trong `main` (static), muốn dùng thứ non-static thì phải **tạo object** trước: `new Main().ten`.

### 6. Để field `public` (không đóng gói)

Không sai cú pháp, nhưng **thói quen xấu**. Nên để `private` + getter/setter để kiểm soát dữ liệu. IntelliJ sinh getter/setter tự động, không tốn công.

### 7. `implements` mà thiếu method

Khi `implements` một interface, **phải viết đủ** mọi method của nó. Thiếu một cái → không biên dịch được. IntelliJ gợi ý "Implement methods" (`Alt+Enter`) để sinh khung sẵn.

---

## Bài Tập Thực Hành — Tuần 2

**Bài 2.1 (Dễ) — Class `Product`.**
Tạo class `Product` với 3 field `public`: `String ten`, `double gia`, `int soLuong`. Trong `Main`, tạo 2 object, gán giá trị, in ra thông tin từng sản phẩm.

**Bài 2.2 (Dễ–TB) — Thêm constructor và method.**
Nâng cấp `Product` ở bài 2.1: thêm constructor nhận cả 3 field; thêm method `double tongTien()` trả về `gia * soLuong`; thêm method `void inThongTin()`. Tạo object bằng constructor và gọi các method.

**Bài 2.3 (TB) — Đóng gói class `User`.**
Tạo class `User` với field `private`: `username`, `email`, `tuoi`. Viết constructor + getter/setter đầy đủ. Trong setter của `tuoi`, chặn giá trị âm (đặt về 0) và giá trị > 150 (đặt về 150). Test bằng cách set `-5`, `200`, `25` rồi in ra.

**Bài 2.4 (TB) — Kế thừa `BasePage` / `LoginPage`.**
Tạo `BasePage` với field `protected String url` và method `moTrang()` (in "Mở trang: <url>"), `nhapText(String o, String giaTri)` (in "Nhập '<giaTri>' vào ô <o>"). Tạo `LoginPage extends BasePage` với method `dangNhap(String user, String pass)` gọi lại `nhapText(...)` hai lần rồi in "Click Login". Trong `Main`, dùng `LoginPage` để đăng nhập.

**Bài 2.5 (TB–Khó) — Override.**
Tạo `BasePage` có method `moTrang()` in "BasePage đang mở trang". Tạo `HomePage extends BasePage` **override** `moTrang()`: gọi `super.moTrang()` rồi in thêm "HomePage: chờ banner hiển thị". Chạy và quan sát thứ tự in.

**Bài 2.6 (Khó) — Interface `Browser`.**
Tạo interface `Browser` với method `moTrang(String url)` và `String tenTrinhDuyet()`. Tạo `ChromeBrowser` và `WebkitBrowser` implements nó. Trong `Main`, tạo một `List<Browser>` chứa cả hai, duyệt qua và gọi `moTrang("https://test.com")` cho từng cái (thể hiện polymorphism).

**Bài 2.7 (Khó) — `static` đếm object.**
Tạo class `TestCase` với field `private String ten` và một field `static int tongSoTest`. Mỗi lần tạo object `TestCase`, tăng `tongSoTest`. Thêm method `static int getTongSoTest()`. Trong `Main`, tạo 4 object rồi in tổng số test đã tạo.

---

## ✅ Checklist Tự Kiểm Tra — Tuần 2

- [ ] Phân biệt được **class** (bản thiết kế) và **object** (sản phẩm cụ thể).
- [ ] Tạo được object bằng `new` và truy cập field/method bằng dấu `.`.
- [ ] Viết được **constructor** và hiểu `this`.
- [ ] Biết dùng `private` + getter/setter (**encapsulation**) và vì sao nên đóng gói.
- [ ] Viết được class con `extends` class cha và dùng lại method kế thừa.
- [ ] Hiểu và dùng được `@Override` và `super`.
- [ ] Đọc hiểu `interface` + `implements`, biết một biến interface trỏ được nhiều class (polymorphism).
- [ ] Phân biệt được (đại khái) interface vs abstract class.
- [ ] Hiểu `static` là "thuộc về class", biết vì sao `main` phải static.
- [ ] Đọc được cấu trúc `LoginPage extends BasePage` — nền tảng framework sắp học.


## 📖 Đáp Án — Tuần 2

**Đáp án 2.1 — Class `Product`.**
```java
// FILE: Product.java
public class Product {
    public String ten;
    public double gia;
    public int soLuong;
}

// FILE: Main.java
public class Main {
    public static void main(String[] args) {
        Product p1 = new Product();
        p1.ten = "Áo thun";
        p1.gia = 150.0;
        p1.soLuong = 3;

        Product p2 = new Product();
        p2.ten = "Giày";
        p2.gia = 500.0;
        p2.soLuong = 1;

        System.out.println(p1.ten + " - " + p1.gia + " x " + p1.soLuong);
        System.out.println(p2.ten + " - " + p2.gia + " x " + p2.soLuong);
    }
}
```

**Đáp án 2.2 — Constructor và method.**
```java
public class Product {
    public String ten;
    public double gia;
    public int soLuong;

    public Product(String ten, double gia, int soLuong) {
        this.ten = ten;
        this.gia = gia;
        this.soLuong = soLuong;
    }

    public double tongTien() {
        return gia * soLuong;
    }

    public void inThongTin() {
        System.out.println(ten + ": " + gia + " x " + soLuong
                + " = " + tongTien());
    }
}

public class Main {
    public static void main(String[] args) {
        Product p = new Product("Áo thun", 150.0, 3);
        p.inThongTin();                       // Áo thun: 150.0 x 3 = 450.0
        System.out.println("Tổng: " + p.tongTien()); // 450.0
    }
}
```

**Đáp án 2.3 — Đóng gói `User`.**
```java
public class User {
    private String username;
    private String email;
    private int tuoi;

    public User(String username, String email, int tuoi) {
        this.username = username;
        this.email = email;
        setTuoi(tuoi);   // đi qua setter để được kiểm tra ngay từ constructor
    }

    public String getUsername() { return username; }
    public void setUsername(String username) { this.username = username; }

    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }

    public int getTuoi() { return tuoi; }
    public void setTuoi(int tuoi) {
        if (tuoi < 0) {
            this.tuoi = 0;
        } else if (tuoi > 150) {
            this.tuoi = 150;
        } else {
            this.tuoi = tuoi;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        User u = new User("admin", "admin@test.com", 25);
        System.out.println(u.getTuoi()); // 25

        u.setTuoi(-5);
        System.out.println(u.getTuoi()); // 0

        u.setTuoi(200);
        System.out.println(u.getTuoi()); // 150
    }
}
```

**Đáp án 2.4 — Kế thừa `BasePage`/`LoginPage`.**
```java
// FILE: BasePage.java
public class BasePage {
    protected String url;

    public void moTrang() {
        System.out.println("Mở trang: " + url);
    }

    public void nhapText(String o, String giaTri) {
        System.out.println("Nhập '" + giaTri + "' vào ô " + o);
    }
}

// FILE: LoginPage.java
public class LoginPage extends BasePage {
    public LoginPage() {
        this.url = "https://www.saucedemo.com";
    }

    public void dangNhap(String user, String pass) {
        nhapText("username", user);   // dùng method kế thừa từ BasePage
        nhapText("password", pass);
        System.out.println("Click Login");
    }
}

// FILE: Main.java
public class Main {
    public static void main(String[] args) {
        LoginPage loginPage = new LoginPage();
        loginPage.moTrang();                    // Mở trang: https://www.saucedemo.com
        loginPage.dangNhap("admin", "123456");
    }
}
```

**Đáp án 2.5 — Override.**
```java
public class BasePage {
    public void moTrang() {
        System.out.println("BasePage đang mở trang");
    }
}

public class HomePage extends BasePage {
    @Override
    public void moTrang() {
        super.moTrang();  // chạy phần của cha trước
        System.out.println("HomePage: chờ banner hiển thị");
    }
}

public class Main {
    public static void main(String[] args) {
        HomePage home = new HomePage();
        home.moTrang();
        // Kết quả (đúng thứ tự):
        // BasePage đang mở trang
        // HomePage: chờ banner hiển thị
    }
}
```

**Đáp án 2.6 — Interface `Browser` + polymorphism.**
```java
// FILE: Browser.java
public interface Browser {
    void moTrang(String url);
    String tenTrinhDuyet();
}

// FILE: ChromeBrowser.java
public class ChromeBrowser implements Browser {
    @Override
    public void moTrang(String url) {
        System.out.println("[Chrome] mở " + url);
    }
    @Override
    public String tenTrinhDuyet() { return "Chrome"; }
}

// FILE: WebkitBrowser.java
public class WebkitBrowser implements Browser {
    @Override
    public void moTrang(String url) {
        System.out.println("[WebKit] mở " + url);
    }
    @Override
    public String tenTrinhDuyet() { return "WebKit"; }
}

// FILE: Main.java
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Browser> dsBrowser = List.of(new ChromeBrowser(), new WebkitBrowser());

        for (Browser b : dsBrowser) {
            System.out.println("Đang chạy trên: " + b.tenTrinhDuyet());
            b.moTrang("https://test.com");
        }
        // Cùng vòng lặp, cùng cách gọi, nhưng mỗi browser hành xử khác nhau
        // → đây chính là polymorphism (đa hình), nền tảng của Factory Pattern.
    }
}
```

**Đáp án 2.7 — `static` đếm object.**
```java
public class TestCase {
    private String ten;
    private static int tongSoTest = 0;   // dùng chung cho mọi object

    public TestCase(String ten) {
        this.ten = ten;
        tongSoTest++;                    // mỗi object mới → +1
    }

    public static int getTongSoTest() {
        return tongSoTest;
    }
}

public class Main {
    public static void main(String[] args) {
        new TestCase("Login test");
        new TestCase("Search test");
        new TestCase("Cart test");
        new TestCase("Checkout test");

        System.out.println("Tổng số test: " + TestCase.getTongSoTest()); // 4
    }
}
```


---

# 📅 TUẦN 3 — Java Thực Dụng Cho Automation

**Đây là tuần "vàng".** Những thứ trong tuần này là **thứ Playwright dùng liên tục** mà người mới hay hổng. Đặc biệt là **Lambda** — nếu không hiểu, bạn sẽ copy code Playwright mà không biết mình đang viết gì. Chúng ta sẽ dạy Lambda **thật kỹ**.

**Nội dung tuần 3:**
1. **Lambda & Functional Interface (TRỌNG TÂM — dạy kỹ nhất)**
2. Generics cơ bản (`List<T>`, `ThreadLocal<Page>`)
3. Enum
4. Exception handling (`try/catch/finally`, `try-with-resources`)
5. Đọc/ghi file cơ bản
6. Stream API (`filter`, `map`, `collect`)
7. Annotation là gì
8. **Debug bằng IntelliJ** (breakpoint, step, Evaluate Expression)

---

## 3.1. ⭐ Lambda & Functional Interface (PHẦN QUAN TRỌNG NHẤT)

> Hãy đọc mục này **chậm**, gõ lại **mọi** ví dụ. Đây là chỗ quyết định bạn có hiểu code Playwright hay không.

### Bối cảnh: Vì sao phải học Lambda?

Mở tài liệu Playwright Java, bạn sẽ thấy ngay những dòng như:

```java
page.onDialog(dialog -> dialog.accept());
page.waitForResponse("**/api/users", () -> page.click("#load"));
page.waitForPopup(() -> page.click("a[target=_blank]"));
locator.all().forEach(item -> System.out.println(item.textContent()));
```

Những cái `dialog -> dialog.accept()` và `() -> page.click(...)` chính là **lambda**. Nếu bạn không hiểu nó, bạn sẽ bị "khựng" ngay ở test đầu tiên. Vậy nên ta phá vỡ nỗi sợ này ngay bây giờ.

### Lambda là gì? (giải thích đời thường)

**Lambda là một "hành động" được đóng gói để đưa cho code khác chạy sau.** Nó là "một đoạn code bạn truyền đi như một giá trị".

Ví von: Bạn giao cho người giúp việc một **tờ ghi chú**: "**Khi** có người bấm chuông cửa, **hãy** mở cửa và mời họ vào". Bạn không tự mở cửa ngay — bạn đưa **hướng dẫn** (một hành động) để người khác thực hiện **khi đến lúc**. Lambda chính là tờ ghi chú đó.

Trong Playwright: `page.onDialog(dialog -> dialog.accept())` nghĩa là "**Khi** có hộp thoại (dialog) hiện ra, **hãy** chấp nhận (accept) nó". Bạn không biết khi nào dialog xuất hiện — nên bạn đưa **hành động** cho Playwright giữ, nó sẽ chạy hành động đó **khi** dialog hiện lên. Đây gọi là **callback** (hàm gọi lại).

### Functional Interface — "cái khuôn" chứa lambda

Trước khi hiểu cú pháp lambda, cần hiểu nó "rót vào đâu". Câu trả lời: **functional interface**.

**Functional interface** là một interface **chỉ có ĐÚNG MỘT method chưa viết** (một "hành động" cần định nghĩa). Vì chỉ có một method, Java thừa biết bạn định viết method nào → cho phép bạn viết ngắn gọn bằng lambda.

```java
@FunctionalInterface
interface HanhDong {
    void thucHien();   // chỉ đúng 1 method → là functional interface
}
```

- `@FunctionalInterface` → annotation đánh dấu "đây là functional interface". Không bắt buộc, nhưng nếu bạn lỡ thêm method thứ 2, Java báo lỗi ngay.
- Một method `thucHien()` chưa có nội dung → chờ được "điền" bằng lambda.

### Từ cách cũ (anonymous class) ĐẾN lambda — so sánh trực tiếp

Đây là phần **quan trọng nhất** để "thông" lambda. Ta cùng làm **một việc** bằng 3 cách, từ dài tới ngắn.

**Việc cần làm:** đưa cho method `chay(...)` một hành động "in ra Hello".

**Cách 1 — Class thường (dài dòng nhất):**
```java
@FunctionalInterface
interface HanhDong {
    void thucHien();
}

// Một class riêng thực thi interface
class InHello implements HanhDong {
    @Override
    public void thucHien() {
        System.out.println("Hello!");
    }
}

public class Main {
    static void chay(HanhDong hd) {  // nhận một "hành động"
        hd.thucHien();               // rồi thực hiện nó
    }
    public static void main(String[] args) {
        chay(new InHello());         // phải tạo cả một class chỉ để in Hello
    }
}
```

**Cách 2 — Anonymous class (class vô danh — code Java "cũ", trước Java 8):**
```java
public class Main {
    static void chay(HanhDong hd) { hd.thucHien(); }

    public static void main(String[] args) {
        chay(new HanhDong() {          // tạo class "vô danh" ngay tại chỗ
            @Override
            public void thucHien() {
                System.out.println("Hello!");
            }
        });
    }
}
```
Đỡ hơn (không cần file class riêng), nhưng vẫn **rất dài** cho một việc đơn giản: nào là `new HanhDong()`, `@Override`, `public void thucHien()`... chỉ để nói "in Hello".

**Cách 3 — Lambda (Java 8+, cách hiện đại — NGẮN GỌN):**
```java
public class Main {
    static void chay(HanhDong hd) { hd.thucHien(); }

    public static void main(String[] args) {
        chay(() -> System.out.println("Hello!"));   // 🎉 CHỈ MỘT DÒNG
    }
}
```

**So sánh trực tiếp — cùng một việc:**

```java
// ANONYMOUS CLASS (cũ):
chay(new HanhDong() {
    @Override
    public void thucHien() {
        System.out.println("Hello!");
    }
});

// LAMBDA (mới) — GIỐNG HỆT nhưng bỏ hết "phần thừa":
chay(() -> System.out.println("Hello!"));
```

**Java tự hiểu:** vì `HanhDong` chỉ có **một** method (`thucHien`), Java biết chắc lambda này là để viết method đó. Nên bạn **không cần** viết lại `new HanhDong()`, `@Override`, tên method, kiểu... Java điền hết giúp. Bạn chỉ cần cung cấp: **(tham số) -> (nội dung)**. Đó chính là lambda.

> 💡 **Chốt ý:** Lambda = anonymous class được **rút gọn tối đa**, chỉ dùng được khi interface có **đúng 1 method** (functional interface). Playwright thiết kế mọi callback của nó là functional interface, chính là để bạn viết được bằng lambda gọn gàng.

### Cú pháp Lambda — 3 dạng bạn PHẢI thuộc

Cấu trúc chung: **`(tham số) -> (việc cần làm)`**. Mũi tên `->` đọc là "thì làm" hoặc "trở thành".

#### Dạng 1: `() -> ...` — KHÔNG có tham số

Dùng khi hành động **không cần dữ liệu đầu vào**.

```java
() -> System.out.println("Chạy!")
() -> page.click("#load")          // Playwright: "hãy click nút load"
```

Cặp ngoặc `()` rỗng nghĩa là "không nhận tham số nào".

#### Dạng 2: `x -> ...` — MỘT tham số

Dùng khi hành động **cần một dữ liệu đầu vào**. Có thể bỏ ngoặc quanh tham số.

```java
dialog -> dialog.accept()          // Playwright: "nhận dialog, thì accept nó"
name -> System.out.println(name)   // nhận name, thì in ra
n -> n * 2                         // nhận n, thì trả về n nhân 2
```

`dialog` ở đây là **tên tham số** bạn tự đặt (đặt `d` cũng được). Playwright sẽ "trao" object dialog vào đó khi dialog xuất hiện.

#### Dạng 3: `(a, b) -> ...` — NHIỀU tham số

Dùng khi cần **hai (hoặc hơn) đầu vào**. Bắt buộc có ngoặc.

```java
(a, b) -> a + b                    // nhận a và b, trả về tổng
(user, pass) -> login(user, pass)  // nhận 2 giá trị, gọi login
```

#### Thân lambda: một dòng hay nhiều dòng?

```java
// Một biểu thức: viết thẳng, KẾT QUẢ tự được "return"
x -> x * 2

// Nhiều dòng: dùng ngoặc nhọn { }, và PHẢI tự viết return nếu cần trả về
x -> {
    int ketQua = x * 2;
    System.out.println("Đang xử lý " + x);
    return ketQua;
}
```

| Kiểu thân | Cú pháp | `return` |
|-----------|---------|----------|
| Một biểu thức | `x -> x * 2` | Tự động, **không viết** `return` |
| Khối nhiều lệnh | `x -> { ...; return y; }` | **Phải tự viết** `return` |

### Ví dụ chạy được đầy đủ — tự định nghĩa functional interface

```java
public class LambdaTuDinhNghia {

    // 3 functional interface khác nhau
    @FunctionalInterface interface KhongThamSo   { void chay(); }
    @FunctionalInterface interface MotThamSo     { void xuLy(String s); }
    @FunctionalInterface interface CoTraVe       { int tinh(int a, int b); }

    public static void main(String[] args) {
        // Dạng 1: () ->
        KhongThamSo hanhDong = () -> System.out.println("Không tham số, chỉ chạy");
        hanhDong.chay();

        // Dạng 2: x ->
        MotThamSo inHoa = ten -> System.out.println("Xin chào " + ten.toUpperCase());
        inHoa.xuLy("admin");   // Xin chào ADMIN

        // Dạng 3: (a, b) ->
        CoTraVe cong = (a, b) -> a + b;
        System.out.println("Tổng: " + cong.tinh(3, 5));   // 8
    }
}
```

**Giải thích:**
- `KhongThamSo hanhDong = () -> ...` → gán một lambda vào biến kiểu functional interface. Lambda **là** phần thực thi của method `chay()`.
- `hanhDong.chay()` → **kích hoạt** lambda (chạy nội dung đã đóng gói).
- Với `CoTraVe cong = (a, b) -> a + b;`, khi gọi `cong.tinh(3, 5)`, `a=3`, `b=5`, kết quả `8` được trả về (tự return vì là một biểu thức).

### Các Functional Interface CÓ SẴN của Java (gặp nhiều nhất)

Bạn không phải lúc nào cũng tự định nghĩa interface. Java có sẵn một bộ trong `java.util.function` (và `Runnable`). Đây là những cái bạn sẽ gặp:

| Interface | Method | Ý nghĩa | Ví dụ lambda |
|-----------|--------|---------|--------------|
| `Runnable` | `run()` | Hành động, không input, không output | `() -> page.click("#x")` |
| `Consumer<T>` | `accept(T)` | Nhận 1 input, không trả về ("tiêu thụ") | `s -> System.out.println(s)` |
| `Supplier<T>` | `get()` | Không input, trả về 1 giá trị ("cung cấp") | `() -> "dữ liệu"` |
| `Function<T,R>` | `apply(T)` | Nhận T, trả về R (biến đổi) | `s -> s.length()` |
| `Predicate<T>` | `test(T)` | Nhận T, trả về `boolean` (kiểm tra) | `n -> n > 5` |
| `BiFunction<T,U,R>` | `apply(T,U)` | Nhận 2 input, trả về 1 | `(a,b) -> a + b` |

Ví dụ chạy được:

```java
import java.util.function.*;

public class FunctionalCoSan {
    public static void main(String[] args) {
        // Consumer: nhận 1, không trả về
        Consumer<String> inRa = s -> System.out.println("Log: " + s);
        inRa.accept("Bắt đầu test");           // Log: Bắt đầu test

        // Supplier: không nhận, trả về
        Supplier<String> layToken = () -> "token-abc-123";
        System.out.println(layToken.get());     // token-abc-123

        // Function: nhận String, trả về Integer (độ dài)
        Function<String, Integer> doDai = s -> s.length();
        System.out.println(doDai.apply("admin")); // 5

        // Predicate: nhận Integer, trả về boolean
        Predicate<Integer> laNguoiLon = tuoi -> tuoi >= 18;
        System.out.println(laNguoiLon.test(20)); // true
        System.out.println(laNguoiLon.test(15)); // false
    }
}
```

Đừng cố học thuộc bảng này ngay — chỉ cần **nhận ra** khi gặp. `Predicate` (trả boolean, để lọc) và `Consumer`/`Runnable` (làm hành động) là hay gặp nhất.

### 🎭 LIÊN HỆ TRỰC TIẾP TỚI PLAYWRIGHT (phần "aha")

Bây giờ ta soi lại đúng những dòng Playwright ở đầu mục, và bạn sẽ **hiểu hết**:

```java
// 1) CALLBACK dialog: "KHI có dialog, hãy accept nó"
page.onDialog(dialog -> dialog.accept());
```
- `onDialog(...)` nhận một lambda dạng **1 tham số** (`dialog -> ...`).
- Playwright giữ lambda này. **Khi** trang bật một hộp thoại (alert/confirm), Playwright trao object `dialog` vào và chạy `dialog.accept()`.
- Đây đúng là "tờ ghi chú" ta ví von: bạn không biết khi nào dialog hiện, nên đưa **hành động** cho Playwright.

```java
// 2) CHỜ CÓ ĐIỀU KIỆN: "hãy click #load, và chờ response từ API users"
Response res = page.waitForResponse("**/api/users", () -> page.click("#load"));
```
- Tham số thứ hai là lambda dạng **không tham số** (`() -> page.click("#load")`).
- Playwright cần **bắt đầu lắng nghe** response *trước*, **rồi mới** thực hiện hành động gây ra request. Nó làm đúng thứ tự đó bằng cách: bật lắng nghe → chạy lambda (`page.click`) → chờ response khớp `**/api/users`.
- Nếu không có lambda, bạn sẽ dễ click **trước** khi kịp lắng nghe → bỏ lỡ response (một lỗi race condition kinh điển). Lambda giải quyết gọn.

```java
// 3) CHỜ POPUP: click link mở tab mới, Playwright trả về Page của popup
Page popup = page.waitForPopup(() -> page.click("a[target=_blank]"));
```

```java
// 4) DUYỆT DANH SÁCH element bằng forEach + lambda
page.locator(".product-name").all()
    .forEach(item -> System.out.println(item.textContent()));
```
- `.all()` trả về `List<Locator>`. `.forEach(item -> ...)` chạy lambda cho **từng** element: `item` lần lượt là từng locator, in text của nó.

```java
// 5) route/mock API cũng dùng lambda
page.route("**/api/**", route -> route.fulfill(
    new Route.FulfillOptions().setBody("{ \"ok\": true }")));
```

> **Chốt lại:** Ở đâu bạn thấy `->` trong code Playwright, hãy đọc là: "**đây là một hành động tôi đưa cho Playwright chạy vào đúng lúc**". Tham số bên trái `->` là "dữ liệu Playwright sẽ trao cho tôi" (dialog, route, response...), phần bên phải là "việc tôi muốn làm với nó". Hiểu tới đây là bạn đã qua được cửa ải khó nhất của người mới. 🎉

### Method Reference — viết tắt của lambda (biết để đọc code)

Khi lambda **chỉ gọi đúng một method có sẵn**, Java cho viết tắt bằng `::`:

```java
// Lambda thường:
Consumer<String> in1 = s -> System.out.println(s);
// Method reference (viết tắt tương đương):
Consumer<String> in2 = System.out::println;

list.forEach(s -> System.out.println(s));   // lambda
list.forEach(System.out::println);          // method reference — giống hệt
```

`System.out::println` đọc là "dùng method `println` của `System.out`". Bạn **không cần** tự viết method reference lúc mới học, nhưng phải **nhận ra** `::` là "lambda viết tắt" khi đọc code.

---

## 3.2. Generics Cơ Bản (`List<T>`, `ThreadLocal<Page>`)

Bạn đã dùng generics từ Tuần 1 mà chưa biết tên: `List<String>`, `Map<String, Integer>`. Phần trong `< >` chính là **generics**.

**Generics là gì:** cách nói cho Java biết một "hộp chứa" (như `List`, `Map`) sẽ chứa **kiểu gì**. Ví von: một cái thùng có dán nhãn "CHỈ ĐỰNG SÁCH" — bạn không bỏ nhầm giày vào được.

```java
List<String> ten = new ArrayList<>();
ten.add("admin");
// ten.add(123);   // ❌ lỗi ngay lúc viết code — vì list này chỉ chứa String

String x = ten.get(0);  // ✅ lấy ra chắc chắn là String, không cần ép kiểu
```

**Lợi ích:**
1. **An toàn:** bỏ nhầm kiểu → báo lỗi **ngay khi gõ**, không đợi chạy mới sập.
2. **Không phải ép kiểu:** `ten.get(0)` chắc chắn ra `String`.

`T`, `K`, `V`, `R` chỉ là **chữ đại diện cho một kiểu** (T = Type, K = Key, V = Value). `List<T>` nghĩa là "list chứa kiểu T nào đó". Khi dùng thật, `T` được thay bằng kiểu cụ thể: `List<String>`, `List<User>`, `List<Product>`.

### `ThreadLocal<Page>` — bạn sẽ gặp ở framework parallel

Trong automation chạy song song (parallel), mỗi luồng (thread) cần một `Page` **riêng** để không "giẫm chân" nhau. `ThreadLocal<Page>` là "hộp chứa một Page riêng cho mỗi thread".

```java
// Xem trước — sẽ học kỹ ở Giai đoạn 6. Giờ chỉ cần ĐỌC HIỂU cú pháp generics.
public class DriverManager {
    private static ThreadLocal<Page> pageThreadLocal = new ThreadLocal<>();

    public static void setPage(Page page) {
        pageThreadLocal.set(page);       // đặt Page cho thread hiện tại
    }
    public static Page getPage() {
        return pageThreadLocal.get();    // lấy Page CỦA RIÊNG thread hiện tại
    }
}
```

- `ThreadLocal<Page>` → generics: "một ThreadLocal chứa kiểu `Page`".
- `.set(page)` / `.get()` → mỗi thread thao tác trên **bản riêng** của nó. Không cần hiểu sâu bây giờ, chỉ cần **không sợ** khi thấy cú pháp `ThreadLocal<Page>` — nó chỉ là generics.

### Viết một generic method đơn giản (đọc hiểu là đủ)

```java
public class TienIch {
    // <T> nghĩa là: method này làm việc với MỘT kiểu bất kỳ tên T
    public static <T> T layPhanTuDau(List<T> list) {
        return list.get(0);
    }

    public static void main(String[] args) {
        List<String> ten = List.of("admin", "guest");
        List<Integer> so = List.of(10, 20, 30);

        System.out.println(layPhanTuDau(ten)); // admin (T = String)
        System.out.println(layPhanTuDau(so));  // 10    (T = Integer)
    }
}
```

Cùng một method `layPhanTuDau` chạy được với `List<String>` lẫn `List<Integer>` nhờ generics. Người mới chỉ cần **đọc hiểu** — chưa cần tự viết generic method.

---

## 3.3. Enum — Tập Hợp Hằng Số Có Tên

**Enum** là kiểu dữ liệu có **một tập giá trị cố định, có tên rõ ràng**. Ví von: các ngày trong tuần, các hướng (Bắc/Nam/Đông/Tây) — danh sách đóng, không thêm bừa.

Trong automation cực hay dùng cho: **loại browser**, **môi trường** (dev/staging/prod), **loại user**.

```java
public enum BrowserType {
    CHROMIUM,
    FIREFOX,
    WEBKIT
}
```

```java
public class Main {
    public static void main(String[] args) {
        BrowserType browser = BrowserType.FIREFOX;

        // Dùng với switch rất gọn và an toàn
        switch (browser) {
            case CHROMIUM -> System.out.println("Khởi động Chromium");
            case FIREFOX  -> System.out.println("Khởi động Firefox");
            case WEBKIT   -> System.out.println("Khởi động WebKit");
        }
    }
}
```

**Vì sao dùng enum thay vì String `"firefox"`?**
- **An toàn:** `BrowserType.FIREFOX` không thể gõ sai. Còn `"firefox"` dễ gõ nhầm thành `"Firfox"` → bug âm thầm.
- **Gợi ý IDE:** IntelliJ liệt kê sẵn các giá trị hợp lệ.
- **Rõ ràng:** đọc code biết ngay chỉ có 3 loại browser.

### Enum môi trường — ví dụ thực tế

```java
public enum Environment {
    DEV("https://dev.myapp.com"),
    STAGING("https://staging.myapp.com"),
    PROD("https://myapp.com");

    private final String url;              // mỗi hằng đi kèm một URL

    Environment(String url) {              // constructor của enum
        this.url = url;
    }
    public String getUrl() {
        return url;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Environment env = Environment.STAGING;
        System.out.println("Chạy test trên: " + env);          // STAGING
        System.out.println("URL: " + env.getUrl());            // https://staging.myapp.com

        // Duyệt tất cả giá trị của enum
        for (Environment e : Environment.values()) {
            System.out.println(e + " -> " + e.getUrl());
        }
    }
}
```

**Giải thích:**
- Enum có thể mang **dữ liệu kèm theo** (ở đây mỗi môi trường gắn một `url`) qua constructor.
- `Environment.values()` → trả về mảng tất cả giá trị enum, duyệt được bằng for-each.
- Rất thực tế: đọc biến môi trường `ENV=staging` → chọn `Environment.STAGING` → lấy đúng URL. Bạn sẽ làm y hệt ở Giai đoạn 5 (config đa môi trường).


---

## 3.4. Exception Handling — Xử Lý Lỗi

**Exception (ngoại lệ)** là lỗi xảy ra **lúc chạy** chương trình: file không tồn tại, chia cho 0, gọi method trên `null`, mạng lỗi... Nếu không xử lý, chương trình **dừng đột ngột** (crash). Trong automation, một element không tìm thấy, một request timeout... đều ném exception.

### `try / catch` — "thử và bắt lỗi"

Ví von: bạn **thử** làm một việc rủi ro; nếu **có sự cố** thì có sẵn phương án dự phòng thay vì để mọi thứ sụp đổ.

```java
public class TryCatchCoBan {
    public static void main(String[] args) {
        try {
            int a = 10;
            int b = 0;
            int ketQua = a / b;               // ⚠️ chia cho 0 → ném ArithmeticException
            System.out.println(ketQua);       // dòng này KHÔNG chạy tới
        } catch (ArithmeticException e) {
            System.out.println("Lỗi chia cho 0: " + e.getMessage());
        }
        System.out.println("Chương trình vẫn chạy tiếp!"); // vẫn chạy nhờ đã bắt lỗi
    }
}
```

**Giải thích:**
- `try { ... }` → đặt code **có thể lỗi** vào đây.
- `catch (ArithmeticException e) { ... }` → **nếu** có lỗi loại `ArithmeticException`, nhảy vào đây thay vì crash. `e` là object lỗi; `e.getMessage()` cho biết chi tiết.
- Nhờ bắt lỗi, chương trình **không sập** mà chạy tiếp.

### `finally` — luôn chạy dù có lỗi hay không

```java
try {
    System.out.println("Mở kết nối / mở browser");
    int x = 5 / 0;                       // ném lỗi
} catch (ArithmeticException e) {
    System.out.println("Bắt được lỗi: " + e.getMessage());
} finally {
    System.out.println("Đóng browser / dọn dẹp");  // LUÔN chạy
}
```

`finally` **luôn** chạy — dù có lỗi hay không, dù đã `return`. Dùng để **dọn dẹp** (đóng browser, đóng file, đóng kết nối). Trong automation, `finally` hay dùng để `browser.close()` cho chắc chắn.

### Bắt nhiều loại lỗi

```java
try {
    // ... code
} catch (ArithmeticException e) {
    System.out.println("Lỗi tính toán");
} catch (NullPointerException e) {
    System.out.println("Lỗi null");
} catch (Exception e) {         // Exception là "cha" của mọi lỗi — bắt tất cả còn lại
    System.out.println("Lỗi khác: " + e.getMessage());
}
```

`Exception` là loại "chung nhất" (cha của mọi exception) — bắt được **mọi** lỗi. Nên đặt nó **cuối cùng**. ⚠️ Đừng lạm dụng `catch (Exception e)` rồi bỏ trống — nuốt lỗi âm thầm khiến debug khốn khổ.

### `throw` và `throws` — ném lỗi ra

Đôi khi bạn muốn **chủ động** báo lỗi khi dữ liệu không hợp lệ:

```java
public static void datTuoi(int tuoi) {
    if (tuoi < 0) {
        throw new IllegalArgumentException("Tuổi không được âm: " + tuoi);
    }
    System.out.println("Đặt tuổi = " + tuoi);
}
```

- `throw new ...Exception(...)` → **ném** một lỗi ra ngoài (người gọi phải xử lý).
- `throws` (có `s`) khai báo trên method: "method này *có thể* ném loại lỗi này" — người gọi biết mà chuẩn bị `try/catch`. Bạn sẽ thấy `throws IOException` ở phần đọc file dưới đây.

### `try-with-resources` — tự động đóng tài nguyên (RẤT QUAN TRỌNG)

Với những thứ cần **đóng lại sau khi dùng** (file, kết nối, và... **`Playwright`**!), Java có cú pháp `try (...)` **tự đóng** giúp bạn — kể cả khi có lỗi.

```java
// Đây CHÍNH LÀ mẫu bạn thấy trong test Playwright đầu tiên!
try (Playwright playwright = Playwright.create()) {
    Browser browser = playwright.chromium().launch();
    Page page = browser.newPage();
    page.navigate("https://playwright.dev");
    System.out.println(page.title());
}   // ← hết try, playwright TỰ ĐỘNG được đóng (không cần gọi .close())
```

**Giải thích:**
- `try (Playwright playwright = Playwright.create())` → mở tài nguyên **trong ngoặc** của `try`.
- Khi khối `try` kết thúc (dù xong bình thường hay do lỗi), Java **tự gọi `.close()`** cho `playwright`. Không lo quên đóng → không rò rỉ tài nguyên.
- Điều kiện: tài nguyên phải "đóng được" (implements `AutoCloseable`). `Playwright`, file stream... đều vậy.

> 🎯 Đây là lý do test Playwright đầu tiên (xem giáo trình Giai đoạn 3) viết `try (Playwright playwright = Playwright.create()) { ... }`. Giờ bạn hiểu **vì sao** rồi — nó tự đóng Playwright cho bạn.

---

## 3.5. Đọc / Ghi File Cơ Bản

Trong automation, đọc file để lấy **dữ liệu test** (data-driven): đọc danh sách user từ file, ghi kết quả/log ra file. Đây là bước đệm cho Giai đoạn 5.

### Đọc toàn bộ file thành danh sách dòng (cách gọn nhất)

Giả sử có file `users.txt`:
```
admin,123456
guest,guest123
test01,pass01
```

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class DocFile {
    public static void main(String[] args) {
        try {
            List<String> dong = Files.readAllLines(Path.of("users.txt"));
            for (String d : dong) {
                String[] phan = d.split(",");     // tách theo dấu phẩy
                System.out.println("User: " + phan[0] + " | Pass: " + phan[1]);
            }
        } catch (IOException e) {
            System.out.println("Không đọc được file: " + e.getMessage());
        }
    }
}
```

**Giải thích:**
- `Files.readAllLines(Path.of("users.txt"))` → đọc **tất cả các dòng** vào một `List<String>`. Mỗi phần tử là một dòng.
- `d.split(",")` → tách một dòng `"admin,123456"` thành mảng `["admin", "123456"]`.
- Thao tác file **bắt buộc** xử lý `IOException` (lỗi vào/ra) — nên phải bọc `try/catch`. Đây là "checked exception" (lỗi Java bắt buộc bạn xử lý).

### Ghi file

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class GhiFile {
    public static void main(String[] args) {
        List<String> ketQua = List.of(
            "Test login: PASS",
            "Test search: PASS",
            "Test checkout: FAIL"
        );
        try {
            Files.write(Path.of("ket-qua.txt"), ketQua);
            System.out.println("Đã ghi kết quả ra file ket-qua.txt");
        } catch (IOException e) {
            System.out.println("Lỗi ghi file: " + e.getMessage());
        }
    }
}
```

`Files.write(Path.of("ket-qua.txt"), ketQua)` ghi mỗi phần tử của list thành một dòng trong file.

### Đọc file lớn bằng `BufferedReader` + try-with-resources

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class DocFileLon {
    public static void main(String[] args) {
        try (BufferedReader reader = Files.newBufferedReader(Path.of("users.txt"))) {
            String dong;
            while ((dong = reader.readLine()) != null) {   // đọc từng dòng tới hết
                System.out.println("Đọc: " + dong);
            }
        } catch (IOException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }   // reader tự đóng nhờ try-with-resources
}
```

Lưu ý cách kết hợp **try-with-resources** (mục 3.4) với đọc file — reader tự đóng, không rò rỉ. `reader.readLine()` trả về `null` khi hết file, nên vòng `while` dừng.

> 💡 File `users.txt` đặt ở **thư mục gốc của project** (ngang hàng `src`) để `Path.of("users.txt")` tìm thấy. Nếu không thấy file, kiểm tra vị trí và tên (đây là lỗi hay gặp).

---

## 3.6. Stream API — Xử Lý Danh Sách Kiểu Hiện Đại

**Stream** là cách xử lý danh sách theo kiểu "dây chuyền": **lọc → biến đổi → thu thập**, viết gọn và dễ đọc. Nó **kết hợp lambda** (mục 3.1) nên là "đất diễn" của lambda.

Ví von: một dây chuyền sản xuất. Dữ liệu chảy qua các trạm: trạm **lọc** (`filter`) giữ lại cái đạt, trạm **biến đổi** (`map`) chế biến, trạm cuối **đóng gói** (`collect`) thành kết quả.

### So sánh: vòng lặp cũ vs Stream

**Bài toán:** từ danh sách sản phẩm, lấy tên các sản phẩm có giá > 100, viết HOA.

**Cách cũ (vòng lặp):**
```java
List<String> ketQua = new ArrayList<>();
for (Product p : sanPham) {
    if (p.getGia() > 100) {                 // lọc
        ketQua.add(p.getTen().toUpperCase()); // biến đổi + thu thập
    }
}
```

**Cách Stream (gọn, đọc như tiếng Anh):**
```java
List<String> ketQua = sanPham.stream()
    .filter(p -> p.getGia() > 100)          // lọc: giữ cái giá > 100
    .map(p -> p.getTen().toUpperCase())     // biến đổi: lấy tên, viết hoa
    .collect(Collectors.toList());          // thu thập thành List
```

### Ví dụ chạy được đầy đủ

```java
import java.util.List;
import java.util.stream.Collectors;

public class StreamCoBan {

    record Product(String ten, double gia) {}   // record: class dữ liệu gọn (Java 16+)

    public static void main(String[] args) {
        List<Product> sanPham = List.of(
            new Product("Áo thun", 150),
            new Product("Bút bi", 5),
            new Product("Giày", 500),
            new Product("Tẩy", 3)
        );

        // Lọc sản phẩm > 100, lấy tên viết hoa, thu thành List
        List<String> dat = sanPham.stream()
            .filter(p -> p.gia() > 100)
            .map(p -> p.ten().toUpperCase())
            .collect(Collectors.toList());
        System.out.println(dat);   // [ÁO THUN, GIÀY]

        // Đếm số sản phẩm rẻ (< 10)
        long soRe = sanPham.stream()
            .filter(p -> p.gia() < 10)
            .count();
        System.out.println("Số sản phẩm rẻ: " + soRe);  // 2

        // In từng tên bằng forEach + lambda
        sanPham.forEach(p -> System.out.println("- " + p.ten()));
    }
}
```

**Giải thích các "trạm" hay dùng:**

| Method | Tác dụng | Ví dụ |
|--------|----------|-------|
| `.stream()` | Bắt đầu dây chuyền từ một List | `list.stream()` |
| `.filter(điều kiện)` | **Giữ lại** phần tử thỏa điều kiện (nhận `Predicate`) | `.filter(p -> p.gia() > 100)` |
| `.map(biến đổi)` | **Biến đổi** mỗi phần tử (nhận `Function`) | `.map(p -> p.ten())` |
| `.collect(Collectors.toList())` | **Thu** kết quả về một List | |
| `.count()` | Đếm số phần tử còn lại | |
| `.forEach(hành động)` | Làm gì đó với từng phần tử (nhận `Consumer`) | `.forEach(System.out::println)` |
| `.sorted()` | Sắp xếp | |
| `.anyMatch(đk)` / `.allMatch(đk)` | Có/mọi phần tử thỏa điều kiện? (trả boolean) | |

**Quan sát quan trọng:** mọi tham số của `filter`, `map`, `forEach`... đều là **lambda**. Đây là lý do ta học lambda **trước** stream. Trong Playwright bạn sẽ viết:
```java
List<String> tenSP = page.locator(".product-name").all().stream()
    .map(loc -> loc.textContent())
    .collect(Collectors.toList());
```
→ "lấy tất cả element tên sản phẩm, biến mỗi cái thành text, thu thành List". Đọc trơn tru nhờ đã hiểu stream + lambda.

---

## 3.7. Annotation Là Gì

**Annotation** là "mẩu ghi chú đặc biệt" bắt đầu bằng `@`, đặt **trên** class/method/field để **cung cấp thông tin thêm** cho Java hoặc thư viện. Nó **không phải** code chạy — nó là "nhãn dán" mà công cụ khác đọc để biết phải làm gì.

Ví von: nhãn dán trên thùng hàng ("DỄ VỠ", "MẶT NÀY LÊN TRÊN") — không phải món hàng, nhưng chỉ dẫn cách xử lý.

Bạn đã gặp `@Override`, `@FunctionalInterface`. Các annotation hay gặp:

| Annotation | Ý nghĩa |
|-----------|---------|
| `@Override` | "Method này ghi đè method của class cha" — Java kiểm tra giúp |
| `@FunctionalInterface` | "Interface này chỉ có 1 method" — để dùng lambda |
| `@Deprecated` | "Cái này lỗi thời, đừng dùng nữa" (như `type()` trong Playwright) |
| `@Test` | (JUnit/TestNG) "Đây là một test case cần chạy" — học ở Giai đoạn 2 |
| `@BeforeEach` / `@BeforeMethod` | "Chạy method này **trước mỗi** test" (setup) |
| `@SuppressWarnings` | "Bỏ qua cảnh báo này" |

Ví dụ bạn sẽ viết ở Giai đoạn 2 (xem trước cho quen mặt):

```java
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.BeforeEach;

public class LoginTest {

    @BeforeEach                       // chạy TRƯỚC mỗi test
    void setup() {
        System.out.println("Mở browser, vào trang login");
    }

    @Test                             // ĐÂY là một test case
    void loginThanhCong() {
        System.out.println("Kiểm tra đăng nhập đúng");
    }

    @Test
    void loginThatBai() {
        System.out.println("Kiểm tra đăng nhập sai");
    }
}
```

**Giải thích:** Test runner (JUnit) **đọc** annotation `@Test` để biết method nào là test và tự chạy chúng; đọc `@BeforeEach` để chạy setup trước mỗi test. Bản thân annotation không "làm gì" — nó chỉ **báo hiệu** cho framework. Người mới chỉ cần **hiểu vai trò "nhãn báo hiệu"** này; cách dùng chi tiết sẽ học ở Giai đoạn 2.

---

## 3.8. 🐞 Debug Bằng IntelliJ (Breakpoint, Step, Evaluate Expression)

> Đây là **kỹ năng dùng hằng ngày** của automation engineer, quan trọng ngang việc viết code. Khi test đỏ, người giỏi **debug bằng breakpoint** thay vì rải `System.out.println` khắp nơi rồi đoán mò.

**Debug là gì:** cho chương trình **chạy chậm lại và dừng ở điểm bạn chọn** (breakpoint), để bạn **soi giá trị từng biến** ngay tại thời điểm đó, chạy **từng dòng một** và xem điều gì thực sự xảy ra. Giống như xem lại video quay chậm một pha bóng để biết lỗi ở đâu.

### Chương trình mẫu để tập debug

Gõ chương trình sau (có một lỗi logic để ta cùng "bắt"):

```java
import java.util.List;

public class DebugDemo {

    public static int tinhTong(List<Integer> so) {
        int tong = 0;
        for (int i = 0; i < so.size(); i++) {
            tong = tong + so.get(i);
        }
        return tong;
    }

    public static void main(String[] args) {
        List<Integer> diem = List.of(10, 20, 30, 40);
        int ketQua = tinhTong(diem);
        System.out.println("Tổng điểm: " + ketQua);   // kỳ vọng 100
    }
}
```

### Bước 1 — Đặt Breakpoint

- **Breakpoint** = điểm dừng. Nhấp chuột **vào lề trái** (ngay cạnh số dòng) tại dòng `tong = tong + so.get(i);`. Một **chấm tròn đỏ** xuất hiện → đã đặt breakpoint.
- Đặt thêm một breakpoint ở dòng `int ketQua = tinhTong(diem);` trong `main`.

### Bước 2 — Chạy ở chế độ Debug

- Thay vì nút ▶ (Run), nhấn nút **🐞 (Debug)** ngay cạnh nó (hoặc chuột phải → **Debug 'DebugDemo.main()'**).
- Chương trình chạy tới breakpoint đầu tiên rồi **DỪNG**. Dòng sắp chạy được **tô sáng** (thường màu xanh). Khung **Debug** hiện ra ở dưới.

### Bước 3 — Đọc cửa sổ Variables (xem giá trị biến)

- Trong khung Debug, tab **Variables** liệt kê **mọi biến đang tồn tại** và giá trị hiện tại của chúng: `so = [10, 20, 30, 40]`, `tong = 0`, `i = 0`...
- Đây là "phép màu": bạn thấy **chính xác** giá trị mọi biến tại thời điểm dừng, không phải đoán.

### Bước 4 — Các nút Step (chạy từng bước)

Trên thanh Debug có các nút điều khiển:

| Nút | Tên | Tác dụng |
|-----|-----|----------|
| ⤵ (F8) | **Step Over** | Chạy **dòng hiện tại** rồi dừng ở dòng kế. Nếu dòng gọi method, chạy hết method đó (không nhảy vào trong). Dùng nhiều nhất. |
| ⤷ (F7) | **Step Into** | **Nhảy vào bên trong** method đang gọi để xem nó chạy thế nào. |
| ⤴ (Shift+F8) | **Step Out** | Chạy nốt method hiện tại rồi **thoát ra** chỗ gọi nó. |
| ▶ (F9) | **Resume** | Chạy tiếp tới **breakpoint tiếp theo** (hoặc hết chương trình). |

**Thực hành:** đứng ở breakpoint trong `main` (dòng gọi `tinhTong`), nhấn **Step Into (F7)** → con trỏ **nhảy vào** method `tinhTong`. Rồi nhấn **Step Over (F8)** nhiều lần → xem `tong` **lớn dần** qua từng vòng lặp: `0 → 10 → 30 → 60 → 100`, `i` tăng `0 → 1 → 2 → 3`. Bạn **tận mắt** thấy phép tính diễn ra.

### Bước 5 — Evaluate Expression (tính thử một biểu thức tại chỗ)

Đây là công cụ **cực mạnh**: khi đang dừng, bạn có thể **tính thử bất kỳ biểu thức nào** với giá trị biến hiện tại — không cần sửa code.

- Nhấn nút **Evaluate Expression** (biểu tượng máy tính, hoặc phím `Alt+F8`).
- Gõ vào ô, ví dụ: `so.get(i)` → nhấn **Evaluate** → thấy kết quả (vd `20`).
- Thử: `tong + 100`, `so.size()`, `i * 2`, `so.get(i) > 15`... → xem kết quả tức thì.
- Dùng để **kiểm tra giả thuyết**: "nếu tôi cộng thêm 5 thì sao?", "biểu thức điều kiện này ra true hay false?".

### Bước 6 — Conditional Breakpoint (breakpoint có điều kiện)

Khi vòng lặp chạy 1000 lần mà bạn chỉ quan tâm lúc `i == 500`:

- **Chuột phải** vào chấm đỏ breakpoint → hiện ô **Condition**.
- Gõ điều kiện, ví dụ: `i == 2`.
- Bây giờ chương trình **chỉ dừng khi `i == 2`**, bỏ qua các vòng khác. Cực hữu ích khi debug bảng dữ liệu lớn.

### Vì sao debug quan trọng với automation?

Khi một test Playwright fail, bạn đặt breakpoint **ngay dòng thao tác lỗi**, chạy Debug, rồi:
- Xem **locator** đang trỏ tới cái gì, `getText()` trả về gì thật sự.
- Dùng **Evaluate Expression** thử `page.locator("#abc").count()` để biết có bao nhiêu element khớp (bắt lỗi strict mode).
- Chạy **Step Over** để xem chính xác dòng nào ném exception.

👉 Kỹ năng này giúp bạn **tiết kiệm hàng giờ** so với việc rải `println` rồi chạy đi chạy lại. Hãy tập ngay từ bây giờ trên chương trình Java thường, để tới Playwright là dùng thành thạo.

> 💡 **Mẹo:** Muốn tạm tắt tất cả breakpoint mà không xóa: nhấn **Mute Breakpoints** (biểu tượng chấm đỏ gạch chéo) trong khung Debug.

---

## ⚠️ Lỗi Thường Gặp Của Người Mới — Tuần 3

### 1. Biến dùng trong lambda phải "effectively final"

```java
int demSo = 0;
Runnable r = () -> System.out.println(demSo);
demSo = 5;   // ❌ lỗi biên dịch: biến dùng trong lambda không được thay đổi sau đó
```
Biến bên ngoài mà lambda dùng phải **không bị gán lại** (effectively final). Nếu cần đếm/tích lũy, dùng field, `AtomicInteger`, hoặc cách khác. Người mới hay vấp khi cố `count++` trong lambda.

### 2. Quên `.collect(...)` — stream không "chạy"

```java
sanPham.stream().filter(p -> p.gia() > 100);   // ❌ không làm gì cả!
```
Các thao tác như `filter`, `map` là **"lười"** — chỉ mô tả dây chuyền, chưa chạy. Phải có thao tác **kết thúc** (`collect`, `count`, `forEach`, `toList`) thì stream mới thực sự chạy.

### 3. Checked exception bên trong lambda

```java
list.forEach(f -> Files.readAllLines(f));   // ❌ Files.readAllLines ném IOException
```
Nhiều lambda **không cho** ném checked exception (như `IOException`) thẳng ra. Phải bọc `try/catch` **bên trong** lambda. Người mới hay bối rối chỗ này khi trộn file I/O với stream.

### 4. `NullPointerException` trong stream

Nếu một phần tử là `null`, `.map(p -> p.getTen())` sẽ NPE. Lọc null trước: `.filter(p -> p != null)` hoặc đảm bảo dữ liệu sạch.

### 5. Bắt `Exception` rồi bỏ trống (nuốt lỗi)

```java
try { ... } catch (Exception e) { }   // ❌ lỗi biến mất, debug khốn khổ
```
Ít nhất hãy `e.printStackTrace()` hoặc log lại. Nuốt lỗi âm thầm là "tội lỗi" khi làm automation — test xanh giả tạo.

### 6. Quên đóng tài nguyên (không dùng try-with-resources)

Mở file/browser mà quên đóng → rò rỉ tài nguyên, máy chậm dần, test flaky. Ưu tiên `try (...) { }` để tự đóng.

### 7. Nhầm enum với String

```java
if (browser == BrowserType.FIREFOX)   // ✅ đúng — enum so sánh bằng ==
if (browser.equals("FIREFOX"))        // ❌ sai kiểu — browser là enum, không phải String
```
Enum so sánh bằng `==` (an toàn), không phải `.equals("...")` với String.

### 8. So sánh sai loại (đọc lại Tuần 1)

Vẫn là bẫy `==` vs `.equals()` với String — nó theo bạn suốt. Khi lambda/stream xử lý chuỗi, nhớ `.equals()`.


---

## Bài Tập Thực Hành — Tuần 3

**Bài 3.1 (Dễ) — Lambda đầu tiên.**
Định nghĩa functional interface `LoiChao` với method `String chao(String ten)`. Trong `main`, tạo một lambda thực thi nó để trả về `"Xin chào, <ten>!"`. Gọi và in kết quả với `"Lan"`.

**Bài 3.2 (Dễ–TB) — Từ anonymous class sang lambda.**
Cho functional interface `KiemTra` với method `boolean test(int n)`. Viết **hai** cách kiểm tra "số dương": (a) bằng **anonymous class**, (b) bằng **lambda**. Gọi cả hai với `5` và `-3`, in kết quả. Mục tiêu: thấy tận mắt hai cách cho **cùng** kết quả.

**Bài 3.3 (TB) — Predicate lọc tuổi.**
Dùng `java.util.function.Predicate<Integer>`. Tạo predicate `laNguoiLon` kiểm tra `tuoi >= 18`. Cho `List<Integer> tuoi = List.of(15, 20, 17, 30, 18);`. Duyệt list, dùng `laNguoiLon.test(...)` để in ra những tuổi là người lớn.

**Bài 3.4 (TB) — Enum `BrowserType`.**
Tạo enum `BrowserType` gồm `CHROMIUM, FIREFOX, WEBKIT`. Viết method `static void khoiDong(BrowserType b)` dùng `switch` (kiểu `->`) in ra thông báo khởi động tương ứng. Gọi với cả 3 giá trị.

**Bài 3.5 (TB) — Stream lọc + biến đổi.**
Cho `List<String> emails = List.of("admin@test.com", "guest@demo.io", "bob@test.com", "sam@abc.org");`. Dùng **Stream** để: lọc các email chứa `"@test.com"`, chuyển sang CHỮ HOA, thu về một `List<String>` và in ra.

**Bài 3.6 (TB–Khó) — Exception & validate.**
Viết method `static void datSoLuong(int sl)` ném `IllegalArgumentException` với thông báo rõ ràng nếu `sl < 1`, ngược lại in `"Số lượng hợp lệ: <sl>"`. Trong `main`, gọi `datSoLuong(3)` và `datSoLuong(-2)`, dùng `try/catch` để bắt lỗi và in thông báo, chương trình **không được crash**.

**Bài 3.7 (Khó) — Đọc file dữ liệu test.**
Tạo file `users.txt` (ngang hàng `src`) với nội dung:
```
admin,123456
guest,guest123
test01,pass01
```
Đọc file bằng `Files.readAllLines(...)`, tách mỗi dòng theo `,`, và với mỗi dòng in ra: `Đăng nhập thử với user=<username>, pass=<password>`. Xử lý `IOException` bằng `try/catch`.

**Bài 3.8 (Khó — tổng hợp) — Stream + record + lambda.**
Cho:
```java
record SanPham(String ten, double gia, boolean conHang) {}
List<SanPham> ds = List.of(
    new SanPham("Áo thun", 150, true),
    new SanPham("Quần jean", 300, false),
    new SanPham("Giày", 500, true),
    new SanPham("Mũ", 80, true)
);
```
Dùng Stream để: (a) lọc sản phẩm **còn hàng** và **giá > 100**, (b) lấy **tên** chúng, (c) thu về `List<String>` và in ra. Sau đó, dùng stream tính **tổng giá trị** của các sản phẩm còn hàng (gợi ý: `.filter(...).mapToDouble(SanPham::gia).sum()`).

---

## ✅ Checklist Tự Kiểm Tra — Tuần 3

- [ ] Giải thích được **lambda là gì** (một hành động đóng gói để chạy sau) bằng lời của mình.
- [ ] Biết **functional interface** là interface có **đúng 1 method**.
- [ ] Viết được cả 3 dạng lambda: `() -> ...`, `x -> ...`, `(a,b) -> ...`.
- [ ] Chuyển được một **anonymous class** thành **lambda** tương đương.
- [ ] **Đọc hiểu** `page.onDialog(dialog -> dialog.accept())` và `page.waitForResponse(url, () -> page.click(...))` — nói được mỗi phần nghĩa là gì.
- [ ] Hiểu generics `List<T>`, `Map<K,V>` và không "sợ" khi thấy `ThreadLocal<Page>`.
- [ ] Tạo và dùng được **enum** (kèm switch).
- [ ] Viết được `try/catch/finally` và hiểu `finally` luôn chạy.
- [ ] Hiểu và dùng được **try-with-resources** (biết vì sao test Playwright viết `try (Playwright... )`).
- [ ] Đọc được file bằng `Files.readAllLines` và tách dòng bằng `.split(",")`.
- [ ] Viết được stream `filter → map → collect` và biết phải có thao tác kết thúc.
- [ ] Hiểu **annotation** là "nhãn báo hiệu" cho framework (`@Test`, `@Override`).
- [ ] **Đặt được breakpoint, chạy Debug, Step Over/Into, xem Variables, dùng Evaluate Expression.**

---

## 📖 Đáp Án — Tuần 3

**Đáp án 3.1 — Lambda đầu tiên.**
```java
public class Bai3_1 {
    @FunctionalInterface
    interface LoiChao {
        String chao(String ten);
    }

    public static void main(String[] args) {
        LoiChao loiChao = ten -> "Xin chào, " + ten + "!";
        System.out.println(loiChao.chao("Lan"));  // Xin chào, Lan!
    }
}
```

**Đáp án 3.2 — Anonymous class vs lambda.**
```java
public class Bai3_2 {
    @FunctionalInterface
    interface KiemTra {
        boolean test(int n);
    }

    public static void main(String[] args) {
        // (a) Anonymous class — cách cũ, dài
        KiemTra duongAnon = new KiemTra() {
            @Override
            public boolean test(int n) {
                return n > 0;
            }
        };

        // (b) Lambda — cách mới, ngắn, GIỐNG HỆT về kết quả
        KiemTra duongLambda = n -> n > 0;

        System.out.println(duongAnon.test(5));    // true
        System.out.println(duongAnon.test(-3));   // false
        System.out.println(duongLambda.test(5));  // true
        System.out.println(duongLambda.test(-3)); // false
    }
}
```
> Nhìn hai biến `duongAnon` và `duongLambda`: cùng làm một việc, nhưng lambda gọn hơn hẳn. Java "điền" giúp phần `new KiemTra()`, `@Override`, `public boolean test(int n)` vì `KiemTra` chỉ có 1 method.

**Đáp án 3.3 — Predicate lọc tuổi.**
```java
import java.util.List;
import java.util.function.Predicate;

public class Bai3_3 {
    public static void main(String[] args) {
        Predicate<Integer> laNguoiLon = tuoi -> tuoi >= 18;
        List<Integer> tuoi = List.of(15, 20, 17, 30, 18);

        for (int t : tuoi) {
            if (laNguoiLon.test(t)) {
                System.out.println(t + " là người lớn");  // 20, 30, 18
            }
        }
    }
}
```

**Đáp án 3.4 — Enum `BrowserType`.**
```java
public class Bai3_4 {
    enum BrowserType { CHROMIUM, FIREFOX, WEBKIT }

    static void khoiDong(BrowserType b) {
        switch (b) {
            case CHROMIUM -> System.out.println("Khởi động Chromium...");
            case FIREFOX  -> System.out.println("Khởi động Firefox...");
            case WEBKIT   -> System.out.println("Khởi động WebKit...");
        }
    }

    public static void main(String[] args) {
        khoiDong(BrowserType.CHROMIUM);
        khoiDong(BrowserType.FIREFOX);
        khoiDong(BrowserType.WEBKIT);
    }
}
```

**Đáp án 3.5 — Stream lọc + biến đổi.**
```java
import java.util.List;
import java.util.stream.Collectors;

public class Bai3_5 {
    public static void main(String[] args) {
        List<String> emails = List.of(
            "admin@test.com", "guest@demo.io", "bob@test.com", "sam@abc.org");

        List<String> ketQua = emails.stream()
            .filter(e -> e.contains("@test.com"))   // lọc
            .map(String::toUpperCase)               // biến đổi (method reference)
            .collect(Collectors.toList());          // thu thập

        System.out.println(ketQua);  // [ADMIN@TEST.COM, BOB@TEST.COM]
    }
}
```
> `String::toUpperCase` là method reference — viết tắt của `e -> e.toUpperCase()`. Cả hai đều đúng.

**Đáp án 3.6 — Exception & validate.**
```java
public class Bai3_6 {
    static void datSoLuong(int sl) {
        if (sl < 1) {
            throw new IllegalArgumentException("Số lượng phải >= 1, nhận được: " + sl);
        }
        System.out.println("Số lượng hợp lệ: " + sl);
    }

    public static void main(String[] args) {
        try {
            datSoLuong(3);    // in "Số lượng hợp lệ: 3"
            datSoLuong(-2);   // ném lỗi
        } catch (IllegalArgumentException e) {
            System.out.println("Bắt lỗi: " + e.getMessage());
        }
        System.out.println("Chương trình vẫn chạy tiếp bình thường.");
    }
}
```
> Vì `datSoLuong(-2)` ném lỗi, nên `datSoLuong(3)` chạy trước rồi tới `-2` mới nhảy vào catch. Chương trình không crash nhờ `try/catch`.

**Đáp án 3.7 — Đọc file dữ liệu test.**
```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class Bai3_7 {
    public static void main(String[] args) {
        try {
            List<String> dong = Files.readAllLines(Path.of("users.txt"));
            for (String d : dong) {
                String[] phan = d.split(",");
                String username = phan[0];
                String password = phan[1];
                System.out.println("Đăng nhập thử với user=" + username
                        + ", pass=" + password);
            }
        } catch (IOException e) {
            System.out.println("Không đọc được file: " + e.getMessage());
        }
    }
}
```
> Nếu gặp `NoSuchFileException`: kiểm tra `users.txt` có nằm ở **thư mục gốc project** (ngang hàng thư mục `src`) không. Đây là bẫy vị trí file rất hay gặp.

**Đáp án 3.8 — Stream + record + lambda (tổng hợp).**
```java
import java.util.List;
import java.util.stream.Collectors;

public class Bai3_8 {
    record SanPham(String ten, double gia, boolean conHang) {}

    public static void main(String[] args) {
        List<SanPham> ds = List.of(
            new SanPham("Áo thun", 150, true),
            new SanPham("Quần jean", 300, false),
            new SanPham("Giày", 500, true),
            new SanPham("Mũ", 80, true)
        );

        // (a)(b)(c): còn hàng & giá > 100 → lấy tên → List
        List<String> ketQua = ds.stream()
            .filter(sp -> sp.conHang() && sp.gia() > 100)
            .map(SanPham::ten)
            .collect(Collectors.toList());
        System.out.println(ketQua);   // [Áo thun, Giày]

        // Tổng giá trị các sản phẩm còn hàng
        double tong = ds.stream()
            .filter(SanPham::conHang)
            .mapToDouble(SanPham::gia)
            .sum();
        System.out.println("Tổng giá trị hàng còn: " + tong);  // 730.0
    }
}
```
> `mapToDouble(SanPham::gia)` biến stream các sản phẩm thành stream số `double` (các giá), rồi `.sum()` cộng lại. "Quần jean" (hết hàng) bị loại nên tổng = 150 + 500 + 80 = 730.


---

# 🎯 BÀI KIỂM TRA TỔNG — Cuối Giai Đoạn 1

> Làm bài này **sau khi hoàn thành cả 3 tuần**. Tự chấm bằng phần Đáp án ở cuối. Mục tiêu: **≥ 80%** quiz đúng và làm được **cả 2 bài code**. Nếu chưa đạt, quay lại tuần tương ứng ôn thêm — đừng vội sang Giai đoạn 2.

## Phần A — Trắc Nghiệm (20 câu)

**Câu 1.** Kết quả của `10 / 4` (hai số `int`) trong Java là?
A. `2.5`  B. `2`  C. `2.0`  D. Lỗi

**Câu 2.** Để so sánh **nội dung** hai chuỗi `String a` và `String b`, ta dùng?
A. `a == b`  B. `a = b`  C. `a.equals(b)`  D. `a.compare(b)`

**Câu 3.** Index của phần tử **đầu tiên** trong một mảng/List là?
A. `1`  B. `0`  C. `-1`  D. Tùy kiểu

**Câu 4.** Câu lệnh nào **thêm** phần tử vào cuối một `List<String> ds`?
A. `ds.add("x")`  B. `ds.put("x")`  C. `ds[0] = "x"`  D. `ds.append("x")`

**Câu 5.** Với `Map<String,Integer> m`, cách lấy giá trị theo key `"admin"` là?
A. `m.find("admin")`  B. `m.get("admin")`  C. `m["admin"]`  D. `m.value("admin")`

**Câu 6.** Method khai báo `public static void inTen(String t)` có kiểu trả về là?
A. `String`  B. `void` (không trả về gì)  C. `t`  D. `static`

**Câu 7.** Từ khóa nào dùng để **tạo một object** từ class?
A. `create`  B. `object`  C. `new`  D. `make`

**Câu 8.** Trong constructor, `this.username = username;` có ý nghĩa?
A. Gán tham số cho chính nó  B. Gán **field** của object bằng **tham số** cùng tên
C. So sánh field và tham số  D. Lỗi cú pháp

**Câu 9.** `LoginPage extends BasePage` nghĩa là?
A. `LoginPage` chứa `BasePage`  B. `LoginPage` **kế thừa** field/method của `BasePage`
C. Hai class không liên quan  D. `BasePage` kế thừa `LoginPage`

**Câu 10.** Một biến/method `static` thuộc về?
A. Từng object riêng  B. **Class** (dùng chung, không cần object)
C. Chỉ dùng trong constructor  D. Chỉ dùng trong `main`

**Câu 11.** Một **functional interface** có bao nhiêu method chưa cài đặt (abstract)?
A. 0  B. **Đúng 1**  C. 2  D. Không giới hạn

**Câu 12.** Lambda `dialog -> dialog.accept()` thuộc dạng nào?
A. Không tham số  B. **Một tham số**  C. Hai tham số  D. Không phải lambda

**Câu 13.** Trong `page.waitForResponse("**/api/x", () -> page.click("#go"))`, phần `() -> page.click("#go")` là gì?
A. Một chuỗi  B. **Một lambda (hành động) Playwright sẽ chạy để kích hoạt request**
C. Tên biến  D. Một vòng lặp

**Câu 14.** Cú pháp `List<String>` — phần `<String>` gọi là?
A. Mảng  B. **Generics** (chỉ định kiểu phần tử)  C. Annotation  D. Lambda

**Câu 15.** Enum `BrowserType { CHROMIUM, FIREFOX, WEBKIT }` — so sánh `b == BrowserType.FIREFOX` là?
A. Sai, phải dùng `.equals("FIREFOX")`  B. **Đúng, enum so sánh bằng `==`**
C. Luôn trả về false  D. Lỗi cú pháp

**Câu 16.** Khối `finally` trong try/catch?
A. Chỉ chạy khi có lỗi  B. Chỉ chạy khi không lỗi  C. **Luôn chạy dù có lỗi hay không**  D. Không bao giờ chạy

**Câu 17.** `try (Playwright playwright = Playwright.create()) { ... }` có tác dụng đặc biệt gì?
A. Chạy nhanh hơn  B. **Tự động đóng `playwright` khi hết khối try**  C. Bỏ qua lỗi  D. Lặp lại code

**Câu 18.** Trong Stream, chuỗi `.filter(...).map(...)` **chưa chạy** cho tới khi?
A. Ngay lập tức  B. **Có thao tác kết thúc như `.collect()` / `.count()` / `.forEach()`**
C. Gọi `.start()`  D. Không bao giờ chạy

**Câu 19.** `@Override` đặt trên một method để?
A. Xóa method  B. **Báo rằng method này ghi đè method của class cha (Java kiểm tra giúp)**
C. Làm method chạy nhanh hơn  D. Ẩn method

**Câu 20.** Khi debug ở IntelliJ, công cụ nào cho phép **tính thử một biểu thức** với giá trị biến hiện tại?
A. Step Over  B. Resume  C. **Evaluate Expression**  D. Breakpoint

---

## Phần B — Bài Code Tổng Hợp

### Bài Code 1 — Quản lý danh sách User (OOP + Collection + method)

**Yêu cầu:**
1. Tạo class `User` (đóng gói): field `private` `username` (String), `tuoi` (int), `role` (String — vd `"admin"`/`"user"`). Có constructor đủ 3 field, getter cho cả 3, và method `String moTa()` trả về chuỗi `"<username> (<role>, <tuoi> tuổi)"`.
2. Trong `main`, tạo `List<User>` gồm ít nhất 4 user (vài admin, vài user, tuổi khác nhau).
3. Viết method `static void inTatCa(List<User> ds)` in mô tả từng user.
4. Viết method `static int demTheoRole(List<User> ds, String role)` đếm số user có role cho trước (dùng `.equals()`!).
5. In ra danh sách và số lượng admin.

### Bài Code 2 — Xử lý dữ liệu test bằng Lambda + Stream + Enum + Exception

**Yêu cầu:**
1. Tạo enum `KetQua { PASS, FAIL, SKIP }`.
2. Tạo `record TestResult(String tenTest, KetQua ketQua, double thoiGian)` (thời gian chạy tính bằng giây).
3. Trong `main`, tạo `List<TestResult>` gồm ít nhất 5 test với kết quả và thời gian khác nhau.
4. Dùng **Stream** để:
   - (a) Lấy **tên** các test **FAIL** (in ra `List<String>`).
   - (b) Đếm số test **PASS**.
   - (c) Tính **tổng thời gian** chạy của tất cả test.
5. Viết method `static double thoiGianTrungBinh(List<TestResult> ds)` — nếu list rỗng thì **ném** `IllegalStateException("Danh sách rỗng")`; ngược lại trả về thời gian trung bình. Gọi trong `try/catch`.
6. (Thử thách nhỏ) Dùng một **lambda** `Predicate<TestResult>` tên `laTestCham` (thời gian > 2 giây) để lọc và in ra các test chậm.

---

## 📖 Đáp Án — Bài Kiểm Tra Tổng

### Phần A — Trắc nghiệm

| Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|
| 1 | **B** (`2` — chia nguyên) | 11 | **B** (đúng 1) |
| 2 | **C** (`.equals`) | 12 | **B** (một tham số) |
| 3 | **B** (`0`) | 13 | **B** (lambda hành động) |
| 4 | **A** (`add`) | 14 | **B** (generics) |
| 5 | **B** (`get`) | 15 | **B** (`==` cho enum) |
| 6 | **B** (`void`) | 16 | **C** (luôn chạy) |
| 7 | **C** (`new`) | 17 | **B** (tự đóng) |
| 8 | **B** (field = tham số) | 18 | **B** (cần thao tác kết thúc) |
| 9 | **B** (kế thừa) | 19 | **B** (ghi đè) |
| 10 | **B** (class) | 20 | **C** (Evaluate Expression) |

**Cách tính điểm:** mỗi câu 1 điểm, tổng 20. Đạt yêu cầu: **≥ 16/20**. Câu nào sai, ghi lại số câu và quay về đúng mục lý thuyết ôn lại.

### Phần B — Bài Code 1 (lời giải tham khảo)

```java
// FILE: User.java
public class User {
    private String username;
    private int tuoi;
    private String role;

    public User(String username, int tuoi, String role) {
        this.username = username;
        this.tuoi = tuoi;
        this.role = role;
    }

    public String getUsername() { return username; }
    public int getTuoi() { return tuoi; }
    public String getRole() { return role; }

    public String moTa() {
        return username + " (" + role + ", " + tuoi + " tuổi)";
    }
}

// FILE: Main.java
import java.util.List;

public class Main {
    static void inTatCa(List<User> ds) {
        for (User u : ds) {
            System.out.println(u.moTa());
        }
    }

    static int demTheoRole(List<User> ds, String role) {
        int dem = 0;
        for (User u : ds) {
            if (u.getRole().equals(role)) {   // .equals() cho String!
                dem++;
            }
        }
        return dem;
    }

    public static void main(String[] args) {
        List<User> ds = List.of(
            new User("admin1", 30, "admin"),
            new User("bob", 25, "user"),
            new User("admin2", 40, "admin"),
            new User("sam", 22, "user")
        );

        inTatCa(ds);
        System.out.println("Số admin: " + demTheoRole(ds, "admin")); // 2
    }
}
```

### Phần B — Bài Code 2 (lời giải tham khảo)

```java
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class TestReport {

    enum KetQua { PASS, FAIL, SKIP }

    record TestResult(String tenTest, KetQua ketQua, double thoiGian) {}

    static double thoiGianTrungBinh(List<TestResult> ds) {
        if (ds.isEmpty()) {
            throw new IllegalStateException("Danh sách rỗng");
        }
        double tong = ds.stream().mapToDouble(TestResult::thoiGian).sum();
        return tong / ds.size();
    }

    public static void main(String[] args) {
        List<TestResult> ds = List.of(
            new TestResult("loginTest",    KetQua.PASS, 1.2),
            new TestResult("searchTest",   KetQua.FAIL, 3.5),
            new TestResult("cartTest",     KetQua.PASS, 2.8),
            new TestResult("checkoutTest", KetQua.FAIL, 0.9),
            new TestResult("logoutTest",   KetQua.SKIP, 0.0)
        );

        // (a) Tên các test FAIL
        List<String> testFail = ds.stream()
            .filter(t -> t.ketQua() == KetQua.FAIL)
            .map(TestResult::tenTest)
            .collect(Collectors.toList());
        System.out.println("Test FAIL: " + testFail); // [searchTest, checkoutTest]

        // (b) Số test PASS
        long soPass = ds.stream()
            .filter(t -> t.ketQua() == KetQua.PASS)
            .count();
        System.out.println("Số test PASS: " + soPass); // 2

        // (c) Tổng thời gian
        double tongTG = ds.stream().mapToDouble(TestResult::thoiGian).sum();
        System.out.println("Tổng thời gian: " + tongTG + " giây"); // 8.4 giây

        // (5) Thời gian trung bình + xử lý exception
        try {
            System.out.printf("Trung bình: %.2f giây%n", thoiGianTrungBinh(ds));
        } catch (IllegalStateException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }

        // (6) Lambda Predicate: test chậm (> 2 giây)
        Predicate<TestResult> laTestCham = t -> t.thoiGian() > 2;
        System.out.println("--- Test chậm (>2s): ---");
        ds.stream()
          .filter(laTestCham)
          .forEach(t -> System.out.println(t.tenTest() + " - " + t.thoiGian() + "s"));
        // searchTest - 3.5s ; cartTest - 2.8s
    }
}
```

> **Tự chấm Bài Code:** code **biên dịch được**, **chạy ra đúng kết quả kỳ vọng** (đã ghi trong comment), dùng đúng công cụ (`.equals()` cho String, `==` cho enum, stream có thao tác kết thúc, exception được bắt). Nếu code bạn khác về cách viết nhưng ra đúng kết quả → vẫn tốt. Lập trình có nhiều đường tới đích.

---

# 🏁 CHECKLIST MILESTONE — Hoàn Thành Giai Đoạn 1

Đây là các năng lực **bắt buộc** trước khi sang Giai đoạn 2 (Maven, Git, JUnit/TestNG). Tự đánh giá trung thực:

**Nền tảng cú pháp (Tuần 1):**
- [ ] Khai báo & dùng thành thạo `int`, `double`, `boolean`, `String`.
- [ ] Viết được `if/else`, `switch`, cả 3 loại vòng lặp.
- [ ] Dùng được `List` và `Map` (thêm, lấy, duyệt).
- [ ] Tự viết được method có tham số và giá trị trả về.
- [ ] **Không còn nhầm** `==` với `.equals()` khi so sánh String.

**OOP (Tuần 2):**
- [ ] Tạo được class có field, constructor, getter/setter (đóng gói).
- [ ] Viết được **class có kế thừa** (`LoginPage extends BasePage`) — *(milestone chính thức của giáo trình)*.
- [ ] Hiểu và dùng được `@Override`, `super`, `static`.
- [ ] Đọc hiểu interface & abstract class khi gặp trong code.

**Java thực dụng (Tuần 3):**
- [ ] **Hiểu và viết được lambda** (`() ->`, `x ->`, `(a,b) ->`) — *(milestone chính thức)*.
- [ ] **Đọc hiểu cách Playwright dùng lambda** (`onDialog`, `waitForResponse`).
- [ ] Dùng được enum, generics cơ bản, try/catch, try-with-resources.
- [ ] Viết được stream `filter/map/collect`.
- [ ] **Đặt breakpoint và debug một chương trình bằng IntelliJ** — *(milestone chính thức)*.
- [ ] **Đọc hiểu được stack trace** (dòng lỗi, loại exception, dòng nào gây lỗi).

**Kiểm tra tổng:**
- [ ] Đạt **≥ 16/20** quiz.
- [ ] Làm được **cả 2 bài code tổng hợp**, chạy ra đúng kết quả.

> ✅ Khi tick đủ các ô **milestone chính thức** (in đậm), bạn đã đạt chuẩn Giai đoạn 1 của giáo trình: *"Viết được class có kế thừa; hiểu và viết được lambda; đặt breakpoint debug một chương trình; đọc hiểu stack trace."* Chúc mừng — bạn đã sẵn sàng cho Giai đoạn 2! 🎉

### Đọc hiểu Stack Trace (kỹ năng "tốt nghiệp" Giai đoạn 1)

Khi code lỗi lúc chạy, IntelliJ in ra một **stack trace** (đỏ) ở khung Run. Ví dụ:

```
Exception in thread "main" java.lang.NullPointerException: Cannot invoke "String.length()" because "ten" is null
    at Main.xuLy(Main.java:12)
    at Main.main(Main.java:6)
```

Cách đọc:
- **Dòng đầu:** loại lỗi (`NullPointerException`) + **lý do** (`"ten" is null`). Đọc dòng này trước tiên — nó nói gần hết vấn đề.
- **Các dòng `at ...`:** "đường đi" của lỗi, từ chỗ nổ ngược về `main`. Đọc **từ trên xuống**, tìm dòng có **file của bạn** (`Main.java:12`) → lỗi ở **dòng 12**.
- Nhấp thẳng vào `Main.java:12` (màu xanh) → IntelliJ nhảy tới đúng dòng. Đặt breakpoint ở đó và debug.

👉 Đừng hoảng khi thấy "màn hình đỏ". Stack trace là **bạn** — nó chỉ đường tới bug. Kỹ năng đọc nó sẽ theo bạn suốt sự nghiệp automation.

---

# 📚 Tài Nguyên Tham Khảo

**Học Java cơ bản (miễn phí):**
- W3Schools Java — tra cú pháp nhanh, có "Try it yourself": https://www.w3schools.com/java/
- Oracle Java Tutorials (chính thống): https://docs.oracle.com/javase/tutorial/
- Jenkov Java Tutorial (giải thích sâu, dễ hiểu): https://jenkov.com/tutorials/java/index.html
- Baeldung (bài viết chất lượng theo chủ đề, rất hợp khi tra một khái niệm): https://www.baeldung.com/

**Video (YouTube):**
- freeCodeCamp — "Java Full Course" (dài, bài bản cho người mới): https://www.youtube.com/c/Freecodecamp
- Programming with Mosh — "Java Tutorial for Beginners"

**Chuyên sâu Lambda / Stream / Functional Interface:**
- Baeldung — Java 8 Lambda Expressions: https://www.baeldung.com/java-8-lambda-expressions-tips
- Baeldung — The Java 8 Stream API Tutorial: https://www.baeldung.com/java-8-streams
- Oracle — Lambda Expressions: https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html

**Debug bằng IntelliJ:**
- JetBrains — Debug your first Java application: https://www.jetbrains.com/help/idea/debugging-your-first-java-application.html
- JetBrains — Evaluate expressions: https://www.jetbrains.com/help/idea/examining-suspended-program.html

**Liên hệ Playwright (đọc lướt để thấy đích đến — sẽ học kỹ ở Giai đoạn 3):**
- Playwright Java — Intro: https://playwright.dev/java/docs/intro
- Playwright Java — API Reference: https://playwright.dev/java/docs/api/class-playwright

**Sách:**
- *Head First Java* (Kathy Sierra & Bert Bates) — cực kỳ hợp cho người mới, dạy OOP trực quan.

**Luyện tập thêm:**
- Exercism — Java Track (bài tập có mentor review, miễn phí): https://exercism.org/tracks/java
- CodingBat — Java (bài tập nhỏ về logic, method): https://codingbat.com/java

---

> 💪 **Lời nhắn cuối:** Bạn vừa đi qua phần **khó nhất về mặt khái niệm** của cả lộ trình. Từ đây, mọi thứ sẽ "thực tế" và trực quan hơn (dùng công cụ, viết test thật). Nếu có chỗ chưa chắc — **bình thường thôi**, quay lại gõ code thêm vài lần là ngấm. Nhớ nguyên tắc vàng: **code mỗi ngày, dù chỉ 30 phút, hơn hẳn đọc lý thuyết cả buổi.** Hẹn gặp ở Giai đoạn 2! 🚀
