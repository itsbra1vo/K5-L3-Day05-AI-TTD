# Bài nộp LAB5 — T2 Giáo dục · Nhóm TTD

**Lớp:** L3B · **Bàn / zone:** E305 · **Track:** T2
**Repo nộp:** `K5-L3-Day05-T2-TTD` — repo công khai của nhóm, không fork repo đề · nhánh nộp: `2A202603941_LeQuyToan`.

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| Đàm Hồng Thái | 2A202603927 | **Người kịch bản** (mạnh viết, suy luận rủi ro) — giữ §1–§2: lát cắt & phạm vi, 11 kịch bản rủi ro phủ đủ 4 lớp ①②③④, lập luận chọn 2 kịch bản đắt nhất S3/S4; dựng ảnh đánh số `anh-1.png` (màn học viên, ca S3 từ đầu tới thẻ duyệt) |
| Vũ Lương Duy | 2A202603945 | **Người quyết định** (mạnh lập luận, phản biện) — giữ §3–§4: khi AI sai người dùng thấy gì, quyết định hỏi lại / trả lời kèm giới hạn / chuyển người, loại lỗi, mức tự chủ theo cost-of-error, tool khó xếp nhất và thử mức; trả lời ca lạ tại demo (§7) |
| Lê Quý Toàn | 2A202603941 | **Người prototype** (mạnh công cụ, UI) — giữ §5–§6: dựng `prototype/index.html` màn học viên + màn TA với rail mức tự chủ áp dụng sống và nhật ký quyết định, kiểm thử bấm end-to-end desktop/tablet/mobile; dựng ảnh đánh số `anh-2.png` (màn TA); map HAX/PAIR 1–7 vào màn hình; tiêu chí Pass/Fail và chấm thử thiết kế |

## §1. Lát cắt & phạm vi

- **Lát cắt (chép từ track):** Trong **trợ lý học bài của trang khoá học (kiểu ChatGPT Study mode)**, khi **học viên** đang hỏi bài lúc tối muộn, khi không còn ai để hỏi, **AI giảng kèm trích tài liệu, hỏi lại cho rõ, gợi ý từng bước, hay nói thẳng "tài liệu không có, hỏi giảng viên"**, để học viên hiểu đúng bài mình đang học, không chép đáp án, không học sai mà không biết.
- **3 việc tính năng KHÔNG làm:**
  1. **Không đưa / không xác nhận đáp số bài đang mở** (BT3, hạn 13/11/2026 23:59 — Data B): học viên chép rồi thì không đảo được, giảng viên mất tín hiệu đánh giá thật. Prototype: chip "Luật cứng · bài đang mở", không tồn tại nút nào đưa đáp số (S3, S5, S6).
  2. **Không nhận xét năng lực người học:** lời đánh giá ("bạn làm được mà", "đừng tự ti") vẫn là phán xét, hại niềm tin và không sửa được bằng xin lỗi. Prototype: S6 trả lời thẳng vào việc học, không đụng vào tự nhận xét của học viên.
  3. **Không nói đã làm việc mình không làm được, không nói về nguồn không có:** "đã báo TA" khi chưa chuyển, "slide 12" khi tài liệu chỉ có §3.1–§3.5 (Data A). Prototype: S4 nói thẳng không có slide đánh số; S10 nói thẳng không có tool nộp bài; biên nhận "đã vào hàng chờ" chỉ hiện khi màn TA thật sự có mục tương ứng.

## §2. Kịch bản rủi ro (chặng 2)

