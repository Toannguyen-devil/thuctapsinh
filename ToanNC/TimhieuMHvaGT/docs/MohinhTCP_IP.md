# *Mô Hình TCP/IP và Một Số Giao Thức**
## **Mục Lục**
- **1.Tìm Hiểu Mô Hình TCP/IP**
- **2.Quá Trình Chuyển Hoá Dữ Liệu Trong TCP/IP**
- **3.Tìm Hiểu Về Một Số Giao Thức ở Tầng Application**
- **4.Một Số Giao Thức ở Các Tầng Dưới**
### **1.Tìm Hiểu Mô Hình TCP/IP**
- **Bộ giao thức TCP/IP**: (tiếng Anh: Internet protocol suite hoặc IP suite hoặc TCP/IP protocol suite - bộ giao thức liên mạng), là một bộ các giao thức truyền thông cài đặt chồng giao thức mà Internet và hầu hết các mạng máy tính thương mại đang chạy trên đó. Bộ giao thức này được đặt tên theo hai giao thức chính của nó là TCP (Giao thức Điều khiển Giao vận) và IP (Giao thức Liên mạng). Chúng cũng là hai giao thức đầu tiên được định nghĩa.Như nhiều bộ giao thức khác, bộ giao thức TCP/IP có thể được coi là một tập hợp các tầng, mỗi tầng giải quyết một tập các vấn đề có liên quan đến việc truyền dữ liệu, và cung cấp cho các giao thức tầng cấp trên một dịch vụ được định nghĩa rõ ràng dựa trên việc sử dụng các dịch vụ của các tầng thấp hơn. Về mặt lôgic, các tầng trên gần với người dùng hơn và làm việc với dữ liệu trừu tượng hơn, chúng dựa vào các giao thức tầng cấp dưới để biến đổi dữ liệu thành các dạng mà cuối cùng có thể được truyền đi một cách vật lý.
- Theo một số cách chia ngày xưa thì mô hình TCP/IP chỉ có 4 tầng là **Application**,**Transport**,**Network** và **Link** đến thời điểm hiện tại họ đã tách tầng **Link** thành hai tầng là **Data-Link** và **Physical** như vậy mới cách chia này thì mô hình TCP/IP của chúng ta sẽ có 5 tầng 

