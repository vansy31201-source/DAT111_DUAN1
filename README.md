# DAT111_DUAN1 - Dự án Phân tích Hành vi Khách hàng

## 📋 Mô tả dự án

Dự án phân tích dữ liệu bán lẻ nhằm nghiên cứu và hiểu rõ hành vi mua sắm của khách hàng thông qua các giao dịch bán lẻ. Dự án sử dụng Power BI để trực quan hóa dữ liệu và phân tích các xu hướng, mẫu hành vi khách hàng.

## 📁 Cấu trúc thư mục

```
DAT111_DUAN1/
│
├── data_1.xlsx                  # File Excel chứa dữ liệu chính (nguồn dữ liệu)
│
├── retail_data.csv/              # Thư mục chứa dữ liệu CSV (tham khảo)
│   └── retail_data.csv          # File dữ liệu giao dịch bán lẻ (tham khảo)
│
├── retail_data_clean.pbix       # File Power BI đã được làm sạch dữ liệu
├── Retails.pbix                 # File Power BI phân tích dữ liệu bán lẻ
│
├── README.md                    # File hướng dẫn dự án (file này)
└── test.md                      # File ghi chú test
```

## 📊 Mô tả dữ liệu

File `data_1.xlsx` là nguồn dữ liệu chính chứa dữ liệu giao dịch bán lẻ với các thông tin sau:

### Các trường dữ liệu chính:

**Thông tin giao dịch:**
- `Transaction_ID`: Mã giao dịch
- `Date`, `Year`, `Month`, `Time`: Thông tin thời gian giao dịch
- `Total_Purchases`: Tổng số lần mua
- `Amount`: Số tiền giao dịch
- `Total_Amount`: Tổng số tiền

**Thông tin khách hàng:**
- `Customer_ID`: Mã khách hàng
- `Name`, `Email`, `Phone`: Thông tin liên hệ
- `Address`, `City`, `State`, `Zipcode`, `Country`: Địa chỉ
- `Age`, `Gender`: Nhân khẩu học
- `Income`: Thu nhập (Low/High)
- `Customer_Segment`: Phân khúc khách hàng (Regular/Premium)

**Thông tin sản phẩm:**
- `Product_Category`: Danh mục sản phẩm
- `Product_Brand`: Thương hiệu
- `Product_Type`: Loại sản phẩm
- `products`: Tên sản phẩm cụ thể

**Thông tin đơn hàng:**
- `Shipping_Method`: Phương thức vận chuyển
- `Payment_Method`: Phương thức thanh toán
- `Order_Status`: Trạng thái đơn hàng
- `Ratings`: Đánh giá (1-5)
- `Feedback`: Phản hồi khách hàng

## 🛠️ Công nghệ sử dụng

- **Power BI**: Phân tích và trực quan hóa dữ liệu
- **SQL**: 
  - ETL (Extract, Transform, Load) - Trích xuất, chuyển đổi và tải dữ liệu
  - Làm sạch dữ liệu (Data Cleaning)
  - Deduplicate - Loại bỏ dữ liệu trùng lặp
  - Backup dữ liệu
- **Excel**: Xử lý và phân tích dữ liệu cơ bản
- **CSV**: Lưu trữ dữ liệu giao dịch

## 📈 Cách sử dụng

### 1. Mở file Power BI

- Mở file `Retails.pbix` hoặc `retail_data_clean.pbix` bằng Power BI Desktop
- **Quan trọng**: Cập nhật parameter đường dẫn trong Power BI để trỏ tới file `data_1.xlsx`
  - Vào **Transform Data** → **Manage Parameters**
  - Cập nhật parameter với đường dẫn đầy đủ tới file `data_1.xlsx` (ví dụ: `D\DAT111_DUAN1\data_1.xlsx`)
  - Áp dụng thay đổi và refresh dữ liệu
- Khám phá các dashboard và báo cáo đã được tạo sẵn

### 2. Phân tích dữ liệu

- Sử dụng Power BI để tạo các biểu đồ và bảng phân tích
- Phân tích hành vi khách hàng theo các tiêu chí:
  - Phân khúc khách hàng
  - Sản phẩm phổ biến
  - Xu hướng theo thời gian
  - Phương thức thanh toán và vận chuyển

### 3. Quy trình ETL và làm sạch dữ liệu

- **SQL** được sử dụng để thực hiện quy trình ETL:
  - **Extract**: Trích xuất dữ liệu từ nguồn Excel (`data_1.xlsx`)
  - **Transform**: 
    - Làm sạch dữ liệu (xử lý giá trị null, định dạng dữ liệu)
    - Deduplicate - Loại bỏ các bản ghi trùng lặp
    - Chuẩn hóa dữ liệu
  - **Load**: Tải dữ liệu đã được xử lý vào database hoặc file đích
  - **Backup**: Tạo bản sao lưu dữ liệu trước và sau khi xử lý
- File `retail_data_clean.pbix` chứa dữ liệu đã được làm sạch thông qua quy trình ETL
- Có thể sử dụng file này để phân tích trực tiếp

## 📊 DAX Measures

Dự án sử dụng các DAX measures sau để phân tích và tính toán các chỉ số quan trọng:

### Measures về Giá trị đơn hàng và Doanh thu:
- **Average_Order_Value**: Giá trị trung bình của mỗi đơn hàng - tính bằng tổng doanh thu chia cho số lượng đơn hàng
- **Total_order**: Tổng số đơn hàng - đếm tổng số lượng giao dịch/đơn hàng
- **Total_Quantity**: Tổng số lượng sản phẩm - tổng số lượng sản phẩm đã bán

### Measures về Phân khúc khách hàng (RFM Analysis):
- **Avg_Frequency_Segment2**: Phân khúc tần suất mua hàng trung bình - phân loại khách hàng dựa trên tần suất mua hàng (thường xuyên, trung bình, ít)
- **Avg_Monetary_Segment2**: Phân khúc giá trị tiền tệ trung bình - phân loại khách hàng dựa trên tổng giá trị đã chi tiêu (cao, trung bình, thấp)
- **Avg_Recency_Segment2**: Phân khúc độ mới mua hàng trung bình - phân loại khách hàng dựa trên thời gian kể từ lần mua hàng cuối cùng (mới, trung bình, cũ)

### Measures về Giá trị khách hàng:
- **Customer_Lifetime_Value**: Giá trị vòng đời khách hàng - tổng giá trị mà một khách hàng mang lại cho doanh nghiệp trong chu kỳ 6 tháng 
- **Customer_Count2**: Số lượng khách hàng - đếm tổng số khách hàng duy nhất

### Measures về Tỷ lệ rời bỏ:
- **Churn Rate**: Tỷ lệ khách hàng rời bỏ - phần trăm khách hàng ngừng mua hàng hoặc không còn hoạt động trong một khoảng thời gian nhất định

## 📝 Ghi chú

- **Dữ liệu chính**: File `data_1.xlsx` là nguồn dữ liệu chính được sử dụng trong dự án
- File `retail_data.csv` có thể là bản sao hoặc dữ liệu tham khảo (nếu có)
- Các giá trị số có thể chứa dấu chấm (.) làm dấu phân cách hàng nghìn
- Cần xử lý dữ liệu trước khi phân tích để đảm bảo tính chính xác
- Đảm bảo cập nhật đúng đường dẫn parameter trong Power BI trỏ tới file `data_1.xlsx`

## 👤 Tác giả

Dự án DAT111 - Đồ án 1



----------------------------------------
