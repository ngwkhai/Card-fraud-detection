# Phát Hiện Gian Lận Thẻ Tín Dụng

Dự án này sử dụng các kỹ thuật học máy để phát hiện gian lận thẻ tín dụng. Các bước trong dự án bao gồm khám phá dữ liệu, tiền xử lý dữ liệu, kỹ thuật tạo đặc trưng, huấn luyện mô hình và đánh giá hiệu suất. Dự án tập trung vào việc xử lý dữ liệu mất cân bằng và tối ưu hóa các mô hình để phát hiện gian lận hiệu quả.

## Cấu Trúc Dự Án

Dự án được tổ chức theo cấu trúc module, mỗi bước trong quy trình xử lý dữ liệu và huấn luyện mô hình được chia thành các notebook riêng biệt. Dưới đây là cấu trúc thư mục của repo:

```
Card-fraud-detection/
├── data/                # Dữ liệu gốc và dữ liệu đã xử lý
│   ├── generated/      # Dữ liệu đã được xử lý
│   ├── processed/      # Dữ liệu đã làm sạch và xử lý
│   ├── raw/           # Dữ liệu gốc
│   ├── splits/        # Dữ liệu đã chia cho huấn luyện và kiểm tra
│── models/             # Các mô hình đã huấn luyện lưu dưới dạng .pkl
│── notebooks/          # Các notebook Jupyter cho từng bước
│   ├── 1_data_exploration.ipynb    # Khám phá và trực quan hóa dữ liệu
│   ├── 2_data_preprocessing.ipynb  # Tiền xử lý dữ liệu
│   ├── 3_feature_engineering.ipynb # Tạo đặc trưng và chuyển đổi
│   ├── 4_train_test_split.ipynb    # Chia dữ liệu thành tập huấn luyện và kiểm tra
│   ├── 5_model_training.ipynb      # Huấn luyện các mô hình
│   ├── 6_model_evaluation.ipynb    # Đánh giá mô hình và các chỉ số hiệu suất
│── reports/            # Báo cáo và kết quả phân tích
│   ├── figures/       # Các biểu đồ trực quan
│   ├── tables/       # Các bảng dữ liệu (ví dụ: kết quả đánh giá mô hình)
│   ├── evaluation_results.csv  # Tệp CSV chứa kết quả đánh giá mô hình
├── .gitignore         # Tệp ignore của Git
├── README.md          # Tài liệu hướng dẫn
├── requirements.txt   # Các gói phụ thuộc Python
```

## Mô Tả Dự Án

Dự án này được xây dựng với mục tiêu phát hiện gian lận thẻ tín dụng bằng cách sử dụng các thuật toán học máy. Dữ liệu sử dụng trong dự án là các giao dịch thẻ tín dụng của các chủ thẻ ở Châu Âu vào tháng 9 năm 2013, bao gồm các giao dịch gian lận và không gian lận. Mục tiêu là xây dựng một mô hình có khả năng phát hiện giao dịch gian lận với độ chính xác cao mặc dù dữ liệu rất mất cân bằng.

### Các Bước Chính trong Dự Án

1. **Khám Phá Dữ Liệu**:
   - Khám phá và trực quan hóa dữ liệu.
   - Phân tích sự phân phối của các đặc trưng, đặc biệt là sự mất cân bằng lớp giữa gian lận và không gian lận.
   
2. **Tiền Xử Lý Dữ Liệu**:
   - Xử lý dữ liệu thiếu và các ngoại lệ.
   - Chuẩn hóa/chuẩn hóa dữ liệu, bao gồm cả chuyển đổi log nếu cần thiết.
   
3. **Kỹ Thuật Tạo Đặc Trưng**:
   - Tạo các đặc trưng mới như ngày và giờ từ thời gian giao dịch.
   - Nghiên cứu mối quan hệ giữa các đặc trưng và xác định những đặc trưng mới có thể cải thiện hiệu suất mô hình.
   
4. **Huấn Luyện Mô Hình**:
   - Huấn luyện nhiều mô hình học máy (Hồi quy logistic, Cây quyết định, Rừng ngẫu nhiên, XGBoost) trên dữ liệu đã xử lý.
   - Giải quyết vấn đề mất cân bằng lớp bằng các kỹ thuật như SMOTE và ADASYN để cải thiện khả năng phát hiện gian lận của mô hình.
   
5. **Đánh Giá Mô Hình**:
   - Đánh giá hiệu suất của các mô hình bằng các chỉ số như độ chính xác, độ chính xác (precision), độ hồi phục (recall), điểm F1 và ROC-AUC.
   - Trực quan hóa đường cong ROC cho từng mô hình.

## Bắt Đầu

Để bắt đầu với dự án này, hãy làm theo các bước sau:

### 1. Cài đặt các phụ thuộc:

Đảm bảo bạn đã cài đặt Python 3.x. Sau đó, cài đặt các phụ thuộc bằng cách sử dụng lệnh sau:

```bash
pip install -r requirements.txt
```

### 2. Tải Dữ Liệu

Dữ liệu có thể được tìm thấy trong thư mục data/raw/. Nó được chia thành các phần:
- Dữ liệu raw chứa dữ liệu gốc.
- Các thư mục generated và processed chứa dữ liệu đã được xử lý.
- Thư mục splits chứa dữ liệu huấn luyện và kiểm tra.

### 3. Chạy Các Notebook

Để khám phá dữ liệu, tiền xử lý, tạo đặc trưng, huấn luyện mô hình và đánh giá chúng, bạn có thể chạy các notebook sau theo trình tự:
- 1_data_exploration.ipynb: Khám phá và trực quan hóa dữ liệu.
- 2_data_preprocessing.ipynb: Làm sạch dữ liệu và xử lý các giá trị thiếu, ngoại lệ, v.v.
- 3_feature_engineering.ipynb: Tạo các đặc trưng mới và kỹ thuật xử lý.
- 4_train_test_split.ipynb: Chia dữ liệu thành các tập huấn luyện và kiểm tra.
- 5_model_training.ipynb: Huấn luyện mô hình với dữ liệu đã xử lý.
- 6_model_evaluation.ipynb: Đánh giá mô hình và các chỉ số hiệu suất.

### 4. Kết Quả Mô Hình

Các mô hình đã huấn luyện được lưu trong thư mục models/ dưới dạng các tệp .pkl, và kết quả đánh giá được lưu trong tệp evaluation_results.csv trong thư mục reports/.

### 5. Biểu Đồ

Các biểu đồ được tạo ra trong quá trình khám phá và đánh giá sẽ được lưu trong thư mục reports/figures/.
