# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600924
**Name:** Trần Minh Quang
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dữ liệu đã được validate, category được chuẩn hóa và không có record lỗi nghiêm trọng. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Agent bị ảnh hưởng bởi outlier và dữ liệu không sạch nên chọn sản phẩm không hợp lý. |

---

## 2. Phan tich & nhan xet

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Agent trả lời sai khi dùng garbage data vì nó dựa trực tiếp vào nội dung trong file CSV mà không có bước validate dữ liệu trước khi suy luận. Trong garbage data có duplicate ID, kiểu dữ liệu sai như `ten dollars`, category không đồng nhất, giá bằng 0, giá trị rỗng và outlier rất lớn như `Nuclear Reactor` với giá `999999`. Logic của agent chọn sản phẩm electronics có giá cao nhất, nên outlier này lập tức trở thành kết quả được ưu tiên. Đây không phải lỗi của prompt mà là lỗi của nguồn dữ liệu: khi dữ liệu đầu vào bị sai, agent vẫn có thể trả lời tự tin nhưng kết quả không đáng tin cậy. Clean data giúp agent đưa ra câu trả lời hợp lý hơn vì các record lỗi đã bị loại bỏ và các trường quan trọng đã được chuẩn hóa.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý. Prompt tốt có thể hướng dẫn agent cách trả lời, nhưng nếu dữ liệu đầu vào có outlier, null value, duplicate hoặc sai kiểu dữ liệu thì agent vẫn có thể đưa ra kết quả sai. Data quality là nền tảng quan trọng để agent trả lời chính xác và ổn định.
