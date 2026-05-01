# Datathon 2026 Round 1 - Main Pipeline

- `MainPipeline.ipynb`: notebook chính
- `dataset`: dữ liệu đầu vào mà notebook đang sử dụng

## Mục tiêu

`MainPipeline.ipynb` xây dựng pipeline dự báo `Revenue` và `COGS` theo hướng:

1. Tạo seasonal profile từ giai đoạn ổn định gần nhất.
2. Ước lượng yearly level bằng YoY factor.
3. Huấn luyện `LightGBM` trên phần residual.
4. Validate trên năm 2022 để chọn cấu hình tốt nhất.
5. Retrain trên toàn bộ dữ liệu lịch sử rồi forecast cho giai đoạn cần nộp bài.

## Cấu trúc thư mục

```text
.
|-- MainPipeline.ipynb
|-- README.md
|-- .gitignore
`-- dataset/
    `-- sales.csv
```

## Yêu cầu môi trường

- Python `3.10+` khuyến nghị
- Jupyter Notebook hoặc JupyterLab
- Các thư viện:
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `lightgbm`

Cài nhanh:

```bash
pip install jupyter pandas numpy scikit-learn lightgbm
```

## Cách chạy local

1. Clone repo và mở terminal tại thư mục gốc của repo.
2. Cài các thư viện cần thiết.
3. Chạy Jupyter:

```bash
jupyter notebook
```

4. Mở file `MainPipeline.ipynb`.
5. Chọn `Run All` để chạy toàn bộ notebook theo đúng thứ tự.

Notebook sẽ tự dùng:

- Input: `dataset/sales.csv`
- Output: `submission_main_pipeline_refactored.csv`

## Cách chạy trên Google Colab

Notebook đã có sẵn logic nhận diện Colab.

1. Upload `MainPipeline.ipynb` lên Colab.
2. Đảm bảo file `sales.csv` nằm đúng đường dẫn mà notebook đang kiểm tra trong Google Drive:

```text
/content/drive/MyDrive/Colab Notebooks/DATATHON 2026/DATA/datathon-2026-round-1/sales.csv
```

3. Chạy toàn bộ notebook.

Nếu không dùng đúng cấu trúc thư mục trên, hãy sửa các biến đường dẫn ở cell cấu hình đầu tiên:

- `COLAB_DATA_DIR`
- `COLAB_OUT_FILE`

## Đầu vào và đầu ra

Đầu vào bắt buộc:

- `dataset/sales.csv`
- File này cần có các cột mà notebook đang dùng trực tiếp: `Date`, `Revenue`, `COGS`

Đầu ra sinh ra sau khi chạy:

- `submission_main_pipeline_refactored.csv`
- Gồm 3 cột:
  - `Date`
  - `Revenue`
  - `COGS`

## Lưu ý

- Hãy chạy notebook từ thư mục gốc của repo để đường dẫn `dataset/sales.csv` hoạt động đúng.
- Notebook hiện đã được rút gọn, không còn phụ thuộc vào các notebook thử nghiệm hay script calibration phụ khác.
- Nếu muốn thay khoảng forecast, năm stable, hoặc tập validate, hãy chỉnh các hằng số ở cell cấu hình đầu tiên.

## Tóm tắt nhanh

Nếu chỉ cần chạy nhanh:

```bash
pip install jupyter pandas numpy scikit-learn lightgbm
jupyter notebook
```

Sau đó mở `MainPipeline.ipynb` và chọn `Run All`.
