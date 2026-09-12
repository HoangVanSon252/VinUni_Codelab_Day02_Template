# Phase 1

| #   | Subsidiary        | Lens             | Mô tả ngắn bài toán                                                                                                                             |
| --- | ----------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **VinFast**       | Time-consuming   | Kỹ thuật viên xưởng 3S phải lật giở tài liệu kỹ thuật hàng trăm trang để tra cứu mã lỗi và sơ đồ tháo lắp chi tiết.                             |
| 2   | **Xanh SM / GSM** | AI-upgrade       | Đội ngũ CSKH phải đọc thủ công hàng ngàn phản hồi 1–3 sao để gắn nhãn lý do (xe mùi, lái ẩu, điều hòa yếu) phục vụ cải thiện chất lượng tài xế. |
| 3   | **Vinhomes**      | Repetitive       | Nhân viên trực tổng đài phải đọc tin nhắn phản ánh của cư dân để gõ lại địa chỉ căn hộ, loại hư hại và chọn đội kỹ thuật tiếp nhận.             |
| 4   | **Vinmec**        | Stakeholder Pain | Người bệnh phân vân không biết đăng ký khám chuyên khoa nào trên App, khiến tổng đài CSKH phải gọi lại điều hướng thủ công.                     |
| 5   | **Vinpearl**      | Time-consuming   | Lễ tân phải gõ tay từng trường thông tin cá nhân từ ảnh chụp CCCD/Hộ chiếu của từng đoàn khách vào phần mềm quản lý phòng.                      |

# Phase 2
### BƯỚC 1: TRIAGING & LỰA CHỌN TOP 3 (DOWN-SELECTION)

#### Ma trận Thẩm định Vận hành 5 Bài toán

| **STT** | **Đơn vị & Bài toán**                                                        | **Độ phức tạp dữ liệu**                                                                                   | **Khả năng giải bằng Rule/Code/Traditional AI**                                                                     | **Giá trị kinh tế & Tác động Vận hành**                                                                               | **Đánh giá Thẩm định** |
| ------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| **1**   | **VinFast**<br><br>  <br>  <br><br>Tra cứu lỗi 3S & sơ đồ kỹ thuật           | **Rất cao**<br><br>  <br>  <br><br>(PDF đa trang, sơ đồ mạch điện, mã DTC, ngôn ngữ kỹ thuật)             | **Rất thấp**<br><br>  <br>  <br><br>(Search từ khóa không hiểu ngữ cảnh mã lỗi và triệu chứng chéo)                 | **Chiến lược / Cực cao**<br><br>  <br>  <br><br>(Giảm MTTR tại xưởng, tối ưu chi phí bảo hành xe điện toàn cầu)       | **CHỌN (Top 1)**       |
| **2**   | **Xanh SM**<br><br>  <br>  <br><br>Gắn nhãn phản hồi 1–3 sao                 | **Cao**<br><br>  <br>  <br><br>(Văn bản phi cấu trúc, tiếng lóng, mỉa mai, đa nguyên nhân trong 1 câu)    | **Thấp**<br><br>  <br>  <br><br>(Rule-based bỏ sót sắc thái; BERT truyền thống thiếu linh hoạt khi thêm tag mới)    | **Cao**<br><br>  <br>  <br><br>(Kiểm soát chất lượng đội xe ~100k tài xế, tự động hóa toàn diện CSKH/QC)              | **CHỌN (Top 2)**       |
| **3**   | **Vinhomes**<br><br>  <br>  <br><br>Bóc tách tin nhắn báo sự cố cư dân       | **Thấp – Trung bình**<br><br>  <br>  <br><br>(Văn bản ngắn, chứa số căn hộ, lỗi hư hại thường gặp)        | **Cao**<br><br>  <br>  <br><br>(Giải quyết triệt để bằng **UI/UX Form chuẩn hóa** + Regex bóc tách số căn hộ)       | **Thấp – Trung bình**<br><br>  <br>  <br><br>(Chi phí nhân công thấp; lỗi phát sinh chủ yếu do thiết kế app lỏng lẻo) | **LOẠI BỎ (Drop)**     |
| **4**   | **Vinmec**<br><br>  <br>  <br><br>Điều hướng khám chuyên khoa từ triệu chứng | **Rất cao**<br><br>  <br>  <br><br>(Ngôn ngữ đời thường mô tả bệnh lý, rủi ro y khoa, thuật ngữ lâm sàng) | **Rất thấp**<br><br>  <br>  <br><br>(Cây quyết định tĩnh thất bại trước mô tả đa triệu chứng mơ hồ của người bệnh)  | **Cao**<br><br>  <br>  <br><br>(Tối ưu tỷ lệ lấp đầy phòng khám, giảm tải outbound call, nâng chuẩn JCI)              | **CHỌN (Top 3)**       |
| **5**   | **Vinpearl**<br><br>  <br>  <br><br>Nhập liệu CCCD / Hộ chiếu vào PMS        | **Rất thấp**<br><br>  <br>  <br><br>(Ảnh chụp giấy tờ tùy thân theo form chuẩn nhà nước/ICAO)             | **Rất cao**<br><br>  <br>  <br><br>(Giải quyết triệt để bằng **mô hình OCR/eKYC chuyên dụng** sẵn có của VinAI/FPT) | **Trung bình**<br><br>  <br>  <br><br>(Giá trị vận hành tốt nhưng dùng LLM là sai kiến trúc, lãng phí tài nguyên)     | **LOẠI BỎ (Drop)**     |

