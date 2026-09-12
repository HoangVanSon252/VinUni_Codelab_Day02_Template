# Báo Cáo Nhiệm Vụ Cá Nhân - AI Product Scoping (Vin Smart Future)

## 1. Phase 1 — SCAN (Tìm kiếm cơ hội)
Dưới đây là 5 bài toán thực tế tôi đã phân tích dựa trên 4 Lenses cho các công ty thành viên của Vingroup:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinmec** | Tốn thời gian | Bác sĩ mất quá nhiều thời gian viết tóm tắt hồ sơ xuất viện (Discharge Summary) từ hàng loạt ghi chú lâm sàng. |
| 2 | **Vinhomes** | AI-upgrade | Khách hàng hỏi các thủ tục hành chính, ban quản lý phản hồi chậm hoặc rập khuôn, cần trợ lý ảo hướng dẫn và tự động tạo nháp đơn từ. |
| 3 | **VinFast** | AI-upgrade | Kỹ thuật viên gặp khó khăn khi tra cứu mã lỗi từ những mô tả bệnh xe bằng ngôn ngữ tự nhiên (tiếng Việt không chuẩn) của khách hàng. |
| 4 | **Vinpearl** | Pain từ người khác | Quản lý khách sạn mất nhiều thời gian đọc và phân loại thủ công hàng ngàn review từ các nền tảng OTA (Booking, Agoda) để xử lý khiếu nại. |
| 5 | **Xanh SM** | Lặp lại | So khớp hóa đơn và định tuyến lại cuốc xe khi khách hàng thay đổi lộ trình nhiều lần trong giờ cao điểm. |

---

## 2. Phase 2 — QUICK-ASSESS (3 Quick Problem Cards)
Từ danh sách trên, tôi chọn ra 3 bài toán tiềm năng nhất để làm thẻ đánh giá nhanh.

### Card #1 — Vinmec: Tóm tắt hồ sơ xuất viện
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Bác sĩ tốn thời gian tổng hợp ghi chú lâm sàng    │
│ thành hồ sơ xuất viện cho bệnh nhân.                        │
│ Công ty thành viên: [x] Vinmec                              │
│                                                             │
│ Ai đang đau? Bác sĩ (quá tải), Bệnh nhân (chờ đợi)          │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Mở hồ sơ bệnh án điện tử (EMR)                         │
│   → 2. Đọc lại lịch sử khám, xét nghiệm, đơn thuốc          │
│   → 3. Viết tay bản tóm tắt xuất viện (ngôn ngữ y khoa)     │
│   → 4. Dịch tóm tắt thành hướng dẫn dễ hiểu cho bệnh nhân   │
│                                                             │
│ Bước nào tốn nhất? Bước 2, 3 và 4 (⏱ 20-30 phút/bệnh nhân)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3 và 4           │
│ (AI tự động kéo dữ liệu EMR -> Draft tóm tắt & hướng dẫn)   │
│                                                             │
│ Đo thành công bằng gì?                                      │
│ Giảm thời gian làm hồ sơ từ 25 phút ──> dưới 5 phút.        │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
└─────────────────────────────────────────────────────────────┘
```

### Card #2 — Vinhomes: Trợ lý thủ tục hành chính
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Hỗ trợ cư dân tra cứu và tự động điền đơn từ      │
│ cho các thủ tục hành chính (đăng ký thi công, thẻ xe).      │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Cư dân (chờ đợi), Ban quản lý (trả lời lặp lại)│
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Cư dân nhắn tin trên app Resident hoặc gọi hotline     │
│   → 2. Lễ tân đọc/nghe hiểu yêu cầu                         │
│   → 3. Lễ tân gửi lại file biểu mẫu PDF/Word                │
│   → 4. Cư dân in, điền, ký và nộp lại cho ban quản lý       │
│                                                             │
│ Bước nào tốn nhất? Bước 2, 3, 4 (⏱ Có thể kéo dài 1-2 ngày) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 và 3           │
│ (AI chatbot hiểu ý định -> tự động điền sẵn form (Draft))   │
│                                                             │
│ Đo thành công bằng gì?                                      │
│ 80% yêu cầu thủ tục được giải quyết ngay lập tức (under 1m).│
│                                                             │
│ Quick Architecture: [x] Agent (với khả năng gọi API điền form)
└─────────────────────────────────────────────────────────────┘
```

