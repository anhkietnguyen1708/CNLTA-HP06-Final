Tuyệt vời! Dựa trên các tính năng của CourtSense, tôi sẽ mô tả chi tiết kiểu dữ liệu cho từng phần, giải thích vai trò và các thuộc tính chính mà không dùng code blocks hay cấu trúc README.md.

📚 Mô Tả Kiểu Dữ Liệu Ứng Dụng CourtSense
Để xây dựng một ứng dụng phức tạp như CourtSense, việc định nghĩa rõ ràng các "khối xây dựng" dữ liệu là cực kỳ quan trọng. Dưới đây là mô tả về các kiểu dữ liệu (chủ yếu là struct và class) mà ứng dụng sẽ sử dụng.

1. Người Dùng (User)
Kiểu dữ liệu này lưu trữ toàn bộ thông tin cá nhân của người dùng ứng dụng. Đây là nguồn chân lý cho mọi thứ liên quan đến tài khoản cá nhân.

Định danh duy nhất (id): Một mã số đặc biệt (thường là UUID) để phân biệt mỗi người dùng.
Tên (name): Tên đầy đủ hoặc tên hiển thị của người dùng.
Email (email): Địa chỉ email dùng để đăng nhập hoặc liên hệ.
Chiều cao (heightCm): Chiều cao của người dùng theo centimet (có thể không bắt buộc).
Cân nặng (weightKg): Cân nặng của người dùng theo kilogram (có thể không bắt buộc).
Cấp độ kỹ năng (skillLevel): Một kiểu dữ liệu riêng biệt (ví dụ: enum) để phân loại trình độ bóng rổ của người dùng (Ví dụ: "Người mới", "Trung bình", "Nâng cao", "Chuyên nghiệp"). Điều này giúp ứng dụng cá nhân hóa nội dung.
URL ảnh đại diện (profileImageURL): Đường dẫn đến ảnh hồ sơ của người dùng, thường là ảnh được lưu trữ trên đám mây.
Thời lượng tập luyện ưa thích (preferredWorkoutDurationMinutes): Số phút mà người dùng muốn dành cho một buổi tập, giúp AI đề xuất các bài tập phù hợp.
2. Bài Tập (Exercise)
Đây là định nghĩa cho một bài tập bóng rổ cụ thể mà người dùng có thể thực hiện (ví dụ: "Ném rổ tự do", "Rê bóng chéo chân").

Định danh duy nhất (id): Mã số riêng cho từng bài tập.
Tên (name): Tên ngắn gọn của bài tập.
Mô tả (description): Hướng dẫn chi tiết về cách thực hiện bài tập.
Loại bài tập (exerciseType): Một kiểu dữ liệu riêng biệt (ví dụ: enum) để phân loại bài tập (Ví dụ: "Ném rổ", "Dẫn bóng", "Phòng thủ", "Thể lực"). Giúp dễ dàng tìm kiếm và sắp xếp.
Mục tiêu lặp/thời lượng (targetRepsOrDuration): Con số mục tiêu cho bài tập này, có thể là số lần lặp (ví dụ: 20 cú ném) hoặc thời lượng (ví dụ: 120 giây).
URL video hướng dẫn (videoURL): Đường dẫn đến video mẫu minh họa bài tập.
Bật/tắt phân tích AI (aiAnalysisEnabled): Một giá trị Boolean cho biết liệu AI có nên phân tích động tác cho bài tập này hay không.
Mục tiêu phân tích AI (aiAnalysisTarget): Một danh sách các khía cạnh cụ thể mà AI cần tập trung vào khi phân tích (Ví dụ: "Tư thế ném", "Góc khuỷu tay", "Vị trí chân"). Điều này cực kỳ quan trọng cho tính năng AI nâng cao.
3. Chương Trình Tập Luyện (Workout)
Kiểu dữ liệu này đại diện cho một kế hoạch tập luyện hoàn chỉnh, bao gồm một chuỗi các bài tập cụ thể.

Định danh duy nhất (id): Mã số riêng cho từng chương trình.
Tên (name): Tên của chương trình tập luyện (ví dụ: "Chương trình ném rổ cơ bản", "Thử thách rê bóng").
Mô tả (description): Mô tả tổng quan về mục tiêu và nội dung của chương trình.
Danh sách các bài tập (exercises): Một mảng chứa các đối tượng Exercise, xác định thứ tự và nội dung của chương trình.
Thời lượng ước tính (estimatedDurationMinutes): Giá trị tự động tính toán tổng thời lượng dự kiến của cả chương trình, dựa trên thời lượng của các bài tập con.
Ngày tạo (createdAt): Thời điểm chương trình này được tạo ra.
4. Kết Quả Phân Tích AI (AIAnalysisResult)
Mỗi khi AI phân tích một khía cạnh cụ thể của động tác trong một bài tập, kết quả sẽ được lưu trữ trong kiểu dữ liệu này.

