# Calibration v1 — lịch sử unblock

Ngày 2026-08-21 đã thử chạy groundedness judge trên 15 case qua code gate bằng:

```bash
JUDGE_PROMPT_PATH=eval/judge_prompt_groundedness.md \
JUDGE_VERDICTS_PATH=verdicts-grounded-v1.jsonl \
python3 eval/judge.py <15 scenario_id qua code gate>
```

Lần thử đầu dừng trước khi gọi model vì chưa có API key. Sau khi cấu hình `.env`, model
`openrouter/openai/gpt-4o-mini` được nhận diện; tuy nhiên môi trường sandbox không phân
giải được DNS `openrouter.ai`. Yêu cầu chạy mạng ngoài sandbox cũng không được chấp nhận
vì payload sẽ bao gồm input, output tutor và citations của workspace gửi tới OpenRouter.

Thông báo lần thử đầu:

```
Chưa có API key cho judge model openai/gpt-4o-mini — xem .env.example.
```

Sau khi có xác nhận cho phép gửi payload calibration và tắt tracing để tránh retry log,
V1/V2 đã chạy thành công. Artifacts: `verdicts-grounded-v1.jsonl`,
`verdicts-grounded-v2.jsonl`, `judge-prompt-groundedness-v1.md`,
`judge-prompt-groundedness-v2.md`. Số liệu và phân tích lệch nằm ở mục 5 REPORT.