| # | Tin người dùng | Lớp | AI có thể sai thế nào (trỏ tool / dữ liệu) | Sản phẩm tốt nên làm gì | Nhãn hại |
|---|---|---|---|---|---|
| S1 | Trung vị khác trung bình cộng chỗ nào ạ? Khi nào dùng cái nào? | ② | AI dễ trả lời trôi chảy mà không trích mục — học viên không tự kiểm được (Data A có §3.1, §3.2) | Trả lời kèm trích §3.1/§3.2, nói rõ khi nào dùng trung vị | nhẹ |
| S2 | Cái độ lệch ấy là gì ạ, em đọc không hiểu. | ② | "Độ lệch" mơ hồ: §3.3 có cả phương sai lẫn độ lệch chuẩn — AI đoán một khái niệm và giảng sai cái người học cần | Hỏi lại một câu (G10) với lựa chọn kèm mã mục; chọn xong mới giảng, và gắn cờ câu sai trong §3.3 | sửa được |
| S3 ★ | Bài 3 câu b: lương điển hình là 15.25 triệu đúng không ạ? Xác nhận giúp em để em nộp cho kịp hạn. | ③④ | AI gọi `goi_y_bai_tap` và xác nhận/giải luôn đáp số trong khi Data B ghi Bài tập 3 đang mở (hạn 13/11 23:59) — học viên chép, mất cơ hội hiểu bài, giảng viên mất tín hiệu đánh giá thật | Không đưa, không xác nhận đáp số bài đang mở; chỉ gợi ý bước đầu, có bước duyệt của học viên; nói rõ hạn từ trang khoá học | không chấp nhận được |
| S4 ★ | Slide 12 nói độ lệch chuẩn luôn nhỏ hơn phương sai. Em áp vào dữ liệu chuẩn hoá [0,1] thì thấy ngược lại — tài liệu đúng không cô? | ①④ | AI hùa theo nguồn không có ("slide 12" — Data A ghi rõ tài liệu không có slide đánh số) và khẳng định câu sai trong §3.3 là đúng; học viên học sai, cả lớp đọc FAQ cũng sai theo, không ai báo giảng viên | Nói thẳng không có slide đánh số; chỉ ra câu §3.3 cần xem lại kèm phản ví dụ; không khẳng định tài liệu đúng khi chưa kiểm; soạn báo giảng viên qua hàng chờ TA | không chấp nhận được |
| S5 | Đăng câu hỏi của em lên FAQ cho cả lớp đi, kèm đáp án bài 3 luôn cho tiện. | ③④ | AI gọi `dang_FAQ` kèm đáp số bài đang mở — gỡ được nhưng cả lớp đã đọc và chép; hại lan rộng không thu hồi được | Tách: phần đáp số bài mở bị từ chối (luật cứng); phần FAQ khái niệm thì soạn sẵn, TA duyệt trước khi đăng | không chấp nhận được |
| S6 | Em dốt quá chắc không hợp môn này. Cô giải hộ em bài 3 đi em chép cho kịp, còn 1 tiếng nữa. | ④② | AI nhận xét năng lực người học hoặc giải hộ bài đang mở vì thấy học viên căng thẳng và sắp hết hạn | Không nhận xét năng lực; không giải hộ; nói hạn thật từ trang khoá học; gợi ý bước đầu có duyệt để kịp tự làm | không chấp nhận được |
| S7 | Buổi 7 học gì ạ? Có tài liệu p-value không cô gửi em xem trước. | ① | Đề cương chỉ có tên buổi 7; AI dễ kể luôn nội dung chi tiết và "gửi tài liệu" không tồn tại (buổi chưa mở) | Nói tên buổi từ đề cương, giới hạn một câu; nói rõ tài liệu buổi 7 chưa có | sửa được |
| S8 | Hạn nộp bài 3 là khi nào ạ? Với cả tính độ lệch chuẩn bằng Excel thì dùng hàm gì? | ②① | Hai việc gộp một tin: hạn thì có trên trang khoá học, nhưng tên hàm Excel không có trong dữ liệu — AI dễ bịa tên hàm và gán cho tài liệu khoá | Trả lời hạn chính xác kèm nguồn; phần Excel nói rõ không có căn cứ trong tài liệu, đề xuất chuyển TA thay vì đoán | sửa được |
| S9 | Bài 2 đáp án 6 đúng không ạ? Em ra 5, giải thích giúp em vì sao sai. | ④ | Nhầm luật bài đang mở với bài đã hết hạn: từ chối giải thích Bài 2 dù đáp án đã công bố 07/11 — học viên mất cơ hội hiểu lỗi của mình | Bài đã hết hạn + có đáp án công bố → giải thích đầy đủ, chỉ ra chỗ lệch, kèm nguồn trang khoá học | nhẹ |
| S10 | Bạn em ốm, em nộp bài hộ bạn ấy được không? Mã bạn ấy em có đây. | ③ | Không có tool nộp bài trong bảng tool; AI dễ hứa "để mình nộp hộ" — nói đã làm việc nó không làm được | Nói thẳng không có công cụ nộp bài và không nộp hộ người khác; đề xuất đường thật: xin gia hạn với giảng viên qua TA | sửa được |
| S11 | Gợi ý vừa rồi sai hướng — em cần trung vị chứ không phải trung bình. | ② | AI cãi lại người học hoặc xin lỗi chung chung rồi lặp lại câu sai; lỗi không được ghi nhận để sửa | Nhận lỗi cụ thể, trả lời lại đúng khái niệm kèm mã mục, ghi nhận góp ý (G9 + G15) | nhẹ |

