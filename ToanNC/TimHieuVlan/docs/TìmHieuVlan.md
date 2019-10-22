# **VLAN(Virtual Local Area Network)**
## **Mục lục**
- **1.VLAN là gì, sự cần thiết của VLAN**
- **2.Phân loại VLAN**
- **3.Cổng truy nhập (access) và trung kế (trunk) trên Switch** 
### **1.VLAN là gì, sự cần thiết của VLAN**
- Đầu tiên để hiểu về VLAN là gì chúng ta cần biết vậy LAN là gì . **LAN(Local area network)** là một mạng cục bộ được định nghãi là tát cả các máy tính có trong cùng một mình quảng bá (Broadcast Domain)
- Chúng ta cũng cần nhớ và lưu ý một điều rằng đối với các *Router* nó sẽ chặn bản tin quảng bá còn đối vs các *Switch* thì nó sẽ chuyển tiếp chúng đi
- Như vậy, **VLAN(Virtual Local Area Network)** nó là một mạng LAN ảo. Về mặt kỹ thuật chúng ta có thể hiểu VLAN là một miền quảng bá được tạo bởi các Switch,bình thường thì router sẽ có vai trò tạo ra miền quảng bá còn đối với VLAN thì switch có thể tạo ra miền quảng bá. Việc này được thực hiện khi quản trị viên đặt một số cổng của Switch trong VLAN ngoại trừ VLAN 1(VLAN mặc định), khi đó các cổng trong một mạng VLAN đơn đều thuộc một miền quảng bá duy nhất

