# Hướng dẫn này dành cho các bạn sử dụng solarbox bên mình setup sẵn
## 1. Chuẩn bị dây mạng từ router đến PIN
Do box sử dụng giao tiếp bluetooth với Pin nên cần đặt gần PIN, do vậy cần chuẩn bị dây mạng từ router đến PIN. Nếu bạn không mua được dây mạng bên mình có hỗ trợ (4k/m).
## 2. Setup wifi biến tần
- Cài đặt Network Analyzer cho [Ios](https://itunes.apple.com/us/app/network-analyzer-wifi-scanner-speed-test-tools/id557405467?mt=8) hay [android](https://play.google.com/store/apps/details?id=net.techet.netanalyzer.an)
- Xác định địa chỉ IP của module wifi bằng cách scan bằng ứng dụng Network Analyzer (module wifi có tên mico)
- Xác định serial number (SN) của module wifi. [Video hướng dẫn](https://www.youtube.com/watch?v=7GBn8MzmN7o) hoặc có thể xem trực tiếp trên module wifi.
<!-- - Cài dặt địa chỉ tĩnh cho module wifi
- Mở cổng 8000 cho module wifi
- Gửi thông tin: SN, địa chỉ IP cho mình
- Video hướng dẫn  -->
## 3. Đăng nhập vào ứng dụng homeassitant
- Cài đặt ứng dụng cho [Ios](https://apps.apple.com/app/home-assistant/id1099568401?itsct=apps_box_badge&itscg=30200) hoặc [Android](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1)
- Đăng nhập với thông tin mình gửi. [Video hướng dẫn](https://youtube.com/shorts/DpIyl63lWtc?feature=share)
- Kết nối với biến tần. Mình có thể hổ trợ từ xa hoặc bạn có thể kết nối bằng[Video hướng dẫn](https://www.youtube.com/shorts/g12Ak6pNzmc)
- Nếu gặp vấn đề gì inbox mình hỗ trợ