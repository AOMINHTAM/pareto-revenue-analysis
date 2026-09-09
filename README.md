# 📊 TeddyWorld — Phân Tích Doanh Thu Nguyên Lý Pareto (80/20)

Dự án phân tích đóng góp doanh thu sản phẩm dựa trên tập dữ liệu thương mại điện tử **TeddyWorld** (hơn 32.000 đơn hàng), ứng dụng **Nguyên lý Pareto (80/20)** để xác định dòng sản phẩm chủ lực ("vital few") tạo ra phần lớn giá trị kinh doanh, phát hiện rủi ro phụ thuộc danh mục và đề xuất giải pháp tối ưu vận hành.

---

## 🎯 1. Bối Cảnh & Mục Tiêu Kinh Doanh

* **Bối cảnh:** TeddyWorld kinh doanh đa dạng các dòng gấu bông và phụ kiện quà tặng. Ban lãnh đạo cần đánh giá mức độ phụ thuộc doanh thu vào từng SKU để phân bổ ngân sách marketing và kế hoạch nhập hàng hợp lý.
* **Mục tiêu:**
  * Tính toán doanh thu thực nhận (*Net Revenue = Gross Revenue - Refunds*).
  * Xác định tỷ trọng đóng góp tích lũy của từng sản phẩm.
  * Phân nhóm danh mục theo ngưỡng Pareto (Nhóm 80% doanh thu vs Nhóm 20% còn lại).
  * Đưa ra khuyến nghị chiến lược tồn kho và kinh doanh.

---

## 🛠️ 2. Công Cụ & Thư Viện

* **Ngôn ngữ:** Python 3.x
* **Thư viện chính:**
  * `pandas` / `numpy`: Làm sạch, merge bảng và tính toán doanh thu lũy kế (`cumsum`).
  * `matplotlib` / `seaborn`: Trực quan hóa biểu đồ Pareto kết hợp (Bar chart + Line chart tích lũy).
* **Môi trường:** Jupyter Notebook

---

## 📈 3. Kết Quả & Trực Quan Hóa (Pareto Chart)

### Bảng số liệu phân tích lũy kế

| Thứ hạng | Tên sản phẩm | Số lượng bán | Doanh thu ($) | Tỷ trọng (%) | Lũy kế (%) | Phân nhóm Pareto |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **1** | The Original Mr. Fuzzy | 15,200 | 485,000 | 45.2% | 45.2% | **Top 80% (Core)** |
| **2** | Forever Bear | 8,400 | 268,800 | 25.1% | 70.3% | **Top 80% (Core)** |
| **3** | The Birthday Sugar Panda | 3,900 | 124,800 | 11.6% | 81.9% | **Top 80% (Core)** |
| **4** | The Hudson River Mini bear | 3,100 | 99,200 | 9.3% | 91.2% | **Bottom 20% (Tail)** |
| **...** | Các phụ kiện & SKU khác | ... | ... | ... | 100.0% | **Bottom 20% (Tail)** |

> **Quy tắc 80/20 được kiểm chứng:** Chỉ **3 dòng sản phẩm đầu bảng** đã đóng góp đến **~82% tổng doanh thu** của toàn bộ thương hiệu.

---

## 💡 4. Insights & Bài Học Kỹ Thuật

* **Sự tập trung rủi ro danh mục:** Doanh số phụ thuộc áp đảo vào dòng sản phẩm *The Original Mr. Fuzzy* (>45%). Nếu xảy ra đứt gãy chuỗi cung ứng hoặc lỗi chất lượng với SKU này, dòng tiền công ty sẽ bị tổn hại nghiêm trọng.
* **Hiệu ứng Cross-selling chưa tối ưu:** Nhóm sản phẩm đuôi (Long-tail items) chiếm nhiều mã SKU nhưng mang lại biên đóng góp thấp, cần đánh giá lại chi phí lưu kho.
* **Lưu ý kỹ thuật khi xử lý dữ liệu:**
  * Phải join bảng đơn hàng với bảng hoàn tiền (`refunds`) trước khi tính doanh thu ròng, tránh phóng đại số liệu thực thu.
  * Sắp xếp giảm dần (`sort_values(ascending=False)`) trước khi chạy hàm `.cumsum()` tính tỷ lệ phần trăm tích lũy.

---

## 🚀 5. Khuyến Nghị Hành Động (Actionable Recommendations)

1. **Quản trị Tồn kho Ưu tiên:** Áp dụng mô hình dự báo nhu cầu chính xác và mức tồn kho an toàn (Safety Stock) cao nhất cho 3 SKU nhóm 80% (*Mr. Fuzzy, Forever Bear, Sugar Panda*), tránh tình trạng Out-of-Stock vào mùa cao điểm.
2. **Chiến lược Bán kèm (Bundling):** Tạo các combo quà tặng ghép đôi sản phẩm chủ lực với các SKU nhóm đuôi để kích thích thanh lý hàng tồn phụ kiện.
3. **Phân bổ Ngân sách Paid Ads:** Tập trung 70–80% chi phí chạy quảng cáo chuyển đổi vào Top 3 sản phẩm chủ lực để tối đa hóa ROAS (Return on Ad Spend).

---

## ⚙️ 6. Hướng Dẫn Tái Hiện Môi Trường (Reproducibility)

1. Clone repository về máy:
   ```bash
   git clone [https://github.com/AOMINHTAM/pareto-revenue-analysis.git](https://github.com/AOMINHTAM/pareto-revenue-analysis.git)
   cd pareto-revenue-analysis