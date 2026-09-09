# SmartToys — Business Review & Growth Strategy

Phân tích **472,871 phiên truy cập** và **32,313 đơn hàng** của một doanh nghiệp e-commerce trong 3 năm (03/2012 – 03/2015), nhằm tìm nguyên nhân trượt lợi nhuận và các nút thắt tăng trưởng.

📊 **[Xem báo cáo slide (PDF)](reports/SmartToys_Business_Review.pdf)** · 📓 **[Notebook đầy đủ](notebooks/smarttoys_business_review.ipynb)**

---

## 1. Bối cảnh & Mục tiêu

SmartToys kinh doanh gấu bông cao cấp. Sau 3 năm vận hành, doanh số tăng trưởng nhưng Ban Giám đốc lo ngại về các "điểm mù": chi phí quảng cáo tăng mà không rõ nhóm khách nào bền vững, tỷ lệ hoàn hàng bất thường ở một số dòng sản phẩm, và luồng chuyển đổi trên website có dấu hiệu tắc nghẽn.

> **Câu hỏi trung tâm:** Làm thế nào để tối ưu hóa lợi nhuận và trải nghiệm khách hàng trong năm tới?

Ba mục tiêu cụ thể:

- **Giải mã hiện tượng trượt lợi nhuận** — bóc tách khoảng cách giữa doanh thu gộp và lợi nhuận thực sau giá vốn và hoàn tiền
- **Tìm nút thắt chuyển đổi** — xác định khách rơi rụng ở bước nào, trên thiết bị nào, từ nguồn nào
- **Tìm đòn bẩy tăng trưởng** — đánh giá cơ hội nâng AOV và giữ chân khách hàng

## 2. Dữ liệu & Techstack

**Dữ liệu:** 6 bảng quan hệ — `website_sessions`, `website_pageviews`, `orders`, `order_items`, `order_item_refunds`, `products`. Tổng hơn 1.1 triệu bản ghi pageview.

**Ngôn ngữ & thư viện:** Python · pandas · numpy · matplotlib · seaborn · plotly

**Kỹ thuật phân tích:**

| Kỹ thuật | Trả lời câu hỏi |
|---|---|
| Unit Economics | Sản phẩm nào thực sự sinh lời sau giá vốn và hoàn tiền? |
| Pareto & phân loại ABC | Mức độ tập trung rủi ro ở sản phẩm, kênh, khách hàng? |
| RFM Segmentation | Ai là khách giá trị cao? |
| Cohort Retention | Khách có quay lại không? |
| Sankey Journey | Traffic đi theo đường nào từ nguồn tới sản phẩm? |
| Conversion Funnel | Khách rơi rụng ở bước nào? |
| Market Basket Analysis | Sản phẩm nào thường được mua kèm? |

## 3. Bức tranh tổng thể

| Chỉ số | Giá trị |
|---|---|
| Doanh thu gộp | $1,938,509.75 |
| Giá vốn (COGS) | $722,370.25 — 37.26% doanh thu |
| Hoàn tiền | $85,338.69 — 4.40% doanh thu |
| **Lợi nhuận ròng** | **$1,130,800.81 — biên 58.33%** |
| Tỷ lệ chuyển đổi | 6.83% |
| AOV | $59.99 |

## 4. Ba phát hiện chính

### 4.1. Doanh nghiệp gần như không có vòng đời khách hàng

**98.14%** khách chỉ mua đúng một lần (31,105 trong tổng số 31,696). Tỷ lệ mua lại là **1.86%**, retention tháng thứ nhất **0.84%**, tháng thứ ba còn **0.20%**.

Doanh thu trung bình mỗi khách là **$61.16** — gần như bằng đúng AOV. Nói cách khác: mỗi khách chỉ đem về một đơn hàng rồi biến mất, nên chi phí quảng cáo bỏ ra để kéo họ về chỉ được thu hồi qua duy nhất đơn đó. Mọi tăng trưởng đều phải mua bằng ngân sách mới.

![Cohort Retention Rate](reports/figures/06b_cohort_retention.png)