#### 2 Bài toán Loại bỏ (Drop / Postpone) & Lý do

- **Loại bỏ Bài toán 5 (Vinpearl - Nhập liệu CCCD/Hộ chiếu):**
    
      
    - _Lý do kỹ thuật:_ Đây là bài toán nhận dạng tài liệu có cấu trúc định sẵn (Structured Document Extraction). Công nghệ **OCR/eKYC truyền thống (Computer Vision + LayoutLM/CRNN)** đã hoàn thiện đạt độ chính xác >98% với chi phí compute chỉ bằng 1/100 so với LLM.
        
          
        
    - _Nguyên tắc kiến trúc:_ Dùng GenAI/LLM để đọc số CCCD/Passport là "lấy đại bác bắn chim sẻ", tiềm ẩn nguy cơ ảo giác (hallucination) làm sai lệch số định danh pháp lý và vi phạm nghiêm trọng chuẩn bảo mật dữ liệu PII. Bài toán này chuyển giao trực tiếp cho đội IT tích hợp API OCR chuyên dụng hiện hành của Tập đoàn.
        
          
        
- **Loại bỏ Bài toán 3 (Vinhomes - Đọc tin nhắn phản ánh sự cố cư dân):**
    
      
    - _Lý do vận hành:_ Đây là triệu chứng của **thiết kế Product/UX yếu kém**, không phải bài toán cần AI giải cứu. Cư dân phải gõ tự do là do tính năng Ticket trên App Vinhomes Resident thiếu bộ lọc trường dữ liệu bắt buộc (Dropdown chọn Tòa/Tầng/Căn hộ gắn theo Token User + Phân loại sự cố: Điện/Nước/Hạ tầng).
        
          
        
    - _Giải pháp thay thế:_ Tái cấu trúc Form gửi yêu cầu trên App di động giải quyết dứt điểm 90% việc routing tự động bằng Rule-based Backend. 10% trường hợp mô tả đặc biệt chỉ cần Regex kết hợp NER cơ bản, không xứng đáng để cấp ngân sách hạ tầng LLM.
        
          
        

### BƯỚC 2: 3 QUICK PROBLEM CARDS CHUẨN XÁC

#### PROBLEM CARD 01: VINFAST 3S TECHNICAL ASSISTANT

**1. Tên bài toán & Đơn vị:**

Trợ lý AI Hỗ trợ Chẩn đoán & Tra cứu Kỹ thuật Xưởng 3S (VinFast Aftersales & Service).

  

**2. Bối cảnh & Điểm nghẽn hiện trường:**

Kỹ thuật viên (KTV) tại xưởng 3S mất quá nhiều thời gian lật tìm tài liệu Service Manual (dài 300–800 trang/dòng xe) khi gặp mã lỗi phức tạp (DTC). Việc tra cứu chéo giữa sơ đồ mạch điện, danh sách giắc nối (pin-out) và bảng mã phụ tùng diễn ra rời rạc, dẫn đến xe chiếm cầu nâng lâu, phát sinh tình trạng "thay thử phụ tùng" gây lãng phí chi phí bảo hành.

  

**3. Workflow thủ công hiện tại (5 bước nghiệp vụ):**

  

- _Bước 1:_ KTV cắm thiết bị chẩn đoán chuyên dụng vào cổng OBD-II, ghi nhận danh sách mã lỗi DTC và dữ liệu Freeze Frame.
    
      
    
- _Bước 2:_ KTV mở máy tính nội bộ xưởng, truy cập cổng tài liệu kỹ thuật, gõ tìm mã lỗi trong hàng chục file PDF sơ đồ hướng dẫn.
    
      
    
