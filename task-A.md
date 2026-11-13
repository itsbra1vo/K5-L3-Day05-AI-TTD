# Bài làm của Người A — "Người kịch bản" (Track T2 Giáo dục)

> **Vai trò A:** Viết **§1** (lát cắt & phạm vi) + **§2** (kịch bản rủi ro) · dựng **ảnh 1** prototype · demo phần lát cắt + ca khó #4.

## PHẦN 1 — §1 Lát cắt & phạm vi (viết vào `spec.md`)

### 1.1 Lát cắt (nguyên văn từ track)

> *[A chép nguyên văn lát cắt từ `tracks/t2-education.md` — đề nói đã phát sẵn, không chọn lại]*

**A diễn giải lại để cả nhóm dùng chung (một câu):**

> Một **học viên** đang hỏi bài **tối muộn** trên trang khoá học · AI phải quyết định **giải thích dựa trên tài liệu buổi học, hỏi lại cho rõ, hay chuyển TA** · kết quả là học viên **hiểu đúng** — hoặc **học sai mà không biết** (cái giá âm thầm đặc thù của T2).

### 1.2 Ba việc tính năng KHÔNG làm

| # | Việc KHÔNG làm | Vì sao (trỏ về track) |
|---|---|---|
| 1 | **Không làm bài hộ / không đưa đáp án cuối cùng khi học viên chưa tự làm.** | Study Mode được thiết kế để **không làm hộ** — system prompt của OpenAI ghi rõ *"DO NOT DO THE USER'S WORK FOR THEM"* . Làm hộ = học viên nộp bài không hiểu, đúng cái giá T2: *"học sai mà không biết"*. |
| 2 | **Không trả lời nội dung buổi học chưa có tài liệu trong `[T2]`.** | Track T2 nói rõ: *"trang khoá học chỉ có tên buổi 4 'Trực quan hoá dữ liệu', chưa có tài liệu → AI dễ kể luôn 'buổi 4 học biểu đồ cột và Tableau'"*. Bịa nội dung = lớp ① nguồn sự thật. |
| 3 | **Không thay TA/giảng viên xác nhận "bạn đã hiểu rồi" hay chấm điểm.** | Thẩm quyền của TA; AI xác nhận sai → học viên yên tâm với kiến thức sai, không ai phát hiện. |

**Kiểm tra chéo:** ảnh 1 prototype (A dựng) **không được vi phạm** 3 việc này — không có nút "đưa đáp án", không có tool "xác nhận đã hiểu", badge vàng khi thiếu tài liệu.

---

## PHẦN 2 — §2 Kịch bản rủi ro (≥8, phủ 4 lớp)

> **Cách A làm:** bắt đầu từ **3 tin mồi** của track `[T2]` + **Hard tests** trong `t2-education.md`, rồi viết thêm cho đủ 4 lớp. Mỗi dòng 5 cột: `tin người dùng | lớp | AI có thể sai thế nào | sản phẩm tốt nên làm gì | nhãn`.
>
> **Tool tham chiếu** (A đối chiếu tên chính xác trong `[T2]`):
> - `doc_tai_lieu_buoi_hoc` (đọc) — đọc slide/ghi chú buổi học
> - `giai_thich_theo_buoc` (đọc) — giải thích từng bước, dẫn dắt
> - `ra_quiz_kiem_tra` (đọc) — tạo quiz tự kiểm tra
> - `danh_dau_chua_chac` (ghi) — đánh dấu câu "chưa có căn cứ" cho TA
> - `chuyen_TA` (ghi) — chuyển câu hỏi cho TA

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

### Kiểm tra phủ 4 lớp (A tự soát trước M1)

| Lớp | Kịch bản | Đạt? |
|---|---|---|
| ① Nguồn sự thật | #1, #3 | ✅ |
| ② Mơ hồ / thiếu thông tin | #2, #6, #8 | ✅ |
| ③ Ngoài phạm vi / thẩm quyền | #5 | ✅ |
| ④ Đặc thù domain (âm thầm) | #2, #4, #7 | ✅ |

**Kiểm tra cột "AI có thể sai thế nào":** mỗi dòng trỏ về **1 tool + 1 dòng data cụ thể** (tài liệu buổi 4 chỉ có tên; tài liệu buổi 3 có nhiều đoạn; không có data đề thi). Không có dòng nào ghi "AI trả lời sai" chung chung. ✅

### 2 kịch bản đắt nhất — lập luận chọn

**#4 — "AI giải thích sai khái niệm, học viên tưởng đúng"**

