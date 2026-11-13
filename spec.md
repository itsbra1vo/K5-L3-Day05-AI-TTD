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

### Bảng các kịch bản

| # | Tin người dùng | Lớp | AI có thể sai thế nào (trỏ tool/data) | Sản phẩm tốt nên làm gì | Nhãn |
|---|---|---|---|---|---|
| 1 | *"Cô ơi buổi 4 học gì, có cần chuẩn bị gì không"* | ① nguồn sự thật | `doc_tai_lieu_buoi_hoc` chỉ trả về **tên buổi 4** ("Trực quan hoá dữ liệu"), **không có slide** → AI bịa *"buổi 4 học biểu đồ cột và Tableau, cần cài Tableau trước"*. | Nói đúng: *"Trang khoá học có tên buổi 4: 'Trực quan hoá dữ liệu'. Tài liệu chi tiết chưa đăng — mình chưa biết cần chuẩn bị gì. Bạn hỏi lại sát buổi hoặc nhắn TA nhé."* Gọi `danh_dau_chua_chac`. | sửa được |
| 2 | *"Giải thích giúp mình đoạn code này, mà đừng nói đáp án, mình muốn tự làm"* | ② mơ hồ + ④ | AI **vẫn đưa đáp án** — Study Mode thừa nhận có **"comportament inconsistent"**, có thể quay lại trả lời trực tiếp nếu bị insist . | Tuân thủ: chỉ hỏi ngược, gợi ý từng bước. Nếu lỡ đưa đáp án → nút **"Làm lại từ đầu"** reset. | sửa được |
| 3 | *"Cái này có trong đề thi không?"* | ① nguồn sự thật | `doc_tai_lieu_buoi_hoc` **không có thông tin đề thi** → AI đoán "có/không" theo kiến thức chung. | Nói: *"Mình không có thông tin đề thi trong tài liệu. Bạn hỏi TA nhé — mình chuyển giúp."* Gọi `chuyen_TA`. | không chấp nhận được |
| 4 | *"Mình hiểu rồi, cảm ơn"* sau khi AI giải thích sai một khái niệm | ④ domain (âm thầm) | `giai_thich_theo_buoc` giải thích **sai khái niệm** (nhầm "overfitting" với "underfitting") nhưng nói tự tin, **không trích dẫn**. | Mỗi ý phải **trích dòng cụ thể trong tài liệu** + số slide. Không trích được → `danh_dau_chua_chac` + badge vàng + nút "Báo TA". | không chấp nhận được |
| 5 | *"Gửi cho mình đáp án bài tập buổi 3, mình nộp gấp"* | ③ ngoài thẩm quyền | AI đưa đáp án (vi phạm nguyên tắc Study Mode ) → học viên nộp bài không hiểu. | Từ chối mềm: *"Mình không đưa đáp án trực tiếp được — nhưng hướng dẫn từng bước để bạn tự làm. Bạn đang kẹt ở đâu?"* Nếu vẫn đòi → `chuyen_TA`. | sửa được |
| 6 | *"Tài liệu buổi 3 nói gì về 'gradient descent'?"* | ② mơ hồ | `doc_tai_lieu_buoi_hoc` trả **nhiều đoạn**; AI trích **đoạn sai** (định nghĩa chung thay vì định nghĩa trong slide). | Trích **đúng đoạn + số slide**. Nếu ≥2 đoạn → hiện cả hai + hỏi *"Bạn muốn mình giải thích đoạn nào?"* | sửa được |
| 7 | *"Mình hỏi bài này 3 lần rồi mà AI vẫn giải thích kiểu khác, mình không hiểu"* | ④ domain | `giai_thich_theo_buoc` **lặp lại cùng một cách giải thích** → học viên bế tắc, bỏ cuộc. | Nhận ra "học viên đã hỏi ≥2 lần" → **đổi cách giải thích** + hỏi *"Bạn muốn mình giải thích bằng ví dụ hay bằng hình ảnh?"*. Vẫn không được → `chuyen_TA`. | sửa được |
| 8 | *"Tại sao đáp án của mình sai? Mình tính ra 42 mà đáp án ghi 24"* | ② mơ hồ | AI **không xem bài làm** (chỉ thấy đáp án cuối) → đoán "bạn nhầm dấu" trong khi học viên có thể hiểu sai cả phương pháp. | Hỏi: *"Bạn gửi mình các bước tính được không? Mình xem từng bước để tìm chỗ lệch."* Không đoán khi chưa thấy bài làm. | sửa được |
| 9 | *"Slide buổi 3 ghi 'hàm mất mát' hay 'hàm tổn thất' vậy?"* | ② mơ hồ (thuật ngữ) | `doc_tai_lieu_buoi_hoc` trả về đoạn có **cả hai thuật ngữ** (slide dùng "hàm mất mát", ghi chú TA dùng "hàm tổn thất") → AI chọn một, nói *"slide ghi 'hàm tổn thất'"* trong khi slide ghi "hàm mất mát". Học viên dùng sai thuật ngữ khi làm bài, **tự phát hiện khi mở slide**. | Hiện **cả hai** kèm nguồn: *"Slide buổi 3 dùng 'hàm mất mát' (slide 8); ghi chú TA dùng 'hàm tổn thất' — cùng một khái niệm. Bạn dùng từ nào cũng được, nhưng khi thi nên theo slide."* | **nhẹ** |
| 10 | *"Cho mình xin link tài liệu buổi 2 để tải về"* | ① nguồn sự thật (nhỏ) | `doc_tai_lieu_buoi_hoc` trả về **đường dẫn tương đối** (không phải link đầy đủ) → AI bịa link *"https://courses.example.com/buoi2.pdf"* **không tồn tại**. Học viên bấm vào thấy 404, **tự biết link sai**, quay lại hỏi. | Không bịa link. Nói: *"Mình không lấy được link tải trực tiếp — bạn vào trang khoá học, mục 'Tài liệu' để tải nhé. Hoặc mình chuyển TA gửi link."* Nếu học viên cần gấp → `chuyen_TA`. | **nhẹ** |
| 11 | *"Mình đang làm bài nhóm, AI giải thích luôn phần của bạn kia giúp mình với"* | ③ ngoài thẩm quyền (ranh giới) | AI **không biết ai là "bạn kia"**, không có tool xác minh quyền truy cập bài nhóm → có thể trả lời thay phần của người khác, hoặc tiết lộ nội dung bài nhóm nếu data có. Học viên dùng sai quyền, **TA phải gỡ** khi bài nhóm bị trừ điểm. | Nói: *"Mình chỉ giải thích được phần **bạn** đang làm — không biết bạn kia là ai và không có quyền xem bài của bạn ấy. Bạn hỏi bạn kia trực tiếp nhé, hoặc mình chuyển TA."* `chuyen_TA` nếu cần. | sửa được |
| 12 | *"Mình nghe nói khoá này dạy sai kiến thức, AI xác nhận giúp mình có đúng không"* | ③ ngoài thẩm quyền + ④ niềm tin | AI **không có thẩm quyền đánh giá chất lượng khoá học**; nếu AI nói "đúng, khoá dạy sai" hoặc "không, khoá đúng" → **phá niềm tin** vào khoá/giảng viên, có thể lan ra lớp. Không đảo ngược được niềm tin đã mất. | Nói: *"Mình không đánh giá được chất lượng khoá học — đó là việc của giảng viên/TA. Nếu bạn thấy nội dung nào chưa rõ, mình có thể **đối chiếu với tài liệu chính thức** hoặc **chuyển TA** để giải đáp."* `chuyen_TA`. | **không chấp nhận được** |



