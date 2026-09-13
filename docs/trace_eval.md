# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Nguyễn Danh Gia Minh  
> **Mã Sinh Viên / Mã Học viên:** 2A202602441
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni: Tra cứu điểm GPA, lịch thi và đặt lịch tư vấn học vụ với Cố vấn.  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Với truy vấn phức hợp (VD: "GPA giảm, tôi nên gặp cố vấn khi nào?") hệ thống phải: (1) truy xuất GPA, (2) đối chiếu ngưỡng cảnh báo học vụ, (3) tra lịch thi/lịch học, (4) tra lịch trống cố vấn, (5) đề xuất khung giờ phù hợp. Một số truy vấn đơn giản (tra GPA/lịch thi) thì chỉ cần 1 bước nên chưa đạt mức tối đa. |
| **2. Tool Interaction** | 5 / 5 | Hệ thống bắt buộc kết nối hệ thống quản lý học vụ (SIS) để lấy GPA, CSDL lịch thi, và hệ thống lịch/calendar của cố vấn để đặt lịch hẹn — không thể xử lý chỉ bằng dữ liệu tĩnh →cần kết nối với MCP Server / Cơ sở dữ liệu bên ngoài |
| **3. Dynamic Decision** | 4 / 5 | Nếu khung giờ cố vấn rảnh trùng lịch thi/lịch học của sinh viên, hệ thống phải tự động truy vấn lại và đề xuất khung giờ khác; nếu GPA dưới ngưỡng, hệ thống chủ động gợi ý đặt lịch tư vấn. Phạm vi khá giới hạn nên chưa đạt mức tối đa. |
| **4. Long Horizon Goal** | 3 / 5 | Ở mức trung bình, mục tiêu (giúp sinh viên tra cứu và đặt lịch thành công) cần duy trì qua nhiều lượt trong một phiên (tra thông tin → chọn giờ → xử lý xung đột → xác nhận), nhưng không kéo dài nhiều ngày/nhiều phiên như agent quản lý dự án dài hạn. |
| **TỔNG ĐIỂM AGENTIC FIT** | **16 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Đặt lịch hẹn: 'Đặt lịch hẹn tư vấn cho SV2026001 vào 14:00 ngày 15/09/2026'",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "14:00 15/09/2026",
      "advisor_name": "PGS.TS Nguyễn Văn A"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "14:00 15/09/2026",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 14:00 15/09/2026."
    },
    "latency_ms": 3480.24
  },
  {
    "step": 2,
    "query": "Đặt lịch hẹn: 'Đặt lịch hẹn tư vấn cho SV2026001 vào 14:00 ngày 15/09/2026'",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 14:00 15/09/2026.",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 5 lượt.
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
