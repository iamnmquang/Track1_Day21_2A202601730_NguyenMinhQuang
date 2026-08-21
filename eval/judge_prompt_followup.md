# Judge prompt — FOLLOW-UP QUALITY

Bạn là evaluator độc lập cho AI Tutor tiếng Việt. Chỉ chấm **một câu hỏi**: ba câu
`followup_questions` có giúp học viên đào sâu đúng nội dung bài học hay không? Không
chấm groundedness, citation, scope, JSON, hay độ đúng của answer.

## Input học viên
{{input}}

## Output cần chấm
{{answer}}

## Quy tắc quan sát được

- **PASS**: có đúng ba câu, mỗi câu bám chủ đề AI evaluations/câu hỏi ban đầu và mời
  học viên so sánh, áp dụng, hoặc đi sâu vào khái niệm; không hỏi xã giao.
- **FAIL**: câu hỏi lạc sang chủ đề ngoài corpus, lặp lại vô nghĩa, ép học viên trả lời,
  hoặc không tạo được bước học tiếp theo.
- **UNCERTAIN**: không đủ ngữ cảnh để biết câu hỏi có liên quan; không dùng chỉ vì cách
  diễn đạt không giống ví dụ.

## Near-miss examples

1. **PASS (`sc-02`)**: hỏi cách xây taxonomy cho một use case và vì sao chuẩn hóa trace
   codes quan trọng — đều mở rộng đúng chủ đề trace analysis.
2. **FAIL (mẫu)**: “Bạn thấy câu trả lời của tôi hay không?” — xã giao, không tạo bước
   học tiếp theo.
3. **FAIL (mẫu)**: sau câu hỏi về calibration lại hỏi nơi mua GPU/giá crypto — lệch
   corpus và lệch mục tiêu học.

## Output bắt buộc

Chỉ trả về một JSON object hợp lệ:
{
  "verdict": "pass" | "fail" | "uncertain",
  "score": 0.0,
  "rationale": "một lý do ngắn bằng tiếng Việt",
  "issues": ["follow-up cụ thể nếu có"]
}
