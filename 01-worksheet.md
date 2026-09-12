# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

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

Tôi ưu tiên các bài toán có dữ liệu hình ảnh/video và các tác vụ kiểm tra trực quan đang cần con người thực hiện thủ công, vì đây là những khu vực có tiềm năng ứng dụng Computer Vision.

### 📝 List bài toán của tôi:

| # | Subsidiary (VinFast/Xanh SM...) | Lens                               | Mô tả ngắn bài toán                                                                                                                                                                                                                                                                 |
| - | ------------------------------- | ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | **VinFast**                     | **Lặp lại (Repetitive)**           | **Visual Quality Inspection:** Nhân viên QC phải kiểm tra trực quan thân vỏ xe sau các công đoạn sản xuất để phát hiện các lỗi bề mặt như trầy xước, móp, sai lệch chi tiết hoặc lỗi hoàn thiện. Computer Vision có thể hỗ trợ phát hiện và khoanh vùng các vùng nghi ngờ trên ảnh. |
| 2 | **Xanh SM**                     | **Tốn thời gian (Time-consuming)** | **Vehicle Damage & Cleanliness Inspection:** Kiểm tra tình trạng ngoại thất và độ sạch của xe taxi trước/sau ca vận hành. Computer Vision có thể so sánh ảnh xe để phát hiện vết xước, móp, đèn vỡ hoặc các khu vực có dấu hiệu không sạch cần kiểm tra.                            |
| 3 | **Vinpearl / VinWonders**       | **Stakeholder Pain**               | **Crowd & Queue Monitoring:** Khách phải chờ lâu tại cổng, quầy dịch vụ hoặc khu trò chơi trong giờ cao điểm. Computer Vision từ camera có thể ước lượng số người và độ dài hàng chờ để cảnh báo điểm ùn tắc cho nhân viên vận hành.                                                |
| 4 | **Vinhomes**                    | **AI-upgrade**                     | **Parking Occupancy Detection:** Việc xác định vị trí đỗ xe còn trống trong bãi xe lớn có thể chậm hoặc phụ thuộc vào cảm biến riêng lẻ. Computer Vision có thể phân tích camera bãi xe để xác định ô trống/đã sử dụng và cập nhật trạng thái gần real-time.                        |
| 5 | **VinFast**                     | **Tốn thời gian (Time-consuming)** | **Vehicle Service Visual Triage:** Khi khách đưa xe đến xưởng, Service Advisor phải quan sát và ghi nhận thủ công các hư hỏng ngoại thất. Computer Vision có thể phát hiện và đánh dấu sơ bộ các vùng trầy, móp hoặc hư hỏng từ ảnh chụp xe để hỗ trợ tạo biên bản tiếp nhận.       |

