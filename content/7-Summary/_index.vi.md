---
title: "Tóm tắt"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

Trong phòng thí nghiệm này, bạn đã xây dựng thành công một pipeline dữ liệu không cần máy chủ từ đầu đến cuối bao gồm nhập dữ liệu, chuyển đổi dữ liệu và trực quan hóa dữ liệu. Bạn đã tận dụng các dịch vụ không cần máy chủ của AWS để tạo kiến trúc hồ dữ liệu mạnh mẽ và có thể mở rộng.

Tóm tắt phòng thí nghiệm:

1. Nhập dữ liệu: Bạn đã nhập dữ liệu từ nhiều nguồn khác nhau vào Amazon S3, nơi lưu trữ hồ dữ liệu trung tâm. Bước này bao gồm việc thu thập và lưu trữ dữ liệu thô ở định dạng gốc của nó để xử lý sau này.

2. Chuyển đổi dữ liệu: Sử dụng AWS Glue, bạn đã định nghĩa và thực thi các công việc ETL (Trích xuất, Chuyển đổi, Tải) để xử lý dữ liệu thô được lưu trữ trong S3. Các công việc này đã chuyển đổi dữ liệu thành định dạng có cấu trúc phù hợp cho phân tích và báo cáo.

3. Danh mục dữ liệu: AWS Glue Data Catalog đóng vai trò quan trọng trong việc tổ chức và quản lý siêu dữ liệu cho hồ dữ liệu của bạn. Nó cung cấp một kho trung tâm để lưu trữ các định nghĩa lược đồ, nguồn gốc dữ liệu và các siêu dữ liệu khác liên quan đến bộ dữ liệu của bạn.

4. Phân tích dữ liệu: Với Amazon Athena, bạn có thể truy vấn và phân tích dữ liệu đã chuyển đổi được lưu trữ trong S3 bằng cách sử dụng cú pháp SQL chuẩn. Kiến trúc không cần máy chủ của Athena cho phép bạn chạy các truy vấn ad-hoc mà không cần cung cấp hoặc quản lý bất kỳ hạ tầng nào.

5. Trực quan hóa dữ liệu: Cuối cùng, bạn đã kết nối Amazon QuickSight với các nguồn dữ liệu của mình, cho phép bạn tạo các hình ảnh tương tác và bảng điều khiển. QuickSight cung cấp giao diện người dùng thân thiện để khám phá và trình bày các thông tin chi tiết về dữ liệu của bạn.

Trong suốt phòng thí nghiệm này, bạn đã trải nghiệm sức mạnh và sự linh hoạt của các dịch vụ không cần máy chủ của AWS trong việc xây dựng kiến trúc hồ dữ liệu hiện đại. Bằng cách tận dụng các công nghệ không cần máy chủ, bạn đã loại bỏ nhu cầu cung cấp và quản lý máy chủ, cho phép bạn tập trung vào các nhiệm vụ chính về kỹ thuật dữ liệu của mình.

Bạn có thể tiếp tục nâng cao và mở rộng hồ dữ liệu không cần máy chủ của mình bằng cách tích hợp thêm các nguồn dữ liệu bổ sung, triển khai các kỹ thuật xử lý dữ liệu nâng cao và khám phá các dịch vụ AWS khác như Amazon Kinesis, AWS Lambda và Amazon SageMaker, cùng những dịch vụ khác.
