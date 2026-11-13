# Bài nộp LAB5 — T2 Giáo dục · Nhóm TTD

**Lớp:** L3B · **Bàn / zone:** E305 · **Track:** T2
**Repo nộp:** `K5-L3B-Day05-T2-TTD` — repo công khai của nhóm, không fork repo đề · nhánh nộp: `2A202603941_LeQuyToan`.

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| Đàm Hồng Thái | 2A202603927 | **Người kịch bản** (mạnh viết, suy luận rủi ro) — giữ §1–§2: lát cắt & phạm vi, 11 kịch bản rủi ro phủ đủ 4 lớp ①②③④, lập luận chọn 2 kịch bản đắt nhất S3/S4; dựng ảnh đánh số `anh-1.png` (màn học viên, ca S3 từ đầu tới thẻ duyệt) |
| Vũ Lương Duy | 2A202603945 | **Người quyết định** (mạnh lập luận, phản biện) — giữ §3–§4: khi AI sai người dùng thấy gì, quyết định hỏi lại / trả lời kèm giới hạn / chuyển người, loại lỗi, mức tự chủ theo cost-of-error, tool khó xếp nhất và thử mức; trả lời ca lạ tại demo (§7) |
| Lê Quý Toàn | 2A202603941 | **Người prototype** (mạnh công cụ, UI) — giữ §5–§6: dựng `prototype/index.html` màn học viên + màn TA với rail mức tự chủ áp dụng sống và nhật ký quyết định, kiểm thử bấm end-to-end desktop/tablet/mobile; dựng ảnh đánh số `anh-2.png` (màn TA); map HAX/PAIR 1–7 vào màn hình; tiêu chí Pass/Fail và chấm thử thiết kế |

## §1. Lát cắt & phạm vi

- **Lát cắt (chép từ track):** Trong **trợ lý học bài của trang khoá học (kiểu ChatGPT Study mode)**, khi **học viên** đang hỏi bài lúc tối muộn, khi không còn ai để hỏi, **AI giảng kèm trích tài liệu, hỏi lại cho rõ, gợi ý từng bước, hay nói thẳng "tài liệu không có, hỏi giảng viên"**, để học viên hiểu đúng bài mình đang học, không chép đáp án, không học sai mà không biết.
- Ba việc nhóm quyết định không làm:
  1. **Không đưa đáp án, cũng không xác nhận đáp án bài đang mở.** Bài 3 còn mở tới 23:59 hôm nay (Data B). Học viên chép rồi thì không rút lại được, còn giảng viên mất tín hiệu đánh giá thật. Trên prototype, nhóm để chip "Luật cứng · bài đang mở" và không làm bất kỳ nút nào đưa đáp số — bấm thử S3, S5, S6 sẽ thấy.
  2. **Không nhận xét năng lực người học.** Kể cả lời nghe như động viên ("bạn làm được mà", "đừng tự ti") thì vẫn là phán xét, và kiểu hại niềm tin này không sửa được bằng một câu xin lỗi. Trong S6, trợ lý trả lời thẳng vào việc học, không đụng gì tới câu tự chê của học viên.
  3. **Không nói đã làm việc mình không làm được, không nói về nguồn không có.** Tài liệu chỉ có §3.1–§3.5 (Data A), nên "slide 12" là nguồn không tồn tại; "đã báo TA" khi chưa chuyển cũng vậy. Prototype xử lý ở S4 (nói thẳng không có slide đánh số) và S10 (nói thẳng không có tool nộp bài); biên nhận "đã vào hàng chờ" chỉ hiện khi bên màn TA thật sự có mục đó.

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

**Vì sao S3 và S4 là hai ca đắt nhất:**

- S3: hại không đảo được, lại rơi đúng lúc người học dễ thỏa hiệp nhất. Còn hơn một tiếng là tới hạn, học viên chỉ cần một chữ "đúng" là chép xong. Một lần xác nhận sai vừa phá mục đích học tập, vừa làm hỏng tín hiệu đánh giá của cả khoá. Ca này diễn ra trong chat riêng, không có hàng chờ duyệt nào đỡ hộ, nên thiết kế phải tự chặn.
- S4: hại âm thầm và có đường khuếch đại. Câu sai nằm ngay trong tài liệu chính thống (§3.3); nếu trợ lý gật đầu "tài liệu đúng", học viên học sai mà không biết, và câu đó lên FAQ thì cả lớp sai theo. Thêm nữa, nguồn "slide 12" không tồn tại, nên mọi trích dẫn bám theo nó đều là bịa.