![ảnh minh hoạ](https://imgur.com/Wi6jFYD.png)
- Vậy khi so với mô hình OSI thì mô hình TCP/IP đã ít hai hai tầng so vs mô hình OSI 

![ảnh minh hoạ](https://imgur.com/yv9T4pl.png)
  
  - Như vậy chúng ta có thế thấy rằng trong mô hình TCP/IP tầng**Application** là bao gồm 3 tầng **Application**,**Presentation**,**Session** của mô hình OSI , vậy bây giờ chúng ta cùng đi cụ thể vào từng tâng nha.
     - **Tầng Application**: là tầng ứng dụng ở đây có hầu hết các giao thức để phục vụ cho quá trình truyền thông giữ người dùng và Internet
![ảnh minh hoạ](https://imgur.com/WUciDUa.png)
     - **Tầng Transport**: là tầng giao vận có nhiệm vụ tạo các kết nối giao thức như là điểu khiển chuyền ảo TCP, giao thức gói dữ liệu người dùng UDP giữa máy chủ và mạng , nó còn giúp chỉ định các cổng cho các quy trình đang chạy trên máy để TCP và UDP có thể mô tả chi tiết về cổng nguồn và cổng đích
![ảnh minh hoạ](https://imgur.com/3HIjY55.png)
     - **Tầng Network**: là tâng mạng có nhiệm vụ định tuyến thêm các địa chỉ IP để định tuyến cho gói tin di chuyển trong mạng gói tin khi đó sẽ được có thêm địa chỉ Logic nguồn và Logic đích
![ảnh minh hoạ](https://imgur.com/noDlSXV.png)
     - **Tầng Data-Link**: là tầng liên kết dữ liệu tại tầng này các gói tin sẽ được thêm cái địa chỉ vật lý(địa chỉ MAC) để nhằm kiểm soát phương tiện truyền dẫn vật lý và định tuyến chính xác hơn
![ảnh minh hoạ](https://imgur.com/1rlkQee.png)
     - **Tầng Physical**: là tâng vật lý nó gửi và nhận tín hiệu trên dây vật lý hoặc ăng-ten để truyền các bit đượcc tìm thấy trong khung
![ảnh minh hoạ](https://imgur.com/mDDVMfT.png)
### **2.Quá Trình Chuyển Hoá Dữ Liệu Trong TCP/IP**
![ảnh minh hoạ](https://imgur.com/9O5K7dF.png)

- **Tầng Application**:tạo ra một thông báo. Trong trường hợp này, ứng dụng cụ thể là một trình duyệt web yêu cầu tải xuống trang web. Thông báo này sau đó được gửi đến tầng Transport.
- **Tầng Transport**:Tầng Giao vận thêm tiêu đề TCP hoặc UDP bao gồm các địa chỉ cổng nguồn và đích. Thông tin bổ sung như số thứ tự gói được sử dụng cho TCP cũng sẽ được thêm vào tiêu đề. Dữ liệu được tạo bởi lớp vận chuyển được gọi là Phân đoạn nếu TCP được sử dụng và được gọi là Datagram nếu sử dụng UDP. Đoạn này sau đó được gửi đến lớp Mạng.
- **Tầng Network**:Tầng mạng thêm một tiêu đề bao gồm địa chỉ IP nguồn và đích để tạo gói. Gói này sau đó được gửi đến lớp Liên kết dữ liệu.
- **Tầng Data-Link**: Tầng liên kết dữ liệu thêm một tiêu đề chứa thông tin địa chỉ MAC để tạo khung. Khung sau đó được gửi đến lớp Vật lý để truyền các bit.
- **Tầng Physical**: Tầng vật lý nhận các chuỗi bit từ trên và truyền nó đi 
![ảnh minh hoạ](https://imgur.com/bxTSWnn.png)
### **3.Tìm Hiểu Về Một Số Giao Thức ở Tầng Application**
- **DHCP(Dynamic Host Configuration Protocol)** : là giao thức cấu hình máy chủ động chịu trách nhiệm yêu cầu và cung cấp địa chỉ Logic(IP). Máy khách DHCP tự động yêu cầu địa chỉ IP từ máy chủ DHCP khi phát hiện một mạng .Một máy chủ DHCP thường chạy bộ định tuyến và cung cấp địa chỉ IP cho các máy khách DHCP

![ảnh minh hoạ](https://imgur.com/mJ71Fcx.png)
- **DNS(Domain Name System)**: hệ thống tên mình cho phép người dùng mạng có thể truy nhập trang wed bằng cách cung cấp trên trang wed hoặc tên miền thay vì việc phải nhớ địa chỉ IP của trang wed đó. Nó ánh xạ tên miền đến địa chỉ IP. Máy chỉ cần địa chỉ IP(không phải tên miền hay tên gói) của máy chủ wed để trao đổi tin

![ảnh minh hoạ](https://imgur.com/bT4Ejsv.png)
- **HTTP(Hypertext Transfer Protocol )**: giao thức truyền siêu văn bản được sử dụng phổ biến nhất vì nó chuyển các trang wed từ máy chủ wed sang thành trình duyệt wed. Các trang wed được viết bằng HTML(Hypertext Markup Language), nói cách khác HTTP được sử dụng để chuyển các tệp HTML

![ảnh minh hoạ](https://imgur.com/oVWdaC2.png)
- **Telnet(Bi-directional serial text communication)**:là một ứng dụng cho phép giao tiếp văn bản hai chiều thông qua một ứng dụng đầu cuối như  HyperTerm hoặc TeraTerm.
 
![ảnh minh hoạ](https://imgur.com/ImItucP.png)
- **FTP(File Transfer Protocol)**: là giao thức truyền tải tập tin được dùng trong việc trong đổi dữ liệu trong mạng thông qua giao thức TCP/IP, thường hoạt động trên hai công là 20 và 21.Với giao thức này, các máy client trong mạng có thể truy cập đến máy chủ FTP để gửi hoặc lấy dữ liệu. Điểm nổi bật là người dùng có thể truy cập vào máy chủ FTP để truyền và nhận dữ liệu dù đang ở xa.

![ảnh minh hoạ](https://imgur.com/mosdUUg.png)
- **TFTP(Trivial File Transfer Protocol)**: được sử dụng để tệp tin trên mạng cục bộ(LAN). Nó có thể sử dụng để cập nhập firmware trên thiết bị nhưng với bộ tái khởi động , là phiên bản rút gọn của FTP, không có quy định về bảo mật , nó truyền theo khối từ 512 byte đến max là 4GB

![ảnh minh hoạ](https://imgur.com/anJa22T.png)
### **4.Một Số Giao Thức ở Các Tầng Dưới**
- **Tầng Transport**: hai giao thức nổi tiếng ở tầng này đó chính là TCP và UDP
  - Một số ứng dụng yêu cầu phân phối gói tin đáng tin cậy . Chính giao thức TCP sẽ cung cấp khả năng này, nó sử dụng cơ chế như là bắt tay ba bước,điều khiển luồng,báo nhận để truyền gói tin với độ tin cậy cao và có chế phục hồi truyền lại khi gói tin lỗi
  - Một số ứng dụng khác lại yêu cầu tốc độ truyền nhanh và không quan tâm tới việc gói tin của mình có được bên nhận tiếp nhận hay không thì đã có giao thức UDP để cung cấp tính năng này , UDP sử dụng kiểu truyền tổng lực không tin cậy lên khi truyền nó không cần biết bên nhận có nhận được tin hay không và trong trường hợp tin bị mất hay lỗi cũng sẽ không có cơ chế phục hồi hay là truyền lại gói tin
![ảnh minh hoạ](https://imgur.com/YsX5Hm2.png)
  - Như trong ảnh chúng ta có thể thấy là giao thức TCP cung cấp kiểu kết nối Unicast(kết nối điểm điểm), còn UDP hộ trợ cả ba kiểu kết nối Unicast,Multicast,Broadcast(kết nối điểm điểm điểm, điểm nhiều điểm, quảng báo)
- **Giao Thức RARP(Reverse Address Resolution Protocol)**: phần giải địa chỉ MAC(địa chỉ vật lý) thành địa chỉ IP(địa chỉ logic). RARP đòi hỏi một hoặc nhiều máy chủ lưu trữ để duy trì một cơ sở dữ liệu bản đồ của địa chỉ lớp liên kết đến các địa chỉ giao thức tương ứng. Media Access Control (MAC) địa chỉ cần thiết để được cấu hình riêng trên các máy chủ của quản trị viên. RARP được giới hạn chỉ phục vụ các địa chỉ IP.

![ảnh minh hoạ](https://imgur.com/tuYkMqG.png)
- **Mô Tả QT Bắt Tay Ba Bước**
![ảnh minh hoạ](https://imgur.com/DwLkXbc.png)
![ảnh minh hoạ](https://imgur.com/ulfPnYa.png)
- **Cơ chế điều khiển luồng(Flow Control)
![ảnh minh hoạ](https://imgur.com/QFkFoO4.png)
- Trên đây là một số tìm hiểu sơ bộ về mô hình TCP/IP cũng như các giao thức hoạt động tại các tầng 
-[link tham khảo 1 ](https://cuongquach.com/tu-hoc-ccna-tim-hieu-giao-thuc-tcp-udp.html)
-[link tham khảo 2 ](https://microchipdeveloper.com/tcpip:tcp-ip-application-layer-layer-5)
-[link tham khảo 2 ](https://vi.wikipedia.org/wiki/TCP/IP)


