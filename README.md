# nhan-su-dieu-phoi

**Vai Điều phối trong đội nhân sự A.I** — của [Tô Hải Đoàn](https://www.facebook.com/tohaidoan/).

Một plugin Claude Code, ba lệnh. Nó trả lời đúng câu hỏi mà một bộ não đầy dữ liệu vẫn không tự trả lời được: **tháng này tôi nên làm gì trước.**

> **Phiên bản:** `1.7.0` · 2026-09-23 · giấy phép MIT

---

## Cài

```bash
claude plugin marketplace add creator-ceo/nhan-su-dieu-phoi
```

```bash
claude plugin install dieu-phoi
```

## Ba lệnh, ba nhịp khác nhau

| Lệnh | Làm gì | Bao lâu một lần |
|---|---|---|
| `/banh-xe-cuoc-doi` | Chấm 8 khía cạnh cuộc sống → kế hoạch dài hạn + 90 ngày. **Nạp con người**, không nạp dữ liệu việc | 3 tháng |
| `/kham-benh` | Soi bạn đang tắc ở khâu nào — ~22 ô, kê đơn hai ngăn | 3 tháng |
| `/dieu-hanh` | Đọc bản khám → chốt con số và mục tiêu của khâu → mỗi tháng chữa **một quy trình** (việc mỗi ngày, cuối tháng nghiệm thu) → hết 90 ngày gọi tái khám | suốt 90 ngày |

### Ba lệnh ghép thành một hành trình chữa ba tháng

```
khám  →  chốt số của khâu  →  tháng 1: một quy trình  →  tháng 2: một quy trình  →  tháng 3: một quy trình  →  tái khám
```

1. **Khám** — `/kham-benh` chỉ ra khâu đang tắc và kê đơn. Đã làm bài khám trên web (tomedia.vn) trong 3 tháng gần đây thì khỏi khám lại: nói cho `/dieu-hanh` biết bài khám chỉ ra khâu nào, còn giữ email đơn thuốc thì dán vào.
2. **Chốt số** — `/dieu-hanh` hỏi con số hiện tại *(giờ bạn tự tay bỏ vào khâu đó · một con số kinh doanh của khâu)*, bạn tự đặt mục tiêu, và hẹn ngày tái khám — mặc định 90 ngày sau.
3. **Mỗi tháng một quy trình** — trong đúng khâu đó, chọn một quy trình để chữa. Cùng bạn lập khung giờ cố định mỗi ngày và việc cụ thể cho từng ngày, lập lại mỗi tuần; cuối tháng nghiệm thu quy trình đó đã tự chạy chưa. Tạo sẵn **file lịch nhắc** cho điện thoại: chuông mỗi ngày trước khung giờ, chuông trước mỗi lần nghiệm thu tháng, và chuông trước ngày tái khám 7 ngày. Mỗi quy trình đi đủ năm bước: **làm thật → đóng gói → tối ưu → đơn giản → tự động**.
4. **Tái khám** — tới ngày hẹn, `/dieu-hanh` dừng mọi việc khác và mời bạn khám lại. Đo lại đúng những con số cũ, đặt cạnh mục tiêu — không đo bằng cảm giác.

Cố định là **cái nhịp**. Khâu nào được chữa thì tuỳ bản khám của từng người.

⚠️ **`/dieu-hanh` không tự khám** — khâu lấy từ `/kham-benh`, hoặc từ bài khám bạn đã làm trên web. Nó không hỏi thêm để "kiểm lại" khâu bạn khai, vì hai bộ khám là hai kết quả khác nhau cho cùng một người, và **không có gì báo khi chúng lệch**.

## ⚙️ Máy giữ chỗ, không phải AI giữ chỗ

Bài khám hơn hai chục ô. Nếu AI tự giữ chỗ thì nó sẽ đổ cả bài ra một lượt, hoặc nhảy cóc, hoặc tự chấm hộ bạn — cả ba đều làm bản khám thành vô nghĩa mà đọc vẫn trôi chảy.

Nên vị trí nằm trong file (`bo-kham/kham.mjs`), **nhả đúng một ô mỗi lượt**. AI không biết câu kế tiếp cho tới khi ghi xong câu đang hỏi.

⚡ **Câu trả lời của bạn ghi vào KHO CỦA BẠN** (`kham-ra/phien/`), không ghi vào thư mục plugin. Thư mục plugin bị thay mỗi lần `claude plugin update` — khám dở mà cập nhật một cái là mất sạch, và không có gì báo.

## ⚠️ Cần cái nền chạy trước

Vai này **đọc** bộ não thứ 2 của bạn, nó không dựng ra bộ não đó:

```bash
git clone https://github.com/creator-ceo/nhan-su-thu-thu.git
```

| Lớp | Skill | Ở đâu |
|---|---|---|
| Bộ khung bộ não thứ 2 | `/onboard` · `/nap-kho` · `/kiem-chung` | kho `nhan-su-thu-thu` — **cài trước** |
| Vai Điều phối | `/banh-xe-cuoc-doi` · `/kham-benh` · `/dieu-hanh` | **kho này** |

Chưa chạy `/onboard` thì chưa có gì để điều phối. Vai này vẫn khám được, nhưng bản đề xuất không có chỗ để ghi vào — và lời khuyên sẽ chung chung vì nó không biết bạn bán gì cho ai.

## Vai này nằm ở đâu trong đội

| Vai | Kho | Trạng thái |
|---|---|---|
| 🧑‍🏫 **Thủ thư** — cái nền, cài trước tiên | `creator-ceo/nhan-su-thu-thu` | ✅ |
| 🎛️ **Điều phối** *(Tổng giám đốc)* | `creator-ceo/nhan-su-dieu-phoi` | ✅ **kho này** |
| ✍️ **Content** | `creator-ceo/nhan-su-content` | ✅ |
| 💰 **Bán hàng** | `creator-ceo/nhan-su-ban-hang` | ✅ |
| 🔍 **Nghiên cứu** | `creator-ceo/nhan-su-nghien-cuu` | 🟡 bản tạm |
| 🎨 **Thiết kế** | `creator-ceo/nhan-su-thiet-ke` | 🟡 bản tạm |
| 🤝 **Chăm sóc** | `creator-ceo/nhan-su-cham-soc` | 🟡 bản tạm |

⚠️ **Bảng giao việc của `/dieu-hanh` nói thẳng vai nào chưa có.** Gặp việc thuộc vai chưa phát, nó bảo bạn **làm tay hoặc chọn quy trình khác** — không gọi một lệnh không tồn tại, và không ép sang vai gần đúng nhất.

---

## Ai làm cái này

**Tô Hải Đoàn** — người làm nội dung và xây thương hiệu cá nhân tại Việt Nam. Bánh xe cuộc đời là công cụ tôi tự dùng từ 2015; bộ khám là quy trình tôi dùng cho công việc của chính mình, đóng gói lại để bạn chạy trên dữ liệu của bạn.

**Kẹt ở đâu thì nhắn tôi:** [facebook.com/tohaidoan](https://www.facebook.com/tohaidoan/)
