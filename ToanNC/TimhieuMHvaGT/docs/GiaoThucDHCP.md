# **Tìm Hiểu Giao Thức DHCP**
## **Mục Lục**
- **1.Khái Niệm**
- **2.Cơ Chế Hoạt Động**
- **3.Cấu Trúc Bản Tin DHCP**
- **4.Phân Tích Bản Tin DHCP bằng Wireshark**
### **1.Khái Niệm**
- DHCP (Dynamic Host Configuration Protocol) là giao thức cấu hình host động. Nó cung cấp cho máy tính địa chỉ ip ; subnet mask; default gateway. Và nó thường được cấp phát bởi DHPC server được tích hợp sẵn trên router.
- DHCP giao tiếp bằng UDP và sử dụng port 67 và 68. DHCP server sử dụng port 67 để nghe thông tin từ các client và sử dụng port 68 để reply thông tin
- Ưu điểm khi sử dụng DHCP
  - Tập trung quản trị thông tin cấu hình host
  - Cấu hình động các máy
  - Cấu hình IP cho các máy một cách liền mạch.
  - Sự linh hoạt
  - Đơn giản hóa vai trò quản trị của việc cấu hình địa chỉ IP của client.
- DHCP làm việc theo mô hình client server và thành phần chính của DHCP là:
  - DHCP client: Là thiết bị dùng để kết nối vào mạng
  - DHCP server: Là thiết bị dùng để cấp phát địa chỉ cho client
