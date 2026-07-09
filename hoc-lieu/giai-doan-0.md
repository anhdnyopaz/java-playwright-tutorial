# 🧭 Giai đoạn 0 — Mindset, Môi trường & Nền tảng Web

> **Học liệu chính thức — Khóa Automation Test với Java + Playwright**
> **Đối tượng:** Tester (manual) chưa biết code, mới bắt đầu học automation.
> **Hệ điều hành thực hành:** macOS.
> **Thời lượng gợi ý:** ~1 tuần (nhưng hãy đi chậm cho chắc — phần nền tảng này quyết định 80% việc bạn có viết được locator tốt sau này hay không).

---

## 📖 Mục lục

1. [Giai đoạn 0 dạy gì và tại sao quan trọng](#0)
2. [Phần 1 — Mindset Automation (Bài đọc)](#1)
3. [Phần 2 — Cài đặt môi trường](#2)
   - [Phần 2A — macOS](#2)
   - [Phần 2W — Windows](#2w)
4. [Phần 3 — HTML nền tảng cho Automation](#3)
5. [Phần 4 — CSS Selector](#4)
6. [Phần 5 — DOM là gì](#5)
7. [Phần 6 — Chrome DevTools (F12)](#6)
8. [Phần 7 — Bài thực hành có hướng dẫn: SauceDemo](#7)
9. [Phần 8 — Bài tập tự làm](#8)
10. [Phần 9 — Quiz tự đánh giá](#9)
11. [Phần 10 — Đáp án bài tập](#10)
12. [Phần 11 — Đáp án quiz](#11)
13. [Phần 12 — Checklist Milestone Giai đoạn 0](#12)
14. [Phần 13 — Tài nguyên tham khảo](#13)

---

<a id="0"></a>
## 🎯 Giai đoạn 0 dạy gì và tại sao quan trọng

Bạn sắp học viết code để máy tính **tự click, tự nhập liệu, tự kiểm tra** thay bạn. Nhưng trước khi máy làm được điều đó, **bạn** phải chỉ cho nó: "Hãy click vào **cái nút này**, gõ vào **ô này**". Vấn đề là máy không nhìn màn hình bằng mắt như bạn — nó nhìn trang web qua **cấu trúc code bên trong** (HTML/DOM). Vì vậy:

> **Muốn ra lệnh cho máy thao tác trên trang web, bạn phải biết đọc "bản đồ bên trong" của trang web đó.**

Giai đoạn 0 chính là học đọc bản đồ đó, cộng với chuẩn bị "xưởng làm việc" (môi trường) và "tư duy nghề" (mindset). Cụ thể bạn sẽ:

| Mục tiêu | Bạn sẽ làm được |
|----------|-----------------|
| **Mindset** | Hiểu automation để làm gì, khi nào nên/không nên dùng, bỏ được kỳ vọng sai |
| **Môi trường** | Cài JDK, IntelliJ, Git, Maven trên macOS và kiểm tra chạy đúng |
| **HTML** | Đọc hiểu thẻ và thuộc tính của một element bất kỳ |
| **CSS Selector** | Tự viết được "địa chỉ" trỏ tới một element |
| **DOM** | Hiểu trang web là một cái cây, và Playwright thao tác trên cái cây đó |
| **DevTools (F12)** | Inspect element, test selector trong Console, xem Network |

Đây **chưa phải** lúc viết test Java. Đây là lúc xây móng. Móng chắc thì nhà cao mới không sập.

---

<a id="1"></a>
## 🧠 Phần 1 — Mindset Automation (Bài đọc)

### 1.1. Tại sao một tester giỏi nên học automation?

Hãy tưởng tượng một ngày làm việc của bạn với vai trò manual tester. Team vừa ra bản build mới. Bạn mở checklist regression 120 test case — login, tìm kiếm, thêm giỏ hàng, thanh toán, đổi mật khẩu, phân trang... Bạn click, nhập, so sánh kết quả, ghi lại. Mất 2 ngày. Xong xuôi thì dev báo: "Anh vừa fix thêm một bug, em test lại từ đầu giúp nhé." Và bạn lại click từ đầu.

Việc đó **cần thiết** — nhưng nó lặp đi lặp lại, nhàm chán, và **con người rất dễ sai khi làm việc lặp lại**. Đến case thứ 90 bạn mệt, mắt lướt qua, bỏ sót một lỗi nhỏ. Đó không phải lỗi của bạn — đó là giới hạn tự nhiên của con người.

Bây giờ tưởng tượng khác đi: bạn viết một lần bộ script, gõ một lệnh, đi pha cà phê. 8 phút sau quay lại, 120 case đã chạy xong, có báo cáo màu xanh/đỏ rõ ràng, kèm ảnh chụp màn hình chỗ lỗi. Bạn dùng thời gian được giải phóng để làm việc mà **máy không làm được**: khám phá (exploratory testing), test trải nghiệm người dùng, nghĩ ra các kịch bản mới lắt léo.

> **Automation không lấy mất việc của bạn. Nó lấy đi phần việc tẻ nhạt nhất, để trả lại cho bạn phần việc thú vị và có giá trị nhất.**

Và về mặt sự nghiệp: automation tester ở Việt Nam hiện có mức lương và cơ hội cao hơn đáng kể so với thuần manual, vì bạn vừa hiểu **nghiệp vụ kiểm thử** vừa biết **lập trình** — một kết hợp mà thị trường luôn thiếu.

### 1.2. Automation vs Manual — không phải cuộc chiến, mà là phân công

Nhiều người mới hiểu lầm rằng "học automation là để thay thế manual". Sai. Hai bên **bổ sung** cho nhau:

| Tiêu chí | Manual Test | Automation Test |
|----------|-------------|-----------------|
| **Mạnh ở** | Khám phá, đánh giá UX/cảm giác, case mới, ad-hoc | Lặp lại, regression, chạy nhiều lần, khối lượng lớn |
| **Yếu ở** | Chậm khi lặp lại, dễ mệt/sai, tốn người | Không "cảm nhận" được đẹp/xấu, khó test case chưa ổn định |
| **Tốc độ** | Chậm | Rất nhanh |
| **Chi phí ban đầu** | Thấp (test luôn) | Cao (phải viết code trước) |
| **Chi phí về sau** | Cao (lặp lại tốn người) | Thấp (chạy lại gần như miễn phí) |
| **Phù hợp nhất** | Test lần đầu, tính năng đang thay đổi liên tục | Test đã ổn định, chạy đi chạy lại nhiều lần |

**Một ví von:** Manual test giống nếm thử món ăn — cần lưỡi người, cảm nhận, phán đoán. Automation test giống dây chuyền kiểm tra chai nước trong nhà máy — chai nào thiếu nắp thì loại, làm hàng nghìn chai một giờ không mệt. Bạn cần **cả hai** trong một nhà bếp chuyên nghiệp.

### 1.3. Không phải test case nào cũng nên automate

Đây là tư duy **quan trọng nhất** của người làm automation chuyên nghiệp. Người mới thường mắc bệnh "automate tất cả mọi thứ" và lãnh hậu quả: tốn hàng tuần viết script cho những case chẳng bao giờ chạy lại, hoặc script gãy liên tục vì tính năng còn đang thay đổi.

**Tiêu chí ƯU TIÊN automate một case** (càng nhiều dấu ✅ càng nên automate):

- ✅ **Chạy lặp lại nhiều lần** (regression, smoke test mỗi lần build).
- ✅ **Ổn định** — tính năng đã "chốt", ít thay đổi giao diện/logic.
- ✅ **Quan trọng / rủi ro cao** — luồng nghiệp vụ cốt lõi (login, thanh toán, đặt hàng).
- ✅ **Tốn công làm tay** — nhiều bước, nhiều dữ liệu (data-driven: 50 bộ dữ liệu login).
- ✅ **Kết quả rõ ràng, kiểm tra được bằng logic** (đúng/sai xác định, không mơ hồ).
- ✅ **Khó test tay** — ví dụ cần chạy trên 3 trình duyệt, hoặc cần lặp 100 lần.

**Tiêu chí NÊN CÂN NHẮC / KHÔNG nên automate (ít nhất là chưa):**

- ❌ **Case chỉ chạy một lần** (test một tính năng nhỏ sắp bị gỡ bỏ).
- ❌ **Tính năng đang thay đổi liên tục** — viết xong sáng, chiều gãy.
- ❌ **Cần đánh giá cảm quan** — "màu này có đẹp không?", "bố cục có dễ nhìn không?".
- ❌ **Case cực kỳ phức tạp về setup**, chi phí automate lớn hơn lợi ích thu về.
- ❌ **Captcha, OTP thật, xác thực sinh trắc học** — vốn được thiết kế để chặn máy.

> **Câu hỏi vàng để tự hỏi trước khi automate một case:** *"Case này sẽ được chạy lại bao nhiêu lần? Nó có ổn định không? Nếu tôi bỏ 3 giờ viết script, tôi có tiết kiệm được nhiều hơn 3 giờ trong tương lai không?"* Nếu câu trả lời là "chỉ chạy 1 lần" hoặc "tính năng còn đổi liên tục" → khoan automate.

### 1.4. Những kỳ vọng SAI cần bỏ ngay hôm nay

Người mới bước vào automation thường mang theo vài niềm tin sai lầm, khiến họ nản hoặc đi sai đường. Bỏ chúng đi:

1. **"Automation là click chuột nâng cao, không cần biết code."**
   ❌ Sai. **Automation LÀ lập trình.** Bạn sẽ viết code Java thật, dùng vòng lặp, hàm, class. Công cụ record-and-playback (ghi lại thao tác) chỉ giúp lúc đầu, nhưng script tạo ra thường mong manh, khó bảo trì. Muốn đi xa, bạn phải code.

2. **"Học automation là hết flaky test, test luôn xanh."**
   ❌ Sai. Test tự động vẫn có thể "chập chờn" (flaky) — lúc pass lúc fail dù code không đổi — do trang load chậm, do chờ sai cách, do dữ liệu chồng chéo. **Một phần lớn kỹ năng automation là học cách viết test ỔN ĐỊNH.** Đây là điều phân biệt junior với người đi làm được.

3. **"Viết test một lần là xong, không cần đụng lại."**
   ❌ Sai. Ứng dụng thay đổi thì test phải cập nhật theo. Test là **code sống**, cần bảo trì. Vì vậy ta học viết test **dễ bảo trì** (Page Object Model, đặt tên rõ ràng...) ngay từ đầu.

4. **"Cứ automate hết 100% là chuyên nghiệp."**
   ❌ Sai (đã nói ở 1.3). Automate đúng chỗ mới là chuyên nghiệp. 100% automation là ảo tưởng và lãng phí.

5. **"Tôi không biết code, chắc không học nổi."**
   ❌ Sai. Bạn đã có thứ quý nhất mà lập trình viên thuần thường thiếu: **tư duy kiểm thử** — biết đặt câu hỏi "cái gì có thể hỏng?". Code là kỹ năng học được. Hàng nghìn manual tester đã chuyển thành automation engineer giỏi. Bạn đi từng bước, mỗi ngày viết một chút, sẽ tới.

> **Nguyên tắc vàng của cả khóa:** Học automation = **code mỗi ngày**. Đọc 10 tutorial không bằng tự tay viết 1 dòng và làm nó chạy. Ngay ở Giai đoạn 0 này, hãy **thực sự mở terminal gõ lệnh, thực sự mở F12 test selector** — đừng chỉ đọc.

---

<a id="2"></a>
## 💻 Phần 2A — Cài đặt môi trường trên macOS

> 🍎 Phần này dành cho **macOS**. Nếu bạn dùng **Windows**, hãy nhảy tới **[Phần 2W — Cài đặt trên Windows](#2w)** rồi quay lại làm bài Hello World ở mục 2.8. Cả hai hệ đều cho kết quả cuối như nhau: JDK + IntelliJ + Git + Maven sẵn sàng.

Mục tiêu phần này: biến chiếc Mac của bạn thành một "xưởng làm việc automation" hoàn chỉnh. Sau khi xong, bạn sẽ có:

- **JDK 17+** — bộ công cụ để chạy code Java (Java Development Kit).
- **Homebrew** — "chợ ứng dụng dòng lệnh" của macOS, giúp cài phần mềm bằng 1 câu lệnh.
- **IntelliJ IDEA Community** — phần mềm để viết code Java (IDE).
- **Git** — công cụ quản lý phiên bản mã nguồn.
- **Maven** — công cụ quản lý thư viện và build project Java.

> 💡 **Terminal là gì?** Là ứng dụng cho phép bạn gõ lệnh ra cho máy tính thay vì click chuột. Trên macOS, mở bằng `Cmd + Space` → gõ `Terminal` → Enter. Đừng sợ nó — bạn chỉ cần copy-paste các lệnh dưới đây.

### 2.1. Cài Homebrew (nền tảng để cài mọi thứ khác)

Homebrew giống như "App Store cho terminal". Cài nó trước, mọi thứ sau sẽ dễ.

Mở Terminal và dán lệnh sau (đây là lệnh chính thức từ trang [brew.sh](https://brew.sh/)):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Nó sẽ hỏi mật khẩu máy Mac của bạn (gõ vào, **màn hình không hiện ký tự** — đó là bình thường, cứ gõ rồi Enter).

**Quan trọng với máy Mac chip Apple Silicon (M1/M2/M3/M4):** sau khi cài xong, Homebrew thường yêu cầu bạn chạy thêm 2 lệnh để "đăng ký" brew vào hệ thống. Màn hình cài đặt sẽ in ra chính xác 2 lệnh đó (mục *Next steps*). Thường là:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

> 📌 Trên Mac Intel (đời cũ), Homebrew nằm ở `/usr/local/bin` và thường không cần bước này.

**Kiểm tra Homebrew đã cài đúng:**

```bash
brew --version
```

Nếu thấy in ra ví dụ `Homebrew 4.x.x` là thành công. ✅

### 2.2. Cài JDK 17+ (Java Development Kit)

Có 2 cách. Chọn **một**.

**Cách A — Cài bằng Homebrew (khuyến nghị, nhanh gọn nhất):**

Ta dùng bản **Temurin** của Eclipse Adoptium — bản JDK miễn phí, phổ biến, chuẩn cho automation.

```bash
brew install --cask temurin@21
```

> 💡 Vì sao là 21? JDK 21 là bản LTS (hỗ trợ dài hạn) mới, rất hợp cho khóa học này. Giáo trình yêu cầu **17 trở lên**, nên 17 hoặc 21 đều được. Nếu muốn 17: `brew install --cask temurin@17`.

**Cách B — Tải file cài từ trang Adoptium:**

1. Vào [https://adoptium.net/temurin/releases/](https://adoptium.net/temurin/releases/)
2. Chọn: **Operating System = macOS**, **Architecture = aarch64** (nếu máy chip Apple M-series) hoặc **x64** (nếu Mac Intel), **Package Type = JDK**, **Version = 21 (hoặc 17)**.
3. Tải file `.pkg` về, mở lên, bấm Next → Next → Install như cài app bình thường.

> ❓ **Máy tôi là chip gì?** Bấm logo Apple  góc trái trên → *About This Mac*. Nếu thấy "Apple M1/M2/M3..." → chọn **aarch64**. Nếu thấy "Intel" → chọn **x64**.

**Kiểm tra JDK đã cài đúng — bước QUAN TRỌNG NHẤT của mục này:**

```bash
java -version
```

Kết quả mong đợi (con số có thể là 17.x hoặc 21.x):

```
openjdk version "21.0.x" 2024-xx-xx
OpenJDK Runtime Environment Temurin-21.0.x (build 21.0.x+...)
OpenJDK 64-Bit Server VM Temurin-21.0.x (build 21.0.x+..., mixed mode)
```

Nếu thấy số phiên bản **17 trở lên** là ✅ thành công.

Kiểm tra thêm trình biên dịch:

```bash
javac -version
```

Phải in ra ví dụ `javac 21.0.x` — nghĩa là bộ **biên dịch** (compiler) đã sẵn sàng.

> ⚠️ **Nếu `java -version` báo "command not found" hoặc ra số cũ (như 1.8):**
> - Đóng hẳn Terminal rồi mở lại (để nạp cấu hình mới).
> - Kiểm tra biến `JAVA_HOME`. Thêm dòng sau vào cuối file `~/.zshrc` (mở bằng `open -e ~/.zshrc`), lưu, rồi mở Terminal mới:
>   ```bash
>   export JAVA_HOME=$(/usr/libexec/java_home -v 21)
>   ```
>   (Đổi `21` thành `17` nếu bạn cài 17.)
> - `/usr/libexec/java_home -V` (chữ V hoa) liệt kê mọi bản JDK đang có trên máy.

### 2.3. Cài IntelliJ IDEA Community (IDE viết code)

**IDE (Integrated Development Environment)** là phần mềm giúp bạn viết code: tô màu cú pháp, gợi ý code, báo lỗi ngay khi gõ, chạy/debug bằng một nút bấm. IntelliJ IDEA Community Edition là bản **miễn phí** và tốt nhất cho Java.

**Cách A — bằng Homebrew:**

```bash
brew install --cask intellij-idea-ce
```

(`ce` = Community Edition, bản miễn phí. Đừng cài bản `intellij-idea` không có `-ce` vì đó là bản trả phí.)

**Cách B — tải thủ công:**

1. Vào [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/)
2. Kéo xuống mục **Community Edition** (KHÔNG phải Ultimate — đó là bản trả phí), tải file `.dmg`.
3. Chọn đúng bản chip: **Apple Silicon** hoặc **Intel**.
4. Mở file `.dmg`, kéo icon IntelliJ vào thư mục Applications.

**Kiểm tra:** Mở IntelliJ (`Cmd + Space` → gõ `IntelliJ`). Lần đầu mở nó sẽ hỏi vài cấu hình — cứ chọn mặc định (theme tùy thích). Vào được màn hình *Welcome to IntelliJ IDEA* là ✅.

### 2.4. Cài Git (quản lý mã nguồn)

Git giúp bạn lưu lịch sử code, quay lại phiên bản cũ, và làm việc nhóm. macOS đôi khi đã có sẵn Git (kèm Xcode Command Line Tools), nhưng ta cài bản mới cho chắc:

```bash
brew install git
```

**Kiểm tra:**

```bash
git --version
```

In ra ví dụ `git version 2.4x.x` là ✅.

**Cấu hình danh tính lần đầu** (Git cần biết ai đang commit — làm một lần cho cả máy):

```bash
git config --global user.name "Ten Cua Ban"
git config --global user.email "email_cua_ban@example.com"
```

Kiểm tra lại cấu hình:

```bash
git config --global --list
```

### 2.5. Cài Maven (quản lý thư viện & build)

**Maven** là công cụ tự động tải về các thư viện (như Playwright, JUnit) mà project của bạn cần, và build/chạy test. Nó đọc một file tên `pom.xml` để biết cần những gì.

> 💡 Thực tế IntelliJ có Maven đi kèm bên trong, nên bạn **có thể** chạy Maven qua IntelliJ mà không cần cài riêng. Nhưng ta vẫn cài Maven ở dòng lệnh để chạy được `mvn` trong terminal — sẽ cần khi làm CI/CD sau này.

```bash
brew install maven
```

**Kiểm tra — quan trọng:**

```bash
mvn -version
```

Kết quả mong đợi (in ra cả version Maven và version Java nó đang dùng):

```
Apache Maven 3.9.x (...)
Maven home: /opt/homebrew/Cellar/maven/3.9.x/libexec
Java version: 21.0.x, vendor: Eclipse Adoptium, runtime: ...
```

Chú ý dòng **Java version** — nó phải khớp với JDK bạn vừa cài (17 hoặc 21). Nếu khớp là ✅ hoàn hảo.

### 2.6. (Tùy chọn) Node.js — cho Playwright Codegen sau này

Chưa bắt buộc ở Giai đoạn 0, nhưng cài luôn cho tiện. Node.js giúp dùng công cụ `playwright codegen` (ghi thao tác thành code) rất tiện ở giai đoạn sau:

```bash
brew install node
node -v
npm -v
```

### 2.7. ✅ Bảng kiểm tra "đã cài đúng chưa"

Chạy lần lượt các lệnh sau trong **một Terminal mới** (mở lại để chắc chắn nạp cấu hình mới nhất). Đối chiếu kết quả:

| Lệnh | Kết quả kỳ vọng | Ý nghĩa |
|------|-----------------|---------|
| `brew --version` | `Homebrew 4.x.x` | Trình cài đặt hoạt động |
| `java -version` | `openjdk version "17..."` hoặc `"21..."` | JDK chạy được, đúng version |
| `javac -version` | `javac 17.x` / `javac 21.x` | Trình biên dịch sẵn sàng |
| `git --version` | `git version 2.4x.x` | Git sẵn sàng |
| `mvn -version` | `Apache Maven 3.9.x` + dòng `Java version` khớp JDK | Maven sẵn sàng, dùng đúng JDK |
| `node -v` (nếu cài) | `v2x.x.x` | Node sẵn sàng (tùy chọn) |
| Mở IntelliJ | Vào được màn hình Welcome | IDE sẵn sàng |

> 🎉 Nếu cả 5 lệnh bắt buộc đầu tiên đều cho kết quả đúng và IntelliJ mở được → **môi trường của bạn đã sẵn sàng.** Đây là một cột mốc thật sự, nhiều người mới vấp ngay ở đây. Bạn qua rồi!

---

<a id="2w"></a>
## 🪟 Phần 2W — Cài đặt môi trường trên Windows

> 🪟 Phần này dành cho bạn dùng **Windows 10 / 11**. Nếu bạn dùng macOS, hãy làm Phần 2A ở trên và bỏ qua phần này. Kết quả cuối của cả hai hệ là như nhau: JDK + IntelliJ + Git + Maven sẵn sàng.

Mục tiêu vẫn là biến máy Windows thành "xưởng automation": có **JDK 17+**, **IntelliJ IDEA Community**, **Git**, **Maven** (và Node.js tùy chọn).

> 💡 **Terminal trên Windows là gì?** Là **PowerShell** hoặc **Command Prompt (cmd)**. Khuyến nghị dùng **PowerShell**: bấm nút Start → gõ `PowerShell` → mở **Windows PowerShell**. Một vài lệnh cài đặt nên chạy ở chế độ quản trị: chuột phải vào PowerShell → **Run as administrator**.

### 2W.1. Chọn cách cài: winget (khuyến nghị) hay tải file thủ công

Windows 11 và Windows 10 (bản cập nhật mới) có sẵn **winget** — trình cài đặt dòng lệnh, đóng vai trò giống Homebrew của macOS. Kiểm tra:

```powershell
winget --version
```

- Nếu in ra ví dụ `v1.x.x` → dùng **Cách A (winget)** ở mỗi mục dưới, nhanh gọn nhất.
- Nếu báo lỗi "không nhận lệnh" → cài **App Installer** từ Microsoft Store (tìm "App Installer"), hoặc cứ dùng **Cách B (tải file thủ công)** — cũng hoàn toàn ổn.

> 💡 Ngoài winget còn có **Chocolatey** (`choco`) — một trình quản lý gói phổ biến khác. Không bắt buộc; nếu đã quen thì dùng cũng được.

### 2W.2. Cài JDK 17+ (Java Development Kit)

**Cách A — winget:**

```powershell
winget install EclipseAdoptium.Temurin.21.JDK
```

(Muốn bản 17: `winget install EclipseAdoptium.Temurin.17.JDK`. Giáo trình yêu cầu **17 trở lên**, nên 17 hoặc 21 đều được.)

**Cách B — tải file cài từ Adoptium:**

1. Vào [https://adoptium.net/temurin/releases/](https://adoptium.net/temurin/releases/)
2. Chọn: **Operating System = Windows**, **Architecture = x64**, **Package Type = JDK**, **Version = 21 (hoặc 17)**.
3. Tải file **`.msi`** về, mở lên, bấm Next.
4. ⭐ **QUAN TRỌNG:** ở bước tùy chọn (*Custom Setup*), tìm mục **"Set JAVA_HOME variable"** và **"Add to PATH"** → bấm vào biểu tượng ổ cứng nhỏ → chọn *"Will be installed on local hard drive"*. Bật 2 cái này giúp bạn **khỏi phải** chỉnh biến môi trường thủ công về sau.
5. Next → Install.

**Kiểm tra JDK — mở một cửa sổ PowerShell MỚI** (để nạp PATH mới) rồi gõ:

```powershell
java -version
javac -version
```

Thấy số phiên bản **17 trở lên** là ✅. `javac` in ra được nghĩa là bộ **biên dịch** đã sẵn sàng.

> ⚠️ **Nếu báo "java is not recognized" hoặc ra version cũ:** biến môi trường chưa được set. Sửa thủ công:
> 1. Bấm Start → gõ **"environment variables"** → mở **"Edit the system environment variables"** → nút **Environment Variables…**
> 2. Ở mục **System variables**, bấm **New**: tên `JAVA_HOME`, giá trị là thư mục JDK, ví dụ `C:\Program Files\Eclipse Adoptium\jdk-21.0.x-hotspot`.
> 3. Vẫn trong System variables, chọn biến **Path** → **Edit** → **New** → thêm `%JAVA_HOME%\bin`.
> 4. OK hết các cửa sổ, **đóng và mở lại PowerShell**, thử `java -version` lại.

### 2W.3. Cài IntelliJ IDEA Community (IDE viết code)

**IDE** là phần mềm giúp bạn viết code: tô màu cú pháp, gợi ý code, báo lỗi khi gõ, chạy/debug bằng một nút. IntelliJ IDEA Community Edition là bản **miễn phí** và tốt nhất cho Java.

**Cách A — winget:**

```powershell
winget install JetBrains.IntelliJIDEA.Community
```

**Cách B — tải thủ công:**

1. Vào [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/) , chọn tab **Windows**.
2. Kéo xuống mục **Community Edition** (KHÔNG phải Ultimate — bản trả phí), tải file `.exe`.
3. Chạy file `.exe`. Ở màn hình *Installation Options*, nên tick **"Create Desktop Shortcut (64-bit)"** và mục associate `.java` cho tiện. Next → Install.

**Kiểm tra:** Mở IntelliJ từ Start Menu. Vào được màn hình *Welcome to IntelliJ IDEA* là ✅.

### 2W.4. Cài Git (quản lý mã nguồn)

Git giúp bạn lưu lịch sử code, quay lại phiên bản cũ, và làm việc nhóm.

**Cách A — winget:**

```powershell
winget install Git.Git
```

**Cách B — tải thủ công:** vào [https://git-scm.com/download/win](https://git-scm.com/download/win) , tải bản 64-bit, chạy file cài. Bộ cài có nhiều tùy chọn nhưng cứ **Next** theo mặc định là an toàn cho người mới.

**Kiểm tra (mở PowerShell mới):**

```powershell
git --version
```

In ra ví dụ `git version 2.4x.x` là ✅.

**Cấu hình danh tính lần đầu** (làm một lần cho cả máy):

```powershell
git config --global user.name "Ten Cua Ban"
git config --global user.email "email_cua_ban@example.com"
git config --global --list
```

### 2W.5. Cài Maven (quản lý thư viện & build)

**Maven** tự động tải các thư viện (Playwright, JUnit…) mà project cần và build/chạy test, dựa trên file `pom.xml`.

> 💡 IntelliJ đã có Maven đi kèm bên trong, nên bạn **có thể tạm bỏ qua** mục này mà vẫn build/chạy test trong IntelliJ. Nhưng nên cài để chạy được lệnh `mvn` trong terminal — sẽ cần khi làm CI/CD sau này.

**Cách A — winget:**

```powershell
winget install Apache.Maven
```

**Cách B — cài thủ công (cách truyền thống, chắc ăn nhất):**

1. Vào [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi) , tải file **Binary zip archive** (ví dụ `apache-maven-3.9.x-bin.zip`).
2. Giải nén ra một thư mục cố định, ví dụ `C:\Program Files\Apache\maven` (bên trong có thư mục `bin`).
3. Thêm vào PATH: Start → "environment variables" → Environment Variables → chọn **Path** (System variables) → Edit → New → thêm đường dẫn tới thư mục `bin`, ví dụ `C:\Program Files\Apache\maven\bin`.
4. (Khuyến nghị) tạo biến `MAVEN_HOME` trỏ tới `C:\Program Files\Apache\maven`.

> 💡 Nếu bạn dùng Chocolatey: `choco install maven` sẽ tự lo phần PATH.

**Kiểm tra (mở PowerShell mới):**

```powershell
mvn -version
```

Chú ý dòng **Java version** in ra phải khớp JDK bạn đã cài (17 hoặc 21). Khớp là ✅ hoàn hảo.

### 2W.6. (Tùy chọn) Node.js — cho Playwright Codegen sau này

Chưa bắt buộc ở Giai đoạn 0, cài luôn cho tiện:

```powershell
winget install OpenJS.NodeJS.LTS
```

Hoặc tải bản **LTS** tại [https://nodejs.org/](https://nodejs.org/) . Kiểm tra:

```powershell
node -v
npm -v
```

### 2W.7. ✅ Bảng kiểm tra "đã cài đúng chưa" (Windows)

Mở một **PowerShell mới** (để nạp cấu hình mới nhất) rồi chạy lần lượt, đối chiếu kết quả:

| Lệnh | Kết quả kỳ vọng | Ý nghĩa |
|------|-----------------|---------|
| `winget --version` | `v1.x.x` | Trình cài đặt (nếu dùng) hoạt động |
| `java -version` | `openjdk version "17..."` hoặc `"21..."` | JDK chạy được, đúng version |
| `javac -version` | `javac 17.x` / `javac 21.x` | Trình biên dịch sẵn sàng |
| `git --version` | `git version 2.4x.x` | Git sẵn sàng |
| `mvn -version` | `Apache Maven 3.9.x` + dòng `Java version` khớp JDK | Maven sẵn sàng, đúng JDK |
| `node -v` (nếu cài) | `v2x.x.x` | Node sẵn sàng (tùy chọn) |
| Mở IntelliJ | Vào được màn hình Welcome | IDE sẵn sàng |

> 🎯 **Mẹo vàng cho Windows:** gần như MỌI lỗi "command not found / not recognized" đều do (1) chưa mở PowerShell **mới** sau khi cài, hoặc (2) biến PATH chưa có đường dẫn. Đóng hẳn PowerShell, mở lại, thử lại — trước khi nghĩ là cài hỏng.

> 🎉 Nếu 5 lệnh bắt buộc đầu tiên đều đúng và IntelliJ mở được → **môi trường Windows của bạn đã sẵn sàng.** Tiếp tục làm bài Hello World ở mục 2.8 ngay dưới (giống hệt cho cả hai hệ điều hành).

---

### 2.8. Bài kiểm tra nhỏ (dùng chung cho macOS & Windows): tạo project "Hello World" trong IntelliJ

Để chắc chắn mọi thứ liên thông:

1. Mở IntelliJ → **New Project**.
2. Bên trái chọn **New Project** (loại project thường). Đặt tên `hello-world`.
3. **Language:** Java. **Build system:** IntelliJ (hoặc Maven cũng được). **JDK:** chọn bản 17/21 bạn vừa cài (IntelliJ thường tự nhận ra).
4. Bấm **Create**.
5. Trong thư mục `src`, chuột phải → **New → Java Class**, đặt tên `Main`.
6. Gõ đoạn code này:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Xin chao, day la buoc dau tien cua toi!");
    }
}
```

7. Bấm nút ▶️ (Run) màu xanh bên cạnh dòng `main`.
8. Nếu khung *Run* dưới đáy hiện dòng chữ `Xin chao, day la buoc dau tien cua toi!` → **XONG! Môi trường hoàn hảo.** 🎉

---

<a id="3"></a>
## 🧱 Phần 3 — HTML nền tảng cho Automation

### 3.1. HTML là gì? (ví von dễ hiểu)

Khi bạn mở một trang web, cái bạn **nhìn thấy** (nút, ô nhập, chữ, ảnh) chỉ là lớp "sơn bên ngoài". Bên dưới, trình duyệt đọc một file văn bản gọi là **HTML** để biết cần vẽ cái gì, ở đâu.

> **Ví von:** HTML giống như **bản thiết kế xây nhà**. Bản thiết kế ghi: "Chỗ này là cửa, chỗ kia là cửa sổ, tường cao 3m". Trình duyệt là **thợ xây** đọc bản thiết kế đó và dựng thành ngôi nhà (trang web bạn thấy). Còn bạn — automation tester — cần đọc được **bản thiết kế** để chỉ cho máy "hãy mở **cái cửa này**".

**HTML** viết tắt của *HyperText Markup Language* — ngôn ngữ **đánh dấu** để mô tả cấu trúc trang web. Nó không phải ngôn ngữ lập trình (không có if/else, vòng lặp) — nó chỉ **mô tả**: "đây là một tiêu đề", "đây là một nút bấm".

### 3.2. Cấu trúc một "thẻ" (tag/element) HTML

Đơn vị cơ bản của HTML là **thẻ** (tag). Ví dụ một nút bấm:

```html
<button id="login" class="btn primary" type="submit">Đăng nhập</button>
```

Mổ xẻ từng phần:

```
<button  id="login"  class="btn primary"  type="submit">  Đăng nhập  </button>
  │        │              │                    │              │           │
  │        │              │                    │              │           └─ Thẻ đóng
  │        │              │                    │              └─ Nội dung (text hiển thị)
  │        │              │                    └─ Thuộc tính type
  │        │              └─ Thuộc tính class (có thể chứa nhiều giá trị cách nhau bởi dấu cách)
  │        └─ Thuộc tính id
  └─ Thẻ mở, tên thẻ là "button"
```

- **Thẻ mở** `<button>` và **thẻ đóng** `</button>` (có dấu `/`). Mọi thứ giữa hai thẻ là **nội dung**.
- **Thuộc tính (attribute)** nằm trong thẻ mở, dạng `tên="giá trị"`. Đây là thứ **cực kỳ quan trọng** với automation — ta dùng chúng để "định vị" element.
- Một số thẻ **không có nội dung và không cần thẻ đóng**, gọi là thẻ tự đóng — ví dụ `<input>`, `<img>`.

### 3.3. Các thuộc tính QUAN TRỌNG NHẤT cho automation

Khi automate, bạn cần "chỉ đích danh" một element. Các thuộc tính sau là "chứng minh thư" của element — hãy thuộc lòng:

| Thuộc tính | Ý nghĩa | Vì sao quan trọng với automation |
|-----------|---------|----------------------------------|
| **`id`** | Định danh **DUY NHẤT** trong trang | ⭐ Tốt nhất để định vị — một trang chỉ có một `id` nhất định. Rất ổn định. |
| **`class`** | Nhóm/kiểu (dùng cho CSS trang trí) | Hay dùng, nhưng **có thể trùng** ở nhiều element. Một element có thể có nhiều class. |
| **`name`** | Tên trường (đặc biệt trong form) | Thường dùng cho `<input>`; khá ổn định khi gửi form. |
| **`data-*`** | Thuộc tính "tùy biến" của lập trình viên | ⭐ Ví dụ `data-test="username"`. Rất được ưa chuộng vì thường **dành riêng cho test**, ít bị đổi. |
| **`type`** | Loại của input/button | Phân biệt `text`, `password`, `submit`, `checkbox`... |
| **`placeholder`** | Chữ mờ gợi ý trong ô nhập | Có thể dùng để định vị ô nhập ("Username", "Email"). |
| **`href`** | Địa chỉ đích của một link `<a>` | Kiểm tra link trỏ đúng chỗ. |
| **`value`** | Giá trị hiện tại của input | Đọc/kiểm tra nội dung ô nhập. |

> 💡 **Vì sao `id` và `data-*` là "vàng"?**
> - `id` **duy nhất** → chỉ một element khớp → không nhầm lẫn.
> - `data-test` / `data-testid` thường do dev **cố ý đặt cho tester**, nên nó không đổi khi giao diện thay đổi (đổi màu, đổi chữ). Selector dựa vào nó **bền** nhất.
> - Ngược lại, `class` dùng để trang trí (CSS) nên **hay bị đổi** khi designer chỉnh giao diện → selector dựa vào class dễ gãy hơn.

### 3.4. Các thẻ HTML bạn sẽ gặp nhiều nhất

| Thẻ | Dùng để | Ví dụ |
|-----|---------|-------|
| `<input>` | Ô nhập liệu (text, password, checkbox...) | `<input type="text" id="user">` |
| `<button>` | Nút bấm | `<button>Gửi</button>` |
| `<a>` | Đường link (anchor) | `<a href="/home">Trang chủ</a>` |
| `<div>` | "Cái hộp" gom nhóm, chia bố cục (không có ý nghĩa riêng) | `<div class="card">...</div>` |
| `<span>` | Đoạn text nhỏ trong dòng | `<span class="price">100đ</span>` |
| `<form>` | Bao quanh một biểu mẫu | `<form>...</form>` |
| `<label>` | Nhãn mô tả cho một input | `<label for="user">Tên</label>` |
| `<select>` / `<option>` | Danh sách xổ xuống (dropdown) | `<select><option>A</option></select>` |
| `<table>` `<tr>` `<td>` | Bảng, hàng, ô | `<tr><td>Tên</td></tr>` |
| `<ul>` / `<li>` | Danh sách và mục danh sách | `<ul><li>Mục 1</li></ul>` |
| `<h1>`...`<h6>` | Tiêu đề (heading), h1 to nhất | `<h1>Tiêu đề</h1>` |
| `<p>` | Đoạn văn (paragraph) | `<p>Nội dung...</p>` |
| `<img>` | Hình ảnh | `<img src="logo.png">` |

**Chi tiết về `<input>` — thẻ bạn sẽ tương tác nhiều nhất:**

Thuộc tính `type` quyết định input là loại gì:

```html
<input type="text" ...>       <!-- ô nhập chữ thường -->
<input type="password" ...>   <!-- ô mật khẩu (che ký tự) -->
<input type="email" ...>      <!-- ô email -->
<input type="checkbox" ...>   <!-- ô tick chọn -->
<input type="radio" ...>      <!-- nút chọn tròn (chỉ chọn 1 trong nhóm) -->
<input type="submit" ...>     <!-- nút gửi form -->
```

### 3.5. Ví dụ đầy đủ: một form Login thật

Đây là đoạn HTML mô phỏng một trang đăng nhập điển hình. **Hãy đọc thật kỹ** — sau đó ta sẽ mổ xẻ nó, và ở phần CSS Selector & DevTools ta sẽ dùng lại chính nó.

```html
<form id="login-form" class="auth-box" action="/login" method="post">
  <h2>Đăng nhập hệ thống</h2>

  <label for="username">Tên đăng nhập</label>
  <input
    type="text"
    id="username"
    name="user"
    class="form-input"
    data-test="username-field"
    placeholder="Nhập username của bạn"
  />

  <label for="password">Mật khẩu</label>
  <input
    type="password"
    id="password"
    name="pass"
    class="form-input"
    data-test="password-field"
    placeholder="Nhập mật khẩu"
  />

  <div class="options">
    <input type="checkbox" id="remember" name="remember" />
    <label for="remember">Ghi nhớ đăng nhập</label>
  </div>

  <button type="submit" id="login-btn" class="btn btn-primary" data-test="submit">
    Đăng nhập
  </button>

  <a href="/forgot-password" class="link-forgot">Quên mật khẩu?</a>
</form>
```

**Giải thích từng phần:**

1. **`<form id="login-form" ...>`** — cả biểu mẫu được bọc trong thẻ `<form>`, có `id="login-form"` (duy nhất). `action="/login"` là địa chỉ dữ liệu sẽ được gửi tới, `method="post"` là cách gửi.

2. **`<label for="username">`** — nhãn "Tên đăng nhập". Thuộc tính `for="username"` **liên kết** nhãn này với input có `id="username"` (click vào nhãn sẽ focus vào ô đó). Điều này rất hữu ích — sau này Playwright có `getByLabel("Tên đăng nhập")`.

3. **Ô username:**
   - `type="text"` → ô nhập chữ.
   - `id="username"` → định danh duy nhất (⭐ selector tốt nhất: `#username`).
   - `name="user"` → tên trường khi gửi form.
   - `class="form-input"` → dùng chung với ô password để trang trí (⚠️ **trùng** → không phân biệt được 2 ô).
   - `data-test="username-field"` → ⭐ thuộc tính dành cho test, rất bền.
   - `placeholder="Nhập username của bạn"` → chữ mờ gợi ý.

4. **Ô password:** tương tự username nhưng `type="password"` (che ký tự), `id="password"`, `data-test="password-field"`. Chú ý nó **cũng có** `class="form-input"` giống ô username.

5. **Checkbox "Ghi nhớ":** `<input type="checkbox" id="remember">` nằm trong một `<div class="options">`.

6. **Nút đăng nhập:** `<button type="submit" id="login-btn" class="btn btn-primary" data-test="submit">`. Có tận **hai** class (`btn` và `btn-primary` — cách nhau bởi dấu cách).

7. **Link quên mật khẩu:** `<a href="/forgot-password">` — một đường link, `href` là đích đến.

> 🔑 **Bài học rút ra từ ví dụ này:** Cùng một element có **nhiều cách** để định vị. Ô username ở trên có thể được trỏ tới bằng `id`, `name`, `class`, `data-test`, hay `placeholder`. Kỹ năng của automation tester là **chọn cách bền nhất** — thường là `id` hoặc `data-test`, tránh phụ thuộc `class` hay vị trí.

---

<a id="4"></a>
## 🎯 Phần 4 — CSS Selector

### 4.1. CSS Selector là gì và tại sao phải học?

Trang web có thể có hàng nghìn element. Làm sao chỉ cho máy biết **chính xác** element nào? Bạn cần một cách viết "địa chỉ" của element. Cách phổ biến nhất chính là **CSS Selector**.

> **Ví von:** CSS Selector giống như **địa chỉ nhà**. "Số 5" (`#id`), "tất cả nhà sơn xanh" (`.class`), "mọi ngôi nhà trên phố này" (`tag`)... Bạn mô tả càng chính xác, máy tìm càng đúng element.

CSS Selector vốn được tạo ra để **trang trí** trang web (CSS = Cascading Style Sheets), nhưng automation "mượn" nó để **định vị** element. Playwright, Selenium, và cả hàm `document.querySelector` trong trình duyệt đều hiểu CSS Selector. Học một lần, dùng khắp nơi.

### 4.2. Các loại selector cơ bản

Ta dùng lại form login ở Phần 3.5 để minh họa.

#### a) Selector theo `id` — dùng dấu `#`

```css
#username
```

→ Chọn element có `id="username"`. Vì `id` là **duy nhất**, đây là selector **chính xác và bền nhất**. Luôn ưu tiên nếu element có `id` tử tế.

#### b) Selector theo `class` — dùng dấu `.`

```css
.form-input
```

→ Chọn **TẤT CẢ** element có class `form-input`. Trong form của ta, cả ô username **và** ô password đều có class này → selector này khớp **2 element**. ⚠️ Cẩn thận: khớp nhiều element là nguồn gốc lỗi "strict mode" ở Playwright sau này.

#### c) Selector theo tên thẻ (tag)

```css
button
```

→ Chọn **TẤT CẢ** thẻ `<button>` trong trang. Rất rộng, ít khi dùng một mình.

#### d) Selector theo thuộc tính — dùng `[thuộc-tính=giá-trị]`

```css
[data-test="username-field"]
```

→ Chọn element có thuộc tính `data-test` bằng đúng `username-field`. ⭐ **Rất được ưa chuộng** vì `data-test` thường dành riêng cho automation.

Các biến thể của selector thuộc tính:

| Cú pháp | Ý nghĩa | Ví dụ |
|---------|---------|-------|
| `[attr]` | Có thuộc tính `attr` (bất kể giá trị) | `[disabled]` — mọi element đang bị vô hiệu hóa |
| `[attr="x"]` | `attr` **bằng đúng** `x` | `[type="password"]` |
| `[attr^="x"]` | `attr` **bắt đầu bằng** `x` | `[href^="/user"]` |
| `[attr$="x"]` | `attr` **kết thúc bằng** `x` | `[src$=".png"]` |
| `[attr*="x"]` | `attr` **chứa** `x` | `[class*="btn"]` |

#### e) Kết hợp nhiều điều kiện (viết liền, không cách)

Viết dính nhau nghĩa là "thỏa **tất cả**":

```css
input#username            /* thẻ input VÀ có id="username" */
input.form-input          /* thẻ input VÀ có class form-input */
button.btn.btn-primary    /* thẻ button VÀ có CẢ HAI class btn và btn-primary */
input[type="password"]    /* thẻ input VÀ có type="password" */
```

> 💡 **Mẹo về nhiều class:** `class="btn btn-primary"` là **hai** class riêng biệt. Trong selector, viết `.btn.btn-primary` (hai dấu chấm dính liền) để yêu cầu element có **cả hai**.

### 4.3. Quan hệ giữa các element: cha–con, hậu duệ

Element trong HTML lồng nhau như hộp trong hộp. Ta có thể định vị theo **quan hệ**.

#### Quan hệ hậu duệ (descendant) — dùng **dấu cách**

```css
form input
```

→ Chọn mọi `<input>` **nằm bên trong** (ở bất kỳ độ sâu nào) một `<form>`. "Con, cháu, chắt" đều tính.

```css
#login-form .form-input
```

→ Mọi element có class `form-input` nằm trong element `#login-form`.

#### Quan hệ cha–con trực tiếp (direct child) — dùng **dấu `>`**

```css
.options > input
```

→ Chỉ chọn `<input>` là **con TRỰC TIẾP** (ngay bên dưới một cấp) của `.options`. "Cháu, chắt" **không** tính — chỉ con ruột.

**Minh họa sự khác biệt** với đoạn HTML:

```html
<div class="wrapper">           <!-- ông -->
  <div class="box">             <!-- cha -->
    <span>A</span>              <!-- con trực tiếp của .box -->
    <p><span>B</span></p>       <!-- span B là "cháu" của .box -->
  </div>
</div>
```

| Selector | Khớp element nào | Vì sao |
|----------|------------------|--------|
| `.box span` | **Cả A và B** | Hậu duệ = con và cháu đều tính |
| `.box > span` | **Chỉ A** | Con trực tiếp; B là cháu nên bị loại |
| `.wrapper span` | **Cả A và B** | Đều là hậu duệ của wrapper |
| `.wrapper > span` | **Không có gì** | wrapper không có `<span>` con trực tiếp |

#### Các quan hệ khác (dùng nâng cao)

| Selector | Ý nghĩa |
|----------|---------|
| `a + b` | Element `b` đứng **ngay sau** `a` (anh em liền kề) |
| `a ~ b` | Mọi `b` là **anh em phía sau** `a` |
| `ul li:first-child` | Con **đầu tiên** |
| `ul li:last-child` | Con **cuối cùng** |
| `ul li:nth-child(2)` | Con **thứ 2** |

### 4.4. 📊 BẢNG VÀNG: Selector → element nó trỏ tới

Dùng lại form login ở Phần 3.5. Hãy đối chiếu từng selector với element nó chọn:

| # | CSS Selector | Trỏ tới element nào | Số element khớp | Ghi chú |
|---|--------------|---------------------|:---------------:|---------|
| 1 | `#username` | Ô nhập username | 1 | ⭐ Bền nhất — theo id duy nhất |
| 2 | `#password` | Ô nhập password | 1 | ⭐ Theo id |
| 3 | `#login-btn` | Nút "Đăng nhập" | 1 | ⭐ Theo id |
| 4 | `.form-input` | **Cả** ô username **và** password | **2** | ⚠️ Khớp nhiều — dễ gây strict mode |
| 5 | `input` | Cả 3 input (user, pass, checkbox) | **3** | ⚠️ Quá rộng |
| 6 | `input[type="password"]` | Ô password | 1 | ✅ Kết hợp tag + thuộc tính |
| 7 | `[data-test="username-field"]` | Ô username | 1 | ⭐ Theo data-test, rất bền |
| 8 | `[data-test="submit"]` | Nút "Đăng nhập" | 1 | ⭐ Theo data-test |
| 9 | `button.btn.btn-primary` | Nút "Đăng nhập" | 1 | ✅ Tag + 2 class |
| 10 | `#login-form input` | Cả 3 input trong form | **3** | Quan hệ hậu duệ |
| 11 | `#login-form > button` | Nút "Đăng nhập" | 1 | Con trực tiếp của form |
| 12 | `.options > input` | Checkbox "Ghi nhớ" | 1 | Con trực tiếp của `.options` |
| 13 | `a.link-forgot` | Link "Quên mật khẩu?" | 1 | Tag `a` + class |
| 14 | `[href="/forgot-password"]` | Link "Quên mật khẩu?" | 1 | Theo thuộc tính href |
| 15 | `input[name="user"]` | Ô username | 1 | Theo name |
| 16 | `input[placeholder*="mật khẩu"]` | Ô password | 1 | placeholder **chứa** "mật khẩu" |

> 🎓 **Bài học lớn:** Với ô username, ta có ít nhất **5 selector đúng**: `#username`, `[data-test="username-field"]`, `input[name="user"]`, `#login-form input:first-of-type`, `[placeholder="Nhập username của bạn"]`. Nhưng **không phải cái nào cũng tốt như nhau**. Thứ tự ưu tiên khi chọn:
>
> 1. `id` hoặc `data-test` (bền, rõ ràng) — **ưu tiên cao nhất**.
> 2. Thuộc tính ổn định khác (`name`, `type` kết hợp).
> 3. Class có ý nghĩa (nếu không trùng).
> 4. **Tránh:** phụ thuộc vị trí (`:nth-child`), class trang trí hay đổi, chuỗi hậu duệ quá dài.

---

<a id="5"></a>
## 🌳 Phần 5 — DOM là gì

### 5.1. Từ HTML "phẳng" đến cái cây DOM

Ở Phần 3, HTML là một **file văn bản** — các dòng chữ nối tiếp nhau. Nhưng khi trình duyệt đọc file đó, nó dựng lên trong bộ nhớ một **cấu trúc cây** gọi là **DOM** (*Document Object Model*).

> **Ví von:** HTML là **kịch bản phim viết trên giấy** (văn bản tĩnh). DOM là **bộ phim đang chạy trong đầu đạo diễn** — sống động, có thể tua, sửa, thêm nhân vật. Trình duyệt "diễn" HTML thành DOM, và DOM mới là thứ đang thực sự sống trong trang.

- **HTML** = văn bản gốc bạn viết ra (tĩnh).
- **DOM** = cây các đối tượng mà trình duyệt tạo ra **từ** HTML đó, đang nằm trong bộ nhớ, **có thể thay đổi** bằng JavaScript.

### 5.2. Vì sao gọi là "cây"?

Vì các element **lồng vào nhau** tạo thành quan hệ cha–con y như cây gia phả. Xét đoạn HTML rút gọn của form login:

```html
<form id="login-form">
  <h2>Đăng nhập hệ thống</h2>
  <label for="username">Tên đăng nhập</label>
  <input id="username">
  <div class="options">
    <input id="remember" type="checkbox">
    <label for="remember">Ghi nhớ đăng nhập</label>
  </div>
  <button id="login-btn">Đăng nhập</button>
</form>
```

Trình duyệt dựng thành cây DOM như sau:

```
form#login-form                     ← nút gốc (cha của tất cả bên dưới)
├── h2  ("Đăng nhập hệ thống")
├── label[for=username]  ("Tên đăng nhập")
├── input#username
├── div.options                     ← nút cha con
│   ├── input#remember (checkbox)
│   └── label[for=remember]  ("Ghi nhớ đăng nhập")
└── button#login-btn  ("Đăng nhập")
```

**Thuật ngữ quan hệ trong cây** (bạn sẽ gặp lại ở Playwright khi "đi" trong DOM):

| Thuật ngữ | Nghĩa | Ví dụ trong cây trên |
|-----------|-------|----------------------|
| **Node (nút)** | Mỗi element là một nút | `form`, `input`, `div`... |
| **Parent (cha)** | Nút bao ngoài trực tiếp | `div.options` là cha của `input#remember` |
| **Child (con)** | Nút bên trong trực tiếp | `input#remember` là con của `div.options` |
| **Sibling (anh em)** | Các nút cùng cha | `input#username` và `div.options` là anh em (cùng cha `form`) |
| **Descendant (hậu duệ)** | Con, cháu, chắt... | `label[for=remember]` là hậu duệ của `form` |
| **Ancestor (tổ tiên)** | Cha, ông, cụ... | `form` là tổ tiên của mọi nút bên dưới |
| **Root (gốc)** | Nút trên cùng | `form#login-form` (trong ví dụ này) |

### 5.3. Vì sao Playwright thao tác trên DOM chứ không phải trên "hình ảnh"?

Đây là điểm cốt lõi giúp bạn hiểu bản chất automation:

- Máy tính **không "nhìn" trang web bằng mắt** như bạn. Với con người, cái nút là một hình chữ nhật xanh có chữ. Với máy, cái nút là một **nút trong cây DOM**: `button#login-btn`.
- Khi bạn viết `page.click("#login-btn")`, Playwright **không** đi tìm "hình chữ nhật xanh" trên ảnh chụp màn hình. Nó đi vào **cây DOM**, tìm nút có `id="login-btn"`, rồi ra lệnh click vào đúng nút đó.
- Vì thao tác trên DOM, Playwright **chính xác** và **nhanh**: nó biết chính xác element ở đâu, có tồn tại chưa, đã hiện ra chưa, có bị disable không — những thông tin này đều nằm trong DOM.

> 🔗 **Đây chính là lý do bạn phải học HTML + CSS Selector + DOM TRƯỚC khi học Playwright:** Playwright chỉ là công cụ ra lệnh "hãy tìm nút này trong DOM rồi click". Nhưng **bạn** phải viết được cái "nút này" đó — tức là **CSS Selector** trỏ vào đúng **node** trong **cây DOM** được dựng từ **HTML**. Bốn khái niệm này là một chuỗi liền mạch.

### 5.4. DOM có thể thay đổi — và đây là nguồn gốc của flaky test

Điểm khác biệt lớn giữa HTML tĩnh và DOM sống: **DOM thay đổi liên tục** khi trang chạy. JavaScript có thể:

- Thêm element mới (ví dụ: sau khi login, thêm nút "Đăng xuất").
- Xóa element (ẩn thông báo lỗi sau vài giây).
- Đổi nội dung/thuộc tính (đổi `class`, đổi text).

Ví dụ: khi bạn bấm "Đăng nhập" với sai mật khẩu, JavaScript **chèn thêm** vào DOM một element báo lỗi:

```html
<div class="error-message" data-test="error">Sai tên đăng nhập hoặc mật khẩu.</div>
```

Element này **không có** trong HTML gốc — nó chỉ **xuất hiện trong DOM** sau hành động. Điều này giải thích một thử thách kinh điển của automation: **element có thể chưa tồn tại ngay lúc bạn muốn thao tác** (trang còn đang load, dữ liệu chưa về). Đây là lý do Playwright có tính năng **auto-wait** (tự chờ element xuất hiện) — bạn sẽ học sâu ở Giai đoạn 3. Còn bây giờ, chỉ cần nhớ: **DOM là một cái cây sống, luôn biến đổi.**

---

<a id="6"></a>
## 🔧 Phần 6 — Chrome DevTools (F12)

**Chrome DevTools** là "phòng thí nghiệm" tích hợp sẵn trong trình duyệt Chrome (Edge, Cốc Cốc cũng có, tương tự). Đây là **công cụ số 1** của automation tester — nơi bạn nhìn thấy DOM thật, đọc thuộc tính, và **test selector trước khi viết vào code**. Thành thạo DevTools = tiết kiệm hàng giờ debug.

### 6.1. Mở DevTools

Có 3 cách mở (dùng được trên cả macOS và Windows):

- Phím tắt: bấm **`F12`** (cách nhanh, giống nhau trên cả hai hệ). Hoặc:
  - **macOS:** `Cmd + Option + I`
  - **Windows:** `Ctrl + Shift + I`
- Chuột phải vào bất kỳ chỗ nào trên trang → **Inspect** (Kiểm tra).
- Menu Chrome (⋮ góc phải) → **More Tools → Developer Tools**.

Một bảng công cụ hiện ra (thường ở bên phải hoặc dưới đáy). Bạn sẽ thấy nhiều tab: **Elements, Console, Network, Sources...**. Ta tập trung 3 tab quan trọng nhất.

> 💡 **Mẹo:** Bấm biểu tượng ⋮ trong DevTools → *Dock side* để chọn gắn bảng ở phải/dưới/tách rời cho dễ nhìn.

### 6.2. Tab ELEMENTS — nhìn và đọc DOM

Đây là nơi bạn thấy **cây DOM sống** của trang, và là tab bạn dùng nhiều nhất.

**Thao tác cầm tay — Inspect một element:**

1. Mở tab **Elements**.
2. Bấm biểu tượng **mũi tên trong ô vuông** ở góc trên trái DevTools (phím tắt — macOS: `Cmd + Option + C`, Windows: `Ctrl + Shift + C`) — đây là công cụ **"Inspect/Select element"**.
3. Di chuột lên trang web → element dưới con trỏ được **tô sáng**, kèm tooltip hiện tên thẻ, kích thước, class.
4. **Click** vào element bạn quan tâm (ví dụ ô username).
5. Trong tab Elements, dòng HTML tương ứng được **tô đậm/highlight**. Bạn đọc được ngay toàn bộ thuộc tính của nó.

Ví dụ khi inspect ô username của form login, bạn sẽ thấy dòng như:

```html
<input type="text" id="username" name="user" class="form-input" data-test="username-field" placeholder="Nhập username của bạn">
```

→ Từ đây bạn **đọc được** mọi "chứng minh thư" của element: `id="username"`, `data-test="username-field"`... để chọn selector.

**Các thao tác hữu ích khác trong tab Elements:**

- **Xem quan hệ cây:** các element lồng nhau hiển thị thụt vào; bấm tam giác ▶ để mở/đóng nhánh — bạn thấy rõ cha–con.
- **Copy selector:** chuột phải vào dòng HTML → **Copy → Copy selector** (Chrome tự sinh CSS selector) hoặc **Copy → Copy XPath**.
  > ⚠️ **Cảnh báo:** Selector Chrome tự sinh thường **rất dài và mong manh** (kiểu `#root > div:nth-child(2) > form > input`). Dùng để **tham khảo nhanh** thì được, nhưng hãy tập **tự viết selector ngắn gọn dựa vào `id`/`data-test`** — đó mới là kỹ năng thật.
- **Sửa thử tại chỗ:** double-click vào text hay thuộc tính để sửa (chỉ đổi tạm trên máy bạn, không ảnh hưởng server) — hữu ích để thử nghiệm.
- **Tìm nhanh trong DOM:** bấm tìm ngay trong tab Elements (macOS: `Cmd + F`, Windows: `Ctrl + F`) → gõ text, id, hoặc **cả CSS selector** → nó tìm và nhảy tới element khớp, đồng thời cho biết **có bao nhiêu kết quả**. Đây là cách nhanh để đếm số element một selector khớp.

### 6.3. Tab CONSOLE — "phòng thử" selector (quan trọng nhất với automation)

Console là nơi bạn **gõ lệnh JavaScript** và xem kết quả ngay. Với automation, công dụng đắt giá nhất là: **kiểm tra selector có trỏ đúng element không, TRƯỚC khi viết vào code Java.** Thử ở đây mất 5 giây; đoán mò trong code Java rồi chạy lại mất 5 phút.

**Hai hàm bạn phải thuộc:**

#### `document.querySelectorAll("selector")` — tìm TẤT CẢ element khớp

```javascript
document.querySelectorAll(".form-input")
```

→ Trả về một **danh sách** (NodeList) mọi element khớp selector `.form-input`. Kết quả hiện `NodeList(2) [input#username, input#password]` — cho biết có **2** element khớp và chúng là gì.

#### `document.querySelector("selector")` — tìm element ĐẦU TIÊN khớp

```javascript
document.querySelector("#username")
```

→ Trả về **một** element đầu tiên khớp (hoặc `null` nếu không có).

#### `$$("selector")` và `$("selector")` — bản viết tắt tiện lợi

DevTools cung cấp lối viết tắt (chỉ chạy trong Console, không phải JS chuẩn):

```javascript
$$("selector")    // giống querySelectorAll — trả về MẢNG mọi element khớp
$("selector")     // giống querySelector    — trả về element ĐẦU TIÊN
```

**Thao tác cầm tay — quy trình "test selector":**

1. Mở tab **Console**.
2. Gõ selector bạn định dùng, ví dụ:
   ```javascript
   $$("[data-test='username-field']")
   ```
   > 💡 Chú ý dấu nháy: selector nằm trong `"..."`, nên bên trong dùng `'...'` (nháy đơn) để không bị lẫn.
3. Nhấn **Enter**. Đọc kết quả:
   - `[input#username]` với **1** phần tử → ✅ selector chọn đúng **1** element. Tuyệt.
   - `(2) [...]` hoặc `(3) [...]` → ⚠️ selector khớp **nhiều** element → cần cụ thể hơn (nếu không sẽ dính strict mode ở Playwright).
   - `[]` (mảng rỗng) → ❌ **không** khớp element nào → selector sai, kiểm tra lại.
4. **Đếm số element khớp** nhanh:
   ```javascript
   $$(".form-input").length
   ```
   → in ra `2`.
5. **Rê chuột** lên kết quả trả về trong Console → element tương ứng được **tô sáng** trên trang → xác nhận bằng mắt là đúng element bạn muốn.

**Ví dụ thực chiến — so sánh selector tốt và xấu ngay trong Console:**

```javascript
$$("input").length                        // 3  → quá rộng, khớp cả 3 input
$$(".form-input").length                  // 2  → vẫn khớp 2 (user + pass)
$$("#username").length                     // 1  → ✅ chuẩn xác
$$("[data-test='username-field']").length  // 1  → ✅ chuẩn xác, lại còn bền
```

→ Chỉ trong vài giây, bạn tự chứng minh được vì sao `#username` và `[data-test=...]` tốt hơn `.form-input`.

### 6.4. Tab NETWORK — xem request/response

Tab **Network** ghi lại **mọi cuộc trao đổi** giữa trình duyệt và server: tải trang, tải ảnh, và đặc biệt là các **lời gọi API** (dữ liệu chạy ngầm). Ở Giai đoạn 0 bạn chỉ cần **làm quen** — nó sẽ cực quan trọng khi học API testing và mock (Giai đoạn 4, 6).

**Thao tác cầm tay — xem một request đăng nhập:**

1. Mở tab **Network**.
2. **Quan trọng:** đảm bảo nút ghi hình tròn đỏ đang **bật** (đỏ = đang ghi). Nếu muốn danh sách gọn, bấm 🚫 (Clear) để xóa log cũ.
3. Thực hiện hành động trên trang — ví dụ điền username/password rồi bấm **Đăng nhập**.
4. Danh sách các request hiện ra. Dùng ô lọc **Fetch/XHR** ở thanh trên để chỉ xem các lời gọi API (bỏ bớt ảnh, CSS, font).
5. **Click vào một request** (ví dụ request tên `login` hoặc `authenticate`). Bảng chi tiết mở ra với các mục:
   - **Headers:** thông tin chung — **Request URL** (gọi tới đâu), **Request Method** (`GET`/`POST`...), và **Status Code** (`200` = OK, `401` = không có quyền, `404` = không tìm thấy, `500` = lỗi server).
   - **Payload** (hoặc *Request*): dữ liệu **gửi đi** — ví dụ `{ "username": "...", "password": "..." }`.
   - **Response:** dữ liệu server **trả về** — thường là JSON (ví dụ token đăng nhập, thông tin user, hoặc thông báo lỗi).
   - **Preview:** bản xem đẹp mắt của Response.

**Vì sao automation tester cần Network?**

- **Hiểu ứng dụng hoạt động ra sao:** thấy được UI gọi API nào, gửi/nhận gì.
- **Debug:** khi test fail, xem request có gửi đúng không, server trả về lỗi gì.
- **Chuẩn bị cho API test & mock** (Giai đoạn 4, 6): sau này bạn sẽ **giả lập** (mock) response để test UI mà không cần server thật.

> 📌 Ở Giai đoạn 0, mục tiêu chỉ là: **mở được tab Network, thực hiện một hành động, tìm được request tương ứng, và đọc được Status Code + Response.** Vậy là đủ.

### 6.5. Bảng tổng hợp 3 tab

| Tab | Dùng để | Lệnh/thao tác chính | Bạn cần thành thạo |
|-----|---------|---------------------|--------------------|
| **Elements** | Nhìn & đọc DOM, lấy thuộc tính | Inspect (Mac `Cmd+Opt+C` / Win `Ctrl+Shift+C`), tìm trong DOM (Mac `Cmd+F` / Win `Ctrl+F`) | ⭐⭐⭐ |
| **Console** | Test selector | `$$("sel")`, `document.querySelectorAll("sel")`, `.length` | ⭐⭐⭐ |
| **Network** | Xem request/response API | Lọc Fetch/XHR, đọc Status/Payload/Response | ⭐⭐ (làm quen) |

---

<a id="7"></a>
## 🛠️ Phần 7 — Bài thực hành có hướng dẫn: SauceDemo

Giờ ta áp dụng mọi thứ vào một trang **thật**: [https://www.saucedemo.com/](https://www.saucedemo.com/) — một website mua sắm giả lập được tạo riêng để luyện automation. Đây là "sân tập" bạn sẽ dùng suốt cả khóa.

> 🎯 **Mục tiêu bài thực hành:** Tự tay F12, tìm được selector của ô **username**, ô **password**, và nút **Login** trên SauceDemo. Test chúng bằng Console. Đây chính là kỹ năng bạn sẽ dùng ở mọi bài Playwright sau này.

### Bước 1 — Mở trang và DevTools

1. Mở Chrome, vào [https://www.saucedemo.com/](https://www.saucedemo.com/).
2. Bạn thấy một form login đơn giản: ô "Username", ô "Password", nút "Login". (Trang còn liệt kê sẵn các tài khoản mẫu như `standard_user` và mật khẩu `secret_sauce` — tiện cho việc login thử.)
3. Mở DevTools: bấm **`F12`** (hoặc macOS: `Cmd + Option + I` / Windows: `Ctrl + Shift + I`).

### Bước 2 — Inspect ô Username

1. Bấm công cụ Inspect (macOS: `Cmd + Option + C` / Windows: `Ctrl + Shift + C`).
2. Click vào **ô nhập Username** trên trang.
3. Trong tab Elements, đọc dòng HTML được highlight. Ghi lại các thuộc tính bạn thấy: có `id` không? có `data-test` không? `name`, `class`, `placeholder`?

<details>
<summary>💡 <b>Gợi ý đáp án — Ô Username</b> (tự làm trước rồi mới mở)</summary>

Dòng HTML của ô username trên SauceDemo trông giống:

```html
<input type="text" id="user-name" name="user-name" class="input_error form_input" data-test="username" placeholder="Username" autocorrect="off" autocapitalize="none">
```

**Các selector đúng (test được trong Console):**

| Selector | Số khớp | Đánh giá |
|----------|:-------:|----------|
| `#user-name` | 1 | ⭐ Tốt — theo id |
| `[data-test="username"]` | 1 | ⭐ Tốt nhất — data-test dành cho test |
| `input[name="user-name"]` | 1 | ✅ Ổn — theo name |
| `[placeholder="Username"]` | 1 | ✅ Được — theo placeholder |

</details>

### Bước 3 — Inspect ô Password

Làm y hệt Bước 2 nhưng click vào **ô Password**.

<details>
<summary>💡 <b>Gợi ý đáp án — Ô Password</b></summary>

```html
<input type="password" id="password" name="password" class="input_error form_input" data-test="password" placeholder="Password" autocorrect="off" autocapitalize="none">
```

**Selector đúng:**

| Selector | Số khớp | Đánh giá |
|----------|:-------:|----------|
| `#password` | 1 | ⭐ Tốt |
| `[data-test="password"]` | 1 | ⭐ Tốt nhất |
| `input[type="password"]` | 1 | ✅ Được (chỉ có 1 ô password trên trang này) |

</details>

### Bước 4 — Inspect nút Login

Inspect **nút Login**.

<details>
<summary>💡 <b>Gợi ý đáp án — Nút Login</b></summary>

```html
<input type="submit" class="submit-button btn_action" id="login-button" name="login-button" data-test="login-button" value="Login">
```

> 👀 Lưu ý thú vị: nút Login của SauceDemo **không phải** thẻ `<button>` mà là `<input type="submit">` với `value="Login"` — chữ "Login" nằm ở thuộc tính `value`, không phải nội dung thẻ. Đây là lý do phải **inspect thật** thay vì đoán!

**Selector đúng:**

| Selector | Số khớp | Đánh giá |
|----------|:-------:|----------|
| `#login-button` | 1 | ⭐ Tốt |
| `[data-test="login-button"]` | 1 | ⭐ Tốt nhất |
| `input[type="submit"]` | 1 | ✅ Được |

</details>

### Bước 5 — Test selector trong Console

Mở tab **Console**, gõ lần lượt và quan sát kết quả:

```javascript
$$("#user-name").length          // kỳ vọng: 1
$$("#password").length           // kỳ vọng: 1
$$("#login-button").length       // kỳ vọng: 1
$$("[data-test='username']")     // kỳ vọng: [input#user-name]  (1 phần tử)
$$(".form_input").length         // thử xem: khớp mấy element?
```

Rê chuột lên kết quả trả về để thấy element được highlight trên trang. Bạn vừa **tự xác minh** selector của mình — đúng quy trình một automation tester chuyên nghiệp làm hằng ngày.

### Bước 6 — (Thử thách) Login thật và xem Network

1. Mở tab **Network**, bật ghi, lọc **Fetch/XHR**.
2. Trên trang, nhập username `standard_user`, password `secret_sauce`, bấm **Login**.
3. Bạn được chuyển sang trang danh sách sản phẩm. Quay lại tab Network xem có request nào được ghi.
4. Thử inspect một sản phẩm bất kỳ trên trang mới — tìm `data-test` của nút "Add to cart".

<details>
<summary>💡 <b>Gợi ý</b></summary>

- SauceDemo là ứng dụng khá tĩnh, nên khi login có thể bạn thấy ít request XHR (nó chủ yếu điều hướng trang). Đừng lo nếu Network không nhiều — bạn vẫn thấy request tải trang mới.
- Nút thêm giỏ hàng có `data-test` dạng `add-to-cart-sauce-labs-backpack` — mỗi sản phẩm một giá trị khác nhau. Quan sát cách dev đặt `data-test` có quy luật → sau này bạn khai thác được khi viết test data-driven.

</details>

> ✅ **Hoàn thành bài thực hành này nghĩa là bạn đã làm được kỹ năng cốt lõi của Giai đoạn 0:** inspect element bất kỳ, đọc thuộc tính, tự viết và tự kiểm chứng CSS selector trên một trang thật.

---

<a id="8"></a>
## ✍️ Phần 8 — Bài tập tự làm

> Hãy **tự làm hết** rồi mới xem [Đáp án ở Phần 10](#10). Tự vật lộn 5 phút giá trị hơn đọc đáp án 5 giây. Nhiều bài yêu cầu bạn **thực sự mở F12 và gõ trong Console** — đừng chỉ nghĩ trong đầu.

Dùng lại đoạn **HTML form login ở Phần 3.5** cho các bài 1–5 (chép nó ra, hoặc hình dung nó).

**Bài 1 (HTML — đọc thuộc tính).**
Cho thẻ: `<input type="email" id="email" name="userEmail" class="form-input required" data-test="email-input" placeholder="you@example.com">`.
Hãy liệt kê: (a) tên thẻ, (b) giá trị của `id`, (c) `input` này có mấy class và là những class nào, (d) thuộc tính nào phù hợp nhất để automation dùng và vì sao.

**Bài 2 (CSS Selector — viết selector).**
Với form login ở Phần 3.5, hãy viết CSS selector trỏ **duy nhất** tới:
(a) ô password, (b) nút "Đăng nhập", (c) checkbox "Ghi nhớ đăng nhập", (d) link "Quên mật khẩu?". Với mỗi câu, ưu tiên selector **bền nhất**.

**Bài 3 (CSS Selector — đếm số khớp).**
Cũng với form đó, cho biết mỗi selector sau khớp **bao nhiêu** element, và **là element nào**:
(a) `.form-input` (b) `input` (c) `#login-form > input` (d) `[data-test]` (e) `button`.

**Bài 4 (CSS Selector — sửa selector xấu).**
Một bạn viết selector `#login-form > div > input` để trỏ tới checkbox "Ghi nhớ". Selector này có đúng không? Có điểm gì chưa tối ưu? Hãy đề xuất một selector tốt hơn.

**Bài 5 (DOM — quan hệ cây).**
Với form login ở Phần 3.5: (a) `<div class="options">` là **con** của element nào? (b) Element `<label for="remember">` và `<input id="remember">` có quan hệ gì với nhau? (c) Liệt kê tất cả **con trực tiếp** của `<form id="login-form">`.

**Bài 6 (DevTools — Console, làm thật).**
Mở [SauceDemo](https://www.saucedemo.com/), F12 → Console. Dùng `$$()` để trả lời:
(a) Selector `.form_input` khớp mấy element? (b) Trên trang login, có bao nhiêu thẻ `input` tổng cộng? (c) `$$("#login-button").length` trả về gì?

**Bài 7 (DevTools — Elements, làm thật).**
Trên SauceDemo, sau khi login bằng `standard_user` / `secret_sauce`, inspect **nút giỏ hàng** (icon giỏ ở góc phải trên) và **một tên sản phẩm** bất kỳ. Ghi lại `data-test` (hoặc `id`/`class`) của chúng và viết selector trỏ tới từng cái.

**Bài 8 (Tổng hợp — 5 selector cho 1 element).**
Trên SauceDemo, hãy viết **5 CSS selector KHÁC NHAU** cùng trỏ tới **ô Username**, rồi test cả 5 trong Console để xác nhận mỗi cái đều khớp đúng 1 element. Sau đó xếp hạng chúng từ **bền nhất → dễ gãy nhất** và giải thích ngắn gọn. (Đây chính là bài tập trong giáo trình gốc — làm được bài này là bạn đã "chốt" Giai đoạn 0.)

---

<a id="9"></a>
## 🧪 Phần 9 — Quiz tự đánh giá

> Chọn đáp án rồi đối chiếu [Phần 11](#11). Làm nghiêm túc, không xem trước.

**Câu 1.** Phát biểu nào **ĐÚNG** về automation test?
- A. Automation thay thế hoàn toàn manual test.
- B. Mọi test case đều nên được automate.
- C. Automation phù hợp nhất cho các case regression, ổn định, chạy lặp nhiều lần.
- D. Automation không cần biết lập trình.

**Câu 2.** Trường hợp nào **KHÔNG nên** ưu tiên automate?
- A. Luồng login chạy lại mỗi lần build.
- B. Một tính năng đang thay đổi giao diện liên tục mỗi ngày.
- C. Test data-driven với 50 bộ dữ liệu.
- D. Smoke test các chức năng cốt lõi.

**Câu 3.** Thuộc tính nào thường **bền nhất** để viết selector cho automation?
- A. `class` (dùng để trang trí).
- B. Vị trí `:nth-child(3)`.
- C. `id` hoặc `data-test`.
- D. Màu sắc của element.

**Câu 4.** CSS selector `.form-input` trong form login ở Phần 3.5 khớp bao nhiêu element?
- A. 0
- B. 1
- C. 2
- D. 3

**Câu 5.** Selector `.box > span` khác `.box span` ở điểm nào?
- A. Không khác gì, chỉ là hai cách viết.
- B. `>` chỉ chọn **con trực tiếp**; dấu cách chọn **mọi hậu duệ** (con, cháu...).
- C. `>` chọn mọi hậu duệ; dấu cách chỉ chọn con trực tiếp.
- D. `>` chọn anh em kế tiếp.

**Câu 6.** DOM là gì?
- A. Một ngôn ngữ lập trình.
- B. File HTML gốc lưu trên server.
- C. Cấu trúc **cây** các đối tượng mà trình duyệt dựng ra từ HTML, có thể thay đổi khi trang chạy.
- D. Một loại CSS selector.

**Câu 7.** Trong Console của DevTools, lệnh nào cho biết một selector khớp **bao nhiêu** element?
- A. `document.querySelector("sel")`
- B. `$$("sel").length`
- C. `click("sel")`
- D. `$("sel")`

**Câu 8.** Bạn muốn xem một lời gọi API trả về Status Code và dữ liệu gì khi bấm nút Login. Bạn mở tab nào của DevTools?
- A. Elements
- B. Console
- C. Network
- D. Sources

---

<a id="10"></a>
## ✅ Phần 10 — Đáp án bài tập

**Bài 1.**
(a) Tên thẻ: `input`.
(b) `id` = `email`.
(c) Có **2** class: `form-input` và `required` (phân tách bởi dấu cách).
(d) Tốt nhất cho automation: **`data-test="email-input"`** (hoặc `id="email"`). Lý do: `data-test` thường được dev đặt riêng cho test nên rất bền; `id` thì duy nhất. Tránh dùng `class="form-input"` vì nó có thể trùng với input khác và hay bị đổi khi chỉnh giao diện.

**Bài 2.** (Có thể có nhiều đáp án đúng; đây là lựa chọn bền nhất.)
- (a) Ô password: `#password` hoặc `[data-test="password-field"]`.
- (b) Nút "Đăng nhập": `#login-btn` hoặc `[data-test="submit"]`.
- (c) Checkbox "Ghi nhớ": `#remember`.
- (d) Link "Quên mật khẩu?": `a.link-forgot` hoặc `[href="/forgot-password"]`.

**Bài 3.**
- (a) `.form-input` → **2** element: ô username và ô password.
- (b) `input` → **3** element: username, password, checkbox `#remember`.
- (c) `#login-form > input` → **2** element: username và password (chúng là con **trực tiếp** của form; còn checkbox `#remember` nằm trong `div.options` nên **không** phải con trực tiếp của form → không tính).
- (d) `[data-test]` → **3** element: ô username (`username-field`), ô password (`password-field`), nút đăng nhập (`submit`).
- (e) `button` → **1** element: nút "Đăng nhập".

**Bài 4.**
- Selector `#login-form > div > input` **có thể chạy đúng** (trỏ tới checkbox `#remember`, vì nó là `input` con của `div.options` con của form). Tuy nhiên **chưa tối ưu** vì:
  - Phụ thuộc vào **cấu trúc lồng nhau** (`form > div > input`) — nếu dev thêm/bớt một lớp `div`, selector gãy.
  - Không rõ ràng: người đọc không biết nó trỏ tới cái gì.
  - Nếu trong `div` có nhiều `input`, selector sẽ khớp nhầm.
- **Selector tốt hơn:** `#remember` (dùng thẳng id duy nhất) — ngắn, bền, rõ ràng.

**Bài 5.**
- (a) `<div class="options">` là con **trực tiếp** của `<form id="login-form">`.
- (b) `<label for="remember">` và `<input id="remember">` là **anh em (sibling)** — cùng là con của `<div class="options">`. (Ngoài ra `for="remember"` liên kết logic nhãn với input.)
- (c) Con trực tiếp của `<form id="login-form">`: `<h2>`, `<label for="username">`, `<input id="username">`, `<label for="password">`, `<input id="password">`, `<div class="options">`, `<button id="login-btn">`, và `<a class="link-forgot">`. (Checkbox `#remember` và nhãn của nó **không** phải con trực tiếp của form — chúng nằm trong `div.options`.)

**Bài 6.** (Kết quả trên SauceDemo tại thời điểm biên soạn; con số có thể đổi nếu site cập nhật — điều quan trọng là bạn **tự chạy và đọc được kết quả**.)
- (a) `.form_input` → thường khớp **2** (ô username và password đều mang class `form_input`).
- (b) Tổng số `input` trên trang login: `$$("input").length` → thường là **3** (username, password, và nút submit — nhớ rằng nút Login là `<input type="submit">`, không phải `<button>`).
- (c) `$$("#login-button").length` → **1**.

**Bài 7.** (Giá trị tham khảo — hãy tự inspect để xác nhận.)
- Nút giỏ hàng: có `data-test="shopping-cart-link"` (và class `shopping_cart_link`) → selector: `[data-test="shopping-cart-link"]` hoặc `.shopping_cart_link`.
- Tên sản phẩm: nằm trong element có class `inventory_item_name` (thường là `data-test="inventory-item-name"`) → selector: `.inventory_item_name` (khớp **nhiều** vì có nhiều sản phẩm — đây là ví dụ thực tế của selector trỏ tới một **danh sách**, bạn sẽ học cách lọc từng cái ở Giai đoạn 4).

**Bài 8.** (Ví dụ 5 selector cho ô Username của SauceDemo, xếp từ bền → dễ gãy.)

| Hạng | Selector | Vì sao |
|:----:|----------|--------|
| 1 (bền nhất) | `[data-test="username"]` | `data-test` dành riêng cho test, ít khi đổi |
| 2 | `#user-name` | `id` duy nhất, rất ổn định |
| 3 | `input[name="user-name"]` | `name` khá ổn định (dùng khi gửi form) |
| 4 | `[placeholder="Username"]` | placeholder có thể đổi khi đổi ngôn ngữ/wording |
| 5 (dễ gãy nhất) | `form > div:first-child input` | Phụ thuộc **vị trí & cấu trúc** — đổi layout là gãy |

Cả 5 khi test bằng `$$("...").length` đều cho kết quả **1**. Bài học: **cùng trỏ đúng 1 element, nhưng độ bền rất khác nhau** — luôn chọn selector dựa trên thuộc tính ổn định (`data-test`, `id`), tránh phụ thuộc vị trí.

---

<a id="11"></a>
## 🎓 Phần 11 — Đáp án quiz

| Câu | Đáp án | Giải thích ngắn |
|:---:|:------:|-----------------|
| 1 | **C** | Automation mạnh nhất ở regression/case ổn định chạy lặp nhiều lần. A, B, D đều là kỳ vọng sai. |
| 2 | **B** | Tính năng đang đổi liên tục → viết xong lại gãy → chưa nên automate. |
| 3 | **C** | `id` (duy nhất) và `data-test` (dành cho test) là bền nhất. Class trang trí và vị trí dễ gãy. |
| 4 | **C** | `.form-input` khớp **2**: ô username và password đều có class này. |
| 5 | **B** | `>` = con trực tiếp; dấu cách = mọi hậu duệ (con, cháu, chắt...). |
| 6 | **C** | DOM là cây đối tượng trình duyệt dựng từ HTML, sống động và thay đổi được. |
| 7 | **B** | `$$("sel").length` đếm số element khớp. `$()`/`querySelector` chỉ lấy 1. |
| 8 | **C** | Tab **Network** để xem request/response, Status Code, Payload. |

**Thang tự đánh giá:**
- **7–8 đúng:** Xuất sắc — bạn nắm chắc nền tảng, sẵn sàng qua Giai đoạn 1.
- **5–6 đúng:** Khá — xem lại các câu sai và phần lý thuyết tương ứng.
- **Dưới 5:** Hãy đọc lại Phần 1–6 và **làm lại bài thực hành F12**. Đừng vội qua giai đoạn sau — nền tảng này quá quan trọng.

---

<a id="12"></a>
## 🏁 Phần 12 — Checklist Milestone Giai đoạn 0

Bạn hoàn thành Giai đoạn 0 khi tick được **TẤT CẢ** ô dưới đây. Hãy thành thật với chính mình.

### 🧠 Mindset
- [ ] Giải thích được (bằng lời của mình) **vì sao học automation** và automation **khác** manual thế nào.
- [ ] Nêu được ít nhất **3 tiêu chí** để quyết định một case **có nên** automate không.
- [ ] Kể được ít nhất **2 kỳ vọng sai** về automation mà mình đã bỏ.

### 💻 Môi trường (macOS hoặc Windows)
- [ ] Trình cài đặt chạy được: `brew --version` (macOS) **hoặc** `winget --version` (Windows) — nếu bạn dùng nó.
- [ ] `java -version` ra bản **17+** (và `javac -version` chạy được).
- [ ] `git --version` chạy được và đã `git config` tên + email.
- [ ] `mvn -version` chạy được, dòng **Java version** khớp JDK đã cài.
- [ ] Mở được **IntelliJ IDEA Community** và **chạy được chương trình "Hello World"** in ra màn hình.

### 🧱 HTML
- [ ] Đọc được một thẻ HTML và chỉ ra: tên thẻ, các thuộc tính, nội dung.
- [ ] Giải thích được vai trò của `id`, `class`, `name`, `data-*` và **vì sao `id`/`data-*` tốt cho automation**.

### 🎯 CSS Selector
- [ ] Viết được selector theo `#id`, `.class`, `tag`, `[attr=value]`.
- [ ] Phân biệt được **con trực tiếp (`>`)** và **hậu duệ (dấu cách)**.
- [ ] Với một element bất kỳ, viết được **ít nhất 2 selector đúng** và chọn được cái bền hơn.

### 🌳 DOM
- [ ] Giải thích được DOM là **cây cấu trúc** dựng từ HTML.
- [ ] Nêu đúng quan hệ cha / con / anh em / hậu duệ trên một ví dụ.
- [ ] Giải thích được **vì sao Playwright thao tác trên DOM** (chứ không phải trên hình ảnh).

### 🔧 Chrome DevTools
- [ ] **Inspect** được một element bất kỳ và đọc đúng thuộc tính của nó (tab Elements).
- [ ] **Test được selector** bằng `$$("...")` / `document.querySelectorAll("...")` trong Console và đọc được **số element khớp**.
- [ ] Mở được tab **Network**, thực hiện một hành động và tìm được request tương ứng, đọc được **Status Code**.

### 🛠️ Thực hành SauceDemo (bài chốt)
- [ ] Tự F12 tìm được selector của **ô username, ô password, nút login** trên SauceDemo.
- [ ] Viết được **5 CSS selector khác nhau** cùng trỏ tới một element và test đúng trong Console (Bài tập 8).

> 🎉 **Tick hết? Chúc mừng — bạn đã hoàn thành Giai đoạn 0!** Bạn đã có xưởng làm việc sẵn sàng, tư duy đúng, và — quan trọng nhất — **đọc được cấu trúc bên trong của trang web**. Đây chính là nền tảng mà nhiều người bỏ qua rồi vấp ngã ở Playwright. Bạn đã đi đúng đường. Tiếp theo: **Giai đoạn 1 — Java cơ bản cho Tester.** 🚀

---

<a id="13"></a>
## 📚 Phần 13 — Tài nguyên tham khảo

**Cài đặt & công cụ (macOS):**
- Homebrew (trình cài đặt): [https://brew.sh/](https://brew.sh/)
- Eclipse Adoptium Temurin (JDK): [https://adoptium.net/temurin/releases/](https://adoptium.net/temurin/releases/)
- IntelliJ IDEA Community: [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/)
- Apache Maven: [https://maven.apache.org/](https://maven.apache.org/)
- Git: [https://git-scm.com/](https://git-scm.com/)

**HTML / CSS / DOM (học nền tảng):**
- MDN — HTML cơ bản (chuẩn mực nhất): [https://developer.mozilla.org/vi/docs/Web/HTML](https://developer.mozilla.org/vi/docs/Web/HTML)
- MDN — CSS Selectors: [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors)
- MDN — Giới thiệu về DOM: [https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- W3Schools — HTML: [https://www.w3schools.com/html/](https://www.w3schools.com/html/)
- W3Schools — CSS Selectors Reference: [https://www.w3schools.com/cssref/css_selectors.php](https://www.w3schools.com/cssref/css_selectors.php)
- Trò chơi luyện CSS Selector (rất vui, nên chơi): [https://flukeout.github.io/](https://flukeout.github.io/)

**Chrome DevTools:**
- Tài liệu chính thức DevTools: [https://developer.chrome.com/docs/devtools](https://developer.chrome.com/docs/devtools)
- Console utilities (`$`, `$$`...): [https://developer.chrome.com/docs/devtools/console/utilities](https://developer.chrome.com/docs/devtools/console/utilities)

**Trang luyện tập (sân tập cả khóa):**
- SauceDemo: [https://www.saucedemo.com/](https://www.saucedemo.com/)
- The-Internet Herokuapp: [https://the-internet.herokuapp.com/](https://the-internet.herokuapp.com/)
- Automation Exercise: [https://automationexercise.com/](https://automationexercise.com/)
- OrangeHRM demo: [https://opensource-demo.orangehrmlive.com/](https://opensource-demo.orangehrmlive.com/)

**Đón đầu (chưa cần đọc kỹ, để bookmark):**
- Playwright Java Docs: [https://playwright.dev/java/docs/intro](https://playwright.dev/java/docs/intro)

---

> 💪 **Lời nhắn cuối:** Giai đoạn 0 nghe có vẻ "chưa code gì" nhưng thực ra là giai đoạn quyết định. Người đi đường dài trong automation là người **đọc được DOM trong giấc ngủ**. Mỗi khi mở một trang web bất kỳ, hãy tập phản xạ nhấn F12, inspect vài element, thử vài selector trong Console. Biến nó thành thói quen — và Playwright sau này sẽ nhẹ như trở bàn tay. Hẹn gặp ở Giai đoạn 1! ☕
```

*Học liệu Giai đoạn 0 — Khóa Automation Test với Java + Playwright.*
