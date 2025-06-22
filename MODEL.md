# 📚 Cấu Trúc Dữ Liệu Ứng Dụng CourtSense

Tài liệu này mô tả chi tiết các kiểu dữ liệu chính (models) và đối tượng quản lý dữ liệu được sử dụng trong ứng dụng **CourtSense: Phân Tích & Huấn Luyện Bóng Rổ Cá Nhân**. Việc định nghĩa rõ ràng các cấu trúc này là nền tảng cho việc quản lý trạng thái, lưu trữ thông tin và xây dựng các tính năng phức tạp của ứng dụng.

---

## I. Các Kiểu Dữ Liệu Chính (Models - `struct`)

Các kiểu dữ liệu này đại diện cho các thực thể cụ thể trong ứng dụng và thường sẽ tuân thủ các giao thức như `Identifiable` (để sử dụng với `ForEach`, `List` trong SwiftUI) và `Codable` (để lưu trữ hoặc trao đổi dữ liệu).

### 1. `User` (Hồ Sơ Người Dùng)

Mô hình lưu trữ thông tin cá nhân của người dùng.

* **`id`**: Kiểu `UUID`. Một mã định danh duy nhất cho mỗi người dùng.
* **`name`**: Kiểu `String`. Tên hiển thị của người dùng.
* **`email`**: Kiểu `String`. Địa chỉ email dùng để đăng nhập.
* **`heightCm`**: Kiểu `Double?`. Chiều cao của người dùng tính bằng centimet (tùy chọn).
* **`weightKg`**: Kiểu `Double?`. Cân nặng của người dùng tính bằng kilogram (tùy chọn).
* **`skillLevel`**: Kiểu `SkillLevel` (enum). Cấp độ kỹ năng bóng rổ của người dùng.
* **`profileImageURL`**: Kiểu `URL?`. Đường dẫn đến ảnh đại diện của người dùng (tùy chọn).
* **`preferredWorkoutDurationMinutes`**: Kiểu `Int`. Thời lượng tập luyện ưa thích của người dùng tính bằng phút.

#### `SkillLevel` (Enum)

Đại diện cho các cấp độ kỹ năng bóng rổ.

* **Các giá trị**: `beginner` (Người mới), `intermediate` (Trung bình), `advanced` (Nâng cao), `professional` (Chuyên nghiệp).
* **Tuân thủ**: `String`, `Codable`, `CaseIterable`, `Identifiable`.

### 2. `Exercise` (Bài Tập)

Định nghĩa một bài tập bóng rổ cụ thể.

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi bài tập.
* **`name`**: Kiểu `String`. Tên của bài tập (ví dụ: "Ném Rổ Tự Do", "Rê Bóng Chéo Chân").
* **`description`**: Kiểu `String`. Mô tả chi tiết cách thực hiện bài tập.
* **`exerciseType`**: Kiểu `ExerciseType` (enum). Phân loại bài tập (ví dụ: "Ném rổ", "Dẫn bóng", "Phòng thủ", "Thể lực").
* **`targetRepsOrDuration`**: Kiểu `Int`. Mục tiêu số lần lặp (reps) hoặc thời lượng (giây) cho bài tập.
* **`videoURL`**: Kiểu `URL?`. Đường dẫn đến video hướng dẫn bài tập (tùy chọn).
* **`aiAnalysisEnabled`**: Kiểu `Bool`. Cho biết AI có phân tích động tác cho bài tập này không.
* **`aiAnalysisTarget`**: Kiểu `[AIAnalysisTarget]` (enum). Danh sách các khía cạnh AI cần phân tích trong động tác.

#### `ExerciseType` (Enum)

Phân loại các bài tập.

* **Các giá trị**: `shooting` (Ném rổ), `dribbling` (Dẫn bóng), `defense` (Phòng thủ), `conditioning` (Thể lực), `other` (Khác).
* **Tuân thủ**: `String`, `Codable`, `CaseIterable`, `Identifiable`.

#### `AIAnalysisTarget` (Enum)

