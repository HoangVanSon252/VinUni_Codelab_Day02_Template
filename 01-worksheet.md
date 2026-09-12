# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

STTCông ty thành viênLĩnh vựcBài toán thực tếTác động kinh doanh (Impact)
1VinFastÔ tô / Sản xuấtDự báo nhu cầu phụ tùng thay thế và linh kiện bảo dưỡng tại các xưởng dịch vụ.Giảm chi phí tồn kho, tối ưu hóa thời gian chờ sửa chữa của khách hàng.
2VinmecY tế / Chăm sóc sức khỏeTối ưu hóa lịch hẹn khám và điều phối nhân sự y tế theo khung giờ cao điểm.Giảm thời gian chờ của bệnh nhân, nâng cao công suất phục vụ của bác sĩ.
3VinpearlDu lịch / Nghỉ dưỡngTự động hóa điều chỉnh giá phòng khách sạn và dịch vụ (Dynamic Pricing) theo thời gian thực.Tối ưu hóa doanh thu (RevPAR) dựa trên cung - cầu và hành vi thị trường.
4VinhomesBất động sản / Vận hànhQuản lý và tối ưu hóa tiêu thụ năng lượng thông minh tại các khu đô thị lớn (Smart City).Giảm chi phí vận hành hạ tầng, đáp ứng tiêu chí phát triển bền vững (ESG).
5Vincom RetailBán lẻ / Trung tâm thương mạiPhân tích hành vi và luồng di chuyển của khách hàng tại các TTTM qua thị giác máy tính.
---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
## Bảng quét cơ hội (SCAN)

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast | Ô tô / Sản xuất | Dự báo nhu cầu phụ tùng thay thế và linh kiện bảo dưỡng tại các xưởng dịch vụ để tối ưu tồn kho và giảm thời gian chờ của xe. |
| 2 | Vinmec | Y tế / Chăm sóc sức khỏe | Tối ưu hóa lịch hẹn khám và điều phối nhân sự y tế theo thời gian thực để giảm thời gian chờ đợi của bệnh nhân. |
| 3 | Vinpearl | Du lịch / Nghỉ dưỡng | Tự động hóa định giá phòng khách sạn (Dynamic Pricing) theo cung - cầu thị trường và thời gian thực để tối đa hóa doanh thu (RevPAR). |
| 4 | Vinhomes | Bất động sản / Vận hành | Quản lý và tối ưu hóa tiêu thụ năng lượng thông minh (Smart City) cho hệ thống chiếu sáng và hạ tầng khu đô thị. |
| 5 | Vincom Retail | Bán lẻ / TTTM | Phân tích hành vi và luồng di chuyển của khách hàng bằng Computer Vision để tối ưu hóa quy hoạch mặt bằng và giá thuê gian hàng. |

---
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Dự báo nhu cầu phụ tùng thay thế và linh  │
│ kiện bảo dưỡng tại xưởng dịch vụ VinFast để tối ưu tồn kho. │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Quản lý kho, Chuỗi cung ứng, Thợ kỹ thuật │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách mang xe đến xưởng ──> 2. Thợ lập danh sách phụ tùng ──> 3. Thủ kho check phần mềm thủ công ──> 4. Thiếu hàng phải đặt tổng kho  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 120-240 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Dự báo nhu cầu tự động│
│ và tạo đề xuất đặt hàng trước dựa trên dữ liệu lịch sử và odo.│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   VD: "Giảm tỷ lệ thiếu hụt phụ tùng từ 15% ──> under 5%"   │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Tối ưu hóa lịch hẹn khám và điều phối nhân│
│ sự y tế theo thời gian thực để giảm thời gian chờ tại Vinmec│
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Lễ tân, Bác sĩ, Bệnh nhân             │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Bệnh nhân đăng ký lịch ──> 2. Lễ tân xếp slot thủ công ──> 3. Bệnh nhân đến viện chờ khám ──> 4. Bác sĩ khám thực tế (thời gian lệch nhiều) │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 30-60 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Dự báo thời gian khám │
│ thực tế theo triệu chứng và tự động tối ưu hóa lịch hẹn.    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   VD: "Giảm thời gian chờ đợi trung bình từ 45 min ──> 15 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động hóa định giá phòng khách sạn      │
│ (Dynamic Pricing) theo thời gian thực để tối ưu doanh thu.  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác (Vinpearl)        │
│                                                             │
│ Ai đang đau (Actor)? Giám đốc doanh thu (Revenue Manager)   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tổng hợp công suất phòng ──> 2. Tra cứu giá đối thủ trên OTA ──> 3. Trình sếp duyệt giá ──> 4. Cập nhật thủ công lên PMS │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 180 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Quét dữ liệu thời gian│
│ thực, phân tích cung-cầu và tự động đề xuất/cập nhật giá.   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   VD: "Tăng doanh thu trung bình RevPAR từ baseline ──> +10%"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
