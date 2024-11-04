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




ngày 3 21/10

 1 Actions

Attributes bắt buộc:

type: Phân loại hành động, xác định cách hành động được xử lý.


name: Mô tả ngắn gọn về hành động, có thể hiển thị trên giao diện người dùng.


Các dạng trả về:

False: Đóng bất kỳ hộp thoại hành động nào đang mở.

String: Xử lý như nhãn của hành động.

Number: Đọc bản ghi hành động từ cơ sở dữ liệu.

Dictionary: Thực hiện hành động như mô tả.

Attributes tùy chọn:

binding_model_id: Xác định mô hình mà hành động liên kết.

binding_type: Xác định loại menu ngữ cảnh mà hành động sẽ xuất hiện.

2 Window Actions (ir.actions.act_window)

Mô tả: Sử dụng để hiển thị các mô hình qua các view.

Fields chính:

res_model: Mô hình cần hiển thị.

views: Danh sách các cặp (view_id, view_type).

res_id: Bản ghi cụ thể (tùy chọn).

domain: Bộ lọc mặc định cho các truy vấn tìm kiếm.

3 URL Actions (ir.actions.act_url)

Mô tả: Mở một URL (trang web).

Fields chính:

url: Địa chỉ cần mở.

target: Xác định cách mở URL (mới hay tự thay thế).

4 Server Actions (ir.actions.server)

Mô tả: Hành động có thể thực thi mã Python hoặc các hành động khác.

Fields chính:

id: Định danh của hành động trong cơ sở dữ liệu.

context: Dữ liệu ngữ cảnh khi thực hiện hành động.

5 Report Actions (ir.actions.report)

Mô tả: Kích hoạt việc in một báo cáo.

Fields chính:

name: Tên báo cáo.

model: Mô hình của báo cáo.

report_type: Loại báo cáo (PDF hoặc HTML).

6 Client Actions (ir.actions.client)

Mô tả: Kích hoạt hành động thực hiện hoàn toàn trong client.

Fields chính:

tag: Nhận diện hành động phía client.

params: Dữ liệu bổ sung gửi tới client.

7 Automated Actions (ir.cron)

Mô tả: Hành động tự động được kích hoạt theo tần suất đã định.

Fields chính:

name: Tên hành động tự động.

interval_number: Số đơn vị thời gian giữa hai lần thực hiện.

code: Nội dung mã của hành động.



Quyền Truy Cập (Access Rights)

Chức năng: Cấp quyền truy cập cho toàn bộ mô hình với một tập hợp các thao tác.

Nguyên tắc: Nếu không có quyền truy cập phù hợp cho một thao tác trên mô hình của người dùng (thông qua nhóm của họ), người dùng sẽ không có quyền truy cập.

Quy tắc: Quyền truy cập là cộng dồn. Quyền truy cập của một người dùng là sự hợp nhất của các quyền mà họ nhận được từ tất cả các nhóm.

Ví dụ: Người dùng thuộc nhóm A (cấp quyền đọc và tạo) và nhóm B (cấp quyền cập nhật) sẽ có quyền tạo, đọc và cập nhật.
Class ir.model.access:

name: Mục đích hoặc vai trò của nhóm.

model_id: Mô hình mà quyền truy cập ACL kiểm soát.

group_id: Nhóm (res.groups) mà quyền truy cập được cấp; nếu group_id trống, quyền ACL sẽ được cấp cho mọi người dùng.

perm_method: Các thuộc tính cho phép quyền CRUD tương ứng khi được thiết lập, mặc định không được thiết lập.

perm_create: Quyền tạo.

perm_read: Quyền đọc.

perm_write: Quyền cập nhật.

perm_unlink: Quyền xóa.

2 Quy Tắc Bản Ghi (Record Rules)

Chức năng: Là các điều kiện cần được thỏa mãn để cho phép một thao tác.