**Suýt chọn S5** (đăng FAQ kèm đáp án bài mở). Cuối cùng không chọn vì S5 còn lưới thứ hai: bản nháp FAQ phải qua TA duyệt trước khi đăng, tức là thiết kế chặn được ở cổng duyệt. S3 thì không có lưới nào ngoài chính thiết kế, còn S4 đánh vào nguồn sự thật chứ không chỉ vào hành vi. S5 vẫn được giữ làm kịch bản thử mức của `dang_FAQ`.

## §3. Khi AI sai (chặng 3)

### S3 — xin xác nhận đáp số bài đang mở

**AI nói nguyên văn:**

- "Bài tập 3 **đang mở** — hạn 23:59 hôm nay (trang khoá học). Mình **không đưa và không xác nhận đáp số** bài đang mở, kể cả khi bạn đã ra con số của riêng bạn. Xác nhận lúc này là giúp bạn nộp một con số mình chưa kiểm chứng."
- "Mình có thể gửi **gợi ý bước đầu** để bạn tự kiểm tra trong thời gian còn lại. Gợi ý chỉ hướng làm, không chứa đáp số."
- Thẻ duyệt: "**AI SOẠN SẴN — CHƯA GỬI**" + nguyên văn gợi ý: "Bước 1 (câu a): sắp xếp 8 giá trị tăng dần rồi xác định hai vị trí giữa (§3.2); trung bình lấy tổng chia cho số giá trị (§3.1). Bước 2 (câu b): xem giá trị cao nhất kéo trung bình thế nào so với trung vị (§3.1, §3.4) — và tự hỏi đó là lỗi nhập liệu hay dữ liệu thật trước khi bỏ (§3.4). Không đáp số, không xác nhận con số của bạn." + "Người duyệt: **bạn**. Nếu gợi ý quá tay rồi bạn chép thì không thu hồi được, nên bạn đọc nguyên văn trước khi bấm. Bước duyệt không phải lớp chặn rò rỉ — người duyệt cũng là người muốn đáp án; lớp chặn thật là luật cứng "preview không chứa đáp số"." Nút: "Duyệt & nhận gợi ý" / "Không cần, mình tự làm".

**Người dùng thấy gì:** chip "Luật cứng · bài đang mở" ngay trên tin; dòng "Dựa vào: BT3 · đang mở, §3.5" bấm được để mở ngăn kéo nguyên văn; thẻ gợi ý nằm ở trạng thái CHƯA GỬI với preview đầy đủ; đồng hồ ngữ cảnh báo "còn 1 giờ 12 phút" để học viên quyết trong thời gian thật.

**Làm gì tiếp:** duyệt để nhận gợi ý bước đầu (duyệt xong có nút Thu hồi), hoặc tự làm, hoặc bấm đường gặp TA. Không tồn tại nút nào xác nhận con số 15.25.

**Ai được báo, sau bao lâu:** tách theo từng nút bấm cho rõ. Chưa bấm gì thì chưa ai bị báo — gợi ý chưa gửi tức là chưa tồn tại với hệ thống. Bấm "Duyệt & nhận gợi ý" thì gợi ý vào chat của chính học viên, không báo TA; có nút Thu hồi, nhưng nội dung đã đọc hoặc chép thì không lấy lại được — thẻ nói thẳng điều đó. Bấm chuyển TA thì mục vào hàng chờ ngay, biên nhận có mã thật; lúc 22:47 TA ngoài giờ nên chờ 08:00 sáng mai, tức là sau hạn 23:59 — biên nhận kèm dòng "Lưu ý: 08:00 sáng mai là sau hạn Bài 3 (23:59 hôm nay) — mình không hứa có trả lời trước hạn.", không hứa suông. Mục nào quá 30 phút chưa xử lý trong giờ TA sẽ bị nhắc giảng viên trong nhật ký, và bên màn TA hiện pill "Quá hạn".

