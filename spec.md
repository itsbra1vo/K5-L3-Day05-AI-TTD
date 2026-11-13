# LAB5 — Thiết kế sản phẩm AI cho lúc nó sai · AI20K K5 · Ngày 5

# Bài nộp LAB5 — [Track 02] · Nhóm TTD

## Thành viên nhóm

**Lớp:** L3B · **Track:** 02

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| Đàm Hồng Thái | 2A202603927  | §1, §2  |
|  |  |  |
|  |  |  |

## §1. Lát cắt & phạm vi
- **Lát cắt** : Trong **trợ lý học bài của trang khoá học (kiểu ChatGPT Study mode)**, khi **học viên** đang hỏi bài lúc tối muộn, khi không còn ai để hỏi, **AI giảng kèm trích tài liệu, hỏi lại cho rõ, gợi ý từng bước, hay nói thẳng "tài liệu không có, hỏi giảng viên"**, để học viên hiểu đúng bài mình đang học, không chép đáp án, không học sai mà không biết.
- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.

| # | Việc KHÔNG làm | Vì sao (trỏ về track) |
|---|---|---|
| 1 | **Không làm bài hộ / không đưa đáp án cuối cùng khi học viên chưa tự làm.** | Study Mode được thiết kế để **không làm hộ** — system prompt của OpenAI ghi rõ *"DO NOT DO THE USER'S WORK FOR THEM"* . Làm hộ = học viên nộp bài không hiểu, đúng cái giá T2: *"học sai mà không biết"*. |
| 2 | **Không trả lời nội dung buổi học chưa có tài liệu trong `[T2]`.** | Track T2 nói rõ: *"trang khoá học chỉ có tên buổi 4 'Trực quan hoá dữ liệu', chưa có tài liệu → AI dễ kể luôn 'buổi 4 học biểu đồ cột và Tableau'"*. Bịa nội dung = lớp ① nguồn sự thật. |
| 3 | **Không thay TA/giảng viên xác nhận "bạn đã hiểu rồi" hay chấm điểm.** | Thẩm quyền của TA; AI xác nhận sai → học viên yên tâm với kiến thức sai, không ai phát hiện. |

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.



## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