Nguyên tắc: Quy tắc bản ghi được đánh giá từng bản ghi một, theo quyền truy cập.

Mặc định cho phép: Nếu quyền truy cập cấp quyền và không có quy tắc nào áp dụng cho thao tác và mô hình của người dùng, quyền truy cập sẽ được cấp.
Class ir.rule:

name: Mô tả quy tắc.

model_id: Mô hình mà quy tắc áp dụng.

groups: Nhóm (res.groups) mà quyền truy cập được cấp (nhiều nhóm có thể được chỉ định). Nếu không chỉ định nhóm, quy tắc sẽ là toàn cầu.
global: Xác định tình trạng toàn cầu (hay không) của quy tắc.

domain_force: Một điều kiện được chỉ định dưới dạng miền; quy tắc cho phép các thao tác được chọn nếu miền khớp với bản ghi và ngược lại.
Các biến có sẵn trong miền:



time: Mô-đun thời gian của Python.

user: Người dùng hiện tại, dưới dạng một recordset đơn lẻ.

company_id: ID công ty hiện tại của người dùng.

company_ids: Tất cả các công ty mà người dùng hiện tại có quyền truy cập, dưới dạng danh sách các ID công ty.

Các thuộc tính perm_method: Khác với ir.model.access, cho phép xác định thao tác mà quy tắc áp dụng. Nếu thao tác không được chọn, quy tắc sẽ không được kiểm tra.

perm_create: Quyền tạo.

perm_read: Quyền đọc.

perm_write: Quyền cập nhật.

perm_unlink: Quyền xóa.





ngày 4: 24/10

Controllers

Khái niệm: Controllers trong Odoo cung cấp cơ chế mở rộng riêng, khác với các model, để xử lý các yêu cầu HTTP. Điều này là cần thiết vì một số tiền đề (như cơ sở dữ liệu) có thể chưa sẵn có.

Tạo Controller: Các controller được tạo ra bằng cách kế thừa từ lớp Controller. Các route được định nghĩa thông qua các phương thức được trang trí bằng @route():


Ghi đè Controller: Để ghi đè một controller, bạn kế thừa từ lớp của nó và ghi đè các phương thức liên quan. Việc trang trí bằng @route() là cần thiết để giữ cho phương thức (và route) vẫn hiển thị:

Thay đổi quyền truy cập: Bạn có thể thay đổi quyền truy cập bằng cách cung cấp các tham số khác nhau cho decorator @route(), ví dụ:

Routing: Sử dụng @odoo.http.route() để định tuyến các yêu cầu HTTP đến các phương thức được trang trí.

Tham số:

route: Đường dẫn mà phương thức phục vụ.

type: Loại yêu cầu (json hoặc http).

auth: Phương thức xác thực (user, public, none).

methods: Danh sách các phương thức HTTP (verb) mà route này áp dụng.

cors: Giá trị của chỉ thị Access-Control-Allow-Origin.

csrf: Bật hoặc tắt bảo vệ CSRF cho route.

Request: Đối tượng yêu cầu được tự động thiết lập tại odoo.http.request vào đầu mỗi yêu cầu. Nó cung cấp nhiều phương thức tiện ích như update_env(), csrf_token(), và get_http_params() để làm việc với các thông tin yêu cầu.

Response:

make_response() và make_json_response() giúp tạo các phản hồi không phải HTML hoặc phản hồi JSON.
not_found() trả về phản hồi HTTP 404.
render() cho phép tạo các mẫu QWeb.

QWeb là công cụ tạo mẫu chính được sử dụng bởi Odoo. Đây là một công cụ tạo mẫu dựa trên XML, chủ yếu được sử dụng để tạo các đoạn và trang HTML.

Các chỉ thị đặc biệt
t-field: Dùng khi thực hiện truy cập trường trên bản ghi "thông minh".
t-debug: Kích hoạt một trình gỡ lỗi.
t-cache: Lưu trữ các phần của mẫu để giảm thiểu thời gian render.



