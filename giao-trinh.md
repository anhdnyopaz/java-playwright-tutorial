# 🎯 Giáo Trình Automation Test với Java + Playwright (Dành cho Tester)

> **Đối tượng:** Tester (manual) muốn chuyển sang / bổ sung kỹ năng automation.
> **Thời lượng:** ~14–18 tuần (học 1–2 giờ/ngày). Đây là mức **tối thiểu, dễ bị hụt** với người chưa từng code — hãy coi mốc thời gian là mục tiêu linh hoạt, không phải deadline.
> **Kỳ vọng thực tế:** Học xong bạn sẽ ở ngưỡng **junior automation tự tin / job-ready ở mức entry**, tự xây được framework UI + API chạy trên CI. Để làm chủ dự án production thật vẫn cần thêm kinh nghiệm thực chiến.

> **📢 Phiên bản 2** — đã bổ sung sau vòng review độc lập: Lambda, HTML/DOM/DevTools, Strict Mode, phân loại Assertion, quản lý Secret, Thread-safety cho parallel, debug bằng breakpoint, flaky test, test data management, Git nhóm & chuẩn bị phỏng vấn.

---

## 📌 Lộ trình tổng quan

| Giai đoạn | Nội dung | Thời gian | Kết quả đạt được |
|-----------|----------|-----------|------------------|
| **0** | Mindset, môi trường & nền tảng Web (HTML/DOM/DevTools) | 1 tuần | Máy sẵn sàng + đọc được DOM |
| **1** | Java cơ bản cho Tester (gồm Lambda, Generics) | 3 tuần | Đọc/viết được code Java |
| **2** | Công cụ nền tảng (Maven, Git, JUnit/TestNG) | 1 tuần | Quản lý & chạy được test project |
| **3** | Playwright cơ bản (Locator, Strict Mode, Assertion) | 2 tuần | Viết được test UI đúng chuẩn |
| **4** | Playwright nâng cao + chống Flaky test | 2 tuần | Xử lý mọi tình huống thực tế |
| **5** | Thiết kế Framework (POM, Factory, Test Data, Secret) | 2–3 tuần | Framework chuẩn production |
| **6** | API Testing + Report + Parallel (thread-safe) | 2 tuần | Test tích hợp & báo cáo |
| **7** | CI/CD (GitHub Actions) + Git nhóm | 1 tuần | Test tự chạy tự động |
| **8** | Dự án tổng hợp (Capstone) + Chuẩn bị phỏng vấn | 2 tuần | Portfolio & sẵn sàng đi làm |

---

## 🧭 Giai đoạn 0 — Mindset, Môi trường & Nền tảng Web (1 tuần)

### Tư duy cần có
- Automation **không thay thế** manual test — nó giải phóng bạn khỏi việc lặp lại (regression).
- Không phải test case nào cũng nên automate. Ưu tiên: regression, smoke, các luồng ổn định, chạy nhiều lần.
- Automation là **lập trình** → cần tư duy code, không chỉ "click chuột".