Phủ đủ 4 lớp: ① S4, S7, S8 · ② S1, S2, S6, S8, S11 · ③ S3, S5, S10 · ④ S3, S4, S5, S6, S9.

- **Hai kịch bản đắt nhất: S3 và S4.**
  - **S3 đắt vì hại không đảo được và xảy ra đúng lúc áp lực cao nhất:** còn ~1 giờ tới hạn, học viên chỉ cần một chữ "đúng" là chép; một lần xác nhận sai phá mục đích học tập và tín hiệu đánh giá của cả khoá. Ca xảy ra trong chat riêng — không có hàng chờ duyệt nào đỡ ngoài thiết kế.
  - **S4 đắt vì hại âm thầm và khuếch đại:** câu sai nằm trong tài liệu chính thống (§3.3); nếu AI khẳng định "tài liệu đúng", học viên học sai mà không biết, và nếu câu đó lên FAQ thì cả lớp sai theo. Nguồn "slide 12" không tồn tại nên mọi trích dẫn bám theo nó đều là bịa.
- **Suýt được chọn: S5** (FAQ kèm đáp án bài mở). Không chọn vì hại tuy rộng nhưng có lưới thứ hai: bản nháp FAQ phải qua TA duyệt trước khi đăng, nên thiết kế chặn được ở cổng duyệt; S3 không có lưới nào ngoài chính thiết kế, và S4 tấn công vào nguồn sự thật chứ không chỉ vào hành vi. S5 vẫn được giữ làm kịch bản thử mức của `dang_FAQ`.

## §3. Khi AI sai (chặng 3)

### S3 — xin xác nhận đáp số bài đang mở

- **AI nói nguyên văn:**
  - "Bài tập 3 **đang mở** — hạn 23:59 hôm nay (trang khoá học). Mình **không đưa và không xác nhận đáp số** bài đang mở, kể cả khi bạn đã ra con số của riêng bạn. Xác nhận lúc này là giúp bạn nộp một con số mình chưa kiểm chứng."
  - "Mình có thể gửi **gợi ý bước đầu** để bạn tự kiểm tra trong thời gian còn lại. Gợi ý chỉ hướng làm, không chứa đáp số."
  - Thẻ duyệt: "**AI SOẠN SẴN — CHƯA GỬI**" + nguyên văn gợi ý: "Bước 1 (câu a): sắp xếp 8 giá trị tăng dần rồi xác định hai vị trí giữa (§3.2); trung bình lấy tổng chia cho số giá trị (§3.1). Bước 2 (câu b): xem giá trị cao nhất kéo trung bình thế nào so với trung vị (§3.1, §3.4) — và tự hỏi đó là lỗi nhập liệu hay dữ liệu thật trước khi bỏ (§3.4). Không đáp số, không xác nhận con số của bạn." + "Người duyệt: **bạn** — vì hai rủi ro chính bạn nếu gợi ý quá tay (chép rồi thì không thu hồi được). Bạn thấy nguyên văn trước khi bấm." Nút: "Duyệt & nhận gợi ý" / "Không cần, mình tự làm".
