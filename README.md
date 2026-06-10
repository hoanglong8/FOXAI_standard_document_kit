# FOXAI_standard_document_kit

# TÀI LIỆU KỸ THUẬT CHUẨN (STANDARD BASELINE) – FOXAI

## 1. Mục tiêu và Phạm vi áp dụng
Bộ thư viện này thiết lập các tiêu chuẩn kỹ thuật bắt buộc áp dụng cho mọi dự án AI tại FOXAI theo tư duy **Tuân thủ ngay từ khâu thiết kế (Compliance-by-Design)**. Mục tiêu là đảm bảo mọi sản phẩm phần mềm đều tích hợp sẵn các module an toàn dữ liệu và minh bạch AI, giúp rút ngắn thời gian kiểm thử và sẵn sàng cho công tác thanh tra của cơ quan Nhà nước.

---

## 2. Module 1: Mã hóa Dữ liệu (Encryption Module)
Áp dụng cho mọi hệ thống có xử lý dữ liệu cá nhân của người dùng Việt Nam.

*   **Mã hóa lưu trữ (At-rest):** Toàn bộ dữ liệu cá nhân quan trọng, dữ liệu nhạy cảm (như thông tin định danh, tài chính) phải được mã hóa khi lưu trữ trong cơ sở dữ liệu hoặc Cloud.
*   **Mã hóa truyền tải (In-transit):** Sử dụng các giao thức bảo mật để đảm bảo dữ liệu không bị đánh cắp hoặc sửa đổi trong quá trình truyền đưa trên không gian mạng.
*   **Quản lý khóa:** Xây dựng quy trình quản lý vòng đời khóa mã hóa, tách biệt quyền quản trị hệ thống và quản trị khóa.
*   **Ẩn danh hóa:** Đối với các dự án Big Data hoặc huấn luyện mô hình, dữ liệu cá nhân phải được xử lý ẩn danh hoặc khử định dạng trước khi sử dụng để tránh tái nhận dạng.

---

## 3. Module 2: Nhật ký hệ thống tập trung (Logging Module 12 Months)
Hệ thống ghi nhật ký (Logging) là yêu cầu pháp lý cốt lõi để phục vụ điều tra vi phạm và xác minh sự cố.

*   **Thời gian lưu trữ:** Tối thiểu **12 tháng**.
*   **Các loại nhật ký bắt buộc thu thập:**
    *   **Nhật ký truy cập:** Ghi lại thời gian, địa chỉ IP và danh tính người dùng/quản trị viên thực hiện các tác vụ trên hệ thống.
    *   **Nhật ký hoạt động AI:** Ghi lại dữ liệu đầu vào, kết quả đầu ra, phiên bản mô hình được sử dụng và các tham số cấu hình liên quan.
    *   **Nhật ký cảnh báo:** Các sự kiện liên quan đến lỗi hệ thống, cảnh báo bảo mật hoặc các trường hợp kết quả AI có độ tin cậy thấp.
*   **Tính toàn vẹn:** Nhật ký phải được lưu giữ tập trung và áp dụng biện pháp chống sửa xóa trái phép.

---

## 4. Module 3: Gắn nhãn và Đánh dấu AI (Labeling & Watermarking Module)
Bắt buộc đối với các sản phẩm AI tạo sinh (Generative AI) hoặc nội dung có khả năng gây nhầm lẫn cho người dùng.

*   **Đánh dấu kỹ thuật (Watermarking):**
    *   Sử dụng siêu dữ liệu (metadata), chữ ký số hoặc dấu hiệu nhận biết tích hợp vào cấu trúc tệp tin ở định dạng máy đọc được (machine-readable) cho âm thanh, hình ảnh và video.
    *   Dấu hiệu đánh dấu phải xác nhận rõ nội dung được tạo ra hoặc chỉnh sửa bởi AI.
