# UC-1.5 Question Backlog

> **File purpose:** Chứa danh sách câu hỏi mở từ UC review, cần BA answer trước khi tiến hành test design.
>
> **Source:** UC Readiness Review — UC-1.5_Distinction Purchase — v1.0 (2026-05-27)
>
> **Instructions:** Mỗi câu hỏi được đánh ID (Q1, Q2...) theo thứ tự ưu tiên. BA điền answer vào cột Answer, update Status thành "Resolved".

---

## Unified Gap & Question Report

| ID | Priority | Question | Answer | Why It Matters | Status |
|----|----------|----------|--------|----------------|--------|
| Q1 | High | **Model conflict — Stripe vs Activations**: Tài liệu cũ (UC-5.1/5.2/5.3) đề cập Stripe payment với CHF price per NFT. Tài liệu mới ("New Distinction Purchasing Design") bỏ Stripe, dùng "activations/packaging" model. | **Answer:** Tài liệu Cũ: mua từng distinction → thanh toán Stripe tại checkout. Tài liệu Mới: sử dụng activation package đã mua trước đó (không cần Stripe tại thời điểm mint). | Critical impact on payment flow test cases; hiểu rõ khi nào dùng Stripe vs activations | Resolved |
| Q2 | High | **Points calculation rule**: Tài liệu cũ: 10% buyer + 10% recipient + 10% pool = 30% total. Tài liệu mới: 10% buyer + 20 points cho partner/recipient. | **Answer:** Cả 2 đều đúng. Tài liệu Cũ = logic hiện tại. Tài liệu Mới = logic sắp được update trong tương lai. | Không thể verify points calculation correct nếu rule không rõ ràng | Resolved |
| Q3 | High | **Pricing table vs Distinction types**: Tài liệu mới có pricing table (Class 0 miễn phí với 10 activations → Class 7 CHF 190 với 1 activation) nhưng distinction types giờ là Collaboration/Investor/Bridge — không còn Philanthropist như tài liệu cũ. | **Answer:** Theo tài liệu Mới: không có giá cho từng distinction type. Giá là theo package dựa trên class (Class 0-7). | Không match được pricing với distinction type → test data không chính xác | Resolved |
| Q4 | Medium | **Activations tracking logic**: Tài liệu mới đề cập "activations remaining = activations purchased - activations used". Mỗi lần mint giảm bao nhiêu activations? | **Answer:** Mỗi lần mint giảm 1 activation. | Critical cho test balance calculation và remaining count trong pop-up message | Resolved |
| Q5 | Medium | **Email notification specs (EMC 12/13)**: Tài liệu đề cập EMC 12 (buyer badge) và EMC 13 (recipient badge) nhưng không có email template/content spec. | **Answer:** EMC 12: Email gửi cho buyer, gồm: tên + email người mua, tên + email người nhận, distinction type, số point đã nhận. EMC 13: Email gửi cho recipient, gồm: tên + email người mua, tên + email người nhận, distinction type, số point đã nhận. | Không thể verify email output nếu không có template/spec | Resolved |
| Q6 | Medium | **Badge issuance criteria**: Badge được cấp khi "1st purchasing/receiving". Cần xác nhận: (1) First-time per user? (2) First-time per distinction type? (3) Có reset theo năm không? | **Answer:** Không duy nhất cho 1 account. Kể cả khi account A mint NFT cho nhiều recipient khác nhau, account A vẫn chỉ nhận 1 badge ở lần đầu tiên. | Test precondition ambiguous, có thể dẫn đến false positive/negative trong test | Resolved |
| Q7 | Medium | **Year 2+ Discount trigger**: Tài liệu cũ đề cập 20% discount cho returning customers từ năm thứ 2+. Trigger condition là auto-detect hay user opt-in? | **Answer:** Có thể chọn không dùng discount. | Không thể design test case cho returning customer discount flow | Resolved |
| Q8 | Low | **Individual class points exception**: Individual mua Bridge tại CHF 19 — buyer (Individual) có được nhận points không? | **Answer:** Buyer (Individual) không được nhận points. | Unclear exemption rule ảnh hưởng đến test coverage cho Individual flow | Resolved |
| Q9 | Low | **Anti-return enforcement location**: Anti-return check (MSG 28) được enforce ở đâu — frontend only, backend only, hay cả hai? | **Answer:** Frontend (FE). | Need to know để design test cases cho bypass scenarios | Resolved |
| Q10 | Low | **New recipient wallet creation timing**: NFT có được mint NGAY khi purchase hoàn tất không, hay phải chờ recipient sign up? | **Answer:** Mint ngay (không cần chờ recipient sign up). | Timing ambiguity ảnh hưởng đến test case sequencing | Resolved |

---

## Change Log

| Version | Date | Author | Summary of Changes |
|---------|------|--------|--------------------|
| v1 | 2026-05-27 | QC Agent (qc-uc-read) | Initial question backlog from UC-1.5 first audit |
| v2 | 2026-05-27 | BA | All Q1-Q10 answered and resolved |

---

*Question Backlog — UC-1.5 v2.0 — Updated by BA — 2026-05-27*