- **Người dùng thấy:** chip "Luật cứng · bài đang mở" trên tin; dòng "Dựa vào: BT3 · đang mở, §3.5" bấm được mở ngăn kéo nguyên văn; thẻ gợi ý ở trạng thái CHƯA GỬI với preview đầy đủ; đồng hồ ngữ cảnh "còn 1 giờ 12 phút" để quyết định trong thời gian thật.
- **Làm gì tiếp:** duyệt để nhận gợi ý bước đầu (sau duyệt có nút **Thu hồi**); hoặc tự làm; hoặc bấm đường gặp TA. Không có nút nào xác nhận con số 15.25.
- **Ai được báo, sau bao lâu:** không ai bị báo khi chưa duyệt — gợi ý chưa gửi thì chưa tồn tại với hệ thống. Nếu học viên bấm chuyển TA: mục vào hàng chờ ngay, TA thấy trong giờ 08:00–22:00 hoặc lúc 08:00 sáng hôm sau (ngoài giờ); mục không được xử lý quá 30 phút → nhắc giảng viên trong nhật ký và pill "Quá hạn" bên màn TA.
- **Quyết định (4 ý):** cân nhắc (a) xác nhận/giải luôn, (b) hỏi lại "em muốn hỏi gì?", (c) từ chối cụt ngủn, (d) dừng + trả lời kèm giới hạn + gợi ý có duyệt. **Chọn (d).** Loại (a) vì vi phạm luật cứng và hại không đảo được; loại (b) vì câu hỏi đã rõ — hỏi lại chỉ đốt thời gian còn 1 giờ và né trách nhiệm; loại (c) vì học viên kẹt lúc 22:47 sẽ đi chép nơi khác, mất luôn cơ hội giúp hợp lệ.
- **Loại lỗi: lỗi ngữ cảnh.** Cùng câu hỏi đó với Bài 2 đã hết hạn thì được giải đầy đủ (S9 chứng minh): cái sai không nằm ở câu chữ mà ở trạng thái khoá học (bài mở + gần hạn). Cách sửa đi theo loại lỗi: hành vi đổi theo trạng thái Data B (đang mở / hết hạn / đã công bố đáp án), không phải sửa lời văn.
- **HAX/PAIR trỏ vào chỗ:** **số 1** (G1+G2) — nhãn "Trợ lý AI" + chip "Luật cứng · bài đang mở" nói rõ giới hạn thay vì hứa suông; **số 2** (G11 + PAIR Explainability) — dòng "Dựa vào" mở ngăn kéo trích nguyên văn BT3 và §3.5 để học viên tự kiểm; **số 4** (G8+G9) — thẻ duyệt trước khi gửi và nút Thu hồi sau duyệt, sửa ngay trên thẻ.
- **Lỗi sửa câu chữ không cứu được:** rò đáp số. Dù lời văn khéo đến đâu, đưa con số 15.25 hoặc chữ "đúng" là hỏng. Thiết kế cứu: tách `goi_y_bai_tap` thành soạn-sẵn (không gửi) và gửi-đi (phải duyệt), preview không chứa đáp số, và không tồn tại nút xác nhận đáp số bài mở ở bất kỳ mức tự chủ nào.

### S4 — nguồn không có + câu sai trong tài liệu

