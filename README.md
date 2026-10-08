# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Nguyễn Quang Huy
- MSSV / mã học viên: 2A202602421
- Lớp: H201
- Ngành đã chọn: HR / tuyển dụng — AI sàng lọc CV, đánh giá hoặc hỗ trợ tuyển ứng viên

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | **Ứng viên mất cơ hội việc làm** vì bị loại tự động theo đặc điểm không liên quan đến năng lực (giới tính, tuổi, khuyết tật, chủng tộc). **Doanh nghiệp** chịu kiện tụng, phạt và mất uy tín. **Thị trường lao động** có thể bị khóa lại theo định kiến cũ khi mô hình học từ dữ liệu tuyển dụng trong quá khứ. Ứng viên thường **không biết mình bị AI loại** nên khó khiếu nại. |
| Mức độ high-stakes | **Cao.** Quyết định tuyển dụng ảnh hưởng trực tiếp đến thu nhập và sinh kế của một người. Một công cụ sàng lọc dùng chung cho nhiều doanh nghiệp có thể lặp lại cùng một lỗi trên rất nhiều hồ sơ. EU AI Act xếp AI dùng để tuyển dụng và sàng lọc ứng viên vào nhóm rủi ro cao (Phụ lục III). |
| Dữ liệu nhạy cảm có thể được sử dụng | Họ tên, ngày sinh (suy ra tuổi), giới tính, ảnh, video phỏng vấn (khuôn mặt, giọng nói), địa chỉ, tình trạng sức khỏe hoặc khuyết tật, dân tộc, tôn giáo, lịch sử làm việc. Ngay cả khi không đưa trực tiếp, mô hình vẫn suy ra được đặc điểm nhạy cảm qua **biến đại diện** — tên trường, câu lạc bộ, năm tốt nghiệp. Bài này không dùng dữ liệu cá nhân thật. |
| Nhu cầu human review | **Cao.** (1) **Trước khi đưa vào dùng:** bộ phận nhân sự và pháp chế kiểm tra tỉ lệ đỗ theo nhóm (tuổi, giới) trên dữ liệu thử. (2) **Trước khi loại một ứng viên:** người tuyển dụng xem lại các hồ sơ bị AI loại, không để AI loại tự động mà không ai xem. (3) **Định kỳ:** kiểm tra lại vì dữ liệu và vị trí tuyển thay đổi. Lý do: sai lệch thường **không nhìn thấy được trên từng hồ sơ**, chỉ lộ ra khi thống kê theo nhóm. |

### 2. Case study 1 — Amazon: công cụ tuyển dụng thử nghiệm hạ điểm hồ sơ của nữ

#### Brief Case

