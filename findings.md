# Phát hiện

- Ảnh hiện trạng cho thấy CRM là giao diện danh sách khách hàng với các tab trạng thái: Tất cả, Trễ hạn, Chưa tiếp cận, Đã tiếp cận, Tiềm năng, Không tiềm năng.
- Bảng có ngày nhận, trạng thái, nhân sự phụ trách, doanh số dự kiến và ghi chú; đây là các trường phù hợp để tổng hợp theo tháng.
- Yêu cầu AI dùng DeepSeek. API key đã được người dùng cung cấp trong hội thoại nhưng tuyệt đối không lưu vào tệp kế hoạch, mã nguồn phía client hoặc lịch sử Git.
- Thư mục đích hiện là Git repository sạch và chỉ có một tệp `index.html` trước khi thay đổi.
- Ứng dụng là single-page HTML/JavaScript, tải và ghi dữ liệu realtime qua bảng Supabase `leads`; không có backend riêng trong repository.
- Trạng thái hiển thị được tính từ `stage`; riêng khách `new` quá ngưỡng nhắc được coi là `overdue`.
- `computeStats()` và `filteredLeads()` hiện dùng toàn bộ dữ liệu, nên cần thêm lớp lọc tháng dùng trường `time` trước khi thống kê và lọc trạng thái.
- Phương án AI an toàn: UI gọi Supabase Edge Function; Edge Function đọc `DEEPSEEK_API_KEY` từ secret phía server và chuyển tiếp luồng trả lời. Context gửi sang AI sẽ bỏ số điện thoại và giới hạn theo tháng đang chọn.
- Kiểm tra giao diện thật ở kích thước 1440×1200 cho thấy tháng 10/2026 được chọn mặc định, tổng 6 khách, các số đếm trạng thái khớp danh sách (5 trễ hạn, 1 đã tiếp cận), và bố cục không bị vỡ.
- Nút AI hiển thị cố định ở góc dưới bên phải mà không che bảng dữ liệu.
- Tài liệu DeepSeek hiện hành (03/10/2026) liệt kê `deepseek-flash` và `deepseek-v4-pro`; chọn `deepseek-flash` với streaming SSE để ưu tiên tốc độ hỏi đáp realtime.
- Tài liệu Supabase xác nhận secret production nên được đặt bằng Dashboard/CLI và đọc bằng `Deno.env.get`; Edge Function có thể deploy qua API mà không cần Docker.