**Nhóm đã cân nhắc những gì:** thật ra có bốn đường. Xác nhận hoặc giải luôn thì bị loại đầu tiên, vì phạm luật cứng và hại không đảo được. Hỏi lại "em muốn hỏi gì?" nghe an toàn, nhưng câu hỏi đã rõ rồi — hỏi lại chỉ đốt mất thời gian còn một tiếng và là cách né trách nhiệm. Từ chối cụt ngủn cũng không xong: học viên đang kẹt lúc 22:47 sẽ đi chép chỗ khác, mất luôn cơ hội giúp hợp lệ. Đường nhóm chọn là dừng, trả lời kèm giới hạn, rồi đưa gợi ý có duyệt — vừa giữ luật, vừa không bỏ rơi người học.

**Loại lỗi:** đây là lỗi ngữ cảnh, không phải lỗi câu chữ. Cùng câu hỏi đó nhưng rơi vào Bài 2 đã hết hạn thì được giải đầy đủ (S9 chứng minh). Cái sai nằm ở trạng thái khoá học — bài đang mở, lại gần hạn — nên cách sửa là đổi hành vi theo trạng thái Data B (đang mở / hết hạn / đã công bố đáp án), chứ không phải gọt lại lời văn. Một phần S3 cũng là lỗi người dùng: học viên xin đáp số vì sắp hết hạn chứ không phải hệ thống hỏng — nên cách nói không đổ lỗi, không giảng đạo đức, nêu thẳng giới hạn rồi mở đường hợp lệ (gợi ý bước đầu, chuyển TA kèm giờ thật).

**HAX/PAIR nằm ở đâu:** số 1 (G1+G2) — nhãn "Trợ lý AI" kèm chip "Luật cứng · bài đang mở" nói rõ giới hạn thay vì hứa suông; số 2 (G11 + PAIR Explainability) — dòng "Dựa vào" mở ngăn kéo trích nguyên văn BT3 và §3.5 cho học viên tự kiểm; số 4 (G8+G9) — thẻ duyệt trước khi gửi, nút Thu hồi sau duyệt, và sửa được ngay trên thẻ.

**Có lỗi mà sửa câu chữ không cứu được:** rò đáp số. Lời văn khéo đến mấy mà buông con số 15.25 hoặc một chữ "đúng" là hỏng. Thiết kế cứu bằng cách tách `goi_y_bai_tap` thành hai bước soạn-sẵn (không gửi) và gửi-đi (phải duyệt), preview không chứa đáp số, và không làm nút xác nhận đáp số bài mở ở bất kỳ mức tự chủ nào.

### S4 — nguồn không có + câu sai trong tài liệu

**AI nói nguyên văn:**

- "Tài liệu buổi 3 **không có slide đánh số** — mình không tìm thấy "slide 12". Ý bạn nhắc nằm ở **§3.3**."
- "Câu "độ lệch chuẩn luôn nhỏ hơn phương sai" **cần xem lại**: nó chỉ đúng khi phương sai ≥ 1. Phản ví dụ: phương sai 0.25 → độ lệch chuẩn √0.25 = 0.5, **lớn hơn**. Dữ liệu chuẩn hoá [0,1] thường có phương sai < 1 nên bạn thấy ngược lại là có cơ sở."
- "Mình **không khẳng định tài liệu đúng hay sai** khi chưa kiểm — bạn nên báo giảng viên." Câu tiếp theo đổi theo mức của việc chuyển TA đang đặt: mức tự làm thì nói "Mức của việc chuyển TA hiện là **tự làm**, nên mục đã vào hàng chờ TA ngay (mã ở thẻ bên dưới), không cần bạn bấm duyệt."; mức cần duyệt thì nói "Mức của việc chuyển TA hiện là **cần người duyệt** — báo cáo kèm cờ nghi lỗi tài liệu nằm ở thẻ bên dưới; bạn bấm duyệt thì mục mới vào hàng chờ TA." Đổi mức trên rail là câu này đổi theo, không hứa một đằng làm một nẻo.
- Biên nhận (mức tự làm của `chuyen_TA`): "**ĐÃ VÀO HÀNG CHỜ TA** · Mã: Q-1043 · 22:47 · trạng thái: Ngoài giờ TA · chờ 08:00. TA không trực lúc này (giờ TA 08:00–22:00). Câu hỏi chờ tới 08:00 sáng mai; mình không hứa trả lời ngay. TA sẽ thấy kèm tóm tắt + căn cứ, bạn không phải kể lại."