- Tổ chức / sản phẩm AI: Amazon — công cụ chấm điểm hồ sơ ứng viên dùng học máy, phát triển nội bộ, không công bố tên.
- Thời gian, địa điểm / bối cảnh: Phát triển từ năm 2014 tại Mỹ, dùng cho tuyển kỹ sư phần mềm và các vị trí kỹ thuật. Reuters công bố ngày 10/10/2018.
- AI được dùng để làm gì: Đọc hồ sơ và chấm ứng viên từ 1 đến 5 sao để chọn ra người nên tuyển.
- Vấn đề hoặc sự kiện đáng chú ý: Mô hình học từ hồ sơ nộp vào Amazon trong 10 năm, phần lớn là của nam giới. Theo Reuters, hệ thống **hạ điểm hồ sơ có chữ "women's"** (ví dụ "women's chess club captain") và hạ điểm người tốt nghiệp hai trường đại học chỉ dành cho nữ. Amazon sửa để mô hình trung lập với các từ này nhưng không đảm bảo được mô hình không tìm cách phân biệt khác. Nhóm phát triển bị giải tán vào đầu năm 2017.
- Số liệu có nguồn: Dữ liệu huấn luyện là **hồ sơ trong 10 năm**. Thang chấm **1–5 sao**. Theo Reuters, nhóm đã xây khoảng **500 mô hình** theo từng vị trí và địa điểm, mỗi mô hình nhận biết khoảng **50.000 từ khóa** xuất hiện trong hồ sơ cũ.
- Nguồn: Jeffrey Dastin, "Amazon scraps secret AI recruiting tool that showed bias against women", Reuters, 10/10/2018 — bản đăng lại trên Euronews: https://www.euronews.com/business/2018/10/10/amazon-scraps-secret-ai-recruiting-tool-that-showed-bias-against-women · Hồ sơ sự cố: AI Incident Database, Incident 37 — https://incidentdatabase.ai/cite/37/
- Phân biệt bằng chứng và nhận định: **Nguồn xác nhận:** công cụ có thiên lệch theo giới, đã bị dừng, và theo Amazon thì người tuyển dụng **chưa bao giờ chỉ dựa vào** điểm của công cụ. Thông tin đến từ nguồn giấu tên của Reuters. **Chưa rõ:** có ứng viên cụ thể nào bị từ chối vì công cụ hay không, và bao nhiêu người. **Nhận định của tôi:** tác hại lên ứng viên là **nguy cơ**, chưa được chứng minh đã xảy ra.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Bước sàng lọc đầu tiên: AI chấm sao cho hàng nghìn hồ sơ, người tuyển dụng nhìn điểm để quyết định gọi ai phỏng vấn. |
| Stakeholder bị ảnh hưởng | Ứng viên nữ vào vị trí kỹ thuật; người tốt nghiệp trường dành cho nữ; người tuyển dụng của Amazon (dùng điểm sai); Amazon (rủi ro pháp lý và uy tín). |
| Failure mode | **Bias / fairness** — mô hình học lại định kiến trong dữ liệu lịch sử. Có thêm nguy cơ **over-reliance** nếu người tuyển dụng tin điểm sao mà không xem hồ sơ. |
| Layer bắt đầu lỗi | **Model**, cụ thể là dữ liệu huấn luyện: lỗi có sẵn trong hồ sơ 10 năm lệch về nam. Nguồn xác nhận nguyên nhân là dữ liệu lịch sử, không phải giao diện hay lớp bảo vệ. |
| Harm xảy ra là gì? | Ứng viên nữ **có nguy cơ** bị xếp hạng thấp hơn và mất cơ hội phỏng vấn khi hồ sơ có dấu hiệu là nữ. **Đã xảy ra:** mô hình hạ điểm (nguồn xác nhận). **Chưa xác nhận:** có người thật bị từ chối vì việc này. |
| Harm lens | Opportunity loss (mất cơ hội việc làm); dignity loss (bị đánh giá thấp vì giới tính). |
| Severity | **High** — ảnh hưởng tới cơ hội việc làm và thu nhập; là phân biệt đối xử theo giới. Không lên Critical vì không có tổn hại thể chất và công cụ đã dừng trước khi được dùng làm căn cứ duy nhất. |
| Scale | **Có thể lớn nhưng chưa đủ dữ liệu.** Amazon tuyển nhiều kỹ sư mỗi năm, nhưng nguồn không công bố số hồ sơ đã được công cụ chấm. |
| Probability | **Cao** với ứng viên nữ có từ khóa liên quan — nguồn xác nhận mô hình hạ điểm có hệ thống. Khả năng việc này dẫn tới bị loại thật: **chưa đủ dữ liệu để đánh giá**. |
| Frequency | **Cao trong thời gian thử nghiệm** — lỗi nằm trong mô hình nên lặp lại với mọi hồ sơ có đặc điểm tương tự. Đã chấm dứt khi dừng dự án. |
| Vì sao? | Mô hình học "người được tuyển trước đây trông thế nào", mà người được tuyển trước đây phần lớn là nam, nên nó học luôn định kiến đó. Bài học: dữ liệu lịch sử không trung lập; xóa một từ khóa không đủ vì mô hình tìm được biến đại diện khác. Giới hạn bằng chứng: chỉ có nguồn báo chí dựa trên người giấu tên, không có báo cáo kỹ thuật của Amazon. |

### 3. Case study 2 — iTutorGroup: phần mềm tự động loại ứng viên lớn tuổi

#### Brief Case

