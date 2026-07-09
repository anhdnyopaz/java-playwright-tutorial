# 📱 Automation Test với Java + Appium — Giáo trình & Học liệu cho Tester (Mobile - Android)

> Bộ giáo trình và học liệu tự học **Mobile Automation Test** bằng **Java + Appium**, biên soạn cho **tester (manual)** muốn chuyển sang / bổ sung kỹ năng automation. Trọng tâm **Android trước** (iOS học sau — cần Mac + Xcode). Nội dung bằng **tiếng Việt**, đi từ nền tảng đến khi tự xây được framework chạy trên CI.

<p align="left">
  <img alt="Java" src="https://img.shields.io/badge/Java-17%2B-orange">
  <img alt="Appium" src="https://img.shields.io/badge/Appium-2.x-662D91">
  <img alt="UiAutomator2" src="https://img.shields.io/badge/Driver-UiAutomator2-3DDC84">
  <img alt="Android" src="https://img.shields.io/badge/Platform-Android-3DDC84">
  <img alt="Level" src="https://img.shields.io/badge/Tr%C3%ACnh%20%C4%91%E1%BB%99-Beginner%20%E2%86%92%20Job--ready-blue">
  <img alt="Language" src="https://img.shields.io/badge/Ng%C3%B4n%20ng%E1%BB%AF-Ti%E1%BA%BFng%20Vi%E1%BB%87t-red">
</p>

---

## 📚 Nội dung chính

| Tài liệu | Mô tả |
|----------|-------|
| **[📋 Giáo trình / Lộ trình tổng](giao-trinh.md)** | Bản đồ toàn khóa: 9 giai đoạn, mục tiêu, milestone, bài tập, các sai lầm cần tránh |
| **[📖 Học liệu chi tiết](hoc-lieu/)** | Bài giảng đầy đủ theo từng giai đoạn (lý thuyết + ví dụ + bài tập có lời giải + quiz) |

---

## 🎯 Dành cho ai?

- Tester **manual** muốn bắt đầu học **mobile automation** từ con số 0.
- Người mới với Java, cần một lộ trình **có thứ tự, có bài tập, có cột mốc**.
- Ai muốn tự học tới mức **job-ready ở trình entry**: tự xây framework Mobile UI + API, chạy trên CI, có report.

> Không yêu cầu biết lập trình trước. Chỉ cần kiên trì **code mỗi ngày trên emulator**.

---

## 🗺️ Lộ trình tổng quan (9 giai đoạn · ~14–18 tuần)

| GĐ | Nội dung | Học liệu |
|----|----------|:--------:|
| **0** | Mindset mobile, môi trường (Android Studio + Appium, macOS & Windows) & cấu trúc UI Android | ✅ [Xem](hoc-lieu/giai-doan-0.md) |
| **1** | Java cơ bản cho Tester (cú pháp → OOP → Lambda/Generics/Debug) | ✅ [Xem](hoc-lieu/giai-doan-1.md) |
| **2** | Công cụ nền tảng (Maven, Git, JUnit/TestNG + Appium Java Client) | 🚧 Đang biên soạn |
| **3** | Appium cơ bản (AndroidDriver, Capabilities, Locator, Inspector) | 🚧 |
| **4** | Appium nâng cao (gestures, context, lifecycle) + chống Flaky test | 🚧 |
| **5** | Thiết kế Framework (POM mobile, DriverFactory, Test Data, Secret) | 🚧 |
| **6** | API Testing + Report + Parallel nhiều thiết bị (thread-safe) | 🚧 |
| **7** | CI/CD (emulator trên CI) + Device Farm + Git nhóm | 🚧 |
| **8** | Dự án tổng hợp (Capstone) + Chuẩn bị phỏng vấn | 🚧 |

> Chi tiết đầy đủ từng giai đoạn: xem **[giáo trình tổng](giao-trinh.md)**.

---

## 📂 Cấu trúc thư mục

```
.
├── README.md            ← Bạn đang ở đây (trang chủ)
├── giao-trinh.md        ← Lộ trình tổng của cả khóa
└── hoc-lieu/            ← Học liệu chi tiết theo từng giai đoạn
    ├── README.md        ← Chỉ mục học liệu
    ├── giai-doan-0.md   ← GĐ0: Mindset, môi trường, cấu trúc UI Android
    └── giai-doan-1.md   ← GĐ1: Java cơ bản cho Tester (3 tuần)
```

---

## 🚀 Bắt đầu thế nào?

1. Đọc **[giáo trình tổng](giao-trinh.md)** để nắm bức tranh toàn cảnh và cách khóa học vận hành.
2. Vào **[Giai đoạn 0](hoc-lieu/giai-doan-0.md)** — cài đặt môi trường (Android Studio + SDK + Emulator, Node.js + Appium + driver UiAutomator2, Appium Inspector) và học cấu trúc UI Android.
3. Sang **[Giai đoạn 1](hoc-lieu/giai-doan-1.md)** — học Java cơ bản, làm **bài tập kèm lời giải** và **quiz** cuối mỗi tuần.
4. Bám nguyên tắc vàng: **70% thời gian là code thực hành** trên emulator, không chỉ đọc.

> 💡 Mỗi giai đoạn có **checklist milestone** — hoàn thành hết mới sang giai đoạn sau.

---

## 🧰 Công nghệ & công cụ trong khóa

`Java 17+` · `Appium 2.x` · `UiAutomator2` · `Appium Java Client` · `Android SDK / Emulator` · `Appium Inspector` · `Maven` · `JUnit 5 / TestNG` · `RestAssured` · `Git & GitHub Actions` · `Allure Report` · `Page Object Model` · `Datafaker`

---

## 📲 App luyện tập dùng trong khóa

- **Sauce Labs My Demo App** (APK Android) — app demo shopping, có sẵn `content-desc`/`resource-id` chuẩn để luyện locator
- **ApiDemos** — app sample của Appium, nhiều loại widget/cử chỉ để thực hành
- [reqres.in](https://reqres.in/) — API mẫu cho phần API testing
- Soi cây UI & tìm locator bằng **[Appium Inspector](https://github.com/appium/appium-inspector)**

> 💡 iOS học sau: cần **Mac + Xcode + driver XCUITest**. Giáo trình tập trung **Android trước**.

---

## 📌 Trạng thái

Học liệu đang được biên soạn dần theo lộ trình. Hiện đã có **Giai đoạn 0** và **Giai đoạn 1**; các giai đoạn còn lại sẽ được bổ sung.

---

*Học liệu phi lợi nhuận, phục vụ mục đích học tập. Chúc bạn học tốt và sớm đi làm mobile automation! 🚀*