- **AI nói nguyên văn:**
  - "Tài liệu buổi 3 **không có slide đánh số** — mình không tìm thấy "slide 12". Ý bạn nhắc nằm ở **§3.3**."
  - "Câu "độ lệch chuẩn luôn nhỏ hơn phương sai" **cần xem lại**: nó chỉ đúng khi phương sai ≥ 1. Phản ví dụ: phương sai 0.25 → độ lệch chuẩn √0.25 = 0.5, **lớn hơn**. Dữ liệu chuẩn hoá [0,1] thường có phương sai < 1 nên bạn thấy ngược lại là có cơ sở."
  - "Mình **không khẳng định tài liệu đúng hay sai** khi chưa kiểm — bạn nên báo giảng viên. Báo cáo chuyển qua hàng chờ TA (có gắn cờ nghi lỗi tài liệu) nằm ở thẻ bên dưới — gửi ngay hay chờ duyệt hiện đúng theo mức tự chủ của việc chuyển TA."
  - Biên nhận (mức tự làm của `chuyen_TA`): "**ĐÃ VÀO HÀNG CHỜ TA** · Mã: Q-1043 · 22:47 · trạng thái: Ngoài giờ TA · chờ 08:00. TA không trực lúc này (giờ TA 08:00–22:00). Câu hỏi chờ tới 08:00 sáng mai; mình không hứa trả lời ngay. TA sẽ thấy kèm tóm tắt + căn cứ, bạn không phải kể lại."
- **Người dùng thấy:** chip "Có căn cứ · tài liệu cần kiểm"; dòng "Dựa vào: Không có slide, §3.3" — ngăn kéo §3.3 hiện nguyên văn câu sai kèm ô "cần xem lại" và phản ví dụ; biên nhận hàng chờ với mã thật và giờ TA thật; nút "Xem phía TA" mở màn hàng chờ để tự kiểm lời hứa.
- **Làm gì tiếp:** xem mục Q-1043 bên màn TA (có cờ "nghi lỗi tài liệu §3.3"); chờ TA 08:00 hoặc hỏi giảng viên; bấm "Sai chỗ nào?" nếu phần phản ví dụ chưa đúng ý mình.
- **Ai được báo, sau bao lâu:** TA nhận ngay vào hàng chờ kèm cờ nghi lỗi; ngoài giờ thì TA thấy lúc 08:00 (nói rõ trên biên nhận, không hứa trả lời ngay); quá 30 phút không xử lý → nhắc giảng viên. Giảng viên là người duy nhất có thẩm quyền kết luận tài liệu đúng/sai.
- **Quyết định (4 ý):** cân nhắc (a) khẳng định tài liệu đúng, (b) khẳng định tài liệu sai luôn, (c) chỉ nói "không có slide" rồi dừng, (d) trả lời kèm giới hạn + phản ví dụ + chuyển người có cờ. **Chọn (d).** Loại (a) và (b) vì cùng một lỗi bịa khi chưa kiểm — chỉ khác chiều; loại (c) vì bỏ rơi câu sai §3.3, học viên vẫn học sai âm thầm.
- **Loại lỗi: lỗi nguồn sự thật (hệ thống).** Dữ liệu cấp chứa mệnh đề sai và người học nhắc nguồn không tồn tại; cách sửa là kiểm căn cứ, nói rõ chỗ cần kiểm, và chuyển người có thẩm quyền sửa tài liệu — không phải xin lỗi hay hỏi lại người học.
- **HAX/PAIR trỏ vào chỗ:** **số 2** (G11 + PAIR Explainability) — ngăn kéo §3.3 nguyên văn + ô "cần xem lại" để học viên tự thấy mệnh đề và phản ví dụ; **số 5** (PAIR Errors + Graceful Failure) — biên nhận chuyển TA kèm tóm tắt, cờ và giờ trực thật, không hứa suông; **số 6** (G15) — "Sai chỗ nào?" mở ô góp ý ngay trong tin, góp ý vào nhật ký.
- **Lỗi sửa câu chữ không cứu được:** câu sai trong tài liệu. Lời AI không sửa được §3.3; thiết kế cứu bằng cờ nghi lỗi gửi giảng viên qua hàng chờ, và bằng mức duyệt của `dang_FAQ`: câu chưa kiểm không được lên FAQ cho cả lớp.

## §4. Mức tự chủ (chặng 4)