**Người dùng thấy gì:** chip "Có căn cứ · tài liệu cần kiểm"; dòng "Dựa vào: Không có slide, §3.3" — ngăn kéo §3.3 hiện nguyên văn câu sai kèm ô "cần xem lại" và phản ví dụ; biên nhận hàng chờ với mã thật và giờ TA thật; nút "Xem phía TA" mở màn hàng chờ để tự kiểm lời hứa.

**Làm gì tiếp:** xem mục Q-1043 bên màn TA (có cờ "nghi lỗi tài liệu §3.3"); chờ TA 08:00 hoặc hỏi giảng viên; bấm "Sai chỗ nào?" nếu phần phản ví dụ chưa đúng ý mình.

**Ai được báo, sau bao lâu:** TA nhận ngay vào hàng chờ kèm cờ nghi lỗi; ngoài giờ thì TA thấy lúc 08:00 (nói rõ trên biên nhận, không hứa trả lời ngay); quá 30 phút không xử lý thì nhắc giảng viên. Giảng viên là người duy nhất có thẩm quyền kết luận tài liệu đúng/sai.

**Nhóm đã cân nhắc những gì:** khẳng định tài liệu đúng hay khẳng định tài liệu sai luôn đều bị loại, vì cùng là một lỗi bịa khi chưa kiểm — chỉ khác chiều. Chỉ nói "không có slide" rồi dừng cũng không xong, vì bỏ rơi câu sai §3.3 thì học viên vẫn học sai âm thầm. Nhóm chọn trả lời kèm giới hạn, đưa phản ví dụ, và chuyển người có cờ — phần kết luận đúng/sai để giảng viên, vì đó là thẩm quyền của họ.

**Loại lỗi:** lỗi nguồn sự thật (hệ thống). Dữ liệu cấp chứa mệnh đề sai và người học nhắc nguồn không tồn tại; cách sửa là kiểm căn cứ, nói rõ chỗ cần kiểm, và chuyển người có thẩm quyền sửa tài liệu — không phải xin lỗi hay hỏi lại người học. S4 còn kiêm lỗi ngữ cảnh: mệnh đề trong §3.3 không sai với mọi dữ liệu, nó sai với dữ liệu chuẩn hoá [0,1] của học viên (phương sai < 1) — nên sửa câu chữ AI chưa đủ, phải có cờ nghi lỗi tới giảng viên để sửa tận gốc tài liệu.

**HAX/PAIR nằm ở đâu:** số 2 (G11 + PAIR Explainability) — ngăn kéo §3.3 nguyên văn + ô "cần xem lại" để học viên tự thấy mệnh đề và phản ví dụ; số 5 (PAIR Errors + Graceful Failure) — biên nhận chuyển TA kèm tóm tắt, cờ và giờ trực thật, không hứa suông; số 6 (G15) — "Sai chỗ nào?" mở ô góp ý ngay trong tin, góp ý vào nhật ký.

**Có lỗi mà sửa câu chữ không cứu được:** câu sai trong tài liệu. Lời AI không sửa được §3.3; thiết kế cứu bằng cờ nghi lỗi gửi giảng viên qua hàng chờ, và bằng mức duyệt của `dang_FAQ`: câu chưa kiểm không được lên FAQ cho cả lớp.

## §4. Mức tự chủ (chặng 4)

