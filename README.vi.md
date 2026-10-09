# Bộ hẹn giờ giới thiệu

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Bộ hẹn giờ một trang để mọi người lần lượt giới thiệu bản thân trong buổi họp lớp hay sự kiện tương tự. Chỉ cần mở `index.html` trong trình duyệt — không cần cài đặt, máy chủ hay kết nối internet.

## Cách dùng

1. Mở `index.html` trong trình duyệt (Safari / Chrome).
2. Ở màn hình cài đặt: tải CSV (xem `sample/participants.csv` hoặc “Tải dữ liệu mẫu”), bật/tắt điểm danh từng người, sắp xếp theo trường bất kỳ, đặt tiêu đề / thời gian mỗi người / danh xưng / ngôn ngữ và thử âm thanh.
3. Bấm “Vào bộ hẹn giờ” (việc này cũng bật âm thanh).
4. Vận hành bộ hẹn giờ:

| Thao tác | Kết quả |
|---|---|
| `Space` / nút Bắt đầu | Bắt đầu người tiếp theo (kèm tiếng vỗ tay) |
| Bấm vào tên ở danh sách bên phải | Bắt đầu người đó; những người đứng trước chuyển sang “Bị bỏ qua” |
| Bấm vào tên trong “Bị bỏ qua” | Bắt đầu người đó |
| Bỏ chọn “Có mặt” trong “Bị bỏ qua” | Sau khi xác nhận, đánh dấu vắng mặt và xóa khỏi danh sách (bộ hẹn giờ vẫn chạy) |

Còn 10 giây: tiếng tích mỗi giây · còn 3 giây: tiếng bíp dồn dập · 0 giây: tiếng nổ và nhãn “Hết giờ!”. Góc trên bên phải hiển thị tổng thời gian đã trôi qua; cột bên phải hiển thị 10 người tiếp theo.

## Định dạng CSV

Dòng đầu tiên là tiêu đề. Tự động nhận UTF-8 và Shift_JIS. Cột tên và danh xưng được chọn tự động theo tiêu đề (ví dụ `tên`, `danh xưng`) và có thể đổi trong cài đặt. Nếu ô danh xưng trống, sẽ dùng danh xưng mặc định.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Ngôn ngữ

16 ngôn ngữ: đổi bằng mục “Ngôn ngữ” ở màn hình cài đặt (lần đầu dùng ngôn ngữ của trình duyệt, lựa chọn của bạn được lưu). Văn bản giao diện, tiêu đề và danh xưng mặc định, dữ liệu mẫu và vị trí danh xưng (trước/sau tên) thay đổi theo ngôn ngữ; tiếng Ả Rập dùng bố cục từ phải sang trái. Bản dịch chưa được người bản ngữ kiểm tra — hãy sửa `I18N` trong `index.html` để chỉnh. Muốn thêm ngôn ngữ, thêm mục vào `LANGS`, `I18N` và `SAMPLE_NAMES`.

## Di động

Có bố cục cho điện thoại dọc và ngang. Trên iPhone, công tắc im lặng sẽ tắt âm thanh. Mở tệp qua ứng dụng Tệp là chắc chắn nhất; nếu đăng lên GitHub Pages thì chỉ cần mở một URL.

## Cấu trúc

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` chứa tất cả: từ điển ngôn ngữ, bộ phân tích CSV, màn hình cài đặt, tổng hợp âm thanh bằng Web Audio (không cần tệp âm thanh), logic hẹn giờ (dựa trên dấu thời gian nên không bị lệch) và màn hình chạy. Cài đặt và tiến trình được tự động lưu vào `localStorage`.

Giấy phép: [MIT](LICENSE)
