# AI Support Log

> Ghi lại bạn đã dùng AI (ChatGPT/Claude/Kimi...) ở những bước nào khi làm deliverables.
> Trung thực là một phần của bài nộp — không ai làm một mình, quan trọng là bạn giữ
> quyền kiểm soát chất lượng.

| # | Bước | AI dùng để làm gì | Bạn kiểm chứng kết quả thế nào |
|---|------|-------------------|-------------------------------|
| 1 | Phase 2–4 | Chạy/diễn giải agreement, đề xuất rule deterministic cho quote, brainstorm assertion code check và soạn nháp prompt judge. | Đối chiếu từng rule với `results-v1.jsonl`, corpus và output `code_checks.py`; nhóm phải đọc case bất đồng trước khi chấp nhận. |
| 2 | Phase 4 | Tóm tắt pattern judge lệch và đề xuất một thay đổi V2: refusal out-of-scope không cần citation. | Chạy V1/V2 thật, lưu verdicts; kiểm tra confusion matrix và đọc tay các mismatch, đặc biệt `sc-12`. |
| 3 | Phase 5–6 | Soạn nháp scorecard, routing map và report PM từ số liệu đã có. | Số liệu được tính lại từ JSONL/CSV; threshold, verdict Hold và backlog phải do nhóm xác nhận, không lấy AI làm người quyết định. |

## AI đã giúp tôi ở đâu?

AI giúp tôi biến log thô thành bảng dễ đọc: tổng hợp disagreement, chỉ ra rằng quote
fidelity là rule kiểm được bằng code, và tóm tắt 7 lỗi V1 của judge thành một pattern
out-of-scope rõ ràng. AI cũng giúp soạn cấu trúc rubric, prompt judge và report để tôi
có thời gian đọc các trace quan trọng thay vì chép số liệu thủ công.

## AI sai, hời hợt hoặc làm mất coverage ở đâu?

AI từng có xu hướng đánh giá quá rộng: coi một answer chung chung là grounded hoặc đề
xuất kết luận từ sample semantic chỉ có 2 fail. Judge V1 cũng chặn nhầm các refusal đúng
vì prompt chưa nêu ngoại lệ out-of-scope. AI không có bằng chứng về provenance trace
thật, tần suất user hay dataset review; các điểm đó được ghi là gap thay vì bịa dữ liệu.
Quan trọng nhất, AI không được thay nhóm chốt nhãn Phase 2, threshold hay verdict.

## Tôi đã tự sửa hoặc quyết định lại điều gì?

Tôi/nhóm giữ human baseline từ các file nhãn độc lập và phải tự phê duyệt nhãn vàng sau
khi đọc case lệch. Nhóm siết quote thành token liên tiếp, tách code gate khỏi judge, và
chỉ chấp nhận thay đổi V2 sau khi xem matrix thật. Tôi/nhóm chọn threshold 100% cho
blocker, chọn **Hold** khi quote chỉ đạt 15/25 và `sc-20` còn làm hộ capstone. Các ô
coverage, nguồn dữ liệu và verdict cuối cần được các thành viên xác nhận trước khi nộp.
