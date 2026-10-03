# Kích hoạt trợ lý AI CRM

API key DeepSeek được giữ trong Supabase Edge Function, không nằm trong `index.html` và không bị lộ trên GitHub Pages.

## Triển khai lần đầu

1. Đăng nhập Supabase CLI:

   ```powershell
   npx supabase login
   ```

2. Trong Supabase Dashboard, mở **Edge Functions → Secrets**, tạo secret tên `DEEPSEEK_API_KEY` và dán API key mới vào đó. Cách này không ghi key vào terminal history hoặc repository.

3. Deploy Edge Function:

   ```powershell
   npx supabase functions deploy crm-ai --project-ref dgnecbcbydpnjhukocjg --no-verify-jwt
   ```

Sau khi deploy, nút **Hỏi AI về CRM** trên trang sẽ hoạt động ngay. Khi thay đổi tháng, AI tự chuyển sang phân tích dữ liệu của tháng mới. Số điện thoại không được gửi sang DeepSeek.

## Cập nhật hoặc thay API key

Chạy lại bước 2 với key mới. Secret có hiệu lực ngay, không cần deploy lại function. Không dán key vào `index.html`, `.env` được commit, hoặc GitHub Pages.