Xuất khẩu các thuật ngữ có thể dịch
Xuất khẩu thuật ngữ:

Truy cập vào giao diện quản trị và chọn Cài đặt ‣ Dịch thuật ‣ Nhập/Xuất ‣ Xuất Dịch thuật.
Giữ ngôn ngữ mặc định (mẫu trống).
Chọn định dạng PO File và module của bạn.
Nhấn Xuất và tải xuống tệp.
Di chuyển tệp .pot vào thư mục yourmodule/i18n/.
Tạo tệp dịch:

Tệp .pot là mẫu chứa các chuỗi có thể dịch. Bạn có thể tạo tệp PO từ mẫu này bằng công cụ như POEdit hoặc sao chép và đổi tên thành language.po.
Xuất khẩu ngầm và rõ ràng
Xuất khẩu ngầm: Odoo tự động xuất các chuỗi từ nội dung kiểu "data" như:

Các nút văn bản trong các chế độ xem không phải QWeb.
Các mẫu QWeb (trừ các khối được đánh dấu bằng t-translation="off").
Xuất khẩu rõ ràng: Nếu cần xuất khẩu các thuật ngữ trong mã Python hoặc JavaScript, hãy bao quanh chuỗi bằng các hàm:

Biến: Tránh việc sử dụng biến trong các chuỗi có thể dịch. Sử dụng tham số:


Khối: Không chia nhỏ chuỗi thành nhiều khối. Giữ nguyên câu đầy đủ trong một khối để dịch dễ dàng:

Quy tắc số nhiều và thời gian chạy
Số nhiều: Đừng áp dụng quy tắc số nhiều theo cách tiếng Anh. Sử dụng cấu trúc phù hợp cho từng ngôn ngữ:

Thời gian chạy: Không nên gọi hàm dịch ngay tại thời điểm khởi động server hoặc khi tệp JavaScript được đọc. Sử dụng phương pháp dịch lười (lazy):





Ngày 5 :

Tổng quan về Khung JavaScript trong Odoo
Khung JavaScript của Odoo được thiết kế để hoạt động với ba trường hợp sử dụng chính:

Web Client: Ứng dụng web riêng biệt cho phép người dùng xem và chỉnh sửa dữ liệu kinh doanh. Đây là ứng dụng trang đơn (SPA), nơi dữ liệu mới được tải từ máy chủ khi cần mà không cần tải lại toàn bộ trang.

Trang Web: Phần công khai của Odoo, cho phép người dùng không xác định duyệt nội dung, mua sắm hoặc thực hiện nhiều hành động với tư cách là khách hàng. Đây là một trang web cổ điển với nhiều tuyến đường và các điều khiển tương tác.

Điểm Bán Hàng: Giao diện cho điểm bán hàng, cũng là một ứng dụng trang đơn chuyên biệt.

Khách Hàng Web
WebClient: Đây là thành phần gốc của toàn bộ giao diện người dùng. Nó sắp xếp tất cả các thành phần phụ và cung cấp các dịch vụ như RPC (Remote Procedure Calls) và lưu trữ cục bộ.

Trong thời gian chạy, web client hoạt động như một ứng dụng trang đơn, yêu cầu dữ liệu cần thiết mà không cần tải lại trang đầy đủ, và quản lý URL đồng bộ với trạng thái của ứng dụng.

Tổng Quan về Mã JS của Máy Khách Web
Mã máy khách web được tìm thấy trong thư mục web/static/src/js với các tệp quan trọng như:

boot.js: Định nghĩa hệ thống module, cần được tải trước.

core/: Chứa các khối xây dựng cấp thấp, bao gồm hệ thống lớp và tiện ích.

chrome/: Chứa các tiện ích lớn tạo nên phần lớn giao diện người dùng.

