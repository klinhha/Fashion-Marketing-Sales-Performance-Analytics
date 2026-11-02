# [POWER BI] Fashion Marketing Sales Performance Analytics
## I. Introduction
This **Power BI dashboard** provides an overview of **fashion business performance** by integrating _sales, product, and digital marketing campaign data_. It enables users to **monitor** revenue, profitability, advertising efficiency, and product performance to **support data-driven business decisions**.
## II. Objectives
- **Evaluate business performance**: Monitor revenue, profit, profit margin, orders, and average order value.
- **Analyze marketing effectiveness**: Assess campaign performance using ROAS, CPC, CPM, CTR, and advertising revenue.
- **Identify product opportunities**: Compare product categories based on sales, advertising spend, and order performance.
- **Track performance trends**: Analyze weekly changes in revenue, profit, advertising costs, and campaign engagement.
- **Support budget optimization**: Identify effective campaigns and products to improve advertising investment decisions.
## III. Project Outcome
- **Advertising-driven sales**: Advertising sales contribute a larger share of total revenue than direct sales, highlighting the importance of marketing campaigns to business performance.
- **Product performance**: Váy Chiết Eo Xoè and Áo Tách Set generate strong advertising revenue, while Váy Chiết Eo Ôm demonstrates particularly strong advertising efficiency.
- **Campaign optimization**: ROAS varies considerably across campaigns, indicating opportunities to reallocate budgets from underperforming campaigns to more effective ones.
- **Weekly performance monitoring**: Revenue, profit, and advertising costs fluctuate over time, emphasizing the need for continuous performance tracking.
- **Data-driven decisions**: The dashboard enables stakeholders to evaluate business results and identify opportunities to improve marketing efficiency and product profitability.
## IV. Data Structure & Relationships
### 1. Data Structure
- **Order** - Contains overall sales transaction data, including revenue from both advertising and direct sales.
- **mkt_camp_by_sku** - Contains advertising performance data at campaign and product level, including advertising spend and product-related sales information.
- **mkt_camp_cost** - Contains marketing campaign expenditure, budget, and advertising delivery metrics.
- **danh_muc_san_pham** - Contains product master data used to analyze sales and marketing performance by product and category.

## Dataset Structure

The dataset consists of four main tables covering marketing campaign performance, product-level advertising costs, customer orders, and product information.

| Table | Records | Columns | Description |
|---|---:|---:|---|
| `mkt_camp_by_sku_cost` | 3,874 | 37 | Campaign performance and cost allocation by product/SKU |
| `mkt_camp_cost` | 854 | 10 | Daily marketing campaign costs and performance |
| `order` | 3,451 | 22 | Customer order and transaction details |
| `danh sach san pham` | 2,250 | 16 | Product details, pricing, and attributes |

### Data Dictionary

<details>
<summary><strong>Table 1: mkt_camp_by_sku_cost</strong> (3,874 records)</summary>

Contains marketing campaign performance data allocated across individual products/SKUs, including advertising costs, engagement, customer messages, and sales-related metrics.

| Column Name | Data Type | Description |
|---|---|---|
| `Tên chiến dịch` | VARCHAR | Name of the marketing campaign. |
| `Ngày` | DATE | Date of the campaign performance record. |
| `Đơn vị tiền tệ` | VARCHAR | Currency used for campaign spending. |
| `Số tiền đã chi tiêu (VND)` | DECIMAL | Total advertising spend in VND. |
| `Phân phối chiến dịch` | VARCHAR | Campaign delivery status. |
| `Ngân sách chiến dịch` | DECIMAL | Campaign budget. |
| `Loại ngân sách chiến dịch` | VARCHAR | Campaign budget type, such as Daily. |
| `Lần bắt đầu cuộc trò chuyện qua tin nhắn` | INT | Number of messaging conversations initiated. |
| `Bình luận về bài viết` | INT | Number of comments on campaign posts. |
| `CPM` | DECIMAL | Cost per 1,000 impressions. |
| `CPC` | DECIMAL | Cost per click. |
| `CTR` | DECIMAL | Click-through rate. |
| `Tin nhắn mới` | INT | Number of new customer messages. |
| `Lượt hiển thị` | INT | Number of ad impressions. |
| `Mã Sản phẩm` | VARCHAR | Product identifier. |
| `Tên Sản Phẩm` | VARCHAR | Product name. |
| `Giá bán` | DECIMAL | Selling price of the product. |
| `Tên Bài Chạy` | VARCHAR | Name of the advertising post or ad. |
| `Bài chạy theo ngày` | VARCHAR | Ad name combined with its campaign date identifier. |
| `Tiền đã chạy Theo Sản phẩm` | DECIMAL | Advertising spend allocated to each product. |
| `Ngân sách Theo sản phẩm` | DECIMAL | Campaign budget allocated to each product. |
| `Inbox Theo AM` | DECIMAL | Number of inbox conversations allocated per product. |
| `Comments Theo AM` | DECIMAL | Number of comments allocated per product. |
| `Inbox + Comments Theo AM` | DECIMAL | Combined inbox and comment volume allocated per product. |
| `CP/KQ Theo AM` | DECIMAL | Cost per result allocated per product. |
| `CPM Theo AM` | DECIMAL | CPM allocated per product. |
| `CPC Theo AM` | DECIMAL | CPC allocated per product. |
| `CTR Theo AM` | DECIMAL | CTR allocated per product. |
| `Khách mới Theo AM` | DECIMAL | New customers/messages allocated per product. |
| `Khách cũ Theo AM` | DECIMAL | Existing customers/messages allocated per product. |
| `Lượt hiển thị Theo AM` | DECIMAL | Impressions allocated per product. |
| `SL bán tổng` | INT | Total quantity sold for the product on the recorded date. |
| `Tổng CMT trên SP` | DECIMAL | Total comments allocated per product. |
| `SL bán được phân bổ theo tỉ lệ` | DECIMAL | Product sales quantity allocated based on a ratio. |
| `SL tồn` | INT | Remaining product inventory. |
| `Tổng SL bán theo Campaign` | DECIMAL | Total sales quantity associated with the campaign. |

