# 01 — Problem Scan & Quick Assess

> Các số liệu thời gian, sản lượng và tỷ lệ dưới đây là **baseline giả định để thiết kế pilot**. Cần xác thực bằng log vận hành, dữ liệu ẩn danh và phỏng vấn người dùng trước khi cam kết KPI.

## Phase 1 — SCAN

Tôi sử dụng bốn lens: tác vụ lặp lại, tác vụ tốn thời gian, cơ hội nâng cấp bằng AI và pain point của stakeholder.

| # | Công ty thành viên | Lens | Bài toán thực tế / bottleneck |
|---:|---|---|---|
| 1 | Vinhomes | Lặp lại | CSKH phải đọc, gắn nhãn, xác định mức ưu tiên và chuyển từng phản ánh cư dân đến đúng đội kỹ thuật hoặc CSKH. |
| 2 | VinFast | Lặp lại | Nhân viên đối chiếu hóa đơn sạc của đối tác với log phiên sạc để phát hiện chênh lệch kWh, đơn giá và VAT. |
| 3 | Vinpearl | Pain từ người khác | Quản lý phải tổng hợp review xấu từ nhiều kênh để phát hiện sớm vấn đề vệ sinh, an toàn hoặc thái độ phục vụ. |
| 4 | Xanh SM | Tốn thời gian | Điều phối viên đọc ghi chú sự cố của tài xế, tra SOP và soạn hướng dẫn xử lý phù hợp với từng tình huống. |
| 5 | Vinmec | AI có thể tốt hơn | Bác sĩ mất thời gian tổng hợp bệnh án, xét nghiệm và ghi chú để soạn tóm tắt xuất viện trước khi ký duyệt. |

### Tiêu chí chọn top 3

Tôi ưu tiên các bài toán có workflow lặp lại, đầu vào đủ dữ liệu để thử nghiệm, metric đo được và có thể giữ người duyệt ở bước quyết định. Theo tiêu chí đó, top 3 là: **Vinhomes ticket triage**, **VinFast đối chiếu hóa đơn sạc** và **Vinpearl cảnh báo review khẩn cấp**.

## Phase 2 — QUICK-ASSESS

### QUICK PROBLEM CARD #1 — Vinhomes ticket triage

| Hạng mục | Nội dung |
|---|---|
| Bài toán | Phân loại, ưu tiên, định tuyến và soạn nháp phản hồi cho phản ánh cư dân. |
| Công ty / stakeholder | **Vinhomes**; CSKH, ban quản lý vận hành và đội kỹ thuật. |
| Actor | Nhân viên CSKH và điều phối vận hành tại ban quản lý tòa nhà. |
| Workflow hiện tại | Nhận ticket trên app → đọc nội dung/ảnh → tra danh mục và SOP → chọn đội xử lý/mức ưu tiên → tạo work order → soạn phản hồi và chuyển việc. Baseline giả định: 8 phút/ticket. |
| Bottleneck | Ticket ngắn, viết tắt hoặc có nhiều vấn đề làm bước hiểu ngữ cảnh và chọn đội mất khoảng 6/8 phút; dễ chuyển sai đội hoặc bỏ sót tín hiệu khẩn cấp. |
| AI solution | Rule phát hiện tín hiệu khẩn cấp, SLA và phân quyền; LLM đề xuất nhãn, mức ưu tiên, đội nhận việc, lý do và bản nháp phản hồi tiếng Việt. CSKH phải xem và duyệt. |
| Metric pilot | Median triage từ 8 xuống **≤3 phút**; **≥85%** nhãn/đội được reviewer chấp nhận; recall **100%** trên tập test ticket khẩn cấp; không tự đóng ticket. |
| Quick architecture | **Rule + LLM feature**, không dùng agent tự trị; confidence thấp thì chuyển hàng đợi thủ công. |

### QUICK PROBLEM CARD #2 — VinFast đối chiếu hóa đơn sạc

| Hạng mục | Nội dung |
|---|---|
| Bài toán | Tự động phát hiện chênh lệch giữa hóa đơn sạc của đối tác và log phiên sạc. |
| Công ty / stakeholder | **VinFast**; nhân viên tài chính vận hành trạm sạc và đối tác cung cấp dịch vụ. |
| Actor | Nhân viên tài chính hoặc vận hành phụ trách đối soát. |
| Workflow hiện tại | Tải file hóa đơn → xuất log phiên sạc → chuẩn hóa mã trạm, thời gian và xe → so khớp kWh, đơn giá, VAT → kiểm tra ngoại lệ → lập danh sách cần xử lý. |
| Bottleneck | Mã trạm, múi giờ và định dạng file không thống nhất; nhân viên phải kiểm tra thủ công từng dòng, giả định khoảng 10 phút/hóa đơn. |
| AI solution | Parser/ETL và luật đối soát làm phần chính; LLM chỉ chuẩn hóa ghi chú và giải thích ngoại lệ cho nhân viên, không tự phê duyệt thanh toán. |
| Metric pilot | **≥95%** dòng được đối soát tự động; thời gian xử lý giảm từ 10 xuống **≤2 phút/hóa đơn**; **100%** ngoại lệ có bằng chứng log để reviewer kiểm tra. |
| Quick architecture | **Rule/ETL trước, LLM tùy chọn**; bài toán này có thể triển khai không cần agent. |

### QUICK PROBLEM CARD #3 — Vinpearl cảnh báo review dịch vụ

| Hạng mục | Nội dung |
|---|---|
| Bài toán | Tổng hợp review đa kênh và cảnh báo sớm các phàn nàn nghiêm trọng về dịch vụ. |
| Công ty / stakeholder | **Vinpearl**; duty manager, đội chăm sóc khách hàng và quản lý khách sạn. |
| Actor | Duty manager và nhân viên chăm sóc khách hàng. |
| Workflow hiện tại | Mở từng nền tảng review → đọc review → ghi vào bảng tổng hợp → phân loại chủ đề/mức độ → chuyển manager → soạn phản hồi hoặc tạo việc khắc phục. |
| Bottleneck | Review tự do, đa ngôn ngữ và số lượng lớn; vấn đề an toàn, vệ sinh hoặc thái độ phục vụ có thể bị phát hiện muộn. Baseline giả định: khoảng 5 phút/review. |
| AI solution | LLM tóm tắt, dịch khi cần, gắn chủ đề/cảm xúc và đề xuất mức độ nghiêm trọng; rule ưu tiên từ khóa an toàn; manager duyệt cảnh báo và phản hồi. |
| Metric pilot | **≥90%** review nghiêm trọng được gắn cờ trong **15 phút**; thời gian tổng hợp hằng ngày giảm **≥60%**; **100%** cảnh báo nghiêm trọng có người xác nhận trước khi tạo việc. |
| Quick architecture | **LLM feature + rules**; không tự phản hồi khách và không tự kết luận sự cố an toàn. |

## Lựa chọn bài toán để deep-dive

Chọn **Card #1 — Vinhomes ticket triage**. Bài toán có đầu vào ngôn ngữ tự do phù hợp với LLM, nhưng vẫn có thể kiểm soát bằng rule, human-in-the-loop và fallback thủ công. Metric về thời gian, acceptance rate và recall ticket khẩn cấp cũng đủ cụ thể để thiết kế pilot.

Card #2 phù hợp hơn với ETL và rule-based vì dữ liệu có cấu trúc; LLM chỉ là phần bổ trợ. Card #3 có giá trị nhưng phụ thuộc quyền truy cập API, điều khoản dữ liệu và chất lượng review đa ngôn ngữ, nên cần xác minh tính khả thi trước.
