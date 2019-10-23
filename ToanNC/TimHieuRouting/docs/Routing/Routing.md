# **Tìm Hiểu Về Routing**
## **Mục Lục**
- **1.Thế nào là Routing**
- **2.Static Routing**
### **1.Thế nào là Routing**
- Định tuyến là phương thức mà Router(Bộ định tuyến) hay PC(Thiết bị mạng) dùng để chuyển các gói tin đến địa chỉ đích một cách tối ưu nhất , nghĩa là chỉ ra hướng và đường đi tốt nhất cho gói tin. Router thu thập và duy trì các thông tin định tuyến để cho phép truyền và nhận các dữ liệu. Quá trình Routing dựa vào thông tin trên bảng định tuyến (Routing Table), là bảng chứa các lộ trình nhanh và tốt nhất đến các mạng khác nhau trên mạng , để hướng các gói dữ liệu đi một cách hiệu quả nhất
- Thông tin trên bảng định tuyến có thể được cấu hình thủ công hoặc có thể sử dụng một giao thức định tuyến động để tạo ra và tự động cập nhập các thông tin định tuyến. Routing-table là một dạng database cần thiết để tìm đường đi nhanh nhất, nó có thể được xậy dựng thông qua nhiều cách, có thể là do cấu hình người quản trị và cũng có thể được tích hợp trong các giao thức định tuyến.

