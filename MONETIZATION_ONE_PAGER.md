# DAY 22 · AI-IN-ACTION · TRACK 1
# MONETIZATION ONE-PAGER

* **Tên / Nhóm:** Đàm Quang Trung (MSSV: 2A202602525) — Lớp K4 Track 1
* **Sản phẩm:** AutoResolve AI (Trợ lý CSKH ca đêm tự động cho SME Bán lẻ & E-commerce)
* **Value Metric đã chọn:** OUTCOME ($0,99 / resolution)
* **Kênh đã chọn:** Partner-Led (Haravan — đối tác chính 90 ngày đầu)
* **Ngày chốt số liệu:** 08/10/2026

* **Định vị (1 câu):** AutoResolve AI thay ca trực CSKH đêm của shop SME bán lẻ/e-commerce trên Haravan — tính $0,99 cho mỗi ticket được giải quyết xong. **Job** = 1 ticket mà khách xác nhận xong hoặc không hỏi lại sau 24h (`1_Cost_Job!B5`).

> *Mọi con số dưới đây đều truy xuất được về một ô trong file `day22_monetization_model.xlsx`. Số không có lý do = số ảo.*

---

## 1 · PRICING

### NGÂN SÁCH KHÁCH HÀNG
* **Tiền trả cho bạn đến từ ngân sách nào?**
  Tiền trả cho AutoResolve AI được rút từ **Ngân sách Vận hành CSKH (Customer Support Operations Budget)** và một phần ngân sách nhân sự (Headcount) trực đêm, **KHÔNG** rút từ ngân sách Phần mềm/IT.
* **Ai là người ký duyệt?**
  Người ký duyệt là **Trưởng phòng CSKH / Trưởng bộ phận Vận hành (Operations Lead)** hoặc **Chủ doanh nghiệp SME (Owner/Founder)**. Tiêu chí phê duyệt: Chi phí trả theo kết quả (~$203/tháng cho shop ~250 ticket) bằng khoảng 58% lương 1 nhân sự trực đêm (8–10 triệu ₫ ≈ $350/tháng) nhưng phủ 24/7, chỉ trả khi ticket được giải quyết, và giảm tỷ lệ mất đơn do khách chờ quá 5 phút.

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
| **Gross Margin (trước chia sẻ partner)** | **74,89%** | `2_Pricing!B21` |
| **Giá ròng sau 20% revenue share** | **$0,792 / job** | `2_Pricing!B57` |
| **Gross Margin sau revenue share** | **68,61%** (≥ 60%, vùng an toàn) | `2_Pricing!B59` |
| **Breakeven containment sau revenue share** | **77,41%** (trước chia sẻ: 72,68% — `2_Pricing!B33`) | `2_Pricing!B60` |
| **Containment hiện tại** | **82,00%** (ước tính từ bộ eval nội bộ 500 ca — đối chiếu lại ở pilot) | `1_Cost_Job!B10` |
| **Đệm an toàn** | **4,59 điểm %** (82% − 77,41%) | `2_Pricing!B61` |

### CÁCH NEO GIÁ
* **Neo theo nhân công (50–70%) — chỉ để đối chiếu, không phải điểm bán chính:** Lương trực đêm ≈ $350/tháng (8–10 triệu ₫; `2_Pricing!B14`). Shop điển hình ~250 ticket/tháng, ~205 được giải quyết → trả ≈ $203/tháng ≈ 58% lương 1 người, nhưng phủ 24/7. Trần theo nhân công 50–70% ≈ $0,70–0,98/job (`2_Pricing!B15–B16`); giá $0,99 nằm sát đỉnh vùng này → neo chính vẫn là giá trị giữ lại, không bán bằng "rẻ hơn lương".
* **Neo theo giá trị tạo ra (10–25%) — neo chính:** Giả định (sẽ kiểm chứng ở pilot) mỗi shop ~250 ticket/tháng giữ lại được ≈ $1.000 doanh thu đơn hàng ca đêm (`2_Pricing!B10`). Outcome chỉ tính 820/1.000 ticket thành công, tức ≈ $203/tháng = **20,3%** giá trị giữ lại, nằm trong khoảng 10–25% (trần giá trị `2_Pricing!B13` = $1,00/job).

