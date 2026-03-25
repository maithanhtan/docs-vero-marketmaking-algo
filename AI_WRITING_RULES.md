# AI Writing Rules for Market Making & Hedge Documentation

## Core Principles

### 1. Image-First Structure
**Rule**: Mỗi hình ảnh phải có phần giải thích riêng ngay sau nó.

**Pattern**:
```markdown
<img src="/images/filename.png" alt="Description" />

[Giải thích tổng quan về màn hình/chức năng]

**Section Name**:
- **Field Name**: ý nghĩa và mục đích của field
- **Field Name 2**: ý nghĩa và mục đích của field
```

**DON'T**:
```markdown
<img src="/images/image1.png" />
<img src="/images/image2.png" />
<img src="/images/image3.png" />

[Giải thích chung cho tất cả hình]
```

**DO**:
```markdown
<img src="/images/image1.png" />
[Giải thích cụ thể cho hình 1]

<img src="/images/image2.png" />
[Giải thích cụ thể cho hình 2]

<img src="/images/image3.png" />
[Giải thích cụ thể cho hình 3]
```

---

## 2. Field-Level Documentation

### Rule: Diễn giải từng field trong mọi màn hình

**Requirements**:
- Mỗi field phải có giải thích riêng
- Bao gồm: tên field, ý nghĩa, đơn vị (nếu có), ví dụ (nếu cần)
- Sử dụng bullet points cho dễ đọc

**Example**:
```markdown
**Core Parameters**:
- **Price Mode**: chế độ tham chiếu giá để đặt lệnh
  - **Last Price**: sử dụng giá khớp cuối cùng làm tham chiếu
  - **Best Bid/Ask**: sử dụng giá tốt nhất hiện tại làm tham chiếu
- **Price bid-ask spacing (price step)**: khoảng cách giá giữa bid và ask so với giá lý thuyết (spread), tính bằng bậc giá
- **Randomize Qty Interval (ms)**: chu kỳ thay đổi khối lượng ngẫu nhiên (milliseconds)
```

---

## 3. Terminology Standards

### Critical Terms (MUST follow exactly):

| English Term | Vietnamese Term | Notes |
|--------------|-----------------|-------|
| Theo Price | Giá lý thuyết | NOT "giá tham chiếu" |
| Theoretical Price | Giá lý thuyết | Consistent with "Theo Price" |
| Notional | Danh nghĩa | Always use "danh nghĩa" for notional values |
| Notional Value | Giá trị danh nghĩa | NOT "giá trị" alone |
| Hedge Threshold | Ngưỡng giá trị danh nghĩa vị thế ròng | Include "danh nghĩa" |
| Fill Threshold | Giá trị danh nghĩa fill | Include "danh nghĩa" |
| Price Step | Bậc giá | Standard term |
| Layer | Layer | Keep in English |
| Spread | Spread | Keep in English |
| Gap Notional | Giá trị danh nghĩa của gap | Include "danh nghĩa" |

### Value Units:
- **VND values**: Always specify "(VND)" after the field name
- **Percentage**: Always specify "(%)" or "tỷ lệ %"
- **Time**: Always specify "(ms)" for milliseconds, "(s)" for seconds
- **Quantity**: Use "khối lượng" consistently

---

## 4. Table Documentation

### Rule: Mỗi bảng phải có giải thích từng cột

**Pattern**:
```markdown
**Table Name**:
- **Column 1**: ý nghĩa của cột (đơn vị nếu có)
- **Column 2**: ý nghĩa của cột (ví dụ nếu cần)
- **Column 3**: ý nghĩa của cột (giá trị đặc biệt nếu có)
```

