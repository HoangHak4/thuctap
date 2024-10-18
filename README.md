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



Ngày 2 18/10

+ ORM API
* Models
   Định nghĩa Mô Hình: Bạn có thể tạo một mô hình bằng cách kế thừa từ lớp models.Model

   Trường và Phương Thức: Không thể định nghĩa một trường và một phương thức có cùng tên, nếu không trường sẽ ghi đè phương thức.

   Nhãn Trường (Field Label): Nhãn mặc định của một trường là tên viết hoa của trường đó, nhưng bạn có thể thay đổi bằng cách sử dụng tham số string

   Giá trị Mặc Định: Giá trị mặc định có thể được chỉ định trực tiếp hoặc thông qua một hàm

   Loại Mô Hình: Odoo cung cấp các loại mô hình khác nhau

   Recordset: Mỗi bản ghi trong Odoo được biểu diễn dưới dạng một tập hợp bản ghi có thứ tự (recordset). Các recordset này có thể được trả về từ các phương thức như browse(), search(), hoặc qua truy cập trường.

   Kế Thừa: Odoo hỗ trợ kế thừa mô hình. Bằng cách sử dụng _inherits, mô hình mới có thể kế thừa các trường từ mô hình khác mà không lưu trữ trực tiếp

   Các Thuộc Tính Mô Hình Khác: Một số thuộc tính khác trong mô hình bao gồm:


   _auto: Xác định xem có tự động tạo bảng cơ sở dữ liệu hay không.

   _order: Trường mặc định để sắp xếp bản ghi.

   _rec_name: Trường sử dụng để dán nhãn cho bản ghi.

   _parent_name: Trường many2one dùng để liên kết cha con


* Fields
Thuộc tính của các trường
string: Nhãn của trường được hiển thị cho người dùng. Nếu không được thiết lập, hệ thống sẽ sử dụng tên của trường và tự động viết hoa.  


help: Chuỗi chú giải công cụ hiển thị khi người dùng di chuột qua trường.


invisible: Quy định trường có được ẩn hay không (boolean, mặc định là False).


readonly: Quy định trường có chỉ đọc không. Điều này chỉ ảnh hưởng đến giao diện người dùng (UI), nhưng việc gán giá trị trong mã vẫn có hiệu lực.


required: Xác định trường có bắt buộc phải có giá trị hay không (boolean, mặc định là False).


index: Quy định trường có được lập chỉ mục trong cơ sở dữ liệu hay không, và loại chỉ mục:


"btree": chỉ mục chuẩn.
"trigram": chỉ mục tìm kiếm toàn văn.
None: không lập chỉ mục (mặc định).


default: Giá trị mặc định cho trường, có thể là một giá trị tĩnh hoặc một hàm.


states: Một từ điển ánh xạ các giá trị trạng thái đến thuộc tính UI (readonly, required, invisible).


groups: Danh sách các nhóm người dùng được phép truy cập trường.


company_dependent: Quy định giá trị của trường có phụ thuộc vào công ty hiện tại hay không.

copy: Xác định trường có nên được sao chép khi bản ghi được sao chép hay không.


store: Quy định trường có được lưu trữ trong cơ sở dữ liệu hay không.


group_operator: Hàm tổng hợp sử dụng khi nhóm (group) trường này, ví dụ: sum, avg, count.


Kiểu trường cơ bản:


Boolean: Trường kiểu boolean (đúng/sai).


Char: Trường chuỗi, thường hiển thị dưới dạng một dòng văn bản.


size: Độ dài tối đa của chuỗi.


trim: Có cắt bỏ khoảng trắng hay không (mặc định True).


translate: Cho phép dịch chuỗi (mặc định là True).


Float: Trường số thực (float).


digits: Độ chính xác của số thập phân (tùy chọn).


Các phương thức tĩnh:

round(): Làm tròn số float với độ chính xác cụ thể.
is_zero(): Kiểm tra số float có bằng không với độ chính xác cụ thể không.


compare(): So sánh hai số float với độ chính xác cụ thể.


Integer: Trường kiểu số nguyên (integer).


Các trường tính toán:

compute: Tên của phương thức tính toán trường. Trường được tính toán và không lưu trực tiếp trong cơ sở dữ liệu.


inverse: Tên của phương thức đảo ngược (khi cần lưu ngược lại giá trị tính toán).


search: Tên của phương thức tìm kiếm tùy chỉnh cho trường.


related: Chuỗi các tên trường liên quan, cho phép truy cập trường từ mô hình khác.


precompute: Xác định liệu trường có nên được tính toán trước khi lưu bản ghi vào cơ sở dữ liệu hay không (mặc định False).


Các hàm tổng hợp cho group_operator:

array_agg: Gộp các giá trị thành một mảng.


count: Đếm số bản ghi.
sum: Tổng các giá trị.
avg: Tính giá trị trung bình.
min: Lấy giá trị nhỏ nhất.
max: Lấy giá trị lớn nhất.
* Recordsets

Cho phép trùng lặp:

Trái ngược với tên gọi, các recordsets có thể chứa các bản ghi trùng lặp, mặc dù điều này có thể thay đổi trong tương lai.
Phương thức mô hình trên Recordsets:

Các phương thức được định nghĩa trong một mô hình được thực thi trên các recordsets, trong đó self tham chiếu đến recordset

Lặp qua Recordsets:

Lặp qua một recordset sẽ tạo ra "singleton", tương tự như lặp qua một chuỗi trong Python

Truy cập trường
Truy cập trực tiếp:
Các trường có thể được đọc và ghi trực tiếp như thuộc tính

Sử dụng Mapped cho nhiều bản ghi:
Đối với các trường không liên kết trên nhiều bản ghi, sử dụng phương thức mapped()