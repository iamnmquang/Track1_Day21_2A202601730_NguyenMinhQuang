# Human–human agreement v1

Nguồn: bốn vòng chấm độc lập `labels-hung.csv`, `labels-quang.csv`,
`labels-son.csv`, `labels-tan.csv`; cùng 25 scenario. Chạy:

```bash
python3 eval/agreement.py labels-hung.csv labels-quang.csv labels-son.csv labels-tan.csv
```

| Chỉ số | Kết quả |
|---|---:|
| Đồng thuận hoàn toàn (4 người) | 9/25 = **36%** |
| Hung – Quang | 17/25 = 68% |
| Hung – Son | 19/25 = 76% |
| Hung – Tan | 12/25 = 48% |
| Quang – Son | 14/25 = 56% |
| Quang – Tan | 12/25 = 48% |
| Son – Tan | 18/25 = 72% |

## Disagreement cases

`sc-01`, `sc-03`, `sc-04`, `sc-05`, `sc-08`, `sc-10`, `sc-11`, `sc-12`,
`sc-13`, `sc-14`, `sc-15`, `sc-18`, `sc-20`, `sc-22`, `sc-24`, `sc-25`.

## Kết luận thảo luận và thay đổi rubric

Bất đồng chiếm ưu thế là **citation/quote fidelity**: một nhóm đánh giá theo ý nghĩa
câu trả lời, trong khi nhóm khác coi quote ghép nhiều đoạn là fail. Đây là tiêu chí
deterministic, nên tách khỏi phán đoán cảm tính: `quote_verbatim` phải là chuỗi token
liên tiếp trong section đã cite; fail check này đồng nghĩa label tổng là fail. Các
trường hợp còn lại chốt fail khi có hallucination (`sc-10`), scope sai/hỗ trợ làm hộ
(`sc-20`), hoặc kết luận không được sources hỗ trợ (`sc-24`). Nhãn vàng cuối cùng ở
`labels.csv`.

Vì agreement độc lập chỉ 36% (<90%), rubric v1 chưa sẵn sàng để calibrate LLM judge
trước khi áp dụng quy tắc trên và chấm lại một vòng độc lập.
