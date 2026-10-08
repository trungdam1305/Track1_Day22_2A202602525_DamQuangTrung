# Lab 22 — AI Monetization & Go-To-Market (GTM) Strategy

* **Học viên:** Đàm Quang Trung
* **MSSV / MHV:** 2A202602525
* **Lớp:** K4 Track 1 — AI-in-Action
* **Sản phẩm:** AutoResolve AI — Trợ lý AI giải quyết Ticket CSKH ca đêm tự động cho SME Bán lẻ & E-commerce
* **Ngày thực hiện & kiểm tra giá:** 08/10/2026

---

## 1. Tuyên ngôn định vị & 3 Câu hỏi cốt lõi

> *"Build is no longer the bottleneck. Distribution is. Sản phẩm chạy được là bài toán kỹ thuật. Bán được là bài toán sinh tồn."*

Lab thực chiến 120 phút trả lời trọn vẹn 3 câu hỏi sinh tử trước khách hàng doanh nghiệp và nhà đầu tư:
1. **Ai trả tiền & Từ ngân sách nào?** $\rightarrow$ Trưởng phòng Vận hành CSKH / Chủ shop SME trả từ **Ngân sách Vận hành CSKH (Operations Budget)** và Ngân sách nhân sự trực đêm, cạnh tranh trực tiếp với lương nhân sự ca đêm ($1.500/tháng), không đụng vào ngân sách IT/phần mềm.
2. **Trả theo đơn vị gì (Value Metric)?** $\rightarrow$ **OUTCOME ($0,99 / resolution)** — Chỉ tính tiền khi ticket được giải quyết thành công (khách xác nhận hoặc không hỏi lại sau 24h). Attribution đạt 8/10, Autonomy đạt 7/10. Khách hàng SME chịu 0% rủi ro tài chính.
3. **Tiếp cận qua kênh nào & Nhúng vào đâu?** $\rightarrow$ **Partner-Led** thông qua hệ sinh thái ứng dụng của **Pancake POS & Haravan Omnichannel**. Điểm nhúng là Webhook/App Extension ngay trong hộp thư chat ca đêm (23:00 – 02:00 sáng).

---

## 2. Bảng chỉ số tài chính sống còn (Executive Summary)

Mọi con số đều truy xuất trực tiếp từ mô hình tài chính tại [day22_monetization_model.xlsx](day22_monetization_model.xlsx):

| Chỉ số | Giá trị | Đơn vị | Nguồn ô Excel | Ý nghĩa kinh tế |
|---|---|---|---|---|
| **Cost/Job** | **$0,2486** (≈ 6.464 ₫) | $/job | `2_Pricing!B5` | Tổng chi phí đủ 5 thành phần (API + Infra + HITL + Retry + QA) chia cho **820 job hoàn thành** (Biến thể B: ta chịu escalation). |
| **Giá sàn (3×)** | **$0,7459** (≈ 19.392 ₫) | $/job | `2_Pricing!B7` | Ngưỡng an toàn tối thiểu ($3 \times \text{Cost/Job}$) để cover R&D, hạ tầng và sai số vận hành. |
| **Giá bán đề xuất** | **$0,99** (≈ 25.740 ₫) | $/job | `2_Pricing!B19` | Định giá cạnh tranh, ngang bằng Intercom Fin ($0,99) và rẻ hơn Zendesk ($1,50). |
| **Gross Margin** | **74,89%** | % | `2_Pricing!B21` | Vượt xa benchmark an toàn (≥ 60%), cao hơn trung bình AI-native 2026 (52–53%). |
| **Breakeven Containment** | **72,68%** | % | `2_Pricing!B33` | Ngưỡng sống còn: Containment rate tối thiểu để giữ GM $\ge 60\%$. Dưới 60% GM tụt về 32,3%. |
| **Containment hiện tại** | **82,00%** | % | `1_Cost_Job!B10` | Đo từ bộ Eval 500 test cases $\rightarrow$ Vượt ngưỡng hòa vốn **+9,32%**. |
| **Ngân sách CAC tối đa** | **$1.797,28** | $/khách | `4_Channel_Fit!B9` | $\text{ARPU } (\$200) \times \text{GM } (74,89\%) \times 12 \text{ tháng payback (SMB)}$. |
| **CAC Sales-Led thực tế** | **$32.000** | $/khách | `4_Channel_Fit!B22` | Cost per opportunity (\$8.000) / Win rate (25%) theo ICONIQ 2026. Lệch **17,8 lần** $\rightarrow$ Sales-Led bất khả thi. |

---

## 3. Tóm tắt 4 Khối Chiến Lược

