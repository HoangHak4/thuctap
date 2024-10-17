# thuctap

 Ngày 17/10
Ngày Hôm nay em đọc phần : Xây dựng module
 + Cấu trúc: 
 Thư mục
data/: Chứa dữ liệu mẫu và dữ liệu XML.


models/: Định nghĩa các mô hình (model).


controllers/: Chứa các bộ điều khiển (HTTP routes).


views/: Chứa các chế độ xem và mẫu (templates).


static/: Chứa các tài sản web, được chia thành các thư mục như css/, js/, img/, lib/.


wizard/: Nhóm các mô hình tạm thời và chế độ xem của chúng.


report/: Chứa báo cáo và mô hình có thể in.
 

tests/: Chứa các bài kiểm tra Python.


Đặt tên Tập tin
Tên tệp nên phản ánh mô hình chính, với các tệp mô hình được phân loại rõ ràng.


Đối với bảo mật, sử dụng ba tệp chính: ir.model.access.csv, <module>_groups.xml, và <model>_security.xml.


Các tệp chế độ xem nên có hậu tố _views.xml và các mẫu nên được lưu trong tệp <model>_templates.xml.


Tên tệp chỉ nên chứa ký tự [a-z0-9_].

Các tập tin XML: 

Sử dụng <record> để khai báo bản ghi trong XML, với id trước model.


Đặt thuộc tính name đầu tiên trong khai báo trường.


Nhóm các bản ghi theo mô hình.


Sử dụng <data> cho dữ liệu không thể cập nhật và đặt noupdate=1 khi cần thiết

ID XML và đặt tên
Menu: <model_name>_menu hoặc <model_name>_menu_do_stuff


Chế độ xem: <model_name>_view_<view_type>


Hành động: <model_name>_action_<detail>


Nhóm người dùng: <module_name>_group_<group_name>


Quy tắc: <model_name>_rule_<concerned_group>

Tổ chức Tập tin Tĩnh
Thư mục Tĩnh: Tất cả các tệp tĩnh nằm trong thư mục static/, được phục vụ với tiền tố là tên tiện ích bổ sung.
Cấu trúc thư mục:
static/: Tất cả các tệp tĩnh.


static/lib/: Thư mục chứa các thư viện JavaScript.


static/src/: Thư mục chứa mã nguồn tĩnh.


static/src/css/: Tất cả các tệp CSS.


static/src/fonts/: Tệp phông chữ.


static/src/images/: Tệp hình ảnh.


static/src/js/: Tệp JavaScript.


static/src/js/tours/: Tệp hướng dẫn người dùng.


static/src/scss/: Tệp SCSS.


static/src/xml/: Tệp mẫu QWeb.


static/tests/: Tệp thử nghiệm.

Cú pháp và Định dạng SCSS
Khoảng thụt lề: 4 khoảng trắng, không sử dụng tab.


Chiều rộng tối đa: 80 ký tự cho mỗi cột.


Dấu ngoặc nhọn mở {: có khoảng trống sau bộ chọn cuối cùng.


Dấu ngoặc nhọn đóng }: trên một dòng mới riêng biệt.


Một dòng cho mỗi khai báo và sử dụng khoảng trắng có ý nghĩa.
Thiết lập Stylelint

Ngày mai thì em sẽ đọc phần:
+ ORM API
* Models
* Fields
* Recordsets
* ORM methods

* Method decorators
* Environment
* Inheritance
