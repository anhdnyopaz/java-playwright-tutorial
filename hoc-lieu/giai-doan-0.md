# 📱 Giai đoạn 0 — Mindset, Môi trường & Nền tảng UI Android

> **Học liệu chính thức — Khóa Automation Test Mobile với Java + Appium**
> **Đối tượng:** Tester (manual) chưa biết code, mới bắt đầu học automation **mobile**.
> **Nền tảng trọng tâm:** **Android** (iOS cần Mac + Xcode, sẽ học sau).
> **Hệ điều hành máy học:** hướng dẫn cài đặt cho **CẢ macOS VÀ Windows**.
> **Thời lượng gợi ý:** ~1–2 tuần (phần cài môi trường mobile dài hơn web — cứ đi chậm cho chắc; nền tảng này quyết định 80% việc bạn có viết được locator tốt sau này hay không).

---

## 📖 Mục lục

1. [Giai đoạn 0 dạy gì và tại sao quan trọng](#0)
2. [Phần 1 — Mindset Mobile Automation (Bài đọc)](#1)
3. [Phần 2 — Cài đặt môi trường](#2)
   - [Phần 2A — macOS](#2a)
   - [Phần 2W — Windows](#2w)
   - [Phần 2C — Chung cho cả hai hệ (AVD, Appium, Inspector, APK)](#2c)
4. [Phần 3 — Nền tảng cấu trúc UI Android (View & cây UI)](#3)
5. [Phần 4 — Thuộc tính định danh & Chiến lược locator Appium](#4)
6. [Phần 5 — Dùng Appium Inspector (thay cho F12)](#5)
7. [Phần 6 — Bài thực hành có hướng dẫn: Sauce Labs My Demo App](#6)
8. [Phần 7 — Bài tập tự làm](#7)
9. [Phần 8 — Quiz tự đánh giá](#8)
10. [Phần 9 — Đáp án bài tập](#9)
11. [Phần 10 — Đáp án quiz](#10)
12. [Phần 11 — Checklist Milestone Giai đoạn 0](#11)
13. [Phần 12 — Tài nguyên tham khảo](#12)

---

<a id="0"></a>
## 🎯 Giai đoạn 0 dạy gì và tại sao quan trọng

Bạn sắp học viết code để máy tính **tự mở app, tự chạm, tự nhập liệu, tự vuốt, tự kiểm tra** trên điện thoại thay bạn. Nhưng trước khi máy làm được điều đó, **bạn** phải chỉ cho nó: "Hãy chạm vào **cái nút này**, gõ vào **ô này**". Vấn đề là máy không nhìn màn hình điện thoại bằng mắt như bạn — nó nhìn app qua **cấu trúc bên trong** (cây các View của Android). Vì vậy:

> **Muốn ra lệnh cho máy thao tác trên app, bạn phải biết đọc "bản đồ bên trong" của màn hình app đó.**

Giai đoạn 0 chính là học đọc bản đồ đó, cộng với dựng "xưởng làm việc" (môi trường mobile) và "tư duy nghề" (mindset). Cụ thể bạn sẽ:

| Mục tiêu | Bạn sẽ làm được |
|----------|-----------------|
| **Mindset** | Hiểu automation mobile để làm gì, khi nào nên/không nên dùng, biết đặc thù test mobile, bỏ được kỳ vọng sai |
| **Môi trường** | Cài JDK, IntelliJ, Android Studio + SDK, tạo máy ảo (emulator), cài Appium 2 + driver, chạy được trên macOS **hoặc** Windows |
| **Cấu trúc UI Android** | Hiểu app là một **cây View**, đọc được thuộc tính của một element bất kỳ |
| **Locator Appium** | Tự viết được "địa chỉ" trỏ tới một element bằng `AppiumBy` |
| **Appium Inspector** | "Soi" cây UI của app, đọc `resource-id`/`content-desc`, tự lấy locator |

Đây **chưa phải** lúc viết bộ test Java hoàn chỉnh. Đây là lúc xây móng. Móng chắc thì nhà cao mới không sập.

> 🌐➡️📱 **Nếu bạn từng nghe về automation web (Selenium/Playwright):** tin vui là 80% tư duy giống nhau. Chỗ khác biệt lớn nhất: web thao tác trên **DOM/HTML** trong trình duyệt, còn mobile thao tác trên **cây View** của app Android. Ta sẽ học chính cây View đó ở Phần 3–5.

---

<a id="1"></a>
## 🧠 Phần 1 — Mindset Mobile Automation (Bài đọc)

### 1.1. Tại sao một tester giỏi nên học automation mobile?

Hãy tưởng tượng một ngày làm việc của bạn với vai trò manual mobile tester. Team vừa ra bản build mới của app. Bạn cầm chiếc điện thoại, mở checklist regression 80 test case — mở app, đăng nhập, tìm sản phẩm, thêm giỏ hàng, thanh toán, đổi mật khẩu, đăng xuất... Bạn chạm, vuốt, nhập, so sánh, chụp màn hình, ghi lại. Rồi sếp nói: "Test lại giúp anh trên con Samsung màn to, con Xiaomi Android 11, và con Pixel Android 14 nữa nhé." Thế là bạn cầm **3 máy**, làm lại **cùng 80 case** cho **từng máy**. Mất 2–3 ngày. Xong xuôi thì dev báo: "Anh vừa fix thêm một bug, em test lại từ đầu giúp nhé."

Việc đó **cần thiết** — nhưng nó lặp đi lặp lại, nhàm chán, và **con người rất dễ sai khi làm việc lặp lại**. Đến máy thứ 3, case thứ 60, bạn mỏi tay, mắt lướt qua, bỏ sót một lỗi hiển thị nhỏ. Đó không phải lỗi của bạn — đó là giới hạn tự nhiên của con người.

Bây giờ tưởng tượng khác đi: bạn viết một lần bộ script Appium, gõ một lệnh, đi pha cà phê. Script tự bật emulator (hoặc nhiều emulator/thiết bị), tự cài app, tự chạy hết 80 case, chụp màn hình chỗ lỗi, xuất báo cáo xanh/đỏ. Bạn dùng thời gian được giải phóng để làm việc mà **máy không làm được**: test cảm giác vuốt/chạm có mượt không, khám phá (exploratory), test tình huống lắt léo trên thiết bị thật.

> **Automation không lấy mất việc của bạn. Nó lấy đi phần việc tẻ nhạt nhất (bấm đi bấm lại trên nhiều máy), để trả lại cho bạn phần việc thú vị và có giá trị nhất.**

Và về mặt sự nghiệp: automation tester mobile ở Việt Nam hiện còn **hiếm hơn** cả automation web, nên lương và cơ hội rất tốt — bạn vừa hiểu **nghiệp vụ kiểm thử**, vừa biết **lập trình**, lại còn nắm **đặc thù mobile** mà thị trường luôn thiếu người.

### 1.2. Automation vs Manual trên mobile — không phải cuộc chiến, mà là phân công

Nhiều người mới hiểu lầm rằng "học automation là để thay thế manual". Sai. Hai bên **bổ sung** cho nhau, đặc biệt trên mobile — nơi cảm giác chạm/vuốt và trải nghiệm rất quan trọng:

| Tiêu chí | Manual Mobile Test | Automation Mobile Test |
|----------|--------------------|------------------------|
| **Mạnh ở** | Cảm nhận UX/gesture, khám phá, test trên thiết bị thật, camera/cảm biến, case mới | Lặp lại, regression, chạy trên **nhiều thiết bị/độ phân giải**, chạy nhiều lần |
| **Yếu ở** | Chậm khi lặp trên nhiều máy, dễ mệt/sai, tốn người & tốn thiết bị | Không "cảm" được mượt/giật, khó test tính năng đang thay đổi, tốn công dựng ban đầu |
| **Tốc độ** | Chậm | Rất nhanh (nhất là khi chạy song song nhiều máy ảo) |
| **Chi phí ban đầu** | Thấp | Cao (phải dựng môi trường + viết code trước) |
| **Chi phí về sau** | Cao (mỗi bản build lại làm tay trên từng máy) | Thấp (chạy lại gần như miễn phí) |
| **Phù hợp nhất** | Test lần đầu, cảm quan, tính năng đang thay đổi | Regression đã ổn định, chạy đi chạy lại trên nhiều cấu hình |

**Một ví von:** Manual test mobile giống lái thử một chiếc xe — cần cảm giác vô-lăng, độ êm, tiếng máy. Automation test giống dây chuyền kiểm tra trong nhà máy ô tô — mỗi chiếc xe chạy qua trạm kiểm đèn, kiểm phanh tự động, hàng trăm chiếc một giờ không mệt. Bạn cần **cả hai** trong một xưởng chuyên nghiệp.

### 1.3. Không phải test case nào cũng nên automate

Đây là tư duy **quan trọng nhất** của người làm automation chuyên nghiệp. Người mới thường mắc bệnh "automate tất cả mọi thứ" và lãnh hậu quả: tốn hàng tuần viết script cho những case chẳng bao giờ chạy lại, hoặc script gãy liên tục vì app còn đang thay đổi.

**Tiêu chí ƯU TIÊN automate một case** (càng nhiều dấu ✅ càng nên automate):

- ✅ **Chạy lặp lại nhiều lần** (regression, smoke test mỗi lần build).
- ✅ **Ổn định** — màn hình/luồng đã "chốt", ít thay đổi giao diện/logic.
- ✅ **Quan trọng / rủi ro cao** — luồng nghiệp vụ cốt lõi (đăng nhập, thanh toán, đặt hàng).
- ✅ **Tốn công làm tay** — nhiều bước, hoặc phải chạy lại trên **nhiều thiết bị/độ phân giải**.
- ✅ **Data-driven** — cùng một luồng nhưng chạy với 50 bộ dữ liệu.
- ✅ **Kết quả rõ ràng, kiểm tra được bằng logic** (đúng/sai xác định, không mơ hồ).

**Tiêu chí NÊN CÂN NHẮC / KHÔNG nên automate (ít nhất là chưa):**

- ❌ **Case chỉ chạy một lần** (test một tính năng nhỏ sắp bị gỡ).
- ❌ **Màn hình đang thay đổi liên tục** — viết xong sáng, chiều gãy.
- ❌ **Cần đánh giá cảm quan** — "animation này có mượt không?", "màu này có đẹp không?", "chạm có đã tay không?".
- ❌ **Phụ thuộc phần cứng thật** — camera, vân tay, khuôn mặt, NFC, cảm biến, cuộc gọi thật... (emulator không mô phỏng tốt).
- ❌ **Captcha, OTP thật, sinh trắc học** — vốn được thiết kế để chặn máy.

> **Câu hỏi vàng trước khi automate một case:** *"Case này sẽ được chạy lại bao nhiêu lần, trên bao nhiêu thiết bị? Nó có ổn định không? Nếu tôi bỏ 3 giờ viết script, tôi có tiết kiệm được nhiều hơn 3 giờ trong tương lai không?"* Nếu câu trả lời là "chỉ chạy 1 lần" hoặc "màn hình còn đổi liên tục" → khoan automate.

### 1.4. Đặc thù & thách thức RIÊNG của test mobile (khác web ở đây!)

Test mobile có những thử thách mà test web ít gặp. Biết trước để không bị "sốc":

1. **Rừng thiết bị (device fragmentation).** Android có **hàng nghìn** kiểu máy: Samsung, Xiaomi, Oppo, Pixel... mỗi hãng lại tùy biến giao diện (One UI, MIUI...). Một app chạy đẹp trên Pixel có thể vỡ layout trên Samsung. → Automation giúp bạn chạy **cùng bộ test trên nhiều máy** dễ dàng.

2. **Nhiều độ phân giải & kích thước màn hình.** Điện thoại nhỏ, điện thoại to, máy tính bảng... Vị trí (toạ độ x,y) của một nút **khác nhau** trên mỗi máy. → Đây là lý do **tuyệt đối tránh** click theo toạ độ cố định; phải dùng **locator** (định danh element) — ta học ở Phần 3–5.

3. **Nhiều phiên bản Android (OS version).** Android 10, 11, 12, 13, 14... hành vi khác nhau (quyền, thông báo, cử chỉ điều hướng). → Cần test trên nhiều API level.

4. **Cử chỉ (gesture).** Web chủ yếu là click. Mobile có **chạm (tap), chạm giữ (long press), vuốt (swipe), kéo-thả, chụm/mở (pinch zoom), cuộn (scroll)**. Automation mobile phải xử lý các cử chỉ này (học sâu ở giai đoạn sau).

5. **Quyền (permission) & popup hệ thống.** App thường xin quyền: vị trí, camera, thông báo, danh bạ... Các hộp thoại này **của hệ điều hành**, không phải của app, và **nhảy ra bất chợt** → dễ làm gãy test nếu không xử lý.

6. **Loại app khác nhau:** **Native** (viết thuần cho Android), **Hybrid** (web nhúng trong app — có WebView), **Web app** (mở trên trình duyệt di động). Cách "soi" element mỗi loại hơi khác. Khóa này tập trung app **Native** Android trước.

7. **Trạng thái thiết bị.** Xoay ngang/dọc, cuộc gọi đến, hết pin, mất mạng, app chạy nền rồi quay lại... đều là tình huống cần nghĩ tới.

8. **Emulator vs thiết bị thật.** Emulator (máy ảo) tiện, miễn phí, dễ tự động hoá → ta dùng để **học**. Nhưng nó không thay được thiết bị thật ở khoản hiệu năng, cảm biến, camera. Thực tế thường chạy automation trên **cả hai**.

> 🧩 **Chốt lại:** So với web, mobile "khó" hơn ở **sự đa dạng thiết bị và cử chỉ**. Nhưng đừng sợ — Appium + locator tốt sẽ giúp bạn viết **một** bộ test chạy được trên nhiều máy. Nền tảng của việc đó chính là biết chọn **locator bền** (Phần 4), thứ bạn sắp học.

### 1.5. Những kỳ vọng SAI cần bỏ ngay hôm nay

Người mới bước vào automation mobile thường mang theo vài niềm tin sai lầm, khiến họ nản hoặc đi sai đường. Bỏ chúng đi:

1. **"Automation là chạm chuột/record lại thao tác, không cần biết code."**
   ❌ Sai. **Automation LÀ lập trình.** Bạn sẽ viết code Java thật với vòng lặp, hàm, class. Công cụ record chỉ giúp lúc đầu, nhưng script tạo ra thường mong manh, click theo toạ độ, gãy ngay khi đổi máy. Muốn đi xa, phải code.

2. **"Cứ dùng toạ độ (x, y) để chạm cho nhanh."**
   ❌ Sai — và đây là bẫy chết người của mobile. Toạ độ đổi theo từng độ phân giải/máy. Chạm toạ độ cố định = test gãy ngay trên máy khác. **Luôn dùng locator** (`resource-id`, `content-desc`...), không dùng toạ độ.

3. **"Học automation là hết flaky test, test luôn xanh."**
   ❌ Sai. Test mobile vẫn "chập chờn" (flaky) — do app load chậm, do animation, do popup quyền nhảy ra, do emulator lag. **Một phần lớn kỹ năng automation là học viết test ỔN ĐỊNH** (chờ đúng cách). Đây là điều phân biệt junior với người đi làm được.

4. **"Viết test một lần là xong, không cần đụng lại."**
   ❌ Sai. App thay đổi thì test phải cập nhật theo. Test là **code sống**, cần bảo trì. Vì vậy ta học viết test **dễ bảo trì** (Page Object Model, đặt tên rõ ràng...) ngay từ đầu.

5. **"Tôi không biết code, chắc không học nổi."**
   ❌ Sai. Bạn đã có thứ quý nhất mà lập trình viên thuần thường thiếu: **tư duy kiểm thử** — biết đặt câu hỏi "cái gì có thể hỏng?". Code là kỹ năng học được. Hàng nghìn manual tester đã chuyển thành automation engineer giỏi. Đi từng bước, mỗi ngày viết một chút, sẽ tới.

> **Nguyên tắc vàng của cả khóa:** Học automation = **code mỗi ngày**. Đọc 10 tutorial không bằng tự tay mở Appium Inspector soi một element và làm nó chạy. Ngay ở Giai đoạn 0 này, hãy **thực sự cài môi trường, bật emulator, mở Inspector soi app** — đừng chỉ đọc.

---

<a id="2"></a>
## 💻 Phần 2 — Cài đặt môi trường

> ⚠️ **Đây là phần dài & quan trọng nhất của Giai đoạn 0.** Cài môi trường mobile phức tạp hơn web (thêm Android Studio, SDK, emulator, Appium server). Đừng nản — làm từng bước, kiểm tra từng bước. Xong phần này là bạn đã vượt qua chỗ nhiều người bỏ cuộc.

### 2.0. Bức tranh tổng thể: các mảnh ghép của một "xưởng automation mobile"

Trước khi cài, hãy hiểu **các mảnh ghép** kết nối với nhau ra sao. Nắm sơ đồ này rồi thì mỗi bước cài đặt sau sẽ có nghĩa:

```
[ Code test Java (IntelliJ) ]
        │  gửi lệnh "tìm nút Login, chạm vào"
        ▼
[ Appium Server  (http://127.0.0.1:4723) ]   ← cài bằng Node.js/npm
        │  dịch lệnh sang ngôn ngữ Android
        ▼
[ Driver UiAutomator2 ]                        ← cài bằng: appium driver install uiautomator2
        │  điều khiển thiết bị qua adb
        ▼
[ adb (Android Debug Bridge) ]                 ← đi kèm Android SDK (platform-tools)
        │
        ▼
[ Emulator (máy ảo Android)  hoặc  điện thoại thật ]   ← tạo bằng Android Studio Device Manager
        │
        ▼
[ App cần test (file .apk) ]                    ← cài vào máy ảo bằng: adb install app.apk
```

**Đọc sơ đồ:** Code Java của bạn không nói chuyện trực tiếp với điện thoại. Nó gửi lệnh tới **Appium Server**. Server nhờ **driver UiAutomator2** dịch lệnh, driver dùng **adb** để điều khiển **emulator/thiết bị** đang chạy **app** của bạn. Mỗi mảnh là một thứ ta phải cài.

**Danh sách cần cài (tick dần khi làm):**

| # | Thành phần | Vai trò |
|---|-----------|---------|
| 1 | **JDK 17+** | Chạy code Java (và cả Appium/Android đều cần Java) |
| 2 | **IntelliJ IDEA Community** | IDE để viết code test (dùng nhiều ở giai đoạn sau) |
| 3 | **Android Studio + Android SDK** | Cho ta `adb`, emulator, và các thư viện Android |
| 4 | **Biến môi trường `ANDROID_HOME` + PATH** | Để gõ được lệnh `adb`, `emulator` ở bất kỳ đâu |
| 5 | **Máy ảo Android (AVD/Emulator)** | "Điện thoại giả" để test |
| 6 | **Node.js** | Nền tảng để cài Appium |
| 7 | **Appium 2 + driver UiAutomator2** | "Bộ não" điều khiển thiết bị |
| 8 | **Appium Inspector** | Công cụ "soi" element (như F12 của web) |
| 9 | **APK mẫu** | App để luyện tập |

> 👉 **Chọn phần của bạn:** Dùng **macOS** thì làm **[Phần 2A](#2a)**. Dùng **Windows** thì làm **[Phần 2W](#2w)**. Sau đó **cả hai** cùng làm **[Phần 2C](#2c)** (tạo emulator, cài Appium, Inspector, APK) — phần này gần như giống nhau cho hai hệ.

---

<a id="2a"></a>
## 🍎 Phần 2A — Cài đặt trên macOS

> 🍎 Phần này dành cho **macOS**. Dùng Windows thì nhảy tới **[Phần 2W](#2w)**. Xong phần OS của mình, cả hai cùng gặp nhau ở **[Phần 2C](#2c)**.

> 💡 **Terminal là gì?** Là ứng dụng cho phép bạn gõ lệnh ra cho máy tính thay vì click chuột. Trên macOS, mở bằng `Cmd + Space` → gõ `Terminal` → Enter. Đừng sợ — bạn chủ yếu copy-paste các lệnh dưới đây.

### 2A.1. Cài Homebrew (nền tảng để cài mọi thứ khác)

Homebrew giống như "App Store cho terminal". Cài nó trước, mọi thứ sau sẽ dễ. Mở Terminal và dán lệnh chính thức từ [brew.sh](https://brew.sh/):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Nó sẽ hỏi mật khẩu máy Mac (gõ vào, **màn hình không hiện ký tự** — đó là bình thường, cứ gõ rồi Enter).

**Máy Mac chip Apple Silicon (M1/M2/M3/M4):** sau khi cài xong, Homebrew thường in ra 2 lệnh ở mục *Next steps* để "đăng ký" brew vào hệ thống. Thường là:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Kiểm tra:

```bash
brew --version
```

Thấy `Homebrew 4.x.x` là ✅.

### 2A.2. Cài JDK 17+ (Java Development Kit)

Automation Java **và** cả Appium/Android đều cần Java. Dùng bản **Temurin** của Eclipse Adoptium (miễn phí, chuẩn cho automation):

```bash
brew install --cask temurin@17
```

> 💡 Giáo trình yêu cầu **17 trở lên**. Bản 17 hoặc 21 (LTS) đều được. Muốn 21: `brew install --cask temurin@21`.

**Kiểm tra — bước QUAN TRỌNG:**

```bash
java -version
javac -version
```

Thấy số phiên bản **17 trở lên** là ✅. `javac` in ra được nghĩa là bộ **biên dịch** đã sẵn sàng.

> ⚠️ **Nếu `java -version` báo "command not found" hoặc ra bản cũ (1.8):** đóng hẳn Terminal rồi mở lại. Nếu vẫn lỗi, thêm dòng sau vào cuối `~/.zshrc` (mở bằng `open -e ~/.zshrc`), lưu, mở Terminal mới:
> ```bash
> export JAVA_HOME=$(/usr/libexec/java_home -v 17)
> ```
> Lệnh `/usr/libexec/java_home -V` (chữ V hoa) liệt kê mọi JDK đang có.

### 2A.3. Cài IntelliJ IDEA Community (IDE viết code)

**IDE** là phần mềm giúp bạn viết code: tô màu cú pháp, gợi ý code, báo lỗi khi gõ, chạy/debug bằng một nút. IntelliJ IDEA Community Edition là bản **miễn phí** tốt nhất cho Java.

```bash
brew install --cask intellij-idea-ce
```

(`ce` = Community Edition, miễn phí. Đừng cài `intellij-idea` không có `-ce` vì đó là bản trả phí.)

Mở thử (`Cmd + Space` → gõ `IntelliJ`). Vào được màn hình *Welcome to IntelliJ IDEA* là ✅.

> 💡 **Git & Maven:** khóa mobile này bạn cũng sẽ cần **Git** (`brew install git`) và **Maven** (`brew install maven`) ở giai đoạn sau — cài luôn cho tiện, kiểm tra bằng `git --version` và `mvn -version`. Ở Giai đoạn 0 hai thứ này chưa bắt buộc, nên đây chỉ là ghi chú.

### 2A.4. Cài Android Studio + Android SDK

Đây là mảnh ghép **quan trọng nhất** riêng của mobile. Android Studio đem lại cho ta: **Android SDK** (thư viện Android), **platform-tools** (chứa `adb`), **emulator**, và **Device Manager** để tạo máy ảo.

**Cài Android Studio:**

```bash
brew install --cask android-studio
```

(Hoặc tải thủ công tại [https://developer.android.com/studio](https://developer.android.com/studio), mở file `.dmg`, kéo vào Applications. Nhớ chọn đúng bản chip **Apple Silicon** hoặc **Intel**.)

**Chạy trình cài đặt SDK lần đầu:**

1. Mở **Android Studio**. Lần đầu nó chạy **Setup Wizard** → chọn **Standard** → Next → Finish. Nó sẽ tải về **Android SDK**, **SDK Platform** (một phiên bản Android), và **emulator**. Bước này tải khá nặng (vài GB) — kiên nhẫn.
2. Sau khi vào màn hình chào, mở **SDK Manager**: bấm **More Actions** (hoặc biểu tượng ⚙️) → **SDK Manager**. (Trong project đang mở thì vào **Settings → Languages & Frameworks → Android SDK**.)
3. Tab **SDK Platforms**: tick chọn ít nhất **một** phiên bản Android, ví dụ **Android 14 (API 34)** hoặc **Android 13 (API 33)**.
4. Tab **SDK Tools**: đảm bảo các mục sau được **tick** (bấm *Apply* để tải):
   - ✅ **Android SDK Platform-Tools** (chứa `adb` — bắt buộc!)
   - ✅ **Android SDK Build-Tools**
   - ✅ **Android Emulator**
   - ✅ **Android SDK Command-line Tools (latest)**
5. Ghi nhớ **Android SDK Location** hiện ở đầu cửa sổ SDK Manager — thường là:
   ```
   /Users/<tên-bạn>/Library/Android/sdk
   ```
   Ta cần đường dẫn này ở bước sau.

### 2A.5. Cấu hình biến môi trường `ANDROID_HOME` + PATH (zsh)

Để gõ được `adb`, `emulator` ở **bất kỳ thư mục nào** trong Terminal, hệ thống cần biết chúng nằm đâu. Ta khai báo qua biến môi trường trong file `~/.zshrc` (macOS mới dùng shell **zsh**).

Mở file cấu hình:

```bash
open -e ~/.zshrc
```

Thêm các dòng sau vào **cuối file** (nếu SDK của bạn nằm chỗ khác, sửa lại đường dẫn cho khớp mục *Android SDK Location* ở bước trên):

```bash
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin
```

> 💡 `ANDROID_HOME` là "địa chỉ nhà" của Android SDK; ba dòng `PATH` thêm lần lượt: `adb` (platform-tools), `emulator`, và các công cụ dòng lệnh. Appium **cần** biến `ANDROID_HOME` để tìm SDK.

**Lưu file, rồi nạp lại cấu hình** (hoặc đóng/mở Terminal):

```bash
source ~/.zshrc
```

**Kiểm tra:**

```bash
echo $ANDROID_HOME        # phải in ra đường dẫn SDK
adb --version             # phải in ra "Android Debug Bridge version 1.x.x"
emulator -version         # in ra version emulator
```

Cả ba in ra kết quả (không báo "command not found") là ✅. Nếu `adb` báo not found → kiểm tra lại đường dẫn `ANDROID_HOME` có đúng thư mục SDK không, và đã `source ~/.zshrc` chưa.

### 2A.6. Cài Node.js (nền tảng cho Appium)

Appium 2 chạy trên **Node.js**. Cài bản LTS:

```bash
brew install node
node -v      # nên là v18 trở lên
npm -v
```

Thấy version in ra là ✅. `npm` (Node Package Manager) là công cụ ta dùng để cài Appium ở Phần 2C.

> ✅ **Xong phần macOS!** Bạn đã có JDK, IntelliJ, Android Studio + SDK (có `adb`), biến môi trường, và Node.js. Giờ nhảy tới **[Phần 2C](#2c)** để tạo emulator và cài Appium (chung cho cả hai hệ điều hành).

---

<a id="2w"></a>
## 🪟 Phần 2W — Cài đặt trên Windows

> 🪟 Phần này dành cho **Windows 10 / 11**. Dùng macOS thì làm Phần 2A ở trên. Xong phần OS của mình, cả hai cùng gặp nhau ở **[Phần 2C](#2c)**.

> 💡 **Terminal trên Windows là gì?** Là **PowerShell** hoặc **Command Prompt (cmd)**. Khuyến nghị **PowerShell**: Start → gõ `PowerShell` → mở **Windows PowerShell**. Vài lệnh cài đặt nên chạy quyền quản trị: chuột phải PowerShell → **Run as administrator**.

### 2W.1. Chọn cách cài: winget (khuyến nghị) hay tải file thủ công

Windows 11 và Windows 10 (bản mới) có sẵn **winget** — trình cài đặt dòng lệnh, giống Homebrew của macOS. Kiểm tra:

```powershell
winget --version
```

- In ra `v1.x.x` → dùng **Cách A (winget)**, nhanh gọn nhất.
- Báo lỗi "không nhận lệnh" → cài **App Installer** từ Microsoft Store, hoặc dùng **Cách B (tải file thủ công)** — cũng ổn.

### 2W.2. Cài JDK 17+ (Java Development Kit)

**Cách A — winget:**

```powershell
winget install EclipseAdoptium.Temurin.17.JDK
```

(Muốn bản 21: `winget install EclipseAdoptium.Temurin.21.JDK`. Yêu cầu là **17 trở lên**.)

**Cách B — tải file cài từ Adoptium:**

1. Vào [https://adoptium.net/temurin/releases/](https://adoptium.net/temurin/releases/)
2. Chọn: **OS = Windows**, **Architecture = x64**, **Package Type = JDK**, **Version = 17 (hoặc 21)**.
3. Tải file **`.msi`**, mở lên, Next.
4. ⭐ **QUAN TRỌNG:** ở bước *Custom Setup*, bật **"Set JAVA_HOME variable"** và **"Add to PATH"** (bấm biểu tượng ổ cứng → *Will be installed on local hard drive*). Bật 2 cái này để **khỏi phải** chỉnh biến môi trường thủ công.
5. Next → Install.

**Kiểm tra — mở PowerShell MỚI** (để nạp PATH mới):

```powershell
java -version
javac -version
```

Thấy số phiên bản **17 trở lên** là ✅.

> ⚠️ **Nếu báo "java is not recognized":** biến môi trường chưa set. Sửa thủ công: Start → gõ **"environment variables"** → **Edit the system environment variables** → **Environment Variables…** → trong **System variables** tạo `JAVA_HOME` trỏ tới thư mục JDK (ví dụ `C:\Program Files\Eclipse Adoptium\jdk-17.0.x-hotspot`), rồi thêm `%JAVA_HOME%\bin` vào biến **Path**. Đóng/mở lại PowerShell, thử lại.

### 2W.3. Cài IntelliJ IDEA Community (IDE viết code)

**Cách A — winget:**

```powershell
winget install JetBrains.IntelliJIDEA.Community
```

**Cách B — tải thủ công:** vào [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/) → tab **Windows** → mục **Community Edition** (KHÔNG phải Ultimate — bản trả phí) → tải `.exe` → chạy → tick *Create Desktop Shortcut* → Install.

Mở IntelliJ từ Start Menu, vào được màn hình *Welcome* là ✅.

> 💡 **Git & Maven** cũng sẽ cần ở giai đoạn sau: `winget install Git.Git` và `winget install Apache.Maven`. Ở Giai đoạn 0 chưa bắt buộc.

### 2W.4. Cài Android Studio + Android SDK

Android Studio đem lại **Android SDK**, **platform-tools** (chứa `adb`), **emulator**, và **Device Manager**.

**Cài Android Studio:**

**Cách A — winget:**

```powershell
winget install Google.AndroidStudio
```

**Cách B — tải thủ công:** [https://developer.android.com/studio](https://developer.android.com/studio) → tải file `.exe` → chạy → Next theo mặc định → Install.

**Chạy trình cài đặt SDK lần đầu:**

1. Mở **Android Studio**. Lần đầu chạy **Setup Wizard** → chọn **Standard** → Next → Finish. Nó tải về **Android SDK**, **SDK Platform**, **emulator** (vài GB — kiên nhẫn).
2. Ở màn hình chào, mở **SDK Manager**: **More Actions** (hoặc ⚙️) → **SDK Manager**.
3. Tab **SDK Platforms**: tick ít nhất **một** phiên bản, ví dụ **Android 14 (API 34)** hoặc **Android 13 (API 33)**.
4. Tab **SDK Tools**: đảm bảo được **tick** rồi bấm *Apply* để tải:
   - ✅ **Android SDK Platform-Tools** (chứa `adb` — bắt buộc!)
   - ✅ **Android SDK Build-Tools**
   - ✅ **Android Emulator**
   - ✅ **Android SDK Command-line Tools (latest)**
5. Ghi nhớ **Android SDK Location** hiện ở đầu cửa sổ — trên Windows thường là:
   ```
   C:\Users\<tên-bạn>\AppData\Local\Android\Sdk
   ```
   Ta cần đường dẫn này ở bước sau. (`AppData` là thư mục ẩn — cứ copy nguyên đường dẫn trên là được.)

### 2W.5. Cấu hình biến môi trường `ANDROID_HOME` + PATH (Environment Variables)

Để gõ được `adb`, `emulator` ở bất kỳ đâu, ta khai báo biến môi trường qua giao diện Windows:

1. Bấm **Start** → gõ **"environment variables"** → mở **"Edit the system environment variables"** → nút **Environment Variables…**
2. Ở mục **User variables** (hoặc System variables), bấm **New**:
   - **Variable name:** `ANDROID_HOME`
   - **Variable value:** `C:\Users\<tên-bạn>\AppData\Local\Android\Sdk` (đúng theo *Android SDK Location* ở bước trên)
3. Vẫn trong mục đó, chọn biến **Path** → **Edit** → **New**, thêm lần lượt **ba** dòng sau (mỗi dòng một entry):
   ```
   %ANDROID_HOME%\platform-tools
   %ANDROID_HOME%\emulator
   %ANDROID_HOME%\cmdline-tools\latest\bin
   ```
4. Bấm **OK** đóng hết các cửa sổ.
5. ⭐ **Đóng hẳn PowerShell rồi mở lại** (bắt buộc — để nạp biến mới).

**Kiểm tra (PowerShell mới):**

```powershell
echo $env:ANDROID_HOME     # phải in ra đường dẫn SDK
adb --version              # phải in ra "Android Debug Bridge version 1.x.x"
emulator -version          # in ra version emulator
```

Cả ba in ra kết quả là ✅. Nếu `adb` báo not recognized → kiểm tra lại đường dẫn `ANDROID_HOME` và nhớ đã **mở PowerShell mới** chưa.

### 2W.6. Cài Node.js (nền tảng cho Appium)

**Cách A — winget:**

```powershell
winget install OpenJS.NodeJS.LTS
```

**Cách B:** tải bản **LTS** tại [https://nodejs.org/](https://nodejs.org/) rồi chạy file cài.

**Kiểm tra (PowerShell mới):**

```powershell
node -v      # nên là v18 trở lên
npm -v
```

> 🎯 **Mẹo vàng cho Windows:** gần như MỌI lỗi "command not found / not recognized" đều do (1) chưa mở PowerShell **mới** sau khi cài/đổi biến môi trường, hoặc (2) biến Path chưa đúng. Đóng hẳn, mở lại, thử lại — trước khi nghĩ là cài hỏng.

> ✅ **Xong phần Windows!** Bạn đã có JDK, IntelliJ, Android Studio + SDK (có `adb`), biến môi trường, và Node.js. Giờ nhảy tới **[Phần 2C](#2c)** để tạo emulator và cài Appium (chung cho cả hai hệ điều hành).

---

<a id="2c"></a>
## 🔗 Phần 2C — Chung cho cả hai hệ (Emulator, Appium, Inspector, APK)

> 🍎🪟 Từ đây trở đi **giống nhau** cho macOS và Windows (chỉ khác vài chi tiết nhỏ — sẽ ghi rõ). Đảm bảo bạn đã hoàn thành Phần 2A **hoặc** 2W trước khi làm phần này.

### 2C.1. Tạo máy ảo Android (AVD) bằng Device Manager

**AVD (Android Virtual Device)** = "điện thoại giả" chạy trên máy tính bạn. Đây là nơi ta cài app và chạy test.

1. Mở **Android Studio** → ở màn hình chào bấm **More Actions** → **Virtual Device Manager** (hoặc biểu tượng điện thoại ⚙️). (Trong project đang mở: menu **Tools → Device Manager**.)
2. Bấm **Create Device** (dấu **+**).
3. **Chọn phần cứng (Select Hardware):** chọn một điện thoại phổ biến, ví dụ **Pixel 6** hoặc **Pixel 7** → **Next**.
4. **Chọn ảnh hệ điều hành (System Image):** chọn một API level bạn đã tải (ví dụ **API 34 – Android 14** hoặc **API 33**). Nếu thấy nút **Download** cạnh tên → bấm để tải ảnh hệ điều hành về (vài GB) → **Next**.
   > 💡 Ưu tiên ảnh có ghi **"Google APIs"** (có sẵn Google services) hoặc bản thường đều được để học.
5. **Đặt tên AVD** (ví dụ `Pixel_6_API_34`) → **Finish**.
6. Máy ảo mới xuất hiện trong danh sách. Bấm nút **▶ (Play)** để khởi động → một cửa sổ điện thoại Android hiện lên. Lần đầu boot khá lâu (1–3 phút), hãy chờ tới khi thấy màn hình chính Android.

> 🖥️ **Máy yếu?** Emulator ăn RAM. Nếu lag: chọn thiết bị nhỏ (Pixel 4), tắt bớt app khác. Máy Apple Silicon nên chọn ảnh **arm64**; máy Intel/Windows chọn ảnh **x86_64**. Không chạy nổi emulator thì có thể **cắm điện thoại Android thật** qua USB (bật **Developer Options → USB Debugging**) — `adb` sẽ nhận ra tương tự.

### 2C.2. Kiểm tra thiết bị bằng `adb devices`

Với emulator **đang chạy**, mở Terminal/PowerShell mới và gõ:

```bash
adb devices
```

Kết quả mong đợi:

```
List of devices attached
emulator-5554	device
```

Thấy dòng `emulator-5554   device` (hoặc một device khác kèm chữ `device`) là ✅ — máy tính đã "nhìn thấy" điện thoại/emulator.

> ⚠️ Nếu thấy `unauthorized` (khi cắm máy thật) → nhìn màn hình điện thoại, bấm **Allow** cho popup "Allow USB debugging". Nếu list rỗng → đảm bảo emulator đã boot xong, hoặc chạy `adb kill-server` rồi `adb devices` lại.

**Vài lệnh adb hữu ích (nhớ dần):**

```bash
adb devices                 # liệt kê thiết bị đang kết nối
emulator -list-avds         # liệt kê các AVD đã tạo
emulator -avd Pixel_6_API_34   # khởi động emulator bằng dòng lệnh (không cần mở Android Studio)
adb install duong-dan/app.apk  # cài một file apk vào máy đang chạy
adb uninstall com.vi.du.package  # gỡ app theo package name
```

### 2C.3. Cài Appium 2 và driver UiAutomator2

**Appium** là "bộ não" điều khiển thiết bị. Cài toàn cục (global) bằng npm:

```bash
npm install -g appium
```

**Kiểm tra:**

```bash
appium -v          # in ra ví dụ 2.x.x
```

> 📌 Số version có thể thay đổi theo thời gian — miễn là **2.x** trở lên là đúng (khóa này dùng **Appium 2**).

**Cài driver UiAutomator2** (driver để điều khiển app **Android**):

```bash
appium driver install uiautomator2
```

**Kiểm tra driver đã cài:**

```bash
appium driver list --installed
```

Thấy `uiautomator2` trong danh sách (kèm dấu tích/ghi "installed") là ✅.

> 💡 **Vì sao cần driver?** Appium chỉ là "khung". Mỗi nền tảng cần một **driver** riêng: **UiAutomator2** cho Android, **XCUITest** cho iOS (cần Mac). Ta đang học Android nên cài UiAutomator2.

### 2C.4. Chạy Appium Server

```bash
appium
```

Server khởi động và in ra dòng tương tự:

```
[Appium] Welcome to Appium v2.x.x
[Appium] Appium REST http interface listener started on http://127.0.0.1:4723
```

→ Server đang lắng nghe ở **`http://127.0.0.1:4723`** (đây chính là địa chỉ code Java và Appium Inspector sẽ kết nối tới). **Để nguyên cửa sổ này chạy** — đừng đóng. Muốn dừng server: bấm `Ctrl + C`.

> 💡 **Địa chỉ này quan trọng, nhớ kỹ:** `http://127.0.0.1:4723`. (`127.0.0.1` = "chính máy này"; `4723` là cổng mặc định của Appium 2.) Ở Appium 1.x cũ, địa chỉ có đuôi `/wd/hub` — Appium 2 **bỏ** đuôi đó, chỉ còn cổng `4723`.

### 2C.5. Kiểm tra môi trường bằng "doctor"

Appium có công cụ tự kiểm tra xem môi trường Android đã đủ chưa (Java, ANDROID_HOME, adb...). Cách khuyến nghị với Appium 2:

```bash
appium driver doctor uiautomator2
```

Nó chạy một loạt kiểm tra và in ✅/❌ cho từng mục (Java, `ANDROID_HOME`, `adb`, ...). Chỗ nào ❌ thì làm theo gợi ý sửa.

> 💡 **Cách cũ (vẫn dùng được):** công cụ `appium-doctor`:
> ```bash
> npm install -g appium-doctor
> appium-doctor --android
> ```
> Cả hai đều nhằm mục đích: xác nhận Java + Android SDK + biến môi trường đã sẵn sàng. Nếu nó báo thiếu `ANDROID_HOME` → quay lại Phần 2A.5 / 2W.5.

### 2C.6. Cài Appium Inspector (công cụ "soi" element — như F12 của web)

**Appium Inspector** là ứng dụng desktop cho phép bạn **nhìn cây UI của app** và **đọc thuộc tính từng element** (`resource-id`, `content-desc`...) — đúng vai trò mà DevTools/F12 làm cho web. Đây là công cụ bạn dùng **hằng ngày**.

1. Vào trang releases chính thức: [https://github.com/appium/appium-inspector/releases](https://github.com/appium/appium-inspector/releases)
2. Tải bản mới nhất phù hợp máy:
   - **macOS:** file `.dmg` (chọn đúng `mac` / `mac-arm64` cho chip Apple).
   - **Windows:** file `.exe` (Setup).
3. Cài như app bình thường.
   > 🍎 **macOS chặn mở app "chưa xác thực"?** Chuột phải vào app → **Open** → **Open** lần nữa. Hoặc vào **System Settings → Privacy & Security** → bấm **Open Anyway**.

Ta sẽ dùng Inspector ở **Phần 5 & 6**. Bây giờ chỉ cần cài xong.

### 2C.7. Tải APK mẫu để luyện & cài vào emulator

Ta cần một app thật để luyện "soi element". Dùng **Sauce Labs My Demo App** — app demo mua sắm được tạo riêng cho automation (giống vai trò của SauceDemo bên web).

1. Vào releases: [https://github.com/saucelabs/my-demo-app-rn/releases](https://github.com/saucelabs/my-demo-app-rn/releases)
2. Tải file **`.apk`** cho Android (tên dạng `Android-myRNDemoApp.x.y.z.build-nnn.apk`). Lưu vào một chỗ dễ nhớ, ví dụ thư mục `Downloads`.
3. Với **emulator đang chạy**, cài app bằng `adb`:

   **macOS:**
   ```bash
   adb install ~/Downloads/Android-myRNDemoApp.1.3.0.build-244.apk
   ```
   **Windows (PowerShell):**
   ```powershell
   adb install "$env:USERPROFILE\Downloads\Android-myRNDemoApp.1.3.0.build-244.apk"
   ```
   (Đổi tên file cho khớp bản bạn tải.)
4. Thấy dòng `Success` là ✅ — mở màn hình app trên emulator, bạn sẽ thấy icon **My Demo App** vừa được cài.

> 💡 **App thay thế (tuỳ chọn):** **ApiDemos** — app mẫu kinh điển của Appium, rất ổn định để luyện. Tải `ApiDemos-debug.apk` tại [https://github.com/appium/android-apidemos/releases](https://github.com/appium/android-apidemos/releases) rồi `adb install`. Package của nó là `io.appium.android.apis`.

**Tìm `appPackage` và `appActivity` của app** (sẽ cần khi cấu hình Inspector ở Phần 5). Mở app trên emulator rồi chạy:

**macOS/Linux:**
```bash
adb shell dumpsys window | grep -i mCurrentFocus
```
**Windows (PowerShell):**
```powershell
adb shell dumpsys window | Select-String mCurrentFocus
```

Kết quả dạng `mCurrentFocus=Window{... com.saucelabs.mydemoapp.rn/com.saucelabs.mydemoapp.rn.MainActivity}` → phần trước dấu `/` là **appPackage** (`com.saucelabs.mydemoapp.rn`), phần sau là **appActivity** (`com.saucelabs.mydemoapp.rn.MainActivity`).

> 💡 Liệt kê mọi package đã cài: `adb shell pm list packages | grep -i sauce` (macOS) / `... | Select-String sauce` (Windows).

### 2C.8. ✅ Bảng kiểm tra "đã cài đúng chưa" (cho CẢ macOS & Windows)

Mở một Terminal/PowerShell **mới** (để nạp cấu hình mới nhất), bật **emulator**, và chạy lần lượt. Đối chiếu:

| # | Lệnh | Kết quả kỳ vọng | Ý nghĩa |
|---|------|-----------------|---------|
| 1 | `java -version` | `openjdk version "17..."` (hoặc 21) | JDK sẵn sàng, đúng version |
| 2 | `javac -version` | `javac 17.x` / `21.x` | Trình biên dịch sẵn sàng |
| 3 | `echo $ANDROID_HOME` (mac) / `echo $env:ANDROID_HOME` (win) | đường dẫn tới SDK | Biến môi trường đúng |
| 4 | `adb --version` | `Android Debug Bridge version 1.x.x` | adb sẵn sàng |
| 5 | `adb devices` | có dòng `emulator-5554  device` | Máy tính thấy được emulator/thiết bị |
| 6 | `node -v` | `v18...` trở lên | Node.js sẵn sàng |
| 7 | `appium -v` | `2.x.x` | Appium 2 sẵn sàng |
| 8 | `appium driver list --installed` | có `uiautomator2` | Driver Android đã cài |
| 9 | `appium` (rồi mở) | in ra `...listener started on http://127.0.0.1:4723` | Server chạy được |
| 10 | Mở **IntelliJ** | vào được màn hình Welcome | IDE sẵn sàng |
| 11 | Mở **Appium Inspector** | app mở được | Công cụ soi element sẵn sàng |
| 12 | `adb shell pm list packages \| grep -i sauce` | có `com.saucelabs.mydemoapp.rn` | APK mẫu đã cài vào emulator |

> 🎉 **Nếu tất cả (đặc biệt 1–9) đều đúng → môi trường automation mobile của bạn đã sẵn sàng.** Đây là một cột mốc thật sự — cài môi trường mobile khó hơn web, rất nhiều người vấp ở đây. Bạn qua rồi! Giờ ta học phần "đọc bản đồ app" ở Phần 3.

---

<a id="3"></a>
## 🧱 Phần 3 — Nền tảng cấu trúc UI Android (View & cây UI)

> 🌐➡️📱 **Đây là phần thay cho HTML/CSS/DOM của bản web.** Web có "cây DOM" gồm các thẻ HTML; Android có "cây View" gồm các View. Tư duy giống hệt, chỉ khác tên gọi. Nếu nắm chắc phần này, bạn viết được locator tốt — kỹ năng cốt lõi số 1 của automation.

### 3.1. Một màn hình app Android được dựng từ gì?

Khi bạn mở một app và **nhìn thấy** nút, ô nhập, chữ, ảnh — đó chỉ là "lớp sơn bên ngoài". Bên dưới, Android dựng màn hình từ những viên gạch gọi là **View**:

- **View** = một thành phần giao diện **đơn lẻ**: một cái nút (`Button`), một ô nhập (`EditText`), một dòng chữ (`TextView`), một ô tick (`CheckBox`), một ảnh (`ImageView`)...
- **ViewGroup** = một "cái hộp" **chứa** các View khác để sắp xếp bố cục: `LinearLayout` (xếp hàng ngang/dọc), `FrameLayout`, `RecyclerView` (danh sách cuộn)... ViewGroup giống thẻ `<div>` bên web — nó gom nhóm.

> **Ví von:** Màn hình app giống một **cái tủ nhiều ngăn**. Cái tủ và các ngăn lớn là **ViewGroup** (cái hộp chứa). Từng món đồ trong ngăn — cây bút, quyển sổ, cục tẩy — là **View** (thành phần đơn lẻ). Bạn — automation tester — cần chỉ đích danh "lấy **cây bút xanh ở ngăn thứ hai**", tức là trỏ đúng vào **một View** cụ thể.

Các View lồng vào nhau (ViewGroup chứa View và cả ViewGroup con) tạo thành một **cây phân cấp** — y hệt cây DOM của web.

### 3.2. Cây UI (giống cây DOM của web)

Hãy hình dung một màn hình **Đăng nhập** đơn giản: có tiêu đề, ô username, ô password, ô tick "ghi nhớ", nút đăng nhập, link quên mật khẩu. Android dựng nó thành cây như sau:

```
FrameLayout                          ← gốc màn hình (ViewGroup)
└── LinearLayout (login_container)   ← hộp chứa (ViewGroup)
    ├── TextView   ("Đăng nhập")         ← View: tiêu đề
    ├── EditText   (ô username)          ← View: ô nhập
    ├── EditText   (ô password)          ← View: ô nhập
    ├── CheckBox   ("Ghi nhớ đăng nhập") ← View
    ├── Button     ("ĐĂNG NHẬP")         ← View: nút
    └── TextView   ("Quên mật khẩu?")    ← View: chữ bấm được
```

**Thuật ngữ quan hệ trong cây** (giống hệt DOM — sẽ gặp lại khi viết XPath):

| Thuật ngữ | Nghĩa | Ví dụ trong cây trên |
|-----------|-------|----------------------|
| **Node / element** | Mỗi View là một nút | `Button`, `EditText`... |
| **Parent (cha)** | ViewGroup bao ngoài trực tiếp | `LinearLayout` là cha của `Button` |
| **Child (con)** | View bên trong trực tiếp | `Button` là con của `LinearLayout` |
| **Sibling (anh em)** | Các View cùng cha | ô username và ô password là anh em |
| **Descendant (hậu duệ)** | Con, cháu, chắt... | mọi View là hậu duệ của `FrameLayout` |
| **Root (gốc)** | Nút trên cùng | `FrameLayout` |

> 🔑 **Điểm mấu chốt:** Máy tính **không "nhìn" nút bằng mắt** như bạn. Với con người, "ĐĂNG NHẬP" là một hình chữ nhật xanh. Với Appium, nó là một **View trong cây UI** có tên lớp `android.widget.Button` và các thuộc tính định danh. Khi bạn ra lệnh "chạm nút đăng nhập", Appium đi vào **cây UI**, tìm đúng **View** đó, rồi chạm. Vì thao tác trên cây (chứ không phải trên ảnh chụp), Appium **chính xác** — nó biết View ở đâu, đã hiện chưa, có bị disable không.

### 3.3. Các thuộc tính định danh của một View Android

Mỗi View mang theo một loạt **thuộc tính** — giống "chứng minh thư". Đây chính là thứ ta dùng để "chỉ đích danh" View khi automation. Hãy thuộc lòng bảng này:

| Thuộc tính | Ý nghĩa | Giá trị so sánh với web | Dùng làm locator? |
|-----------|---------|-------------------------|-------------------|
| **`content-desc`** | *Accessibility ID* — mô tả để hỗ trợ người khiếm thị (đọc màn hình) | ~ `data-test` / aria-label | ⭐⭐⭐ **TỐT NHẤT** — ổn định, thường do dev cố ý đặt |
| **`resource-id`** | Định danh tài nguyên, dạng `package:id/tên` | ~ thuộc tính `id` của HTML | ⭐⭐ **RẤT TỐT** — thường duy nhất trong màn hình |
| **`text`** | Chữ hiển thị trên View | ~ nội dung text của thẻ | ⚠️ Được, nhưng **đổi theo ngôn ngữ** (Việt/Anh) → dễ gãy |
| **`class`** | Tên lớp Android của View | ~ tên thẻ (`button`, `input`) | ⚠️ Thường **trùng** nhiều View (nhiều `EditText`) → ít khi đủ để chỉ đích danh |
| **`bounds`** | Toạ độ khung `[trái,trên][phải,dưới]` | ~ vị trí pixel | ❌ **Tránh** — đổi theo độ phân giải/máy |
| **`clickable`** | View có bấm được không (`true`/`false`) | — | Không phải locator, nhưng giúp biết View có tương tác được |
| **`enabled`** | View có đang bật (dùng được) không | ~ `disabled` | Kiểm tra trạng thái, không phải locator |
| **`displayed`** | View có đang hiển thị trên màn hình không | ~ visible | Kiểm tra trạng thái |
| **`checkable` / `checked`** | Áp dụng cho CheckBox/Switch | ~ checkbox `checked` | Kiểm tra trạng thái tick |
| **`package`** | App nào chứa View này | — | Ít dùng để định vị |
| **`focusable` / `scrollable` / `password`** | Các cờ trạng thái khác | — | Bổ trợ |

> 💡 **Vì sao `content-desc` (accessibility id) và `resource-id` là "vàng"?**
> - **`content-desc`** (accessibility id) thường do **dev cố ý đặt** để hỗ trợ trình đọc màn hình — và cũng để **cho tester**. Nó ít bị đổi khi giao diện thay đổi, và **không đổi theo ngôn ngữ**. Bền nhất. Các app viết cho automation (như Sauce Labs demo) đặt sẵn dạng `test-Username`, `test-LOGIN`...
> - **`resource-id`** giống `id` bên web: thường **duy nhất** trong một màn hình → chỉ một View khớp → không nhầm lẫn.
> - Ngược lại, **`text`** đổi khi app đổi ngôn ngữ (nút "ĐĂNG NHẬP" → "LOGIN"); **`class`** (như `android.widget.EditText`) **trùng** ở nhiều ô; **`bounds`** đổi theo màn hình. Ba cái này dễ gãy.

> ⚠️ **Cảnh báo về `resource-id`:** Không phải View nào cũng có. Nhiều app (đặc biệt viết bằng **React Native** hoặc **Flutter**) **không có** `resource-id` rõ ràng cho mọi element — nhưng thường lại đặt **`content-desc`** rất tốt. Đó là thêm một lý do nữa để **ưu tiên accessibility id**.

### 3.4. Ví dụ đầy đủ: cây UI của một màn hình Đăng nhập (dạng XML)

Appium Inspector và lệnh dump sẽ cho bạn thấy cây UI dưới dạng **XML** (giống HTML). Đây là XML mô phỏng màn hình Login ở trên — **hãy đọc thật kỹ**, ta sẽ dùng lại nó xuyên suốt Phần 4, bài tập, và đáp án (giống cách bản web dùng lại form login):

```xml
<hierarchy rotation="0">
  <android.widget.FrameLayout>
    <android.widget.LinearLayout resource-id="com.example.app:id/login_container">

      <android.widget.TextView
          resource-id="com.example.app:id/title"
          class="android.widget.TextView"
          text="Đăng nhập"
          content-desc=""
          clickable="false" enabled="true" displayed="true"
          bounds="[120,300][600,380]" />

      <android.widget.EditText
          resource-id="com.example.app:id/username"
          class="android.widget.EditText"
          text=""
          content-desc="test-Username"
          clickable="true" enabled="true" displayed="true"
          bounds="[80,420][1000,520]" />

      <android.widget.EditText
          resource-id="com.example.app:id/password"
          class="android.widget.EditText"
          text=""
          content-desc="test-Password"
          password="true"
          clickable="true" enabled="true" displayed="true"
          bounds="[80,560][1000,660]" />

      <android.widget.CheckBox
          resource-id="com.example.app:id/remember"
          class="android.widget.CheckBox"
          text="Ghi nhớ đăng nhập"
          content-desc=""
          checkable="true" checked="false"
          clickable="true" enabled="true" displayed="true"
          bounds="[80,700][620,760]" />

      <android.widget.Button
          resource-id="com.example.app:id/login_button"
          class="android.widget.Button"
          text="ĐĂNG NHẬP"
          content-desc="test-LOGIN"
          clickable="true" enabled="true" displayed="true"
          bounds="[80,820][1000,920]" />

      <android.widget.TextView
          resource-id="com.example.app:id/forgot"
          class="android.widget.TextView"
          text="Quên mật khẩu?"
          content-desc="test-Forgot password"
          clickable="true" enabled="true" displayed="true"
          bounds="[350,960][730,1010]" />

    </android.widget.LinearLayout>
  </android.widget.FrameLayout>
</hierarchy>
```

**Giải thích từng phần:**

1. **`<hierarchy>`** là gốc của bản dump cây UI. Bên trong là các View lồng nhau (thụt vào = cấp sâu hơn).

2. **Ô username** (`EditText`):
   - `resource-id="com.example.app:id/username"` → ⭐⭐ id, thường duy nhất. Chú ý dạng đầy đủ có cả **package** (`com.example.app`) + `:id/` + tên (`username`).
   - `content-desc="test-Username"` → ⭐⭐⭐ accessibility id — **bền nhất**.
   - `class="android.widget.EditText"` → ⚠️ trùng với ô password (cả hai đều là `EditText`) → **không đủ** để phân biệt.
   - `text=""` → đang trống (chưa gõ gì).
   - `bounds="[80,420][1000,520]"` → toạ độ khung — ❌ đừng dùng làm locator.

3. **Ô password:** giống username nhưng `resource-id=".../password"`, `content-desc="test-Password"`, và có `password="true"` (ẩn ký tự). **Cũng là** `android.widget.EditText` như username → đây là ví dụ điển hình việc `class` bị trùng.

4. **CheckBox "Ghi nhớ":** `resource-id=".../remember"`, có `checkable="true"` và `checked="false"` (chưa tick). `content-desc` để trống → ở đây nên dùng `resource-id` hoặc `text`.

5. **Nút "ĐĂNG NHẬP":** `resource-id=".../login_button"`, `content-desc="test-LOGIN"`, `text="ĐĂNG NHẬP"`. Chú ý: `text` là tiếng Việt in hoa — nếu app đổi sang tiếng Anh, `text` sẽ thành "LOGIN" → locator theo `text` sẽ gãy, còn `content-desc="test-LOGIN"` thì **không đổi**.

6. **Link "Quên mật khẩu?":** là một `TextView` nhưng `clickable="true"` (bấm được), có cả `content-desc="test-Forgot password"`.

> 🔑 **Bài học rút ra:** Cùng một View có **nhiều cách** để định vị. Ô username ở trên có thể trỏ tới bằng `content-desc`, `resource-id`, `class` (kèm điều kiện khác), hay `bounds`. Kỹ năng của automation tester là **chọn cách bền nhất** — ưu tiên **`content-desc` (accessibility id) → `resource-id`**, tránh phụ thuộc `text`, `class` đơn lẻ, hay `bounds`.

### 3.5. Bảng đối chiếu nhanh: Web (HTML/DOM) ↔ Mobile (Android UI)

Nếu bạn đã biết web, bảng này giúp "chuyển ngữ". Nếu chưa, cứ đọc cột Mobile là đủ:

| Khái niệm | Web (HTML/DOM) | Mobile (Android) |
|-----------|----------------|------------------|
| Đơn vị giao diện | Thẻ HTML (`<button>`, `<input>`) | View (`Button`, `EditText`) |
| Hộp gom nhóm | `<div>`, `<form>` | ViewGroup (`LinearLayout`, `FrameLayout`) |
| Cấu trúc tổng thể | Cây **DOM** | Cây **View (UI hierarchy)** |
| Id duy nhất | `id="username"` | `resource-id="...:id/username"` |
| Định danh cho test | `data-test="username"` | `content-desc="test-Username"` (accessibility id) |
| Nội dung chữ | text giữa 2 thẻ | thuộc tính `text` |
| "Loại" element | tên thẻ (tag) | thuộc tính `class` |
| Cách định vị | CSS Selector, XPath | `AppiumBy` (accessibilityId, id, className, UIAutomator, XPath) |
| Công cụ soi | Chrome DevTools (F12) | Appium Inspector |

> 🌉 Nắm bảng này, bạn thấy rõ: **tư duy y hệt**, chỉ đổi "từ vựng". Giờ ta học cách viết "địa chỉ" element trong Appium — phần 4.

---

<a id="4"></a>
## 🎯 Phần 4 — Chiến lược locator Appium

> 🌐➡️📱 **Đây là phần thay cho CSS Selector của bản web.** Web viết "địa chỉ" element bằng CSS Selector; Appium viết bằng **`AppiumBy`**. Đây là kỹ năng quan trọng nhất bạn mang theo cả khóa.

### 4.1. Locator là gì?

Một màn hình app có thể có hàng chục, hàng trăm View. Làm sao chỉ cho Appium biết **chính xác** View nào? Bạn cần một cách mô tả "địa chỉ" của View — gọi là **locator**.

> **Ví von:** Locator giống **cách bạn chỉ một người trong đám đông**. "Người **tên Nam**" (theo id), "người mặc **áo có bảng tên 'nhân viên'**" (theo accessibility id), "**mọi người mặc áo xanh**" (theo class — có thể trúng nhiều người). Mô tả càng đặc trưng và duy nhất, máy tìm càng đúng.

Trong Appium (Java Client), ta tạo locator bằng lớp **`AppiumBy`** rồi đưa cho `driver.findElement(...)`. Ví dụ tối giản:

```java
import io.appium.java_client.AppiumBy;

// "Tìm View có content-desc = test-Username"
driver.findElement(AppiumBy.accessibilityId("test-Username"));
```

> 📌 `AppiumBy` là lớp của **Appium Java Client** (phiên bản 8/9 trở lên). Ở giai đoạn này bạn chưa cần viết cả chương trình — chỉ cần **hiểu từng loại locator**. Ta sẽ dùng chúng thật sự ở Giai đoạn sau. (Cú pháp có thể thay đổi chút theo phiên bản Java Client.)

### 4.2. Các loại locator (AppiumBy) cho Android

Đây là 5 "vũ khí" chính. Dùng lại cây UI Login ở Phần 3.4 để minh họa:

#### a) `AppiumBy.accessibilityId` — theo `content-desc` ⭐⭐⭐

```java
driver.findElement(AppiumBy.accessibilityId("test-Username"));
```

→ Tìm View có `content-desc="test-Username"`. **Ưu tiên số 1.** Bền, không đổi theo ngôn ngữ, chạy được cả Android lẫn iOS (nếu app đặt id chung).

#### b) `AppiumBy.id` — theo `resource-id` ⭐⭐

```java
driver.findElement(AppiumBy.id("com.example.app:id/username"));
```

→ Tìm View có `resource-id` khớp. Giống `id` bên web, thường **duy nhất** trong màn hình.

> 💡 **Mẹo:** thường có thể ghi gọn phần tên id (`username`) thay vì đầy đủ `com.example.app:id/username` — nhưng ghi đầy đủ **chắc chắn** hơn, tránh nhầm khi có nhiều app.

#### c) `AppiumBy.className` — theo `class` ⚠️

```java
driver.findElement(AppiumBy.className("android.widget.EditText"));
```

→ Tìm View theo tên lớp Android. **Cẩn thận:** trong màn hình Login, cả ô username **và** password đều là `android.widget.EditText` → locator này khớp **2 View** → `findElement` sẽ trả về **cái đầu tiên**, dễ nhầm. Chỉ nên dùng khi class đó **duy nhất** trên màn hình.

#### d) `AppiumBy.androidUIAutomator` — dùng UiSelector (mạnh & linh hoạt) ⭐

Đây là locator **riêng của Android**, dùng ngôn ngữ **UiSelector** của Android để mô tả element theo **nhiều thuộc tính**:

```java
// theo resource-id
driver.findElement(AppiumBy.androidUIAutomator(
    "new UiSelector().resourceId(\"com.example.app:id/login_button\")"));

// theo text
driver.findElement(AppiumBy.androidUIAutomator(
    "new UiSelector().text(\"ĐĂNG NHẬP\")"));

// theo content-desc (accessibility)
driver.findElement(AppiumBy.androidUIAutomator(
    "new UiSelector().description(\"test-LOGIN\")"));

// kết hợp nhiều điều kiện: là Button VÀ text chứa "ĐĂNG"
driver.findElement(AppiumBy.androidUIAutomator(
    "new UiSelector().className(\"android.widget.Button\").textContains(\"ĐĂNG\")"));
```

> 💡 UiSelector có nhiều "bộ lọc": `.text()`, `.textContains()`, `.textStartsWith()`, `.resourceId()`, `.description()`, `.className()`, `.checkable()`, `.index()`... Rất mạnh khi cần kết hợp điều kiện. Nhớ **escape dấu nháy** (`\"`) vì cả biểu thức nằm trong chuỗi Java. Đào sâu ở Giai đoạn 3.

#### e) `AppiumBy.xpath` — theo đường dẫn trên cây ⚠️ (dùng khi bí)

XPath mô tả vị trí trong cây XML. Rất **linh hoạt** (định vị được gần như mọi thứ) nhưng **chậm hơn** và **dễ gãy hơn** — dùng khi các cách trên không được:

```java
// theo content-desc
driver.findElement(AppiumBy.xpath("//android.widget.Button[@content-desc='test-LOGIN']"));

// theo text
driver.findElement(AppiumBy.xpath("//android.widget.EditText[@text='']"));

// theo resource-id
driver.findElement(AppiumBy.xpath("//*[@resource-id='com.example.app:id/password']"));

// text chứa một chuỗi
driver.findElement(AppiumBy.xpath("//*[contains(@text,'Quên mật khẩu')]"));
```

> ⚠️ **Tránh XPath "tuyệt đối"** kiểu `/hierarchy/FrameLayout/LinearLayout/Button[2]` — nó phụ thuộc cấu trúc cây, chỉ cần dev thêm/bớt một lớp layout là gãy. Nếu buộc dùng XPath, hãy dựa vào **thuộc tính** (`@content-desc`, `@resource-id`, `@text`) chứ đừng dựa vào vị trí.

### 4.3. 🏆 Thứ tự ưu tiên khi chọn locator (HỌC THUỘC)

Khi một View có nhiều cách định vị, chọn theo thứ tự ưu tiên sau:

| Hạng | Loại locator | Vì sao |
|:----:|--------------|--------|
| 1 ⭐⭐⭐ | `accessibilityId` (`content-desc`) | Bền nhất, không đổi theo ngôn ngữ, dev thường đặt sẵn cho test |
| 2 ⭐⭐ | `id` (`resource-id`) | Thường duy nhất, ổn định (nếu app có đặt) |
| 3 ⭐ | `androidUIAutomator` với thuộc tính ổn định | Linh hoạt, kết hợp nhiều điều kiện, nhanh |
| 4 | `className` (nếu **duy nhất** trên màn hình) | Chỉ khi chỉ có 1 View loại đó |
| 5 (cuối cùng) | `xpath` dựa trên thuộc tính | Khi hết cách; tránh XPath theo vị trí |
| ❌ Tránh | Toạ độ (x, y), `bounds`, XPath tuyệt đối | Gãy ngay khi đổi máy/độ phân giải/cấu trúc |

> **Câu thần chú:** *"accessibility id trước, resource-id sau, UIAutomator khi cần kết hợp, XPath là phương án cuối, toạ độ thì không bao giờ."*

### 4.4. 📊 BẢNG VÀNG: locator → View nó trỏ tới

Dùng lại cây UI Login ở **Phần 3.4**. Đối chiếu từng locator với View nó chọn và số lượng khớp:

| # | Locator (Java) | Trỏ tới View | Số khớp | Ghi chú |
|---|----------------|--------------|:-------:|---------|
| 1 | `AppiumBy.accessibilityId("test-Username")` | Ô username | 1 | ⭐⭐⭐ Bền nhất |
| 2 | `AppiumBy.accessibilityId("test-Password")` | Ô password | 1 | ⭐⭐⭐ |
| 3 | `AppiumBy.accessibilityId("test-LOGIN")` | Nút ĐĂNG NHẬP | 1 | ⭐⭐⭐ |
| 4 | `AppiumBy.id("com.example.app:id/username")` | Ô username | 1 | ⭐⭐ Theo resource-id |
| 5 | `AppiumBy.id("com.example.app:id/login_button")` | Nút ĐĂNG NHẬP | 1 | ⭐⭐ |
| 6 | `AppiumBy.className("android.widget.EditText")` | ô username **và** password | **2** | ⚠️ Trùng → trả về cái đầu |
| 7 | `AppiumBy.className("android.widget.Button")` | Nút ĐĂNG NHẬP | 1 | ✅ Chỉ có 1 Button trên màn hình này |
| 8 | `AppiumBy.androidUIAutomator("new UiSelector().text(\"ĐĂNG NHẬP\")")` | Nút ĐĂNG NHẬP | 1 | ✅ Theo text (⚠️ đổi ngôn ngữ là gãy) |
| 9 | `AppiumBy.androidUIAutomator("new UiSelector().description(\"test-Password\")")` | Ô password | 1 | ✅ = accessibility id, viết kiểu UiSelector |
| 10 | `AppiumBy.xpath("//android.widget.Button[@content-desc='test-LOGIN']")` | Nút ĐĂNG NHẬP | 1 | ✅ XPath theo thuộc tính (ổn) |
| 11 | `AppiumBy.xpath("//*[contains(@text,'Quên mật khẩu')]")` | Link Quên mật khẩu | 1 | ✅ text chứa chuỗi |
| 12 | `AppiumBy.id("com.example.app:id/remember")` | CheckBox Ghi nhớ | 1 | ⭐⭐ |

> 🎓 **Bài học lớn:** Với ô password, ta có ít nhất **4 locator đúng**: `accessibilityId("test-Password")`, `id(".../password")`, `androidUIAutomator(...description("test-Password"))`, `xpath("//*[@resource-id='...password']")`. Nhưng **không phải cái nào cũng tốt như nhau** — hãy chọn theo thứ tự ưu tiên ở 4.3. Còn `className("android.widget.EditText")` thì **sai** vì khớp cả 2 ô.

### 4.5. Nếu bạn đã biết code: khung một locator trong Java

Chưa cần viết ngay, nhưng để bạn hình dung locator "sống" trong code test thế nào (Giai đoạn sau sẽ làm chi tiết):

```java
import io.appium.java_client.AppiumBy;
import org.openqa.selenium.WebElement;

// Tìm ô username rồi gõ chữ vào
WebElement usernameField = driver.findElement(AppiumBy.accessibilityId("test-Username"));
usernameField.sendKeys("bob@example.com");

// Tìm nút Login rồi chạm
driver.findElement(AppiumBy.accessibilityId("test-LOGIN")).click();
```

> Thấy chưa? Toàn bộ độ khó nằm ở việc **viết đúng cái locator** bên trong `AppiumBy.…(...)`. Đó là lý do ta luyện đọc cây UI và chọn locator ngay từ Giai đoạn 0. Còn `.sendKeys()`, `.click()` chỉ là hành động, học sau rất nhanh.

---

<a id="5"></a>
## 🔧 Phần 5 — Dùng Appium Inspector (thay cho F12)

> 🌐➡️📱 **Đây là phần thay cho Chrome DevTools/F12 của bản web.** Web dùng F12 để soi DOM và đọc thuộc tính; mobile dùng **Appium Inspector** để soi cây UI và đọc `resource-id`/`content-desc`. Đây là **công cụ số 1** của automation mobile tester — thành thạo nó = tiết kiệm hàng giờ.

**Appium Inspector** kết nối tới Appium Server, mở một phiên (session) trên emulator, chụp lấy cây UI hiện tại, và hiển thị cho bạn: bên trái là **ảnh màn hình app**, ở giữa là **cây UI**, bên phải là **bảng thuộc tính** của View bạn chọn. Bạn click vào View trên ảnh → nó highlight trong cây → bạn đọc được `resource-id`, `content-desc`, `class`, `bounds`... và **copy** để làm locator.

### 5.1. Chuẩn bị trước khi mở Inspector

Inspector cần 3 thứ đang **sẵn sàng** (đã cài ở Phần 2):

1. ✅ **Emulator đang chạy** (kiểm tra: `adb devices` thấy `emulator-5554 device`).
2. ✅ **Appium Server đang chạy.** Mở một Terminal, gõ `appium`, để nguyên cửa sổ (thấy dòng `...listener started on http://127.0.0.1:4723`).
3. ✅ **App mẫu đã cài** vào emulator (Phần 2C.7).

### 5.2. Hiểu về "Capabilities" — tờ khai để mở phiên

**Capabilities** (viết tắt "caps") là một **tờ khai** dạng JSON cho Appium biết: bạn muốn test **nền tảng nào, thiết bị nào, app nào**. Giống như điền phiếu trước khi vào phòng test. Các cap cơ bản cho Android:

| Capability | Ý nghĩa | Ví dụ giá trị |
|-----------|---------|---------------|
| `platformName` | Nền tảng | `Android` |
| `appium:automationName` | Driver dùng | `UiAutomator2` |
| `appium:deviceName` | Tên thiết bị (Android khá "dễ tính", ghi gì cũng được) | `Android Emulator` |
| `appium:app` | Đường dẫn tới file `.apk` (Appium tự cài & mở) | `/Users/ban/Downloads/app.apk` |
| `appium:appPackage` | Package của app (nếu app **đã cài sẵn**) | `com.saucelabs.mydemoapp.rn` |
| `appium:appActivity` | Activity khởi động | `com.saucelabs.mydemoapp.rn.MainActivity` |

> 💡 **Hai cách chỉ định app:** (1) dùng `appium:app` = đường dẫn tới `.apk` → Appium tự cài rồi mở. (2) App **đã cài sẵn** thì dùng cặp `appium:appPackage` + `appium:appActivity` (lấy bằng lệnh `adb shell dumpsys window | grep mCurrentFocus` ở Phần 2C.7). Cách (2) nhanh hơn vì khỏi cài lại.

> 📌 Chú ý tiền tố **`appium:`** ở đầu các cap dành riêng cho Appium (chuẩn W3C mới). `platformName` là cap chuẩn nên **không** cần tiền tố.

**Ví dụ tờ khai caps đầy đủ (JSON — dán vào Inspector):**

```json
{
  "platformName": "Android",
  "appium:automationName": "UiAutomator2",
  "appium:deviceName": "Android Emulator",
  "appium:appPackage": "com.saucelabs.mydemoapp.rn",
  "appium:appActivity": "com.saucelabs.mydemoapp.rn.MainActivity"
}
```

### 5.3. Kết nối Inspector tới Appium Server (thao tác cầm tay)

1. Mở **Appium Inspector**.
2. Ở khu vực **Remote Host / Remote Port**, để mặc định:
   - **Remote Host:** `127.0.0.1`
   - **Remote Port:** `4723`
   - **Remote Path:** `/` (Appium 2 dùng `/`; nếu là bản 1.x cũ mới là `/wd/hub`).
3. Ở ô **Desired Capabilities**, chọn chế độ **JSON Representation** (biểu tượng `{}`) rồi **dán** đoạn JSON caps ở trên. (Hoặc điền từng dòng key/value ở chế độ bảng.)
4. (Tuỳ chọn) bấm **Save As** để lưu bộ caps này, lần sau khỏi gõ lại.
5. Bấm **Start Session**.
6. Chờ vài giây → Inspector hiện: **ảnh màn hình app** bên trái, **cây UI** ở giữa, **bảng thuộc tính** bên phải. 🎉

> ⚠️ **Lỗi thường gặp khi Start Session:**
> - *"Could not connect / ECONNREFUSED"* → Appium Server chưa chạy (chưa gõ `appium`) hoặc sai Host/Port.
> - *"No device / device not found"* → emulator chưa bật; kiểm tra `adb devices`.
> - *"Activity ... never started"* → sai `appActivity`; lấy lại bằng lệnh `dumpsys` ở Phần 2C.7, hoặc thử thêm cap `appium:appWaitActivity` = `*`.

### 5.4. Đọc thuộc tính element & lấy locator (phần quan trọng nhất)

Đây là kỹ năng cốt lõi — làm y hệt việc "Inspect" một element bên web:

1. **Click vào một element trên ảnh màn hình** bên trái (ví dụ ô Username). Element đó được **tô sáng** cả trên ảnh lẫn trong cây UI ở giữa.
2. **Bảng thuộc tính bên phải** (mục *Selected Element* / *Attribute*) hiện toàn bộ "chứng minh thư" của View: `resource-id`, `content-desc`, `class`, `text`, `bounds`, `clickable`, `enabled`, `checked`...
3. **Đọc và chọn locator bền nhất** (theo thứ tự ưu tiên Phần 4.3): ưu tiên `content-desc` → `resource-id`.
4. **Inspector còn gợi ý sẵn locator!** Ở bảng bên phải thường có phần **"Find By"** liệt kê các chiến lược khả dụng (accessibility id, id, xpath...) kèm giá trị, và có nút **copy** (biểu tượng 📋) để chép ngay. Rất tiện — nhưng **đừng tin XPath dài nó gợi ý**; hãy tự ưu tiên accessibility id / id.

**Ví dụ:** click vào ô Username của app, bảng thuộc tính có thể hiện:

```
content-desc : test-Username
class        : android.widget.EditText
resource-id  : (trống hoặc com.saucelabs...:id/...)
bounds       : [48,506][1032,638]
clickable    : true
enabled      : true
```

→ Locator tốt nhất: `AppiumBy.accessibilityId("test-Username")`.

### 5.5. Các nút hữu ích khác trong Inspector

| Nút / khu vực | Công dụng |
|---------------|-----------|
| **Tap** (chọn element rồi bấm) | Chạm thử vào element ngay trên emulator |
| **Send Keys** | Gõ chữ thử vào ô nhập đang chọn |
| **Refresh Source** (🔄) | Chụp lại cây UI sau khi màn hình thay đổi (rất hay dùng: cứ chuyển màn hình là bấm refresh) |
| **Back** (◀) | Bấm nút Back của Android |
| **Start/Stop Recording** (⏺) | Ghi lại thao tác thành **code mẫu** (nhiều ngôn ngữ, gồm Java) — tham khảo nhanh, đừng phụ thuộc |
| **Swipe By Coordinates** | Vuốt thử theo toạ độ (chỉ để thử tay) |
| **Search for element** | Tìm element theo một locator để kiểm chứng nó có khớp không |

> 💡 **Quy trình "test locator" trong Inspector** (giống test selector trong Console web): sau khi đoán một locator, dùng chức năng **Search for element** → nhập chiến lược (accessibility id) + giá trị (`test-Username`) → Inspector cho biết có tìm thấy không và **bao nhiêu** element khớp. Đây là cách xác minh locator **trước khi** viết vào code Java — thử ở đây mất 5 giây, đoán mò trong code rồi chạy lại mất 5 phút.

### 5.6. Công cụ thay thế / bổ trợ (biết để phòng khi)

Ngoài Appium Inspector, còn vài cách "soi" cây UI:

- **`uiautomatorviewer`** — công cụ cũ đi kèm Android SDK (thư mục `tools/bin`). Chụp ảnh màn hình + cây UI tĩnh. Đơn giản nhưng không mở session Appium; một số bản SDK mới đã bỏ. Chạy: `uiautomatorviewer` (nếu có trong PATH).
- **`adb shell uiautomator dump`** — dump cây UI hiện tại ra file XML ngay trên máy tính:
  ```bash
  adb shell uiautomator dump /sdcard/ui.xml
  adb pull /sdcard/ui.xml ./ui.xml
  ```
  Mở `ui.xml` bằng trình soạn thảo để đọc `resource-id`, `content-desc`... Cách này **luôn dùng được**, tiện khi Inspector trục trặc.
- **`adb shell dumpsys`** — xem thông tin hệ thống. Hữu ích nhất: tìm activity đang mở:
  ```bash
  adb shell dumpsys window | grep -i mCurrentFocus     # macOS/Linux
  adb shell dumpsys window | Select-String mCurrentFocus  # Windows PowerShell
  ```
- **Android Studio → Layout Inspector** — soi layout của app (chủ yếu cho dev, nhưng xem được cây View).

> 📌 Ở Giai đoạn 0, mục tiêu chỉ cần: **mở được Inspector, Start Session vào app mẫu, click một element và đọc đúng `content-desc`/`resource-id`/`class` của nó, rồi copy ra làm locator.** Vậy là đủ.

---

<a id="6"></a>
## 🛠️ Phần 6 — Bài thực hành có hướng dẫn: Sauce Labs My Demo App

Giờ ta áp dụng mọi thứ vào một app **thật**: **Sauce Labs My Demo App** (bạn đã cài ở Phần 2C.7) — một app mua sắm giả lập được tạo riêng để luyện automation. Đây là "sân tập" bạn sẽ dùng suốt cả khóa (giống vai trò SauceDemo bên web).

> 🎯 **Mục tiêu:** Tự tay mở Appium Inspector, Start Session vào app, và tìm được locator của các element chính: **nút thêm giỏ hàng**, **ô Username / Password / nút Login** ở màn hình đăng nhập, và **tên sản phẩm**. Đây chính là kỹ năng bạn dùng ở mọi bài Appium sau này.

> ⚠️ **Lưu ý quan trọng về giá trị locator:** Các `content-desc`/`resource-id` bên dưới là **giá trị điển hình** của app này (bản React Native). **Phiên bản app có thể thay đổi** → điều bắt buộc là bạn **tự mở Inspector kiểm chứng**, đừng chép đáp án. Chính việc "soi thật" mới là kỹ năng cần luyện.

### Bước 1 — Khởi động bộ ba

1. Bật **emulator** (Android Studio → Device Manager → ▶). Chờ boot xong.
2. Mở Terminal, gõ `appium` để chạy server (để nguyên cửa sổ đó).
3. Kiểm tra nhanh: `adb devices` thấy `emulator-5554 device`.

### Bước 2 — Start Session bằng Appium Inspector

1. Mở **Appium Inspector**. Remote Host `127.0.0.1`, Port `4723`, Path `/`.
2. Dán caps (dùng package/activity của app; nếu app bạn tải khác version, lấy lại bằng `adb shell dumpsys window | grep mCurrentFocus`):

   ```json
   {
     "platformName": "Android",
     "appium:automationName": "UiAutomator2",
     "appium:deviceName": "Android Emulator",
     "appium:appPackage": "com.saucelabs.mydemoapp.rn",
     "appium:appActivity": "com.saucelabs.mydemoapp.rn.MainActivity"
   }
   ```
3. Bấm **Start Session**. App mở ra màn hình danh sách sản phẩm (Products/Catalog).

### Bước 3 — Soi nút "Add to cart" của một sản phẩm

1. Trên ảnh màn hình trong Inspector, click vào **nút giỏ hàng nhỏ** (hoặc nút "Add to cart") của một sản phẩm.
2. Đọc bảng thuộc tính bên phải: ghi lại `content-desc`, `class`.

<details>
<summary>💡 <b>Gợi ý đáp án — Nút Add to cart</b> (tự soi trước rồi mới mở)</summary>

App này đặt accessibility id rất "thân thiện với test". Nút thêm giỏ hàng thường có:

```
content-desc : test-Add To Cart
class        : android.widget.ImageView  (hoặc android.view.ViewGroup)
```

**Locator tốt:** `AppiumBy.accessibilityId("test-Add To Cart")`.

> 👀 Chú ý: app React Native thường **không có** `resource-id` cho nhiều element, nhưng **có** `content-desc` rất tốt → đây là minh chứng thực tế cho việc **ưu tiên accessibility id**. Nhiều sản phẩm cùng có `content-desc="test-Add To Cart"` → locator này khớp **nhiều** element (mỗi sản phẩm một nút) — đây là ví dụ thực tế của locator trỏ tới **danh sách**, bạn sẽ học cách lọc từng cái ở giai đoạn sau.

</details>

### Bước 4 — Mở màn hình Login và soi ô Username

1. Trong app, mở **menu** (biểu tượng ☰ góc trái trên) → chọn **Log In** (hoặc **Login**). (Bấm trực tiếp trên cửa sổ emulator, rồi bấm **Refresh Source** 🔄 trong Inspector để cập nhật cây UI.)
2. Click vào **ô Username** trên ảnh, đọc thuộc tính.

<details>
<summary>💡 <b>Gợi ý đáp án — Ô Username</b></summary>

```
content-desc : test-Username
class        : android.widget.EditText
```

**Locator:** `AppiumBy.accessibilityId("test-Username")`.

> 💡 Tài khoản mẫu của app: username `bob@example.com`, password `10203040` (tiện để đăng nhập thử).

</details>

### Bước 5 — Soi ô Password và nút Login

Làm y hệt Bước 4 cho **ô Password** và **nút LOGIN**.

<details>
<summary>💡 <b>Gợi ý đáp án — Password & Login</b></summary>

**Ô Password:**
```
content-desc : test-Password
class        : android.widget.EditText
```
→ `AppiumBy.accessibilityId("test-Password")`

**Nút Login:**
```
content-desc : test-LOGIN
class        : android.widget.ImageView / android.view.ViewGroup
text         : LOGIN
```
→ `AppiumBy.accessibilityId("test-LOGIN")` (bền hơn dùng `text="LOGIN"` vì text đổi theo ngôn ngữ).

</details>

### Bước 6 — Soi tên một sản phẩm

Quay lại màn hình danh sách (bấm Back ◀, Refresh Source). Click vào **tên một sản phẩm** (ví dụ "Sauce Labs Backpack").

<details>
<summary>💡 <b>Gợi ý đáp án — Tên sản phẩm</b></summary>

```
content-desc : test-Item title
class        : android.widget.TextView
text         : Sauce Labs Backpack   (đổi theo từng sản phẩm)
```

**Locator:** `AppiumBy.accessibilityId("test-Item title")` khớp **nhiều** (mỗi sản phẩm một cái). Muốn đúng 1 sản phẩm cụ thể, kết hợp thêm `text`:
```java
AppiumBy.androidUIAutomator(
    "new UiSelector().description(\"test-Item title\").text(\"Sauce Labs Backpack\")");
```
Đây là bài học thực chiến: khi accessibility id **trùng**, ta **kết hợp** thêm điều kiện (text) để chỉ đích danh.

</details>

### Bước 7 — (Thử thách) Kiểm chứng locator bằng Search for element

1. Trong Inspector, bấm **Search for element**.
2. Chọn chiến lược **Accessibility ID**, nhập `test-Username` → **Search**.
3. Inspector báo tìm thấy mấy element. Với `test-Username` kỳ vọng **1**; với `test-Add To Cart` (ở màn hình sản phẩm) sẽ là **nhiều**.

> ✅ **Hoàn thành bài này nghĩa là bạn đã làm được kỹ năng cốt lõi của Giai đoạn 0:** Start Session, soi element bất kỳ, đọc thuộc tính, tự chọn và tự kiểm chứng locator trên một app thật. Đây đúng là việc một automation mobile tester làm hằng ngày.

---

<a id="7"></a>
## ✍️ Phần 7 — Bài tập tự làm

> Hãy **tự làm hết** rồi mới xem [Đáp án ở Phần 9](#9). Tự vật lộn 5 phút giá trị hơn đọc đáp án 5 giây. Nhiều bài yêu cầu bạn **thực sự mở Appium Inspector và soi app** — đừng chỉ nghĩ trong đầu.

Dùng lại **cây UI Login ở Phần 3.4** cho các bài 1–5 (chép nó ra, hoặc hình dung nó).

**Bài 1 (Đọc thuộc tính View).**
Cho element sau:
```xml
<android.widget.EditText
    resource-id="com.shop.app:id/email"
    class="android.widget.EditText"
    text=""
    content-desc="test-Email"
    clickable="true" enabled="true"
    bounds="[64,410][1016,520]" />
```
Hãy cho biết: (a) tên `class`, (b) giá trị `resource-id`, (c) giá trị `content-desc` (accessibility id), (d) thuộc tính nào **bền nhất** để làm locator và **vì sao**, (e) vì sao **không** nên dùng `bounds`.

**Bài 2 (Viết locator bền nhất).**
Với cây UI Login ở Phần 3.4, viết locator `AppiumBy...` trỏ **duy nhất** tới:
(a) ô password, (b) nút "ĐĂNG NHẬP", (c) checkbox "Ghi nhớ đăng nhập", (d) link "Quên mật khẩu?". Với mỗi câu, ưu tiên locator **bền nhất** theo thứ tự ở Phần 4.3.

**Bài 3 (Đếm số khớp).**
Cũng với cây UI đó, cho biết mỗi locator sau khớp **bao nhiêu** View, và **là View nào**:
(a) `AppiumBy.className("android.widget.EditText")`
(b) `AppiumBy.className("android.widget.Button")`
(c) `AppiumBy.accessibilityId("test-Username")`
(d) `AppiumBy.id("com.example.app:id/remember")`
(e) `AppiumBy.xpath("//android.widget.TextView")`

**Bài 4 (Sửa locator xấu).**
Một bạn viết locator sau để trỏ tới nút "ĐĂNG NHẬP":
`AppiumBy.xpath("/hierarchy/android.widget.FrameLayout/android.widget.LinearLayout/android.widget.Button")`.
Locator này có thể chạy đúng không? Có điểm gì **chưa tối ưu / dễ gãy**? Hãy đề xuất một locator **tốt hơn** và giải thích. (Gợi ý: nghĩ tới chuyện dev thêm một lớp layout, hoặc đổi ngôn ngữ.)

**Bài 5 (Quan hệ cây UI).**
Với cây UI Login ở Phần 3.4: (a) `LinearLayout (login_container)` là **con** của View nào? (b) Ô username và ô password có **quan hệ** gì với nhau? (c) Liệt kê tất cả **con trực tiếp** của `LinearLayout (login_container)`.

**Bài 6 (Mindset — chọn case để automate).**
Với mỗi tình huống, quyết định **NÊN** hay **KHÔNG nên** ưu tiên automate ở thời điểm hiện tại, và giải thích ngắn:
(a) Luồng đăng nhập của app, chạy lại mỗi lần build, đã ổn định 6 tháng.
(b) Màn hình "khuyến mãi Tết" chỉ dùng 1 tuần rồi gỡ.
(c) Test đăng nhập vân tay (fingerprint) trên thiết bị thật.
(d) Kiểm tra danh sách 40 sản phẩm hiển thị đúng tên & giá sau khi lọc.
(e) Đánh giá "animation chuyển trang có mượt và đẹp không".

**Bài 7 (Appium Inspector — làm thật).**
Mở Appium Inspector, Start Session vào **Sauce Labs My Demo App**, mở màn hình **Login**. Dùng Inspector soi và ghi lại **locator** (ưu tiên accessibility id) cho: (a) ô Username, (b) ô Password, (c) nút Login. Sau đó dùng **Search for element** để xác nhận mỗi locator khớp đúng **1** element.

**Bài 8 (Tổng hợp — nhiều locator cho 1 element).**
Với **ô Username** trong cây UI Login ở Phần 3.4, hãy viết **4 locator KHÁC NHAU** cùng trỏ tới nó (dùng ít nhất 3 chiến lược khác nhau: accessibilityId, id, androidUIAutomator, xpath). Sau đó **xếp hạng** từ **bền nhất → dễ gãy nhất** và giải thích ngắn gọn từng cái. (Làm được bài này là bạn đã "chốt" Giai đoạn 0.)

---

<a id="8"></a>
## 🧪 Phần 8 — Quiz tự đánh giá

> Chọn đáp án rồi đối chiếu [Phần 10](#10). Làm nghiêm túc, không xem trước.

**Câu 1.** Phát biểu nào **ĐÚNG** về automation test mobile?
- A. Automation thay thế hoàn toàn manual test.
- B. Mọi test case đều nên được automate.
- C. Automation phù hợp nhất cho các case regression, ổn định, chạy lặp trên nhiều thiết bị.
- D. Automation không cần biết lập trình.

**Câu 2.** Vì sao trên mobile **tuyệt đối tránh** chạm theo toạ độ (x, y) cố định?
- A. Vì toạ độ khó gõ.
- B. Vì toạ độ đổi theo độ phân giải/kích thước từng thiết bị → test gãy trên máy khác.
- C. Vì Appium không hỗ trợ toạ độ.
- D. Vì toạ độ luôn sai.

**Câu 3.** Thuộc tính nào **bền nhất** để làm locator cho một View Android?
- A. `bounds` (toạ độ khung).
- B. `text` (chữ hiển thị).
- C. `content-desc` (accessibility id) hoặc `resource-id`.
- D. `class` (như `android.widget.EditText`).

**Câu 4.** Trong cây UI Login ở Phần 3.4, `AppiumBy.className("android.widget.EditText")` khớp bao nhiêu View?
- A. 0
- B. 1
- C. 2
- D. 3

**Câu 5.** Câu nào **ĐÚNG** về locator dùng `text` (ví dụ text = "ĐĂNG NHẬP")?
- A. Rất bền, nên luôn ưu tiên.
- B. Có thể **gãy khi app đổi ngôn ngữ** (ĐĂNG NHẬP → LOGIN), nên kém bền hơn accessibility id.
- C. Không bao giờ dùng được.
- D. Giống hệt `resource-id`.

**Câu 6.** Cây UI của một màn hình app Android là gì?
- A. Một ảnh chụp màn hình.
- B. Một file APK.
- C. Cấu trúc **cây** các **View/ViewGroup** lồng nhau mà Android dựng ra, có thuộc tính đọc được.
- D. Một loại CSS selector.

**Câu 7.** Địa chỉ mặc định của Appium Server (bản 2) là gì?
- A. `http://127.0.0.1:4723`
- B. `http://127.0.0.1:4723/wd/hub`
- C. `http://localhost:8080`
- D. `http://127.0.0.1:9515`

**Câu 8.** Bạn muốn "soi" một element trong app để đọc `content-desc` và `resource-id`. Công cụ nào phù hợp nhất?
- A. Chrome DevTools (F12)
- B. Appium Inspector
- C. Notepad
- D. Android Studio Profiler

**Câu 9.** Lệnh nào kiểm tra máy tính đã "nhìn thấy" emulator/thiết bị Android chưa?
- A. `appium -v`
- B. `adb devices`
- C. `java -version`
- D. `npm -v`

**Câu 10.** Sau khi cài Appium 2, để điều khiển được app **Android** bạn cần cài thêm gì?
- A. Không cần gì thêm.
- B. Driver **XCUITest**.
- C. Driver **UiAutomator2** (`appium driver install uiautomator2`).
- D. Chrome DevTools.

---

<a id="9"></a>
## ✅ Phần 9 — Đáp án bài tập

**Bài 1.**
(a) `class` = `android.widget.EditText`.
(b) `resource-id` = `com.shop.app:id/email`.
(c) `content-desc` (accessibility id) = `test-Email`.
(d) Bền nhất: **`content-desc="test-Email"`** → dùng `AppiumBy.accessibilityId("test-Email")`. Lý do: accessibility id thường do dev cố ý đặt cho test, **không đổi theo ngôn ngữ**, ổn định khi giao diện thay đổi. (`resource-id="com.shop.app:id/email"` cũng rất tốt, hạng nhì.)
(e) Không dùng `bounds` vì nó là **toạ độ pixel** — đổi theo độ phân giải/kích thước từng máy → locator gãy ngay trên thiết bị khác.

**Bài 2.** (Có thể nhiều đáp án đúng; đây là lựa chọn bền nhất.)
- (a) Ô password: `AppiumBy.accessibilityId("test-Password")` (hoặc `AppiumBy.id("com.example.app:id/password")`).
- (b) Nút "ĐĂNG NHẬP": `AppiumBy.accessibilityId("test-LOGIN")` (hoặc `AppiumBy.id("com.example.app:id/login_button")`).
- (c) Checkbox "Ghi nhớ": `AppiumBy.id("com.example.app:id/remember")` — vì `content-desc` của nó **để trống**, nên dùng `resource-id`.
- (d) Link "Quên mật khẩu?": `AppiumBy.accessibilityId("test-Forgot password")` (hoặc `AppiumBy.id("com.example.app:id/forgot")`).

**Bài 3.**
- (a) `className("android.widget.EditText")` → **2** View: ô username và ô password.
- (b) `className("android.widget.Button")` → **1** View: nút "ĐĂNG NHẬP".
- (c) `accessibilityId("test-Username")` → **1** View: ô username.
- (d) `id("com.example.app:id/remember")` → **1** View: checkbox "Ghi nhớ".
- (e) `xpath("//android.widget.TextView")` → **2** View: tiêu đề "Đăng nhập" và link "Quên mật khẩu?" (cả hai đều là `TextView`).

**Bài 4.**
- Locator XPath tuyệt đối này **có thể chạy đúng** (trỏ tới Button là con của LinearLayout con của FrameLayout). Nhưng **rất dễ gãy** và chưa tối ưu vì:
  - **Phụ thuộc cấu trúc cây:** chỉ cần dev thêm/bớt một lớp layout (ví dụ bọc thêm một `LinearLayout`), đường dẫn sai ngay.
  - **Chậm hơn:** XPath phải duyệt cả cây; accessibility id/id thì tra thẳng.
  - **Không rõ ràng:** người đọc không biết nó trỏ tới cái gì.
- **Locator tốt hơn:** `AppiumBy.accessibilityId("test-LOGIN")` (hoặc `AppiumBy.id("com.example.app:id/login_button")`) — ngắn, bền, rõ ràng, không phụ thuộc vị trí.

**Bài 5.**
- (a) `LinearLayout (login_container)` là **con trực tiếp** của `FrameLayout` (nút gốc).
- (b) Ô username và ô password là **anh em (sibling)** — cùng là con trực tiếp của `LinearLayout (login_container)`.
- (c) Con trực tiếp của `LinearLayout (login_container)`, gồm **6** View: `TextView` (tiêu đề "Đăng nhập"), `EditText` (username), `EditText` (password), `CheckBox` (remember), `Button` (login_button), `TextView` (forgot — "Quên mật khẩu?").

**Bài 6.**
- (a) **NÊN** — luồng cốt lõi, ổn định lâu, chạy lại mỗi build. Đây là ứng viên automate hoàn hảo (nhiều dấu ✅).
- (b) **KHÔNG** — chỉ dùng 1 tuần rồi gỡ, chi phí viết script lớn hơn lợi ích. Test tay là đủ.
- (c) **KHÔNG (chưa)** — vân tay là **sinh trắc học/phần cứng**, emulator không mô phỏng tốt và tính năng này vốn thiết kế để chặn máy. Nên test tay trên thiết bị thật.
- (d) **NÊN** — nhiều dữ liệu (40 sản phẩm), kết quả **xác định** (tên & giá đúng/sai rõ ràng), làm tay rất tốn công. Ứng viên tốt (data-driven).
- (e) **KHÔNG** — đánh giá **cảm quan** (mượt/đẹp), máy không "cảm" được. Việc của manual/exploratory.

**Bài 7.** (Giá trị tham khảo cho Sauce Labs My Demo App — hãy **tự soi để xác nhận**, vì có thể đổi theo version.)
- (a) Ô Username: `AppiumBy.accessibilityId("test-Username")`.
- (b) Ô Password: `AppiumBy.accessibilityId("test-Password")`.
- (c) Nút Login: `AppiumBy.accessibilityId("test-LOGIN")`.
- Dùng **Search for element** với chiến lược Accessibility ID cho từng giá trị → mỗi cái kỳ vọng khớp **1** element trên màn hình Login.

**Bài 8.** (Ví dụ 4 locator cho ô Username ở Phần 3.4, xếp từ bền → dễ gãy.)

| Hạng | Locator (Java) | Vì sao |
|:----:|----------------|--------|
| 1 (bền nhất) | `AppiumBy.accessibilityId("test-Username")` | accessibility id, dành cho test, không đổi theo ngôn ngữ |
| 2 | `AppiumBy.id("com.example.app:id/username")` | `resource-id` duy nhất, rất ổn định |
| 3 | `AppiumBy.androidUIAutomator("new UiSelector().resourceId(\"com.example.app:id/username\")")` | Tương đương id nhưng dài hơn; vẫn dựa vào thuộc tính ổn định |
| 4 (dễ gãy nhất) | `AppiumBy.xpath("(//android.widget.EditText)[1]")` | Phụ thuộc **thứ tự/vị trí** — đổi layout hoặc thêm ô nhập là gãy |

Cả 4 đều trỏ đúng ô username. **Bài học:** cùng trỏ 1 element nhưng độ bền rất khác nhau — luôn chọn locator dựa trên thuộc tính ổn định (`content-desc`, `resource-id`), tránh vị trí. Lưu ý `AppiumBy.className("android.widget.EditText")` **không** hợp lệ ở đây vì nó khớp **2** View (cả password) → không "duy nhất".

---

<a id="10"></a>
## 🎓 Phần 10 — Đáp án quiz

| Câu | Đáp án | Giải thích ngắn |
|:---:|:------:|-----------------|
| 1 | **C** | Automation mạnh nhất ở regression/case ổn định chạy lặp trên nhiều thiết bị. A, B, D là kỳ vọng sai. |
| 2 | **B** | Toạ độ đổi theo độ phân giải/máy → chạm toạ độ cố định gãy ngay trên máy khác. Luôn dùng locator. |
| 3 | **C** | `content-desc` (accessibility id) và `resource-id` bền nhất. `text` đổi theo ngôn ngữ, `class` trùng, `bounds` đổi theo màn hình. |
| 4 | **C** | Cả ô username và password đều là `android.widget.EditText` → khớp **2**. |
| 5 | **B** | Locator theo `text` gãy khi đổi ngôn ngữ (ĐĂNG NHẬP → LOGIN) → kém bền hơn accessibility id. |
| 6 | **C** | Cây UI = cấu trúc cây các View/ViewGroup lồng nhau Android dựng ra, có thuộc tính đọc được. |
| 7 | **A** | Appium 2 dùng `http://127.0.0.1:4723` (bỏ đuôi `/wd/hub` của bản 1.x). |
| 8 | **B** | **Appium Inspector** là công cụ soi element của app (vai trò như F12 bên web). |
| 9 | **B** | `adb devices` liệt kê thiết bị/emulator đang kết nối. |
| 10 | **C** | Điều khiển app Android cần driver **UiAutomator2**. XCUITest là cho iOS. |

**Thang tự đánh giá:**
- **9–10 đúng:** Xuất sắc — bạn nắm chắc nền tảng, sẵn sàng qua Giai đoạn 1.
- **6–8 đúng:** Khá — xem lại các câu sai và phần lý thuyết tương ứng.
- **Dưới 6:** Hãy đọc lại Phần 1–5 và **làm lại bài thực hành Appium Inspector**. Đừng vội qua giai đoạn sau — nền tảng này quá quan trọng.

---

<a id="11"></a>
## 🏁 Phần 11 — Checklist Milestone Giai đoạn 0

Bạn hoàn thành Giai đoạn 0 khi tick được **TẤT CẢ** ô dưới đây. Hãy thành thật với chính mình.

### 🧠 Mindset
- [ ] Giải thích được (bằng lời của mình) **vì sao học automation mobile** và nó **khác** manual thế nào.
- [ ] Nêu được ít nhất **3 tiêu chí** để quyết định một case **có nên** automate không.
- [ ] Kể được ít nhất **2 đặc thù/thách thức riêng của test mobile** (đa thiết bị, gesture, permission, toạ độ...).
- [ ] Kể được ít nhất **2 kỳ vọng sai** về automation mà mình đã bỏ.

### 💻 Môi trường (macOS hoặc Windows)
- [ ] `java -version` ra bản **17+** (và `javac -version` chạy được).
- [ ] Mở được **IntelliJ IDEA Community**.
- [ ] Cài xong **Android Studio + SDK**; `echo $ANDROID_HOME` (mac) / `echo $env:ANDROID_HOME` (win) ra đúng đường dẫn.
- [ ] `adb --version` chạy được và `adb devices` **thấy emulator/thiết bị**.
- [ ] Tạo & khởi động được **một máy ảo Android (AVD)**.
- [ ] `node -v` ra **v18+**; `appium -v` ra **2.x**; `appium driver list --installed` có **uiautomator2**.
- [ ] Chạy được `appium` server (thấy dòng `...http://127.0.0.1:4723`).
- [ ] Cài & mở được **Appium Inspector**.
- [ ] Cài được **APK mẫu** vào emulator bằng `adb install` (thấy `Success`).

### 🧱 Cấu trúc UI Android
- [ ] Giải thích được app là **cây View/ViewGroup** (tương tự cây DOM).
- [ ] Đọc được một element và chỉ ra: `class`, `resource-id`, `content-desc`, `text`.
- [ ] Giải thích được **vì sao `content-desc`/`resource-id` tốt cho automation** còn `text`/`class`/`bounds` dễ gãy.

### 🎯 Locator Appium
- [ ] Viết được locator bằng `AppiumBy.accessibilityId`, `AppiumBy.id`, `AppiumBy.className`, `AppiumBy.xpath`.
- [ ] Nêu đúng **thứ tự ưu tiên** locator (accessibility id → resource-id → ... → xpath; tránh toạ độ).
- [ ] Với một element bất kỳ, viết được **ít nhất 2 locator đúng** và chọn được cái bền hơn.

### 🔧 Appium Inspector (bài chốt)
- [ ] **Start Session** được vào app mẫu bằng bộ Capabilities cơ bản.
- [ ] **Soi** được một element bất kỳ và đọc đúng `content-desc`/`resource-id`/`class` của nó.
- [ ] Tự tìm được locator của **ô username, ô password, nút login** trên Sauce Labs My Demo App.
- [ ] Viết được **4 locator khác nhau** cùng trỏ tới một element và giải thích cái nào bền hơn (Bài tập 8).

> 🎉 **Tick hết? Chúc mừng — bạn đã hoàn thành Giai đoạn 0!** Bạn đã có xưởng làm việc mobile sẵn sàng, tư duy đúng, và — quan trọng nhất — **đọc được cấu trúc bên trong của một app Android**. Đây chính là nền tảng mà nhiều người bỏ qua rồi vấp ngã khi viết code Appium. Bạn đã đi đúng đường. Tiếp theo: **Giai đoạn 1 — Java cơ bản cho Tester.** 🚀

---

<a id="12"></a>
## 📚 Phần 12 — Tài nguyên tham khảo

**Cài đặt & công cụ:**
- Eclipse Adoptium Temurin (JDK): [https://adoptium.net/temurin/releases/](https://adoptium.net/temurin/releases/)
- IntelliJ IDEA Community: [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/)
- Android Studio (kèm SDK, adb, emulator): [https://developer.android.com/studio](https://developer.android.com/studio)
- Node.js (LTS): [https://nodejs.org/](https://nodejs.org/)
- Homebrew (macOS): [https://brew.sh/](https://brew.sh/)

**Appium:**
- Trang chủ & tài liệu Appium: [https://appium.io/docs/en/latest/](https://appium.io/docs/en/latest/)
- Cài đặt Appium (Quickstart): [https://appium.io/docs/en/latest/quickstart/](https://appium.io/docs/en/latest/quickstart/)
- Driver UiAutomator2 (Android): [https://github.com/appium/appium-uiautomator2-driver](https://github.com/appium/appium-uiautomator2-driver)
- Appium Inspector (tải bản desktop): [https://github.com/appium/appium-inspector/releases](https://github.com/appium/appium-inspector/releases)
- Appium Java Client (thư viện Java): [https://github.com/appium/java-client](https://github.com/appium/java-client)

**Android nền tảng:**
- Cấu hình biến môi trường (ANDROID_HOME): [https://developer.android.com/tools/variables](https://developer.android.com/tools/variables)
- adb (Android Debug Bridge): [https://developer.android.com/tools/adb](https://developer.android.com/tools/adb)
- Tạo & quản lý AVD (Emulator): [https://developer.android.com/studio/run/managing-avds](https://developer.android.com/studio/run/managing-avds)
- UiAutomator UiSelector (cho `androidUIAutomator`): [https://developer.android.com/reference/androidx/test/uiautomator/UiSelector](https://developer.android.com/reference/androidx/test/uiautomator/UiSelector)

**App mẫu để luyện tập (sân tập cả khóa):**
- Sauce Labs My Demo App (React Native): [https://github.com/saucelabs/my-demo-app-rn/releases](https://github.com/saucelabs/my-demo-app-rn/releases)
- Sauce Labs Sample App (native, bản cũ): [https://github.com/saucelabs/sample-app-mobile/releases](https://github.com/saucelabs/sample-app-mobile/releases)
- Appium ApiDemos (app demo kinh điển): [https://github.com/appium/android-apidemos/releases](https://github.com/appium/android-apidemos/releases)

**Đón đầu (chưa cần đọc kỹ, để bookmark):**
- Locator strategies trong Appium: [https://appium.io/docs/en/latest/guides/finding-elements/](https://appium.io/docs/en/latest/guides/finding-elements/)
- Appium Java Client — Capabilities & Options: [https://github.com/appium/java-client](https://github.com/appium/java-client)

---

> 💪 **Lời nhắn cuối:** Giai đoạn 0 nghe có vẻ "chưa code gì" nhưng thực ra là giai đoạn quyết định. Người đi đường dài trong automation mobile là người **đọc được cây UI của app trong giấc ngủ**. Mỗi khi mở một app bất kỳ, hãy tập phản xạ bật Appium Inspector, soi vài element, thử vài locator. Biến nó thành thói quen — và code Appium sau này sẽ nhẹ như trở bàn tay. Hẹn gặp ở Giai đoạn 1! ☕

---

*Học liệu Giai đoạn 0 — Khóa Automation Test Mobile với Java + Appium (Android).*