![ảnh minh hoạ](https://imgur.com/lJwg7ld.png)
### **2.Cơ Chế Hoạt Động**
- Trước tiên chúng ta cùng tìm hiểu về một số loại bản tin mà giao thức DHCP sẽ sử dụng :
  - **DHCP DISCOVER**: Ban đầu, một máy tính DHCP Client muốn gia nhập mạng, nó yêu cầu thông tin địa chỉ IP từ DHCP Server bằng cách gửi broadcast một gói DHCP Discover. Địa chỉ IP nguồn trong gói là 0.0.0.0 bởi vì client chưa có địa chỉ IP.
  - **DHCP OFFER**: Mỗi DHCP server nhận được gói DHCP Discover từ client đáp ứng với gói DHCP Offer chứa địa chỉ IP cho thuê và thông tin định cấu hình TCP/IP bổ sung(thêm vào), chẳng hạn như subnet mask và gateway mặc định. Nhiều hơn một DHCP server có thể đáp ứng với gói DHCP Offer. Client sẽ chấp nhận gói DHCP Offer đầu tiên nó nhận được.
  - **DHCP REQUEST**: Khi DHCP client nhận được một gói DHCP Offer, nó đáp ứng lại bằng việc broadcast gói DHCP Request mà chứa yêu cầu địa chỉ IP mà server cung cấp trong bản tin offer - thể hiện sự chấp nhận của địa chỉ IP được yêu cầu từ một server xác định.
  - **DHCP ACK**: DHCP server được chọn lựa chấp nhận DHCP Request từ Client cho địa chỉ IP bởi việc gửi một gói DHCP Acknowledge (ACK). Tại thời điểm này, Server cũng định hướng bất cứ các tham số định cấu hình tuỳ chọn. Sự chấp nhận trên của DHCP Acknowledge, Client có thể tham gia trên mạng TCP/IP và hoàn thành hệ thống khởi động. (Bản tin này gần như giống nội dung bản tin OFFER)

![ảnh minh hoạ](https://imgur.com/PkgOGqx.png)
- Ngoài 4 bản tin cơ bản trên chúng ta cũng có một số bản tin khác nữa :
  - **DHCP NAK**: Nếu địa chỉ IP không thể được sữ dụng bởi client bởi vì nó không còn giá trị nữa hoặc được sử dụng hiện tại bởi một máy tính khác, DHCP Server đáp ứng với gói DHCP Nak, và Client phải bắt đầu tiến trình thuê bao lại. Bất cứ khi nào DHCP Server nhận được yêu cầu từ một địa chỉ IP mà không có giá trị theo các Scope mà nó được định cấu hình với, nó gửi thông điệp DHCP Nak đối với Client.
  - **DHCP DECLINE**: Khi client nhận được thông tin cấu hình từ DHCP server, nhưng có thể xảy ra ván đề là IP mà DHCP setver cung cấp đã bị sử dụng bởi một thiết bị khác thì nó gửi gói DHCP Decline đến các server và client phải bắt đầu tiến trình thuê lại từ đầu
  - **DHCP RELEASE**: Một DHCP không còn như cầu sử dụng IP hiện tại nữa nó sẽ gửi một gói DHCP Release đến server quản lý để giải phóng địa chỉ IP và xoá bất cứ hợp đồng đang thuê nào tồn tại
  - **DHCP INFORM**: Các thiết bị không sử dụng DHCP để lấy địa chỉ IP vẫn có thể sử dụng khả năng cấu hình khác của nó . Một client có thể gửi bản tin DHCP Inform để yêu cầu máy chủ có sẵn nào gửi cho thông số để mạng hoạt động. DHCP server đáp ứng với các thông số yêu cầu được điền tọng phần tuỳ chọn của DHCP trong bản tin DHCP ACK
![ảnh minh hoạ](https://imgur.com/5PJGEsx.png)
- *Chúng ta cùng tìm hiểu cụ thể về cơ chế hoạt động xin cấp phát địa chỉ IP*
  - Bước 1: **Client tạo bản tin DHCPDISCOVER**. Ban đầu, Client chưa có địa chỉ IP và nó có thể biết hoặc không biết vị trí của DHCP server trong mạng. Để tìm DHCP server, nó tạo bản tin DHCP DISCOVER, bao gồm các thông tin như sau:
     - Điền địa chỉ MAC vào trường CHAddr để xác nhận nó.
     - Sinh ra một số định danh transaction ngẫu nhiên và điền vào trường XID.
     - Client có thể yêu cầu một địa chỉ IP xác định sử dụng trường tùy chọn Request IP Address trong phần DHCP option.
  - Bước 2: **Client gửi bản tin DHCP DISCOVER**. Client gửi broadcast bản tin DHCP DISCOVER trên mạng nội bộ
  - Bước 3: **Server nhận và xử lý bản tin DHCP DISCOVER**.Mỗi DHCP server trên mạng LAN nhận được bản tin DHCP DISCOVER của client và kiểm tra nó. Server tìm kiếm phần địa chỉ MAC của client trong database và chọn cho nó một IP phù hợp đồng thời các thông số liên quan. Nếu client yêu cầu một IP xác định thì server sẽ xử lý yêu cầu nó. Server có thể quyết định việc nó dùng địa chỉ IP chỉ định kia là hợp lệ hay không để gửi reply về
  - Bước 4: **Server tạo bản tin DHCP OFFER**.Mỗi server được chọn trả lời lại cho client tạo bản tin DHCP OFFER bao gồm các thông tin sau:
     - Địa chỉ IP cấp phát cho client trong trường YIAddr. Nếu trước đó, client đã "thuê" một địa chỉ IP và thời hạn dùng của nó vẫn còn thì sẽ sử dụng địa chỉ cũ đó cho client. Nếu không thì nó sẽ chọn một IP có sẵn bất kì cho client.
     - Thời hạn được sử dụng IP.
     - Các thông số cấu hình khác mà client yêu cầu.  
     - Định danh của DHCP server trong phần tùy chọn DHCP Server Identifier option.
     - Cùng số XID được sử dụng trong bản tin DHCP DISCOVER.
  - Bước 5: **Server dò tìm xem địa chỉ IP mà cấp phát cho client đã được một thiết bị nào khác sử dụng hay chưa**.Trước khi gửi bản tin DHCP OFFER cho client, server nên kiểm tra lại xem địa chỉ IP cấp cho client đã được sử dụng hay chưa bằng cách gửi bản tin ICMP.Nếu IP đó đã được sử dụng thì nó sẽ chọn lại địa chỉ IP khác cho client.Nếu IP chưa được sử dụng, server sẽ cấp phát IP cho client.
  - Bước 6: **Các Server gửi bản tin DHCPOFFER**.Mỗi server gửi bản tin DHCP OFFER của nó. Chúng có thể được gửi unicast hoặc broadcast tùy thuộc vào client (Nếu client cho phép nhận bản tin unicast khi chưa được cấu hình IP thì nó sẽ set bit B trong bản tin DHCP DISCOVER là 0, còn nếu không thì nó sẽ set bit B là 1 để biểu thị nhận bản tin broadcast)
  - Bước 7: **Client nhận và xử lý bản tin DHCPOFFER**.Client nhận bản tin DHCP OFFER và nó sẽ chọn lựa server nào mà nó nhận được bản tin DHCP OFFER đầu tiên. Nếu không nhận được bản tin DHCP OFFER nào sau một thời gian, client sẽ tạo lại bản tin DHCP DISCOVER và gửi lại từ đầu.
  - Bước 8: **Client tạo bản tin DHCP REQUEST**.Client tạo bản tin DHCP REQUEST cho server mà nó chọn nhận bản tin OFFER. Bản tin này sẽ gồm 2 mục đích chính là nói với server mà cho phép cấp phát IP cho nó là nó đồng ý dùng IP đó trong trường hợp IP đó vẫn còn dành cho nó và cũng thông báo với các DHCP server còn lại là bản tin OFFER của chúng không được nhận.
     - Trong bản tin này bao gồm các thông tin:
        - Định danh của server được chọn trong phần SEerver Identifier option.
        - Địa chỉ IP mà DHCP server cho phép client trong bản tin DHCP OFFER, client để vào phần Request IP Address DHCP option.
        - Và một số thông tin cấu hình mà nó muốn trong phần Parameter Request List option.
  - Bước 9: **Client gửi bản tin DHCP REQUEST**.Client gửi broadcast bản tin DHCP REQUEST. Sau đó chờ reply từ server.
  - Bước 10: **Các server nhận và xử lý bản tin DHCP REQUEST**.Mỗi server nhận được bản tin REQUEST của client. Các server không được chọn sẽ bỏ qua bản tin này.
  - Bước 11: **Server gửi bản tin DHCPACK hoặc DHCPNAK**.Server được chọn sẽ kiểm tra xem địa chỉ IP nó OFFER cho còn sử dụng được hay không. Nếu không còn, nó sẽ gửi lại DHCPNAK (negative acknowledgment). Thông thường, server sẽ vẫn dành địa chỉ IP đó cho client, server sẽ gửi lại bản tin DHCPACK để xác nhận và cấp các thông số mà client yêu cầu.
  - Bước 12: **Client nhận bản tin DHCPACK hoặc DHCPACK**.Client sẽ nhận lại bản tin DHCPACK hoặc DHCPNAK từ server.
     - Nếu là DHCPNAK, client sẽ bắt đầu gửi lại DISCOVER từ bước 1.
     - Nếu là DHCPACK, client đọc địa chỉ IP trong trường YIAddr, ghi lại các thông số khác trong phần DHCP option.
     - Nếu không nhận được bản tin nào, client sẽ gửi lại DHCP REQUEST một hoặc vài lần nữa. Sau một khoảng thời gian vẫn không nhận được gì, nó sẽ bắt đầu lại từ Bước 1.
  - Bước 13: **Client kiểm tra xem IP được sử dụng hay chưa**.Client sẽ kiểm tra lần cuối trước khi xác định chắc chắn IP chưa được thiết bị khác sử dụng trước khi sử dụng nó. Bước này sẽ được thực hiện bởi giao thức ARP trên mạng LAN.Nếu có bất kì thiết bị nào phản hồi lại ARP, client sẽ gửi bản tin DHCP DECLINE lại server để thông báo với server rằng IP đó đã được máy khác sử dụng. Và client trở lại Bước 1.Nếu không có phản hồi, client sẽ sử dụng IP. Kết thúc quá trình Lease Allocation.

![ảnh minh hoạ](https://imgur.com/2QLCFdQ.png)
### **3.Cấu Trúc Bản Tin DHCP**
- DHCP là giao thức được cải tiến từ giao thức BOOTP nên cấu trúc gói tin cũng tương tự như bản tin của BOOTP, nhưng phần dành cho nhà sản xuất của BOOTP được thay thế bằng tùy chọn của DHCP.
- Một client tạo ra một bản tin sử dựa trên chuẩn định dạng của DHCP, cũng gần giống nhau BOOTP. Khi server reply lại client thì nó không hoàn toàn tạo ra bản tin mới mà chỉ đơn giản là copy lại bản tin request và thay đổi một số field và gửi lại cho client. Một mã đặc biệt là transaction identifier (XID) được thay thế được đặt trong request và duy trì trong reply, cái mà cho phép client biết reply đi với một request xác định.

![ảnh minh hoạ](https://imgur.com/JUPtZOq.png)
![ảnh minh hoạ](https://imgur.com/3W2yqdT.png)
![ảnh minh hoạ](https://imgur.com/VcVYQ8v.png)
![ảnh minh hoạ](https://imgur.com/r2V4ojN.png)
- Một số trường **Option**:
  - Option 54: chỉ đính danh DHCP server
  - Option 51: thời gian cho thuê địa chỉ IP
  - Option 1: địa chỉ subnet Mask
  - Option 28 : địa chỉ broadcast
  - Option 3 : địa chỉ default gateway
  - Option 6 : địa chỉ DNS
  - Option 53: Kiểu tin nhắn
  - Option 55: Danh sách tham số yêu cầu
  - Option 50: Địa chỉ IP yêu cầu
### **4.Phân Tích Bản Tin DHCP bằng Wireshark**
- Để có thể bắt được gói tin chúng ta cần phải cài đặt Wireshark
- [link tải wireshark](https://www.wireshark.org/download.html)
- Sau đó chúng ta có thể Release đị chỉ IP đang sử dụng bằng hai cách :
  - Cách 1:Tắt card mạng đang dùng r bật lại 
  - Cách 2: Dùng cửa sổ CMD: 
![ảnh minh hoạ](https://imgur.com/lY6XWpV.png)
![ảnh minh hoạ](https://imgur.com/HbIoYa9.png)
     - Tham số **/release** sau lệnh ipconfig sẽ xóa địa chỉ IP hiện tại. Sau khi thực thi xong lệnh **ipconfig/release**, nhập tiếp lệnh **ipconfig/renew** để lấy địa chỉ IP mới từ máy chủ DHCP.
     - Để lấy địa chỉ IP mới, chỉ cần nhập lệnh **ipconfig /renew**. Tham số /renew sau lệnh ipconfig yêu cầu địa chỉ IP mới từ máy chỉ DHCP.

![ảnh minh hoạ](https://imgur.com/amMdAhl.png)
- Vậy sau khi xoá IP và yêu cầu lại IP mới quá trình diễn ra tại máy tính của bạn sẽ ra sao ?? .Cùng mình tìm hiểu nhé chúng ta sẽ cần dùng Wireshark để hỗ trợ ở đây
- Đây là sau khi dùng Wireshaks để bắt gói tin
![ảnh minh hoạ](https://imgur.com/CtUMnlw.png)
  - Chúng ta có thể thấy các bản tin của giao thức trong quá trình xin cấp IP bây giờ cùng xem chi tiết từng gói nha
  - **Bản Tin DHCP DISCOVER**:
![ảnh minh hoạ](https://imgur.com/40ac3SM.png)
    - tại đây mọi người có thể thấy được địa chỉ IP nguồn,IP đích,các tham số của địa chỉ IPv4, Port nguồn, Port đích,Địa chỉ MAC
![ảnh minh hoạ](https://imgur.com/Je1gIPy.png)
    - ảnh này cho mọi người biết về các tường Option của bản tin , và một vài chỉ số quan trọng của giao thức DHCP được gạch đỏ
  - **Bản Tin DHCP OFFER**:
![ảnh minh hoạ](https://imgur.com/uaGPk24.png)
    - bản tin này gửi về cho biết địa chỉ IP được cấp cho máy là 172.16.79.203, đồng thời là cả các thông tin về subnet , gateway  được thể hiện tại các trường Option
  - **Bản Tin DHCP REQUEST**:
![ảnh minh hoạ](https://imgur.com/PAcsaL7.png)
![ảnh minh hoạ](https://imgur.com/MbJfex1.png)
    - bản tin này mục đích máy khách muốn xác nhận với server để chắc chắn là chưa có địa chỉ IP này đang hoạt động trên mạng 
  - **Bản Tin DHCP ACK**:
![ảnh minh hoạ](https://imgur.com/ppkswyJ.png)
![ảnh minh hoạ](https://imgur.com/CkHCVmJ.png)




