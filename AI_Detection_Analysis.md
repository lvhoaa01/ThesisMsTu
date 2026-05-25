# Phân Tích Dấu Hiệu AI Can Thiệp giữa RpSug_backup (gốc) và RpSug (sau khi sửa bởi Codex)

> **Đối tượng phân tích:** So sánh `RpSug_backup_before_phases.md` (bản gốc) với `RpSug.md` (bản đã chỉnh sửa bởi agent Codex), đánh giá dưới góc nhìn cơ chế phát hiện AI của **Turnitin AI Writing Detection**.
>
> **Ngày phân tích:** 2026-05-25

---

## 1. Cơ Chế Phát Hiện AI Của Turnitin (Bối Cảnh)

Turnitin AI Detection hoạt động dựa trên 3 trụ cột chính:

1. **Perplexity (độ bất ngờ)** – đo lường mức độ "dễ đoán" của từ tiếp theo trong câu. Văn bản AI có perplexity **thấp** vì mô hình chọn token có xác suất cao nhất.
2. **Burstiness (độ biến thiên)** – đo độ chênh lệch về độ dài câu và cấu trúc. Văn bản người viết có burstiness **cao** (câu dài/ngắn xen kẽ), AI viết thì **đều đặn**.
3. **Sentence-level classification** – phân loại từng câu xem có khớp với phân bố ngôn ngữ điển hình của LLM (cụm từ chuyển ý lặp, mệnh đề hedge, cấu trúc "topic → giải thích → caveat").

Ngoài ra Turnitin còn nhận diện các **n-gram đặc trưng của LLM**, ví dụ: *"It is important to note"*, *"should be interpreted carefully"*, *"This does not mean X. It means Y."*, *"The actuarial implication is..."*.

---

## 2. Tổng Quan Định Lượng

| Chỉ số | Bản gốc (backup) | Bản đã sửa (RpSug.md) | Mức tăng |
|--------|------------------|------------------------|----------|
| Số dòng nội dung (loại ảnh base64) | 249 | 340 | **+36.5 %** |
| Tổng số từ | **5.279** | **10.857** | **+105.7 %** |
| Cụm từ hedge (*should be interpreted, carefully, however, therefore, this means that, ...*) | 6 lần | **16 lần** | +167 % |
| Cụm liệt kê tuyến tính (*First, Second, Third, At the same time, ...*) | 6 lần | **14 lần** | +133 % |
| Cụm chuyển ngữ học thuật (*Demographically, Actuarially, consistent with, reinforces, complementary, ...*) | 10 lần | **31 lần** | +210 % |
| Số section mới được thêm | – | +1 (Section 5: Gompertz) | – |

> **Diễn giải:** Khi nội dung tăng hơn gấp đôi mà mật độ cụm AI lại tăng mạnh hơn nữa, đây là tín hiệu rõ rệt rằng phần văn bản mới **không phải chỉ là chỉnh sửa**, mà là **sinh thêm bằng LLM**.

---

## 3. Các Khu Vực Có Dấu Hiệu AI Can Thiệp Cụ Thể

### 3.1 Section 1 — Introduction (CAN THIỆP MẠNH)

**Bản gốc** (3 đoạn ngắn, ~330 từ): trình bày trực tiếp, súc tích, giọng người.

**Bản sửa** (4 đoạn rất dài, ~800 từ):

- Câu mở mới: *"Mortality improvement is a central issue in actuarial science because life-contingent liabilities depend on both the probability of death and the timing of that death."* → cấu trúc **chủ đề → vì-mệnh đề** điển hình của LLM (perplexity thấp).
- Đoạn 2 hoàn toàn được sinh thêm: *"The actuarial effect of longer survival depends on the type of benefit being valued. For public pensions, occupational pensions, and life annuities…"* → liệt kê 3 thành phần kèm caveat cuối đoạn — khuôn mẫu cổ điển của GPT/Claude.
- Lặp lại nội dung của abstract bằng cách **diễn dải lại** (paraphrase loop) — Turnitin coi đây là tín hiệu mạnh.

**Mức nghi ngờ:** ★★★★★

---

### 3.2 Section 2.1 — Data Source (CAN THIỆP TRUNG BÌNH-MẠNH)

Bản gốc chỉ có 3 đoạn. Bản sửa được mở rộng thành **5 đoạn**, thêm:

- Một đoạn giải thích lý do dùng `1×1 life-table` (*"This structure is well suited to the report's objectives because…"*) — câu lý-giải-meta, đặc trưng của LLM khi được yêu cầu "expand" văn bản.
- Đoạn cuối mới: *"Two methodological limitations should be kept in view from the beginning. First… Second…"* → tín hiệu **liệt kê tuyến tính + cụm hedge**.

