# I. Giới thiệu SolarBox

## 1. Giới thiệu
SolarBox thật ra là tvbox được mod lại để chay server [homeassitant](https://www.home-assistant.io/) để đạt giá thành rẻ

- Vào nhóm để hỗ trợ và chia sẻ kinh nghiệm: https://web.facebook.com/groups/535518005787356
- Mình có nhận setup box hoàn chỉnh giá từ 400k đến 800k (tvbox, pi ..) tùy theo nhu cầu. 

**Bản thương mại sẽ có thêm những tính năng**
+ Truy cập từ xa có sẵn tên miền và chứng chỉ https
+ Cài đặt và nâng cấp từ xa, phù hợp cho những bạn không có thời gian.
+ Cài đặt để không spam server của lux.
+ Được cập nhật tính năng mới nhanh nhất

## 2. SolarBox dùng để theo dõi biến tần
Với SolarBox bạn có thể theo dõi song song nhiều biến tần của nhiều hãng khác nhau trên cùng một ứng dụng không phụ thuộc vào server của hãng, thời gian cập nhật nhanh.
<p float="left">
  <img src="pic/InverterMonitor1.jpg" width="45%" />
  <img src="pic/InverterMonitor2.jpg" width="45%" />
</p>

## 3. SolarBox dùng để theo dõi Pin không giao tiếp
Với SolarBox bạn có thể theo dõi song song nhiều Pin lithium của nhiều hãng khác nhau trên cùng một ứng dụng.
![Battery Monitor](pic/battMonior.jpg)

## 4. Solarbox có thể kết nối từ bất kì đâu
Solarbox hỗ trợ người dùng theo dõi biến tần và bms từ bất kì nơi nào nếu có kết nối internet (wifi công cộng, 4g ...)

## 5. SolarBox dùng để tạo thông báo
Với Solarbox có thể dùng để tạo thông báo, ví dụ: 
- Thông báo khi mất điện.
- Thông báo khi pin đầy.
- Thông báo khi pin sắp cạn.
- ...

## 6. SolarBox dùng để thực thi task tự động
Với Solarbox có thể dùng để thực thi task tự động, ví dụ:
- Tự động mở tải khi PV dư mà pin đầy
- Tự động ngưng xả khi pin còn quá thấp và còn điện lưới.
- Tự động thay đổi giới hạn dòng xả của pin. VD: ngày xả 40A tối xả 60A

## 7. SolarBox dùng để theo dõi chỉ số điện từ server EVN
Với Solarbox có thể dùng để theo dõi chỉ số địen từ EVN server.
![EVN Monitor](pic/evn_monitor.jpg)

## 8. SolarBox dùng để kết nối các thiết bị nhà thông minh
Đang cập nhật .... 

# II. Nguyên Lý Hoạt Động
## 1. Mô hình SolarBox không hỗ trợ wifi & bluetooth
- Mô hình này cần có thêm module theo dõi pin lithium, nhiệm vụ của module này dùng để tạo kết nối bluetooth với JK BMS để thu thập dữ liệu và gửi thông tin về SolarBox thông qua wifi. **Do kết nối bluetooth của JK BMS rất ngắn nên module này cần được đặt gần Pin Lithium (khoảng 20cm)**
- SolarBox sẽ hoạt động như [homeassitant](https://www.home-assistant.io/) server. SolarBox sẽ thu thập thông tin từ module wifi của biến tần lux và module theo dõi Pin Lithium

Đang cập nhật hình ảnh .... 

## 2. Mô hình SolarBox hỗ trợ wifi và bluetooth
- SolarBox sẽ thiết lập kết nối với Pin Lithium thông qua bluetooth, và module wifi Lux thông qua wifi
- SolarBox sẽ hoạt động như homeassitant server. SolarBox sẽ thu thập thông tin từ module wifi của biến tần lux và Pin Lithium
- **Do kết nối bluetooth của JK BMS rất ngắn nên SolarBox cần được đặt gần Pin Lithium (khoảng 20cm)**

Đang cập nhật hình ảnh .... 
# Bonus: Hướng dẫn tạo 1 SolarBox cho riêng bạn

## 1. Cài đặt hassio
**Không khuyến khích mua tvbox mới để cài do có thể chip mới chưa được hỗ trợ**
- Xác định chip của tv box của bạn
- Tải image tương ứng với model tvbox của bạn [tại đây](https://github.com/ophub/amlogic-s9xxx-armbian/releases/tag/Armbian_HassIoSupervisor_bookworm_save_2024.09)
- Tạo SD card hoặc usb boot với [Etcher](https://etcher.balena.io/) hoặc [win32diskimager](https://sourceforge.net/projects/win32diskimager/)
- Cắm sd card hoặc usb boot vào tvbox
- TVbox vào hassio bằng cách nhấn giữ nút reset (thường nằm ở cổng av) và cấp nguồn.
- Chờ khoảng 20p và kết nối đến: `http:\\<IP của box>:8123`
- [Video hướng dẫn tại đây](https://web.facebook.com/groups/535518005787356)

## 2. Cài đặt addon lux

### a Cài đặt addon
Gửi yêu cầu cho tác giả để được truy cập repo của addon

Copy addone đến thư mục /usr/share/hassio/homeassistant/custom_components/

scp -r /duong dan den/custom_components/luxpower_proxy root@<ip của box>://usr/share/hassio/homeassistant/custom_components/

### b. Thiết lập biến tần

Để tránh các vấn đề phát sinh, bạn nên đảm bảo rằng Biến tần của bạn có địa chỉ IP tĩnh hoặc được đặt DHCP Reservation từ router của bạn. Điều này sẽ đảm bảo rằng địa chỉ IP của nó sẽ không thay đổi khi khởi động lại.

Chúng ta cần cấu hình nó để mở một cổng khác mà chúng ta có thể giao tiếp. Mở trình duyệt web đến IP của datalogger của bạn (có thể phải kiểm tra máy chủ DHCP để tìm nó) và đăng nhập với tên người dùng/mật khẩu admin/admin. Nhấp vào English ở góc trên bên phải

Bạn sẽ thấy:

![](pic/lux_run_state.png)
Nhấp vào Network Setting trong menu. Bạn sẽ thấy hai biểu mẫu, biểu mẫu trên cùng được điền với IP của LuxPower ở Trung Quốc - biểu mẫu thứ hai chúng ta có thể sử dụng. Cấu hình nó để trông giống như bên dưới và lưu lại:

![](pic/lux_network_setting.png)

Sau khi datalogger khởi động lại (chỉ mất vài giây và không ảnh hưởng đến hoạt động chính của biến tần, nó sẽ tiếp tục hoạt động bình thường), cổng 8000 trên IP của biến tần của bạn sẽ có thể truy cập được từ SolarBox. 

### c. Thiết lập kết nối
1. Settings > Devices and Services > Add Integration trong Home Assistant.
2. Search for "LuxPower Inverter".

![Integration Setup](https://user-images.githubusercontent.com/64648444/169526481-d261df8b-ecaa-48c4-a6df-f7abae382316.png)

3. Điền IP, Cổng (8000), số serial của dongle và số serial của biến tần (có sẵn trên trang web Lux tại server.luxpowertek.com).

![Integration Details](https://user-images.githubusercontent.com/64648444/169526428-a508e905-19ef-45e5-ab2c-185b454489e3.png)

4. Sau khi thêm tích hợp, bạn sẽ thấy một số cảm biến trong Home Assistant.

![HA Sensors](https://user-images.githubusercontent.com/64648444/169526605-0f667815-87dc-4ab7-86f5-dbffe85ff765.png)

<!-- [Video [SolarBox] Kết nối với biến tần](https://www.youtube.com/watch?v=g12Ak6pNzmc) -->

## 3. Cài đặt giao tiếp với Pin Lithium không giao tiếp

### 3.1 Batmon với box có bluetooth
- Link den github cua tac gia [batmon-ha](https://github.com/fl4p/batmon-ha)
- [Video hướng dẫn tại đây](https://web.facebook.com/groups/535518005787356)

### 3.2 theo dõi pin với box không có bluetooth

## 4. Cài đặt để truy cập từ xa
- Đang được cập nhật ....

<!--
3. Nhóm hỗ trợ
https://web.facebook.com/groups/535518005787356
-->

