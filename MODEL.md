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
* **`description