![ảnh minh hoạ](https://imgur.com/m2UKRYy.png)

![ảnh minh hoạ](https://imgur.com/3tzJqZS.png)
- Khi chúng ta gửi đi một gói dữ liệu từ một máy tính này sang một máy tính khác , đàu tiên quá trình sẽ xác định xem là gói dữ liệu được gửi nội bộ đến máy tính khác trên LAN hay đến Router để định tuyến đến LAN đích
- Nếu gói dữ liệu được gửi tới một máy tính nằm trong LAN khác , nó sẽ được gửi đến Router (hoặc gateway). Sau đó Router sẽ xác định tuyến đi khả thi nhất để chuyển tiếp dữ liệu theo tuyến đó . Gói dữ liệu sẽ được gửi đên Router tiếp theo và quá trình như vậy được lặp lại cho đến khi gặp được LAN đích
- Trong các Router sử dụng thuật toán định tuyến phức tạp , thuật toán này sử dụng một loạt các hệ số gồm có tốc độ của môi trường truyền dẫn , số đoạn mạng và đoạn mạng có khả năng chuyển tải lưu lượng ở mức độ tối thiểu. Các Router sẽ chia sẻ trạng thái và các thông tin định tuyến cho nhau để chúng có thể quản lý lưu lượng và tránh được các kết nối chậm
- Các phương thức định tuyến , Routing được chia làm 2 phương thức chính là:
  - **Static Routing( Định tuyến tĩnh)**
![ảnh minh hoạ](https://imgur.com/TpnIaoV.png)
  - **Dynamic Routing(Định tuyến động)**

![ảnh mình hoạ](https://imgur.com/W6PotWy.png)
- Cụ thể hơn chúng ta có thể xem về sơ đồ phân chia các hình thức định tuyến sau đây
![ảnh minh hoạ](https://imgur.com/sc6tS3e.png)
- Bây giờ chúng ta cùng tìm hiểu về một số khái niệm khác như: 
  - Routing Protocol: là ngôn ngữ để một Router trao đổi với một Router khác để chia sẻ thông tin định tuyến về khả năng được đến mạng đích cũng như trạng thái của mạng, routing protocol được cài đặt trên các Router nhằm xây dựng Routing table và đảm bảo rằng tất cả các Router đều có Routing table tương thích với nhau.
  - Routed Protocol: sử dụng Routing table mà Routing protocol xây dựng nên để đảm bảo việc truyền dữ liệu trên mạng một cách đáng tin cậy (IP, IPX..).
  - Vùng tự trị AS (Autonomous System): là tập hợp các mạng có cùng chính sách định tuyến và được kết nối với nhau thông qua các Router, mỗi hệ thống AS thường thuộc quyền sở hữu của một công ty hoặc của nhà cung cấp dịch vụ Internet (ISP). Mỗi AS đều có một số nhận diện được cung cấp bởi một nhà cung cấp AS (Internet Registy).
![ảnh minh hoạ](https://imgur.com/mE753po.png)
  - Administrative Distance (AD): được sử dụng để đánh giá độ tin cậy của thông tin định tuyến mà Router nhận được từ Router hàng xóm. AD có giá trị nguyên từ: 0 đến 255; “0” là độ tin cậy cao nhất và “255” có nghĩa là không có lưu lượng đi qua tuyến này (không được sử dụng để vận chuyển thông tin). Khi Router nhận được một thông tin định tuyến, thông tin này được đánh giá và được đưa vào bảng định tuyến.
  - Ngoài ra chúng ta còn một số khái niệm thường dùng khi định tuyến như **IP address**,**Subnet mask**,**Default gateway**
    - **IP address**:Địa chỉ IP - Xác định một máy duy nhất trên mạng cục bộ.
    - **Subnet mask**:Mặt nạ mạng con - Xác định mạng con máy chủ mạng.
    - **Default gateway**:Cổng mặc định - Xác định bộ định tuyến mà gói tin được gửi đến khi đích không nằm trên cùng mạng con mạng cục bộ.

![ảnh minh hoạ](https://imgur.com/kzZxeFS.png)
### **2.Static Routing**
#### **2.1. Khái niệm và nguyên lý làm việc**
- Chúng ta cùng tìm hiểu về quá trình định tuyễn tĩnh nhé. Static Routing(định tuyến tĩnh) là quá trình mà người quản trị mạng sẽ nhập tất cả thông tin về đường đi cho router.Vì vậy khi mà cấu trúc mạng có sự thay đổi thì người quản trị sẽ thay đổi lại bằng cách xoá hay thêm các thông tin về đường đi cho router, nói cách khác đường này là đường cố định.
- Nguyên lý hoạt động của Static Routing có thể hiểu như sau:
  - Đầu tiên người quản trị cấu hình các đường đi cố định cho router
  - Sau đó, router sẽ cài đặt đường đi này vào bảng định tuyến.
  - Và gói dữ liệu được gửi theo đường cố định
- Có 3 cách để chỉ ra đường đi cho router :
  - chỉ theo cổng ra của router: ở cách này chúng ta cần cung cấp cho router nhưng thông số như IP đích, sub mask và getway cụ thể về câu lệnh mọi người có thể xem sau

![ảnh minh hoạ](https://imgur.com/IgifY29.png)
  - chỉ theo theo ip liền kề 
![ảnh minh hoạ](https://imgur.com/6gZlbKy.png)
  - Default Route: xét về câu lệnh cấu hình cũng tương tự như 2 dạng trên chỉ có khác một điều là không cần biết địa chỉ đích và Subnet Mask.

![ảnh minh hoạ](https://imgur.com/kQsJwId.png)
- Các địa chỉ IP được định tuyến tĩnh thì trong bảng định tuyến của router sẽ được ký hiệu bằng chữ *S* ở đầu, riêng với lênh IP route thì nó sẽ là ký hiệu S* ở đầu

![ảnh minh hoạ](https://imgur.com/TuLOJk1.png)
![ảnh minh hoạ](https://imgur.com/UmcO4ul.png)

#### **2.2.Ưu nhược điểm của Static Routing**
- Vậy **Static routing** có nhưng ưu nhược điểm như nào so với cách **Dynamic routing(định tuyến động)** 
  - Ưu Điểm:
    - Dễ cấu hình, dễ hiểu
    - Các định tuyến tĩnh không được quảng cáo qua mạng ,lên độ bảo mật tốt hơn
    - Các định tuyến tĩnh sử dụng ít băng thông hơn các giao thức định tuyến động, không có chu kỳ CPU nào được sử dụng để tính toán và giao tiếp trên các tuyến
    - Đường dẫn mà một định tuyến tĩnh sử dụng dể gửi dữ liệu là được chỉ định và người quản trị biết
  - Nhược điểm:
    - Cấu hình và bảo trì mất nhiều thời gian
    - cấu hình dễ lỗi khi gặp các mạng lớn
    - Cần có sự can thiệt của quản trị viên để duy trì thay đổi thông tin tuyến đường
    - Không mở rộng quy mô với các mạng lưới đang phát triển
    - Đòi hỏi kiến thức và tỷ mỉ trong quá trình cấu hình để không nhầm lẫn
#### **2.3.Mục đích của Static Routing**
- Mục đính của **Static Routing** nó có 3 mục đích chính là :
  - Cung cấp dễ dàng bảo trì bảng đinh tuyến trong các mạng nhỏ và dự kiến sẽ không tăng trưởng đáng kể
  - Định tuyến đến các mạng sơ khai là một mạng được truy cập bởi một tuyến duy nhất và bộ định tuyến không có hàng xóm khác
  - Sử dụng một tuyến mặc định duy nhất để biểu thị một đường dẫn đến bất kỳ mạng nào không có kết quả khớp cụ thể hơn với một tuyến khác trong bảng định tuyến . Các tuyến mặc định sử dụng để gửi lưu lượng đến bất kỳ đích nào ngoài bộ định tuyến 

[link tham khảo](https://vnpro.vn/thu-vien/static-route-la-gi-2045.html)

[link tham khảo](https://hocvienit.wordpress.com/2012/04/24/static-routing/)

  