</details>

<details>
<summary><strong>Table 2: mkt_camp_cost</strong> (854 records)</summary>

Contains daily marketing campaign spending and advertising performance metrics.

| Column Name | Data Type | Description |
|---|---|---|
| `Tên chiến dịch` | VARCHAR | Name of the marketing campaign. |
| `Ngày` | DATE | Date of the campaign performance record. |
| `Số tiền đã chi tiêu` | DECIMAL | Total advertising spend. |
| `Phân phối chiến dịch` | VARCHAR | Campaign delivery status. |
| `Ngân sách chiến dịch` | DECIMAL | Campaign budget. |
| `Loại ngân sách chiến dịch` | VARCHAR | Campaign budget type, such as Daily. |
| `CPM (Chi phí trên mỗi 1.000 lần hiển thị)` | DECIMAL | Cost per 1,000 ad impressions. |
| `CPC (Chi phí trên mỗi lượt click vào liên kết)` | DECIMAL | Cost per link click. |
| `Lượt hiển thị` | INT | Number of ad impressions. |
| `Click` | INT | Number of ad clicks. |

</details>

<details>
<summary><strong>Table 3: order</strong> (3,451 records)</summary>

Contains customer order information, product details, transaction values, and order statuses.

| Column Name | Data Type | Description |
|---|---|---|
| `ID` | INT | Order identifier. |
| `Thời gian` | DATETIME | Date and time when the order was recorded. |
| `Nguồn` | VARCHAR | Source or channel through which the order was created. |
| `Tên khách hàng` | VARCHAR | Customer name. |
| `Mã khách hàng` | VARCHAR | Customer identifier. |
| `Cấp độ khách hàng` | VARCHAR | Customer membership or loyalty level. |
| `Sinh nhật` | DATE / VARCHAR | Customer date of birth. |
| `Thành phố` | VARCHAR | Customer's city. |
| `Quận huyện` | VARCHAR | Customer's district. |
| `Phường xã` | VARCHAR | Customer's ward or commune. |
| `Sản phẩm` | VARCHAR | Ordered product, including its variant where applicable. |
| `Mã sản phẩm cha` | VARCHAR | Parent product identifier. |
| `Tên sản phẩm cha` | VARCHAR | Parent product name. |
| `Mã sản phẩm` | VARCHAR | Product/SKU identifier. |
| `Mã vạch` | VARCHAR | Product barcode. |
| `Danh mục sản phẩm` | VARCHAR | Product category. |
| `Chiết khấu` | DECIMAL | Discount applied to the order item. |
| `Giá` | DECIMAL | Selling price recorded for the order item. |
| `Số lượng` | INT | Quantity ordered. |
| `Giá vốn` | DECIMAL | Product cost recorded for the order item. |
| `Trạng thái` | VARCHAR | Current order status. |
| `Lý do hủy` | VARCHAR | Reason for order cancellation. |

</details>

<details>
<summary><strong>Table 4: danh sach san pham</strong> (2,250 records)</summary>

Contains product master data, including product identifiers, pricing, categories, brands, and product attributes.