*   **Gắn nhãn hiển thị (Labeling):**
    *   Thông báo rõ ràng cho người dùng trước hoặc tại thời điểm tiếp cận nội dung: "Nội dung được tạo ra bởi AI".
    *   Hình thức nhãn: Hiển thị trực tiếp trên nội dung, tiêu đề, chú thích hoặc thông báo bằng âm thanh.
*   **Trường hợp miễn trừ:** Các chỉnh sửa kỹ thuật thông thường (sửa lỗi chính tả, dịch thuật, tóm tắt) không làm thay đổi bản chất nội dung thì không bắt buộc gắn nhãn.

---

## 5. Module 4: Xác thực và Quản lý Truy cập (MFA & IAM)
*   **Xác thực đa nhân tố (MFA):** Bắt buộc áp dụng cho mọi tài khoản quản trị viên và các truy cập từ xa vào hệ thống chứa dữ liệu cá nhân.
*   **Phân quyền (RBAC):** Triển khai cơ chế kiểm soát truy cập phân cấp nghiêm ngặt, đảm bảo nguyên tắc đặc quyền tối thiểu.

---

## 6. Module 5: Hồ sơ tuân thủ AI (Compliance Kit)
Mỗi dự án AI cần đóng gói sẵn bộ tài liệu kỹ thuật để phục vụ Đánh giá tác động (DPIA) và phân loại rủi ro AI.

*   **Thẻ hệ thống/Thẻ mô hình (System/Model Card):** Mô tả kiến trúc, thuật toán, dữ liệu huấn luyện, giới hạn của hệ thống và kết quả kiểm thử an toàn.
*   **Sơ đồ luồng dữ liệu (Data Flow Diagram - DFD):** Thể hiện rõ luồng dữ liệu cá nhân đi từ đâu, qua các ứng dụng nào và lưu trữ tại đâu.
*   **Giải trình tính minh bạch (Explainable AI - XAI):** Cung cấp thông tin về logic vận hành và các yếu tố ảnh hưởng chính đến kết quả đầu ra, đặc biệt với các hệ thống AI rủi ro cao.

---
Ngoài 05 module kỹ thuật đã xây dựng, để kinh doanh và sản xuất phần mềm AI tại Việt Nam một cách hợp pháp, FOXAI cần tuân thủ các yêu cầu khắt khe về nhân sự, giấy phép, và bộ hồ sơ pháp lý theo các luật mới nhất (Luật AI 2025, Luật Bảo vệ dữ liệu cá nhân, Luật An ninh mạng).

### 1. Yêu cầu về Bằng cấp và Chứng chỉ Nhân sự
Pháp luật quy định các tiêu chuẩn cụ thể cho đội ngũ vận hành các hệ thống công nghệ cao:
*   **Nhân sự bảo vệ dữ liệu cá nhân (DPO):** FOXAI bắt buộc phải chỉ định nhân sự hoặc bộ phận phụ trách bảo vệ dữ liệu cá nhân. Nhân sự này phải có **trình độ cao đẳng trở lên**, có ít nhất **02 năm kinh nghiệm** trong các lĩnh vực pháp chế, CNTT, an ninh mạng hoặc quản trị rủi ro, và phải được **đào tạo, bồi dưỡng kiến thức pháp luật về bảo vệ dữ liệu**.
*   **Nhân sự quản trị hệ thống an ninh mạng:** Người trực tiếp quản trị, vận hành hệ thống thông tin từ **Cấp độ 3 trở lên** phải được tập huấn và cấp **chứng nhận kỹ năng chuyên sâu về an ninh mạng**.
*   **Lãnh đạo doanh nghiệp (nếu tham gia Sandbox):** Trong trường hợp FOXAI tham gia cơ chế thử nghiệm có kiểm soát (Sandbox), người đại diện pháp luật hoặc Giám đốc phải có **bằng đại học trở lên** (chuyên ngành Kinh tế, Luật hoặc CNTT) và ít nhất **02 năm kinh nghiệm quản lý** trong lĩnh vực tương ứng.