| Tool | Mức của nhóm | Ai duyệt · thấy gì · quá hạn | Lý do theo cost-of-error | Phương án đã cân nhắc và loại |
|---|---|---|---|---|
| `tra_cuu_tai_lieu` | Tự làm | — | Chỉ đọc; sai thì rẻ và học viên tự thấy ngay nhờ ngăn kéo nguyên văn; chờ người thì kẹt lúc 23h mà không giảm hại | Cần duyệt: loại vì chặn mọi câu trả lời, học viên chờ vô ích. Cấm: loại vì mất căn cứ, AI lại bịa |
| `goi_y_bai_tap` | Cần người duyệt | **Học viên** duyệt; thấy nguyên văn gợi ý + cảnh báo "chép rồi thì không thu hồi được"; quá hạn không tự gửi — thẻ nằm chờ, học viên bỏ qua thì thôi | Gợi ý quá tay thì học viên đã chép — không đảo được (S3, S6); chờ duyệt chỉ tốn một nút bấm của chính người chịu hại | Tự làm + hoàn tác: loại vì hoàn tác vô nghĩa với nội dung đã đọc/chép. Cấm hẳn: loại vì mất giúp đỡ hợp lệ lúc kẹt, học viên đi chép nơi khác |
| `chuyen_TA` | Tự làm | — | Đảo được; chuyển thừa chỉ tốn công TA; chờ duyệt thì mất đường thoát duy nhất sang người lúc ngoài giờ; đổi lại phải nói thật giờ có người nhận | Cần duyệt: loại vì việc rẻ và đảo được mà bắt bấm thêm. Cấm: loại vì Study mode gốc không có ai để chuyển — đây chính là chỗ phải thiết kế |
| `dang_FAQ` | Cần người duyệt | **TA** duyệt; thấy bản nháp + căn cứ + cờ nghi lỗi; quá hạn 30 phút trong giờ TA → nhắc giảng viên; ngoài giờ TA → chờ 08:00, không tự đăng (không duyệt = không đăng; cái giá: FAQ lên chậm tới sáng, chấp nhận vì FAQ không gấp như bài nộp) | Gỡ được nhưng cả lớp đã đọc — hại lan rộng không thu hồi (S4, S5); chờ TA duyệt rẻ hơn một lần cả lớp học sai | Tự làm + gỡ: loại vì gỡ không cứu người đã đọc. Cấm: loại vì mất kênh chia sẻ câu hỏi hay |

**Tool khó xếp nhất là `goi_y_bai_tap`, và nhóm cãi nhau đúng chỗ này.** Lê Quý Toàn (người prototype) chọn *tự làm + hoàn tác* cho nhanh lúc 22:47; Vũ Lương Duy (người quyết định) chọn *cấm* với bài đang mở cho an toàn tuyệt đối; Đàm Hồng Thái (người kịch bản) chọn *cần người duyệt*. Cái giá mỗi phía đều trỏ về §2: tự làm thì S3/S6 rò đáp án không đảo được, và hoàn tác vô nghĩa với nội dung đã đọc hoặc chép; cấm thì S6 học viên kẹt không còn giúp đỡ hợp lệ, đi chép nơi khác; duyệt thì thêm một bấm, nhưng người chịu hại được đọc nguyên văn trước khi nhận. Có một phương án nữa là để TA duyệt — nhóm bỏ, vì TA chỉ trực 08:00–22:00 mà học viên cần lúc 22:47, hạn 23:59: chờ TA là chờ vô ích, thành ra tương đương cấm. Chốt lại: cần người duyệt là chính học viên, kèm tách bước và luật cứng dưới đây; rail cho đổi mức sống để demo thấy cái giá của từng phía. Nhóm cũng thừa nhận giới hạn: người duyệt là chính học viên nên bước duyệt không chặn được ý định chép — nó chỉ giúp học viên đọc nguyên văn và tự chọn, còn chặn rò rỉ là luật cứng "preview không chứa đáp số". Học viên vẫn có thể xin đáp số ở nơi khác; thiết kế không giải quyết được điều đó.

**Thử mức đã đặt trên S3, S4 và S1:**

- *Cái sai có bị chặn không?* S3: không tồn tại nút xác nhận đáp số; gợi ý chỉ bước đầu và phải duyệt mới gửi. S4: câu chưa kiểm không tự lên FAQ; báo cáo nghi lỗi tới TA kèm cờ.
- *Còn việc nào làm khi lẽ ra phải hỏi?* Không: mọi hành động gửi đi hoặc qua duyệt (gợi ý, FAQ) hoặc nằm ở tool đảo được (chuyển TA, chỉ đọc).
- *Người dùng bình thường có phải chờ vô ích?* Không: S1 và S9 được trả lời ngay bằng `tra_cuu_tai_lieu` tự làm, kèm căn cứ bấm được.

**Luật thêm / tách bước:** tách `goi_y_bai_tap` thành soạn-sẵn (tự làm, không gửi) và gửi-đi (phải duyệt) — phần soạn không hại ai, phần gửi mới hại. Luật cứng: bài đang mở thì không đáp số kể cả trong gợi ý và FAQ; bài đã hết hạn và đã công bố đáp án thì giải thích đầy đủ (S9); hạn nộp chỉ lấy từ trang khoá học (S8).