Các điểm hoặc khía cạnh cụ thể mà AI sẽ phân tích trong động tác.

* **Các giá trị**: `shootingForm` (Tư thế ném), `elbowAngle` (Góc khuỷu tay), `legPosition` (Vị trí chân), `dribbleHeight` (Độ cao dẫn bóng), `bodyBalance` (Thăng bằng cơ thể), `stepFootwork` (Tư thế chân bước).
* **Tuân thủ**: `String`, `Codable`, `CaseIterable`, `Identifiable`.

### 3. `Workout` (Chương Trình Tập Luyện)

Một kế hoạch tập luyện bao gồm một chuỗi các bài tập.

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi chương trình tập luyện.
* **`name`**: Kiểu `String`. Tên của chương trình (ví dụ: "Chương Trình Ném Rổ Cơ Bản").
* **`description`**: Kiểu `String`. Mô tả tổng quan về chương trình.
* **`exercises`**: Kiểu `[Exercise]`. Một mảng chứa các đối tượng `Exercise` trong chương trình.
* **`estimatedDurationMinutes`**: Kiểu `Int`. Thời lượng ước tính của cả chương trình (tính toán tự động từ các bài tập con).
* **`createdAt`**: Kiểu `Date`. Ngày tạo chương trình.

### 4. `AIAnalysisResult` (Kết Quả Phân Tích AI)

Chi tiết kết quả phân tích AI cho một khía cạnh cụ thể của động tác.

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi kết quả phân tích.
* **`target`**: Kiểu `AIAnalysisTarget` (enum). Khía cạnh được phân tích (ví dụ: tư thế ném).
* **`score`**: Kiểu `Double`. Điểm số định lượng (ví dụ: 0.0 - 1.0 hoặc 0 - 100) cho độ chính xác.
* **`feedback`**: Kiểu `String`. Phản hồi bằng văn bản từ AI (ví dụ: "Cần hạ thấp đầu gối hơn").
* **`timestamp`**: Kiểu `Date`. Thời điểm phân tích được thực hiện.
* **`thumbnailUrl`**: Kiểu `URL?`. Đường dẫn đến ảnh/video thumbnail của khoảnh khắc phân tích (tùy chọn).

### 5. `ExercisePerformance` (Hiệu Suất Bài Tập)

Ghi lại hiệu suất của một bài tập đơn lẻ trong một phiên tập luyện.

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi bản ghi hiệu suất.
* **`exerciseId`**: Kiểu `UUID`. Liên kết đến ID của bài tập đã thực hiện.
* **`actualRepsOrDuration`**: Kiểu `Int`. Số lần lặp hoặc thời lượng thực tế đã hoàn thành.
* **`score`**: Kiểu `Double`. Điểm tổng thể cho bài tập này.
* **`accuracy`**: Kiểu `Double?`. Độ chính xác (ví dụ: tỷ lệ ném rổ thành công), tùy chọn.
* **`analysisResults`**: Kiểu `[AIAnalysisResult]`. Một mảng chứa các kết quả phân tích AI chi tiết cho bài tập này.
* **`videoRecordingURL`**: Kiểu `URL?`. Đường dẫn đến video ghi lại buổi tập (tùy chọn).

### 6. `WorkoutSession` (Phiên Tập Luyện)

Ghi lại một buổi tập luyện hoàn chỉnh đã được thực hiện.

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi phiên tập.
* **`workoutId`**: Kiểu `UUID?`. Liên kết đến ID của chương trình tập luyện đã sử dụng (tùy chọn, nếu là tập tự do).
* **`userId`**: Kiểu `UUID`. Liên kết đến ID của người dùng đã thực hiện phiên tập.
* **`date`**: Kiểu `Date`. Ngày và giờ thực hiện phiên tập.
* **`durationMinutes`**: Kiểu `Int`. Tổng thời lượng của phiên tập tính bằng phút.
* **`totalScore`**: Kiểu `Double`. Điểm tổng thể của phiên tập.
* **`exercisePerformances`**: Kiểu `[ExercisePerformance]`. Một mảng chứa các bản ghi hiệu suất của từng bài tập trong phiên.
* **`notes`**: Kiểu `String?`. Ghi chú thêm của người dùng về buổi tập (tùy chọn).