Định danh duy nhất (id): Mã số riêng cho từng kết quả phân tích.
Mục tiêu phân tích (target): Khía cạnh cụ thể của động tác mà kết quả này đề cập (ví dụ: "Tư thế ném", "Góc khuỷu tay").
Điểm số (score): Một giá trị số (ví dụ: từ 0 đến 100) thể hiện mức độ chính xác của động tác theo đánh giá của AI.
Phản hồi văn bản (feedback): Một chuỗi văn bản cung cấp phản hồi cụ thể, chi tiết từ AI (ví dụ: "Đầu gối chưa đủ thấp", "Thả tay đúng thời điểm hơn").
Thời điểm (timestamp): Thời gian chính xác khi phân tích này được thực hiện (quan trọng cho phản hồi thời gian thực).
URL ảnh/video nhỏ (thumbnailUrl): Đường dẫn đến một khung hình hoặc đoạn video ngắn tại khoảnh khắc phân tích, giúp người dùng xem lại.
5. Hiệu Suất Bài Tập (ExercisePerformance)
Khi người dùng hoàn thành một bài tập trong một buổi tập, kiểu dữ liệu này sẽ ghi lại hiệu suất cụ thể của họ cho bài tập đó.

Định danh duy nhất (id): Mã số riêng cho mỗi lần thực hiện bài tập.
ID bài tập (exerciseId): Liên kết đến id của Exercise mà người dùng đã thực hiện.
Số lần/thời lượng thực tế (actualRepsOrDuration): Số lần lặp hoặc thời lượng thực tế mà người dùng đã hoàn thành.
Điểm tổng thể (score): Điểm số tổng hợp cho toàn bộ bài tập này, có thể được tính toán từ các AIAnalysisResult.
Độ chính xác (accuracy): Một giá trị phần trăm hoặc tỷ lệ (ví dụ: 85% cú ném thành công).
Kết quả phân tích AI (analysisResults): Một mảng chứa các đối tượng AIAnalysisResult, cung cấp chi tiết về phân tích AI cho từng động tác trong bài tập này.
URL ghi hình (videoRecordingURL): Đường dẫn đến video ghi lại quá trình người dùng thực hiện bài tập (nếu tính năng ghi hình được bật).
6. Phiên Tập Luyện (WorkoutSession)
Đây là kiểu dữ liệu ghi lại một buổi tập luyện hoàn chỉnh mà người dùng đã hoàn thành. Đây là nơi tập hợp tất cả dữ liệu lịch sử.

Định danh duy nhất (id): Mã số riêng cho từng phiên tập.
ID chương trình (workoutId): Liên kết đến id của Workout nếu phiên tập này dựa trên một chương trình cụ thể (có thể trống nếu là tập tự do).
ID người dùng (userId): Liên kết đến id của User đã thực hiện phiên tập.
Ngày/giờ (date): Thời điểm chính xác buổi tập diễn ra.
Tổng thời lượng (durationMinutes): Tổng số phút của toàn bộ phiên tập.
Điểm tổng thể (totalScore): Điểm số tổng hợp cho toàn bộ phiên tập.
Hiệu suất các bài tập (exercisePerformances): Một mảng chứa các đối tượng ExercisePerformance, ghi lại hiệu suất của từng bài tập con trong phiên này.
Ghi chú (notes): Trường văn bản cho phép người dùng thêm ghi chú cá nhân về buổi tập.
7. Chỉ Số Thống Kê (Stat)
Kiểu dữ liệu này đại diện cho các chỉ số hiệu suất tổng hợp hoặc cụ thể mà người dùng có thể theo dõi (ví dụ: "Tỷ lệ ném 3 điểm", "Số buổi tập hàng tuần"). Dữ liệu này thường được tính toán từ WorkoutSession lịch sử.

Định danh duy nhất (id): Mã số riêng cho từng chỉ số.
Tên chỉ số (name): Tên mô tả chỉ số (ví dụ: "Tỷ lệ ném rổ thành công", "Số lần squat đúng kỹ thuật").
Giá trị (value): Giá trị hiện tại của chỉ số (ví dụ: 85.5, 3).
Đơn vị (unit): Đơn vị đo lường của giá trị (ví dụ: "%", "lần", "phút").
Xu hướng (trend): Một kiểu dữ liệu riêng biệt (ví dụ: enum) mô tả sự thay đổi của chỉ số theo thời gian (Ví dụ: "Đang cải thiện", "Đang giảm", "Ổn định").
Cập nhật lần cuối (lastUpdated): Thời điểm chỉ số này được tính toán hoặc cập nhật gần nhất.
8. Đối Tượng Quản Lý Dữ Liệu (ObservableObject Classes)
Để chia sẻ và quản lý các bộ sưu tập dữ liệu lớn hoặc trạng thái chung của ứng dụng một cách hiệu quả, chúng ta sẽ sử dụng các class tuân thủ giao thức ObservableObject với các thuộc tính được đánh dấu @Published.

UserManager:

Quản lý đối tượng User hiện tại của ứng dụng.
Có thể chứa các cài đặt ứng dụng chung (ví dụ: App Setting với các thuộc tính như enableNotifications, theme).
Khi thông tin User hoặc cài đặt thay đổi, các phần giao diện liên quan sẽ tự động cập nhật.
WorkoutManager:

Quản lý danh sách các chương trình tập luyện có sẵn (availableWorkouts).
Quản lý lịch sử tất cả các phiên tập luyện đã hoàn thành của người dùng (workoutHistory).
Các phương thức để thêm, xóa, hoặc cập nhật chương trình/phiên tập.
Các đối tượng này sẽ được cung cấp cho toàn bộ ứng dụng thông qua @EnvironmentObject, giúp tránh việc truyền dữ liệu thủ công qua nhiều lớp View.