**Lời hứa đã đổi theo mức:** `goi_y_bai_tap` ở mức duyệt đổi lời hứa từ "mình gửi gợi ý cho bạn" thành "mình soạn sẵn — bạn duyệt thì mới gửi": chậm hơn một nhịp, nhưng người chịu hại được quyền quyết. `chuyen_TA` tự làm kèm lời hứa mới: "không hứa trả lời ngay ngoài giờ — biên nhận nói rõ chờ 08:00", thay cho lời hứa suông "đã báo TA".

## §5. Prototype (chặng 5)

- **File:** `prototype/index.html` — một file HTML thuần, mở trực tiếp bằng trình duyệt, không cần server. Deep-link cho demo: `#run=S3`, `#run=S4`, `#ta`. **Công cụ:** HTML/CSS/JS thuần + coding agent. **Mock:** toàn bộ lời AI là kịch bản dựng chạy theo trạng thái; bộ phân loại ca lạ bằng từ khoá; không có lời gọi AI thật (không nhận bonus +3), không API key trong code. Màn TA (hàng chờ câu được chuyển) là bonus của track. Dữ liệu đúng Data A/Data B của track, toàn bộ dựng.
- **Ảnh đánh số:** `prototype/anh-1.png` (màn học viên, ca khó S3 bấm từ đầu tới thẻ duyệt) và `prototype/anh-2.png` (màn TA: hàng chờ, cờ nghi lỗi, cổng duyệt FAQ). Chú thích đủ 1–7 nằm ở rail "Chú thích HAX / PAIR", bật/tắt bằng công tắc; số in ngay trên màn hình:
  | Số | Thể hiện gì | Nguyên tắc | Mức tự chủ liên quan |
  |---|---|---|---|
  | 1 | Nhãn "Trợ lý AI" + chip độ chắc định tính trên mỗi tin (anh-1: chip "Luật cứng · bài đang mở") | G1 + G2 | mọi mức — nói rõ giới hạn |
  | 2 | Dòng "Dựa vào" bấm được, mở ngăn kéo trích nguyên văn tài liệu / trang khoá học (anh-1: BT3 · đang mở, §3.5; S4: §3.3 + ô cần xem lại) | G11 + PAIR Explainability | `tra_cuu_tai_lieu` tự làm |
  | 3 | Thẻ hỏi lại một câu khi mơ hồ (chạy S2 hoặc ca lạ để thấy) | G10 | ngưỡng tự tin quyết định hỏi hay đoán-có-báo |
  | 4 | Thẻ duyệt trước khi gửi + nút thu hồi + sửa trên thẻ (anh-1: "AI SOẠN SẴN — CHƯA GỬI", "Duyệt & nhận gợi ý") | G8 + G9 | `goi_y_bai_tap` cần duyệt |
  | 5 | Đường chuyển người thật kèm tóm tắt; biên nhận nói rõ giờ TA (S4: Q-1043 chờ 08:00; anh-2: hàng chờ) | PAIR Errors + Graceful Failure | `chuyen_TA` tự làm |
  | 6 | "Sai chỗ nào?" mở ô góp ý ngay trong tin; góp ý vào nhật ký (anh-1: hàng góp ý dưới tin) | G15 | mọi mức |
  | 7 | Thẻ "Mình làm được / không làm" ở cột ngữ cảnh (anh-1, cột KHOÁ HỌC) | G1 | phạm vi nhìn thấy trước khi hỏi |
- **Vì sao hiện theo cách này (nhóm đã nghĩ cách khác):**
  - *Độ chắc:* nhóm định hiện con số %, nhưng bỏ — % cho cảm giác chính xác giả mà không kiểm chứng được, trái G2. Thay bằng chip định tính: "Chắc chắn · có căn cứ", "Chưa chắc · hỏi lại", "Không có căn cứ · dừng", "Luật cứng".
  - *Bằng chứng:* ngăn kéo trích nguyên văn mở từ chip. Inline dài thì chat ngập và không tách được lời AI khỏi nguồn; tooltip thì không đọc được trên mobile — cả hai đều bị loại.
  - *Điều khiển mức tự chủ:* rail luôn hiện (4 select mức + ngưỡng tự tin + hạn xử lý + giờ mô phỏng). Nhóm bỏ modal cài đặt vì TA và demo cần đổi mức giữa ca và thấy hiệu ứng ngay trên thẻ đang mở.
  - *Thẻ duyệt:* nằm trong luồng chat, cạnh lời hứa nó chặn. Popup bị loại vì người duyệt phải đọc cùng ngữ cảnh câu trả lời; việc cấm thì không có nút làm ở mọi mức.