### 7. `Stat` (Chỉ Số Thống Kê)

Đại diện cho các chỉ số hiệu suất tổng hợp hoặc cụ thể được hiển thị trong tab "Thống Kê".

* **`id`**: Kiểu `UUID`. Mã định danh duy nhất cho mỗi chỉ số.
* **`name`**: Kiểu `String`. Tên chỉ số (ví dụ: "Tỷ lệ ném 3 điểm", "Số buổi tập hàng tuần").
* **`value`**: Kiểu `Double`. Giá trị hiện tại của chỉ số.
* **`unit`**: Kiểu `String`. Đơn vị đo lường của giá trị (ví dụ: "%", "lần", "phút").
* **`trend`**: Kiểu `Trend` (enum). Xu hướng của chỉ số theo thời gian (tăng, giảm, ổn định).
* **`lastUpdated`**: Kiểu `Date`. Thời điểm chỉ số này được tính toán/cập nhật cuối cùng.

#### `Trend` (Enum)

Mô tả xu hướng của một chỉ số.

* **Các giá trị**: `improving` (Đang cải thiện), `declining` (Đang giảm), `stable` (Ổn định).
* **Tuân thủ**: `String`, `Codable`.

---

## II. Các Đối Tượng Quản Lý Dữ Liệu (Managers - `class ObservableObject`)

Các `class` này sẽ đóng vai trò là "người quản lý" các bộ sưu tập dữ liệu lớn và chia sẻ trạng thái ứng dụng tới các View bằng `@EnvironmentObject`. Chúng sử dụng `@Published` để thông báo khi dữ liệu thay đổi.

### 1. `UserManager`

Quản lý thông tin và cài đặt của người dùng hiện tại.

* **`currentUser`**: Kiểu `User?`. Đối tượng người dùng hiện tại đang đăng nhập.
* **`appSettings`**: Kiểu `AppSettings`. Các cài đặt chung của ứng dụng (ví dụ: bật/tắt thông báo, chủ đề giao diện).
    * **`AppSettings` (Struct):** `enableNotifications` (Bool), `theme` (AppTheme enum).

#### `AppTheme` (Enum)

Đại diện cho chủ đề giao diện ứng dụng.

* **Các giá trị**: `light` (Sáng), `dark` (Tối), `system` (Hệ thống).
* **Tuân thủ**: `String`, `Codable`, `CaseIterable`, `Identifiable`.

### 2. `WorkoutManager`

Quản lý danh sách các chương trình tập luyện và lịch sử các phiên tập luyện của người dùng.

* **`availableWorkouts`**: Kiểu `[Workout]`. Một mảng chứa tất cả các chương trình tập luyện có sẵn trong ứng dụng.
* **`workoutHistory`**: Kiểu `[WorkoutSession]`. Một mảng chứa lịch sử tất cả các phiên tập luyện mà người dùng đã hoàn thành.

---

## III. Mối Quan Hệ Giữa Các Kiểu Dữ Liệu

* Một `User` có thể có nhiều `WorkoutSession`.
* Một `Workout` bao gồm một hoặc nhiều `Exercise`.
* Một `WorkoutSession` chứa kết quả của một hoặc nhiều `ExercisePerformance`.
* Mỗi `ExercisePerformance` lại có một hoặc nhiều `AIAnalysisResult`.
* `UserManager` quản lý một đối tượng `User` duy nhất.
* `WorkoutManager` quản lý các bộ sưu tập `Workout` và `WorkoutSession`.

Cấu trúc dữ liệu này được thiết kế để dễ dàng mở rộng, lưu trữ hiệu quả với SwiftData (hoặc Core Data) và tương tác liền mạch với giao diện SwiftUI.
