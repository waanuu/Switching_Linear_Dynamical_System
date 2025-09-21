# Switching Linear Dynamical System (SLDS) with HMM & Kalman Filter

📌 **Mục tiêu:**  
Triển khai mô hình **Switching Linear Dynamical System (SLDS)** kết hợp **Hidden Markov Model (HMM)** và **Kalman Filter** để mô hình hóa hệ thống động học đa chế độ.

---

## 📂 Cấu trúc dữ liệu

- **Slds_data.csv**: chứa các cột sau
  - `Time`: chỉ số thời gian
  - `Mode`: chế độ ẩn (hidden state)
  - `X_Position`: vị trí X
  - `Y_Position`: vị trí Y
  - `VX`: vận tốc X
  - `VY`: vận tốc Y

---

## 🔹 Hidden Markov Model (HMM)

- **Ý tưởng**:  
  Hệ thống có nhiều chế độ (mode) chuyển động khác nhau, ví dụ:
  - `Mode 0`: đứng yên / chuyển động chậm / quay đầu
  - `Mode 1`: chuyển động thẳng nhanh / đi đường chính  

  Mode là **trạng thái ẩn**, ta chỉ quan sát được vận tốc (`VX`, `VY`) để suy luận.

- **Cách hoạt động**:
  - Trạng thái ẩn = Mode
  - Quan sát = Vận tốc (VX, VY)
  - HMM học được:
    - Phân phối Gaussian đặc trưng cho mỗi mode
    - Xác suất chuyển đổi giữa các mode
    - Xác suất ban đầu của mode
## 🔹 Kalman Filter

Ý tưởng:
Ước lượng trạng thái liên tục (như vị trí) từ chuỗi quan sát nhiễu.
Mỗi chế độ (mode) sẽ có một Kalman Filter riêng.

Các bước chính:

Tạo Kalman Filter cho từng chế độ.

Ước lượng trạng thái hệ thống dựa trên quan sát.

Nếu không đủ dữ liệu → fallback giữ nguyên quan sát.