### 4.2. Mobile là lỗ hổng tốn kém nhất, và đang xấu đi

Mobile chiếm **30.8%** traffic nhưng tỷ lệ chuyển đổi chỉ **3.09%**, so với **8.50%** của Desktop — chênh **2.75 lần**, và kém hơn ở **toàn bộ** các bước của phễu.

Khoảng cách này xuất hiện ở **cả 4 nguồn traffic**, không trừ nguồn nào. Đây là bằng chứng quan trọng: nếu do chất lượng traffic, mức chênh sẽ khác nhau giữa các kênh. Việc nó đồng đều chỉ ra nguyên nhân nằm ở chính giao diện website.

Củng cố thêm: tỷ lệ mua lại của khách Mobile (1.63%) gần bằng Desktop (1.90%). Khách Mobile không kém chất lượng — họ chỉ khó mua hàng hơn.

Nếu Mobile đạt được CR của Desktop, doanh nghiệp có thêm **7,889 đơn**, tương đương khoảng **$473,000** doanh thu trong 3 năm. Và trong 6 tháng gần nhất, khoảng cách drop-off tại bước thanh toán còn **nới rộng từ 10.3 lên 14.2 điểm phần trăm**.

![Phễu chuyển đổi Desktop vs Mobile](reports/figures/09_funnel_device.png)

### 4.3. Sản phẩm sinh lời nhất đang bị chôn vùi

`The Hudson River Mini bear` có **biên lợi nhuận ròng cao nhất danh mục (67.08%)** và **tỷ lệ hoàn hàng thấp nhất (1.28%)**. Khi khách đã xem trang chi tiết, **65.13%** thêm vào giỏ — cũng là cao nhất, vượt sản phẩm chủ lực `Mr. Fuzzy` (43.04%) tới 22 điểm phần trăm.

Nhưng chỉ **1.00%** khách xem trang danh mục click vào nó — thấp hơn `Mr. Fuzzy` **62 lần**.

Đây không phải vấn đề sản phẩm kém hấp dẫn mà là vấn đề hiển thị. Trong khi đó `Mr. Fuzzy` chiếm 62.47% doanh thu nhưng lại có biên ròng **thấp nhất (55.91%)**, do giá vốn cao cộng 1,237 đơn hoàn tiền làm mất $61,837.63.

![CTR qua từng bước phễu theo sản phẩm](reports/figures/11b_funnel_by_product.png)

## 5. Các phát hiện đáng chú ý khác

- **Hoàn hàng đạt đỉnh vào mùa hè, không phải mùa lễ hội.** Tháng 8 và 9 cùng ở mức **7.76%** — gấp 2.4 lần tháng 10 (3.17%), trong khi tháng 11–12 bán nhiều nhất lại hoàn thấp hơn trung bình. Vì tháng 6–9 là mùa thấp điểm, nguyên nhân không thể là quá tải công suất.
- **Sản phẩm hoàn hàng nhiều nhất theo tỷ lệ là `Birthday Sugar Panda` (6.04%)**, không phải `Mr. Fuzzy` — khoản hoàn tiền ăn mất 9.67% lợi nhuận của chính nó.
- **Bán chéo nâng AOV 75.6%** ($89.25 so với $50.82), chiếm 23.87% số đơn nhưng đóng góp 35.51% doanh thu. Tuy nhiên **cả 6 cặp sản phẩm đều có Lift < 1**, tức không có liên kết dương thực sự.
- **Phân loại ABC khách hàng không tuân theo Pareto:** cần tới 74.40% số khách mới đạt 80% doanh thu — hệ quả trực tiếp của việc không ai mua lại.

## 6. Khuyến nghị

