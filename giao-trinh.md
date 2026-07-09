# 📱 Giáo Trình Automation Test với Java + Appium (Mobile - Android, Dành cho Tester)

> **Đối tượng:** Tester (manual) muốn chuyển sang / bổ sung kỹ năng **mobile automation**.
> **Nền tảng:** **Android trước** (iOS học sau — cần Mac + Xcode). Công cụ: **Appium 2.x + Appium Java Client + driver UiAutomator2**.
> **Thời lượng:** ~14–18 tuần (học 1–2 giờ/ngày). Đây là mức **tối thiểu, dễ bị hụt** với người chưa từng code — hãy coi mốc thời gian là mục tiêu linh hoạt, không phải deadline.
> **Kỳ vọng thực tế:** Học xong bạn sẽ ở ngưỡng **junior mobile automation tự tin / job-ready ở mức entry**, tự xây được framework Mobile UI + API chạy trên CI. Để làm chủ dự án production thật vẫn cần thêm kinh nghiệm thực chiến.

> **📢 Phiên bản mobile** — chuyển từ Playwright (web) sang Appium (mobile). Trọng tâm Android: cấu trúc UI Android, Capabilities/UiAutomator2Options, chiến lược locator mobile, cử chỉ (gestures) W3C Actions, context NATIVE_APP ↔ WEBVIEW, ThreadLocal cho parallel nhiều thiết bị, quản lý Secret, chống flaky, device farm & chuẩn bị phỏng vấn.

---

## 📌 Lộ trình tổng quan

| Giai đoạn | Nội dung | Thời gian | Kết quả đạt được |
|-----------|----------|-----------|------------------|
| **0** | Mindset mobile, môi trường (Android Studio + Appium) & cấu trúc UI Android | 1 tuần | Máy chạy được emulator + Appium, đọc được cây UI |
| **1** | Java cơ bản cho Tester (gồm Lambda, Generics) | 3 tuần | Đọc/viết được code Java |
| **2** | Công cụ nền tảng (Maven, Git, JUnit/TestNG + Appium Java Client) | 1 tuần | Quản lý & chạy được test project |
| **3** | Appium cơ bản (AndroidDriver, Capabilities, Locator, Inspector) | 2 tuần | Viết được test mobile đúng chuẩn |
| **4** | Appium nâng cao (gestures, context, lifecycle) + chống Flaky test | 2 tuần | Xử lý mọi tình huống thực tế trên app |
| **5** | Thiết kế Framework (POM mobile, DriverFactory, Test Data, Secret) | 2–3 tuần | Framework chuẩn production |
| **6** | API Testing + Report + Parallel nhiều thiết bị (thread-safe) | 2 tuần | Test tích hợp & báo cáo |
| **7** | CI/CD (GitHub Actions + emulator trên CI) + Device Farm + Git nhóm | 1 tuần | Test tự chạy tự động |
| **8** | Dự án tổng hợp (Capstone) + Chuẩn bị phỏng vấn | 2 tuần | Portfolio & sẵn sàng đi làm |

---

## 🧭 Giai đoạn 0 — Mindset, Môi trường & Nền tảng UI Android (1 tuần)

### Tư duy cần có
- Automation **không thay thế** manual test — nó giải phóng bạn khỏi việc lặp lại (regression) trên nhiều thiết bị/phiên bản OS.
- Không phải test case nào cũng nên automate. Ưu tiên: regression, smoke, các luồng ổn định, chạy nhiều lần trên nhiều thiết bị.
- Mobile automation là **lập trình** → cần tư duy code, không chỉ "chạm màn hình".
- **Đặc thù mobile** so với web: có nhiều thiết bị/độ phân giải/phiên bản Android, có **permission dialog**, cử chỉ (swipe/scroll), app **native / hybrid / webview**, vòng đời app (background/kill/reset). Đây là những thứ web không có.

### Cài đặt môi trường (Android)
Mobile automation cần **nhiều mảnh ghép** hơn web. Cài theo thứ tự:

1. **JDK 17+** (LTS) — cài từ [Adoptium Temurin](https://adoptium.net/). Đặt `JAVA_HOME`.
2. **IntelliJ IDEA Community** (miễn phí) — IDE tốt nhất cho Java.
3. **Android Studio** — kèm theo:
   - **Android SDK** (API level phù hợp, ví dụ Android 13/API 33)
   - **platform-tools** (chứa `adb` — công cụ giao tiếp với thiết bị)
   - **Android Emulator + AVD** (tạo một máy ảo Android để luyện tập)
   - Đặt biến môi trường `ANDROID_HOME` (hoặc `ANDROID_SDK_ROOT`) và thêm `platform-tools`, `emulator` vào `PATH`.
4. **Node.js LTS** — để cài Appium (Appium chạy trên Node).
5. **Appium Server 2.x**: `npm i -g appium`
6. **Driver UiAutomator2** (driver cho Android): `appium driver install uiautomator2`
7. **Appium Inspector** — công cụ GUI để soi cây UI & tìm locator (tải bản release trên GitHub).
8. **Một APK mẫu để luyện tập** — ví dụ **Sauce Labs My Demo App** (`mda-*.apk`) hoặc **ApiDemos** (app sample của Appium).

✅ **Checklist môi trường:**
- `java -version`, `mvn -version` chạy được.
- `adb devices` thấy emulator (sau khi khởi động AVD).
- `appium-doctor --android` (hoặc `appium driver doctor uiautomator2`) không còn lỗi đỏ.
- `appium` khởi động server ở `http://127.0.0.1:4723`.
- Cài được APK mẫu vào emulator: `adb install duong-dan/app.apk`.

```bash
# Kiểm tra thiết bị/emulator đang kết nối
adb devices

# Khởi động Appium server (mặc định cổng 4723)
appium

# Cài APK mẫu vào emulator
adb install ~/apk/mda-2.2.0-25.apk

# Lấy tên package & activity của app đang mở (hữu ích để cấu hình Capabilities)
adb shell dumpsys window | grep -E 'mCurrentFocus'
```

> 💡 **iOS học sau:** iOS cần **máy Mac + Xcode + driver XCUITest**. Cú pháp Appium gần giống nhau nên khi vững Android bạn chuyển sang iOS khá nhanh. Giáo trình này tập trung **Android trước**.

### 🆕 Nền tảng cấu trúc UI Android — BẮT BUỘC trước khi học locator
> Bạn không thể viết locator tốt nếu không đọc được cây UI của app. Đây là tiền đề bị nhiều người bỏ qua rồi vấp ở Appium (giống như web cần đọc DOM).

- **Cây UI Android** — màn hình app là một cây các **View** (giống DOM của web nhưng là các widget native).
- **Các thuộc tính quan trọng của element** (tương đương attribute HTML):
  - **`content-desc`** → dùng cho **accessibility id** (locator ưu tiên số 1).
  - **`resource-id`** → dùng cho **id** (ví dụ `com.example:id/login_button`).
  - **`class`** → className (ví dụ `android.widget.Button`, `android.widget.EditText`).
  - **`text`** → nội dung chữ hiển thị.
  - `clickable`, `enabled`, `displayed`, `bounds` (tọa độ) …
- **Công cụ soi UI:**
  - **Appium Inspector** — kết nối tới Appium session, chạm vào element để xem `content-desc`, `resource-id`, `class`, `text`, và gợi ý locator.
  - **`uiautomatorviewer`** (kèm Android SDK) hoặc **Layout Inspector** — chụp cây UI để đọc thuộc tính.
  - Lệnh nhanh: `adb shell uiautomator dump` rồi đọc file XML để thấy cấu trúc màn hình.

**Bài tập:**
- Khởi động emulator, cài **Sauce Labs My Demo App**, mở **Appium Inspector**, soi màn hình đăng nhập: tìm `content-desc`/`resource-id`/`text` của ô username, password và nút login.
- Viết ra 3 cách khác nhau để trỏ tới **cùng một nút** (accessibility id, id, XPath) và ghi chú cách nào ổn định nhất.

✅ **Milestone GĐ0:** Khởi động được emulator, chạy được Appium server, cài APK mẫu; dùng Appium Inspector soi được element bất kỳ, đọc hiểu `content-desc`/`resource-id`/`class`/`text`.

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
- Kế thừa (Inheritance) — nền tảng cho BaseTest, BasePage/BaseScreen
- Interface & Abstract class
- `static` — khi nào dùng

**Bài tập:** Tạo class `User` đầy đủ; tạo `BaseScreen` và `LoginScreen extends BaseScreen`.

### Tuần 3 — Java THỰC DỤNG cho automation
> Phần này chứa những thứ Appium dùng liên tục mà người mới hay hổng.
- **🆕 Lambda & Functional Interface** — **CỰC KỲ QUAN TRỌNG.** Appium/Selenium Java dùng lambda ở khắp nơi, đặc biệt trong **explicit wait**:
  ```java
  // Chờ tường minh bằng lambda (WebDriverWait dùng ExpectedConditions hoặc lambda tùy biến)
  WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
  wait.until(d -> d.findElement(AppiumBy.accessibilityId("login")).isDisplayed());
  ```
  Hiểu cú pháp `() ->` và `x -> ...` là bắt buộc, nếu không bạn sẽ copy code mà không hiểu gì.
- **🆕 Generics cơ bản** (`List<T>`, `ThreadLocal<AndroidDriver>`) — để đọc hiểu code framework.
- **🆕 Enum** — dùng cho `Platform` (ANDROID/IOS), `Environment` (dev/staging/prod).
- Exception handling (`try/catch/finally`, `try-with-resources`) — xử lý `NoSuchElementException`, `TimeoutException`.
- Đọc/ghi file cơ bản (chuẩn bị cho data-driven & đọc config).
- Stream API cơ bản (`filter`, `map`, `collect`).
- Annotation là gì (`@Test`, `@Override`…).
- **🆕 Debug bằng IntelliJ** — đặt **breakpoint**, chạy Debug mode, **step over/into**, xem giá trị biến, **Evaluate Expression**. Đây là kỹ năng debug hằng ngày, quan trọng ngang việc đọc stack trace.

📚 **Tài nguyên:** [W3Schools Java](https://www.w3schools.com/java/), Java full course (freeCodeCamp YouTube), sách *Head First Java*.

✅ **Milestone GĐ1:** Viết được class có kế thừa; **hiểu và viết được lambda**; đặt breakpoint debug một chương trình; đọc hiểu stack trace.

---

## 🛠️ Giai đoạn 2 — Công cụ nền tảng (1 tuần)

### Maven (quản lý dependency & build)
- Cấu trúc project Maven (`src/main/java`, `src/test/java`, `pom.xml`)
- `pom.xml`: dependency, plugin là gì; lệnh `mvn clean`, `mvn test`, `mvn compile`
- Thêm thư viện từ [Maven Central](https://central.sonatype.com/)
- **🆕 Thêm dependency Appium Java Client** (kéo theo Selenium):
  ```xml
  <dependency>
      <groupId>io.appium</groupId>
      <artifactId>java-client</artifactId>
      <version>9.3.0</version>
      <scope>test</scope>
  </dependency>
  ```
  > ⚠️ **Appium Java Client** phụ thuộc **Selenium**. Hãy để Maven tự kéo Selenium theo đúng version tương thích — **không** tự ghim lẫn lộn version Selenium khác, dễ vỡ.

### Git (bắt buộc)
- `clone`, `add`, `commit`, `push`, `pull`; branch & merge cơ bản
- `.gitignore` (bỏ qua `target/`, report, **file APK dung lượng lớn**, **file chứa secret**)

### Test Runner: JUnit 5 hoặc TestNG
> Khuyến nghị **TestNG** nếu ưu tiên automation (parallel & data provider mạnh — rất hợp chạy nhiều thiết bị) hoặc **JUnit 5** nếu thích hiện đại/phổ biến. Chọn **một** để bắt đầu.
- Annotation: `@Test`, `@BeforeEach/@BeforeMethod`, `@AfterEach/@AfterMethod`, `@BeforeAll/@BeforeClass`
- Assertion cơ bản: `assertEquals`, `assertTrue`
- Grouping, ordering, disable test; Data provider / Parameterized test

**Bài tập:** Tạo project Maven, thêm **Appium Java Client** + JUnit/TestNG, viết 5 test hàm toán học, chạy `mvn test`.

✅ **Milestone GĐ2:** Tạo project Maven có Appium Java Client, viết test, chạy pass/fail, commit lên Git.

---

## 📱 Giai đoạn 3 — Appium Cơ Bản (2 tuần)

### Tuần 1 — Kiến trúc, khởi tạo Driver & Locator
- **Appium là gì, tại sao chọn:** chuẩn mở, một API cho nhiều nền tảng (Android/iOS), dùng lại kỹ năng Selenium/WebDriver, cộng đồng lớn.
- **🆕 Kiến trúc client–server (rất quan trọng để không "học vẹt"):**
  - Test của bạn (**client**, Java) gửi lệnh qua **WebDriver protocol (W3C)** tới **Appium Server** (`http://127.0.0.1:4723`).
  - Appium Server dịch lệnh và chuyển cho **driver UiAutomator2**, driver này điều khiển app trên **emulator/thiết bị thật**.
  - → Vì vậy **phải bật Appium server trước** khi chạy test, và emulator/thiết bị phải sẵn sàng (`adb devices`).
- **🆕 UiAutomator2Options / Capabilities** — "tờ khai" cho Appium biết bạn muốn test gì:
  ```java
  UiAutomator2Options options = new UiAutomator2Options()
          .setPlatformName("Android")
          .setAutomationName("UiAutomator2")
          .setDeviceName("Android Emulator")
          .setApp("/Users/ban/apk/mda-2.2.0-25.apk")   // đường dẫn APK
          // hoặc trỏ tới app đã cài: .setAppPackage(...).setAppActivity(...)
          .setAppWaitActivity("*")
          .setAutoGrantPermissions(true);              // tự cấp quyền, tránh dialog chặn
  ```
- **🆕 Khởi tạo AndroidDriver** (test đầu tiên):
  ```java
  import io.appium.java_client.android.AndroidDriver;
  import io.appium.java_client.android.options.UiAutomator2Options;
  import java.net.URL;

  URL appiumServer = new URL("http://127.0.0.1:4723");
  AndroidDriver driver = new AndroidDriver(appiumServer, options);

  System.out.println(driver.getCurrentPackage());
  // ... thao tác test ...
  driver.quit();   // luôn quit để giải phóng session
  ```
- **🆕 Chiến lược Locator trên Android (kỹ năng cốt lõi)** — dùng lớp **`AppiumBy`**:
  - **Thứ tự ưu tiên nên dùng:** `accessibility id` (content-desc) **>** `id` (resource-id) **>** `androidUIAutomator` **>** `XPath` (hạn chế).
  ```java
  import io.appium.java_client.AppiumBy;

  // 1) Accessibility id — ổn định nhất, dev thường đặt sẵn content-desc
  driver.findElement(AppiumBy.accessibilityId("test-Username"));

  // 2) Id (resource-id) — nhanh, ổn định
  driver.findElement(AppiumBy.id("com.saucelabs.mydemoapp.rn:id/nameET"));

  // 3) className — khi cần gom nhóm cùng loại widget
  driver.findElements(AppiumBy.className("android.widget.EditText"));

  // 4) androidUIAutomator — mạnh, tìm theo text/desc, hỗ trợ scroll (xem GĐ4)
  driver.findElement(AppiumBy.androidUIAutomator(
          "new UiSelector().text(\"Login\")"));

  // 5) XPath — HẠN CHẾ, chậm & dễ gãy; chỉ khi bất khả kháng
  driver.findElement(AppiumBy.xpath("//android.widget.Button[@text='Login']"));
  ```
- **🆕 Tìm element bằng Appium Inspector** — chạm vào element trên cây UI để lấy sẵn `accessibility id`/`resource-id`/gợi ý XPath, thử locator trực tiếp trước khi đưa vào code.

### Tuần 2 — Hành động & Chờ element (Wait)
- Hành động cơ bản: `click()`, `sendKeys("...")`, `clear()`, `getText()`, `isDisplayed()`, `isEnabled()`.
- **🆕 Wait — KHÔNG dùng `Thread.sleep()`:**
  - **Implicit wait** — đặt một lần, áp cho mọi `findElement`:
    ```java
    driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
    ```
  - **Explicit wait** — chờ có điều kiện cụ thể (khuyến nghị cho phần tử động):
    ```java
    WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(15));
    wait.until(ExpectedConditions.visibilityOfElementLocated(
            AppiumBy.accessibilityId("test-LOGIN")));
    ```
  > ⚠️ **Không trộn** implicit + explicit wait quá tay → thời gian chờ cộng dồn khó lường. Nhiều team dùng implicit wait nhỏ + explicit wait cho chỗ cần.
- Phân loại Assertion (chống flaky):
  | Loại | Ví dụ | Đặc điểm |
  |------|-------|----------|
  | **Chờ điều kiện (retry)** | `wait.until(ExpectedConditions.visibilityOf(...))` | Tự chờ tới timeout → dùng cho UI động |
  | **Assertion thường (KHÔNG retry)** | JUnit `assertEquals`, AssertJ | Kiểm tra tức thời → chỉ dùng cho giá trị đã chắc chắn |
  - Assert nội dung ngay khi màn hình chưa render xong = **flaky test kinh điển** → hãy `wait` trước rồi mới assert.
  - **Soft assertion** (TestNG `SoftAssert` / AssertJ) — gom nhiều lỗi, không dừng ngay ở lỗi đầu tiên.

**Bài tập:**
- Đăng nhập **Sauce Labs My Demo App** hoàn chỉnh: nhập username/password, bấm Login, `wait` tới khi màn hình sản phẩm hiện, rồi assert.
- Với **ApiDemos**, tìm 3 element bằng 3 chiến lược locator khác nhau, so sánh độ ổn định.
- Cố tình dùng XPath phụ thuộc index để thấy nó dễ gãy, rồi thay bằng accessibility id.

**Sân tập / app mẫu:** **Sauce Labs My Demo App** (APK), **ApiDemos** (Appium sample). Soi bằng **Appium Inspector**.

✅ **Milestone GĐ3:** Khởi tạo `AndroidDriver` bằng `UiAutomator2Options`; viết test login đúng chuẩn dùng explicit wait; dùng thành thạo `AppiumBy` (accessibility id / id / androidUIAutomator); tìm locator bằng Appium Inspector.

---

## 🚀 Giai đoạn 4 — Appium Nâng Cao + Chống Flaky (2 tuần)

### Tuần 1 — Cử chỉ (Gestures) & tương tác nâng cao
- **🆕 Cử chỉ qua W3C Actions (`PointerInput` / `Sequence`)** — tap, swipe, scroll, long-press, drag & drop:
  ```java
  import org.openqa.selenium.interactions.PointerInput;
  import org.openqa.selenium.interactions.Sequence;
  import java.time.Duration;

  PointerInput finger = new PointerInput(PointerInput.Kind.TOUCH, "finger");
  Sequence swipe = new Sequence(finger, 1);
  swipe.addAction(finger.createPointerMove(Duration.ZERO,
          PointerInput.Origin.viewport(), 500, 1500));   // điểm bắt đầu
  swipe.addAction(finger.createPointerDown(PointerInput.MouseButton.LEFT.asArg()));
  swipe.addAction(finger.createPointerMove(Duration.ofMillis(600),
          PointerInput.Origin.viewport(), 500, 500));     // vuốt lên
  swipe.addAction(finger.createPointerUp(PointerInput.MouseButton.LEFT.asArg()));
  driver.perform(List.of(swipe));
  ```
- **🆕 Scroll tới element** — cách gọn nhất trên Android là `androidUIAutomator` với `UiScrollable`:
  ```java
  driver.findElement(AppiumBy.androidUIAutomator(
      "new UiScrollable(new UiSelector().scrollable(true))"
    + ".scrollIntoView(new UiSelector().text(\"Sauce Labs Backpack\"))"));
  ```
- **🆕 Chuyển context NATIVE_APP ↔ WEBVIEW** (app **hybrid**):
  ```java
  Set<String> contexts = driver.getContextHandles();   // [NATIVE_APP, WEBVIEW_com.xxx]
  driver.context("WEBVIEW_com.example");                // sang webview → thao tác như web
  // ... làm việc với DOM ...
  driver.context("NATIVE_APP");                         // quay lại native
  ```
- **🆕 Xử lý permission dialog** — nguyên nhân flaky rất phổ biến:
  - Cách sạch nhất: đặt `setAutoGrantPermissions(true)` trong Capabilities.
  - Hoặc bấm nút trong dialog hệ thống (Allow/While using the app) khi nó xuất hiện.
- **Bàn phím:** ẩn bàn phím `driver.hideKeyboard()`; lưu ý bàn phím che element cần bấm.
- **Xoay màn hình:** `driver.rotate(ScreenOrientation.LANDSCAPE)`.

### Tuần 2 — App Lifecycle, Context & Chống Flaky
- **🆕 App lifecycle (vòng đời app)** — API rất hay dùng khi test luồng thật:
  ```java
  driver.runAppInBackground(Duration.ofSeconds(5));  // đưa app xuống nền rồi mở lại
  driver.terminateApp("com.saucelabs.mydemoapp.rn");
  driver.activateApp("com.saucelabs.mydemoapp.rn");
  // Cài lại / reset trạng thái app giữa các test khi cần sạch dữ liệu
  ```
- **Test isolation & trạng thái sạch:** mỗi test nên bắt đầu từ trạng thái xác định (đăng xuất/reset app), không phụ thuộc test trước.
- **🆕 Flaky test & Test Isolation — kỹ năng phân biệt junior với người đi làm được:**
  - Nguyên nhân gốc trên mobile: `Thread.sleep`, quên chờ element, **permission dialog** bất chợt, animation chưa xong, thiếu isolation, tốc độ emulator dao động.
  - **Test độc lập:** mỗi test tự setup dữ liệu/đăng nhập, chạy được đơn lẻ.
  - Cấu hình **timeout** hợp lý; **retry** test fail (TestNG `IRetryAnalyzer` / JUnit extension); **quarantine** test flaky.
  - Vì sao "chạy local pass nhưng CI fail" (emulator CI chậm hơn, thiếu phần cứng tăng tốc, độ phân giải khác).
- **Chụp screenshot khi cần:**
  ```java
  File shot = driver.getScreenshotAs(OutputType.FILE);
  ```
- **Log & chẩn đoán:** đọc `adb logcat` khi app crash; bật/đọc log Appium server để debug lệnh.

**Bài tập:**
- Viết test **scroll** tới một sản phẩm ở cuối danh sách rồi thêm vào giỏ (My Demo App).
- Viết test **swipe** qua carousel / onboarding.
- Xử lý một **permission dialog** bằng 2 cách (autoGrant và bấm tay).
- Đưa app xuống nền 5 giây rồi mở lại, verify vẫn ở đúng màn hình.
- Viết lại một test flaky (do thiếu wait) cho ổn định.

✅ **Milestone GĐ4:** Thực hiện được tap/swipe/scroll/long-press bằng W3C Actions; chuyển được context native↔webview; xử lý permission dialog & app lifecycle; nhận diện & sửa được một test flaky.

---

## 🏗️ Giai đoạn 5 — Thiết Kế Framework (2–3 tuần)

> Đây là bước biến bạn từ "người viết script" thành "mobile automation engineer".

### Tuần 1 — Page Object Model cho Mobile & vòng đời Driver
- Vì sao cần **POM cho mobile** (nhiều nơi gọi là **Screen Object**): tách locator/logic khỏi test → dễ bảo trì khi UI app thay đổi.
- Xây `BaseScreen` (method dùng chung: `tap`, `type`, `waitVisible`); mỗi màn hình = một class (`LoginScreen`, `ProductsScreen`, `CartScreen`).
- `BaseTest` — setup/teardown (khởi tạo & `quit()` `AndroidDriver`).
- **🆕 DriverFactory dùng `ThreadLocal<AndroidDriver>`** — nền tảng để chạy song song nhiều thiết bị (chi tiết ở GĐ6):
  ```java
  public class DriverFactory {
      private static final ThreadLocal<AndroidDriver> DRIVER = new ThreadLocal<>();

      public static void createDriver(UiAutomator2Options options, URL server) {
          DRIVER.set(new AndroidDriver(server, options));
      }
      public static AndroidDriver getDriver() { return DRIVER.get(); }
      public static void quitDriver() {
          if (DRIVER.get() != null) { DRIVER.get().quit(); DRIVER.remove(); }
      }
  }
  ```
- **🆕 Design Pattern áp dụng NGAY tại đây** (không để "sau khóa"):
  - **Factory Pattern** — `DriverFactory` khởi tạo `AndroidDriver` theo cấu hình/thiết bị.
  - **Builder Pattern** — dựng `UiAutomator2Options` và test data linh hoạt.
  - (Singleton dùng thận trọng — dễ gây lỗi khi parallel; ưu tiên ThreadLocal.)

```
src/test/java/
├── base/          (BaseTest, BaseScreen)
├── factory/       (DriverFactory  ← ThreadLocal<AndroidDriver>)
├── screens/       (LoginScreen, ProductsScreen, CartScreen)
├── tests/         (LoginTest, CheckoutTest)
├── utils/         (ConfigReader, ScreenshotUtil, GestureUtil)
├── data/          (TestDataBuilder, DataProvider)
└── listeners/     (TestListener — auto screenshot khi fail)
```

### Tuần 2–3 — Nâng cấp framework
- **Data-driven testing:** đọc dữ liệu từ JSON (Jackson/Gson) / Excel (Apache POI) / CSV.
- **🆕 Test Data Management (thực chiến):**
  - Sinh dữ liệu ngẫu nhiên bằng **Datafaker** (email, tên, số điện thoại) → tránh trùng dữ liệu.
  - **Data Builder** dựng object test gọn gàng.
  - **Dọn dữ liệu sau test** (cleanup) — tránh rác trên môi trường dùng chung.
  - Tạo data qua **API** rồi verify trên **app** (nhanh & ổn định hơn tạo qua UI).
- **🆕 Config đa môi trường & đa thiết bị:** `config.properties` (platformName, deviceName, platformVersion, app path/appPackage, appActivity, appium server URL, timeout), đọc bằng `ConfigReader`. Dựng `UiAutomator2Options` **từ config** để đổi thiết bị không cần sửa code.
- **🆕 Quản lý Secret / Credential — BẮT BUỘC, đừng bỏ qua:**
  - ⛔ **KHÔNG hardcode** username/password/token/API key vào code hoặc commit lên Git.
  - Đọc từ **biến môi trường** (`System.getenv()`) hoặc file cục bộ **được `.gitignore`**.
  - Trên CI dùng **GitHub Secrets** (học kỹ ở GĐ7).
  - > ⚠️ Đặc biệt quan trọng vì cuối khóa bạn sẽ đẩy portfolio lên GitHub **public** — lộ mật khẩu / key device farm là sự cố thật, hay gặp ở người mới.
- **🆕 Listener / Extension:** dùng TestNG `ITestListener` (hoặc JUnit `TestWatcher` Extension) để **tự động chụp screenshot khi test fail** (lấy từ `DriverFactory.getDriver()`).
- **Logging:** Log4j2 hoặc SLF4J.
- Cấu trúc thư mục chuẩn, đặt tên nhất quán.

**Bài tập:** Refactor toàn bộ test My Demo App sang POM/Screen Object có `DriverFactory`; chạy login với 3 bộ data từ JSON; sinh email ngẫu nhiên bằng Datafaker; đọc credential từ biến môi trường; dựng `UiAutomator2Options` từ `config.properties`; cấu hình Listener auto-screenshot khi fail.

✅ **Milestone GĐ5:** Framework POM/Screen Object + DriverFactory (ThreadLocal) + data-driven; Capabilities dựng từ config; không có secret nào trong code; tự chụp screenshot khi fail.

---

## 🔗 Giai đoạn 6 — API Testing + Report + Parallel nhiều thiết bị (2 tuần)

### Tuần 1 — API Testing & Report
- **API testing** với **RestAssured**:
  - GET/POST/PUT/DELETE, headers, body, status code, validate response (JSON path).
  - Kết hợp API + Mobile: tạo/dọn data qua API, chỉ verify phần cốt lõi trên app (nhanh & ổn định hơn thao tác tay qua UI).
- **🆕 Reporting với Allure Report** (đẹp, phổ biến nhất):
  - Cài, tích hợp, xem report.
  - Đính kèm **screenshot** (và có thể **video màn hình** qua `adb screenrecord`) khi fail — nối với Listener ở GĐ5.

### Tuần 2 — Parallel nhiều emulator/thiết bị (thread-safe)
- **🆕 Parallel ĐÚNG CÁCH trên mobile** — không chỉ "bật một flag":
  - Appium Java Client **không** tự thread-safe → phải dùng **`ThreadLocal<AndroidDriver>`** trong `DriverFactory` (đã dựng ở GĐ5) để mỗi thread có một session/thiết bị riêng.
  - **Mỗi thiết bị cần một Appium session riêng.** Cách phổ biến:
    - Chạy **nhiều Appium server** trên các cổng khác nhau (`appium -p 4723`, `appium -p 4724`, …) và gán `--udid` cho từng thiết bị; **hoặc**
    - Dùng một Appium server và truyền **`systemPort`** khác nhau cho từng session UiAutomator2 (tránh trùng cổng driver).
  - Truyền `deviceName`/`udid`/`systemPort`/`appium server URL` theo tham số cho từng luồng.
  - Cấu hình `parallel` trong TestNG (`suite`/`tests`) hoặc JUnit 5 (`@Execution(CONCURRENT)`).
  - Lỗi kinh điển khi làm sai: các test "giẫm chân" nhau (dùng chung một driver), trùng `systemPort`, kết quả chập chờn.

```java
// Ví dụ gán systemPort + udid theo từng thiết bị để chạy song song
UiAutomator2Options options = new UiAutomator2Options()
        .setPlatformName("Android")
        .setDeviceName(deviceName)
        .setUdid(udid)                 // định danh thiết bị/emulator
        .setSystemPort(systemPort)     // cổng riêng cho driver UiAutomator2
        .setApp(appPath);
```

**Bài tập:** Viết 5 API test cho một API mẫu (ví dụ [reqres.in](https://reqres.in/) hoặc API của app); tích hợp Allure có screenshot khi fail; chạy cùng một bộ test song song trên **2 emulator** với `ThreadLocal` + `systemPort` riêng, xác nhận không còn giẫm chân nhau.

✅ **Milestone GĐ6:** Test API + Mobile; Allure report có screenshot; chạy parallel trên nhiều emulator ổn định nhờ ThreadLocal + systemPort/udid riêng.

---

## ⚙️ Giai đoạn 7 — CI/CD + Device Farm + Git nhóm (1 tuần)

- **GitHub Actions** (dễ bắt đầu nhất):
  - Viết workflow chạy test tự động khi push / mở Pull Request.
  - **🆕 Chạy Android emulator trên CI** — dùng action `reactivecircus/android-emulator-runner` để boot một AVD headless rồi chạy Appium test.
    > ⚠️ **Gotcha:** emulator trên CI **chậm và dễ flaky** (thiếu tăng tốc phần cứng). Cần timeout rộng hơn, retry hợp lý, và cân nhắc device farm cho bộ test lớn.
  - **🆕 GitHub Secrets** — nạp credential (tài khoản test, **key/username của device farm**) an toàn vào CI (nối tiếp GĐ5).
  - Upload **artifact** (Allure report, screenshot, log) để tải về xem.
- **🆕 Giới thiệu Device Farm (cloud thiết bị thật):**
  - **BrowserStack App Automate** / **Sauce Labs App Automate** — chạy test trên **thiết bị thật trên cloud**, không phải nuôi máy thật.
  - Chỉ cần đổi **Capabilities + server URL** trỏ tới hub của họ (upload APK lên trước, truyền `app` là id trên cloud) — code test gần như giữ nguyên.
  - Ưu điểm: nhiều mẫu máy/phiên bản Android thật, chạy song song lớn, ổn định hơn emulator CI.
- **🆕 Git làm việc nhóm (thực tế công việc):**
  - Branch strategy (feature branch), tạo **Pull Request**, code review.
  - Xử lý **merge conflict**.
  - Chạy test như một **gate** trước khi merge.

**Bài tập:** Tạo GitHub Actions boot emulator + chạy test mỗi lần push/PR; nạp credential qua GitHub Secrets; upload Allure report + screenshot làm artifact; (tùy chọn) chạy thử một test trên **BrowserStack/Sauce Labs App Automate** chỉ bằng cách đổi Capabilities.

✅ **Milestone GĐ7:** Test tự chạy trên CI (có emulator) mỗi lần push/PR, secret an toàn, report tải về được; hiểu cách trỏ test sang device farm.

---

## 🎓 Giai đoạn 8 — Dự Án Capstone + Chuẩn Bị Phỏng Vấn (2 tuần)

Chọn **1 app Android thật** (Sauce Labs My Demo App, một app open-source, hoặc app công ty bạn) và xây framework hoàn chỉnh.

**Yêu cầu dự án:**
- [ ] Framework theo POM/Screen Object + DriverFactory (ThreadLocal)
- [ ] 15–20 test case (login, duyệt sản phẩm, search, add to cart, checkout, negative cases, permission, scroll/swipe…)
- [ ] Data-driven + Datafaker (data tách khỏi code)
- [ ] Config đa môi trường/đa thiết bị (Capabilities dựng từ config)
- [ ] Kết hợp Mobile + API test
- [ ] **Không có secret nào trong code** (dùng env var / GitHub Secrets)
- [ ] Allure report + auto-screenshot khi fail
- [ ] Chạy parallel thread-safe trên nhiều emulator
- [ ] CI/CD trên GitHub Actions (boot emulator hoặc device farm)
- [ ] README.md mô tả rõ cách chạy (yêu cầu môi trường, cách bật Appium, cách chạy)
- [ ] Đẩy lên GitHub làm **portfolio**

### 🆕 Chuẩn bị phỏng vấn mobile automation (đừng bỏ qua)
- **Cách trình bày capstone:** kể được "bài toán → giải pháp → kết quả", giải thích được **vì sao** chọn POM/DriverFactory/ThreadLocal.
- **Câu hỏi mobile automation hay gặp:**
  - Kiến trúc Appium client–server hoạt động thế nào? Vai trò driver UiAutomator2?
  - Thứ tự ưu tiên locator trên Android? Vì sao hạn chế XPath?
  - Khác nhau app native / hybrid / webview? Chuyển context ra sao?
  - Xử lý flaky test & permission dialog thế nào?
  - Implicit vs explicit wait khác gì? Vì sao không dùng `Thread.sleep`?
  - Chạy song song nhiều thiết bị an toàn thế nào (ThreadLocal, systemPort, udid)?
  - Khi nào nên/không nên automate trên mobile?
- Biết cách "bán" portfolio: demo được trên emulator, nói được điểm mạnh của framework.

👉 Đây chính là thứ để đưa vào CV và trả lời phỏng vấn.

---

## 🧩 Kỹ năng bổ trợ (học song song / sau khóa)

| Kỹ năng | Vì sao cần |
|---------|-----------|
| **iOS (XCUITest)** | Mở rộng sang iOS — cần Mac + Xcode; cú pháp Appium gần giống Android |
| **SQL** (nên học sớm) | Verify dữ liệu trong DB — rất phổ biến trong công việc |
| **Docker** | Chạy Appium/emulator trong container, môi trường ổn định |
| **BDD - Cucumber** | Viết test theo Gherkin, làm việc với BA/PO |
| **Jira + Test Management** (Xray/TestRail) | Bối cảnh làm việc thật |
| **Espresso / XCUITest thuần** | Test do dev viết (in-process) — hiểu để phối hợp |

---

## ⚠️ Sai lầm thường gặp cần tránh

1. **Bỏ qua Java (nhất là Lambda), nhảy thẳng vào Appium** → không hiểu code wait/callback, không mở rộng được.
2. **Bỏ qua cấu trúc UI Android (content-desc/resource-id) & Appium Inspector** → viết locator yếu, hay gãy.
3. **Lạm dụng XPath** (nhất là XPath dài phụ thuộc index) → chậm & dễ gãy; ưu tiên **accessibility id > resource-id > androidUIAutomator**.
4. **Không dùng accessibility id** dù dev đã đặt `content-desc` → bỏ phí locator ổn định nhất.
5. **Dùng `Thread.sleep()` khắp nơi** thay vì implicit/explicit wait → test chậm & flaky.
6. **Quên chờ element** rồi assert ngay khi màn hình chưa render → flaky kinh điển.
7. **Quên/cấu hình sai Capabilities** (thiếu `automationName`, sai `appPackage`/`appActivity`, không autoGrant permission) → session không khởi tạo được hoặc bị dialog chặn.
8. **Parallel mà không dùng ThreadLocal** (hoặc trùng `systemPort`/`udid`) → các test giẫm chân nhau, kết quả chập chờn.
9. **Hardcode mật khẩu / key device farm và commit lên GitHub** → lộ credential, sự cố bảo mật thật.
10. **Không dùng POM/Screen Object** → code lặp, sửa một chỗ phải sửa 10 nơi.

---

## 📚 Tài nguyên chính thức (bookmark ngay)

- **Appium Docs:** https://appium.io/docs/en/latest/
- **Appium Java Client:** https://github.com/appium/java-client
- **UiAutomator2 Driver:** https://github.com/appium/appium-uiautomator2-driver
- **Appium Inspector:** https://github.com/appium/appium-inspector
- **UiSelector / UiScrollable (Android):** https://developer.android.com/reference/androidx/test/uiautomator/UiSelector
- **Selenium (WebDriver, nền tảng của Appium):** https://www.selenium.dev/documentation/
- **JUnit 5:** https://junit.org/junit5/docs/current/user-guide/ · **TestNG:** https://testng.org/doc/
- **Allure:** https://allurereport.org/docs/ · **Datafaker:** https://www.datafaker.net/ · **RestAssured:** https://rest-assured.io/
- **App/sân tập:** Sauce Labs My Demo App (APK), ApiDemos (Appium sample), reqres.in (API)

---

## 🗓️ Gợi ý lịch học mỗi ngày

| Thời gian | Hoạt động |
|-----------|-----------|
| 30 phút | Học lý thuyết (đọc docs / xem video) |
| 60 phút | **Code thực hành** (quan trọng nhất — 70% thời gian nên là code trên emulator) |
| 15 phút | Ghi chú lại điều đã học + lỗi gặp phải |

> **Nguyên tắc vàng:** Học mobile automation = **code mỗi ngày trên emulator**. Đọc 10 tutorial không bằng tự tay viết 1 test và debug nó.

---

*Chúc bạn học tốt! Bắt đầu từ Giai đoạn 0 hôm nay. 🚀*
