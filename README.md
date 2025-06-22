# 🏀 CourtSense: Phân Tích & Huấn Luyện Bóng Rổ Cá Nhân

**CourtSense** là một ứng dụng iOS đột phá được thiết kế để nâng cao kỹ năng bóng rổ của bạn thông qua việc theo dõi, phân tích hiệu suất và cung cấp phản hồi thông minh, cá nhân hóa. Ứng dụng này tận dụng sức mạnh của trí tuệ nhân tạo (AI) và công nghệ thực tế tăng cường (AR) để mang đến trải nghiệm huấn luyện chuyên nghiệp ngay trong tầm tay bạn.

---

## ✨ Tính Năng Nổi Bật

* **Phân Tích Động Tác Bằng AI (Nâng cao):**
    * Sử dụng Core ML và Vision Framework để phát hiện, theo dõi các khớp cơ thể và phân tích tư thế của bạn trong thời gian thực khi bạn tập luyện (ví dụ: tư thế ném, dẫn bóng, phòng thủ).
    * **Mô hình AI tùy chỉnh:** Khả năng tích hợp hoặc huấn luyện một mô hình Core ML riêng biệt cho các động tác bóng rổ đặc thù, đảm bảo độ chính xác cao nhất.
    * **Phản hồi tức thì:** Nhận phản hồi chi tiết về kỹ thuật (ví dụ: "Đầu gối chưa đủ thấp", "Thả tay đúng thời điểm hơn") để điều chỉnh ngay lập tức và tránh chấn thương.
    * **Overlay Trực quan:** Hiển thị các điểm khớp xương và đường nối trên luồng video xem trước để bạn dễ dàng hình dung tư thế của mình.

* **Huấn Luyện Tương Tác với ARKit (Nâng cao):**
    * **Mục tiêu 3D ảo:** Đặt các điểm hoặc mục tiêu bóng rổ ảo trong không gian thực tế của bạn bằng ARKit.
    * **Thử thách AR:** Thực hiện các bài tập tương tác như ném bóng vào các vị trí ảo, tăng cường trải nghiệm luyện tập và thêm yếu tố gamification.

* **Quản Lý Dữ Liệu Bền Vững (SwiftData/Core Data - Nâng cao):**
    * Lưu trữ vĩnh viễn hồ sơ người dùng, lịch sử luyện tập chi tiết và các bài tập tùy chỉnh, đảm bảo dữ liệu luôn có sẵn qua các lần sử dụng ứng dụng.

* **Biểu Đồ & Trực Quan Hóa Dữ Liệu Chuyên Sâu (Charts Framework - Nâng cao):**
    * Hiển thị tiến độ, hiệu suất và các số liệu thống kê quan trọng (ví dụ: tỷ lệ ném rổ thành công, sự cải thiện kỹ thuật theo thời gian) bằng các biểu đồ đường, cột, tròn sinh động và dễ hiểu.

* **Kế Hoạch Huấn Luyện Cá Nhân Hóa:**
    * AI học hỏi từ dữ liệu luyện tập và tiến độ của bạn để tự động điều chỉnh kế hoạch, độ khó và mục tiêu, đảm bảo bạn luôn được thử thách phù hợp.

* **Đồng Bộ Apple HealthKit:**
    * Tích hợp liền mạch với HealthKit để theo dõi và đồng bộ dữ liệu tập luyện, nhịp tim, lượng calo tiêu thụ, cung cấp cái nhìn toàn diện về sức khỏe.

* **Phản Hồi Haptic & Âm Thanh (Nâng cao):**
    * Cung cấp phản hồi rung tinh tế qua Core Haptics và âm thanh khi bạn thực hiện đúng động tác hoặc mắc lỗi, tăng cường trải nghiệm và khả năng phản ứng.

* **Giao Diện Người Dùng Hiện Đại với SwiftUI:**
    * Thiết kế giao diện mượt mà, trực quan và dễ sử dụng, tận dụng tối đa các Components, Modifiers, Custom Components của SwiftUI.
    * **TabView:** Tổ chức ứng dụng thành các màn hình chính rõ ràng như Trang Chủ (Dashboard), Bài Tập (Workouts), Thống Kê (Stats) và Hồ Sơ (Profile).

---

## 🛠️ Công Nghệ & Yêu Cầu

* **Ngôn ngữ:** Swift
* **Framework chính:** SwiftUI
* **Yêu cầu hệ điều hành:** iOS 17.0+ (để tận dụng SwiftData và Charts framework mới nhất)
* **Môi trường phát triển:** Xcode 15.0+
* **Các Framework & Thư viện khác:**
    * Core ML: Triển khai các mô hình học máy trên thiết bị.
    * Vision Framework: Xử lý hình ảnh và video cho nhận diện tư thế.
    * ARKit: Tạo trải nghiệm thực tế tăng cường.
    * SwiftData (hoặc Core Data): Quản lý dữ liệu bền vững.
    * Charts: Trực quan hóa dữ liệu.
    * HealthKit: Tích hợp dữ liệu sức khỏe.
    * Core Haptics: Cung cấp phản hồi rung.
    * AVFoundation: Xử lý luồng video.

---

## 🚀 Hướng Phát Triển Tương Lai

* **Tính năng Cộng Đồng:** Cho phép người dùng chia sẻ kết quả, thách đấu với bạn bè, hoặc tham gia vào các bảng xếp hạng.
* **Tích hợp Apple Watch:** Theo dõi nhịp tim và các chỉ số hoạt động khác trực tiếp từ Apple Watch trong khi tập luyện.
* **Tạo Bài Tập Tùy Chỉnh:** Cho phép người dùng tự quay video các động tác của họ và huấn luyện AI của riêng mình để nhận phản hồi cá nhân hóa hơn nữa.
* **Phân tích Trận Đấu:** Tích hợp khả năng phân tích video trận đấu thực tế của người dùng để đưa ra số liệu thống kê chi tiết về hiệu suất trong thi đấu.

---

## 📚 Các Kiến Thức SwiftUI Được Áp Dụng

Dự án này là minh chứng cho việc ứng dụng tổng hợp các kiến thức đã học từ Học phần 5 về SwiftUI, bao gồm:

* **Components:** Image, TextField, Slider, Toggle, Picker, ProgressView, Spacer.
* **Modifiers:** `padding()`, `frame()`, `font()`, `foregroundColor()`, `background()`, `cornerRadius()`, `onTapGesture()`, v.v.
* **Custom Components:** Xây dựng các View có thể tái sử dụng như WorkoutCardView, StatDisplayView, RoundedButton.
* **Property Wrappers:** `@State`, `@Binding`, `@ObservedObject`, `@Published`, `@EnvironmentObject` để quản lý trạng thái và luồng dữ liệu reactive.
* **Reverse Engineering:** Phân tích và học hỏi từ các ứng dụng thể thao hàng đầu để tối ưu thiết kế.
* **ForEach & List:** Hiển thị danh sách dữ liệu động và triển khai các chức năng tương tác.
* **TabView:** Tổ chức cấu trúc điều hướng chính của ứng dụng.
* **Quản lý dữ liệu:** Thiết kế các `struct Identifiable` cho các model dữ liệu như Workout, Exercise, User.

---

## 🤝 Đóng Góp

Mọi ý kiến đóng góp và đề xuất cải tiến cho CourtSense đều rất được chào đón! Vui lòng mở một Issue hoặc Pull Request trên kho lưu trữ GitHub của dự án (nếu đây là mã nguồn mở) hoặc liên hệ trực tiếp.

---