### 2. Giấy phép và Chứng nhận Tổ chức
*   **Giấy phép kinh doanh sản phẩm, dịch vụ an ninh mạng:** Nếu phần mềm của FOXAI có tính năng bảo vệ an ninh mạng, an ninh dữ liệu, công ty bắt buộc phải có giấy phép này.
*   **Giấy chứng nhận đánh giá sự phù hợp AI:** Đối với các hệ thống AI thuộc **Danh mục rủi ro cao**, FOXAI phải thực hiện đánh giá sự phù hợp và được tổ chức có thẩm quyền cấp chứng nhận (hoặc tự đánh giá theo hồ sơ kỹ thuật) trước khi đưa sản phẩm ra thị trường.
*   **Xác lập mã định danh hệ thống AI:** Sau khi thông báo kết quả phân loại rủi ro trên Cổng thông tin điện tử của Bộ Khoa học và Công nghệ, hệ thống sẽ cấp **mã định danh điện tử** cho sản phẩm AI của công ty.
*   **Phê duyệt cấp độ an toàn hệ thống thông tin:** FOXAI cần thực hiện hồ sơ đề xuất và được phê duyệt cấp độ an toàn thông tin (từ cấp độ 1 đến 5) cho hệ thống vận hành của mình.

### 3. Hồ sơ, Tài liệu và Biểu mẫu Bắt buộc
Mỗi dự án AI cần được đóng gói kèm theo bộ hồ sơ pháp lý để sẵn sàng phục vụ thanh tra:
*   **Hồ sơ Phân loại Rủi ro AI:** Bao gồm tài liệu mô tả mục đích, phạm vi, dữ liệu đầu vào và các biện pháp quản lý rủi ro.
*   **Thẻ hệ thống (System Card) và Thẻ mô hình (Model Card):** Tài liệu kỹ thuật chi tiết mô tả kiến trúc, thuật toán, dữ liệu huấn luyện, giới hạn và kết quả đánh giá hiệu năng của AI.
*   **Hồ sơ Đánh giá tác động xử lý dữ liệu cá nhân (DPIA):** Phải lập theo **Mẫu số 10** của Nghị định 356/2025/NĐ-CP và nộp cho Cục An ninh mạng (A05) trong vòng **60 ngày** kể từ khi bắt đầu xử lý dữ liệu.
*   **Hồ sơ chuyển dữ liệu ra nước ngoài (CTIA):** Nếu hệ thống AI sử dụng hạ tầng Cloud quốc tế hoặc gửi dữ liệu ra ngoài lãnh thổ Việt Nam, FOXAI phải lập hồ sơ theo **Mẫu số 01a/01b**.
*   **Báo cáo sự cố nghiêm trọng:** Phải chuẩn bị sẵn các biểu mẫu báo cáo sơ bộ (**Mẫu AI01a/b**) để nộp trong vòng **72 giờ** khi có sự cố khẩn cấp xảy ra.

### 4. Các yêu cầu Tuân thủ khác
*   **Tuân thủ Khung đạo đức AI quốc gia:** FOXAI cần lồng ghép các nguyên tắc đạo đức (không phân biệt đối xử, lấy con người làm trung tâm) vào toàn bộ vòng đời phát triển sản phẩm.
*   **Đăng ký Hệ thống mạng đấu thầu quốc gia:** Để tham gia các gói thầu AI của Chính phủ, FOXAI phải có tên trên hệ thống này trước khi phê duyệt kết quả lựa chọn nhà thầu.
*   **Tuân thủ Khung kiến trúc tổng thể quốc gia số:** Đối với các dự án phần mềm nội bộ sử dụng ngân sách nhà nước, sản phẩm phải phù hợp với chuẩn kiến trúc số quốc gia hiện hành.

**💡 Lời khuyên:** FOXAI nên chuẩn hóa các tài liệu này thành các **biểu mẫu mẫu (Templates)** để đội ngũ kinh doanh và kỹ thuật có thể nhanh chóng hoàn thiện hồ sơ cho từng dự án, tạo lợi thế cạnh tranh về tính chuyên nghiệp và an toàn pháp lý.
