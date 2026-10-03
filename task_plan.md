# Kế hoạch nâng cấp CRM

## Mục tiêu
- Cho phép chọn tháng và xem tổng số khách của tháng đó.
- Hiển thị thống kê theo trạng thái hiện tại trong tháng, đồng thời cho phép lọc danh sách theo trạng thái.
- Thêm trợ lý AI hỏi đáp realtime về dữ liệu CRM, với API key được giữ ngoài mã nguồn giao diện.

## Các giai đoạn
1. [complete] Khảo sát kiến trúc, dữ liệu và luồng hiện tại.
2. [complete] Thiết kế và triển khai bộ lọc/thống kê theo tháng và trạng thái.
3. [complete] Thiết kế và triển khai trợ lý AI theo cách an toàn phù hợp với kiến trúc dự án.
4. [complete] Kiểm thử chức năng, giao diện và bảo mật cấu hình.
5. [complete] Hoàn thiện tài liệu chạy và bàn giao.

## Quyết định chính
- Không ghi API key người dùng cung cấp vào mã HTML/JavaScript phía trình duyệt hoặc commit Git.
- Giữ tương thích với dữ liệu CRM hiện có và tránh làm mất dữ liệu trình duyệt.

## Lỗi gặp phải
| Lỗi | Lần thử | Cách xử lý |
|---|---:|---|
| Chưa có | - | - |
| Bản vá lớn không khớp đoạn kết chuỗi `render()` | 1 | Chia bản vá thành các phần nhỏ và đọc lại đúng đoạn mã đích trước khi áp dụng. |
| Selenium không khởi tạo do ChromeDriver cache v150 không khớp Chrome v154 | 1 | Chuyển sang Playwright điều khiển trực tiếp Chrome đã cài, không dùng ChromeDriver. |
| Bản vá ghép Edge Function và tài liệu sai cấu trúc hunk | 1 | Tách thành hai bản vá độc lập theo từng tệp. |
| TypeScript compiler không nhận diện global `Deno` ngoài runtime Supabase | 1 | Thêm khai báo type tối thiểu cho `Deno.env` và `Deno.serve`, sau đó kiểm tra lại. |