### Cài đặt môi trường
1. **JDK 17+** (LTS) — cài từ [Adoptium Temurin](https://adoptium.net/)
2. **IntelliJ IDEA Community** (miễn phí) — IDE tốt nhất cho Java
3. **Git** — quản lý mã nguồn
4. **Maven** (thường đi kèm IntelliJ) — quản lý thư viện
5. **Node.js** (tùy chọn — để dùng Playwright codegen/inspector tiện lợi)

✅ **Checklist môi trường:** Chạy được `java -version`, `mvn -version`, mở được IntelliJ và tạo project "Hello World".

### 🆕 Nền tảng Web — BẮT BUỘC trước khi học locator
> Bạn không thể viết locator tốt nếu không đọc được cấu trúc trang. Đây là tiền đề bị nhiều người bỏ qua rồi vấp ở Playwright.
- **HTML cơ bản:** thẻ (`<div>`, `<button>`, `<input>`, `<a>`), thuộc tính (`id`, `class`, `name`, `data-*`)
- **CSS Selector cơ bản:** `#id`, `.class`, `tag`, `[attribute=value]`, quan hệ cha-con
- **DOM là gì** — cây cấu trúc trang mà Playwright thao tác
- **Chrome DevTools (F12):**
  - Tab **Elements** — inspect element, đọc HTML/attribute
  - Copy selector, tự viết CSS selector và test bằng `$$("selector")` trong Console
  - Tab **Network** — xem request/response API (cần cho API test & mock sau này)

**Bài tập:**
- Mở [SauceDemo](https://www.saucedemo.com/), F12, tìm `id`/`class` của ô username, password, nút login
- Viết 5 CSS selector khác nhau trỏ tới cùng một nút và test trong Console

✅ **Milestone GĐ0:** Inspect được element bất kỳ, đọc hiểu attribute, tự viết được CSS selector.

---

## ☕ Giai đoạn 1 — Java cơ bản cho Tester (3 tuần)

> Bạn **không cần** trở thành lập trình viên Java pro. Chỉ cần đủ để đọc, viết và debug test. Nhưng đừng bỏ qua giai đoạn này — thiếu Java là lý do #1 khiến automation không mở rộng/bảo trì được.

### Tuần 1 — Nền tảng cú pháp
- Biến, kiểu dữ liệu (`int`, `String`, `boolean`, `double`)
- Toán tử, câu điều kiện (`if/else`, `switch`)
- Vòng lặp (`for`, `while`, `for-each`)
- Mảng và `List`, `Map` (collection cơ bản)
- Method (hàm): tham số, giá trị trả về

**Bài tập:** Viết hàm kiểm tra số chẵn/lẻ; duyệt `List<String>` lọc tên dài > 5; tạo `Map<String, Integer>` lưu tên & tuổi.

### Tuần 2 — Lập trình hướng đối tượng (OOP)
> **Quan trọng nhất** cho automation vì framework dựa hoàn toàn vào OOP.
- Class & Object, thuộc tính (field) & phương thức (method), Constructor
- `private/public`, getter/setter (Encapsulation)
- Kế thừa (Inheritance) — nền tảng cho BaseTest, BasePage
- Interface & Abstract class
- `static` — khi nào dùng

**Bài tập:** Tạo class `User` đầy đủ; tạo `BasePage` và `LoginPage extends BasePage`.

### Tuần 3 — Java THỰC DỤNG cho automation
> Phần này chứa những thứ Playwright dùng liên tục mà người mới hay hổng.
- **🆕 Lambda & Functional Interface** — **CỰC KỲ QUAN TRỌNG.** Playwright Java dùng lambda ở khắp nơi:
  ```java
  page.onDialog(dialog -> dialog.accept());              // callback
  page.waitForResponse("**/api/users", () -> page.click("#load")); // chờ có điều kiện
  ```
  Hiểu cú pháp `() ->` và `x -> ...` là bắt buộc, nếu không bạn sẽ copy code mà không hiểu gì.
- **🆕 Generics cơ bản** (`List<T>`, `ThreadLocal<Page>`) — để đọc hiểu code framework
- **🆕 Enum** — dùng cho BrowserType, Environment (dev/staging/prod)
- Exception handling (`try/catch/finally`, `try-with-resources`)
- Đọc/ghi file cơ bản (chuẩn bị cho data-driven)
- Stream API cơ bản (`filter`, `map`, `collect`)
- Annotation là gì (`@Test`, `@Override`…)
- **🆕 Debug bằng IntelliJ** — đặt **breakpoint**, chạy Debug mode, **step over/into**, xem giá trị biến, **Evaluate Expression**. Đây là kỹ năng debug hằng ngày, quan trọng ngang việc đọc stack trace.

📚 **Tài nguyên:** [W3Schools Java](https://www.w3schools.com/java/), Java full course (freeCodeCamp YouTube), sách *Head First Java*.

✅ **Milestone GĐ1:** Viết được class có kế thừa; **hiểu và viết được lambda**; đặt breakpoint debug một chương trình; đọc hiểu stack trace.

---

## 🛠️ Giai đoạn 2 — Công cụ nền tảng (1 tuần)

### Maven (quản lý dependency & build)
- Cấu trúc project Maven (`src/main/java`, `src/test/java`, `pom.xml`)
- `pom.xml`: dependency, plugin là gì; lệnh `mvn clean`, `mvn test`, `mvn compile`
- Thêm thư viện từ [Maven Central](https://central.sonatype.com/)

### Git (bắt buộc)
- `clone`, `add`, `commit`, `push`, `pull`; branch & merge cơ bản
- `.gitignore` (bỏ qua `target/`, report, **file chứa secret**)

### Test Runner: JUnit 5 hoặc TestNG
> Khuyến nghị **TestNG** nếu ưu tiên automation (parallel & data provider mạnh) hoặc **JUnit 5** nếu thích hiện đại/phổ biến. Chọn **một** để bắt đầu.
- Annotation: `@Test`, `@BeforeEach/@BeforeMethod`, `@AfterEach/@AfterMethod`, `@BeforeAll/@BeforeClass`
- Assertion cơ bản: `assertEquals`, `assertTrue`
- Grouping, ordering, disable test; Data provider / Parameterized test

**Bài tập:** Tạo project Maven, thêm JUnit/TestNG, viết 5 test hàm toán học, chạy `mvn test`.

✅ **Milestone GĐ2:** Tạo project Maven, viết test, chạy pass/fail, commit lên Git.

---

## 🎭 Giai đoạn 3 — Playwright Cơ Bản (2 tuần)

### Tuần 1 — Làm quen & Locator
- Playwright là gì, tại sao chọn (nhanh, auto-wait, đa trình duyệt, screenshot/video/trace sẵn có)
- Thêm dependency `com.microsoft.playwright:playwright`, cài browser (`playwright install`)
- Kiến trúc: `Playwright` → `Browser` → `BrowserContext` → `Page`
  > ⚠️ **Lưu ý binding Java:** khác bản JavaScript, Java **không có file `playwright.config`**. Vòng đời browser/context/page bạn phải tự quản lý thủ công trong code (BaseTest / Factory) — sẽ học ở GĐ5.
- Test đầu tiên:
  ```java
  try (Playwright playwright = Playwright.create()) {
      Browser browser = playwright.chromium().launch(
          new BrowserType.LaunchOptions().setHeadless(false));
      Page page = browser.newPage();
      page.navigate("https://playwright.dev");
      System.out.println(page.title());
      browser.close();
  }
  ```
- **Playwright Codegen** — công cụ ghi thao tác thành code (học nhanh cách viết locator)
- **Locators** (kỹ năng cốt lõi):
  - Thứ tự ưu tiên: `getByRole()` > `getByLabel()` > `getByPlaceholder()` > `getByText()` > `getByTestId()` > CSS/XPath
  - CSS selector & XPath (chỉ khi bắt buộc; tránh XPath phụ thuộc index)

### Tuần 2 — Hành động, Strict Mode & Assertion
- Hành động: `click()`, `fill()`, `check()`, `selectOption()`, `hover()`
  > ⚠️ Dùng `fill()` để nhập text. **`type()` đã deprecated** — nếu cần gõ từng phím dùng `pressSequentially()`.
- **Auto-waiting** — Playwright tự chờ element (ưu điểm lớn so với Selenium) → **không dùng `Thread.sleep()`**
- **🆕 Strict Mode** — QUAN TRỌNG: nếu một locator khớp **nhiều hơn 1 element**, Playwright báo lỗi `strict mode violation`. Đây là lỗi #1 người mới gặp. Cách xử lý: viết locator cụ thể hơn, hoặc dùng `.first()`, `.nth()`, `.filter()`.
- **🆕 Phân biệt 2 loại Assertion (chống flaky):**
  | Loại | Ví dụ | Đặc điểm |
  |------|-------|----------|
  | **Web-first (TỰ RETRY)** | `assertThat(locator).isVisible()`, `.hasText()`, `.isEnabled()` | Tự chờ & retry tới timeout → **dùng cho UI động** |
  | **Assertion thường (KHÔNG retry)** | JUnit `assertEquals`, AssertJ | Kiểm tra tức thời → chỉ dùng cho giá trị đã chắc chắn (số, chuỗi tính toán) |
  - Dùng nhầm assertion thường trên UI đang load = **flaky test kinh điển**.
  - **Soft assertion** — gom nhiều lỗi, không dừng ngay ở lỗi đầu tiên.

**Bài tập:** Login SauceDemo hoàn chỉnh (dùng web-first assertion); thêm sản phẩm vào giỏ trên [Automation Exercise](https://automationexercise.com/); cố tình tạo locator khớp nhiều element để gặp & sửa lỗi strict mode.

**Trang luyện tập:** SauceDemo, [The-Internet Herokuapp](https://the-internet.herokuapp.com/), Automation Exercise, [OrangeHRM demo](https://opensource-demo.orangehrmlive.com/).

✅ **Milestone GĐ3:** Viết test login đúng chuẩn dùng web-first assertion; hiểu & xử lý được strict mode; phân biệt được khi nào dùng assertion nào.

---

## 🚀 Giai đoạn 4 — Playwright Nâng Cao + Chống Flaky (2 tuần)

### Tuần 1 — Locator nâng cao & tình huống thực tế
- **🆕 Locator nâng cao (dùng hằng ngày trong thực tế):**
  - `.filter(hasText / has)` — lọc trong danh sách
  - `.nth(i)`, `.first()`, `.last()` — chọn theo vị trí
  - **Chaining locator** — thu hẹp phạm vi (`row.getByRole("button")`)
  - **Xử lý danh sách phần tử:** `locator.all()`, `count()` — lặp qua bảng/list động
- Xử lý nhiều tab / popup / window; iframe (`frameLocator`)
- Dropdown, checkbox, radio, file upload/download, drag & drop
- Alert/dialog (`page.onDialog`), keyboard, mouse action
- Chụp screenshot & quay video test

### Tuần 2 — Công cụ mạnh & Chống Flaky
- **Trace Viewer** — "hộp đen" ghi lại toàn bộ test để debug (tính năng đắt giá nhất của Playwright)
- **Network interception** — mock/stub API response, chặn request
- **Authentication:** lưu & tái sử dụng session bằng `storageState` (không login lại mỗi test)
- Emulate device (mobile), geolocation, timezone; nhiều `BrowserContext` (test đa người dùng)
- **🆕 Flaky test & Test Isolation — kỹ năng phân biệt junior với người đi làm được:**
  - Nguyên nhân gốc: sai loại assertion, `Thread.sleep`, race condition, phụ thuộc dữ liệu/thứ tự
  - **Test độc lập (isolation):** mỗi test tự setup dữ liệu, không phụ thuộc test khác, chạy được đơn lẻ
  - Cấu hình **timeout** hợp lý; **retry** test fail; **quarantine** test flaky
  - Vì sao "chạy local pass nhưng CI fail" (headless, tốc độ, môi trường)

**Bài tập:** Test bảng dữ liệu động dùng `.filter()` + `all()`; mock API và verify UI hiển thị dữ liệu giả; lưu login state dùng lại; bật trace → gây lỗi → phân tích bằng Trace Viewer; viết lại một test flaky cho ổn định.

✅ **Milestone GĐ4:** Debug bằng Trace Viewer; xử lý iframe/popup/danh sách động; nhận diện & sửa được một test flaky.

---

## 🏗️ Giai đoạn 5 — Thiết Kế Framework (2–3 tuần)

> Đây là bước biến bạn từ "người viết script" thành "automation engineer".

### Tuần 1 — Page Object Model (POM) & vòng đời browser
- Vì sao cần POM: tách locator/logic khỏi test → dễ bảo trì
- Xây `BasePage` (method dùng chung); mỗi trang = một class (`LoginPage`, `HomePage`, `CartPage`)
- `BaseTest` — setup/teardown (khởi tạo & đóng Playwright/Browser/Context/Page)
- **🆕 Design Pattern áp dụng NGAY tại đây** (không để "sau khóa"):
  - **Factory Pattern** — `PlaywrightFactory` khởi tạo browser theo cấu hình
  - **Builder Pattern** — dựng test data linh hoạt
  - (Singleton dùng thận trọng — dễ gây lỗi khi parallel)

```
src/test/java/
├── base/          (BaseTest, BasePage)
├── factory/       (PlaywrightFactory)
├── pages/         (LoginPage, ProductsPage, CartPage)
├── tests/         (LoginTest, CheckoutTest)
├── utils/         (ConfigReader, ScreenshotUtil)
├── data/          (TestDataBuilder, DataProvider)
└── listeners/     (TestListener — auto screenshot khi fail)
```

### Tuần 2–3 — Nâng cấp framework
- **Data-driven testing:** đọc dữ liệu từ JSON (Jackson/Gson) / Excel (Apache POI) / CSV
- **🆕 Test Data Management (thực chiến):**
  - Sinh dữ liệu ngẫu nhiên bằng **Datafaker** (email, tên, số điện thoại) → tránh trùng dữ liệu
  - **Data Builder** dựng object test gọn gàng
  - **Dọn dữ liệu sau test** (cleanup) — tránh rác trên môi trường dùng chung
  - Tạo data qua **API** rồi verify trên **UI** (nhanh & ổn định hơn tạo qua UI)
- **Config đa môi trường:** `config.properties` (URL, browser, timeout theo dev/staging), đọc bằng `ConfigReader`
- **🆕 Quản lý Secret / Credential — BẮT BUỘC, đừng bỏ qua:**
  - ⛔ **KHÔNG hardcode** username/password/token/API key vào code hoặc commit lên Git
  - Đọc từ **biến môi trường** (`System.getenv()`) hoặc file cục bộ **được `.gitignore`**
  - Trên CI dùng **GitHub Secrets** (học kỹ ở GĐ7)
  - > ⚠️ Đặc biệt quan trọng vì cuối khóa bạn sẽ đẩy portfolio lên GitHub **public** — lộ mật khẩu là sự cố thật, hay gặp ở người mới.
- **🆕 Listener / Extension:** dùng TestNG `ITestListener` (hoặc JUnit `TestWatcher` Extension) để **tự động chụp screenshot + đính trace khi test fail**
- **Logging:** Log4j2 hoặc SLF4J
- Cấu trúc thư mục chuẩn, đặt tên nhất quán

**Bài tập:** Refactor toàn bộ test SauceDemo sang POM có Factory; chạy login với 3 bộ data từ JSON; sinh email ngẫu nhiên bằng Datafaker; đọc credential từ biến môi trường; cấu hình Listener auto-screenshot khi fail.

✅ **Milestone GĐ5:** Framework POM + Factory + data-driven; không có secret nào trong code; tự chụp screenshot khi fail.

---

## 🔗 Giai đoạn 6 — API Testing + Report + Parallel (2 tuần)

### Tuần 1 — API Testing & Report
- **API testing** với Playwright `APIRequestContext` hoặc **RestAssured**
  - GET/POST/PUT/DELETE, headers, body, status code, validate response (JSON path)
  - Kết hợp API + UI: tạo/dọn data qua API, chỉ verify phần cốt lõi trên UI
- **Reporting:**
  - **Allure Report** (đẹp, phổ biến nhất) — cài, tích hợp, xem report
  - Đính kèm screenshot/video/trace khi fail (nối với Listener ở GĐ5)

### Tuần 2 — Parallel & Cross-browser (thread-safe)
- **🆕 Parallel ĐÚNG CÁCH** — không chỉ "bật một flag":
  - Playwright Java **không** tự thread-safe. Chạy song song cần **`ThreadLocal<Page>` / `ThreadLocal<BrowserContext>`** trong Factory để mỗi thread có instance riêng
  - Cấu hình `parallel` trong TestNG (`suite`/`methods`) hoặc JUnit 5 (`@Execution(CONCURRENT)`)
  - Lỗi kinh điển khi làm sai: các test "giẫm chân" nhau, kết quả chập chờn
- **Cross-browser:** Chromium, Firefox, WebKit — tham số hóa browser
- Chạy test bằng Docker (nâng cao, tùy chọn)

**Bài tập:** Viết 5 API test cho [reqres.in](https://reqres.in/); tích hợp Allure có screenshot khi fail; chuyển framework sang chạy parallel với `ThreadLocal` và xác nhận không còn giẫm chân nhau.

✅ **Milestone GĐ6:** Test API + UI; Allure report có screenshot; chạy parallel ổn định nhờ ThreadLocal.

---

## ⚙️ Giai đoạn 7 — CI/CD + Git nhóm (1 tuần)

- **GitHub Actions** (dễ bắt đầu nhất):
  - Viết workflow chạy test tự động khi push / mở Pull Request
  - Chạy **headless** trên CI
  - **🆕 GitHub Secrets** — nạp credential an toàn vào CI (nối tiếp GĐ5)
  - Upload **artifact** (Allure report, trace, screenshot) để tải về xem
  - **🆕 Gotcha:** khớp **version Playwright ↔ version browser** trên CI (cài đúng browser cho version đang dùng)
- **🆕 Git làm việc nhóm (thực tế công việc):**
  - Branch strategy (feature branch), tạo **Pull Request**, code review
  - Xử lý **merge conflict**
  - Chạy test như một **gate** trước khi merge

**Bài tập:** Tạo GitHub Actions chạy test mỗi lần push + PR; nạp credential qua GitHub Secrets; upload Allure report làm artifact.

✅ **Milestone GĐ7:** Test tự chạy trên CI mỗi lần push/PR, secret an toàn, report tải về được.

---

## 🎓 Giai đoạn 8 — Dự Án Capstone + Chuẩn Bị Phỏng Vấn (2 tuần)

Chọn **1 web thật** (SauceDemo, Automation Exercise, hoặc OrangeHRM demo) và xây framework hoàn chỉnh.

**Yêu cầu dự án:**
- [ ] Framework theo POM + Factory
- [ ] 15–20 test case (login, search, add to cart, checkout, negative cases…)
- [ ] Data-driven + Datafaker (data tách khỏi code)
- [ ] Config đa môi trường
- [ ] Kết hợp UI + API test
- [ ] **Không có secret nào trong code** (dùng env var / GitHub Secrets)
- [ ] Allure report + auto-screenshot khi fail
- [ ] Chạy parallel thread-safe
- [ ] CI/CD trên GitHub Actions
- [ ] README.md mô tả rõ cách chạy
- [ ] Đẩy lên GitHub làm **portfolio**

### 🆕 Chuẩn bị phỏng vấn (đừng bỏ qua)
- **Cách trình bày capstone:** kể được "bài toán → giải pháp → kết quả", giải thích được **vì sao** chọn POM/Factory/ThreadLocal
- **Câu hỏi automation hay gặp:** auto-wait hoạt động thế nào? xử lý flaky test ra sao? khác biệt web-first vs assertion thường? parallel thread-safe thế nào? khi nào nên/không nên automate?
- Biết cách "bán" portfolio: demo được, nói được điểm mạnh của framework

👉 Đây chính là thứ để đưa vào CV và trả lời phỏng vấn.

---

## 🧩 Kỹ năng bổ trợ (học song song / sau khóa)

| Kỹ năng | Vì sao cần |
|---------|-----------|
| **SQL** (nên học sớm) | Verify dữ liệu trong DB — rất phổ biến trong công việc |
| **Docker** | Chạy test trong container, môi trường ổn định |
| **BDD - Cucumber** | Viết test theo Gherkin, làm việc với BA/PO |
| **Jira + Test Management** (Xray/TestRail) | Bối cảnh làm việc thật |
| **Visual regression** (`toHaveScreenshot`) / Accessibility | Kiểm thử nâng cao (tùy chọn) |

---

## ⚠️ Sai lầm thường gặp cần tránh

1. **Bỏ qua Java (nhất là Lambda), nhảy thẳng vào Playwright** → không hiểu code callback, không mở rộng được.
2. **Bỏ qua HTML/DOM/DevTools** → viết locator yếu, hay gãy.
3. **Dùng `Thread.sleep()` khắp nơi** → test chậm & flaky. Tin vào auto-wait.
4. **Dùng nhầm assertion thường trên UI động** thay vì web-first assertion → flaky.
5. **Không xử lý strict mode** → test đỏ vì locator khớp nhiều element.
6. **Hardcode mật khẩu và commit lên GitHub** → lộ credential, sự cố bảo mật thật.
7. **Parallel mà không dùng ThreadLocal** → các test giẫm chân nhau, kết quả chập chờn.
8. **Dùng XPath dài phụ thuộc index** (`//div[3]/span[2]`) → ưu tiên `getByRole`/`getByTestId`.
9. **Không dùng POM** → code lặp, sửa một chỗ phải sửa 10 nơi.
10. **Bỏ qua Trace Viewer & breakpoint** → mất hàng giờ debug thứ lẽ ra nhìn là ra.

---

## 📚 Tài nguyên chính thức (bookmark ngay)

- **Playwright Java Docs:** https://playwright.dev/java/docs/intro
- **Playwright API Reference:** https://playwright.dev/java/docs/api/class-playwright
- **JUnit 5:** https://junit.org/junit5/docs/current/user-guide/
- **TestNG:** https://testng.org/doc/
- **Allure:** https://allurereport.org/docs/
- **Datafaker:** https://www.datafaker.net/
- **Trang luyện tập:** SauceDemo, The-Internet Herokuapp, Automation Exercise, OrangeHRM demo, reqres.in

---

## 🗓️ Gợi ý lịch học mỗi ngày

| Thời gian | Hoạt động |
|-----------|-----------|
| 30 phút | Học lý thuyết (đọc docs / xem video) |
| 60 phút | **Code thực hành** (quan trọng nhất — 70% thời gian nên là code) |
| 15 phút | Ghi chú lại điều đã học + lỗi gặp phải |

> **Nguyên tắc vàng:** Học automation = **code mỗi ngày**. Đọc 10 tutorial không bằng tự tay viết 1 test và debug nó.

---

*Chúc bạn học tốt! Bắt đầu từ Giai đoạn 0 hôm nay. 🚀*