**Example**:
```markdown
**Coverage Table Columns**:
- **Warrant**: mã chứng quyền (ví dụ: CMWG2504, CMWG2510)
- **Hedger Status**: trạng thái hedger (WARN = cảnh báo cần xem xét)
- **Delta**: hệ số delta của warrant (độ nhạy giá so với underlying)
- **Req Hedge**: khối lượng hedge yêu cầu (required hedge quantity)
- **Hedge Pos**: vị thế hedge hiện tại (current hedge position)
- **Residual**: chênh lệch giữa hedge yêu cầu và thực tế (màu đỏ = thiếu hedge, màu xanh = dư hedge)
- **Covered**: tỷ lệ % hedge coverage (0% = chưa hedge, -3% = over hedge)
```

---

## 5. Enum/Mode Documentation

### Rule: Liệt kê và giải thích tất cả các giá trị có thể

**Pattern**:
```markdown
**Field Name**: mô tả chung
- **Value 1**: ý nghĩa và cách hoạt động
- **Value 2**: ý nghĩa và cách hoạt động
- **Value 3**: ý nghĩa và cách hoạt động
```

**Example**:
```markdown
**Hedge Buy/Sell Mode**: chế độ thực thi lệnh hedge
- **BEST**: đặt lệnh tại giá tốt nhất hiện tại (best bid/ask)
- **LAST**: đặt lệnh tại giá khớp cuối cùng
- **MTL**: Market-to-Limit, đặt market rồi chuyển sang limit
- **BEST+**: đặt lệnh tốt hơn best bid/ask một bậc giá
- **OPPOSITE**: đặt lệnh phía đối diện (buy tại ask, sell tại bid)
- **OPPOSITE+**: đặt lệnh phía đối diện cộng thêm một bậc giá
```

---

## 6. Configuration Sections

### Rule: Nhóm các field liên quan và giải thích mục đích của nhóm

**Pattern**:
```markdown
##### Section Name

<img src="/images/section-image.png" />

[Mô tả tổng quan về section]

**Subsection 1**:
- **Field 1**: giải thích
- **Field 2**: giải thích

**Subsection 2**:
- **Field 3**: giải thích
- **Field 4**: giải thích
```

---

## 7. Special Values Documentation

### Rule: Giải thích ý nghĩa của các giá trị đặc biệt

**Examples**:
- `(0 = disabled)` - Giá trị 0 có ý nghĩa đặc biệt
- `(0 = không giới hạn)` - Giải thích ý nghĩa của 0
- `(WARN = cảnh báo)` - Giải thích status code
- `(màu đỏ = thiếu hedge)` - Giải thích color coding

**Pattern**:
```markdown
- **Field Name (0 = disabled)**: mô tả field, giải thích khi giá trị = 0
```

---

## 8. Examples and Context

### Rule: Cung cấp ví dụ cụ thể khi cần thiết

**When to include examples**:
- Giá trị số (VND amounts, percentages)
- Công thức tính toán
- Tỷ lệ chuyển đổi
- Mã chứng khoán

**Pattern**:
```markdown
- **Field Name**: mô tả (ví dụ: 100,000,000 VND)
- **Conversion Ratio**: tỷ lệ chuyển đổi (ví dụ: 0.1 = 10 warrants cho 1 cổ phiếu cơ sở)
```

---

## 9. Pricing Model Documentation

### Rule: Giải thích đầy đủ các tham số của pricing model

**Black-Scholes Parameters**:
```markdown
- **Strike Price (K)**: giá thực hiện của quyền chọn
- **Maturity Date**: ngày đáo hạn
- **Volatility (%)**: độ biến động ngầm định (implied volatility)
- **Risk-Free Rate (%)**: lãi suất phi rủi ro
- **Option Type**: Call hoặc Put
- **Conversion Ratio**: tỷ lệ chuyển đổi (ví dụ: 0.1 = 10 warrants cho 1 cổ phiếu cơ sở)
```

**Delta One Parameters**:
```markdown
- **Pricing Slope**: hệ số nhân cho giá underlying (multiplier for underlying price)
- **Pricing Intercept**: giá trị cố định cộng thêm vào giá (fixed offset added to price)
```

