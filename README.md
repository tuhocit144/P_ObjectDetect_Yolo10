# YOLOv10 Helmet Safety Detection

## Giới thiệu
Trong phần này, chúng ta sẽ tìm hiểu cách sử dụng YOLOv10 bao gồm việc sử dụng pre-trained model và huấn luyện (fine-tuning) YOLOv10 trên bộ dữ liệu Helmet Safety Detection.

Trong project này, chúng ta sẽ xây dựng một chương trình phát hiện các nhân viên có đeo mũ bảo vệ trong công trường hay không? Mô hình mà chúng ta sử dụng sẽ là mô hình YOLOv10.

## Input và Output
- **Input**: Một tấm ảnh.
- **Output**: Tọa độ (bounding box) của các nhân viên và phần mũ bảo hiểm.

## Các bước thực hiện
Tổng quan, các bước thực hiện trong project của chúng ta để hoàn thiện hệ thống Helmet Safety Detection bao gồm:

### Sử dụng Google Colab
Để thuận tiện trong việc sử dụng YOLOv10, chúng ta sẽ dùng Google Colab làm môi trường cài đặt và thực thi code:

1. Truy cập vào [Google Colab](https://colab.research.google.com/)
2. Khởi tạo notebook mới
3. Thay đổi runtime của notebook từ CPU thành GPU.
4. Khởi động notebook để có thể thực thi các dòng lệnh Python.

### Cài đặt và sử dụng pre-trained model

#### Tải mã nguồn YOLOv10 từ GitHub
Trên Google Colab, khởi tạo một code cell và sử dụng lệnh:
```bash
!git clone https://github.com/THU-MIG/yolov10.git
```
#### Cài đặt các thư viện cần thiết
Mã nguồn YOLOv10 được xây dựng bằng rất nhiều các thư viện Python khác nhau. Đảm bảo bạn đã cài đặt tất cả các thư viện cần thiết.

#### Tải trọng số của pre-trained models
Tải file pretrained model tại đây và đặt file đã tải vào thư mục ./yolov10.
```bash
!wget https://github.com/THU-MIG/yolov10/releases/download/v1.1/yolov10n.pt
```

#### Khởi tạo mô hình
Để khởi tạo mô hình với trọng số vừa tải về, chạy đoạn code sau:

```bash
from ultralytics import YOLOv10

MODEL_PATH = 'yolov10n.pt'
model = YOLOv10 ( MODEL_PATH )
```

#### Tải ảnh cần dự đoán,  test mô hình trên một ảnh bất kỳ.
```bash
! gdown '1tr9PSRRdlC2pNir7jsYugpSMG-7v32VJ' -O './images/'
```
#### Dự đoán
Để chạy dự đoán cho ảnh đã tải về,  truyền đường dẫn ảnh vào mô hình như đoạn code sau:
```bash
IMG_PATH = './images/HCMC_Street.jpg'
result = model ( source = IMG_PATH )[0]
```
#### Lưu kết quả dự đoán. Để lưu lại ảnh đã được dự đoán, chạy đoạn code sau:
```bash

result.save ('./images/HCMC_Street_predict.png')
```