| Column Name | Data Type | Description |
|---|---|---|
| `ID` | INT | Product record identifier. |
| `Mã vạch` | VARCHAR | Product barcode. |
| `Loại sản phẩm` | VARCHAR | Product type. |
| `Mã sản phẩm` | VARCHAR | Product/SKU identifier. |
| `Tên sản phẩm` | VARCHAR | Product name. |
| `Giá nhập` | DECIMAL | Purchase price of the product. |
| `Giá bán` | DECIMAL | Selling price of the product. |
| `Giá bán + VAT` | DECIMAL | Selling price including VAT. |
| `Giá vốn` | DECIMAL | Product cost. |
| `Trạng thái` | VARCHAR | Product status. |
| `Mã danh mục` | VARCHAR | Product category identifier. |
| `Danh mục` | VARCHAR | Product category name. |
| `Mã danh mục nội bộ` | VARCHAR | Internal product category identifier. |
| `Thương hiệu` | VARCHAR | Product brand. |
| `Màu sắc` | VARCHAR | Product color. |
| `Chất liệu` | VARCHAR | Product material. |

</details>

### 2. Data Relationships
<img width="400" height="356" alt="Screenshot 2026-10-14 221702" src="https://github.com/user-attachments/assets/bc80e5ac-7ac2-441d-8d27-a539bddb5b8c" />

| **From Table**          | **To Table**          | **Join Key**                         | **Relationship Type**                                      |
|-------------------------|-----------------------|--------------------------------------|------------------------------------------------------------|
| `danh_muc_san_pham`     | `Order`               | `Mã sản phẩm`                        | One-to-Many (one product can appear in multiple orders)    |
| `danh_muc_san_pham`     | `mkt_camp_by_sku`      | `Mã sản phẩm`                        | One-to-Many (one product can appear in multiple campaigns)|
| `mkt_camp_cost`         | `mkt_camp_by_sku`      | `Tên chiến dịch`             | One-to-Many (one campaign can have multiple product records)|
| `Dim_Date`              | `Order`               | `Date`                  | One-to-Many (one date can have multiple order records)     |
| `Dim_Date`              | `mkt_camp_by_sku`      | `Date`                      | One-to-Many (one date can have multiple marketing records) |

## V. Design Thinking Process

### Stage 1. Empathize
<img width="2000" height="468" alt="stage1_empathize_5w1h-v6" src="https://github.com/user-attachments/assets/51cb7ad0-ba91-4b02-a08f-f23a34dcff47" />
<img width="2000" height="506" alt="stage1_empathize_map-v6" src="https://github.com/user-attachments/assets/c45e6a66-935a-4e99-be28-040d8760db58" />

### Stage 2. Define Point of View
<img width="2000" height="826" alt="stage2_define_pov_northstar-v6" src="https://github.com/user-attachments/assets/3c1a49f9-c8f1-4597-b994-a8e69b9d238c" />

### Stage 3. Ideate
<img width="2000" height="640" alt="stage3_ideate_brainstorming-v6" src="https://github.com/user-attachments/assets/1a3e26d4-bbdc-439b-bc4d-d52f64031c8a" />
<img width="2000" height="521" alt="stage3_ideate_structure_idea-v6" src="https://github.com/user-attachments/assets/e7126dc7-414b-4c50-9ebf-bd2d9172a87b" />

## VI. Visualization
### 1. Executive Summary
<img width="1375" height="782" alt="Screenshot 2026-10-16 at 01 26 09" src="https://github.com/user-attachments/assets/e4b47310-7892-4bc0-be29-894d28098e35" />

### Insights
- **Advertising sales** contribute **63.34%** of total revenue, while **direct sales** account for **36.66%**. → The business **relies** heavily on **advertising campaigns** to generate sales, making marketing efficiency a **key factor** in overall performance.
- **Total revenue** reaches **4,774 million**, while **total profit** is **196 million**, resulting in a profit margin of **4.10%**. → Despite strong sales, the low margin suggests that **costs** need **closer monitoring** to improve profitability.
- Revenue and profit vary across the observed weeks, with **revenue peaking in Week 3** and declining afterward. → **Sales performance** is **not consistent**, highlighting the need to **investigate** weekly demand changes and campaign effectiveness.
- The dashboard shows **substantial differences** between the **highest**- and **lowest-ROAS campaigns**. Some campaigns deliver **strong returns**, while others generate **little** or **no return**. → **Budget reallocation** toward effective campaigns could improve marketing efficiency.
- **Áo Tách Set** and **Váy Chiết Eo Xoè** generate **substantial revenue**, while several other categories contribute considerably less. → **Prioritizing** strong-performing categories while **reviewing** weaker ones could improve sales and budget allocation.

### 2. Marketing Campaign Performance
<img width="1484" height="846" alt="Screenshot 2026-10-16 at 01 38 52" src="https://github.com/user-attachments/assets/1a444b97-44f2-4088-afee-063bc41309f6" />

