# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603326
- Ngày / CVAT local: 12/11/2026
- Công cụ đã dùng: CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip |3 / 3 | 20 |
| medium_instance |medium_instance |3 / 3 | 32 |
| hard_panoptic | hard_panoptic |2 / 2 | 30 |
| cp1_holes | … | … / 1 | 3 |
| cp2_slice | … | … / 1 | 3 |
| cp5_occlusion | … | … / 1 | 3 |
| cp3_thin | … | … / 1 | 3 |
| cp4_curb | … | … / 1 | 3 |
| cp6_coverage | … | … / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Vị trí xe ô tô trên đường
- Class và quy tắc tôi dùng để chọn biên:Với car, vẽ polygon theo đường viền thân xe, chỉ lấy phần nhìn thấy và không lấn sang phương tiện bên cạnh.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng
- Nếu không dùng gợi ý: phân biệt đúng car, truck và bus, không chỉ dựa vào kích thước mà còn dựa vào hình dạng và chức năng phương tiện.
## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Medium instance / Vùng phương tiện giao thông có car
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: sai lớp
- Bằng chứng tôi nhìn thấy: Một số phương tiện bị gán nhầm class car thay vì truck hoặc bus do hình dạng và kích thước phương tiện khá giống nhau khi nhìn từ xa hoặc bị che khuất
- Quy tắc và hành động sửa:car là phương tiện chở người thông thường, có hình dáng ô tô con. Kiểm tra lại từng phương tiện, đối chiếu hình dạng và đặc điểm nhận diện rồi điều chỉnh class cho phù hợp, không gộp nhiều phương tiện thành một object.

- Sau sửa đã Save và export lại chưa? Saved

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1 | Hard Panoptic ảnh 1 – xe chở ô tô ở giữa đường | phân việt phương tiện vận chuyển | hỏi coach về ngưỡng kích thước tối thiểu của object. |
| 2 | Hard Panoptic ranh giới đường và vỉa hè bên trái | sự thay đổi bề mặt và ranh giới | hỏi coach về ngưỡng kích thước tối thiểu của object. |
| 3 | đèn giao thông ở xa giao lộ |Quan sát hình dạng, vị trí và khả năng nhận diện của đèn giao thông | hỏi coach về ngưỡng kích thước tối thiểu của object. |
