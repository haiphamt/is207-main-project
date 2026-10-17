<p align="center">
  <a href="https://www.uit.edu.vn/" title="Trường Đại học Công nghệ Thông tin">
    <img src="https://i.imgur.com/WmMnSRt.png" alt="Trường Đại học Công nghệ Thông tin | University of Information Technology">
  </a>
</p>

<h1 align="center"><b>IS207.R11 - PHÁT TRIỂN ỨNG DỤNG WEB</b></h1>

## BẢNG MỤC LỤC

- [Giới thiệu môn học](#giới-thiệu-môn-học)
- [Giới thiệu đồ án môn học](#giới-thiệu-đồ-án-môn-học)
- [Thành viên nhóm](#thành-viên-nhóm)

## GIỚI THIỆU MÔN HỌC

- **Tên môn học:** Phát triển ứng dụng web
- **Mã môn học:** IS207.R11
- **Giảng viên hướng dẫn:** ThS. **Tạ Việt Phương**
- **Email:** *phuongtv@uit.edu.vn*

---

## GIỚI THIỆU ĐỒ ÁN MÔN HỌC

- **Tên đề tài:** TravelGo - Nền tảng khám phá địa điểm và lập lịch trình du lịch thông minh
- **Repository:** [haiphamt/TravelGo](https://github.com/haiphamt/TravelGo)
- **Thiết kế Figma:** [TravelGo](https://www.figma.com/design/QYzdMjHKiquZjUAvHUdXhq/TravelGo?node-id=43-2)
- **Phạm vi và quyết định triển khai:** [Bản chốt TravelGo — 17/10/2026](docs/PHAM_VI_VA_DINH_HUONG_TRAVELGO.md)

TravelGo là đồ án xây dựng nền tảng web hỗ trợ khám phá địa điểm và lập lịch trình đi chơi, du lịch theo thời gian, ngân sách và sở thích. Phạm vi dữ liệu ban đầu tập trung vào **TP.HCM và Đà Lạt**; mục **Góc Địa Phương** triển khai trước tại **TP.HCM**, giúp người dùng tìm hiểu hàng quán nhỏ và đưa các điểm bán phù hợp vào chuyến đi.

Dự án tập trung vào hành trình **khám phá → cùng lựa chọn → lập lịch trình → mở chỉ đường → chia sẻ trải nghiệm và cập nhật thông tin**. Nguồn dữ liệu địa điểm bên ngoài là OpenStreetMap, bổ sung bằng khảo sát và đóng góp có kiểm duyệt của TravelGo. Không thu thập dataset, ảnh hoặc đánh giá từ Google Maps/Google Places API; Google Maps chỉ được mở qua liên kết để tham khảo và dẫn đường.

**Trạng thái:** repository hiện chứa tài liệu định hướng, chưa có mã nguồn ứng dụng Angular/Laravel. Các nội dung dưới đây là phạm vi đã chốt để triển khai, không phải xác nhận chức năng đã hoạt động. Figma và tài liệu yêu cầu cần được đồng bộ với bản chốt mới.

**Các chức năng dự kiến:**

- Tìm kiếm và lọc địa điểm theo thành phố, khu vực, danh mục, giá tham khảo và đánh giá TravelGo.
- Xem thông tin chi tiết, hình ảnh, giờ hoạt động và vị trí địa điểm trên bản đồ.
- Lưu và quản lý danh sách địa điểm yêu thích.
- Dùng chung một hệ thống đánh giá **1–5 sao** cho TP.HCM, Đà Lạt và Góc Địa Phương; nhận xét và ảnh tùy chọn, một đánh giá có thể chỉnh sửa cho mỗi tài khoản tại mỗi địa điểm.
- Khám phá Góc Địa Phương; đề xuất địa điểm, giờ bán và thay đổi điểm bán để quản trị viên xét duyệt; hiển thị thời điểm cập nhật và lưu lịch sử thay đổi.
- Tạo lịch trình thủ công hoặc nhận gợi ý AI từ địa điểm đã có trong TravelGo; tùy chọn ghé hàng quán địa phương tại TP.HCM. Người dùng được sửa, lưu lịch trình và mở Google Maps để dẫn đường.
- Tạo phòng cùng bạn bè, bình chọn và thống nhất địa điểm phù hợp với nhóm.
- Chủ cơ sở/người bán được đề nghị quyền quản lý địa điểm, cập nhật thông tin và phản hồi đánh giá sau khi được xác minh; quản trị viên quản lý tài khoản, địa điểm và nội dung vi phạm.

**Ba actor nghiệp vụ:** Người dùng; Chủ cơ sở/Người bán; Quản trị viên. Khách chưa đăng nhập là trạng thái truy cập của Người dùng, không được tính thành actor thứ tư. Cấp độ đóng góp và vai trò chủ phòng cũng không dùng để bù số actor.

**Tech stack chốt:** Angular (TypeScript) + PHP/Laravel REST API + **MySQL**; Eloquent và migrations cho dữ liệu, Laravel Sanctum cho xác thực, Leaflet để hiển thị bản đồ từ nguồn OSM. Chỉ chọn một hệ quản trị CSDL: **không chạy MySQL và MariaDB song song**. MariaDB là phương án thay thế nếu nhóm quyết định đổi và kiểm thử lại.

Kiến trúc tách lớp trình bày Angular khỏi Laravel API, vận dụng phân tách trách nhiệm MVC. Cách ánh xạ Model–View–Controller và điểm cần đối chiếu với yêu cầu giảng viên được giải thích trong bản chốt. Nhà cung cấp AI và phiên bản cụ thể của các công cụ sẽ được khóa khi khởi tạo ứng dụng.

**Giới hạn:** chưa triển khai tích điểm đổi quà, quyên góp, đặt món, thanh toán hoặc theo dõi người bán theo thời gian thực. Ảnh demo người bán phải có quyền sử dụng và sự đồng ý công khai; không lấy ảnh của website khác chỉ vì ảnh đang hiển thị công khai.

**Đối chiếu cạnh tranh:** Foody, Google Maps, Wanderlog, TikTok, [Gánh Mưu Sinh .vn](https://ganhmuusinh.vn/) và [Gánh Mưu Sinh .io.vn](https://ganhmuusinh.io.vn/). Danh mục đồ ăn, bản đồ hay yếu tố cộng đồng không phải khác biệt độc quyền của TravelGo; bản chốt nêu rõ phần giao nhau, nguồn tham khảo và định vị cần kiểm chứng.

---

## THÀNH VIÊN NHÓM

| STT | MSSV | Họ và Tên | Github | Email |
|-----|:----:|-----------|--------|-------|
| 1 | 24520442 | Phạm Tuấn Hải | [haiphamt](https://github.com/haiphamt) | 24520442@gm.uit.edu.vn |
| 2 | 24520013 | Nguyễn Thị Quỳnh Hân | [QuynhHan486](https://github.com/QuynhHan486) | nguyenhan04081999@gmail.com |
| 3 | 24520306 | Phạm Công Định | [Dingglebell](https://github.com/Dingglebell) | dinhphmlp@gmail.com |
| 4 | 24520486 | Chung Minh Hiếu | [chungminhhieu2311-collab](https://github.com/chungminhhieu2311-collab) | chungminhhieu2311@gmail.com |
| 5 | 24520495 | Lê Nguyễn Hữu Hiếu | [lihanhutiu](https://github.com/lihanhutiu) | huuhieu1209@gmail.com |
| 6 | 24520708 | Triệu Quang Huy | [1can5ez](https://github.com/1can5ez) | 24520708@gm.uit.edu.vn |