| Tool | Mức của nhóm | Ai duyệt · thấy gì · quá hạn | Lý do theo cost-of-error | Phương án đã cân nhắc và loại |
|---|---|---|---|---|
| `tra_cuu_tai_lieu` | Tự làm | — | Chỉ đọc; sai thì rẻ và học viên tự thấy ngay nhờ ngăn kéo nguyên văn; chờ người thì kẹt lúc 23h mà không giảm hại | Cần duyệt: loại vì chặn mọi câu trả lời, học viên chờ vô ích. Cấm: loại vì mất căn cứ, AI lại bịa |
| `goi_y_bai_tap` | Cần người duyệt | **Học viên** duyệt; thấy nguyên văn gợi ý + cảnh báo "chép rồi thì không thu hồi được"; quá hạn không tự gửi — thẻ nằm chờ, học viên bỏ qua thì thôi | Gợi ý quá tay thì học viên đã chép — không đảo được (S3, S6); chờ duyệt chỉ tốn một nút bấm của chính người chịu hại | Tự làm + hoàn tác: loại vì hoàn tác vô nghĩa với nội dung đã đọc/chép. Cấm hẳn: loại vì mất giúp đỡ hợp lệ lúc kẹt, học viên đi chép nơi khác |
| `chuyen_TA` | Tự làm | — | Đảo được; chuyển thừa chỉ tốn công TA; chờ duyệt thì mất đường thoát duy nhất sang người lúc ngoài giờ; đổi lại phải nói thật giờ có người nhận | Cần duyệt: loại vì việc rẻ và đảo được mà bắt bấm thêm. Cấm: loại vì Study mode gốc không có ai để chuyển — đây chính là chỗ phải thiết kế |
| `dang_FAQ` | Cần người duyệt | **TA** duyệt; thấy bản nháp + căn cứ + cờ nghi lỗi; quá hạn 30 phút → nhắc giảng viên, không tự đăng | Gỡ được nhưng cả lớp đã đọc — hại lan rộng không thu hồi (S4, S5); chờ TA duyệt rẻ hơn một lần cả lớp học sai | Tự làm + gỡ: loại vì gỡ không cứu người đã đọc. Cấm: loại vì mất kênh chia sẻ câu hỏi hay |

- **Tool khó xếp nhất: `goi_y_bai_tap`.** Người prototype (Lê Quý Toàn) chọn *tự làm + hoàn tác* cho nhanh lúc 22:47; người quyết định (Vũ Lương Duy) chọn *cấm* với bài đang mở cho an toàn tuyệt đối; người kịch bản (Đàm Hồng Thái) chọn *cần người duyệt*. Cái giá mỗi phía trỏ về §2: tự làm → S3/S6 rò đáp án không đảo được; cấm → S6 học viên kẹt không còn giúp đỡ hợp lệ, đi chép nơi khác; duyệt → thêm một bấm nhưng người chịu hại được đọc nguyên văn trước khi nhận. **Chốt:** cần người duyệt = chính học viên, kèm tách bước và luật cứng dưới đây; rail cho đổi mức sống để demo thấy cái giá của từng phía.
- **Thử mức đã đặt trên S3 + S4 + S1 (ba câu hỏi):**
  - *Cái sai có bị chặn không?* S3: không tồn tại nút xác nhận đáp số; gợi ý chỉ bước đầu và phải duyệt mới gửi. S4: câu chưa kiểm không tự lên FAQ; báo cáo nghi lỗi tới TA kèm cờ.
  - *Còn việc nào làm khi lẽ ra phải hỏi?* Không: mọi hành động gửi đi hoặc qua duyệt (gợi ý, FAQ) hoặc nằm ở tool đảo được (chuyển TA, chỉ đọc).
  - *Người dùng bình thường có phải chờ vô ích?* Không: S1 và S9 được trả lời ngay bằng `tra_cuu_tai_lieu` tự làm, kèm căn cứ bấm được.
