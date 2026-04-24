# Project FINANCE-AGENT: MVP Boundary & PRD Skeleton

## 5.1 Checkpoint 1 — Scope Review Gate

### MVP Boundary Sheet
| Phạm vi | Chi tiết tính năng | Need Mapping |
| :--- | :--- | :--- |
| **In-Scope** | 1. Trích xuất dữ liệu tự động từ Báo cáo tài chính (PDF/Excel) bằng RAG.<br>2. Phân tích các chỉ số tài chính cốt lõi (P/E, ROE, Debt/Equity).<br>3. Chấm điểm sức khỏe doanh nghiệp và đưa ra khuyến nghị Mua/Bán/Giữ. | Tiết kiệm thời gian đọc báo cáo hàng trăm trang; Cần dữ liệu chuẩn xác; Cần hỗ trợ ra quyết định khách quan. |
| **Out-of-Scope**| Giao dịch trực tiếp qua sàn (Trading), Quản lý danh mục tài sản thực (Portfolio Management), Dự báo giá cổ phiếu theo thời gian thực (Real-time technical analysis). | Tập trung vào khả năng đọc hiểu và tư duy logic của AI Agent thay vì hạ tầng tài chính. |
| **Non-Goals** | Phân tích tâm lý thị trường từ mạng xã hội (Social Sentiment) - Sẽ thực hiện ở các version sau để giữ core tập trung vào dữ liệu cứng. | Tránh nhiễu thông tin từ tin đồn thị trường. |

## 5.2 Checkpoint 2 — Clarity Review Gate

### PRD Skeleton (Dự thảo)
- **User Story:** "Là một nhà đầu tư cá nhân, tôi muốn tải lên 3 báo cáo tài chính của các công ty cùng ngành để Agent so sánh và chỉ ra doanh nghiệp có lợi thế cạnh tranh nhất."
- **Model:** **Gemini 1.5 Pro** (Ưu tiên khả năng xử lý context window lớn để đọc hàng chục file PDF cùng lúc).
- **Fallback:** Nếu dữ liệu trong báo cáo bị thiếu hoặc mâu thuẫn, Agent sẽ liệt kê các "điểm mù" và yêu cầu người dùng xác nhận lại thay vì tự suy diễn.
- **Data Source:** Báo cáo tài chính niêm yết (Vietstock, CafeF), Báo cáo thường niên, và dữ liệu ngành từ các tổ chức uy tín.

---

## 5.3 Final Checklist (Bản nháp)
- **Hypothesis:** "Nếu Agent có thể rút gọn một báo cáo 200 trang thành 5 điểm mấu chốt trong dưới 1 phút, tỷ lệ người dùng quay lại sử dụng để lọc cổ phiếu sẽ đạt trên 80%."
- **Aha Moment:** Khi người dùng đặt một câu hỏi hóc búa (ví dụ: "Khoản nợ tiềm tàng của công ty này nằm ở mục nào?") và Agent chỉ ra chính xác số trang kèm phân tích rủi ro trong vài giây.
