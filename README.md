<div align="center">

# NT-GPS

**Module giả vị trí & mô phỏng lộ trình cho Android (LSPosed)**

Chọn điểm trên bản đồ hoặc để máy "lái xe" theo lộ trình thật: tốc độ, đèn đỏ, lặp A → B → A.

[**⬇ Tải bản mới nhất**](https://github.com/Ndntien/ndnt-licenses/releases/latest) · [Báo lỗi](https://github.com/Ndntien/NT-GPS/issues/new/choose) · [Liên hệ mua license](#liên-hệ)

</div>

---

## Tính năng

- **Giả vị trí theo từng app**: chỉ app bạn chọn trong *Target Apps* mới bị giả, các app khác giữ nguyên.
- **Chọn điểm trên bản đồ** (OpenStreetMap, có thêm nguồn bản đồ khác), tìm địa điểm, lưu **yêu thích**.
- **Mô phỏng lộ trình**
  - Lấy đường đi thật từ OSRM (không cần key) hoặc Mapbox Directions.
  - Tốc độ 5–120 km/h, dừng đèn đỏ ngẫu nhiên, chế độ lặp.
  - Chạy nền bằng foreground service, đóng app vẫn chạy.
  - Ghi lại và lưu lộ trình để dùng lại.
- **Tinh chỉnh** độ chính xác, độ cao, tốc độ, ngẫu nhiên hóa trong bán kính.
- **SiêuPro**: nhóm tùy chọn nâng cao cho người dùng rành kỹ thuật.
- **Giấy phép theo máy**, gia hạn và cập nhật ngay trong app.
- **Dùng thử miễn phí** một lần cho mỗi máy trước khi mua.

## Yêu cầu

| Mục | Yêu cầu |
|---|---|
| Hệ điều hành | Android 10 trở lên (API 29+) |
| Root | Bắt buộc |
| Framework | LSPosed hỗ trợ libxposed API 101+ (bản Vector) |
| Mạng | Cần internet khi mở app (kiểm tra giấy phép) |

## Cài đặt

1. Vào trang [**Releases**](https://github.com/Ndntien/ndnt-licenses/releases/latest), tải file `.apk` mới nhất.
2. Cài APK như app thường (bật *Cho phép cài từ nguồn này* nếu máy hỏi).
3. Mở **LSPosed** → *Modules* → bật module → chọn phạm vi (scope) theo hướng dẫn trong app.
4. Mở app NT-GPS, cấp quyền **vị trí** và **thông báo**.
5. Vào **Target Apps**, chọn app cần giả vị trí, rồi **khởi động lại máy một lần**.

> Bản cập nhật sau này cài đè trực tiếp lên bản cũ, không cần gỡ.

## Sử dụng nhanh

- **Giả một điểm**: chạm điểm trên bản đồ → bấm **Play**. Dùng **Unset** để tắt giả vị trí.
- **Chạy lộ trình**: Menu → *Route simulation* → nhập điểm đi/đến (hoặc chọn từ yêu thích) → **Start route**.
- Dừng lộ trình chỉ dừng di chuyển; vị trí giả ở lại điểm cuối.

## Giấy phép & dùng thử

1. Mở app, màn hình giấy phép hiện **Mã máy** dạng `NDNT…`.
2. Bấm **Dùng thử** để thử miễn phí, hoặc [gửi Mã máy cho mình](#liên-hệ) để mua license.
3. Sau khi thanh toán, bấm **Kiểm tra** trong app để kích hoạt. Không cần gửi file hay nhập tay.

License gắn với **một máy**. Đổi máy hoặc reset máy, hãy báo trước để được hỗ trợ chuyển.

## Câu hỏi thường gặp

**Máy chưa root dùng được không?**
Không. Module chạy qua LSPosed nên cần root.

**Vì sao app đòi internet?**
Để kiểm tra giấy phép và cập nhật. Có thể dùng offline trong thời gian ngắn sau lần kiểm tra gần nhất.

**App báo "bị chỉnh sửa" (TAMPERED)?**
Bạn đang dùng bản không phải bản chính thức. Hãy gỡ và tải lại APK từ trang Releases chính thức (ndnt-licenses).

**Bản mới không cài đè được?**
Chỉ APK tải từ trang Releases chính thức (ndnt-licenses) mới cùng chữ ký. Gỡ bản lạ trước rồi cài lại.

## Liên hệ

- Mua license / hỗ trợ: **[điền Zalo / Telegram / Facebook của bạn]**
- Báo lỗi: [mở Issue](https://github.com/Ndntien/NT-GPS/issues/new/choose) (nhớ ghi model máy, Android, phiên bản app; **đừng** dán token hay thông tin cá nhân).

## Lưu ý

- Chỉ dùng để **kiểm thử và bảo vệ riêng tư**. Giả vị trí có thể vi phạm điều khoản của một số ứng dụng; bạn tự chịu trách nhiệm khi sử dụng.
- Phần mềm đóng mã nguồn. Repo này chỉ chứa giới thiệu và tài liệu; bản dựng chính thức phát hành tại [ndnt-licenses](https://github.com/Ndntien/ndnt-licenses/releases). Xem [LICENSE](LICENSE).
- Dự án dựa trên [XposedFakeLocation](https://github.com/noobexon1/XposedFakeLocation) (giấy phép MIT) cùng một số thư viện mã nguồn mở. Xem [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
