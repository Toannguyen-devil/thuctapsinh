# **Tìm Hiểu Về Địa Chỉ IPv4 và IPv6**
## **Mục Lục**
- **1.IPv4**
- **2.IPv6**
- **3.So sánh IPv4 và IPv6**

### **1.IPv4**
- **IPv4( Internet Protocol version 4)**: là phiên bản thứ 4 thông quá trình phát triển của giao thức Internet(IP). Đây là phiên bản đầu tiên của IP được sử dụng rộng rãi .IPv4 cùng với IPv6 là nòng cốt của giao tiếp Internet. Hiện tại, IPv4 vẫn là giao thức được triển khai rộng rãi nhất trong bộ giao thwucs của lớp Internet
- Giao thức này được công bố bởi IETF trong phiên bản RFC791( tháng 9 năm 1981), thay thế cho phiên bản RFC 760(công bố vào tháng giêng năm 1980). Giao thức này được chuẩn hoá bởi bộ quốc phòng mỹ trong phiên bản MIL-STD-1777
- IPv4 là giao thức hướng dữ liệu, được sử dụng cho hệ thống chuyển mạch gói(tương tự như chuẩn mà Ethernet). Đây là giao thức truyền dữ liệu hoạt động dựa trên nguyên tắc tốt nhất có thể, trong đó nó không quan tâm thứu tự truyền gói tin cũng như không đảm bảo gói tin sẽ đến đích hay việc gây ra tình trạng lặp gói tin ở đích đến . Việc xử lý vấn đề này dành cho lớp trên của chồng giao thức TCP/IP, tuy nhiên , IPv4 có cơ chế đảm bảo tính toàn vẹn dữ liệu thông qua sử dụng gói kiểm tra
- IPv4 sử dụng 32 bit để đánh địa chỉ và được chia là 4 octet( mỗi octet có 8 bit tương đương với 1 byte), mỗi octet được cách nhau bằng dấu chấm
  - VD: địa chỉ 172.16.254.1

