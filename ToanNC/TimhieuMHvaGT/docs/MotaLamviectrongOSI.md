# **Hoạt Đông Trong Mô Hình OSI**
## **Mục lục**
- **1.Cách Thức Hoạt Động Trong OSI**
- **2.Tìm Hiểu Giao thức ARP**
### **1.Cách Thức Hoạt Động Trong OSI**
- Giả sử khi bạn muốn nhập thông điệp HELLO gửi từ máy bạn đến một máy nhận nào đó ta sẽ có quá trình chuyển đổi lần lượt của nó như sau
- Khi vào tầng **Application(tầng Ứng Dụng)**: gói tin vẫn chưa được chuyển đổi qua dạng chuỗi các bit tại đây gói tin này sẽ được đánh thêm các cổng để xuống các tầng giới có thể xác định được loại giao thức và địa chỉ cổng nguồn, cổng đích
![ảnh minh hoạ](https://imgur.com/LtlSwFw.png)
- Khi vào tâng **Presentation(tầng trình bày)**: gói tin lúc này sẽ chuyển qua từ dạng chuỗi ký tự , sô sang thành các chuỗi bit và được cung cấp thêm vài các giao thức mã hoá . Cụ thể ở tầng này dùng các phương pháp dịch mã từ ASCII sang EBCDIC 
- Khi vào tầng **Session(tầng phiên)**: ở tầng này cung cấp các thông tin về việc thông tin giữa hai máy hay huỷ các phiên làm việc , tầng phiên ở đây với mục đích khi bạn mở một tap wed là nhạc sau đó lại mở 1 tap khác về đọc báo thì tầng phiên đảm cho việc khi gói tin bạn nhận được hay chuyển đi là đúng các phiên làm việc của nó chứ không bị lẫn lộn , hay nói cách khác chính là bổ sung thông tin về luồng dữ liệu
  - Ngoài ra ở tầng này còn nó có thêm điểm đồng bộ với mục đồng bộ được dữ liệu khi có lỗi xảy ra
    - VD: khi truyền đi 2000 trang giấy thì mỗi khi truyền xong 100 trang thì sẽ đánh 1 nút đồng bộ vì thì khi trang thứ 523 mà có bị lỗi ta chỉ việc truyền lại từ trang 501 chứ ko pải truyền từ trang 1->500 
- Khi vào tầng **Transport(tầng vận chuyển)**: khi vào đến tầng vận chuyển các gói tin sẽ bị chia nhỏ để nhằm mục đích kiểm soát tác nghẽn (giá trị Max của segement là 1460 bytes ), khi bị chia nhỏ sang thành các segement này gói tin sẽ được ghép nối thông tin về phiên làm việc để chọn ra việc truyền theo hình thức nào tin cậy hay không tin cậy, gói tin ở tầng này được chia thành các segement
  - Trong tâng này ta cần chú ý đến hai giao thức là UDP và TCP . Trong giao thức TCP ta cần chú ý đến việc quá trình bắt tay 3 bước và cửa sổ trượt , cũng như cơ chế để điều khiển luồng
    - Quá trình bắt tay ba bước
![ảnh minh hoạ](https://imgur.com/jJmCVy4.png)
    - Điều Khiển Luồng
![ảnh minh hoạ](https://imgur.com/3i0Pama.png)
    - Cửa Sổ Trượt
![ảnh minh hoạ](https://imgur.com/syZPEBt.png)
    - [link tham khảo](https://www.youtube.com/watch?v=_-opuwvnRk0)
- Khi vào tầng **Network(tầng mạng)**: khi vào đến tầng mạng này nơi mà các router hoạt động ở đây các gói tin sẽ được có thêm địa chỉ logic nhằm mục đích định tuyến được đường đi trên mạng , việc có thêm địa chỉ logic(hay là IP) sẽ giúp cho các router tìm ra đường đi tối ưu cho gói tin đồng thời các gói tin xuống đến tầng này sẽ được đóng gói thành các Packet
    - Việc được đính thêm các header là các IP header vậy cấu trúc IP header chứa những gì
![ảnh minh hoạ](https://imgur.com/Py2mK5S.png)
      - Cụ thể với các trường trong này chúng ta cần chú ý như sau
        - Phiên bản (Version):Trường đầu tiên trong header của gói tin IP chính là trường Phiên bản (Version) dài 4 bit. Với IPv4, nó có giá trị bằng 4. 
        - Header Length : độ lớn của Header 
        - Differentiated Services (DS): trường này gồm 8 bit xác định độ ưu tiên , độ trễ , thông lượng , các đặc tính chỉ định độ tin cậy
        - Total Length: Độ dài tổng của gói tin IPv4
        - Identification:Định danh gói tin. Kích thước 16 bít. Định danh cho gói tin được lựa chọn bởi nguồn gửi gói tin. Nếu gói tin IPv4 bị phân mảnh, mọi phân mảnh sẽ giữ lại giá trị trường định danh này, mục đích để nút đích có thể nhóm lại các mảnh, phục vụ cho việc phục hồi lại gói tin.
        - Flags: trường cờ
        - Time to Live : thời gian giữ lại gói tin
        - Source Address : địa chỉ máy trạm ở đây chính là địa chỉ của máy gửi 
        - Destination Address: địa chỉ máy đích ở đây là địa chỉ của Default gateway
    - [link tham khảo](http://elearning.vnua.edu.vn/mang-may-tinh-k63attt-th02038.html?chaps_slug=41-introduction-to-network-layer-3772441)
- Khi vào tầng **Data-link**: ở đây đầu tiên dữ liệu sẽ được giao thức LLC(logical link control) xử lý trước ở đây gói tin được đóng gói thành các các Frame để mang các thông tin về việc máy đang thông tin hay là truyền thông giữa hai máy bắt đầu và kết thức khi nào , sau khi đã được tạo thành các Frame thì gói tin sẽ được giao thức MAC(Media Acces Control) xử lý sau khi được giao thức MAC xử lý gói tin sẽ được có thêm địa chỉ MAC(là địa chỉ vật lý của máy) dùng cho quá trình định tuyến đường đi để chính xác hơn giao thức MAC này hoạt động ở giữa hai tâng Data-link và Physical

![ảnh minh hoạ](https://imgur.com/uUEpPOi.png)
   - Khi làm việc ở tâng này gói tin sẽ được đính thêm địa chỉ MAC hay chính là địa chỉ vật lý của máy. Vậy địa chỉ MAC ở đây là như nào ???
   - **MAC**:là mã duy nhất được gán bởi nhà sản xuất cho từng phần cứng mạng (như cạc không dây hoặc cạc Ethernet). MAC viết tắt của Media Access Control, và mỗi mã là duy nhất cho một thiết bị. Địa chỉ MAC là một bộ sáu cặp hai ký tự, cách nhau bằng dấu hai chấm.

![ảnh minh hoạ](https://imgur.com/m9UI30L.png)

   - Vậy khi thêm địa chỉ MAC và các giao thức thực hiện xong gói tin ở tầng Data-link sẽ như nào??/

![ảnh minh hoạ](https://imgur.com/wMPE08E.png)
     - 
- Khi và đến tầng**Physical(tầng vật lý)**: khi đó gói tin ở dưới dạng một chuỗi bit hoàn chỉnh vs các thông tin về địa chỉ đến và đi để bắt đầu quá trình truyền tin đi 
![ảnh minh hoạ](https://imgur.com/uUEpPOi.png)
### **2.Tìm Hiểu Giao thức ARP**
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
  - Như vậy chúng ta đã tìm hiểu được về quá trình phân giải địa chỉ IP sang địa chỉ MAC dựa vào giao thức ARP 