### Insights
- **Advertising revenue** reaches **3,023.45 million**, with an overall **ROAS of 7.67**, generated from **394 million** in **ad spend**. → Marketing campaigns are overall efficient at generating returns relative to direct advertising costs.
- The overall **CTR** is **0.82%**, meaning only **a small proportion** of **impressions** result in clicks. → **Improving** creative content, **audience targeting**, and campaign relevance may increase engagement.
- Weekly ROAS varies, reaching its **highest** level in **Week 5** and its **lowest** in **Week 2**. → **Campaign performance** should be **monitored** **regularly** to identify effective periods and adjust spending accordingly.
- **CPC** and **CPM** vary across campaigns, reflecting **differences** in **click** costs and **impression** costs. → **Combining** cost metrics with ROAS and order performance provides a more complete basis for evaluating campaign efficiency.
- The ROAS by Campaign chart shows **substantial differences** in advertising efficiency, with some **campaigns** achieving ROAS **above 40** while **others** remain **below 1**. → This highlights opportunities to **reallocate** budgets toward **high-performing campaigns** and **review** or **optimize** campaigns that **generate insufficient revenue** relative to advertising spend.

### 3. Product & Category Performance
<img width="1432" height="818" alt="Screenshot 2026-10-16 at 02 05 33" src="https://github.com/user-attachments/assets/81a653af-aa68-40e3-9eba-52bb834f2234" />

### Insights
- **Váy Chiết Eo Xoè** brought in **996 Mio.** in ad revenue and **Áo Tách Set** brought in **876 Mio.**, significantly outpacing other product types. → Dresses and matching top sets are **the dominant product choices** driving consumer preference.
- **Váy Chiết Eo Ôm** achieves a ROAS of **22.09**, the **highest** among the listed categories. → **Consider** **scaling** its budget carefully while monitoring performance.
- However, **Áo Tách Set** generates **875.75M** in ad revenue with a **ROAS** of **8.53**, compared with **22.09** for **Váy Chiết Eo Ôm**. → **Evaluate** both revenue scale and advertising efficiency when allocating budgets.
- Ad revenue streams across categories **expanded sharply** during **Week 2** and **Week 3** before **tapering off** in **Week 4** and **Week 5**. → Consumer interest **spikes** mid-campaign period, **aligning** closely with **heightened marketing push**.

### 4. Product Analysis Drill-Through
An interactive **drill-through dashboard page** analyzing **detailed** campaign performance, weekly spend-revenue trends, and day-of-week ROAS efficiency for **specific fashion products**.

<img width="651" height="371" alt="Screenshot 2026-10-14 221247" src="https://github.com/user-attachments/assets/7ca7ed12-1949-4773-9f22-0e70b49c72bd" />

## VII. Conclusions & Recommendations
### 1. Conclusions
- Advertising generates **3,023.45M**, accounting for **63.34%** of total revenue **(4,774M)**, highlighting its **important role** in driving sales.
- Overall **advertising efficiency** is **solid** with an average **ROAS of 7.67**, proving that marketing campaigns **successfully** capture consumer demand.
- **Váy Chiết Eo Xoè** generates the **highest ad revenue (996.25M)**, while **Áo Tách Set** records the **most orders (534)**. **Váy Chiết Eo Ôm** achieves the **highest category ROAS (22.09)**.
- ROAS varies **considerably** across campaigns and weeks, indicating opportunities to **improve** advertising performance through **more targeted** budget allocation.
- **High-revenue categories** may require **greater** advertising investment, while some **smaller** categories and products can deliver **stronger returns** with **lower spend**.
### 2. Recommendations
- **Scale** marketing budgets for **top-performing campaigns** and **high-ROAS products** (e.g., **Váy Chiết Eo Ôm** at 22.09 ROAS), while **cutting** spend on **zero-ROAS** or **underperforming** items.
- **Continue** monitoring **Váy Chiết Eo Xoè** and **Áo Tách Set** because of their **substantial revenue** and **order contributions**.
- **Track** ROAS, CPC, CPM, and CTR **regularly** to **identify** performance **changes** early and **adjust** campaigns accordingly.
- **Address** low click-through rates (**CTR at 0.82%**) by **testing** new ad creatives to **better convert** massive impression volumes into active customer clicks.
- **Shift** ad spend away from **low-performing days** (such as Sunday, which had a low ROAS of 3.88) toward **high-efficiency** mid-week days like Wednesday and Thursday (ROAS ~19.8)
- **Compare** ad revenue, spend, ROAS, and orders to **identify** products that **deserve** more investment and those that **need** optimization or reduced spending.