> **Lưu ý:** Các giá trị thời gian và KPI bên dưới là baseline/target giả định dùng để xây dựng prototype trong phạm vi Lab. Các số liệu này cần được đo và xác nhận lại bằng dữ liệu vận hành thực tế trước khi triển khai.

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent│
└─────────────────────────────────────────────────────────────┘
```

Từ năm bài toán trên, tôi lựa chọn ba bài toán **#1, #2 và #3** để đánh giá sâu hơn. Cả ba đều có đầu vào hình ảnh/video rõ ràng, hiện tồn tại một bước quan sát thủ công và có output có thể kiểm chứng lại bởi con người.

---

## QUICK PROBLEM CARD #1 — VinFast Visual Quality Inspection

**Technical component:** Multimodal Computer Vision/LLM. Ảnh thân xe được đưa vào Gemini 2.5 Flash (vision input) để nhận diện dấu hiệu bất thường, phân loại defect trong phạm vi đã định nghĩa và trả structured output cho nhân viên QC review.

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Dùng Computer Vision hỗ trợ nhân viên QC  │
│ phát hiện và khoanh vùng các lỗi ngoại quan trên thân xe.   │
│                                                             │
│ Công ty thành viên: [x] VinFast [ ] Xanh SM [ ] Vinhomes   │
│                     [ ] Vinmec  [ ] Khác                    │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên Quality Control (QC) tại dây chuyền sản xuất.     │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│ 1. Xe đi đến khu vực kiểm tra ngoại quan                    │
│ → 2. Nhân viên QC quan sát các vùng thân/vỏ xe             │
│ → 3. Phát hiện và xác định vị trí lỗi                       │
│ → 4. Ghi nhận lỗi và chuyển xe sang bước xử lý phù hợp      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-3: kiểm tra toàn bộ bề mặt và phát hiện các lỗi      │
│ nhỏ (baseline giả định: khoảng 5 phút/xe).                  │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 2-3: mô hình multimodal phân tích ảnh từ camera,        │
│ nhận diện vùng/dấu hiệu nghi ngờ, phân loại defect và trả   │
│ structured output để nhân viên QC review.                                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian visual inspection từ baseline ~5 phút xuống  │
│ <2 phút/xe; Recall ≥95% trên các defect category đã được    │
│ định nghĩa; 100% defect do AI flag vẫn qua human review.    │
│                                                             │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

### Operational Boundary

Computer Vision chỉ đóng vai trò **inspection assistant**, không tự động quyết định một chiếc xe đạt hay không đạt tiêu chuẩn xuất xưởng.

AI được phép:

* Phát hiện vùng ảnh có dấu hiệu bất thường.
* Phân loại một số defect category đã được định nghĩa.
* Mô tả/khoanh vùng khu vực nghi ngờ trên ảnh trong structured output.
* Trả confidence score để nhân viên QC tham khảo.

AI **không được phép**:

* Tự động xác nhận xe `PASS`.
* Bỏ qua human review đối với lỗi có confidence thấp.
* Tự suy luận các lỗi cơ khí hoặc lỗi bên trong chỉ từ ảnh ngoại thất.
* Tự quyết định cho phép xe rời dây chuyền.

Quyết định QC cuối cùng luôn thuộc về nhân viên có thẩm quyền.

---

## QUICK PROBLEM CARD #2 — Xanh SM Vehicle Damage & Cleanliness Inspection

**Technical component:** Computer Vision; trong prototype của Lab có thể dùng vision/multimodal model để phân tích ảnh và trả kết quả có cấu trúc.

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Dùng Computer Vision hỗ trợ kiểm tra tình │
│ trạng ngoại thất và độ sạch của xe Xanh SM trước/sau ca.    │
│                                                             │
│ Công ty thành viên: [ ] VinFast [x] Xanh SM [ ] Vinhomes   │
│                     [ ] Vinmec  [ ] Khác                    │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên vận hành đội xe, tài xế và nhân viên kiểm tra xe. │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│ 1. Xe kết thúc ca/quay về điểm tập kết                      │
│ → 2. Nhân viên hoặc tài xế chụp/kiểm tra tình trạng xe      │
│ → 3. Quan sát để tìm vết xước, móp, hư hỏng/độ sạch         │
│ → 4. Ghi nhận và tạo yêu cầu xử lý nếu cần                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-3: phải kiểm tra nhiều vùng trên từng xe             │
│ (baseline giả định: khoảng 6 phút/xe).                      │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 2-3: Computer Vision phân tích bộ ảnh tiêu chuẩn của   │
│ xe, phát hiện vùng có dấu hiệu xước/móp/hư hỏng hoặc bẩn và │
│ highlight để nhân viên kiểm tra lại.                        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian kiểm tra ban đầu từ ~6 phút xuống <2 phút;   │
│ Recall ≥90% với nhóm damage đã định nghĩa; ≥95% trường hợp  │
│ AI flag được review trong quy trình kiểm tra.               │
│                                                             │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

### Operational Boundary

AI chỉ phát hiện **dấu hiệu nghi ngờ trên hình ảnh**, không tự kết luận nguyên nhân hay trách nhiệm của tài xế.

Hệ thống không được:

* Tự động quy trách nhiệm hư hỏng cho tài xế dựa trên ảnh.
* Tự động trừ lương/phạt hoặc tạo quyết định tài chính.
* Kết luận một xe an toàn để tiếp tục vận hành chỉ dựa trên ảnh ngoại thất.
* Bỏ qua kiểm tra con người đối với các damage nghiêm trọng.

Nếu ảnh bị tối, mờ, che khuất hoặc confidence thấp, hệ thống phải yêu cầu **retake ảnh hoặc human inspection**.

---

## QUICK PROBLEM CARD #3 — Vinpearl / VinWonders Crowd & Queue Monitoring

**Technical component:** Computer Vision + rule-based threshold để phát hiện/đếm người và kích hoạt cảnh báo.

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Dùng Computer Vision từ camera để ước     │
│ lượng lượng khách và phát hiện hàng chờ quá dài tại các     │
│ khu vực dịch vụ/trò chơi của Vinpearl/VinWonders.           │
│                                                             │
│ Công ty thành viên: [ ] VinFast [ ] Xanh SM [ ] Vinhomes   │
│                     [ ] Vinmec  [x] Khác: Vinpearl          │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Khách tham quan và nhân viên điều hành khu vui chơi.        │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│ 1. Camera/nhân viên quan sát khu vực                        │
│ → 2. Nhân viên nhận thấy hàng chờ bắt đầu đông             │
│ → 3. Báo cho quản lý/điều phối                             │
│ → 4. Điều thêm nhân viên hoặc điều tiết luồng khách         │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 1-2: phụ thuộc vào con người liên tục quan sát nhiều   │
│ khu vực cùng lúc và có thể phát hiện ùn tắc muộn.           │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 1-2: CV phát hiện/đếm người trong vùng hàng chờ,       │
│ ước lượng queue density và tự động cảnh báo khi vượt        │
│ threshold đã cấu hình.                                      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Person-counting accuracy ≥90% trong điều kiện camera chuẩn; │
│ cảnh báo queue overload trong <30 giây sau khi vượt         │
│ threshold; giảm ≥50% số lần ùn tắc chỉ được phát hiện       │
│ thủ công bởi nhân viên.                                     │
│                                                             │
│ Quick Architecture: [ ] No AI [x] Rule [ ] LLM [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

### Operational Boundary

Hệ thống chỉ sử dụng Computer Vision để **đếm người và phân tích mật độ/queue**, không cần xác định danh tính khách.

Hệ thống không được:

* Thực hiện face recognition để xác định khách hàng.
* Tạo hồ sơ hoặc theo dõi danh tính cá nhân.
* Tự quyết định đóng/mở khu trò chơi trong các tình huống liên quan đến an toàn.
* Thay thế nhân viên phụ trách quyết định điều tiết tại hiện trường.

Output của hệ thống chỉ là số lượng ước tính, trạng thái mật độ và cảnh báo vận hành.

---

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🤖 Stress-Test các Quick Problem Cards

Sau khi xây dựng ba Quick Problem Cards, tôi sử dụng AI như một thought-partner với vai trò CFO và Trưởng phòng Vận hành để phản biện liệu các bài toán có thực sự cần AI hay có thể giải quyết bằng rule-based software thông thường.

## Card #1 — VinFast Visual Quality Inspection

### Điểm yếu 1 — Không phải mọi lỗi đều nhìn thấy được bằng camera

Computer Vision chỉ phù hợp với defect có biểu hiện trực quan. Các lỗi cơ khí, phần mềm, pin hoặc lỗi nằm bên trong xe không thể được phát hiện đáng tin cậy từ ảnh ngoại thất.

**Điều chỉnh scope:** Chỉ giới hạn prototype vào **visual surface defects**, không tuyên bố hệ thống có khả năng kiểm tra toàn bộ chất lượng phương tiện.

### Điểm yếu 2 — Chất lượng camera ảnh hưởng trực tiếp đến model

Reflection trên lớp sơn, ánh sáng không đồng đều, màu xe, góc camera hoặc vật cản có thể tạo false positive/false negative.

**Điều chỉnh:** Chuẩn hóa camera angle, lighting và vùng inspection trước khi đánh giá model.

### Điểm yếu 3 — Tại sao không dùng rule-based image processing?

Các thuật toán threshold, edge detection hoặc template matching có thể xử lý một số lỗi đơn giản trong môi trường cực kỳ cố định.

Tuy nhiên, scratch/dent và các defect có hình dạng, kích thước, vị trí và texture thay đổi lớn. Vì vậy, một mô hình vision/multimodal có khả năng hiểu nội dung ảnh linh hoạt hơn có tiềm năng phù hợp hơn các rule pixel cố định trong prototype này.

**Kết luận sơ bộ:** Có AI Fit, nhưng cần giới hạn defect category và bắt buộc Human-in-the-loop.

---

## Card #2 — Xanh SM Vehicle Damage & Cleanliness Inspection

### Điểm yếu 1 — Ảnh trước và sau ca có thể không đồng nhất

Nếu góc chụp, ánh sáng hoặc khoảng cách thay đổi quá nhiều, hệ thống có thể coi reflection hoặc shadow là damage mới.

**Điều chỉnh:** Yêu cầu một protocol chụp ảnh cố định, ví dụ front/rear/left/right với hướng dẫn camera cụ thể.

### Điểm yếu 2 — AI không thể xác định ai gây ra damage

Ngay cả khi phát hiện một vết xước mới, hình ảnh không đủ bằng chứng để tự động kết luận trách nhiệm thuộc về một tài xế cụ thể.

**Điều chỉnh boundary:** Output chỉ là `potential_damage_detected`; mọi quyết định trách nhiệm phải do con người xác minh.

### Điểm yếu 3 — Rule-based có thể đủ cho cleanliness đơn giản

Nếu chỉ xác định xe đã được nhân viên tick "clean/not clean", không cần AI. CV chỉ mang lại giá trị nếu yêu cầu phát hiện trực quan trên số lượng xe lớn và giảm thời gian inspection thủ công.

**Kết luận sơ bộ:** Có tiềm năng AI Fit nhưng yêu cầu dữ liệu ảnh chuẩn hóa và Human Review.

---

## Card #3 — Vinpearl / VinWonders Crowd & Queue Monitoring

### Điểm yếu 1 — Có thể dùng cảm biến thay vì AI

Turnstile, infrared counter hoặc dữ liệu ticket có thể cho biết số lượt khách vào khu vực mà không cần Computer Vision.

Tuy nhiên, các nguồn này không nhất thiết phản ánh **độ dài và mật độ hàng chờ hiện tại tại một vùng cụ thể**.

### Điểm yếu 2 — Không cần Agent hoặc LLM

Bài toán không cần reasoning bằng ngôn ngữ hoặc autonomous agent.

Một pipeline đơn giản hơn:

Camera → Person Detection → Counting/Tracking → Threshold Rule → Alert

sẽ phù hợp và dễ kiểm soát hơn.

### Điểm yếu 3 — Occlusion khi khu vực quá đông

Khi nhiều người che khuất nhau, person detector có thể đếm thiếu.

**Điều chỉnh:** Cần đánh giá camera placement và có thể sử dụng crowd-density estimation nếu person detection không đủ ổn định.

**Kết luận sơ bộ:** **CV + rule-based alert** phù hợp hơn LLM hoặc Agent.

---

# 🗳️ Đề xuất cá nhân để đưa ra thảo luận nhóm

Trong ba Quick Problem Cards, tôi ưu tiên:

## **Card #1 — VinFast Visual Quality Inspection**

### Lý do lựa chọn

**1. Computer Vision trực tiếp giải quyết bottleneck**

Đầu vào là hình ảnh, tác vụ hiện tại là quan sát bằng mắt và output mong muốn là vị trí/category của defect. Do đó AI được áp dụng trực tiếp vào bản chất của bài toán thay vì cố gắng thêm AI vào một workflow không cần thiết.

**2. Có thể xây dựng pipeline kỹ thuật rõ ràng**

```text
Camera / Image
      ↓
Image Preprocessing
      ↓
Gemini 2.5 Flash (Vision / Multimodal)
      ↓
Defect Classification / Localization
      ↓
Confidence Score
      ↓
Human QC Review
      ↓
PASS / REWORK decision by QC staff
```

**3. Có Human-in-the-loop rõ ràng**

AI không được tự quyết định xe đạt chuẩn. Model chỉ đóng vai trò như một "second pair of eyes", còn QC staff vẫn chịu trách nhiệm quyết định cuối cùng.

**4. Có metric kỹ thuật đo được**

Có thể đánh giá bằng Precision, Recall, false-negative rate, inference time và inspection time thay vì chỉ đánh giá cảm tính.

**5. Có thể scope nhỏ cho prototype**

Prototype không cần xây dựng toàn bộ hệ thống kiểm định VinFast. Có thể giới hạn vào một số defect category cụ thể như:

* scratch;
* dent;
* paint/finish anomaly;
* missing hoặc visibly misaligned exterior component.

Điều này giúp bài toán đủ thực tế để Deep-Dive nhưng vẫn có scope phù hợp với một AI prototype.


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
