# Reflection — Lab 19

**Tên:** _Luong Quoc Doan_
**Cohort:** _A20_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries, hybrid thắng trung bình: BM25 77.8%, semantic 73.2%, hybrid 78.6%. Với `exact`, BM25 rất mạnh vì query chứa đúng technical terms trong corpus; hybrid gần như ngang BM25. Với `mixed`, hybrid thắng rõ nhất vì query vừa có keyword exact vừa có ý paraphrase, nên RRF kết hợp được tín hiệu lexical và semantic. Với `paraphrase`, kết quả lite path chưa đẹp: semantic không thắng vì `BAAI/bge-small-en-v1.5` là model nhẹ, thiên English, nên hiểu tiếng Việt paraphrase còn yếu.

Tôi sẽ không dùng hybrid khi query domain chủ yếu là exact keyword, cần giải thích ranking đơn giản, hoặc latency/cost rất chặt và BM25 đã đủ tốt. Pure vector phù hợp hơn khi user query tự nhiên, nhiều paraphrase, và embedding model multilingual đủ mạnh như `bge-m3`.

---

## Điều ngạc nhiên nhất khi làm lab này

Điều bất ngờ nhất là hybrid không cần thắng mọi slice để vẫn thắng trung bình. Nó hữu ích nhất ở nhóm query mixed, giống hành vi search thật hơn là query exact hoàn toàn.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _N/A_