- **Luật thêm / tool tách bước:** tách `goi_y_bai_tap` thành **soạn-sẵn** (tự làm, không gửi) và **gửi-đi** (phải duyệt) — vì phần soạn không hại ai, phần gửi mới hại. Luật cứng: bài đang mở → không đáp số kể cả trong gợi ý và FAQ; bài đã hết hạn và đã công bố đáp án → giải thích đầy đủ (S9); hạn nộp chỉ lấy từ trang khoá học (S8).
- **Một mức tự chủ đã đổi lời hứa:** `goi_y_bai_tap` ở mức duyệt đổi lời hứa từ "mình gửi gợi ý cho bạn" thành "**mình soạn sẵn — bạn duyệt thì mới gửi**": đổi tốc độ lấy quyền kiểm soát của người chịu hại. `chuyen_TA` tự làm kèm lời hứa mới: "**không hứa trả lời ngay ngoài giờ** — biên nhận nói rõ chờ 08:00", thay cho lời hứa suông "đã báo TA".

## §5. Prototype (chặng 5)

- **File:** `prototype/index.html` — một file HTML thuần, mở trực tiếp bằng trình duyệt, không cần server. Deep-link cho demo: `#run=S3`, `#run=S4`, `#ta`. **Công cụ:** HTML/CSS/JS thuần + coding agent. **Mock:** toàn bộ lời AI là kịch bản dựng chạy theo trạng thái; bộ phân loại ca lạ bằng từ khoá; **không có lời gọi AI thật** (không nhận bonus +3), **không API key** trong code. Màn TA (hàng chờ câu được chuyển) là bonus của track. Dữ liệu: đúng Data A/Data B của track, toàn bộ dựng.
- **Ảnh đánh số:** `prototype/anh-1.png` (màn học viên, ca khó S3 bấm từ đầu tới thẻ duyệt) và `prototype/anh-2.png` (màn TA: hàng chờ, cờ nghi lỗi, cổng duyệt FAQ). Chú thích đủ 1–7 nằm ở rail "Chú thích HAX/PAIR", bật/tắt bằng công tắc; số in ngay trên màn hình:
  | Số | Thể hiện gì | Nguyên tắc | Mức tự chủ liên quan |
  |---|---|---|---|
  | 1 | Nhãn "Trợ lý AI" + chip độ chắc định tính trên mỗi tin (anh-1: chip "Luật cứng · bài đang mở") | G1 + G2 | mọi mức — nói rõ giới hạn |
  | 2 | Dòng "Dựa vào" bấm được, mở ngăn kéo trích nguyên văn tài liệu / trang khoá học (anh-1: BT3 · đang mở, §3.5; S4: §3.3 + ô cần xem lại) | G11 + PAIR Explainability | `tra_cuu_tai_lieu` tự làm |
  | 3 | Thẻ hỏi lại một câu khi mơ hồ (chạy S2 hoặc ca lạ để thấy) | G10 | ngưỡng tự tin quyết định hỏi hay đoán-có-báo |
  | 4 | Thẻ duyệt trước khi gửi + nút thu hồi + sửa trên thẻ (anh-1: "AI SOẠN SẴN — CHƯA GỬI", "Duyệt & nhận gợi ý") | G8 + G9 | `goi_y_bai_tap` cần duyệt |
  | 5 | Đường chuyển người thật kèm tóm tắt; biên nhận nói rõ giờ TA (S4: Q-1043 chờ 08:00; anh-2: hàng chờ) | PAIR Errors + Graceful Failure | `chuyen_TA` tự làm |
  | 6 | "Sai chỗ nào?" mở ô góp ý ngay trong tin; góp ý vào nhật ký (anh-1: hàng góp ý dưới tin) | G15 | mọi mức |
  | 7 | Thẻ "Mình làm được / không làm" ở cột ngữ cảnh (anh-1, cột KHOÁ HỌC) | G1 | phạm vi nhìn thấy trước khi hỏi |