- **Vì sao đắt hơn các kịch bản khác:**
  - Đúng cái giá T2: *"rẻ mỗi lần nhưng âm thầm: học sai mà không biết"*. Học viên **không có tín hiệu phát hiện** — AI nói tự tin, không badge, không trích dẫn.
  - Sai **lan sang** bài tập → bài thi → môn sau. **Không đảo ngược** được — kiến thức sai đã "vào đầu".
  - **Hơn #3** (đề thi): #3 sai thì học viên có thể hỏi TA, sửa trước khi thi. #4 sai **không ai biết** cho đến khi thi rớt.
  - **Hơn #1** (buổi 4): #1 học viên phát hiện khi tới lớp (tài liệu không khớp). #4 không có điểm phát hiện.

**#2 — "Học viên xin đừng đưa đáp án, AI vẫn đưa"**

- **Vì sao đắt hơn các kịch bản khác:**
  - Vi phạm **hợp đồng học tập** — học viên **chủ động** xin hướng dẫn, AI phá vỡ. Study Mode thừa nhận có thể **"quay lại trả lời trực tiếp nếu bị insist"** .
  - Học viên mất cơ hội tự làm, **học sai âm thầm** vì tưởng mình hiểu (thực ra chỉ đọc đáp án). Cùng cái giá T2.
  - **Hơn #5** (nộp gấp): #5 học viên biết mình đang xin đáp án — có thể tự thấy sai. #2 học viên **đã cố gắng học đúng cách** mà AI vẫn phá — mất niềm tin + học sai.

**Kịch bản suýt được chọn: #1 (bịa nội dung buổi 4).**
- **Vì sao suýt:** cũng là bịa (lớp ①), cũng gây học sai.
- **Vì sao không chọn:** #1 học viên **có thể phát hiện** khi tới lớp (tài liệu không khớp với lời AI). #4 và #2 **không có tín hiệu phát hiện** — đúng nghĩa "âm thầm" của T2.

### Ghi chú cho B và C (bàn giao sang chặng 3–5)

- **B (chặng 3):** 2 kịch bản #4 và #2 cần viết verbatim + UI + phương án loại. Gợi ý hướng:
  - #4 → badge vàng + khung nguồn trống + nút "Báo TA" (G2, G11, PAIR Explainability).
  - #2 → nút "Làm lại từ đầu" + log TA (G8, G9, G10).
- **C (chặng 5):** ảnh 1 cần thể hiện badge xanh/vàng + khung nguồn + nút "Báo TA" + nút "Làm lại". Ảnh 2 (quiz) cần nút "Chuyển TA".
- **Nhãn mức hại** đã gắn: #1 sửa được · #2 sửa được · #3 không chấp nhận được · #4 không chấp nhận được · #5 sửa được · #6 sửa được · #7 sửa được · #8 sửa được. **2 kịch bản "không chấp nhận được"** là #3 và #4 — nhưng #4 đắt hơn #3 vì **âm thầm**, nên chọn #4 thay #3.

---

## PHẦN 3 — Ảnh 1 prototype (A dựng ở chặng 5)

### Mô tả màn hình "Hỏi bài" — ca khó #4

**Bố cục (từ trên xuống):**

```
┌─────────────────────────────────────────────────┐
│  Khoá học · Buổi 3 · Hỏi bài                    │
├─────────────────────────────────────────────────┤
│  [Học viên] Overfitting là gì ạ?                │
│                                                 │
│  [AI] Overfitting là khi model học quá kém...   │
│       ┌──────────────────────────────────┐      │
│       │ 🟡 Chưa có căn cứ trong tài liệu │      │
│       │    — TA sẽ xem lại               │      │
│       └──────────────────────────────────┘      │
│       ┌──────────────────────────────────┐      │
│       │ 📄 Nguồn: tài liệu buổi 3        │      │
│       │    (Không tìm thấy đoạn khớp)    │      │
│       └──────────────────────────────────┘      │
│                                                 │
│  [🔁 Làm lại từ đầu]  [🚩 Báo TA câu trả lời]  │
│                                                 │
│  [💬 Chuyển TA]                                 │
└─────────────────────────────────────────────────┘
```

**Đánh số các chỗ + map HAX/PAIR + mức tự chủ:**

| Số | Chỗ trên màn hình | Thể hiện gì | HAX/PAIR | Mức tự chủ |
|---|---|---|---|---|
| **1** | Badge **🟡 "Chưa có căn cứ trong tài liệu — TA sẽ xem lại"** dưới câu AI | Độ chắc của câu trả lời | **G2** — làm rõ AI làm tốt đến đâu | `giai_thich_theo_buoc` = tự làm **có ràng buộc** (không trích được → badge vàng) |
| **2** | Khung **📄 "Nguồn: tài liệu buổi 3 — Không tìm thấy đoạn khớp"** | Bằng chứng AI dựa vào (hoặc thiếu) | **G11** — giải thích vì sao; **PAIR Explainability + Trust** | `doc_tai_lieu_buoi_hoc` = tự làm |
| **3** | Nút **🔁 "Làm lại từ đầu"** | Đường lui khi AI lỡ đưa đáp án | **G8** — gạt bỏ dễ dàng; **G9** — sửa dễ dàng | `giai_thich_theo_buoc` = tự làm (reset) |
| **4** | Nút **🚩 "Báo TA câu trả lời"** | Đường chuyển người khi badge vàng | **G9** — sửa dễ dàng | `danh_dau_chua_chac` + `chuyen_TA` = tự làm |
| **5** | Nút **💬 "Chuyển TA"** (luôn bật) | Đường chuyển người chủ động | **PAIR Errors + Graceful Failure** | `chuyen_TA` = tự làm |

