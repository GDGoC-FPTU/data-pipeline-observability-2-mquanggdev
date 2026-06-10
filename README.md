[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112855&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.quangtm@vinuni.edu.vn
**Name:** Trần Minh Quang

---

## Mo ta

Bài lab này xây dựng một ETL pipeline đơn giản cho dữ liệu sản phẩm. Pipeline đọc dữ liệu từ `raw_data.json`, kiểm tra và loại bỏ các record không hợp lệ, chuẩn hóa `category`, tính giá sau khi giảm 10%, thêm timestamp xử lý và lưu kết quả ra `processed_data.csv`. Bài lab cũng có phần quan sát chất lượng dữ liệu bằng cách so sánh phản hồi của agent khi dùng clean data và garbage data.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chạy ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```

Script `agent_simulation.py` sẽ chạy cùng một câu hỏi với hai file dữ liệu: `processed_data.csv` cho clean data và `garbage_data.csv` cho garbage data. Kết quả được ghi lại trong `experiment_report.md`.

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Input dữ liệu gốc
├── processed_data.csv       # Output của pipeline
├── garbage_data.csv         # Dữ liệu lỗi dùng cho stress test
├── agent_simulation.py      # Agent simulation script
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Ket qua

Pipeline đã xử lý `raw_data.json` và tạo `processed_data.csv` thành công. Kết quả validation: 3 valid records và 2 errors. Các record bị loại là record có `price <= 0` hoặc thiếu `category`.

Trong clean data, agent trả lời: `Laptop at $1200`. Trong garbage data, agent trả lời sai hơn vì chọn `Nuclear Reactor at $999999`, một outlier không hợp lý. Điều này cho thấy chất lượng dữ liệu ảnh hưởng trực tiếp đến câu trả lời của agent.
