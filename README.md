# DataMinds - FreshRetailNet-50K Forecasting Pipeline
---
## 1. Giới thiệu
Dự án này xây dựng một pipeline dự báo doanh số bán lẻ (Daily Sales Forecasting) dựa trên FreshRetailNet-50K, bộ dữ liệu quy mô lớn được công bố trên HuggingFace.
Mục tiêu là:
- Làm sạch dữ liệu bán lẻ nhiều thành phần (store, product, weather, promotion…)
- Xây dựng đặc trưng (feature engineering) theo thời gian (lag features)
- Train nhiều mô hình học máy
- So sánh hiệu suất mô hình (RMSE, R²)
- Vẽ đồ thị phân tích kết quả
- Dự báo thực nghiệm cho 1 store – 1 product cụ thể

## 2. Cấu trúc thư mục
```
├── data_EDA.ipynb                     # Notebook phân tích dữ liệu ban đầu (EDA)
├── data_preprocessing_modelling.ipynb # Notebook chính: tiền xử lý → train models → evaluation
└── README.md
```              
## 3. Kết quả so sánh 
<img width="1390" height="590" alt="image" src="https://github.com/user-attachments/assets/3a274cf7-e38f-4abe-aa28-563eb1a40d19" />
**LightGBM là mô hình tốt nhất.**

## 4. Thảo luận kết quả
- LightGBM đạt hiệu suất tốt nhất nhờ khả năng học phi tuyến mạnh và xử lý dữ liệu nhiều chiều.
- XGBoost ổn định và là mô hình thay thế phù hợp; Random Forest cho kết quả khá nhưng yếu hơn Boosting.
- LSTM hoạt động kém do dữ liệu không phải chuỗi thời gian liên tục theo từng store–product.
- Quy trình tiền xử lý, làm sạch dữ liệu và xây dựng lag features cải thiện đáng kể chất lượng dự báo.

## 5. Những đóng góp chính
- Xây dựng pipeline hoàn chỉnh: tiền xử lý → phục hồi nhu cầu tiềm ẩn → tạo đặc trưng → huấn luyện → đánh giá mô hình.
- Thực hiện so sánh toàn diện giữa nhiều mô hình (RF, XGB, LGB, LSTM, Ensemble).
- Xác định LightGBM là mô hình tối ưu cho dự báo doanh số bán lẻ ngắn hạn.
- Gợi ý khả năng ứng dụng mô hình trong thực tế: tối ưu tồn kho, lập kế hoạch nhập hàng, chính sách giá, phòng tránh thiếu hàng.
- Làm tài liệu tham khảo hữu ích cho các bài toán dữ liệu lớn trong ngành bán lẻ.

## 6. Hạn chế
- Dữ liệu không theo chuỗi liên tục → mô hình LSTM không phát huy hiệu quả.
- Hyperparameter tuning mới ở mức cơ bản, chưa áp dụng tối ưu nâng cao.
- Bước phục hồi nhu cầu tiềm ẩn còn đơn giản, chưa nắm bắt được toàn bộ yếu tố ảnh hưởng.
- Thiếu dữ liệu ngoại sinh như kinh tế vĩ mô, nhân khẩu học, đối thủ cạnh tranh.
  
## 7. Hướng phát triển
- Tổ chức lại dữ liệu thành chuỗi thời gian hoàn chỉnh cho từng store–product để áp dụng tốt hơn các mô hình deep learning (LSTM, GRU, TFT...).
- Thực hiện hyperparameter tuning nâng cao (Bayesian Optimization, Optuna, Hyperband).
- Bổ sung biến ngoại sinh: dữ liệu vĩ mô, dân cư, traffic, đối thủ, xu hướng online.
- Thử nghiệm ensemble nâng cao: stacking, blending, meta-learning.
- Triển khai mô hình realtime forecasting để hỗ trợ vận hành thực tế (nhập hàng, phân bổ tồn kho, chính sách giảm giá).