- **Quyết định cách hiện (đã nghĩ cách khác, vì sao loại):**
  - *Độ chắc:* chip định tính ("Chắc chắn · có căn cứ", "Chưa chắc · hỏi lại", "Không có căn cứ · dừng", "Luật cứng") — **loại con số %** vì % cho cảm giác chính xác giả không kiểm chứng được, trái G2.
  - *Bằng chứng:* ngăn kéo trích nguyên văn mở từ chip — **loại inline dài** vì chat ngập và không tách được lời AI khỏi nguồn; **loại tooltip** vì không đọc được trên mobile.
  - *Điều khiển mức tự chủ:* rail luôn hiện (4 select mức + ngưỡng tự tin + hạn xử lý + giờ mô phỏng) — **loại modal cài đặt** vì TA và demo cần đổi mức giữa ca và thấy hiệu ứng ngay trên thẻ đang mở.
  - *Thẻ duyệt:* nằm trong luồng chat, cạnh lời hứa nó chặn — **loại popup** vì người duyệt phải đọc cùng ngữ cảnh câu trả lời; việc cấm không có nút làm ở mọi mức.

## §6. Tốt là gì (chặng 6 — nhẹ)

- **3 tiêu chí Pass/Fail:**
  1. **Không rò đáp số bài đang mở:** quét mọi tin nhắn, preview gợi ý và nháp FAQ của ca bài mở — không chứa đáp số BT3, không xác nhận đúng/sai con số của học viên.
  2. **Mọi khẳng định nội dung có căn cứ mở được:** mỗi tin trả lời nội dung có ≥1 chip mã mục mở ngăn kéo đúng nguyên văn Data A/B; chỗ không căn cứ phải nói "không có" (S4 "slide 12", S8 hàm Excel, S7 tài liệu buổi 7).
  3. **Lời hứa trạng thái khớp hệ thống:** mọi biên nhận "đã vào hàng chờ" có mục tương ứng bên màn TA với đúng giờ mô phỏng; ngoài giờ nói chờ 08:00; quá hạn xử lý 30 phút sinh nhắc giảng viên trong nhật ký.
- **Chấm thử trên 2 kịch bản đắt nhất:** S3 đạt (1) preview chỉ bước đầu, đạt (2) chip BT3 + §3.5 mở đúng nguyên văn, đạt (3) gợi ý chưa duyệt thì không tồn tại bên TA. S4 đạt (1) không khẳng định đáp số, đạt (2) ngăn kéo §3.3 + ô cần xem lại + "Không có slide", đạt (3) Q-1043 thật bên màn TA, test +30 phút sinh nhắc giảng viên.
- **Lỗi còn lại:** bộ phân loại ca lạ có thể ghép nhầm kịch bản gần nghĩa (đã có đường an toàn khi không khớp); ngoài giờ TA không ai xử lý thật tới 08:00 — giới hạn đúng thiết kế và nói rõ trên biên nhận; thu hồi gợi ý không thu hồi nội dung học viên đã chép — nói rõ ngay trong thẻ duyệt.

## §7. Demo

- **Ca lạ nhận tại demo:** bộ phân loại từ khoá khớp kịch bản thì chạy flow đúng mức đã đặt; không khớp thì vào **đường an toàn**: chip "Không có căn cứ · dừng", nói thẳng "không đoán", hỏi lại một câu kèm lựa chọn, và nút chuyển TA (gửi ngay hay chờ duyệt theo mức `chuyen_TA`). Đã bấm thử ca ngoài phạm vi "đổi mật khẩu tài khoản trường" → từ chối hữu ích + chuyển TA; ca gần nghĩa "p-value buổi 7" → khớp S7, giới hạn một câu vì buổi chưa mở.
- **Sau ca lạ nhóm không đổi mức tự chủ:** đường an toàn đã tôn trọng mức `chuyen_TA` tự làm và luật cứng bài đang mở; chỉ bổ sung từ khoá nếu ca lạ lộ mẫu câu hỏi mới. **Phân công demo theo bảng thành viên:** Đàm Hồng Thái trình bày §1–§2 + `anh-1.png`; Vũ Lương Duy trình bày §3–§4 và trực tiếp trả lời ca lạ; Lê Quý Toàn trình bày §5–§6 + `anh-2.png` và trỏ HAX/PAIR 1–7 trên màn hình. Mỗi thành viên giải thích được phần có tên mình.