---

## 10. Layering Configuration

### Rule: Giải thích cấu trúc layer và các tham số

**Symmetric Layering**:
```markdown
- **Layering Mode**: chế độ phân lớp (Symmetric)
- **Layer Count**: số lượng layer (độ sâu sổ lệnh)
- **Price layer spacing (price step)**: khoảng cách giá giữa các layer
- **Symmetric Layering Configuration**: phân bổ khối lượng cho từng layer (L1, L2, L3, L4, L5)
```

**Asymmetric Layering**:
```markdown
- **Layering Mode**: chế độ phân lớp (Asymmetric)
- **Layer Count**: số lượng layer
- **Asymmetric Layering Configuration**: bảng cấu hình chi tiết cho từng layer
  - **Level**: mức layer (L1, L2, L3, ...)
  - **Bid Price Step**: khoảng cách giá bid so với giá lý thuyết từ pricing model
  - **Ask Price Step**: khoảng cách giá ask so với giá lý thuyết từ pricing model
  - **Bid Qty %**: phần trăm khối lượng bid cho layer này
  - **Ask Qty %**: phần trăm khối lượng ask cho layer này
```

---

## 11. Safety Configuration

### Rule: Giải thích rõ các ngưỡng an toàn và cơ chế bảo vệ

**Safety Limits**:
```markdown
- **Max Loss (0 = disabled)**: ngưỡng lỗ tối đa (VND), dừng thuật toán khi tổng lỗ vượt giá trị này (0 = không giới hạn)
- **Take Profit (0 = disabled)**: ngưỡng lời mục tiêu (VND), dừng thuật toán khi đạt lợi nhuận này (0 = không giới hạn)
```

**Anti-Arb Safety**:
```markdown
- **Fill Window (ms)**: cửa sổ thời gian quan sát fill (milliseconds)
- **Fill Threshold**: giá trị danh nghĩa (VND) fill bất thường trong cửa sổ thời gian để kích hoạt bảo vệ
- **Qty Reduction %**: phần trăm giảm khối lượng khi phát hiện fill bất thường
- **Cooldown (ms)**: thời gian chờ trước khi khôi phục khối lượng bình thường (milliseconds)
```

---

## 12. Monitoring Tabs Documentation

### Rule: Giải thích mục đích và các metrics trong mỗi tab

**Pattern**:
```markdown
### Tab Name

<img src="/images/tab-screenshot.png" />

**Section 1**: mục đích của section
- **Metric 1**: ý nghĩa
- **Metric 2**: ý nghĩa

**Section 2**: mục đích của section
- **Metric 3**: ý nghĩa
- **Metric 4**: ý nghĩa
```

---

## Checklist for New Documentation

Before submitting documentation, verify:

- [ ] Mỗi hình có giải thích riêng ngay sau nó
- [ ] Tất cả field trong màn hình đều được giải thích
- [ ] Sử dụng đúng thuật ngữ (giá lý thuyết, danh nghĩa)
- [ ] Đơn vị được ghi rõ (VND, %, ms)
- [ ] Enum/mode values được liệt kê đầy đủ
- [ ] Giá trị đặc biệt được giải thích (0 = disabled)
- [ ] Ví dụ cụ thể khi cần thiết
- [ ] Bảng có giải thích từng cột
- [ ] Color coding được giải thích (màu đỏ = thiếu hedge)
- [ ] Công thức được viết rõ ràng

---

## Quick Reference

### Must Include for Every Field:
1. **Field name** (in bold)
2. **Purpose/meaning** (what it does)
3. **Unit** (VND, %, ms) if applicable
4. **Special values** (0 = disabled) if applicable
5. **Example** if it helps clarity

### Must Include for Every Image:
1. **Image tag** with descriptive alt text
2. **Overview** of what the screen shows
3. **Field-by-field breakdown** of all visible fields
4. **Context** of when/why to use this screen