| # | Hành động | Căn cứ dữ liệu | Bộ phận | Kỳ vọng | Ưu tiên |
|---|---|---|---|---|---|
| 1 | Tái thiết kế luồng thanh toán Mobile: rút gọn form `/billing`, tích hợp ví điện tử | Drop-off Mobile 47.72% vs Desktop 33.55%, khoảng cách đang nới rộng | Product | Thu hồi ~$150K/năm | Cao |
| 2 | Đưa Hudson lên vị trí nổi bật trang danh mục; gợi ý mua kèm tại Cart | Chỉ 1.00% click nhưng 65.13% thêm giỏ; biên 67.08% | Product & Marketing | Nâng tỷ trọng doanh thu Hudson từ 7.76% lên 15% | Cao |
| 3 | Rà soát chất lượng & đóng gói Panda và Mr. Fuzzy; bổ sung trường lý do hoàn hàng | Panda refund 6.04%; Mr. Fuzzy mất $61,838 (72.5% tổng tiền hoàn) | Vận hành | Giảm refund dưới 3%, tiết kiệm ~$40K | Cao |
| 4 | Siết kiểm soát đóng gói & lưu kho tháng 6–9 | Refund tháng 8–9 đạt 7.76%, gấp 2.4 lần tháng 10 | Vận hành & Kho vận | Đưa refund mùa hè về 4.32% | Cao |
| 5 | Xây chương trình mua lại: email sau 30 ngày, ưu đãi đơn thứ hai | Repeat rate 1.86%; khách mua lần 2 đạt $122–188 vs $61 | CRM | Nâng repeat rate lên 5% | Trung bình |
| 6 | Rà soát `/lander-3`, áp dụng thiết kế của `/lander-5` | Drop-off 96.61% trên 79,000 phiên, cao nhất site | Product | Thêm khoảng 5,300 đơn | Trung bình |
| 7 | Cắt ngân sách `socialbook`, dồn cho `direct/organic` | Socialbook 1.15% doanh thu, repeat 1.17%, CR Mobile 0.83% | Performance Media | Giảm CAC lãng phí | Trung bình |
| 8 | Bổ sung dashboard theo dõi LTV/CAC theo cohort | Chưa có chỉ số đo chất lượng khách hàng dài hạn | Data | Đo được hiệu quả của mục 5 | Trung bình |

## 7. Giới hạn của phân tích

Ba điểm cần nêu rõ khi diễn giải kết quả:

1. **Phân khúc RFM bị hạn chế bởi dữ liệu.** Cột `frequency` chỉ có 3 giá trị duy nhất (1, 2, 3), nên thang F thực chất chỉ 3 bậc thay vì 5. Tên các segment phản ánh chủ yếu Recency và Monetary, không phải mức độ trung thành thực sự.
2. **Market Basket không cho thấy liên kết dương.** Toàn bộ 6 cặp sản phẩm đều có Lift < 1, do `Mr. Fuzzy` quá phổ biến nên kéo Lift của mọi cặp xuống. Khuyến nghị bán chéo ở mục 2 dựa trên Confidence và biên lợi nhuận, không dựa trên Lift.
3. **Chưa có dữ liệu lý do hoàn hàng.** Bảng `order_item_refunds` không có trường lý do, lô hàng hay nhà cung cấp. Các nguyên nhân nêu ở phần hoàn hàng là **giả thuyết cần kiểm chứng**, không phải kết luận.

## 8. Cấu trúc repo

```
smarttoys-ecommerce-analytics/
├── README.md
├── requirements.txt
├── notebooks/
│   └── smarttoys_business_review.ipynb    # Toàn bộ phân tích
├── data/
│   └── raw/                                # 6 file nguồn
└── reports/
    ├── SmartToys_Business_Review.pdf       # Báo cáo slide
    ├── SmartToys_Business_Review.pptx
    └── figures/                            # 20 biểu đồ PNG
```

## 9. Cách chạy lại

```bash
git clone https://github.com/[username]/smarttoys-ecommerce-analytics.git
cd smarttoys-ecommerce-analytics
pip install -r requirements.txt
jupyter notebook notebooks/smarttoys_business_review.ipynb
```

Notebook tự nhận môi trường: chạy trên Google Colab thì mount Drive, chạy local thì dùng đường dẫn tương đối trong repo. Hàm `load()` tự nhận cả file `.csv` lẫn `.csv.gz`.

---

*Thực hiện bởi Ngô Đức Duy · https://www.linkedin.com/in/duyngoduyngo/ · duyngoduyngo@gmail.com *
