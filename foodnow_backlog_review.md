# Rà soát User Story và sắp xếp Product Backlog – FoodNow

## Bước 1. Tìm lỗi (INVEST)

| Mã | Kết quả và lý do |
|----|------------------|
| US1 | **Đạt**: vai trò rõ, một việc, có lợi ích, thử được bằng cách chọn loại món rồi xem kết quả. |
| US2 | **Sai T (Testable)**: "đẹp", "dễ dùng", "hài lòng" là cảm nhận chủ quan, không có ngưỡng đo nên không biết khi nào là xong và không thể kiểm thử. |
| US3 | **Sai V (Valuable)** (kèm vi phạm N – Negotiable): lợi ích "code dễ bảo trì" chỉ có giá trị với lập trình viên, không nối được tới giá trị cho khách hàng hay kinh doanh; đồng thời story áp đặt sẵn giải pháp (React) thay vì mô tả nhu cầu. Việc kỹ thuật vẫn được đưa vào backlog, nhưng phải được viết như một hạng mục kỹ thuật (technical enabler) nêu rõ nó phục vụ kết quả người dùng nào (ví dụ: rút ngắn thời gian ra tính năng mới, giảm lỗi giao diện). |
| US4 | **Sai S (Small)**: gộp quá nhiều việc vào một story (3 mốc thời gian, 2 chiều phân tích theo khu vực và nhà hàng, xuất Excel, tự động gửi email) nên không vừa một Sprint và nhóm không ước lượng được. |

---

## Bước 2. Sửa lỗi

### a) Viết lại US2 với tiêu chí "dễ dùng" đo được

**US2 (đã sửa):** Là một khách hàng, tôi muốn đặt một đơn hàng chỉ qua tối đa 3 bước (chọn món → xem giỏ hàng → xác nhận thanh toán), để đặt món nhanh và không bị rối.

**Tiêu chí chấp nhận (đo được):** Trong buổi thử nghiệm với 5 khách hàng mới chưa từng dùng app, ít nhất 4/5 người hoàn tất một đơn hàng trong tối đa 3 bước và không quá 2 phút, không cần ai hướng dẫn.

### b) Tách US4 và đặt vào cây Epic → Feature → User Story

```
Epic:    Báo cáo & phân tích kinh doanh
 └─ Feature:  Báo cáo doanh thu cho admin
      ├─ US4a: Xem doanh thu theo ngày, tuần, tháng
      └─ US4b: Lọc doanh thu theo khu vực và nhà hàng
```

**US4a:** Là một admin, tôi muốn xem báo cáo doanh thu theo ngày, tuần, tháng, để theo dõi kết quả kinh doanh theo thời gian.
- Tiêu chí: chọn được mốc ngày/tuần/tháng; tổng doanh thu hiển thị khớp với tổng các đơn đã hoàn thành trong kỳ đó.

**US4b:** Là một admin, tôi muốn lọc báo cáo doanh thu theo khu vực và theo nhà hàng, để biết nơi nào đang bán tốt hay kém.
- Tiêu chí: chọn được khu vực và/hoặc nhà hàng; số liệu sau lọc khớp với đơn hàng của khu vực/nhà hàng đó.

**Phần còn lại của US4** (xuất Excel, tự gửi email cho ban giám đốc) là các story độc lập, được ghi lại ở cuối Feature này với ưu tiên thấp và chỉ tách chi tiết khi đến gần Sprint.

---

## Bước 3. Xếp lại backlog

### a) Thứ tự ưu tiên

| Thứ tự | Story | Lý do |
|--------|-------|-------|
| 1 | **US1** – Lọc nhà hàng theo loại món | Đã đạt INVEST, nhỏ, rõ ràng, giúp khách tìm món ngay từ đầu luồng đặt món; có thể ước lượng và làm ngay. |
| 2 | **US2** (đã sửa) – Đặt món tối đa 3 bước | Giá trị cao vì nằm ở luồng đặt đơn cốt lõi (ảnh hưởng trực tiếp tới tỷ lệ hoàn tất đơn), nhưng cần thiết kế giao diện và thử nghiệm với người dùng nên xếp sau US1. |
| 3 | **US4a** – Doanh thu theo ngày/tuần/tháng | Phục vụ nội bộ, không chặn khách hàng đặt món; là phần nền của báo cáo. |
| 4 | **US4b** – Lọc theo khu vực và nhà hàng | Phụ thuộc vào US4a (cần có báo cáo cơ bản trước) và giá trị bổ sung thấp hơn. |

Nếu dữ liệu cho thấy khách bỏ giỏ hàng nhiều, Product Owner có thể đổi chỗ US1 và US2.

### b) Theo DEEP, story đứng đầu cần chi tiết đến mức nào?

Chữ **D (Detailed appropriately)**: các mục ở đầu backlog phải được làm chi tiết nhất, các mục càng xuống dưới càng thô. Với US1 (đứng đầu), mức chi tiết cần có:
- Đạt đủ INVEST, nhỏ đến mức hoàn thành trong một Sprint.
- Có tiêu chí chấp nhận rõ (danh sách loại món, chọn một hay nhiều loại, hiển thị khi không có kết quả).
- Có mô hình/bản phác giao diện nếu cần, và đã làm rõ các câu hỏi chưa biết.

**Buổi Refinement còn phải làm với US1 trước khi đưa vào Sprint:**
1. Làm rõ tiêu chí chấp nhận và các trường hợp biên cùng Product Owner.
2. Nhóm **ước lượng** (ví dụ Planning Poker bằng story point); nếu ước lượng quá lớn thì tách nhỏ tiếp.
3. Xác định phụ thuộc (dữ liệu loại món của nhà hàng, API) và rủi ro.
4. Kiểm tra story đáp ứng **Definition of Ready**, và thống nhất cách kiểm thử theo Definition of Done.
5. Product Owner xác nhận lại thứ tự ưu tiên, rồi mới đưa vào Sprint Planning.

Các chữ còn lại của DEEP áp dụng thêm: **E (Estimated)** – mục đầu phải có ước lượng; **E (Emergent)** – backlog liên tục thay đổi (thêm, tách, bỏ mục) sau mỗi Sprint; **P (Prioritized)** – mục giá trị cao nằm trên cùng.