**Trạng thái xanh (khi AI trích được tài liệu):**
- Badge đổi thành **🟢 "Có trong tài liệu"**; khung nguồn hiện **đoạn trích + số slide** (ví dụ: *"Slide 12, buổi 3: 'Overfitting là khi model học quá khớp tập train...'"*).
- Nút "Báo TA" vẫn hiện (học viên có quyền nghi ngờ dù badge xanh).

**A phải kiểm tra trước M3:**
- [ ] Bấm qua được ca #4 từ đầu tới cuối (hỏi → badge vàng → báo TA → xác nhận).
- [ ] Thấy **≥2 mức tự chủ**: `giai_thich_theo_buoc` (tự làm + ràng buộc) vs `chuyen_TA` (tự làm).
- [ ] Mỗi HAX/PAIR trỏ được vào **một số cụ thể** (1–5) — TA sẽ hỏi *"Chỉ tôi chỗ nào là G2"*.
- [ ] **Không vi phạm §1:** không có nút "đưa đáp án", không có tool "xác nhận đã hiểu".

---

## PHẦN 4 — Demo của A (chuẩn bị)

### Kịch bản demo (khoảng 1 phút 30 giây)

**30 giây đầu — lát cắt + phạm vi:**
> *"Đây là track T2 — Giáo dục. Lát cắt: một học viên hỏi bài tối muộn trên trang khoá học; AI phải quyết định giải thích dựa trên tài liệu, hỏi lại, hay chuyển TA. Cái giá đặc thù: **rẻ mỗi lần nhưng âm thầm — học sai mà không biết**. Tính năng **không làm** 3 việc: không làm bài hộ, không bịa nội dung buổi chưa có tài liệu, không thay TA xác nhận đã hiểu."*

**60 giây — bấm ảnh 1 qua ca khó #4:**
> *"Đây là ca đắt nhất: học viên hỏi 'Overfitting là gì'. AI trả lời — nhưng nhìn badge: **vàng, 'Chưa có căn cứ trong tài liệu'**. Khung nguồn ghi 'Không tìm thấy đoạn khớp'. Đây là **G2** — làm rõ AI chắc tới đâu. Học viên bấm **'Báo TA'** — đây là **G9**. TA nhận ticket ngay, phản hồi trong 24h. Nếu AI lỡ đưa đáp án ở ca khác, có nút **'Làm lại từ đầu'** — **G8**. Mức tự chủ: `giai_thich_theo_buoc` **tự làm có ràng buộc trích dẫn**; `chuyen_TA` **tự làm**."*

**Câu A phải trả lời được khi TA hỏi:**
1. *"Kịch bản #4 trỏ vào tool nào, dòng data nào?"* → `giai_thich_theo_buoc` + `doc_tai_lieu_buoi_hoc` (không trả về đoạn khớp cho "overfitting").
2. *"Vì sao #4 đắt hơn #3?"* → #3 học viên hỏi TA sửa được trước khi thi; #4 **âm thầm**, không ai biết cho đến khi thi rớt.
3. *"Chỉ tôi chỗ nào là G2 trên màn hình."* → Badge vàng số **1**.
4. *"Hành động `giai_thich_theo_buoc` sai thì ai mất gì?"* → Học viên **mất kiến thức đúng** (âm thầm), không ai đền được.

---

## Checklist nộp phần A

- [ ] §1: lát cắt **nguyên văn từ `[T2]`** (không phải bản diễn giải) + 3 việc KHÔNG làm có lý do trỏ track.
- [ ] §2: **≥8 kịch bản**, phủ đủ 4 lớp, mỗi dòng trỏ **tool/data cụ thể**, có nhãn mức hại.
- [ ] §2: lập luận **2 kịch bản đắt nhất** + **kịch bản suýt được chọn + vì sao không**.
- [ ] Ảnh 1: bấm được ca #4, có badge xanh/vàng + khung nguồn + nút "Báo TA" + "Làm lại" + "Chuyển TA"; **đánh số 1–5** map HAX/PAIR + mức tự chủ.
- [ ] Ảnh 1 **không vi phạm** 3 việc KHÔNG làm ở §1.
- [ ] Demo: nói được 30s lát cắt + bấm ca #4 + trả lời 4 câu TA có thể hỏi.
- [ ] Đã **đối chiếu `t2-education.md`** thay hết `[T2]` trước khi nộp.