- Tổ chức / sản phẩm AI: iTutorGroup — ba công ty liên kết cung cấp dịch vụ dạy tiếng Anh trực tuyến cho học sinh ở Trung Quốc; phần mềm nhận hồ sơ gia sư.
- Thời gian, địa điểm / bối cảnh: Tuyển gia sư làm việc từ xa tại Mỹ, năm 2020. Ủy ban Cơ hội Việc làm Bình đẳng Hoa Kỳ (EEOC) khởi kiện năm 2022; hai bên đạt thỏa thuận năm 2023.
- AI được dùng để làm gì: Phần mềm tự động sàng lọc hồ sơ ứng tuyển gia sư.
- Vấn đề hoặc sự kiện đáng chú ý: Theo EEOC, phần mềm được **lập trình để tự động loại** nữ từ 55 tuổi trở lên và nam từ 60 tuổi trở lên. Đây là vụ dàn xếp đầu tiên được EEOC và báo chí gắn với việc dùng AI trong tuyển dụng.
- Số liệu có nguồn: **Hơn 200** ứng viên đủ điều kiện ở Mỹ bị từ chối vì tuổi. iTutorGroup trả **365.000 USD** cho những ứng viên bị loại, chịu giám sát theo thỏa thuận và phải mời ứng viên bị loại trong tháng 3–4/2020 nộp lại.
- Nguồn: EEOC, "iTutorGroup to Pay $365,000 to Settle EEOC Discriminatory Hiring Suit", thông cáo báo chí, 2023 — https://www.eeoc.gov/newsroom/itutorgroup-pay-365000-settle-eeoc-discriminatory-hiring-suit · Bloomberg Law, "EEOC Settles First-of-Its-Kind AI Bias in Hiring Lawsuit" — https://news.bloomberglaw.com/daily-labor-report/eeoc-settles-first-of-its-kind-ai-bias-lawsuit-for-365-000
- Phân biệt bằng chứng và nhận định: **Nguồn xác nhận:** quy tắc loại theo tuổi được cài sẵn, hơn 200 người bị loại, số tiền dàn xếp. iTutorGroup **không thừa nhận sai phạm**. **Lưu ý:** hồ sơ vụ kiện mô tả một **quy tắc cứng theo tuổi**, không phải mô hình học máy; nhãn "AI" chủ yếu đến từ cách EEOC và báo chí trình bày. **Nhận định của tôi:** case vẫn thuộc ngành vì cho thấy phần mềm sàng lọc tự động có thể thực thi phân biệt đối xử hàng loạt khi không có người xem lại.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Lúc ứng viên nộp hồ sơ: phần mềm đọc ngày sinh và loại ngay, không qua người xem. |
| Stakeholder bị ảnh hưởng | Ứng viên nữ từ 55 tuổi và nam từ 60 tuổi; iTutorGroup (bị kiện, phải trả tiền và chịu giám sát); học sinh (mất cơ hội học với gia sư có kinh nghiệm — nhận định của tôi). |
| Failure mode | **Bias / fairness** do quy tắc cố ý loại theo tuổi; **escalation failure** — không có bước chuyển cho người xem lại trước khi loại. |
| Layer bắt đầu lỗi | **Grounding / cấu hình nghiệp vụ**: tiêu chí loại theo tuổi do người cài vào hệ thống. Thiếu lớp **Safety** để chặn tiêu chí trái luật. Không phải lỗi của mô hình học máy. |
| Harm xảy ra là gì? | Hơn 200 ứng viên đủ điều kiện **đã bị** từ chối và mất cơ hội việc làm vì tuổi — **đã xảy ra**, được EEOC xác nhận và dẫn tới bồi thường. |
| Harm lens | Opportunity loss (mất việc làm, thu nhập); dignity loss (bị loại chỉ vì tuổi). |
| Severity | **High** — mất cơ hội việc làm, vi phạm luật chống phân biệt tuổi tác của Mỹ (ADEA). |
| Scale | **Trung bình**: hơn 200 người theo EEOC — có số liệu, nhỏ hơn nhiều so với các nền tảng dùng chung. |
| Probability | **Rất cao (gần như chắc chắn)** với nhóm tuổi bị nhắm tới — quy tắc cứng nên mọi hồ sơ thỏa điều kiện đều bị loại. |
| Frequency | **Cao**: lặp lại với **mỗi** hồ sơ thuộc nhóm tuổi đó cho tới khi bị phát hiện. |
| Vì sao? | Khác với Amazon, đây không phải định kiến "lọt vào" mô hình mà là **tiêu chí trái luật được cài thẳng**, nên xác suất và tần suất gần như tuyệt đối. Bài học: tự động hóa khuếch đại cả quyết định sai của con người; cần rà soát tiêu chí trước khi chạy và có người xem lại trước khi loại. Giới hạn: số người bị ảnh hưởng thực tế có thể khác con số "hơn 200" trong thông cáo. |

### 4. Case study 3 — Mobley v. Workday: vụ kiện tập thể về AI sàng lọc của nhà cung cấp phần mềm

#### Brief Case

