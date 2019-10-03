# **Mô Hình OSI và Một số giao thức**
## **Mục Lục**
- **1.Tìm Hiểu Mô Hình OSI**
- **2.Quá Trình Chuyển Hoá Dữ Liệu Trong OSI**
- **3.Tìm Hiểu về UDP và TCP**
- **4.Giao Thức ARP**
### **1.Tìm Hiểu Mô Hình OSI**
- **Mô Hình OSI**:là một thiết kế dựa vào nguyên lý tầng cấp, lý giải một cách trừu tượng kỹ thuật kết nối truyền thông giữa các máy vi tính và thiết kế giao thức mạng giữa chúng. Mô hình này được phát triển thành một phần trong kế hoạch Kết nối các hệ thống mở (Open Systems Interconnection) do ISO và IUT-T khởi xướng. Nó còn được gọi là Mô hình bảy tầng của OSI.
- **Mô Hình OSI** phân chia chức năng của một giao thức thành mỗi chuỗi các tầng cấp . mỗi tầng cấp có đặc điểm nó chỉ sử dụng chức năng tầng dưới nó và cho phép tâng trên dùng chức năng của chính mình
![ảnh minh hoạ](https://imgur.com/laMSAkn.png)
- Tuy là có 7 tầng nhưng mô hình OSI có thể chia thành hai thành phần chính như sau:
  - Phần 1: gồm 3 tầng trên cùng sẽ đảm bảo công việc thiết lập giao tiếp giữa người dùng với máy tính, máy tính với máy tính.
  - Phần 2: gồm 4 tầng dưới cùng đảm nhận việc truyền tải dữ liệu , đảm bảo độ chính xác, an toàn cũng như gán các địa chỉ máy nguồn máy đích để gói tin đi đúng nơi.
![ảnh minh hoạ](https://imgur.com/5N6CIBH.png)
- Bây giờ chúng ta cùng tìm hiểu cụ thể về tùng tầng một nha
  - **Tầng Ứng Dụng – Application Layer**:Là tầng người dùng giao tiếp với máy tính.Chịu trách nhiệm xác định, thiết lập các kết nối cho người dùng tới những dịch vụ mà họ mong muốn tồn tại.
  - **Tầng Phiên Dịch – Presentation Layer**:mã hóa, giải mã chuyển đổi mã hóa dữ liệu => chuyển dữ liệu người dùng nhập vào thành các chuẩn để các máy tính khác hiểu được trước khi đưa vào đường truyền. Đảm bảo dữ liệu gửi đi thì tầng ứng dụng của các máy khác sẽ đọc được.
![ảnh minh hoạ](https://imgur.com/xXi48er.png)
    - Một số chuẩn mã hóa của tầng phiên dịch :
      - PICT : định dạng cho ảnh
      - TIFF : định dạng cho tập tin đồ họa các độ phân giải cao
      - JPEG : định dạng chuẩn cho tập tin ảnh
      - MIDI : định dạng nhạc số
      - MPEG : điịnh dạng video cho đĩa CD với bit-rate lên tới 1.5Mbps
  - **Tầng Phiên – Session Layer**:Chịu trách nhiệm thiết lập, quản lí và hủy các phiên làm việc với các máy khách.Cung cấp trình kiểm soát hộp thoại giữa các thiết bị số hoặc các chốt. Tầng này tạo các kết nối giữa các hệ thống khác nhau và thiết lập việc giao tiếp bằng 3 modes : simplex, hafl-duplex, full-duplex.
![ảnh minh hoạ](https://imgur.com/yiT5e3o.png)
    - Hafl- duplex ( bán lưỡng truyền) : dữ liệu truyền đi và về trên cùng đường truyền, khi đầu này gửi gói tin đi và đầu bên kia cũng gửi gói tin, khi đến nơi giao nhau, 1 gói tin phải nhường cho gói tin kia đi trước rồi nó mới có thể tiếp tục được truyền tải tiếp, có thể xảy ra xung đột
    - Full- duplex ( lưỡng truyền) : dữ liệu truyền đi và về trên cùng một đường truyền tuy nhiên theo 2 chiều khác nhau và hoàn toàn không liên quan gì đến nhau, do vậy không xảy ra xung đốt => tốc độ truyền nhanh hơn.
    - Simplex ( đơn truyền ) : dữ liệu chỉ được truyền đi hoặc về .
  - **Tầng Giao vận – Transport Layer**:Các Segment và các dữ liệu cần lắp ráp lại từ các tầng ứng dụng ở trên gửi xuống sẽ được đựa vào 1 đường truyền chung.Cung cấp dịch vụ giao vận đầu – cuối và thiết lập các kết nối vật lí giữa máy gửi và máy nhận trong một khu vực mạng.Sử dụng giao thức giao vận tin cậy ( TCP ) hoặc truyền thông không tin cậy ( UDP ).Chịu trách nhiệm cung cấp cơ chế hoạt động cho các dịch vụ ở các tầng ứng dụng ở trên như tạo phiên, hủy các kết nối ảo. Nó cũng ẩn các thông tin chi tiết phụ thuộc của các tầng trên bằng cách cung cấp cơ chế truyền tải trong suốt.
![ảnh minh hoạ](https://imgur.com/f4vvMsh.png)
  - **Tầng Mạng – Network Layer** :(Router)Lớp Mạng có trách nhiệm định tuyến thông qua mạng và địa chỉ mạng. Điều này có nghĩa là lớp Mạng có trách nhiệm truyền tải lưu lượng giữa các thiết bị không nằm trong vùng mạng nội bộ.Routers hoặc các thiết bị khác ở lớp 3 hoạt động và cung cấp dịch vụ định tuyến ở tầng này.
    - **Cơ chế** : khi một packet được router nhận , nó sẽ kiểm tra địa chỉ IP đích của gói tin. Nếu gói tin có địa chỉ đích không phải nó, router sẽ tra cứu trong bảng định tuyến của mình. Khi kiểm tra có địa chỉ IP đó, packet sẽ được chuyển xuống tầng Datalink của Router để gắn địa chỉ MAC thành frame, và gửi ra ngoài mạng nội bộ để truyền tới các router khác. Nếu nó kiểm tra trong bảng định tuyến không thấy IP đích, gói tin đó sẽ bị vứt bỏ.
![ảnh minh hoạ](https://imgur.com/vUGCWvz.png)
  - **Tầng liên kết dữ liệu – Data Link Layer**:(Switch và Bridges)Đảm bảo gói tin sẽ được gửi tới đúng thiết bị và phiên dịch các gói tin đó thành các bit 1 0 0 1 để truyền xuống tầng vật lý.Các packets từ tầng Network sẽ được đóng gói vào các đơn vị lớn hơn gọi là Frame. Địa chỉ MAC nguồn và MAC đích sẽ được gắn vào frame.Để thực hiện được nhiệm vụ đó thì tầng Data link dùng 2 giao thức là LLC (logical link control) và MAC (Media Access Control ) được nằm trong bộ tiêu chuẩn Ethernet
![ảnh minh hoạ](https://imgur.com/Yv1aaVO.png)
  - **Tầng Vật Lý – Physical Layer**:Chức năng :(Hub) gửi và nhận bits 0,1.Mỗi loại thông tin truyền thông sử dụng các định dạng bit khác nhau.Tại lớp Vật lý, giao diện giữa Thiết bị đầu cuối dữ liệu (Data Terminal Equipment - DTE) và Thiết bị Ngắt kết nối Dữ liệu ( DCE - Data Circuit-Terminating Equipment), được xác định. DCE thường nằm ở nhà cung cấp dịch vụ, trong khi DTE là Thiết bị đính kèm. Các dịch vụ có sẵn cho DTE thường được truy cập thông qua Một modem hoặc đơn vị dịch vụ kênh / đơn vị dịch vụ dữ liệu (CSU / DSU)
![ảnh minh hoạ](https://imgur.com/wkK5hbT.png)
### **2.Quá Trình Chuyển Hoá Dữ Liệu Trong OSI**
- Xét trường hợp cụ thể là truy cập vào trang Google.
  => Bước 1: mở trình duyệt IE hoặc Firefox trên máy tính gõ : http://google.com. Do IE là phần mềm sử dụng giao thức http, https (port 80, 443). Bộ giao thức này nằm ở tầng Application. Ai muốn viết phần mềm hoặc lập trình web thì phải tuân thủ.

  => Bước 2: yêu cầu được nhập vào là ký tự trên bàn phím, máy tính sẽ chuyển đổi ra tín hiệu nhị phân (bit 0, 1) để cho máy tính hiểu. Để chuyển đổi được thì máy tính có hẳn riêng một bộ phận làm phiên dịch là tầng Presentation.

  => Bước 3: Trước yêu cầu được truyền đi máy tính sẽ có một bộ phận đàm phán phiên để truyền gọi là Session. Session ở đây nó sẽ tạo ra một kết nối trực tiếp tới Server google, được Server google đồng ý nó mới truyền yêu cầu. Sau khi kết thúc phiên nó sẽ đóng kết nối.

  => Bước 4: Để yêu cầu đi được (yêu cầu là dữ liệu) thì phải có bộ phận đóng gói dữ liệu đó là tầng Transport. Transport sẽ nhận dữ liệu từ Port 80 của giao thức http đi từ tầng Application xuống rồi đóng thêm giao thức để truyền thông là TCP hay UDP để truyền. Giao thức TCP ở tầng Transport có nhiệm vụ băm nhỏ dữ liệu ra thành các Segment (data và header). Trong header có cổng nguồn và cổng đích. Các Segment sẽ chuyển xuống tầng Network để xử lý (dữ liệu từ tầng này trở lên là độc lập với đường truyền).

  => Bước 5: Tầng Network sẽ sử dụng IPv4 và IPv6 nhưng chủ yếu là IPv4. Khi các Segment đưa xuống sẽ đóng vào gói Data lớn hơn. Trong này sẽ có IP nguồn và IP đích (địa chỉ máy gửi là máy mình và địa chỉ máy nhận là địa chỉ Server Google). Sau đó sẽ đưa xống bên dưới là tầng Data Link.

  => Bước 6: Data link đóng vào địa chỉ MAC ( MAC nguồn và MAC đích). MAC của máy PC1 và MAC cổng Gateway. Data link sẽ đóng vào đầu là Header và cuối là Trailer. Sau đó đưa xuống đường vật lí (physical).

  => Bước 7: Đường vật lí là tín hiệu điện 0,1 được gửi đi (tín hiệu điện này khác với tín hiệu điện dữ liệu)

  => Bước 8: Sau khi gửi ra Router thì nó sẽ nhận các tín hiệu và đóng gói rồi phân tích địa chỉ MAC. Router sẽ xem địa chỉ MAC đích là ai nếu đúng nó sẽ xác định để xử lý. Nếu đúng nó tách ra và đưa lên tầng Network để xác định địa chỉ IP của đích tới. Sau khi xác định xong sẽ đóng gói lại và chuyển ra cổng bên ngoài. Router sẽ sử dụng bảng định tuyến để gửi ra đúng cổng cần chuyển. Tương tự các thiết bị Router kế tiếp sẽ nhận và gửi đi sau đó gửi tới đích là Server Google.

  => Bước 9: Sau khi xử lý Server sẽ gửi lại dữ liệu yêu cầu vào đường truyền.

  => Bước 10: Sau khi dữ liệu tới đích nó sẽ gửi lên cửa sổ IE và kết thúc quá trình truyền thông.

- Trong này chúng ta có đề cập tới một số các giao thức cũng như các địa chỉ Logic và Vật Lý vậy nó là gì??, cùng tìm hiểu ở các mục dưới nha
### **3.Tìm Hiểu cơ bản về IP,MAC,TCP và UDP**
  - **Địa chỉ Logic(hay chính là IP)**: là số định dạng cho một phần cứng mạng, các thiết bị sử dụng địa chỉ IP để liên lạc với nhau qua mạng dựa trên IP như mạng Internet.Một địa chỉ IP sẽ có các trường như sau(xét IPv4)
![ảnh minh hoạ](https://imgur.com/Py2mK5S.png)
     - Phiên bản (Version):Trường đầu tiên trong header của gói tin IP chính là trường Phiên bản (Version) dài 4 bit. Với IPv4, nó có giá trị bằng 4. 
     - Header Length : độ lớn của Header 
     - Differentiated Services (DS): trường này gồm 8 bit xác định độ ưu tiên , độ trễ , thông lượng , các đặc tính chỉ định độ tin cậy
     - Total Length: Độ dài tổng của gói tin IPv4
     - Identification:Định danh gói tin. Kích thước 16 bít. Định danh cho gói tin được lựa chọn bởi nguồn gửi gói tin. Nếu gói tin IPv4 bị phân mảnh, mọi phân mảnh sẽ giữ lại giá trị trường định danh này, mục đích để nút đích có thể nhóm lại các mảnh, phục vụ cho việc phục hồi lại gói tin.
     - Flags: trường cờ
     - Time to Live : thời gian giữ lại gói tin
     - Source Address : địa chỉ máy trạm ở đây chính là địa chỉ của máy gửi 
     - Destination Address: địa chỉ máy đích ở đây là địa chỉ của máy đích
  - **Địa chỉ Vật Lý(hay chính là MAC)**:là mã duy nhất được gán bởi nhà sản xuất cho từng phần cứng mạng (như cạc không dây hoặc cạc Ethernet). MAC viết tắt của Media Access Control, và mỗi mã là duy nhất cho một thiết bị. Địa chỉ MAC là một bộ sáu cặp hai ký tự, cách nhau bằng dấu hai chấm.
![ảnh minh hoạ](https://imgur.com/m9UI30L.png)
  - **Giao thức TCP(Transmission Control Protocol)**:là một trong các giao thức cốt lõi của bộ giao thức TCP/IP. Sử dụng TCP, các ứng dụng trên các máy chủ được nối mạng có thể tạo các "kết nối" với nhau, mà qua đó chúng có thể trao đổi dữ liệu hoặc các gói tin. Giao thức này đảm bảo chuyển giao dữ liệu tới nơi nhận một cách đáng tin cậy và đúng thứ tự. TCP còn phân biệt giữa dữ liệu của nhiều ứng dụng (chẳng hạn, dịch vụ Web và dịch vụ thư điện tử) đồng thời chạy trên cùng một máy chủ.
  - Cấu trúc gói tin TCP
![ảnh minh hoạ](https://imgur.com/iivM0xF.png)
    - Source port :Số hiệu của cổng tại máy tính gửi.
    - Destination port:Số hiệu của cổng tại máy tính nhận.
    - Sequence number:Trường này có 2 nhiệm vụ. Nếu cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tiên được gửi có số thứ tự này cộng thêm 1. Nếu không có cờ SYN thì đây là số thứ tự của byte đầu tiên.     
    - Acknowledgement number:Nếu cờ ACK bật thì giá trị của trường chính là số thứ tự gói tin tiếp theo mà bên nhận cần.
    - Data offset:Trường có độ dài 4 bít quy định độ dài của phần header (tính theo đơn vị từ 32 bít). Phần header có độ dài tối thiểu là 5 từ (160 bit) và tối đa là 15 từ (480 bít)
    - Reserved: Dành cho tương lai và có giá trị là 0.
    - Flags (hay Control bits):Bao gồm 6 cờ:
       - URG:Cờ cho trường Urgent pointer
       - ACK:Cờ cho trường Acknowledgement
       - PSH:Hàm Push
       - RST:Thiết lập lại đường truyền
       - SYN:Đồng bộ lại số thứ tự
       - FIN:Không gửi thêm số liệu
    - Window:Số byte có thể nhận bắt đầu từ giá trị của trường báo nhận (ACK)
    - Checksum: 16 bít kiểm tra cho cả phần header và dữ liệu
    - Urgent pointer:Nếu cờ URG bật thì giá trị trường này chính là số từ 16 bít mà số thứ tự gói tin (sequence number) cần dịch trái.
    - Options:Đây là trường tùy chọn. Nếu có thì độ dài là bội số của 32 bít.
  - Ngoài ra trong giao thức này chúng ta cần chú ý đến các khái niệm quá trình bắt tay 3 bước, cửa sổ trượt, điều khiển luồng
    - Truyền thông hướng kết nối :Trong truyền thông tin cậy ,khi 2 máy muốn kết nối với nhau , mỗi máy sẽ thông báo tới hệ thống của mình là 1 kết nối sắp được thiết lập, 2 hệ điều hành sẽ kết nối bằng cách gửi tin nhắn xác nhận cho nhau thông qua mạng về việc chuẩn bị kết nối. Khi mà việc yêu cầu đồng bộ giữa 2 bên hoàn thành, một kết nối sẽ được thiết lập và dữ liệu bắt đầu truyền. Đây gọi là quá trình BẮT TAY 3 BƯỚC.
![ảnh minh hoạ](https://imgur.com/jJmCVy4.png)
    - Kiểm soát lưu lượng:Ngăn chặn việc máy chủ gửi dữ liệu đến máy khách khỏi việc quá tải , điều có thể gây mất dữ liệu. Việc truyền tải dữ liệu tin cậy sẽ yêu cầu các kết nối định hướng giữa các hệ thống, và các giao thức mà đảm bảo được những điều sau đây sẽ đủ tiêu chuẩn để truyền tải tin cậy 
![ảnh minh hoạ](https://imgur.com/3i0Pama.png)
    - Windowing - cửa sổ trượt :Dữ liệu truyền qua đường truyền bằng giao thức truyền thông tin cậy sẽ phải chờ máy khách đã nhận dữ liệu, rồi mới gửi tiếp các segment khác. Tuy nhiên quá trình đó sẽ mất nhiều thời gian và tốc độ không cao, vì vậy hình thành nên giao thức gửi dữ liệu bằng windowing.
![ảnh minh hoạ](https://imgur.com/syZPEBt.png)
  - **UDP (User Datagram Protocol)**: là giao thức theo phương thức không liên kết được sử dụng thay thế cho TCP ở trên IP theo yêu cầu của từng ứng dụng. Khác với TCP, UDP không có các chức năng thiết lập và kết thúc liên kết. Tương tự như IP, nó cũng không cung cấp cơ chế báo nhận (acknowledgment), không sắp xếp tuần tự các gói tin (datagram) đến và có thể dẫn đến tình trạng mất hoặc trùng dữ liệu mà không có cơ chế thông báo lỗi cho người gửi. Qua đó ta thấy UDP cung cấp các dịch vụ vận chuyển không tin cậy như trong TCP.
![ảnh minh hoạ](https://imgur.com/f0W26MO.png)
     - UDP cũng cung cấp cơ chế gán và quản lý các số hiệu cổng (port number) để định danh duy nhất cho các ứng dụng chạy trên một trạm của mạng. Do ít chức năng phức tạp nên UDP thường có xu thế hoạt động nhanh hơn so với TCP. Nó thường được dùng cho các ứng không đòi hỏi độ tin cậy cao trong giao vận.
       - Ví dụ, giả sử bạn đang xem hình ảnh video trực tiếp. Live Stream phát sóng thường sử dụng UDP thay vì TCP. Các máy chủ chỉ cần gửi một dòng của các gói tin UDP để máy tính xem. Nếu bạn bị mất kết nối trong vài giây, video sẽ đóng băng cho một thời điểm và sau đó chuyển đến các bit hiện tại của truyền hình, bỏ qua các bit bạn đã bị bỏ qua. Video hoặc âm thanh có thể bị bóp méo một lúc và video tiếp tục chơi mà không có dữ liệu bị mất.
       - Các thuật ngữ trong UDP
         -**Packet**: trong truyền số liệu một packet là các số nhị phân , biểu diễn dữ liệu cà các tín hiệu điều khiển
         -**Datagram**: là một gói tin đọc lập, tự chứa và mang đầy dữ liệu định tuyến 
         -**MTU(Maximum Transmission Unit): mô tả số byte có thể truyền trong một gói tin
         -**Port**: các cổng để ánh xạ tiến trình cụ thể đang chạy trên máy tính
         -**Time to Live**:cho phép chúng ta thiết lập một giới hạn trên các router mà một datagram có thể đi qua
    - Các cổng của giao thức UDP
![ảnh minh hoa](https://imgur.com/5ibC4mf.png)
### **4.Tìm Hiểu Giao thức ARP**
- là giao thức dùng để phân giải địa chỉ logic(IP) sang thành địa chỉ vật lý(MAC) như vậy làm thế nào để để giao thức này có thể phân giải được . Trước tiên chúng ta tìm hiểu về việc cấu trúc của gói tin ARP như nào
![ảnh minh hoạ](https://imgur.com/WcF6I8I.png)
  - Cụ thể về các thành phần trong gói tin ta cần lưu ý là:
    - Hardware Type:xác định kiểu bộ giao tiếp phần cứng máy gửi cần biết
    - Protocol Type:Xác định kiểu giao thức địa chỉ cấp cao máy gửi cung cấp
    - HLEN: độ dài địa chỉ vật lý (bit)
    - PLEN: độ dài địa chỉ logic (bit)
    - Sender HA (sender hardware address): địa chỉ MAC của máy gửi
    - Sender Protocol Address: địa chỉ IP máy gửi
    - Target HA (target hardware address): địa chỉ MAC của máy nhận
    - Target Protocol Address: địa chỉ IP máy nhận
- Như vậy làm ARP hoạt động sao ??
![ảnh minh hoạ](https://imgur.com/2sekdOF.png)
  - Chúng ta có thể minh hoạ một cách như sau để hiểu qua về cách thức hoạt động của giao thức ARP , ví dụ bây giờ bạn vào một lớp học bạn biết trong lớp đó có một người tên Toàn chẳng hạn , bạn muốn ngồi cạnh người đó nhưng không biết bạn ấy ngồi ở đâu thì lúc đó giải pháp tốt nhất đó chính là việc bạn nói lớn cho mọi người cùng nghe xin hỏi bạn toàn đang ngồi vị trí nào ạ , nếu bạn đó nghe thấy sẽ giơ tay lên để bạn biết được vị trí và để bạn có thể đến gần và bắt đầu cuộc trò chuyện tương tự như thế quá trình hoạt động của ARP sẽ tiến hành như sau :
    - Bước 1: Thiết bị A kiểm tra cache của mình xem có địa chỉ tham chiếu IP và địa chỉ MAC nếu có thì sẽ tiến hành kết nối không thì sẽ tiến hành bước sau
    - Bước 2: Bắt đầu khởi tạo gói tin ARP Request. Nó sẽ gửi một gói tin broadcast đến toàn bộ các máy khác trong mạng với địa chỉ MAC và IP máy gửi là địa chỉ của chính nó, địa chỉ IP máy nhận địa chỉ MAC máy nhận sẽ là ff:ff:ff:ff:ff
    - Bước 3: Thiết bị A phân phát gói tin ARP Request trên toàn mạng. Khi switch nhận được gói tin broadcast nó sẽ chuyển gói tin này tới tất cả các máy trong mạng LAN đó.
    - Bước 4: Các thiết bị trong mạng đều nhận được gói tin ARP Request. Máy tính kiểm tra trường địa chỉ Target Protocol Address. Nếu trùng với địa chỉ của mình thì tiếp tục xử lý, nếu không thì hủy gói tin.
    - Bước 5: hiết bị B có IP trùng với IP trong trường Target Protocol Address sẽ bắt đầu quá trình khởi tạo gói tin ARP Reply bằng cách:
       - lấy các trường Sender Hardware Address và Sender Protocol Address trong gói tin ARP nhận được đưa vào làm Target trong gói tin gửi đi.
       - Đồng thời thiết bị sẽ lấy địa chỉ MAC của mình để đưa vào trường Sender Hardware Address
    - Bước 6:Thiết bị B đồng thời cập nhật bảng ánh xạ địa chỉ IP và MAC của thiết bị nguồn vào bảng ARP cache của mình để giảm bớt thời gian xử lý cho các lần sau
    - Bước 7:Thiết bị B bắt đầu gửi gói tin Reply đã được khởi tạo đến thiết bị A.
    - Bước 8: Thiết bị A nhận được gói tin reply và xử lý bằng cách lưu trường Sender Hardware Address trong gói reply vào địa chỉ phần cứng của thiết bị B.
    - Bước 9:hiết bị A update vào ARP cache của mình giá trị tương ứng giữa địa chỉ IP (địa chỉ network) và địa chỉ MAC (địac chỉ datalink) của thiết bị B. Lần sau sẽ không còn cần tới request.
- Nhưng lại nảy sinh vấn đề nếu A và B ko cùng trong một mạng vậy sẽ cần phải xử lý ra sao . Lúc này chúng ta đề cập đến Proxy ARP phương này cho phép việc giao tiếp xác định giữa hai mạng . Vậy Proxy ARP là gì
  - **Proxy ARP**:là tính năng cho phép Router trả lời dùm forward ARP request của một thiết bị không nằm cùng subnet/broadcast domain với thiết bị gửi ARP request. Vậy nó sẽ hoạt động như nào ??
  - Ta xét mô hình sau đây
![ảnh minh hoạ](https://imgur.com/CNvJUnj.png)
  - Ví dụ như mô hình dưới đây khi PC nằm ở subnet 10.1.10.0 (giả sử 10.1.10.10 có MAC c4:02:03:70:00:00) muốn đi đến server 10.9.1.50. Quá trình PC thực hiện ping tới SERVER sẽ như sau:
     - 1.Gói tin 1 – Client ARP Broadcast :Client gửi gói tin ARP request để yều cầu MAC của IP server 10.9.1.50.  PC sẽ gửi gói ARP request (gói ARP request là gói tin dạng BroadCast) để tìm MAC của server 10.9.1.50 có dạng. Nó sẽ hỏi trong broadcast ARP request và hỏi “who has 10.9.1.50 ?” Nghĩa là ai là 10.9.1.50 thì nói cho Client biết địa chỉ MAC (10.9.1.50) là gì ?
![ảnh minh hoạ](https://imgur.com/txRpLvQ.png)
     - 2.Gói tin 2 – Router ARP Broadcast:Router gửi gói ARP Broadcast để tìm MAC của IP server 10.9.1.50. Khi gói tin ARP request của PC broadcast tới Router, vì gói tin này ở dạng broadcast nên các host trong cùng subnet đều nhận được và kể cả interface f0/1 của Router. Tuy nhiên, gói tin ARP request này sẽ không đến được server 10.9.1.50 vì nó sẽ bị Router drop ngay khi đến được interface f0/1 của Router. Tuy nhiên, nhờ vào cơ chế ARP Proxy được enable sẵn trên Router (default ARP Proxy bị disable trên Firewall và thiết bị security) cho phép Router mở rộng Layer 2 thông qua nhiều interface (LAN segment). Khi Router biết được subnet 10.9.1.0 (10.9.1.50) nó có đến được thì nó sẽ gửi gói tin ARP Broadcast để tìm MAC của 10.9.1.50.
![ảnh minh hoạ](https://imgur.com/WFU467c.png)
     - 3.Gói tin 3 – SERVER ARP Reply:Server trả lời gói tin ARP request của Router. Lúc này server nhận được gói tin Broadcast của Router và thấy nó có IP 10.9.1.50 nên nó sẽ trả lời lại gói ARP request của Router bằng gói ARP reply rằng “10.9.1.50 is at c4:03:14:6c:00:00”. Nghĩa là IP 10.9.1.50 có MAC là của tao (Server).
![ảnh minh hoạ](https://imgur.com/EuTWvIn.png)
     - 4.Gói tin 4 – Router ARP reply:Router gửi gói tin ARP Reply cho Client trả lời MAC của ip 10.9.1.50 cho Client. Lúc này Router sẽ gửi trả lời gói tin ARP reply cho Host A rằng “10.9.1.50 is at c4:01:16:08:00:00”. Nghĩa là nếu PC muốn đi đến host 10.9.1.50 thì hãy gửi tới interface f0/0 của Router để nó forward tới 10.9.1.50. Gói tin ARP reply mà Router trả lời (đây chính là gói tin)
![ảnh minh hoạ](https://imgur.com/emag6TE.png)
     - 5.Gói tin 5 – Client ICMP request:Gói tin ping của Client đến SERVER.Dựa vào MAC address của Server client sẽ gửi gói icmp đến server với thông tin gói tin như sau
![ảnh minh hoạ](https://imgur.com/wErDUCc.png)
     - 6.Gói tin 6 – Router forward ICMP request:Router nhận được gói ICMP từ Client ping đến Server. Nên nó tiến hành forward gói tin ICMP của Clietn đến SERVER.
![ảnh minh hoạ](https://imgur.com/kmY60JW.png)
     - 7.Gói tin 7 – Server ICMP reply:Server nhận được gói ping từ Router forward tới nó, nên nó gửi gói tin trả lời cho Router.   
![ảnh minh hoạ](https://imgur.com/u8Ty9bD.png)
     - 8.Gói tin 8 – Router forward ICMP reply:Router nhận được gói tin ICMP reply của SERVER cho Client nen nó tiến hành forward gói tin ICMP reply của SERVER cho Client. Gói tin icmp của Client sẽ được gửi đến Router và Router sẽ forward tới Server. Sau khi nhận được gói tin reply từ server nó sẽ reply lại cho Client với gói tin ICMP reply.
![ảnh minh hoạ](https://imgur.com/cz43CSO.png)
  - [Link tham khảo quá trình](http://svuit.vn/threads/proxy-arp-1185/)
  