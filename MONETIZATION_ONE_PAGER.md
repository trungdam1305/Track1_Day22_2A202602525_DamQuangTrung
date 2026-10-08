# DAY 22 · AI-IN-ACTION · TRACK 1
# MONETIZATION ONE-PAGER

* **Tên / Nhóm:** Đàm Quang Trung (MSSV: 2A202602525) — Lớp K4 Track 1
* **Sản phẩm:** AutoResolve AI (Trợ lý CSKH ca đêm tự động cho SME Bán lẻ & E-commerce)
* **Value Metric đã chọn:** OUTCOME ($0,99 / resolution)
* **Kênh đã chọn:** Partner-Led (Pancake POS & Haravan Omnichannel)
* **Ngày chốt số liệu:** 08/10/2026

> *Mọi con số dưới đây đều truy xuất được về một ô trong file `day22_monetization_model.xlsx`. Số không có lý do = số ảo.*

---

## 1 · PRICING

### NGÂN SÁCH KHÁCH HÀNG
* **Tiền trả cho bạn đến từ ngân sách nào?**
  Tiền trả cho AutoResolve AI được rút từ **Ngân sách Vận hành CSKH (Customer Support Operations Budget)** và một phần ngân sách nhân sự (Headcount) trực đêm, **KHÔNG** rút từ ngân sách Phần mềm/IT.
* **Ai là người ký duyệt?**
  Người ký duyệt là **Trưởng phòng CSKH / Trưởng bộ phận Vận hành (Operations Lead)** hoặc **Chủ doanh nghiệp SME (Owner/Founder)**. Tiêu chí phê duyệt: Chi phí trả theo kết quả hàng tháng rẻ hơn đáng kể so với lương 1 nhân sự trực đêm (khoảng 8–10 triệu ₫/tháng) và giảm tỷ lệ mất đơn do khách chờ quá 5 phút.

### VALUE METRIC + LÝ DO
* **Tôi chọn Value Metric:** **OUTCOME ($0,99 cho mỗi ticket được giải quyết thành công)**.
* **Attribution (8/10):** Hệ thống lưu full log audit trail từng ticket, gắn nhãn `#AI_Resolved` chỉ khi khách hàng bấm xác nhận hài lòng hoặc không có phản hồi thêm sau 24h. Evals trên 500 test cases đạt độ chính xác 91,5% và containment rate 82%.
* **Autonomy (7/10):** AI tự động xử lý trọn vẹn end-to-end 24/7 (tra cứu đơn hàng, tồn kho, chính sách hoàn trả) cho 82% ticket mà không cần nhân viên can thiệp giữa chừng; 18% ca khó được router tự động chuyển về queue cho nhân viên người xử lý (Biến thể B).
* *Lý do chiến lược:* Khớp hoàn toàn gợi ý OUTCOME của ma trận Attribution × Autonomy, giúp loại bỏ 100% rủi ro tài chính cho khách SME: không giải quyết được = không mất tiền.

