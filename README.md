# ROBOCON KCK · Chấm công và kế hoạch

Trang chấm công và theo dõi công việc của đội ROBOCON KCK (UNETI).

**Mở trang:** https://tumo205.github.io/robocon-kck/

## Có gì trong trang

- **Chấm công** – bấm *Vào ca* / *Ra ca* để ghi giờ thực, hoặc nhập giờ vào ô khi chấm bù ngày khác. Trang tự tính số giờ, đi muộn và về sớm theo ca làm việc (đặt ở nút *Ca làm việc*).
- **Mã QR mỗi ngày** – quản lý bấm *Mã QR* để hiện mã của hôm nay. Thành viên quét bằng camera điện thoại, nhập họ tên, mã sinh viên, lớp, số điện thoại rồi bấm *Vào ca* / *Ra ca*. Giờ lấy từ máy chủ; sang ngày mới mã cũ hết hiệu lực.
- **Bảng công** – tổng hợp theo tháng: ngày công, số lần đi muộn, nghỉ phép, vắng và tổng giờ.
- **Công việc** – giao việc, hạn hoàn thành, tiến độ.
- **Thành viên** – danh sách đội (họ tên, mã sinh viên, lớp, điện thoại).
- **Xuất CSV** – tải bảng đang xem về để mở bằng Excel.

## Dữ liệu dùng chung giữa các quản lý

Mặc định dữ liệu chỉ lưu trong trình duyệt của từng máy. Để mọi quản lý thấy cùng một dữ liệu, trang nối với một **Firebase Realtime Database**:

1. Tạo project tại https://console.firebase.google.com, rồi **Build → Realtime Database → Create Database** (vị trí Singapore, *locked mode*).
2. Mở tab **Rules**, dán nội dung file [`database.rules.json`](database.rules.json), bấm **Publish**.
3. Trong trang, bấm nút trạng thái ở góc trên bên phải → dán địa chỉ database → **Kết nối**. Trang tạo ra **link quản lý**.
4. Gửi link quản lý cho những người quản lý. Ai mở link đó đều xem và sửa được dữ liệu chung, nên chỉ gửi cho đúng người.

Địa chỉ database và khóa bí mật nằm trong link quản lý, không nằm trong mã nguồn. Thông tin thành viên gửi qua mã QR được mã hóa, chỉ trang của quản lý đọc được.

## Chỉnh sửa

Trang gồm `index.html` và hai file ảnh logo (`logo.png`, `icon.png`), không cần cài đặt hay build. Sửa file rồi đẩy lên nhánh `main` là trang tự cập nhật.