- _Bước 3:_ Đọc sơ đồ mạch điện nhiều trang, dò tay vị trí giắc cắm, giá trị điện áp/điện trở chuẩn cần đo kiểm.
    
      
    
- _Bước 4:_ Cầm đồng hồ VOM ra xe đo thực tế; nếu kết quả bất thường, quay lại máy tính tìm mã Part Number của linh kiện trên hệ thống EPC (Electronic Parts Catalog).
    
      
    
- _Bước 5:_ Lập phiếu yêu cầu xuất kho phụ tùng hoặc ghi chú biên bản chẩn đoán vào phần mềm DMS.
    
      
    

**4. Metrics đo lường vận hành:**

  

- _Thời gian tra cứu tài liệu & phương án sửa chữa:_ **Baseline: 35 phút/ca** $\rightarrow$ **Target: < 3 phút/ca**.
    
      
    
- _Tỷ lệ chẩn đoán sai/thay thử phụ tùng (Parts Swapping Rate):_ **Baseline: 11.5%** $\rightarrow$ **Target: < 3%**.
    
      
    
- _Thời gian xe nằm xưởng chờ chẩn đoán (Turnaround Time - TAT):_ Giảm **20% tổng thời gian chiếm cầu nâng**.
    
      
    

**5. Architecture:**

`[ ] No AI` | `[ ] Rule` | `[ ] LLM` | `[X] Agent`

  

- _Căn cứ lựa chọn:_ Quy trình đòi hỏi khả năng **Tool-use đa bước**: Agent vừa phải thực hiện Multimodal RAG trên tài liệu PDF/sơ đồ vector, vừa phải gọi API nội bộ để kiểm tra mã lỗi từ OBD-II, đồng thời đối soát tồn kho phụ tùng thực tế trên SAP/ERP để trả ra quy trình sửa chữa hoàn chỉnh kèm mã phụ tùng chính xác.
    
      
    

#### PROBLEM CARD 02: XANH SM CSKH SENTIMENT & ROOT-CAUSE TRIAGE

**1. Tên bài toán & Đơn vị:**

Hệ thống Tự động Bóc tách Đa tầng & Gán nhãn Nguyên nhân Gốc Phản hồi Khách hàng (Xanh SM Operations & QC).

  

**2. Bối cảnh & Điểm nghẽn hiện trường:**

Mỗi ngày hệ thống ghi nhận từ 20,000 đến 35,000 lượt đánh giá 1–3 sao kèm nhận xét. Đội ngũ QA/QC phải tải dữ liệu ra file bảng tính và đọc thủ công từng phản hồi. Phản hồi thực tế chứa nhiều nội dung trộn lẫn (ví dụ: "xe êm nhưng tài xế đi lòng vòng, bật điều hòa nóng"), việc gán nhãn thủ công chậm chạp, mang tính chủ quan và làm trễ nhịp xử lý kỷ luật/đào tạo tài xế.

  

**3. Workflow thủ công hiện tại (4 bước nghiệp vụ):**

  

- _Bước 1:_ Cuối mỗi ca/ngày, chuyên viên QC trích xuất file Excel chứa toàn bộ review 1–3 sao từ cơ sở dữ liệu CSKH.
    
      
    
- _Bước 2:_ Nhân viên QC đọc từng dòng phản ánh, tự diễn giải ngữ cảnh (tiếng lóng, viết tắt, teencode, văn phong mỉa mai).
    
      
    
- _Bước 3:_ Tích chọn thủ công các cột phân loại nguyên nhân vi phạm (Mùi xe, Tác phong tài xế, Điều hòa, Lộ trình/Gian lận cước, Lỗi ứng dụng).
    
      
    
- _Bước 4:_ Tổng hợp số liệu theo tuần làm báo cáo PowerBI gửi Giám đốc Vận hành để chế tài hoặc xếp lịch đào tạo lại tài xế.
    
      
    

**4. Metrics đo lường vận hành:**

  

- _Độ trễ xử lý dữ liệu phản hồi (Feedback Triage Latency):_ **Baseline: 48 giờ (chờ gom batch)** $\rightarrow$ **Target: < 15 giây (Near real-time)**.
    
      
    
- _Chi phí nhân sự gán nhãn QC:_ **Baseline: ~200 triệu VNĐ/tháng (đội ngũ 12 nhân sự)** $\rightarrow$ **Target: Giảm 70%** (chỉ giữ 3 nhân sự làm nhiệm vụ Human-in-the-loop để audit mẫu).
    
      
    
