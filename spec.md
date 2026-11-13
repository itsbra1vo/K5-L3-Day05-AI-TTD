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

### Bảng 8 kịch bản

| # | Tin người dùng | Lớp | AI có thể sai thế nào (trỏ tool/data) | Sản phẩm tốt nên làm gì | Nhãn |
|---|---|---|---|---|---|
| 1 | *"Cô ơi buổi 4 học gì, có cần chuẩn bị gì không"* | ① nguồn sự thật | `doc_tai_lieu_buoi_hoc` chỉ trả về **tên buổi 4** ("Trực quan hoá dữ liệu"), **không có slide** → AI bịa *"buổi 4 học biểu đồ cột và Tableau, cần cài Tableau trước"*. Học viên chuẩn bị sai, tới lớp mới biết. | Nói đúng: *"Trang khoá học có tên buổi 4: 'Trực quan hoá dữ liệu'. Tài liệu chi tiết chưa đăng — mình chưa biết cần chuẩn bị gì. Bạn hỏi lại sát buổi hoặc nhắn TA nhé."* Gọi `danh_dau_chua_chac`. | sửa được |
| 2 | *"Giải thích giúp mình đoạn code này, mà đừng nói đáp án, mình muốn tự làm"* | ② mơ hồ + ④ | AI **vẫn đưa đáp án** vì "thấy thương" — Study Mode thừa nhận có **"comportament inconsistent"** và có thể **quay lại trả lời trực tiếp nếu học viên insist** . Học viên mất cơ hội tự làm, học sai âm thầm. | Tuân thủ: chỉ hỏi ngược, gợi ý từng bước. Nếu lỡ đưa đáp án → nút **"Làm lại từ đầu"** reset hội thoại. | sửa được |
| 3 | *"Cái này có trong đề thi không?"* | ① nguồn sự thật | `doc_tai_lieu_buoi_hoc` **không có thông tin đề thi** (chỉ slide bài giảng) → AI đoán "có/không" theo "kiến thức chung". Học viên học lệch. | Nói: *"Mình không có thông tin đề thi trong tài liệu. Bạn hỏi TA nhé — mình chuyển giúp."* Gọi `chuyen_TA`. | không chấp nhận được |
| 4 | *"Mình hiểu rồi, cảm ơn"* sau khi AI giải thích sai một khái niệm | ④ domain (âm thầm) | `giai_thich_theo_buoc` giải thích **sai khái niệm** (ví dụ nhầm "overfitting" với "underfitting") nhưng nói rất tự tin, **không trích dẫn**. Học viên tưởng đúng — đúng cái giá T2: *"học sai mà không biết"*. | Mỗi ý phải **trích dòng cụ thể trong tài liệu** + số slide. Không trích được → `danh_dau_chua_chac` + badge vàng **"Chưa có trong tài liệu — TA sẽ xem lại"** + nút "Báo TA". | không chấp nhận được |
| 5 | *"Gửi cho mình đáp án bài tập buổi 3, mình nộp gấp"* | ③ ngoài thẩm quyền | AI đưa đáp án (vi phạm nguyên tắc Study Mode ) → học viên nộp bài không hiểu, giảng viên không biết trình độ thật. | Từ chối mềm: *"Mình không đưa đáp án trực tiếp được — nhưng mình hướng dẫn từng bước để bạn tự làm. Bạn đang kẹt ở đâu?"* Nếu vẫn đòi → `chuyen_TA`. | sửa được |
| 6 | *"Tài liệu buổi 3 nói gì về 'gradient descent'?"* | ② mơ hồ | `doc_tai_lieu_buoi_hoc` trả **nhiều đoạn** liên quan; AI trích **đoạn sai** (định nghĩa chung thay vì định nghĩa trong slide). Học viên học sai theo tài liệu của chính khoá. | Trích **đúng đoạn + số slide/trang**. Nếu ≥2 đoạn → hiện cả hai + hỏi *"Bạn muốn mình giải thích đoạn nào?"* | sửa được |
| 7 | *"Mình hỏi bài này 3 lần rồi mà AI vẫn giải thích kiểu khác, mình không hiểu"* | ④ domain | `giai_thich_theo_buoc` **lặp lại cùng một cách giải thích** (không có biến thể) → học viên bế tắc, bỏ cuộc. | Nhận ra "học viên đã hỏi ≥2 lần" → **đổi cách giải thích** (ví dụ: dùng ví dụ thực tế thay vì công thức) + hỏi *"Bạn muốn mình giải thích bằng ví dụ hay bằng hình ảnh?"*. Vẫn không được → `chuyen_TA`. | sửa được |
| 8 | *"Tại sao đáp án của mình sai? Mình tính ra 42 mà đáp án ghi 24"* | ② mơ hồ | AI **không xem bài làm của học viên** (chỉ thấy đáp án cuối) → đoán "bạn nhầm dấu" trong khi học viên có thể hiểu sai cả phương pháp. Học viên sửa sai chỗ. | Hỏi: *"Bạn gửi mình các bước tính được không? Mình xem từng bước để tìm chỗ lệch."* Không đoán khi chưa thấy bài làm. | sửa được |

## §3. Khi AI sai  (chặng 3)
Với mỗi kịch bản đắt nhất:
- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