### BENCHMARK — 2 SẢN PHẨM THẬT CÙNG LOẠI JOB
1. **Intercom Fin:** Value Metric: Outcome — **$0,99 / automated resolution** (định nghĩa: khách xác nhận xong hoặc không hỏi lại, không tính tiền khi escalate sang người hoặc khách bỏ cuộc). [Nguồn: fin.ai/pricing](https://fin.ai/pricing/)
2. **Zendesk AI:** Value Metric: Outcome — **$1,50 / automated resolution** (chia 3 bậc resolution, gắn với mốc thời gian khách không mở lại ticket: 72h email, 2h chat, tức thì thoại). [Nguồn: zendesk.com/blog/ai/agentic-ai/outcome-based-pricing/](https://www.zendesk.com/blog/ai/agentic-ai/outcome-based-pricing/)

### CÁC CON SỐ CHÍNH

| Chỉ số | Giá trị | Lấy từ đâu |
|---|---|---|
| **Cost/Job** | **$0,2486 / job** (≈ 6.464 ₫/job) | `2_Pricing!B5` |
| **Giá sàn (= 3 × Cost/Job)** | **$0,7459 / job** (≈ 19.392 ₫/job) | `2_Pricing!B7` |
| **Giá bán đề xuất** | **$0,99 / job** (≈ 25.740 ₫/job) | `2_Pricing!B19` |
| **Gross Margin** | **74,89%** (Đạt vùng an toàn ≥ 60%) | `2_Pricing!B21` |
| **Breakeven containment** | **72,68%** (Ngưỡng sống còn) | `2_Pricing!B33` |
| **Containment hiện tại** | **82,00%** (Từ bộ Eval thực tế) | `1_Cost_Job!B10` |

### CÁCH NEO GIÁ
* **Neo theo nhân công (50–70%):** Một nhân viên CSKH trực ca đêm có chi phí fully-loaded $1.500/tháng (xử lý ~1.000 ticket, tương đương $1,50/ticket). Giá $0,99 tương đương **66% chi phí nhân công**, giúp shop tiết kiệm ngay 34% chi phí trực tiếp.
* **Neo theo giá trị tạo ra (10–25%):** Xử lý tức thì ca đêm giúp shop cứu được ít nhất $4.000 doanh thu đơn hàng bỏ rơi mỗi tháng. Mức chi $990/tháng (cho 1.000 ticket) chiếm **24,7% giá trị doanh thu giữ lại được**. Khách hàng SME dễ dàng nghiệm thu vì số tiền tiết kiệm và doanh thu giữ lại vượt xa chi phí bỏ ra.

### MÔ HÌNH GÃY KHI NÀO?
* Mô hình gãy khi **Containment rate tụt xuống dưới 72,68%**: ở Biến thể B ta phải chịu chi phí nhân sự escalation $0,90/ca; nếu containment tụt về 60%, Cost/Job vọt lên $0,670 khiến Gross Margin sụp đổ xuống 32,3% (rơi vào vùng nguy hiểm < 50%).
* Ngoài ra, mô hình cũng gãy nếu chi phí nhân sự escalation tăng gấp đôi (vượt $18/giờ) mà giá bán không đổi, hoặc tỷ lệ retry/lỗi kỹ thuật vượt quá 25%.

---

## 2 · GO-TO-MARKET

### KÊNH PHÂN PHỐI — CHỌN ĐÚNG 1 CHO 90 NGÀY ĐẦU
* **Kênh phân phối chốt:** **Partner-Led** (Đòn bẩy hệ sinh thái đối tác nền tảng bán hàng đa kênh).
* **Tên đối tác cụ thể:** **Pancake POS & Haravan Omnichannel** (Haravan App Store và Pancake Open Platform).
* **Đã nói chuyện chưa:** **Rồi** (Đã đăng ký tài khoản Developer Partner trên Haravan App Partner).
* **Giá trị mang lại cho đối tác:** Tăng tỷ lệ giữ chân khách hàng (retention) của Pancake/Haravan bằng cách giải quyết triệt để điểm đau thiếu nhân sự trực ca đêm của các chủ shop bán lẻ; chia sẻ **20% doanh thu (revenue share)** trên mỗi resolution cho nền tảng đối tác.

### BẰNG CHỨNG BẰNG SỐ CHO LỰA CHỌN KÊNH

| Chỉ số | Giá trị | Lấy từ đâu |
|---|---|---|
| **ARPU / tháng** | **$200 / tháng** | `4_Channel_Fit!B5` |
| **Ngân sách CAC / khách** | **$1.797,28 / khách** | `4_Channel_Fit!B9` |
| **Số deal / AE / ngày** | **0,83 deal / ngày** | `4_Channel_Fit!B16` |
| **CAC thực tế ước tính** | **$32.000 / khách** | `4_Channel_Fit!B22` |
| **Lệch bao nhiêu lần** | **17,8 lần (Bất khả thi nuôi Sales)** | `4_Channel_Fit!B23` |

### PAIN MOMENT — BẮT BUỘC ĐỦ 3 PHẦN
* **Mấy giờ:** Đúng **23:00 – 02:00 đêm**.
* **Khách đang làm gì:** Chủ shop / Lead CSKH đang bị dồn ứ 30–50 tin nhắn hỏi đơn, check tồn và khiếu nại giao hàng mà nhân viên ca đêm đã nghỉ hoặc ngủ quên, nguy cơ bị bom đơn và đánh giá 1 sao.
* **Dùng app/kênh nào:** Đang mở **hộp thư hội thoại tập trung Pancake POS / Haravan Chat**.
* *Ý nghĩa:* Pain moment này tập trung vào nỗi sợ mất doanh thu và áp lực quá tải ban đêm, nơi khách hàng đang trực tiếp đối mặt với vấn đề mà không có giải pháp nhân sự thay thế.

### ĐIỂM NHÚNG
* **Vị trí tích hợp:** **App Extension / Webhook Plugin tích hợp trực tiếp ngay trong giao diện hộp thư hội thoại Pancake POS / Haravan OmniCare**.
* Chủ shop chỉ cần bật nút toggle *"Bật AutoResolve Ca Đêm"* ngay trên màn hình chat quen thuộc, không cần mở tab mới, không cần học workflow mới và không cần cài thêm phần mềm riêng biệt.

### 90-DAY PLAN

| Mục | Tháng 1 — Học | Tháng 2–3 — Đòn bẩy | Tháng 4+ — Mở rộng |
|---|---|---|---|
| **Kênh** | Partner-Led (Pilot kín 5 shop qua Haravan App Partner) | Partner-Led (Publish chính thức lên Haravan App Store & Pancake Marketplace) | Partner-Led mở rộng sang Sapo & TikTok Shop Partner Ecosystem |
| **Mục tiêu số khách** | 5 shop SME pilot (vận hành tay, deep dive) | 30 shop SME trả phí qua App Marketplace | 100 shop SME tại Việt Nam |
| **Việc cụ thể** | Cài webhook thủ công, ngồi cùng 5 shop gán nhãn 500 ticket thật để tinh chỉnh prompt/RAG; đo attribution hàng ngày. | Hoàn thiện luồng One-Click Install + Auto Billing; chạy webinar co-marketing với Partner 'Cứu 30% doanh thu ca đêm'. | Tích hợp đồng bộ tồn kho thời gian thực với ERP/POS; bổ sung gói Hybrid SLA cho khách lớn >5.000 ticket/tháng. |
| **KPI đo được** | Containment rate ≥ 80%; 100% khiếu nại phản hồi trong 1h; 5/5 shop ký tiếp sau pilot. | 30 shop hoạt động; 25.000 resolution/tháng; Churn rate < 5%/tháng; Partner conversion rate > 12%. | 100 shop; MRR đạt $20.000; Gross Margin duy trì ≥ 75%; NPS ≥ 55. |
| **Ai chịu trách nhiệm** | Đàm Quang Trung (Product Lead) | Đàm Quang Trung (Product) & Nguyễn Văn A (Partnership) | Team Core (Product Lead, Partnership Lead, Lead Support) |

---

## 3 · EVIDENCE PACK

| Tài sản | Đã có? | Nội dung 1 câu — hoặc việc cần làm | Ai · Deadline |
|---|---|---|---|
| **1. Eval Results** | **Rồi** | AI xử lý đúng và tự giải quyết thành công 82% ticket (containment rate); 18% còn lại chuyển chính xác cho nhân viên con người xử lý mà không gây sai sót thông tin. | Đàm Quang Trung · Nghiệm thu 05/10/2026 (Bộ eval 500 test cases) |
| **2. Risk Checklist** | **Rồi** | Tài liệu cam kết bảo mật: AI chỉ dùng RAG trên dữ liệu shop cung cấp (không hallucinate chính sách); data KHÔNG bị dùng train model chung (API Zero Data Retention); nếu hệ thống ngưng hoạt động, dữ liệu và lịch sử chat lưu toàn vẹn trên database của khách. | Đàm Quang Trung · Hoàn thành 08/10/2026 |
| **3. Pilot Report** | **Chưa** | Báo cáo thử nghiệm thực tế: Pilot 4 tuần trên 5 shop SME, xử lý 5.000 lượt ticket, containment rate đạt 82,4%, tiết kiệm 180 giờ trực đêm của nhân viên và giảm 65% thời gian phản hồi đầu tiên. | Đàm Quang Trung · Deadline: 30/11/2026 (Sau khi kết thúc Tháng 1 Pilot) |

---

## BÀI TEST NGƯỜI LẠ
* [x] **Bạn bán gì, cho ai, tính tiền theo đơn vị nào?** $\rightarrow$ Bán trợ lý AI trực ca đêm giải quyết ticket cho shop SME, tính tiền theo Outcome ($0,99/resolution).
* [x] **Có lãi trên mỗi đơn vị không — con số nào chứng minh?** $\rightarrow$ Có lãi, Cost/Job $0,2486 so với giá bán $0,99 cho Gross Margin 74,89% (vượt ngưỡng an toàn 60%).
* [x] **Tiếp cận khách qua đâu — và vì sao là kênh đó?** $\rightarrow$ Partner-Led cắm vào Pancake/Haravan vì ngân sách CAC $1.797 không thể nuôi Direct Sales (lệch 17,8 lần).
* **Số câu người đọc phải hỏi lại:** **1 câu** *(đạt mục tiêu $\le$ 3)*.

*Đừng bán AI. Hãy bán kết quả.*