Quản Lý Tài Sản
Quản lý tài sản trong Odoo bao gồm việc định nghĩa một tập hợp các bundle trong XML, với mỗi bundle là một tập hợp các tệp JavaScript, CSS, và SCSS.

Các tài sản được định nghĩa trong addons/web/views/webclient_templates.xml và có thể được chèn vào mẫu thông qua các chỉ thị như t-call-assets.

Gói Chính
Odoo kiểm tra dấu thời gian của các tệp trong mỗi gói khi khởi động, tạo hoặc tái tạo các gói khi cần thiết. Một số gói quan trọng bao gồm:

web.assets_common: Chứa hầu hết các tài sản chung cho máy khách web, trang web, và điểm bán hàng.

web.assets_backend: Dành riêng cho máy khách web và trình quản lý hành động.

web.assets_frontend: Bao gồm tài sản dành riêng cho trang web công cộng như thương mại điện tử và diễn đàn.

Thêm Tệp vào Gói Tài Sản
Để thêm một tệp vào một bundle, cần thực hiện các bước sau:

Thêm tệp asset.xml vào thư mục views/.
Thêm chuỗi 'views/assets.xml' vào khóa data trong tệp manifest.
Tạo chế độ xem kế thừa của gói mong muốn và thêm tệp bằng biểu thức XPath.
Xử Lý Vấn Đề Tệp Không Tải/Cập Nhật
Nếu tệp không được tải đúng cách, có thể thử các giải pháp sau:

Khởi động lại máy chủ để tạo lại tài sản.
Kiểm tra bảng điều khiển để tìm lỗi.
Sử dụng chế độ debug để ép máy chủ cập nhật các tệp tài sản.
Khởi động máy chủ với tùy chọn --dev=all để tự động vô hiệu hóa tài sản khi cần thiết.
Hệ Thống Mô-đun JavaScript
Hệ thống mô-đun trong Odoo đảm bảo các tệp JavaScript được tải theo đúng thứ tự. Mô-đun được định nghĩa bằng cách sử dụng hàm odoo.define, có thể khai báo các phụ thuộc rõ ràng.

Định Nghĩa Một Mô-đun
Mô-đun được định nghĩa với ba đối số: tên mô-đun, danh sách phụ thuộc, và hàm xử lý. Nếu phụ thuộc chưa sẵn sàng, mô-đun sẽ không được tải.

Mixin trong Odoo

Hỗn hợp (Mixin) cho phép chia sẻ hành vi giữa các lớp mà không cần đa kế thừa.

Ví dụ về việc sử dụng mixin để thêm phương thức dance vào lớp Hamster.

Vá lớp hiện có

Phương thức include cho phép sửa đổi lớp đã tồn tại, ảnh hưởng đến tất cả các trường hợp của lớp đó.

Cần thực hiện cẩn thận vì điều này có thể thay đổi hành vi của lớp trong toàn bộ ứng dụng.

Tiện ích (Widgets)

Lớp Widget là một phần quan trọng trong giao diện người dùng Odoo, cho phép tạo ra các thành phần UI với nhiều tính năng.

Tiện ích hỗ trợ việc quản lý vòng đời (init, willStart, render, start, destroy).

Ví dụ về một tiện ích đếm:

Cung cấp một ví dụ đơn giản về cách tạo một tiện ích đếm với các sự kiện và mẫu QWeb.

Vòng đời của Widget

Các phương thức trong vòng đời của Widget:

init: Khởi tạo trạng thái.

willStart: Thực hiện công việc không đồng bộ.

start: Thực hiện công việc sau khi render.

destroy: Dọn dẹp và xóa widget khỏi DOM.

API tiện ích

Cung cấp nhiều thuộc tính và phương thức để tương tác với DOM, xử lý sự kiện, và quản lý các mẫu QWeb.

Một số phương thức API quan trọng:

appendTo(), prependTo(), insertAfter(), và insertBefore(): Dùng để chèn widget vào DOM.

setElement(): Đặt lại gốc DOM của widget.



