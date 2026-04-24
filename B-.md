Đây là bản cải thiện **Version B** cho dự án **FINANCE-AGENT**, tập trung vào việc nâng cấp khả năng suy luận (Reasoning), tính minh bạch của dữ liệu tài chính và tối ưu hóa quy trình ra quyết định cho nhà đầu tư.

---

# Project FINANCE-AGENT (Version B): AI-Analyst for Intelligent Investment

## 5.1 Checkpoint 1 — Scope Review Gate (MVP Boundary)
Sản phẩm tập trung vào định vị: **"Cánh tay phải của nhà đầu tư - Chuyển hóa dữ liệu thô thành lợi thế cạnh tranh."**

| Phạm vi | Chi tiết tính năng | Need Mapping |
| :--- | :--- | :--- |
| **In-Scope** | 1. **Cross-Document Financial Reasoning:** Phân tích đối chiếu giữa Báo cáo tài chính, Báo cáo thường niên và Nghị quyết ĐHĐCĐ để tìm ra sự mâu thuẫn hoặc điểm sáng.<br>2. **Automated Valuation Models:** Tự động chạy các mô hình định giá cơ bản (DCF, P/E Forward) dựa trên dữ liệu trích xuất.<br>3. **Red Flag Detection:** Tự động nhận diện các dấu hiệu rủi ro kế toán hoặc dòng tiền yếu. | Cần cái nhìn đa chiều thay vì chỉ đọc số liệu rời rạc; Cần định giá nhanh để săn "kèo"; Cần bộ lọc rủi ro sớm. |
| **Out-of-Scope**| Robot tự động đặt lệnh (Auto-trading), Phân tích kỹ thuật đồ thị (Chart patterns), Tư vấn pháp luật đầu tư. | Giữ sự tập trung vào phân tích cơ bản (Fundamental Analysis). |
| **Non-Goals** | Hệ thống tin tức thời gian thực (News Feed) - Tránh làm người dùng bị xao nhãng bởi biến động ngắn hạn. | Tập trung vào giá trị nội tại của doanh nghiệp. |

---

## 5.2 Checkpoint 2 — Clarity Review Gate (PRD Skeleton)

### 6 Thành phần Standard:
1. **Context:** Nhà đầu tư cá nhân thường bị ngợp trong biển thông tin và dễ bỏ lỡ các chi tiết quan trọng nằm sâu trong thuyết minh báo cáo tài chính.
2. **Goals:** 100% các khuyến nghị phải đính kèm số trang và nguồn tài liệu gốc để kiểm chứng (Citation); Rút ngắn thời gian thẩm định một mã cổ phiếu từ 4 giờ xuống còn 15 phút.
3. **User Stories:** * "Tôi muốn Agent so sánh biên lợi nhuận gộp của doanh nghiệp này với trung bình ngành trong 3 năm gần nhất để đánh giá lợi thế cạnh tranh."
    * "Tôi muốn biết ban lãnh đạo có thực hiện đúng các cam kết về doanh thu trong nghị quyết năm ngoái hay không."
4. **User Flow:** Upload Files/Enter Ticker -> Agent Scans & Indexes -> **Financial Deep-Dive (Reasoning)** -> Valuation Output -> Interactive Q&A.
5. **Analytics:** Độ chính xác của dữ liệu trích xuất (Data Extraction Accuracy); Tỷ lệ người dùng sử dụng tính năng định giá.
6. **Constraints:** Báo cáo tài chính quét từ bản giấy (OCR lỗi); Các thuật ngữ kế toán đặc thù của từng quốc gia/ngành hàng.

### 3 Thành phần AI-Specific:
7. **Model Selection:** **Gemini 1.5 Pro** kết hợp với **Long Context Caching**.
    * *Lý do:* Khả năng xử lý lên đến 2 triệu tokens cho phép "nuốt trọn" toàn bộ lịch sử báo cáo của một doanh nghiệp trong nhiều năm để tìm ra xu hướng dài hạn.
    * *Trade-off:* Chi phí xử lý cao hơn bản Flash, cần tối ưu hóa bằng cách cache các dữ liệu tĩnh.
8. **Data Source:** Kết nối API với các đơn vị cung cấp dữ liệu tài chính sạch (Structured Data) và bộ thư viện báo cáo PDF (Unstructured Data) từ Ủy ban Chứng khoán.
9. **Fallback UX:** **"Traceable Source Mode"** - Khi đưa ra một con số, Agent sẽ cung cấp nút "View Source", khi click vào sẽ mở đúng trang PDF và highlight dòng chữ chứa dữ liệu đó để đảm bảo niềm tin tuyệt đối.

---

## 5.3 Final Checklist (Bản cải thiện)
- **Hypothesis:** "Nếu Agent cung cấp được bằng chứng (citation) cho mọi nhận định tài chính, sự tin tưởng của người dùng sẽ tăng 50% so với việc chỉ đưa ra kết luận."
- **PMF Scorecard:**
    * **Aha Moment:** Khi Agent phát hiện ra một chi tiết bất thường trong "Thuyết minh các khoản phải thu" mà mắt thường thường bỏ qua.
    * **Actionable Metric:** Số lượng câu hỏi chuyên sâu (Follow-up questions) mà người dùng đặt cho Agent sau khi nhận báo cáo tóm tắt.
    * **PMF Method:** Đo lường tỷ lệ "Lợi nhuận kỳ vọng" của danh mục do Agent gợi ý so với chỉ số VN-Index (Alpha tracking).

---
> **Ghi chú từ Jimala:** Version B này nâng cấp từ một công cụ "tóm tắt" thành một "chuyên viên phân tích thực thụ" nhờ khả năng đối chiếu dữ liệu (Cross-referencing) và tính minh bạch trong nguồn dẫn.