### Khối 1 — Ngân sách & Value Metric
* **Ngân sách:** Ngân sách Vận hành CSKH / Nhân sự ca đêm. Trưởng phòng CSKH / Chủ shop ký duyệt vì đơn giá mỗi ticket giải quyết rẻ hơn 34% so với lương nhân viên trực đêm.
* **Ma trận Attribution × Autonomy:**
  - Attribution = 8/10 (Log trace đầy đủ, phân biệt rạch ròi qua tag `#AI_Resolved`, điều kiện không mở lại sau 24h).
  - Autonomy = 7/10 (AI tự hoàn thành trọn vẹn 82% ticket 24/7, tự động chuyển tiếp 18% ca khó cho người).
  - Khớp gợi ý **OUTCOME**. Đơn vị tính tiền: **$0,99 / resolution**.
* **Benchmark:**
  1. *Intercom Fin:* $0,99 / resolution ([fin.ai/pricing](https://fin.ai/pricing/)).
  2. *Zendesk AI:* $1,50 / resolution ([zendesk.com/blog/ai/agentic-ai/outcome-based-pricing/](https://www.zendesk.com/blog/ai/agentic-ai/outcome-based-pricing/)).

### Khối 2 — Chi phí Cost/Job & Cơ cấu Giá
* **Đủ 5 thành phần chi phí (cho 1.000 job thử, 820 hoàn thành):**
  1. *API LLM:* Claude Haiku 4.5 ($1.00 input, $5.00 output, $1.25 cache write, $0.10 cache read). 6 lượt đối thoại, 3.000 token cache được, 1.000 token fresh, 300 token output. Áp dụng Prompt Caching cắt giảm **38,64%** chi phí LLM, đạt **$0,02025 / job** ($20,25/tháng).
  2. *Infra:* Vector DB, embedding, redis logging = **$0,00500 / job** ($5,00/tháng).
  3. *Retry:* 8% tỷ lệ chạy lại do timeout/lỗi API = **$0,00162 / job** ($1,62/tháng).
  4. *HITL (Biến thể B — ta chịu escalation):* QA nội bộ 5% ca ($15/tháng) + Escalation 180 ca $\times$ 6 phút $\times$ $9/giờ ($162/tháng) = **$177,00 / tháng**.
  5. *Overhead:* $0 (COGS thuần).
* **Mẫu số chuẩn:** Chia cho **820 job hoàn thành** $\rightarrow$ $\text{Cost/Job} = \$203,87 / 820 = \mathbf{\$0,2486 / job}$.
* **Neo giá:** Neo theo chi phí nhân sự ($0,99 = 66\%$ chi phí trực đêm $1,50/ticket) và neo theo giá trị giữ chân khách ($24,7\%$ doanh thu cứu được từ đơn hàng bỏ rơi ban đêm).

### Khối 3 — Kênh GTM & Phân tích Khả thi (Channel Affordability Test)
* **Toán học chứng minh Direct Sales thất bại:**
  - ARPU $200/tháng $\rightarrow$ Ngân sách CAC cho phép là **$1.797,28**.
  - Chi phí nuôi Inside Sales: Với Cost per Opportunity $8.000 và Win rate 25%, CAC thực tế là **$32.000/khách** (gấp **17,8 lần** ngân sách). Direct Sales là tự sát tài chính.
* **Kênh duy nhất trong 90 ngày:** **Partner-Led**.
  - Đối tác: **Pancake POS & Haravan Omnichannel** (Haravan App Store & Pancake Open Platform).
  - Giá trị mang lại: Giữ chân khách hàng cho partner, chia sẻ 20% revenue share trên mỗi resolution.
* **Pain Moment sắc nét:** **23:00 – 02:00 đêm** + Chủ shop bị dồn ứ 30–50 tin nhắn hỏi đơn, nhân viên ca đêm vắng mặt, nguy cơ mất đơn hàng + Mở hộp thư **Pancake POS / Haravan Chat**.
* **Điểm nhúng:** App Extension / Webhook ngay trên giao diện hộp thư Pancake / Haravan.

### Khối 4 — Evidence Pack & Kế hoạch 90 ngày
* **Evidence Pack 3 tài sản:**
  1. *Eval Results:* AI giải quyết đúng 82% ticket (containment rate); 18% escalate an toàn. (Đã có).
  2. *Risk Checklist:* Cam kết bảo mật, không dùng data để train model (API Zero Data Retention), RAG chống hallucination, data toàn vẹn trong DB khách. (Đã có).
  3. *Pilot Report:* Báo cáo kết quả thử nghiệm 4 tuần trên 5 shop SME, xử lý 5.000 ticket, tiết kiệm 180h công. (Deadline: 30/11/2026).
* **Kế hoạch 90 ngày:**
  - *Tháng 1 (Học):* Pilot kín 5 shop SME, gán nhãn 500 ticket, đo attribution hàng ngày. (Lead: Đàm Quang Trung).
  - *Tháng 2–3 (Đòn bẩy):* Publish Haravan/Pancake App Store, co-marketing webinar, đạt 30 shop trả phí.
  - *Tháng 4+ (Mở rộng):* Mở rộng 100 shop, tích hợp Sapo & TikTok Shop, gói Hybrid SLA cho khách lớn.

---

## 4. Nhật ký phản biện mô hình (§4.7 Prompt Runs)

Đã thực hiện đầy đủ 3 prompt phản biện chuyên sâu (xem chi tiết tại [AI_CHALLENGER_LOG.md](AI_CHALLENGER_LOG.md)):
1. **Prompt 4.7.1 — Cost/Job Stress Test (CFO & Skeptical Infra Engineer):**
   - Xác nhận mẫu số 820 hoàn thành (không chia 1.000).
   - Kiểm chứng công thức hòa vốn $R \ge 72,68\%$.
   - Nhận diện biến sinh tử: Chi phí escalation HITL ($e$) và Containment rate ($R$).
   - *Quyết định:* **ACCEPT** giữ nguyên mẫu số và đưa ngưỡng 72,68% vào One-Pager.
2. **Prompt 4.7.2 — Value Metric Challenger:**
   - Phản biện kịch bản khách bỏ cuộc 24h hoặc đối thủ spam bot.
   - *Quyết định:* **ACCEPT** bổ sung Sentiment Filter và quy chế 1-click Dispute vào Risk Checklist.
3. **Prompt 4.7.3 — Channel Reality Check:**
   - Chứng minh số học: CAC Sales-Led lệch 17,8 lần so với ngân sách CAC.
   - Thiết lập bài test giả định 14 ngày trên 10 chủ shop để kiểm chứng sức hút trước khi build.
   - *Quyết định:* **ACCEPT** tập trung 100% nguồn lực cho Partner-Led.

---

## 5. Danh mục File Bàn Giao trong Repository

| Tên file | Mô tả & Trạng thái |
|---|---|
| [day22_monetization_model.xlsx](day22_monetization_model.xlsx) | Workbook 7 tab (5 tab làm việc + 2 tab tham chiếu). Điền đầy đủ 100% ô vàng, không ô trống vô lý. Đèn xanh toàn bộ các chỉ số kiểm tra. |
| [day22_one_pager_template.docx](day22_one_pager_template.docx) | Bản khung nộp bài Monetization One-Pager định dạng Word chuẩn, đã điền đầy đủ 3 khối, 4 bảng số liệu, và bài test người lạ. |
| [MONETIZATION_ONE_PAGER.md](MONETIZATION_ONE_PAGER.md) | Phiên bản Markdown của One-Pager, trình bày trực quan, truy vết 1:1 với file Excel. |
| [AI_CHALLENGER_LOG.md](AI_CHALLENGER_LOG.md) | Nhật ký chi tiết chạy 3 prompt phản biện chuyên sâu (§4.7) kèm phân tích số học và quyết định Accept/Reject. |

---

## 6. Bảng Kiểm Tra Cuối Cùng (Final Checklist §5.8)

- [x] **1. Tab 1** — Đủ 5 thành phần chi phí, không ô nào trống vô lý.
- [x] **2. Tab 1** — Mẫu số là **JOB HOÀN THÀNH** (820), không phải job thử (1.000).
- [x] **3. Tab 2** — Giá bán đề xuất ($0,99) $\ge 3 \times \text{Cost/Job}$ ($0,7459), Gross Margin = 74,89% $\ge 60\%$.
- [x] **4. Tab 2** — Breakeven containment đã tính (72,68%), đã so với eval hiện tại (82,00%).
- [x] **5. Tab 3** — Value Metric chốt (OUTCOME) + Decision Note 3 câu + 2 benchmark thật có link (Intercom, Zendesk).
- [x] **6. Tab 4** — Ngân sách CAC ($1.797,28), deal/AE/ngày (0,83), 1 kênh duy nhất (Partner-Led).
- [x] **7. Tab 5** — 90-day plan có số và tên người chịu trách nhiệm; Evidence Pack có deadline cụ thể.
- [x] **8. Tab 6** — Ghi rõ ngày kiểm tra giá API (`08/10/2026`) tại ô `B3`.
- [x] **9. One-Pager** — Đủ 3 khối, mọi số liệu khớp 100% với file Excel.
- [x] **10. Prompt Phản Biện** — Đã chạy 3 prompt ở §4.7 và ghi lại accept/reject chi tiết trong `AI_CHALLENGER_LOG.md`.

*Người thực hiện: Đàm Quang Trung — Ngày hoàn thành: 08/10/2026.*