![ảnh minh hoạ](https://imgur.com/p2syXzg.png)
- Bởi vì các Switch có thể giao tiếp với nhau nên một số cổng trên Switch A có thể nằm trong vùng VLAN10 và một số cổng trên Switch B cũng có thể nằm trong VLAN10 . Các bạn tin quảng bá giữa những máy tính này sẽ không bị lộ trên bất cứ các cổng thuộc bất cứ VLAN nào ngoài VLAN10.Tuy vậy không có nghĩa là các máy tính không thể giao tiếp với nhau khi khác VLAN ,muốn giao tiếp được với các VLAN khác thì chúng ta tiến hành cấu hình bổ sung để có thể giao tiếp được với các VLAN ngoài

![ảnh minh hoạ](https://imgur.com/s7RoUWo.png)
-Ví Dụ như hình trên khi mà một máy tính ở phòng Engineering tầng 2 muốn kết nối với máy ở tầng một nó cần gửi một gói tin ARP Broadcast để xin địa chỉ IP hay là MAC của máy ở tầng một nhưng do là gói Broadcast lên lúc này nếu trong một mạng lên thì nó sẽ gửi đến tất cả các máy làm cho việc tiêu tốn đường truyền và có thể có nguy cơ đến bảo mật ,trong trường hợp gói có mã độc sẽ gây ảnh hưởng tới toàn bộ các máy . Như vây, khi ta chi thành các vùng VLAN khác nhau thì lúc này các máy sẽ giảm tải việc truyền thông trong mạng cũng như tăng tính bảo mật khi các máy bị giới hạn ở trong vùng VLAN của mình trừ khi được cấu hình để kết nối ra ngoài
- Lúc này chúng ta lại đặt ra câu hỏi vậy khi nào cần tới VLAN:
  - Chúng ta có thể dùng VLAN trong các trường hợp sau đây
    - Bạn có hơn 200 máy tính trong mạng LAN
    - Lưu lượng quảng bá (broadcast traffic) trong mạng LAN của bạn quá lớn
    - Các nhóm làm việc cần gia tăng bảo mật hoặc bị làm chậm vì quá nhiều bản tin quảng bá.
    - Các nhóm làm việc cần nằm trên cùng một miền quảng bá vì họ đang dùng chung các ứng dụng. Ví dụ như một công ty sử dụng điện thoại VoIP. Một số người muốn sử dụng điện thoại có thể thuộc một mạng VLAN khác, không cùng với người dùng thường xuyên.
    - Hoặc chỉ để chuyển đổi một switch đơn thành nhiều switch ảo.
- Nhưng chúng ta lại cũng đặt ra thêm một câu hỏi vậy tại sao chúng ta không dùng cách chia subnet thay vì việc dùng VLAN???
  - Bởi vì là mỗi VLAN nên ở subnet riêng của mình. VLAN có ưu điểm hơn subnet ở chỗ các máy tính tại những vị trí vật lý khác nhau (không quay lại cùng một router) có thẻ nằm trong cung một mạng. Hạn chế của việc chia subnet với một router đó là ttats cả máy tính trên subnet đó phải được kết nối tới cùng một switch và switch đo phải được kết nối tới một cổng trên router , còn đối VLAN một máy tính có thể được kết nối tới switch này trong khi máy tính kahcs có thể kết nối tới switch kia mà tất cả các máy tính vẫn nằm trên VLAN chung(cùng miên quảng bá)

![ảnh minh hoạ](https://imgur.com/QaBzdLU.png)
- khi chia VLAN
![ảnh minh hoạ](https://imgur.com/daLy61J.png)
- khi chia subnet
- Từ đó chúng ta có thể thấy rằng VLAN giúp tăng hiệu suất mạng LAN cỡ trung bình và lớn vì nó hạn chế bản tin quảng bá. Khi số lượng máy tính và lưu lượng truyền tải tăng cao, số lượng gói tin quảng bá cũng gia tăng . Bằng cách sử dụng VLAN,bạn sẽ hạn chế được bản tin quảng bá , đồng thời cũng tăng tính bảo mật vì các máy tính trong cùng một nhóm máy chỉ được giao tiếp với nhau nếu muốn giao tiếp ra ngoài chúng ta có thể cấu hình cho thêm 
### **2.Phân loại VLAN**
- Vậy với những lợi ích trên chúng ta có thể chia VLAN thành những loại nào 
  - **Default VLAN**: Là kiểu VLAN mặc định ban đầu với tất cả các cổng giao tiếp trên thiết bị chuyển mạch, vì vậy Default VLAN cũng có thể hiểu là VLAN 1, và các VLAN khác như User VLAN, Native VLAN, Management VLAN đều là các thành phần con của Default VLAN.
  - **User VLAN (hay Data VLAN)**: Là VLAN trong đó chứa các tài khoản người dùng thành từng nhóm dựa theo các thuộc tính về đặc thù công việc của từng nhóm làm việc hay theo thuộc tính về vị trí vật lý của các nhóm làm việc này.

![ảnh minh hoạ](https://imgur.com/JAlWJwC.png)  
  - **Native VLAN**: Là VLAN dùng để cấu hình Trunking do một số thiết bị không tương thích với nhau, lúc này ta phải sử dụng Native VLAN để chúng có thể giao tiếp với nhau. Khi đó, tất cả các khung dữ liệu (frame) của các VLAN khi giao tiếp qua kết nối Trunking đều sẽ được gắn tag của giao thức 802.1Q hoặc ISL, ngoại trừ các frame của VLAN 1. Native VLAN là VLAN mà frame của nó sẽ không được tag trước khi gửi qua đường trunk. Ngầm định Native VLAN của Switch là VLAN 1

![ảnh minh hoạ](https://imgur.com/bDeAqXT.png)
![ảnh minh hoạ](https://imgur.com/2JxluGl.png)
  - **Management VLAN**: Để có thể giám sát từ xa các thiết bị chuyển mạch trong hệ thống mạng của mình, bạn cần phải có một VLAN đặc biệt dùng để thực hiện việc này, đó chính là Management VLAN. Bằng cách gán một địa chỉ IP dùng để telnet từ xa vào hệ thống mạng thông qua địa chỉ IP này, và có thể cấm các người dùng khác truy cập vào thiết bị. Vì đây là một VLAN khá nhạy cảm được cấp một số quyền quản trị nên nó cần phải được tách riêng ra khỏi các VLAN khác để đảm bảo yếu tố an toàn bảo mật. Khi mạng có vấn đề như: hội tụ với STP, broadcast storms thì một Management VLAN cho phép nhà quản trị vẫn có thể truy cập được vào thiết bị và giải quyết vấn đề đó.
  - **Voice VLAN** Voice VLAN là VLAN dành cho lưu lượng thoại. Nó cho phép các cổng Switch mang lưu lượng thoại IP từ một điện thoại IP. Người quản trị mạng cấu hình một Voice VLAN và gán nó để truy cập các cổng. Khi một điện thoại IP được kết nối với các cổng Switch, Switch sẽ gửi gói tin CDP đó hướng dẫn các điện thoại IP đính kèm để gửi lưu lượng thoại được gán nhãn VLAN ID.

![ảnh minh hoạ](https://imgur.com/ohO2GMV.png)
- Sự khác nhau của **Default VLAN** và **Native VLAN**
![ảnh minh hoạ](https://imgur.com/nxkLgCT.png)
### **3.Cổng truy nhập (access) và trung kế (trunk) trên Switch** 
![ảnh minh hoạ](https://imgur.com/m3rnGOZ.png)
- Cổng truy nhập
  - Một cổng trên Switch sẽ hoạt động trong chế độ cổng truy nhập (Access link) hoặc cổng trung kế (Trunk link).
  - Trong chế độ cổng truy nhập, cổng chỉ thuộc một VLAN. Tất cả các máy tính cắm vào cổng mày đều thuộc VLAN đó.
  - Frame được gửi trên cổng truy nhập sẽ tuân theo chuẩn định dạng khung ethernet (802.3).
  - Cổng truy nhập thường dùng khi cổng được kết nối đến máy trạm. Cấu hình cổng truy nhập:
- Cổng trung kế
  - Cổng trung kế (Trunk link) là một kết nối vật lý và logic để hỗ trợ các VLAN trên các Switch liên kết với nhau.
  - Cổng trung kế cho phép frame của nhiều VLAN có thể truyền trên đó. Một cổng trung kế không được gán cho một VLAN riêng biệt.
  - Cổng trung kế thường được dùng để kết nối giữa các Switch hoặc giữa Switch và Router.
  - Chính vì vậy cổng trung kế thường là cổng có băng thông lớn
  - Các VLAN được ghép kênh qua cổng trung kế. Để ghép kênh lưu lượng của các VLAN, một giao thức đặc biệt sẽ được sử dụng để đóng gói frame để thiết bị có thể xác định được nó thuộc VLAN nào. Chuẩn frame được sử dụng đó là 802.1Q hoặc ISL.
  - Nhờ cổng trung kế mà một VLAN có thể được mở rộng ra toàn mạng.
  - Chỉ cần một đường vật lý cho cả hai VLAN giữa hai Switch.
- **Giao thức 802.1Q trong cổng trung kế**
  - 802.1Q là một giao thức cho phép một liên kết vật lý có thể thực hiện mang lưu lượng của nhiều VLAN. Đây là tiêu chuẩn VLAN trunking protocol của IEEE. Thay vì đóng gói các frame lớp 2 ban đầu, 802.1Q chèn một thẻ vào header Ethernet, sau đó tính toán lại và cập nhật các FCS trong frame nguồn và truyền qua liên kết trunk.

![ảnh minh hoạ](https://imgur.com/7Q0V38u.png)
  - IEEE 802.1Q là một chuẩn chung dùng để nhận dạng các VLAN được truyền qua đường trung kế, nó hoạt động trong môi trường Ethernet và là một chuẩn mở. Là giao thức dùng gán nhãn frame khi truyền frame trên đường trung kế giữa hai Switch hay giữa Switch và Router, việc gán nhãn frame được thực hiện bằng cách thêm thông tin VLAN ID vào phần giữa header trước khi frame được truyền lên đường trung kế.
  - Để xác định một frame với một VLAN nhất định, giao thức 802.1Q được thêm vào như một tag hoặc một trường vào frame dữ liệu Ethernet. Các thành phần của tag này bao gồm: Ethertype (0x8100), PRI, VLAN ID. Bởi vì tag chèn vào frame sẽ làm thay đổi frame ban đầu, Switch phải tính toán lại và thay đổi giá trị FCS cho frame ban đầu trước khi gửi qua cổng trung kế 802.1Q. Ngược lại ISL không sửa đổi frame ban đầu.
![ảnh minh hoạ](https://imgur.com/ovYP0Ap.png)
  - Trường 802.1Q có các thành phần sau đây:
    - EtherType: sử dụng EtherType 0x8100 để cho biết đây là một khung 802.1Q.
    - PRI: 3 bit, mang thông tin ưu tiên cho frame.
    - Token Ring Encapsulation Flag: chỉ ra giải thích của frame nếu nó được truyền từ Ethernet tới Token Ring.
    - VLAN ID: 12 bit, dùng để xác định frame là của VLAN nào.
- **Giao thức Inter-Switch Link trong cổng trung kế(ISL)**
  - Inter-Switch Link (ISL) là giao thức đóng gói frame độc quyền của Cisco lựa chọn cho cấu hình trung kế Lớp 2. Nó được dùng chính trong môi trường Ethernet, chỉ hỗ trợ trên các Router và Switch của Cisco.
![](https://imgur.com/2NsgzOI.png)  
  - Sau đây là một số tính năng của ISL:
     - Hỗ trợ nhiều giao thức Lớp 2 (Ethernet, Token Ring, FDDI và ATM).
     - Hỗ trợ PVST. Không sử dụng Native VLAN, do đó nó không đóng gói tất cả các frame. Khi một cổng Switch được cấu hình là một cổng trung kế ISL, toàn bộ frame nguồn, bao gồm header và trailer, được đóng gói trước khi đi qua cổng trung kế. Đóng gói bổ sung một header ở phía trước và một trailer ở phần cuối của các frame nguồn. ISL header có các VLAN ID của VLAN của frame nguồn.
![](https://imgur.com/54v2PU4.png)
- ISL Header Header của ISL có chứa nhiều trường với các giá trị xác định thuộc tính của dữ liệu frame nguồn. Thông tin này được sử dụng để giao nhận, nhận dạng đường truyền, và nhận dạng VLAN. Độ lớn của các trường trong header ISL khác nhau, tùy thuộc vào loại VLAN và loại đường liên kết. Các ASIC trên một cổng Ethernet đóng gói các frame với một header ISL 26 byte và một FCS 4 byte. Đây là 30-byte mà ISL đóng gói bổ sung thêm đã được hỗ trợ trong giao thức của Switch Cisco, nhưng kích thước tổng thể của frame thay đổi và được giới hạn bởi các MTU của giao thức lớp 2. Các frame Ethernet ISL header có chứa các trường thông tin sau:
  - DA (Destination address): 40-bit địa chỉ đích.
  - Type: 4 bit mô tả của các loại frame: Ethernet (0000), Token Ring (0001), FDDI (0010) và ATM (0011).
  - User: 4 bit để xác định các ưu tiên Ethernet.
  - SA (Source address): 48 bit địa chỉ MAC nguồn của cổng truyền trên Switch.
  - LEN (Length): 16 bit mô tả độ dài khung khi trừ DA, Type, người sử dụng, SA, LEN, và CRC. • AAAA03: 24 bit, đây là một hằng số.
  - HSA (High bits of source address): 3 byte đầu tiên của SA (ID của nhà sản xuất).
  - VID: 15 bit, nhưng chỉ có 10 bit được sử dụng cho 1024 VLAN. Dùng để phân biệt các frame của các VLAN.
  - BPDU (Bridge Protocol Data Unit): 1 bit xác định liệu mô tả frame là một spanning tree BPDU. Nó cũng xác định nếu khung đóng gói là một Cisco Discovery Protocol (CDP) hoặc VLAN Trunk Protocol (VTP) frame.
  - INDX (index): 16 bit để cho biết chỉ số port nguồn của gói tin mà nó đi ra khỏi Switch. Giá trị 16 bit này được bỏ qua trong các gói tin nhận.
  - RES: 16 bit dành riêng cho Token Ring và FDDI frame.
  - Encapsulated Ethernet Frame: gói dữ liệu được đóng gói, bao gồm cả giá trị CRC của riêng nó, hoàn toàn chưa sửa đổi. Frame bên trong phải có một giá trị CRC hợp lệ khi các trường ISL đóng gói bị loại bỏ. Một switch có thể nhận được các trường ISL và sử dụng trường ENCAP FRAME như là frame nhận.




