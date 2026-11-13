# ROBOCON KCK · Chấm công và kế hoạch

Trang chấm công và theo dõi công việc của đội ROBOCON KCK (UNETI).

**Mở trang:** https://tumo205.github.io/robocon-kck/

## Có gì trong trang

- **Chấm công** – bấm *Vào ca* / *Ra ca* để ghi giờ thực, hoặc nhập giờ vào ô khi chấm bù ngày khác. Trang tự tính số giờ, đi muộn và về sớm theo ca làm việc (đặt ở nút *Ca làm việc*). Ô *Không nghỉ / Nghỉ phép / Vắng mặt* dùng cho người không đi làm hôm đó.
- **Mã QR** – quản lý bấm *Mã QR* để hiện mã lên màn hình. Thành viên quét bằng camera điện thoại, nhập họ tên, mã sinh viên, lớp, số điện thoại rồi bấm *Vào ca* / *Ra ca*. Giờ lấy từ máy chủ.
- **Bảng công** – tổng hợp theo tháng: ngày công, số lần đi muộn, nghỉ phép, vắng và tổng giờ.
- **Công việc** – giao việc, hạn hoàn thành, tiến độ.
- **Thành viên** – danh sách đội; thêm từng người hoặc *Nhập từ Excel* (chọn file `.xlsx` hay dán các ô chép từ Excel).
- **Xuất Excel** – tải bảng đang xem thành file `.xlsx`.

## Chống chấm công hộ bằng mã QR

- **Mã đổi sau mỗi 15 giây.** Ảnh chụp mã gửi cho người khác chỉ còn dùng được trong khoảng nửa phút. Muốn *Ra ca* cũng phải quét lại mã đang hiển thị.
- **Mỗi điện thoại chỉ chấm cho một người trong ngày**, và một lần quét chỉ dùng cho một người.
- **Kiểm tra vị trí (tùy chọn).** Trong hộp *Mã QR*, bấm *Chỉ nhận chấm công ở gần đây* để lấy vị trí máy quản lý làm tâm; lượt chấm từ xa hơn bán kính đã chọn sẽ không được nhận.
- Lượt quét không qua được các kiểm tra trên không bị mất: nó nằm trong mục **cần xem lại** ở đầu danh sách chấm công để quản lý *Chấp nhận* hoặc *Bỏ*.
- Thông tin thành viên gửi qua mã QR được mã hóa, chỉ trang của quản lý đọc được.

Các biện pháp này làm việc chấm hộ khó hơn nhiều nhưng không thay được việc quản lý nhìn lại danh sách: hai người phối hợp ngay tại chỗ bằng hai điện thoại thì trang không phân biệt được.

## Dữ liệu dùng chung giữa các quản lý

Mặc định dữ liệu chỉ lưu trong trình duyệt của từng máy. Để mọi quản lý thấy cùng một dữ liệu, trang nối với một **Firebase Realtime Database**:

1. Tạo project tại https://console.firebase.google.com, rồi **Build → Realtime Database → Create Database** (vị trí Singapore, *locked mode*).
2. Mở tab **Rules**, dán nội dung file [`database.rules.json`](database.rules.json), bấm **Publish**.
3. Trong trang, bấm nút trạng thái ở góc trên bên phải → dán địa chỉ database → **Kết nối**. Trang tạo ra **link quản lý**.
4. Gửi link quản lý cho những người quản lý. Ai mở link đó đều xem và sửa được dữ liệu chung, nên chỉ gửi cho đúng người.

Địa chỉ database và khóa bí mật nằm trong link quản lý, không nằm trong mã nguồn.

## Chỉnh sửa

Trang gồm `index.html` và hai file ảnh logo (`logo.png`, `icon.png`), không cần cài đặt hay build. Sửa file rồi đẩy lên nhánh `main` là trang tự cập nhật.
