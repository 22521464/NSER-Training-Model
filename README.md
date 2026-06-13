# Speech Emotion Recognition — Train Models

Mã nguồn huấn luyện các mô hình Nhận diện Cảm xúc Giọng nói (Speech Emotion Recognition) phục vụ đề tài khóa luận tốt nghiệp.

## Tổng quan

Huấn luyện các mô hình nhận diện cảm xúc giọng nói từ các bộ dataset và phân loại âm thanh vào một trong năm lớp cảm xúc: **angry**, **disgust**, **fear**, **sad**, **neutral**.

## Cấu trúc thư mục

```
├── CNN-LSTM/                  # Notebook huấn luyện mô hình CNN-LSTM
├── Conformer/                 # Notebook huấn luyện mô hình Conformer
├── dataset step 1/            # Đặc trưng MFCC — thực nghiệm nhóm d (d01–d09)
├── dataset step 2/            # Đặc trưng MFCC — thực nghiệm nhóm f (f01–f22)
├── dataset step 3/            # Đặc trưng MFCC — thực nghiệm nhóm m (m01–m05)
└── README.md
```

## Pipeline xử lý

1. **Tiền xử lý** — lọc nhãn, chuẩn hóa tần số lấy mẫu về 16kHz
2. **Tăng cường dữ liệu** — thêm nhiễu trắng, dịch chuyển thời gian, dịch chuyển cao độ, mô phỏng âm vang phòng
3. **Trích xuất đặc trưng** — 40 hệ số MFCC, lấy trung bình theo trục thời gian
4. **Huấn luyện** — CNN-LSTM, Conformer, Transformer, DNN

## Các mô hình

| Mô hình | Accuracy | Ghi chú |
|---|---|---|
| Wav2Vec2 (fine-tuned) | 93.06% | Lưu tại HuggingFace Hub |
| DNN | 92.01% | Huấn luyện từ đầu |
| HuBERT (fine-tuned) | 91.33% | Lưu tại HuggingFace Hub |
| Transformer | 90.86% | Huấn luyện từ đầu |
| CNN-LSTM | 90.74% | Huấn luyện từ đầu |
| Conformer | 83.80% | Huấn luyện từ đầu |

Mô hình HuBERT và Wav2Vec2 sau fine-tuned được công khai tại:
- [TienGiang/ser-hubert-ravdess](https://huggingface.co/TienGiang/ser-hubert-ravdess)
- [TienGiang/ser-wav2vec2-ravdess](https://huggingface.co/TienGiang/ser-wav2vec2-ravdess)

## Môi trường

- Python 3.9
- TensorFlow 2.13
- librosa
- scikit-learn
- pyroomacoustics

## Tác giả

Giang Mỹ Tiên - 22521464
Huỳnh Ngọc Trang - 22521510
Khóa luận tốt nghiệp — Trường Đại học Công nghệ Thông tin, ĐHQG TP.HCM