### MÔ HÌNH GÃY KHI NÀO?
* Mô hình gãy khi **containment tụt xuống dưới 77,41%** (GM sau revenue share < 60%); **GM ròng < 50% khi containment < ~72,7%**. Ở Biến thể B mỗi ca escalate tốn $0,90. Ở containment 70%, GM ròng 43,7%; ở 60%, Cost/Job vọt lên $0,670 và GM ròng chỉ còn 15,4%. Đệm hiện tại chỉ 4,59 điểm %.
* Ngoài ra, nếu chi phí xử lý escalation tăng gấp đôi (≥ $18/giờ), Cost/Job lên ≈ $0,464 và GM ròng còn ≈ 41%.

---

## 2 · GO-TO-MARKET

### KÊNH PHÂN PHỐI — CHỌN ĐÚNG 1 CHO 90 NGÀY ĐẦU
* **Kênh phân phối chốt:** **Partner-Led** (đúng 1 kênh cho 90 ngày đầu).
* **Tên đối tác cụ thể:** **Haravan** (Haravan App Store). Pancake POS chỉ xét từ Tháng 4+.
* **Đã nói chuyện chưa:** **Chưa** — mới đăng ký tài khoản Developer Partner trên Haravan; chưa có buổi trao đổi với đội partner. Hẹn liên hệ trước **22/10/2026**.
* **Giá trị mang lại cho đối tác:** Tăng tỷ lệ giữ chân khách hàng (retention) của Haravan bằng cách giải quyết triệt để điểm đau thiếu nhân sự trực ca đêm của các chủ shop bán lẻ; chia sẻ **20% doanh thu (revenue share)** trên mỗi resolution cho nền tảng đối tác (đã tính vào mô hình: `2_Pricing!B56–B61`).

### BẰNG CHỨNG BẰNG SỐ CHO LỰA CHỌN KÊNH

| Chỉ số | Giá trị | Lấy từ đâu |
|---|---|---|
| **ARPU / tháng** | **$200 / tháng** (~250 ticket/shop × 82% × $0,99) | `4_Channel_Fit!B5` |
| **Ngân sách CAC / khách** | **$1.646,60 / khách** ($200 × GM ròng 68,61% × 12) | `4_Channel_Fit!B9` |
| **Số deal / AE / ngày** | **0,83 deal / ngày** (≤ 1 nên về số học chưa loại; kết luận dựa vào CAC bên dưới) | `4_Channel_Fit!B16` |
| **CAC thực tế ước tính** | **$32.000 / khách** | `4_Channel_Fit!B22` |
| **Lệch bao nhiêu lần** | **19,4 lần (Bất khả thi nuôi Sales)** | `4_Channel_Fit!B23` |

### PAIN MOMENT — BẮT BUỘC ĐỦ 3 PHẦN
* **Mấy giờ:** Đúng **23:00 – 02:00 đêm**.
* **Khách đang làm gì:** Chủ shop / Lead CSKH đang bị dồn ứ 30–50 tin nhắn hỏi đơn, check tồn và khiếu nại giao hàng mà nhân viên ca đêm đã nghỉ hoặc ngủ quên, nguy cơ bị bom đơn và đánh giá 1 sao.
* **Dùng app/kênh nào:** Đang mở **hộp thư hội thoại đa kênh của Haravan** (tên bề mặt chính xác cần xác minh trên trang developer Haravan).
* *Ý nghĩa:* Pain moment này tập trung vào nỗi sợ mất doanh thu và áp lực quá tải ban đêm, nơi khách hàng đang trực tiếp đối mặt với vấn đề mà không có giải pháp nhân sự thay thế.

### ĐIỂM NHÚNG
* **Vị trí tích hợp:** **App Extension / Webhook Plugin tích hợp trực tiếp ngay trong giao diện hộp thư hội thoại Haravan**.
* Chủ shop chỉ cần bật nút toggle *"Bật AutoResolve Ca Đêm"* ngay trên màn hình chat quen thuộc, không cần mở tab mới, không cần học workflow mới và không cần cài thêm phần mềm riêng biệt.

### 90-DAY PLAN