- _Độ đồng nhất và chính xác nhãn phân loại (Labeling Consistency):_ **Baseline: 72% (chênh lệch giữa các nhân sự)** $\rightarrow$ **Target: > 94%**.
    
      
    

**5. Architecture:**

`[ ] No AI` | `[ ] Rule` | `[ ] LLM` | `[ ] Agent`

  

- _Căn cứ lựa chọn:_ Yêu cầu cốt lõi là **Structured Output / Multi-label Extraction** từ văn bản tiếng Việt tự nhiên phức tạp. Một pipeline LLM được tối ưu prompt/few-shot kết hợp schema JSON cứng là phương án chuẩn mực nhất: chi phí vận hành thấp, độ trễ nhỏ, không cần cơ chế tự hành (autonomous reasoning) hay tool calling phức tạp của Agent.
    
      
    

#### PROBLEM CARD 03: VINMEC CLINICAL SPECIALTY SMART TRIAGE

**1. Tên bài toán & Đơn vị:**

Trợ lý AI Sàng lọc Triệu chứng Ban đầu & Điều hướng Chuyên khoa Khám (Vinmec Healthcare System).

  

**2. Bối cảnh & Điểm nghẽn hiện trường:**

Khách hàng không có kiến thức y khoa thường gặp lúng túng khi tự đặt lịch trên MyVinmec (ví dụ: đau ngực lan ra sau lưng không rõ do Tim mạch, Tiêu hóa hay Cơ xương khớp). Hậu quả là tỷ lệ đặt sai chuyên khoa cao, bác sĩ chuyên khoa phải hủy phiếu chỉ định khám lại, còn tổng đài CSKH phải tốn hàng ngàn giờ gọi điện ra để hỏi lại triệu chứng và đổi khoa thủ công.

  

**3. Workflow thủ công hiện tại (5 bước nghiệp vụ):**

  

- _Bước 1:_ Khách hàng đặt lịch trên App, chọn đại một chuyên khoa và điền vài từ mô tả sơ sài vào ô ghi chú.
    
      
    
- _Bước 2:_ Điều dưỡng trực tổng đài rà soát danh sách lịch hẹn trên hệ thống HIS, phát hiện triệu chứng ghi chú không tương thích với chuyên khoa đã chọn.
    
      
    
- _Bước 3:_ Điều dưỡng thực hiện cuộc gọi Outbound (kéo dài 4–7 phút) để phỏng vấn sâu triệu chứng cơ năng, thời gian khởi phát và tiền sử bệnh nhân.
    
      
    
- _Bước 4:_ Căn cứ vào bảng phân loại phác đồ lâm sàng nội bộ, điều dưỡng xác định lại chuyên khoa chính xác và tra cứu khung giờ trống của bác sĩ phù hợp.
    
      
    
- _Bước 5:_ Điều chỉnh dữ liệu ca khám trên HIS, hệ thống gửi lại SMS/thông báo xác nhận lịch hẹn mới cho bệnh nhân.
    
      
    

**4. Metrics đo lường vận hành:**

  

- _Tỷ lệ đặt sai chuyên khoa (Misrouted Appointment Rate):_ **Baseline: 24% tổng ca đặt trực tuyến** $\rightarrow$ **Target: < 3.5%**.
    
      
    
- _Thời gian hoàn tất tiếp nhận & điều phối:_ **Baseline: 20 phút (tính cả thời gian chờ gọi lại)** $\rightarrow$ **Target: < 2 phút (hoàn tất tức thì khi đặt)**.
    
      
    
- _Khối lượng cuộc gọi xác minh của Điều dưỡng/CSKH:_ **Baseline: ~14,000 cuộc/tháng** $\rightarrow$ **Target: Giảm 85% cuộc gọi phi chuyên môn**.
    
      
    

**5. Architecture:**

`[ ] No AI` | `[ ] Rule` | `[ ] LLM` | `[X] Agent`

  

- _Căn cứ lựa chọn:_ Đây không đơn thuần là phân loại văn bản một chiều. Hệ thống đòi hỏi **hội thoại tương tác đa lượt (Multi-turn clarification)**: Đặt câu hỏi làm rõ theo giao thức y tế (Clinical Protocols), tuân thủ Guardrails an toàn người bệnh (phát hiện dấu hiệu cấp cứu chuyển hướng ngay 115), và **gọi API hệ thống HIS** để kiểm tra lịch trống khả dụng của bác sĩ chuyên khoa tương ứng theo thời gian thực.