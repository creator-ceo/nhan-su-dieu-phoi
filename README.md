# nhan-su-dieu-phoi

**Vai Điều phối trong đội nhân sự A.I** — của [Tô Hải Đoàn](https://www.facebook.com/tohaidoan/).

Một plugin Claude Code, ba lệnh. Nó trả lời đúng câu hỏi mà một bộ não đầy dữ liệu vẫn không tự trả lời được: **tháng này tôi nên làm gì trước.**

> **Phiên bản:** `1.2.1` · 2026-09-07 · giấy phép MIT

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
| `/dieu-hanh` | Đọc bản khám gần nhất → chốt **một** việc cho tháng → nghiệm thu bằng hai con số | mỗi tháng |

⚠️ **`/dieu-hanh` không tự khám** — nó gọi `/kham-benh`. Hai bộ khám là hai kết quả khác nhau cho cùng một người, và **không có gì báo khi chúng lệch**.

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
| 🎛️ **Điều phối** | `creator-ceo/nhan-su-dieu-phoi` | ✅ **kho này** |
| ✍️ **Content** | `creator-ceo/nhan-su-content` | ✅ |
| 💰 Bán hàng | `creator-ceo/nhan-su-ban-hang` | 🟡 đang đóng gói |
| 🎨 Thiết kế · 🤝 Chăm sóc · 🔍 Nghiên cứu | — | ⬜ chưa |

⚠️ **Bảng giao việc của `/dieu-hanh` nói thẳng vai nào chưa có.** Gặp việc thuộc vai chưa phát, nó bảo bạn **làm tay hoặc chọn quy trình khác** — không gọi một lệnh không tồn tại, và không ép sang vai gần đúng nhất.

---

## Ai làm cái này

**Tô Hải Đoàn** — người làm nội dung và xây thương hiệu cá nhân tại Việt Nam. Bánh xe cuộc đời là công cụ tôi tự dùng từ 2015; bộ khám là quy trình tôi dùng cho công việc của chính mình, đóng gói lại để bạn chạy trên dữ liệu của bạn.

**Kẹt ở đâu thì nhắn tôi:** [facebook.com/tohaidoan](https://www.facebook.com/tohaidoan/)