| Mục | Tháng 1 — Học | Tháng 2–3 — Đòn bẩy | Tháng 4+ — Mở rộng |
|---|---|---|---|
| **Kênh** | Partner-Led (Pilot kín 5 shop qua Haravan App Partner) | Partner-Led (Publish chính thức lên Haravan App Store) | Partner-Led: thêm Pancake POS, sau đó Sapo (chỉ khi Haravan đạt KPI) |
| **Mục tiêu số khách** | 5 shop SME pilot (vận hành tay, deep dive) | 30 shop SME trả phí qua App Marketplace | 100 shop SME tại Việt Nam |
| **Việc cụ thể** | Cài webhook thủ công, ngồi cùng 5 shop gán nhãn 500 ticket thật để tinh chỉnh prompt/RAG; đo attribution hàng ngày. | Hoàn thiện luồng One-Click Install + Auto Billing; chạy webinar co-marketing với Haravan 'Cứu doanh thu ca đêm'. | Tích hợp đồng bộ tồn kho thời gian thực với ERP/POS; bổ sung gói Hybrid SLA cho khách lớn >5.000 ticket/tháng. |
| **KPI đo được** | Containment rate ≥ 80%; 100% khiếu nại phản hồi trong 1h; 5/5 shop ký tiếp sau pilot. | 30 shop hoạt động (~6.000 resolution/tháng, MRR ≈ $6.000); Churn rate < 5%/tháng; Partner conversion rate > 12%. | 100 shop; MRR ≈ $20.000; GM sau revenue share duy trì ≥ 68%; NPS ≥ 55. |
| **Ai chịu trách nhiệm** | Đàm Quang Trung (Product Lead) | Đàm Quang Trung (Product) & Partnership Lead (đang tuyển, chốt trước 30/11/2026) | Team Core (Product Lead, Partnership Lead, Lead Support) |

---

## 3 · EVIDENCE PACK

| Tài sản | Đã có? | Nội dung 1 câu — hoặc việc cần làm | Ai · Deadline |
|---|---|---|---|
| **1. Eval Results** | **Rồi** | Bộ eval nội bộ 500 test cases cho containment rate 82% (số ước tính ban đầu; sẽ đối chiếu lại bằng dữ liệu thật ở pilot). | Đàm Quang Trung · Nghiệm thu 05/10/2026 (Bộ eval 500 test cases) |
| **2. Risk Checklist** | **Rồi** | Tài liệu cam kết bảo mật: AI chỉ dùng RAG trên dữ liệu shop cung cấp (không hallucinate chính sách); data KHÔNG bị dùng train model chung (API Zero Data Retention); nếu hệ thống ngưng hoạt động, dữ liệu và lịch sử chat lưu toàn vẹn trên database của khách. | Đàm Quang Trung · Hoàn thành 08/10/2026 |
| **3. Pilot Report** | **Chưa** | MỤC TIÊU (chưa có kết quả): pilot 4 tuần trên 5 shop SME (~1.250 ticket), đo containment (mục tiêu ≥ 80%), giờ trực đêm tiết kiệm và thời gian phản hồi đầu tiên. | Đàm Quang Trung · Deadline: 30/11/2026 (Sau khi kết thúc Tháng 1 Pilot) |

---

## BÀI TEST NGƯỜI LẠ
* [x] **Bạn bán gì, cho ai, tính tiền theo đơn vị nào?** $\rightarrow$ Bán trợ lý AI trực ca đêm giải quyết ticket cho shop SME, tính tiền theo Outcome ($0,99/resolution).
* [x] **Có lãi trên mỗi đơn vị không — con số nào chứng minh?** $\rightarrow$ Có lãi, Cost/Job $0,2486 so với giá bán $0,99: GM 74,89%, còn 68,61% sau khi chia 20% cho partner (vẫn vượt ngưỡng 60%).
* [x] **Tiếp cận khách qua đâu — và vì sao là kênh đó?** $\rightarrow$ Partner-Led cắm vào Haravan vì ngân sách CAC $1.647 không thể nuôi Direct Sales (CAC thực tế $32.000, lệch 19,4 lần).
* **Số câu người đọc phải hỏi lại:** **1 câu** *(đạt mục tiêu $\le$ 3)*.

*Đừng bán AI. Hãy bán kết quả.*