![ảnh minh hoạ](https://imgur.com/9CXWTWC.png)
- Một địa chỉ IPv4 được chia thành hai phần chính đó là địa chỉ mạng (Network ID) và địa chỉ máy (Host ID)

![ảnh minh hoạ](https://imgur.com/OPDsrPK.png)

- Địa chỉ IPv4 có các loại sau : địa chỉ Unicast,Broadcast,Mutlicast mỗi loại địa chỉ cho phép thiết bị gửi dữ liệu đến các dạng nơi nhận đã được cho phép trước
  - Địa chỉ *Unicast* : là một tên thay thế cho kiểu địa chỉ điểm-điểm đã được sử dụng trong IPv4 . Loại địa chỉ này chỉ được sử dụng để định danh cho một giao diện trên mạng . Một gói dữ liệu có địa chỉ đích dạng địa chỉ Unicast sẽ được chuyển tới giao diện định danh bởi địa chỉ đó. Địa chỉ Unicast được chia thành các nhóm sau:
    - Địa chỉ **Global Unicast**: được sử dụng để định danh các giao diện , cho phép thực hiện kết nối các host tron mạng Internet IPv6 toàn cầu . Tính chất loại địa chỉ này cũng giống như địa chỉ Ipv4 định danh cho một host trong mạng Internet
      - Cấu trúc loại địa chỉ này được xây dựng theo kiến trúc phân cấp rõ rằng. Cụ thể như sau:
        - + 48 bits Public Topology
        - + 16 bits Site Topology
        - + 64 bits định danh giao diện

![ảnh minh hoạ](https://imgur.com/XcwLdED.png)
        - Trong đó:
           - + 001: Định dạng tiền tố đối với loại địa chỉ Global Unicast
           - + TLA ID: Định danh cho nhà cung cấp cao nhất trong hệ thống các nhà cung cấp dịch vụ (Top Level Aggregation)
           - + RES: Chưa sử dụng
           - + NLA ID: Định danh của nhà cung cấp tiếp theo trong hệ thống các nhà cung cấp dịch vụ (Next Level Aggregation)
           - + SLA ID: Định danh các Site của các khách hàng cuối
           - + Interface ID: Định danh của giao tiếp của các host trên mạng trong site của khách hàng cuối; Định danh này xác định theo chuẩn EUI-64.

    - Địa chỉ **Site-local**: được sử dụng để định dạng các giao diện, cho phép thực hiện các kết nốt giữa các host trong mạng local.Các router sẽ chuyển các gói tin sử dụng loại địa chỉ này, nhưng không vượt ra ngoài mạng Internet. Nó là địa chỉ dùng cho việc thay thế Ipv4 trong mạng intranet. Vì vậy lý tưởng cho các tổ chức không kết nối tới internet toàn cầu. FP = 1111 1110 11 (FEC0::/10). Địa chỉ Site Local tương tự như các dải địa chỉ trong Ipv4: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.

![ảnh minh hoạ](https://imgur.com/VxIb0pG.png)

    - Địa chỉ link-local: Dùng trên mỗi liên kết cho việc tự cấu hình địa chỉ, nhận dạng đường kết nói nội bộ, các router sẽ không chuyển các gói dữ liệu sử dụng Link Local, chúng chỉ cho truyền tin cục bộ trên một đoạn mạng. FP = 1111 1110 10 (FE80::/10). Dạng địa chỉ này mang ý nghĩa tương đương với APIPA (Automatic Private IP Addressing) trong Ipv4 được tự động gán chó các máy chạy trên nền hệ điều hành MS Window với dải địa chỉ 169.254.0.0/16. Cấu trúc của dạng địa chỉ này:

![ảnh minh hoạ](https://imgur.com/b5jKztG.png)
       - Giá trị Interface ID được mô tả giống với dạng địa chỉ Global Unicast. Nhưng địa chỉ này chỉ được định nghĩa trong phạm vi kết nốt point-to-point (điểm - điểm) và chỉ có thể được sử dụng bởi các trạm kết nốt với cùng một liên kết hay cũng một mạng địa phương.
       - Qui tắc định tuyến đối với dạng địa chỉ link-local: Một router không thể chuyển bất kỳ gói tin nào có địa chỉ nguồn hoặc địa chỉ đích là địa chỉ link-local Giả sử có một mạng LAN nhỏ với một ít PC kết nối với nhau và không cần router, lúc đó sẽ dùng địa chỉ Link Local.
- Cấu trúc Header của một địa chỉ IPv4

![ảnh minh hoạ](https://imgur.com/Z0rwsNw.png)
  - Trong đó:
    - Phiên bản (Version):Trường đầu tiên trong header của gói tin IP chính là trường Phiên bản (Version) dài 4 bit. Với IPv4, nó có giá trị bằng 4.
    - Độ lớn của header (Internet Header Length) (IHL):Trường thứ hai (4 bit) là độ lớn của header (Internet Header Length - IHL) cho biết số lượng các từ 32-bit trong header. Vì một header của gói tin IPv4 có thể chứa rất nhiều tùy chọn (options), trường này cho biết kích thước của header (nó cũng trùng với offset của data). Giá trị nhỏ nhất cho trường này là 5 (RFC 791), do đó gói tin có độ dài là 5×32 = 160 bit. Vì đây là số 4 bit nên độ dài lớn nhất có thể được của gói tin là 15 từ (15×32 bit) tức là 480 bit.
    - Differentiated Services (DS):rường này có 8 bít, xác định quyền ưu tiên, độ trễ, thông lượng, các đặc tính chỉ định độ tin cậy khác. Trường này gồm TOS (Type of Service) và Precedence. TOS xác định loại dịch vụ, bao gồm: giá trị, độ tin cậy, thông lượng, độ trễ hoặc bảo mật. Precedence xác định mức ưu tiên, sử dụng 8 mức từ 0-7.
    - Total Length:Chỉ định tổng chiều dài gói tin IPv4 (cả phần mào đầu và phần dữ liệu). Kích thước 16 bít, chỉ định rằng gói tin IPv4 nhỏ nhất là 20 byte (chỉ có header không có dữ liệu) và có thể lớn tới 65.535 byte.
    - Identification:Định danh gói tin. Kích thước 16 bít. Định danh cho gói tin được lựa chọn bởi nguồn gửi gói tin. Nếu gói tin IPv4 bị phân mảnh, mọi phân mảnh sẽ giữ lại giá trị trường định danh này, mục đích để nút đích có thể nhóm lại các mảnh, phục vụ cho việc phục hồi lại gói tin.
    - Time to Live (Thời gian giữ lại gói dữ liệu)
    - Header Checksum (Mã kiểm soát lỗi)

- Phân lớp địa chỉ IP:Ban đầu địa chỉ IP được chia làm 2 phần: 8 bit đầu Network và 24 bit sau là Host.Tuy nhiên  số network chỉ giới hạn ở con số 256 mạng nên  một địa chỉ IP được phân chia lại thành 5 lớp như sau:
   - Lớp A. 8 bit network trong đó 1 bit đầu bằng 0 – 24 bit host: 0.0.0.0 đến 126.255.255.255, như vậy sẽ có 127 dải mạng, mỗi dải mạng lớp A có đến 16,777,216 host.
   - Lớp B.16 bit network trong đó 2 bit đầu bằng 10 – 16 bit host: 128.0.0.0 đến 191.255.255.255, lớp B có 16,384 dải mạng, mỗi dải mạng lớp B sẽ có tối đa 65,536 host.
   - Lớp C. 24 bit network trong đó 3 bit đầu bằng 110 – 8 bit host: 192.0.0.0 đến 223.255.255.255, và lớp C có 2,097,152 dải mạng, mỗi dải mạng lớp C sẽ có tối đa 256 host.
   - Lớp D. 4 bit đầu bằng 1110 – 28 bit dùng cho multicast. 224.0.0.0 đến 239.255.255.255
   - Lớp E. 4 bit đầu bằng 1111 – 28 bit còn lại chưa rõ. 240.0.0.0 đến 255.255.255.255

![ảnh minh hoạ](https://imgur.com/Zq8DWAS.png)
- Hạn chế của IPv4:Trong cấu trúc thiết kế của địa chỉ IPv4 không có cách thức bảo mật nào đi kèm. IPv4 không cung cấp phương tiện hỗ trợ mã hóa dữ liệu. Kết quả là hiện nay, bảo mật ở mức ứng dụng được sử dụng phổ biến, không bảo mật lưu lượng truyền tải giữa các host. Nếu áp dụng IPSec là một phương thức bảo mật phổ biến tại tầng IP, mô hình bảo mật chủ yếu là bảo mật lưu lượng giữa các mạng, việc bảo mật lưu lượng đầu cuối – đầu cuối được sử dụng rất hạn chế.Nguy cơ thiếu hụt không gian địa chỉ, cùng những hạn chế của IPv4 thúc đẩy sự đầu tư nghiên cứu một giao thức internet mới, khắc phục những hạn chế của giao thức IPv4 và đem lại những đặc tính mới cần thiết cho dịch vụ và cho hoạt động mạng thế hệ tiếp theo.

![ảnh minh hoạ](https://imgur.com/I0sLNKI.png)
- [Link tham khảo ](https://sites.google.com/site/mangmaytinh00/home/dhia-chi-ip-v4)
- [Link tham khảo](https://vi.wikipedia.org/wiki/IPv4#Ph%C3%A2n_l%E1%BB%9Bp_%C4%91%E1%BB%8Ba_ch%E1%BB%89)
### **2.IPv6**
- **Địa chỉ IPv6 (Internet protocol version 6)**: là thế hệ địa chỉ Internet phiên bản mới được thiết kế để thay thế cho phiên bản địa chỉ IPv4 trong hoạt động Internet.
- IPv6 có những lợi ích gì so với IPv4
  - Không gian địa chỉ lớn hơn và dễ dàng quản lý không gian địa chỉ.
  - Khôi phục lại nguyên lý kết nối đầu cuối-đầu cuối của Internet và loại bỏ hoàn toàn công nghệ NAT
  - Quản trị TCP/IP dễ dàng hơn: DHCP được sử dụng trong IPv4 nhằm giảm cấu hình thủ công TCP/IP cho host. IPv6 được thiết kế với khả năng tự động cấu hình mà không cần sử dụng máy chủ DHCP, hỗ trợ hơn nữa trong việc giảm cấu hình thủ công.
  - Cấu trúc định tuyến tốt hơn: Định tuyến IPv6 được thiết kế hoàn toàn phân cấp.
  - Hỗ trợ tốt hơn Multicast: Multicast là một tùy chọn của địa chỉ IPv4, tuy nhiên khả năng hỗ trợ và tính phổ dụng chưa cao.
  - Hỗ trợ bảo mật tốt hơn: IPv4 được thiết kế tại thời điểm chỉ có các mạng nhỏ, biết rõ nhau kết nối với nhau. Do vậy bảo mật chưa phải là một vấn đề được quan tâm. Song hiện nay, bảo mật mạng internet trở thành một vấn đề rất lớn, là mối quan tâm hàng đầu.
  - Hỗ trợ tốt hơn cho di động: Thời điểm IPv4 được thiết kế, chưa tồn tại khái niệm về thiết bị IP di động. Trong thế hệ mạng mới, dạng thiết bị này ngày càng phát triển, đòi hỏi cấu trúc giao thức Internet có sự hỗ trợ tốt hơn.

![ảnh minh hoạ](https://imgur.com/SJ4FMm1.png)

![ảnh minh hoạ](https://imgur.com/qCtTXry.png)

- Vậy header của IPv6 có gì khác so với IPv4 ??
![ảnh minh hoạ](https://imgur.com/WFKrMkS.png)
  - Version: cho biết version IP (trong trường hợp này là 6).
  - Traffic Class: đây là trường thay thế “Type of Service” trong IPv4. Nó tạo điều kiện xử lí các dữ liệu thời gian thực và những dữ liệu khác đòi hỏi phải xử lí đặc biệt, những node gởi và router chuyển tiếp có thể sử dụng để xác định và phân biệt giữa các class khác nhau hay độ ưu tiên của các gói tin.
  - Flow Label: Trường này phân biệt các gói tin được yêu cầu đối xử như nhau để tạo điều kiện thuận lợi cho việc điều khiển lưu lượng thời gian thực. Host gửi có thể gắn nhãn thứ tự của các gói tin với một tập hợp các tuỳ chọn. Các router theo dõi luồng dữ liệu và có thể xử lí các gói tin thuộc cùng một luồng hiệu quả hơn bởi vì chúng không phải xử lí header mỗi gói tin. Flow label và địa chỉ node nguồn xác định một dòng chảy duy nhất. Các node không hỗ trợ các chức năng của trường Flow label được yêu cầu vượt qua và giữ nguyên trường label khi chuyển tiếp một gói tin và bỏ qua trường khi nhận được gói tin. Tất cả những gói tin thuộc cùng một luồng phải có cùng địa chỉ nguồn và địa chỉ đích.
  - Payload Length: là chiều dài của gói tin IP, bao gồm phần header. Header mở rộng được xem là một phần của tải trọng, do đó bao gồm trong chiều dài này.
  - Next Header: là giá trị mô tả header liền sau header IPv6. Next header có thể là header của lớp cao hơn hay của header mở rộng.
  - Hop Limit: giá trị giới hạn của số hop. Giá trị này được giảm bởi một node mà gói tin đi qua. Gói tin sẽ bị loại bỏ nếu hop limit đạt đến giá trị 0. Một vài chức năng của IPv6, như Router Advertisement, Neighbor Advertisement and Solicitation và IPv6 Redirect, được sử dụng giữa các thiết bị trên một link duy nhất. Một công nghệ được sử dụng bởi IPv6 để xác nhận gói tin không được gởi bởi một node off-link (có thể là một nỗ lực xấu thay đổi hướng dữ liệu) để yêu cầu hop limit đặt là 255, đây là giá trị tối đa của hop limit. Nếu gói tin đi qua một router và được gởi bởi một node off-link, giá trị hop limit sẽ nhỏ hơn 255. Một node IPv6 nhận được gói tin này và xác định gói tin không hợp lệ và loại bỏ nó.
- Như trên có thể thấy IPv6 đã bỏ đi một số trường so với địa chỉ IPv4 cụ thể cùng xem ảnh sau :

![ảnh minh hoạ](https://imgur.com/BC1yxiT.png)
- Các loại địa chỉ IPv6( địa chỉ Anycast thay thế cho Broadcast ở IPv4):

![ảnh minh hoạ](https://imgur.com/t6l5R18.png)
  - Địa chỉ Unicast: Là địa chỉ của một giao diện. Một gói tin được chuyển đến địa chỉ Unicast sẽ chỉ được định tuyến đến giao diện gắn với địa chỉ đó
  - Địa chỉ Anycast: Là địa chỉ của một tập giao diện thuộc của nhiều node khác nhau. Mỗi gói tin tới địa chỉ Anycast được chuyển tới chỉ một trong tập giao diện gắn với địa chỉ đó (là giao diện gần node gửi nhất và có Metrics nhỏ nhất). Địa chỉ anycast không bao giờ được sử dụng làm địa chỉ nguồn của một gói tin.
  - Địa chỉ Multicast: Địa chỉ multicast được cấu hình trong một nhóm multicast. Nhiều node có thể được gắn cho một nhóm multicast nhất định, và nhóm này được gắn một địa chỉ multicast. Do vậy, node thực hiện truyền dữ liệu sẽ chỉ cần xác định địa chỉ multicast này, để gửi gói tin đến mọi node trong nhóm multicast này.
- [link tham khảo về địa chỉ](https://vnpro.vn/thu-vien/dia-chi-anycast-va-multicast-trong-ipv6-2060.html)

- **Header mở rộng (Extention Header)**:IPv6. Nó bao gồm những header riêng rẽ được mã hoá và đặt giữa IPv6 và header lớp trên. Khi gói tin đi từ nguồn tới đích, các Node trong gian không được phép xử lý các Extension Header đến khi nó đến đích, hoặc những node đích (trường hợp địa chỉ Multicast) trừ một vài trường hợp ngoại lệ. Trường hợp ngoại lệ như là Hop-by-Hop Extension Header

![ảnh minh hoạ](https://imgur.com/WB04dmw.png)
- **Thứ tự của Extension Header** :Việc xử lý các header mở rộng phải diễn ra theo đúng tuần tự mà các header sắp xếp trong gói tin IPv6. Không bao giờ được phép xảy ra trường hợp node đích quét qua toàn bộ gói tin và chọn ra một header nào đó để xử lý trước.

![ảnh minh hoạ](https://imgur.com/eGEXyeu.png)
  -Trong bảng trên ta có thể thấy Header Destination Options xuất hiện 2 lần. Nó có ý nghĩa khác nhau với mỗi vị trí. Khí nó xảy ra trước Routing Header, header được kiểm tra bởi điểm đến đầu tiên xuất hiện trong trường đích của header IPv6, và bởi các địa chỉ theo sau được liệt kê trông header routing. Khi Destination Options xuất hiện mà không có Routing Header, hay theo sau là Routing Header thì option được xử lí bởi đích đến cuối cùng của gói tin.
- Sau đây là mô tả cách header mở rộng được sử dụng:

![ảnh minh hoạ](https://imgur.com/VZ2on5L.png)
  - Trong mỗi header, giá trị next-header mô tả header theo sau nó. Sau khi đọc header IPv6, nếu mode xử lý không phải là node đích, và next-header không phải là hop-by-hop, gói tin được chuyển tiếp. Nếu node là đích đến, thì nó xử lý mỗi header trong thứ tự nhận được.
  - **Hop-by-Hop Options Header**: Thông tin bao gồm trong header Hop-by-Hop Options phải được kiểm tra bởi các node dọc đường đi đến node đích. Hop-by-Hop Options phải được đặt ngay sau header IPv6. Nó cho phép những router dọc đường có thể kiểm tra header mà không cần xử lý bất cứ header mở rộng nào khác.
  - **Routing Header**: Đảm nhiệm xác định đường dẫn định tuyến của gói tin. Địa chỉ được liệt kê trong tiêu đề định tuyến xác định những node phải được truy cập trước khi đến đích. Header IPv6 chứa node đầu tiên được truy cập và tiêu đề định tuyến chứa danh sách các node còn lại, bao gồm cả node đích. Tiêu đề định tuyến có chứa Next-Header, Length, Type, Segment Left và các trường địa chỉ. Trường Type có một giá trị được xác định, type 0. Trường Segment Left chứa số lượng các node được liệt kê một cách rõ ràng vẫn chưa được truy cập trước khi đạt tới đích.

  - **Fragment Header**: Được sử dụng khi một node muốn gởi một gói tin có kích thước lớn hơn MTU của con đường đến đích. Node nguồn chịu trách nhiệm phân mảnh các gói dữ liệu nếu MTU của liên kết dọc theo đường truyền tải nhỏ hơn so với gói tin. Các router dọc đường đi không phân mảnh gói tin. Node nguồn phân mảnh gói tin và gởi nhiều gói tin đó và được nối lại bởi đích đến. Node nguồn sử dụng tiến trình gọi là MTU path discovery để xác định MTU nhỏ nhất dọc đường đến node đích.

  - **Destination Options Header**: Header chứa những option phải được xử lý bởi đích đến của gói tin IPv6. Khi header ngay trước header routing, option được xử lý bởi mỗi node trong header routing. Khi header ngay trước header Upp-Layer Protocol, nó được xử lý bởi đích đến cuối cùng.

  - **Authentication: Header Authentication** được thêm vào IPv6. Mục đích là để cung cấp tính toàn vẹn và xác thực cho các gói IP.

  - **Encapsulating Security Payload**: Tính toàn vẹn và bảo mật được cung cấp bởi Encapsulating Security Payload (ESP). Ta có thể sử dụng header Authentication kết hợp với ESP để cung cấp sự xác thực.
### **3.So sánh IPv4 và IPv6**

![ảnh minh hoạ](https://imgur.com/3HXStB7.png)

![ảnh minh hoạ](https://imgur.com/5485dLZ.png)