**Mức nghi ngờ:** ★★★★☆

---

### 3.3 Section 2.2 — Life Table Indicators (CAN THIỆP MẠNH)

Bản gốc có công thức gọn, mô tả vắn tắt. Bản sửa **chèn thêm các câu diễn giải dư thừa** giữa các công thức, ví dụ:

- *"This conditional interpretation is important. A low value of \(q_x\) at age 40 means that a person who has already survived to age 40 has a low probability of dying before age 41."*
- *"The report therefore treats \(l_x\), \(d_x\), and \(q_x\) as complementary rather than interchangeable indicators."*

→ **Đặc trưng "redundant clarification"** của AI: giải thích lại khái niệm vừa nêu, dùng cấu trúc *"This X is important. Y means Z."* — perplexity rất thấp.

**Mức nghi ngờ:** ★★★★★

---

### 3.4 Section 2.3 — Analytical Framework (CAN THIỆP MẠNH)

Mỗi khái niệm (mortality improvement, rectangularization, compression) đều được **lặp lại + caveat** theo công thức:

> **Topic sentence → Giải thích → "It does not imply…" / "It is a statement about… not a claim that…"**

Đây là pattern **"caveat injection"** đặc trưng của LLM hiện đại được fine-tune cho học thuật. Đếm nhanh: từ "does not imply / does not mean / should not be interpreted" xuất hiện **3 lần chỉ trong section này** (bản gốc: 0 lần).

**Mức nghi ngờ:** ★★★★★

---

### 3.5 Section 3.1, 3.2, 3.3 — Trend Analysis (CAN THIỆP MẠNH)

Tất cả ba section trends đều theo **template lặp đi lặp lại**:

1. Mô tả chỉ số (e0, e65+65, Lexis Point).
2. Câu *"The demographic meaning is… The actuarial meaning is…"* (xuất hiện ≥4 lần).
3. Câu caveat: *"The defensible interpretation is… / The conclusion should be limited to…"*
4. Đoạn cuối nói về implication cho pension/annuity.

Việc **3 section liên tiếp dùng đúng 1 khung paragraph** là cờ đỏ kinh điển của AI — vì người viết thật hiếm khi giữ cấu trúc đều như vậy (burstiness thấp).

Số liệu (80.23 → 85.40, 73.40 → 81.92, …) được **giữ nguyên** từ bản gốc, nhưng được **bọc lại** trong các đoạn diễn giải dài — hành vi điển hình khi nhờ AI "academic-ize" một bản nháp.

**Mức nghi ngờ:** ★★★★★

---

### 3.6 Section 3.4 — Gender Comparison (CAN THIỆP TRUNG BÌNH)

Bản sửa thêm đoạn *"The demographic meaning of this convergence is that Swiss male and female mortality profiles have moved closer at the level of modal old-age death…"* — văn phong meta-explanatory, đặc trưng AI.

Đoạn cuối: *"For actuarial practice, the appropriate conclusion is therefore balanced: female longevity remains higher, male improvement is faster, the average gender gap narrows but does not disappear, and modal ages at death converge around advanced ages."* → cấu trúc **"balanced conclusion list"** mà LLM thường dùng để kết section.

**Mức nghi ngờ:** ★★★★☆

---

### 3.7 Section 4 — Mortality Compression (CAN THIỆP MẠNH)

Bản gốc: 6 đoạn vừa phải. Bản sửa: **8 đoạn**, với 2 đoạn mới hoàn toàn:

- *"The Lexis Point, \(e_0\), and \(e_{65}+65\) summarize the same structure from different angles…"* → câu **meta-synthesis** rất AI.
- *"The actuarial significance is strongest for retirement-income liabilities. If more people survive to age 65 and then live longer beyond age 65…"* → cấu trúc **conditional + implication** điển hình.

Đoạn cuối thêm câu **self-limiting statement**: *"The main limitation is that the section relies on visual evidence from selected benchmark years…"* — kỹ thuật "hedge for credibility" của LLM.

**Mức nghi ngờ:** ★★★★★

---

### 3.8 Section 5 — Gompertz / Gompertz-Makeham (HOÀN TOÀN MỚI – CAN THIỆP CỰC MẠNH)

> Section này **không tồn tại** trong bản gốc — nó được sinh hoàn toàn mới bởi AI/Codex và tách ra thành section độc lập.

Cấu trúc hoàn hảo theo "LLM academic template":

