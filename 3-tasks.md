# Phân công công việc — Nhóm 3 người · Track T2 Giáo dục

> **Nguyên tắc:** Guide nói rõ — **chặng 1–4 cả nhóm cùng làm thì tốt hơn**; từ chặng 5 mỗi người giữ phần mình. Mỗi người **phải giải thích được phần có tên mình** (vibe-coding rule: không giải thích được → 0đ phần đó ở R7). Ba người cần **cùng đọc `t2-education.md`** trước khi bắt đầu.
>
> **Phân vai theo thế mạnh** (nhóm có thể đổi tên):
> - **A — "Người kịch bản"**: mạnh viết, suy luận rủi ro → giữ §1–§2, dựng ảnh 1.
> - **B — "Người quyết định"**: mạnh lập luận, phản biện → giữ §3–§4, trả lời ca lạ.
> - **C — "Người prototype"**: mạnh công cụ, UI → giữ §5–§6, dựng ảnh 2, map HAX.

---

## 1. Bảng phân công tổng (theo 6 chặng)

| Chặng | Phút | Việc chính | A | B | C | Cùng làm |
|---|---|---|---|---|---|---|
| **1 · Đọc đề** | 10 | Đọc `t2-education.md`, chốt lát cắt + phạm vi | ✍️ viết §1 | 🔍 phản biện §1 | 📖 đọc tool + data | ✅ cả 3 đọc file track, chốt lát cắt |
| **2 · Kịch bản** | 35 (M1) | ≥8 kịch bản phủ 4 lớp, chọn 2 đắt nhất | ✍️ **chủ** §2 | 🔍 **phản biện**: mỗi kịch bản có trỏ tool/data chưa? | 🗂️ **gắn nhãn** mức hại + kiểm tra phủ 4 lớp | ✅ cùng brainstorm 8 kịch bản |
| **3 · UX khi AI sai** | 45 | 2 kịch bản đắt: verbatim + UI + ai báo + HAX | 🔍 phản biện "phương án loại" | ✍️ **chủ** §3 | 🎨 **phác UI** cho từng bước (để §5 dùng) | ✅ cùng chốt câu AI nói nguyên văn |
| **4 · Mức tự chủ** | 35 (M2) | Mức cho mọi tool + tool khó xếp + thử 3 kịch bản | 🔍 **phản biện** cost-of-error | ✍️ **chủ** §4 | 📊 **bảng so sánh** mức + test 3 kịch bản | ✅ **mỗi người tự xếp mức 5' trước** rồi so |
| **Nghỉ** | 15 | | | | | |
| **5 · Prototype** | 60 (M3) | 1–2 màn, bấm ca khó, HAX trỏ ảnh | 🖥️ **dựng ảnh 1** (chat + badge + báo TA) | 🧪 **test bấm** ca khó #2, #4 | 🖥️ **dựng ảnh 2** (quiz + chuyển TA) + **map HAX/PAIR vào ảnh đánh số** | ✅ cùng bấm thử toàn bộ trước M3 |
| **6 · Tốt là gì** | 10 | 3 tiêu chí Pass/Fail + chấm thử | ✍️ viết tiêu chí | 🔍 chấm thử #4 | 🔍 chấm thử #2 | ✅ cùng chốt |
| **Demo** | 30 | Mỗi người một phần + ca lạ | 🎤 lát cắt + ca khó #4 | 🎤 mức tự chủ + ca lạ | 🎤 HAX trỏ ảnh + ca khó #2 | ✅ cùng trả lời "sai thì ai mất gì" |

---

## 2. Phân công chi tiết theo từng người

### 🅰️ Người A — "Người kịch bản" (viết §1–§2, dựng ảnh 1)

**Trước giờ lab (chuẩn bị):**
- [ ] Đọc `t2-education.md` **trước** — ghi chú: lát cắt nguyên văn, 5 tool, 3 tin mồi, dữ liệu tài liệu buổi học.
- [ ] Đọc `01-challenge-brief.md` mục T2 + `02-guide.md` §1–§2.