## §6. Tốt là gì (chặng 6 — nhẹ)

**Ba tiêu chí Pass/Fail, chấm được không cần tranh luận:**

1. **Không rò đáp số bài đang mở:** quét mọi tin nhắn, preview gợi ý và nháp FAQ của ca bài mở — không chứa đáp số BT3, không xác nhận đúng/sai con số của học viên.
2. **Mọi khẳng định nội dung có căn cứ mở được:** mỗi tin trả lời nội dung có ít nhất một chip mã mục mở ngăn kéo đúng nguyên văn Data A/B; chỗ không căn cứ phải nói "không có" (S4 "slide 12", S8 hàm Excel, S7 tài liệu buổi 7).
3. **Lời hứa trạng thái khớp hệ thống:** mọi biên nhận "đã vào hàng chờ" có mục tương ứng bên màn TA với đúng giờ mô phỏng; ngoài giờ nói chờ 08:00; quá hạn xử lý 30 phút sinh nhắc giảng viên trong nhật ký.

**Chấm thử trên hai ca đắt nhất:** S3 đạt (1) vì preview chỉ bước đầu, đạt (2) vì chip BT3 + §3.5 mở đúng nguyên văn, đạt (3) vì gợi ý chưa duyệt thì không tồn tại bên TA. S4 đạt (1) vì không khẳng định đáp số, đạt (2) vì ngăn kéo §3.3 + ô cần xem lại + "Không có slide", đạt (3) vì Q-1043 thật bên màn TA, và test +30 phút sinh nhắc giảng viên.

**Lỗi còn lại, nhóm biết và chấp nhận có kiểm soát:** bộ phân loại ca lạ có thể ghép nhầm kịch bản gần nghĩa (đã có đường an toàn khi không khớp); ngoài giờ TA không ai xử lý thật tới 08:00 — giới hạn đúng thiết kế và nói rõ trên biên nhận; thu hồi gợi ý không thu hồi nội dung học viên đã chép — nói rõ ngay trong thẻ duyệt.

## §7. Demo

- **Ca lạ nhận tại demo:** bộ phân loại từ khoá khớp kịch bản thì chạy flow đúng mức đã đặt; không khớp thì vào đường an toàn: chip "Không có căn cứ · dừng", nói thẳng "không đoán", hỏi lại một câu kèm lựa chọn, và nút chuyển TA (gửi ngay hay chờ duyệt theo mức `chuyen_TA`).
- **Bốn ca lạ nhóm đã bấm thử, ghi lại đúng những gì màn hình hiện:** "đổi mật khẩu tài khoản trường" → từ chối hữu ích + chuyển TA, không hứa can thiệp tài khoản; "p-value buổi 7" → khớp S7, giới hạn một câu vì buổi chưa mở, không gửi tài liệu không tồn tại; "Cô xác nhận giúp em là em đã hiểu bài chưa ạ" → không chứng nhận đã hiểu, không nhận xét năng lực: "Mình **không thể xác nhận** bạn đã hiểu hay chưa, và mình không đánh giá năng lực của bạn.", gợi ý tự giải thích lại bằng lời mình rồi đối chiếu §3.1–§3.2, kèm nút chuyển TA cho ai muốn người thật xác nhận; "bài 3 em tính ra 15.25, đúng chưa" → bộ phân loại bắt đúng S3 dù câu không có chữ "xác nhận", thẻ duyệt mở như thường, và quét mọi tin AI của ca không thấy con số 15.25 — số của học viên không bị nhắc lại, càng không bị gật đầu.
- **Sau ca lạ nhóm không đổi mức tự chủ:** đường an toàn đã tôn trọng mức `chuyen_TA` tự làm và luật cứng bài đang mở; chỉ bổ sung từ khoá nếu ca lạ lộ mẫu câu hỏi mới.
- **Phân công demo theo bảng thành viên:** Đàm Hồng Thái trình bày §1–§2 + `anh-1.png`; Vũ Lương Duy trình bày §3–§4 và trực tiếp trả lời ca lạ; Lê Quý Toàn trình bày §5–§6 + `anh-2.png` và trỏ HAX/PAIR 1–7 trên màn hình. Mỗi thành viên giải thích được phần có tên mình.