1. Định nghĩa Gompertz (kèm công thức μx = Bc^x).
2. Định nghĩa Gompertz-Makeham (kèm công thức μx = A + Bc^x).
3. Mô tả chart.
4. **Caveat dài** (đoạn *"The chart cannot support stronger claims without formal model output…"*).
5. **Meta-summary** (đoạn *"For the purposes of this report, the Gompertz-Makeham section therefore has a limited role…"*).

Mật độ cụm AI cực cao:
- *"It is therefore useful for…"*
- *"This distinction is relevant to the Swiss charts because…"*
- *"This combination is compatible with…"*
- *"It should not be used to state that…"*

**Mức nghi ngờ:** ★★★★★ (gần như chắc chắn 100% LLM-generated)

---

### 3.9 Section 6 — HLE vs TLE (CAN THIỆP TRUNG BÌNH-MẠNH)

Bản gốc đoạn ngắn (~250 từ). Bản sửa mở rộng lên ~600 từ, thêm:

- Đoạn định nghĩa lại TLE/HLE/HALE bằng cách **mô tả khái niệm WHO** – có vẻ kéo từ kiến thức nền của LLM.
- Số liệu **mới** xuất hiện: *"in 2021, female TLE was about 85.1 years and female HALE about 71.3 years, while male TLE was about 81.5 years and male HALE about 70.9 years"* → **CẢNH BÁO ĐẶC BIỆT**: số liệu này không có trong bản gốc. Cần xác minh có thật trên WHO hay LLM tự sinh (hallucination).
- Đoạn caveat dài về data limitations: *"WHO TLE and HALE values are available here for 2000–2021, whereas the HMD life-table analysis extends to 2024…"*

**Mức nghi ngờ:** ★★★★☆ (kèm rủi ro số liệu bịa)

---

### 3.10 Section 7 — Pension Policy (CAN THIỆP TRUNG BÌNH)

Bản gốc 4 đoạn. Bản sửa **6 đoạn**, chèn thêm:

- Đoạn về "first pillar pressure" (*"For the first pillar, the core pressure arises from the relationship between contributors and beneficiaries…"*).
- Đoạn về "second pillar" (*"For the second pillar, longevity affects funded pension promises through reserves, annuity conversion factors…"*).

→ Cấu trúc **"For X… For Y…"** lặp lại — mô-típ song hành điển hình của AI.

**Mức nghi ngờ:** ★★★★☆

---

### 3.11 Section 8 — Insurance Market (CAN THIỆP NHẸ-TRUNG BÌNH)

Phần lớn dữ liệu FINMA giữ nguyên. AI chủ yếu **bọc thêm** các đoạn diễn giải về GWP vs technical liabilities, ví dụ:

- *"In this section, Gross Written Premiums (GWP) are used as a flow measure of annual business volume, while technical liabilities and actuarial reserves are used as balance-sheet measures of obligations already accumulated."* → câu **định nghĩa thuật ngữ kiểu sách giáo khoa** mà người viết gốc đã không có.

**Mức nghi ngờ:** ★★★☆☆

---

### 3.12 Section 9 — APVB Pricing (CAN THIỆP TRUNG BÌNH)

Công thức APVB được giữ nguyên. AI thêm:

- Đoạn 9.1 mở rộng về deterministic limitations.
- Đoạn cuối 9.2: *"It also shows why the mortality-improvement effect is not the same for all insurance products: for a death benefit, later death increases the discount period, whereas for an annuity, later death lengthens the payment stream."* → câu kết section dạng **"contrast summary"** rất AI.
- Đoạn 9.4 hoàn toàn mới về "Dynamic mortality tables".

**Mức nghi ngờ:** ★★★★☆

---

### 3.13 Section 10 & 11 — Discussion & Conclusion (CAN THIỆP MẠNH)

Section 10 mở rộng từ 4 đoạn → **5 đoạn dài**.
Section 11 mở rộng từ 3 đoạn → **5 đoạn dài**, **thêm hẳn một danh sách 5 hướng research mới** (*"Future research could extend the report in five directions. First… Second… Third… Fourth… Fifth…"*).

Cấu trúc liệt kê 5-bước cuối bài là **cờ đỏ AI mạnh nhất**: Turnitin đã được train trên hàng triệu kết luận GPT-style có dạng *"Future work can extend in N directions"*.

**Mức nghi ngờ:** ★★★★★

---

## 4. Top 10 Cụm Từ "Đặc Trưng AI" Xuất Hiện Trong Bản Sửa