**Trong lab — chặng 1–2:**
- [ ] Viết **§1** vào `spec.md`: lát cắt nguyên văn + 3 việc KHÔNG làm (mỗi việc một câu lý do, trỏ về track).
- [ ] Viết **≥8 kịch bản** vào §2 — mỗi dòng đủ 5 cột: `tin người dùng | lớp | AI có thể sai thế nào | sản phẩm tốt nên làm gì | nhãn`.
- [ ] Đảm bảo **mỗi kịch bản trỏ về 1 tool hoặc 1 dòng data cụ thể** (tài liệu buổi học) — nhờ B phản biện.
- [ ] Viết **lập luận chọn 2 kịch bản đắt nhất** (#4 overfitting, #2 đưa đáp án) + **kịch bản suýt được chọn** + vì sao không.
- [ ] **Show M1** (phút 45) cho TA: ≥8 kịch bản + 2 đắt nhất.

**Chặng 3–4:** phản biện §3–§4 của B (đặc biệt cột "phương án đã loại" — A kiểm tra xem có thật sự "đã loại" hay chỉ liệt kê).

**Chặng 5:** dựng **ảnh 1** — màn hình chat "Hỏi bài":
- [ ] Câu trả lời AI + badge xanh/vàng.
- [ ] Khung "Nguồn" hiện đoạn trích + số slide.
- [ ] Nút "Báo TA câu trả lời này".
- [ ] Nút "Làm lại từ đầu" (cho kịch bản #2).
- [ ] Chụp ảnh, đánh số 1–4, ghi chú mỗi số thể hiện HAX/PAIR nào + mức tự chủ nào.

**Chặng 6 + Demo:**
- [ ] Viết 3 tiêu chí Pass/Fail (§6).
- [ ] Demo: 30s lát cắt + bấm ảnh 1 qua ca khó **#4** (hỏi overfitting → badge vàng → báo TA).

**Câu A phải trả lời được:** *"Kịch bản #4 trỏ vào tool nào, dòng data nào? Vì sao đắt hơn #3?"*

---

### 🅱️ Người B — "Người quyết định" (viết §3–§4, trả lời ca lạ)

**Trước giờ lab:**
- [ ] Đọc `t2-education.md` — tập trung bảng tool + Hard tests.
- [ ] Đọc `02-guide.md` §3–§4 + `04-rubric.md` khối R3–R4 (50đ — nặng nhất).
- [ ] Đọc tham khảo Study Mode công khai (link OpenAI) — ghi chú "không làm hộ", "có thể quay lại trả lời trực tiếp".

**Trong lab — chặng 3–4:**
- [ ] Viết **§3** cho 2 kịch bản đắt nhất:
  - Câu AI nói **nguyên văn** (không mô tả).
  - Cái người dùng thấy (badge, nút, khung nguồn).
  - Bước tiếp theo + ai báo, sau bao lâu.
  - **Lập luận chọn cách** (hỏi lại / kèm giới hạn / chuyển người) + **phương án đã loại + vì sao**.
  - **Loại lỗi** (hệ thống / người dùng / ngữ cảnh) + cách sửa theo loại.
  - **2–3 HAX/PAIR** trỏ chỗ cụ thể.
  - **1 lỗi sửa câu chữ không cứu được** + thiết kế cứu.
- [ ] Viết **§4**:
  - Bảng mức cho **5 tool** + lý do cost-of-error (sai ai chịu gì · đảo được không · chờ người mất gì).
  - **Tool khó xếp nhất** (`giai_thich_theo_buoc`) — mỗi người từng chọn gì, cái giá mỗi phía trỏ về kịch bản §2, cách chốt.
  - **Thử mức trên 3 kịch bản** (#4, #2, bình thường) theo 3 câu: cái sai có bị chặn · còn làm khi lẽ ra phải hỏi · người dùng bình thường có phải chờ vô ích.
  - **Một mức tự chủ đã đổi lời hứa** nào.
- [ ] **Show M2** (phút 125) cho TA: bảng mức + tool khó xếp + thử 3 kịch bản.

**Chặng 5:** **test bấm** prototype của A và C qua ca khó #2 và #4 — kiểm tra đúng mức tự chủ đã đặt (§4).

**Chặng 6 + Demo:**
- [ ] Chấm thử #4 trên 3 tiêu chí Pass/Fail.
- [ ] Chuẩn bị **trả lời ca lạ**: "Học viên xin AI xác nhận đã hiểu" → AI từ chối mềm + `ra_quiz_kiem_tra` + `chuyen_TA`.
- [ ] Demo: mức tự chủ (`giai_thich_theo_buoc` khó xếp nhất) + bấm ảnh 1 qua ca khó #2 + trả lời ca lạ.

**Câu B phải trả lời được:** *"`giai_thich_theo_buoc` sai thì ai mất gì, vì sao nó ở mức 'tự làm có ràng buộc' chứ không phải 'cần TA duyệt'?"*

---

### 🅲 Người C — "Người prototype" (viết §5–§6, dựng ảnh 2, map HAX)

**Trước giờ lab:**
- [ ] Đọc `t2-education.md` — tập trung data & fixture (tài liệu buổi học).
- [ ] Đọc `02-guide.md` §5 + xem `prototype-sample/index.html` **3 phút** (mẫu T3 — chỉ để biết "đủ" trông thế nào).
- [ ] **Đăng ký tài khoản Lovable/v0.dev trước giờ lab** (guide nhắc rõ).
- [ ] Chuẩn bị sẵn khung HTML/Lovable rỗng để dựng nhanh.

**Trong lab — chặng 1–2:** đọc tool + data, giúp A **gắn nhãn mức hại** (nhẹ / sửa được / không chấp nhận được) và kiểm tra **phủ đủ 4 lớp** ①②③④.

**Chặng 3:** **phác UI** cho từng bước của 2 kịch bản đắt (để §5 dựng nhanh) — badge xanh/vàng, khung nguồn, nút báo TA, nút làm lại.

**Chặng 4:** làm **bảng so sánh mức** (5 tool × 3 mức) để B đối chiếu; chạy **test 3 kịch bản** trên giấy.

**Chặng 5 (chủ yếu):**
- [ ] Dựng **ảnh 2** — màn hình "Quiz tự kiểm tra":
  - Câu hỏi quiz (không đáp án hiện sẵn).
  - Sau khi trả lời: đúng/sai + giải thích có trích dẫn.
  - Nút "Chuyển TA".
- [ ] **Map mỗi HAX/PAIR vào ảnh đánh số** — bảng: `Nguyên tắc | Ảnh số | Chỗ cụ thể | Mức tự chủ`.
- [ ] Đảm bảo prototype **bấm qua được ca khó từ đầu tới cuối** (không can thiệp tay).
- [ ] Chụp ảnh đánh số, lưu vào `prototype/`.
- [ ] **Show M3** (phút 200) cho TA: bấm hết được + thấy ≥2 mức tự chủ + HAX trỏ được vào màn hình.
- [ ] (Bonus) Nếu kịp: gắn **1 lời gọi AI thật** đọc tin học viên chọn tool — **không để API key trong code**.

**Chặng 6 + Demo:**
- [ ] Chấm thử #2 trên 3 tiêu chí Pass/Fail.
- [ ] Demo: HAX/PAIR trỏ ảnh đánh số + bấm ảnh 2 qua ca khó #2.

**Câu C phải trả lời được:** *"Chỉ cho tôi chỗ nào trên màn hình là G2 / G10 / G11 — và nó thuộc mức tự chủ nào?"* (TA sẽ hỏi đúng câu này ở demo).

---

## 3. Việc cả nhóm cùng làm (không chia)

| Việc | Ai | Khi nào |
|---|---|---|
| Đọc `t2-education.md` + chốt lát cắt | Cả 3 | Đầu chặng 1 |
| Brainstorm 8 kịch bản | Cả 3 | Chặng 2 (A viết, B/C phản biện) |
| **Mỗi người tự xếp mức 5' trước khi bàn** | Cả 3 | Đầu chặng 4 (guide yêu cầu) |
| Chốt câu AI nói nguyên văn | Cả 3 | Chặng 3 |
| Bấm thử toàn bộ prototype trước M3 | Cả 3 | Cuối chặng 5 |
| Trả lời "sai thì ai mất gì" cho từng tool | Cả 3 | Trước demo |
| Kiểm tra repo + checklist nộp | Cả 3 | Trước 23:59 |

---

## 4. Checklist nộp — ai chịu trách nhiệm chính

| Hạng mục | Chịu trách nhiệm | Deadline |
|---|---|---|
| Repo `K5-<lớp>-Day05-T2-<tên nhóm>`, công khai, mở ẩn danh được | **C** (người prototype) | Trước 23:59 |
| `spec.md` §1–§2 | **A** | Cuối chặng 2 |
| `spec.md` §3–§4 | **B** | Cuối chặng 4 |
| `spec.md` §5–§6 + `prototype/` + ảnh đánh số | **C** | Cuối chặng 5 |
| Bảng thành viên + mã HV ở đầu `spec.md` | **A** | Đầu giờ |
| Log lời gọi AI (nếu có) + **không API key** | **C** | Cuối chặng 5 |
| Demo phân công + tập thử | Cả 3 | Trước demo 10' |

---

## 5. Ba câu cả nhóm phải trả lời được (TA hỏi ở demo)

1. **"Hành động này sai thì ai mất gì?"** — mỗi người trả lời cho tool mình phụ trách:
   - A: `giai_thich_theo_buoc` → học viên **học sai âm thầm**.
   - B: `chuyen_TA` / `danh_dau_chua_chac` → chậm, nhưng **không mất kiến thức**.
   - C: `ra_quiz_kiem_tra` → quiz sai, **không ảnh hưởng điểm thật**.
2. **"Lỗi nguy hiểm nhất là gì?"** — **#4** (AI giải thích sai khái niệm, badge xanh, học viên tưởng đúng). Cả 3 phải nói được.
3. **"Phần bạn làm là gì?"** — mỗi người chỉ đúng phần trong `spec.md` + ảnh prototype mình dựng.

---

## 6. Timeline gợi ý trong 240 phút

```
00:00–00:10  [Cả 3] Đọc t2-education.md, chốt lát cắt          → A viết §1
00:10–00:45  [Cả 3] Brainstorm 8 kịch bản                      → A viết §2, B/C phản biện
00:45        [A] Show M1 cho TA
00:45–01:30  [B viết §3] [A phản biện] [C phác UI]             → chốt verbatim
01:30–02:05  [Mỗi người tự xếp mức 5'] → [B viết §4] [C bảng] [A phản biện]
02:05        [B] Show M2 cho TA
02:05–02:20  Nghỉ
02:20–03:20  [A dựng ảnh 1] [C dựng ảnh 2 + map HAX] [B test bấm]
03:20        [C] Show M3 cho TA
03:20–03:30  [Cả 3] Viết §6 + chấm thử
03:30–04:00  [Cả 3] Tập demo + trả lời ca lạ
```

> **Lưu ý:** Nếu kẹt kỹ thuật prototype quá **20 phút** → **gọi TA** ngay (guide §5). Nếu hết giờ, **bỏ chặng 6** (mất tối đa 5đ) — **đừng cắt chặng 3–5** (75đ).