- Tổ chức / sản phẩm AI: Workday, Inc. — phần mềm quản lý nhân sự và tuyển dụng dùng chung cho nhiều doanh nghiệp, có tính năng sàng lọc và xếp hạng ứng viên (gồm tính năng AI HiredScore).
- Thời gian, địa điểm / bối cảnh: Vụ kiện Mobley v. Workday, Tòa án Liên bang Quận Bắc California, số 3:23-cv-00770, khởi kiện năm 2023. Ngày 16/5/2025 tòa chấp nhận sơ bộ cho kiện tập thể về phân biệt tuổi tác.
- AI được dùng để làm gì: Sàng lọc, chấm điểm và xếp hạng hồ sơ thay cho các doanh nghiệp đang dùng Workday.
- Vấn đề hoặc sự kiện đáng chú ý: Nguyên đơn Derek Mobley cho rằng công cụ của Workday đã khiến ông và những ứng viên từ 40 tuổi trở lên bị từ chối có hệ thống. Tòa cho phép mở rộng thành kiện tập thể với ứng viên từ 40 tuổi trở lên nộp hồ sơ qua Workday từ 24/9/2020.
- Số liệu có nguồn: Theo hồ sơ chính Workday nộp cho tòa, khoảng **1,1 tỷ** hồ sơ ứng tuyển đã bị từ chối qua hệ thống trong giai đoạn liên quan.
- Nguồn: Davis Wright Tremaine, "AI Screening Tools Under Scrutiny: Federal Court Preliminarily Certifies ADEA Collective Action", 05/2025 — https://www.dwt.com/blogs/employment-labor-and-benefits/2025/05/ai-hiring-age-discrimination-federal-court-workday · Civil Rights Litigation Clearinghouse, Mobley v. Workday — https://clearinghouse.net/case/44074/
- Phân biệt bằng chứng và nhận định: **Nguồn xác nhận:** vụ kiện tồn tại, tòa đã chấp nhận sơ bộ cho kiện tập thể, Workday nêu con số khoảng 1,1 tỷ hồ sơ bị từ chối. **Chưa được chứng minh:** việc phân biệt đối xử. Chấp nhận sơ bộ **không phải phán quyết** về đúng sai; con số 1,1 tỷ là tổng số hồ sơ bị từ chối, **không phải** số hồ sơ bị từ chối vì tuổi. **Nhận định của tôi:** tác hại là **nguy cơ đang được tòa xem xét**.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi hồ sơ được công cụ của nhà cung cấp chấm điểm, xếp hạng và có thể bị loại trước khi nhà tuyển dụng nhìn thấy. |
| Stakeholder bị ảnh hưởng | Ứng viên từ 40 tuổi trở lên; các doanh nghiệp dùng Workday (rủi ro pháp lý); Workday (bị kiện với tư cách nhà cung cấp). |
| Failure mode | **Bias / fairness** (cáo buộc); **over-reliance** — doanh nghiệp dựa vào kết quả xếp hạng của nhà cung cấp mà không tự kiểm tra. |
| Layer bắt đầu lỗi | **Chưa đủ bằng chứng.** Giả thuyết của tôi: ở lớp **Model** (dữ liệu huấn luyện hoặc biến đại diện cho tuổi như năm tốt nghiệp). Workday không công bố kiến trúc nên không khẳng định được. |
| Harm xảy ra là gì? | Ứng viên lớn tuổi **có nguy cơ** bị loại có hệ thống ở nhiều doanh nghiệp cùng lúc, kể cả khi họ nộp hồ sơ ở nhiều nơi khác nhau. **Mới là cáo buộc**, chưa có phán quyết. |
| Harm lens | Opportunity loss (mất cơ hội việc làm); dignity loss. |
| Severity | **High** — nếu đúng thì là phân biệt tuổi tác, ảnh hưởng tới sinh kế. |
| Scale | **Rất lớn** — một phần mềm dùng chung cho nhiều doanh nghiệp; Workday nêu khoảng 1,1 tỷ hồ sơ bị từ chối qua hệ thống. Số người bị ảnh hưởng **vì tuổi** chưa có số liệu. |
| Probability | **Chưa đủ dữ liệu để đánh giá** — tòa chưa kết luận có phân biệt đối xử. |
| Frequency | **Chưa đủ dữ liệu để đánh giá** — nếu cáo buộc đúng thì lặp lại liên tục vì công cụ chạy trên mọi hồ sơ. |
| Vì sao? | Điểm khác của case này là **quy mô**: một lỗi ở nhà cung cấp lan sang mọi doanh nghiệp dùng chung, nên người bị từ chối ở công ty A rất có thể lại bị từ chối ở công ty B vì cùng một công cụ. Vụ kiện cũng đặt câu hỏi ai chịu trách nhiệm — doanh nghiệp tuyển dụng hay nhà cung cấp phần mềm. Giới hạn bằng chứng: vụ việc chưa kết thúc; tôi dựa vào tóm tắt pháp lý và hồ sơ vụ kiện, không đọc toàn văn mọi lệnh của tòa. |

### 5. Nhận xét chung

| Case | Nguồn lỗi | Tác hại | Bằng chứng |
| --- | --- | --- | --- |
| Amazon | Dữ liệu lịch sử lệch về giới | Nguy cơ | Báo chí, nguồn giấu tên |
| iTutorGroup | Tiêu chí trái luật cài sẵn | **Đã xảy ra**, hơn 200 người | Cơ quan nhà nước, có dàn xếp |
| Workday | Chưa rõ (đang kiện) | Cáo buộc, quy mô rất lớn | Hồ sơ tòa án |

Ba case cho thấy ba con đường khác nhau dẫn tới cùng một tác hại là mất cơ hội việc làm. Biện pháp chung: **kiểm tra tỉ lệ đỗ theo nhóm trước và sau khi triển khai**, **không để AI tự loại ứng viên mà không có người xem lại**, và **báo cho ứng viên biết có dùng AI** để họ có cơ hội khiếu nại.