| # | Cụm từ / mẫu | Số lần (bản sửa) | Số lần (bản gốc) |
|---|---|---|---|
| 1 | *"should be interpreted carefully"* / *"should be interpreted"* | nhiều | hiếm |
| 2 | *"The defensible interpretation is…"* | xuất hiện mới | 0 |
| 3 | *"The demographic meaning is… The actuarial meaning is…"* | ≥4 | 0 |
| 4 | *"This does not mean X. It means Y."* (đảo nghĩa) | ≥3 | hiếm |
| 5 | *"For actuarial purposes / practice / work"* | rất nhiều | ít |
| 6 | *"First… Second… Third…"* (signposting) | nhiều | ít |
| 7 | *"consistent with"* (đệm) | nhiều | trung bình |
| 8 | *"It should not be used to state that…"* | mới | 0 |
| 9 | *"This combination is compatible with…"* | mới | 0 |
| 10 | *"complementary rather than interchangeable"* | mới | 0 |

---

## 5. Đánh Giá Tổng Thể Dưới Góc Nhìn Turnitin

| Tiêu chí Turnitin | Điểm rủi ro AI (1–5) |
|---|---|
| **Perplexity thấp** (ngôn ngữ "dễ đoán") | **5/5** – văn bản rất mượt, câu nào cũng có thể đoán từ tiếp theo |
| **Burstiness thấp** (câu đều đặn) | **5/5** – đa số câu dài 25–45 từ, ít câu ngắn |
| **Lặp mẫu cấu trúc đoạn** (topic → giải thích → caveat) | **5/5** – gần như mọi đoạn đều theo khung này |
| **N-gram AI điển hình** | **5/5** – mật độ cụm "carefully", "consistent with", "this does not mean" rất cao |
| **Section được thêm hoàn toàn mới** | **5/5** – Section 5 (Gompertz) gần như chắc chắn LLM-generated |
| **Hallucination rủi ro** | **3/5** – số WHO mới (TLE/HALE 2021) cần xác minh nguồn |
| **Tỉ lệ AI-likely lines (ước lượng)** | **70 – 85 %** |

> **Kết luận:** Bản `RpSug.md` (sau khi sửa bởi Codex) có **dấu hiệu AI can thiệp ở mức rất cao**. Nếu submit qua Turnitin, dự đoán điểm **AI Writing ≈ 70–90 %**. Bản backup gốc nhiều khả năng chỉ có AI ≈ 15–30 %.

---

## 6. Khuyến Nghị Giảm Rủi Ro AI Detection

1. **Rút gọn các đoạn mở rộng**: cắt 30–40 % các đoạn của Section 1, 2.2, 2.3, 3.x, 4, 10, 11. Giữ thông tin cốt lõi, bỏ các câu "diễn giải lại".
2. **Loại bỏ / viết lại Section 5 (Gompertz)** — đây là section AI rõ nhất. Hoặc viết lại bằng giọng cá nhân, có ví dụ số cụ thể từ dữ liệu của bạn.
3. **Thay các cụm sáo của LLM** bằng từ ngữ riêng:
   - *"should be interpreted carefully"* → *"this reading has limits"* hoặc bỏ luôn
   - *"The defensible interpretation is…"* → *"I read this as…"* / *"The chart suggests…"*
   - *"The demographic meaning is… The actuarial meaning is…"* → gộp thành 1 câu
4. **Tăng burstiness**: chèn câu ngắn (5–10 từ) xen kẽ câu dài. Đặt 1–2 câu **mệnh lệnh / cảm thán nhẹ** trong discussion.
5. **Xác minh số liệu WHO** trong Section 6 — nếu LLM bịa, sẽ bị bóc cả về đạo văn lẫn AI.
6. **Giữ lại các đánh dấu `[CHECK REFERENCE DETAILS]` / `[NEED EMPIRICAL VALUE]`** — đây là dấu hiệu người thật đang làm việc, không nên xóa.
7. **Viết tay lại Conclusion & Discussion** — đây là phần Turnitin "soi" mạnh nhất, vì AI luôn kết bài theo công thức "First, Second, Third…".

---

## 7. Tóm Tắt Một Câu

> Bản `RpSug.md` đã được **mở rộng gấp đôi (5.3k → 10.9k từ)** bằng cách chèn thêm các đoạn diễn giải, caveat và meta-summary theo khuôn mẫu LLM điển hình, kèm 1 section hoàn toàn mới (Gompertz). Nội dung số liệu cốt lõi vẫn giữ từ bản gốc, nhưng **lớp vỏ ngôn ngữ học thuật bao quanh là gần như chắc chắn do AI sinh ra** — và đó chính là phần Turnitin sẽ đánh dấu.