### Card #3 — VinFast: Chẩn đoán mã lỗi qua mô tả
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Chẩn đoán mã lỗi sơ bộ cho xe VinFast từ các      │
│ mô tả bằng ngôn ngữ nói của khách hàng.                     │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau? Tư vấn viên dịch vụ, Kỹ thuật viên (chẩn đoán) │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Khách hàng gọi tổng đài mô tả lỗi ("xe có tiếng kêu")  │
│   → 2. Tư vấn viên ghi chép lại theo ý hiểu                 │
│   → 3. Kỹ thuật viên đọc ghi chép, tra cứu sổ tay kỹ thuật  │
│   → 4. Phân loại mã lỗi và điều phối phụ tùng sửa chữa      │
│                                                             │
│ Bước nào tốn nhất? Bước 2 và 3 (⏱ 15 phút - nhiều sai sót)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 và 3           │
│ (AI trích xuất từ khóa bệnh xe -> Map với CSDL mã lỗi)      │
│                                                             │
│ Đo thành công bằng gì?                                      │
│ Tỉ lệ dự đoán đúng cụm lỗi (hệ thống) đạt trên 90%.         │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
└─────────────────────────────────────────────────────────────┘
```

---

## 3. Hướng xử lý vấn đề, Workflow và Giải pháp giải quyết
(Chọn bài toán tiêu biểu **Card #1 - Vinmec: Tóm tắt hồ sơ xuất viện** để phân tích sâu theo định hướng của Lab)

### 3.1. Phân tích điểm nghẽn (Current-State Workflow & Bottleneck)
*   **Workflow hiện tại:** Bác sĩ khám → Nhập liệu rải rác trong EMR qua nhiều ngày → Bệnh nhân xuất viện → Bác sĩ phải lật lại hồ sơ đọc toàn bộ thông tin → Soạn thảo tóm tắt chuyên môn → Dịch ra ngôn ngữ phổ thông cho bệnh nhân hiểu (chế độ dinh dưỡng, nhắc nhở uống thuốc).
*   **Bottleneck (Điểm nghẽn):** Khâu đọc lại hồ sơ tổng hợp và dịch sang ngôn ngữ dễ hiểu tốn rất nhiều thời gian (20-30 phút/bệnh nhân) và là nguyên nhân chính khiến bác sĩ bị quá tải, đồng thời khiến bệnh nhân phải chờ đợi giấy tờ xuất viện lâu.

### 3.2. Hướng giải quyết bằng AI (Future-State Flow)
Giải pháp là xây dựng một **LLM Feature** (tính năng hỗ trợ từ LLM) tích hợp trực tiếp vào hệ thống Hồ sơ bệnh án điện tử (EMR) hiện tại. Không cần đến một Agent hoàn toàn tự trị, vì quy trình này cần kiểm soát chặt chẽ.

*   **Future Workflow (Workflow tích hợp AI):**
    1.  **Trigger:** Bác sĩ ấn nút "Tạo hồ sơ xuất viện AI" trên hệ thống EMR.
    2.  **AI Step (Auto-pull & Summarize):** Hệ thống lập tức gọi API nội bộ kéo tất cả text từ đơn thuốc, kết quả lab, chẩn đoán. Một system prompt thiết kế nghiêm ngặt sẽ yêu cầu LLM tóm tắt theo đúng Schema chuẩn y khoa.
    3.  **AI Step (Translate):** LLM tự động viết thêm một phần "Dành cho bệnh nhân" với ngôn ngữ đơn giản, dễ hiểu, liệt kê việc cần làm sau xuất viện.
    4.  **Human Step (HITL - Human in the loop):** Bác sĩ tiến hành đọc lại bản Draft do AI tạo ra. Bác sĩ chỉnh sửa, thêm bớt ý (nếu cần), sau đó click "Phê duyệt & Ký số".
    5.  **Fallback:** Nếu LLM phản hồi chậm hoặc lỗi, luồng sẽ tự động quay về khung nhập liệu thủ công truyền thống để bác sĩ tự gõ như cũ.

### 3.3. Ranh giới vận hành (Operational Boundary) để giải quyết vấn đề an toàn
Trong y tế, một sai sót do AI "ảo giác" (Hallucination) là không thể chấp nhận được:
*   **No-Go (Tuyệt đối không được làm):** AI bị nghiêm cấm việc tự suy diễn chẩn đoán mới, thay đổi liều lượng thuốc, hoặc đưa ra quyết định lâm sàng. Nó chỉ được quyền tổng hợp dữ liệu *đã có sẵn*.
*   **Guardrails (Ranh giới bắt buộc):** Mọi bản text AI sinh ra đều phải hiển thị dạng "Bản Nháp (Draft)" và phải có sự can thiệp phê duyệt của bác sĩ (HITL) trước khi ra quyết định in hoặc gửi cho bệnh nhân.

---

## 4. Phase 6 — AI Log & Reflection (Nhật ký tương tác AI)
*   **AI đã giúp gì:** AI là một "thought partner" xuất sắc giúp tôi nhanh chóng nghĩ ra 5 bài toán thực tế sát với vận hành của hệ sinh thái Vingroup thông qua các Lenses được hướng dẫn. Khi cần phản biện cho "Quick Problem Cards", AI đã chỉ ra những điểm yếu trong việc thiết lập ranh giới an toàn.
*   **AI trả lời sai hoặc chưa tối ưu ở đâu:** Trong những câu hỏi đầu tiên, AI hay đưa ra các Use case về phân tích dữ liệu lớn offline hoặc phân tích dự báo (dùng Machine Learning truyền thống) thay vì các Use Case GenAI tối ưu hóa quy trình thủ công thời gian thực.
*   **Cách sửa prompt để khắc phục:** Tôi đã phải định hướng lại role (nhập vai) cho AI. Yêu cầu AI hóa thân thành "nhân viên điều vận thực địa đang bị quá tải công việc giấy tờ, nhập liệu" để AI đưa ra các Use Case "Time-consuming" sát thực tế nhất. Kết quả thu được rất chất lượng và logic.
