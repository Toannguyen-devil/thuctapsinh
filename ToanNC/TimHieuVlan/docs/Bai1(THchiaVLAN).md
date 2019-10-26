# **Lab 1: Tập cấu hình với Switch cơ bản**
## **Các nội dung chính**
- **1.Mục Đích**
- **2.Thực Hành**
### **1.Mục Đích**
- Với bài lab này yêu cầu chúng ta biết được những mục sau
  - Cấu hình cơ bản trên các switch
  - Tạo các VLAN
  - Gán các port đến một VLAN
  - Thêm, xoá và thay đổi các port
  - Kiểm tra cấu hình VLAN
  - Kích hoạt trunking trên các kết nối liên switch
  - Kiểm tra cấu hình trunk
  - Sao lưu cấu hình trunk
- Cấu hình cơ bản trên Switch ở đây chúng ta cần nắm được cách cấu hình về:
  - Cấu hình host name
  - Cấu hình mật khẩu chế độ EXEC: 123
  - Cấu hình mật khẩu kết nối console: 456
  - Cấu hình mật khẩu kết nối vty: 789
### **2.Thực Hành**
#### **2.1.Cấu hình cơ bản trên Switch**
- Mật khẩu truy cập vào enable mode
  - Switch(config)#enable password 123(nghĩa là mật khẩu để vào được enable mode là 123) mật khẩu này chưa ở dạng được mã hoá
- Đặt mật khẩu truy cập cho cổng console 
  - Switch(config)#line console 0
  - Switch(config-line)#login
  - Switch(config-line)#password 456
- Đặt mật khẩu telnet: dùng lệnh line vty
  - Switch(config-line)#line vty 0 4
  - Switch(config-line)#login
  - Switch(config-line)#password 789
- Cụ thể chúng ta cùng xem các bước sau
![ảnh](https://imgur.com/f8bSiRc.png)

- Sau khi làm các bước trên xong chúng ta sẽ xử dụng câu lệnh **do show running** nếu đang ở trong (config) còn nếu không thì chỉ việc dùng **show running**. Khi show running ta sẽ thấy được các cấu hình pass vừa cấu hình trên cũng như banner và hostname mới
 
![ảnh](https://imgur.com/gcXHJVe.png)
![ảnh](https://imgur.com/1SFASEA.png)
#### **2.2.Tiến hành cấu hình cho các Switch**
- đầu tiên cần xây dựng mô hình trên ở packet nha mọi người và cấp IP cho các PC

![ảnh](https://imgur.com/MmnLuqc.png)
![ảnh](https://imgur.com/54F2BcW.png)
- Sau khi tiến hành xây dựng mô hình và cấp IP cho các PC ta tiến hành cấu hình trên Switch như sau
- Tạo các VLANs trên switch S1(làm tương tự vs các switch S2 và S3):

  - S1(config)#vlan 10
  - S1(config-vlan)#name faculty/staff
  - S1(config-vlan)#vlan 20
  - S1(config-vlan)#name students
  - S1(config-vlan)#vlan 30
  - S1(config-vlan)#name guest
  - S1(config-vlan)#vlan 99
  - S1(config-vlan)#name management 
  - S1(config-vlan)#end
- Kiểm tra các VLANs đã tạo trên switch S1:

  - S1#show vlan brief
- Cấu hình các port trên switch S2, S3:

  - S2:
     - S2(config)#interface range fa0/6, fa0/11, fa0/18
     - S2(config-if-range)#switchport mode access--chỉ là cổng truy cập
     - S2(config-if-range)#no shutdown
  - S3:
     - S3(config)#interface range fa0/6, fa0/11, fa0/18
     - S3(config-if-range)#switchport mode access
     - S3(config-if-range)#no shutdown
- Gán các port đến các VLANs trên switch S2, S3:

  - S2(Cấu hình tương tự trên S3):
     - S2(config)#interface range fa0/6-11
     - S2(config-if-range)#switchport access vlan 30
     - S2(config-if-range)#interface range fa0/11-17
     - S2(config-if-range)#switchport access vlan 10
     - S2(config-if-range)#interface range fa0/18-24
     - S2(config-if-range)#switchport access vlan 20
     - S2(config-if-range)#end
     - S2#copy running-config startup-config--Lưu ý nếu ko có câu này các câu lệnh cấu hình trên sẽ mất
- Gán IP cho các VLAN management trên switch S1, S2, S3:
  - S1:
     - S1(config)#interface vlan 99
     - S1(config-if)#ip address 172.17.99.11 255.255.255.0
     - S1(config-if)#no shutdown
  - S2:
     - S2(config)#interface vlan 99
     - S2(config-if)#ip address 172.17.99.12 255.255.255.0
     - S2(config-if)#no shutdown
  - S3:
     - S3(config)#interface vlan 99
     - S3(config-if)#ip address 172.17.99.13 255.255.255.0
     - S3(config-if)#no shutdown
- Cấu hình trunking và native VLAN cho các port trunking trên các switch S1, S2, S3:

  - S1:
     - S1(config)#interface range fa0/1-5
     - S1(config-if-range)#switchport mode trunk
     - S1(config-if-range)#switchport trunk native vlan 99
     - S1(config-if-range)#no shutdown
     - S1(config-if-range)#end
  - S2:
     - S2(config)#interface range fa0/1-5
     - S2(config-if-range)#switchport mode trunk
     - S2(config-if-range)#switchport trunk native vlan 99
     -S2(config-if-range)#no shutdown
     - S2(config-if-range)#end
  - S3:
     - S3(config)#interface range fa0/1-5
     - S3(config-if-range)#switchport mode trunk
     - S3(config-if-range)#switchport trunk native vlan 99
     - S3(config-if-range)#no shutdown
     - S3(config-if-range)#end
- Sau khi xong mọi người tiến hành kiểm tra các cấu hình mình vừa làm nha

![ảnh](https://imgur.com/A2qZdfo.png)
![ảnh](https://imgur.com/RpFbepC.png)
![ảnh](https://imgur.com/abrjT8R.png)
![ảnh](https://imgur.com/hiA8tx3.png)