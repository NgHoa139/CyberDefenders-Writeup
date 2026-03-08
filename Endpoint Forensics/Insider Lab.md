# Insider Lab

Q1 : What distribution of Linux is being used on this machine?
- Mở file bằng công cụ FTK Imager và kiểm tra phần syslog ở var/log ta có thể tìm ra bản linux được dùng là : **Kali**
<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/208d018f-ac1d-45b7-9e25-6fff7eed6598" />

Q2 : What is the MD5 hash of the apache access.log? 
- Export file hash list ta có : **d41d8cd98f00b204e9800998ecf8427e**
<img width="1281" height="809" alt="image" src="https://github.com/user-attachments/assets/d9d601db-8672-4eb6-bec9-5b2465e96d53" />

Q3 : It is suspected that a credential dumping tool was downloaded. What is the name of the downloaded file?
- Để kiểm tra file được tải xuống ta tìm kiếm trong root/Dowload/ : **mimikatz_trunk.zip**
<img width="1221" height="551" alt="image" src="https://github.com/user-attachments/assets/cbb95bbf-bac7-4940-8171-77364b69e24a" />

Q4 : A super-secret file was created. What is the absolute path to this file?
- Ta kiểm tra file root/bash_history : 
<img width="1240" height="728" alt="image" src="https://github.com/user-attachments/assets/dc7719dc-a937-434e-9a5a-321e0b8705fd" />

- Ta có thể thấy file được tạo ở : /root/Desktop/

Q5 : What program used didyouthinkwedmakeiteasy.jpg during execution?
- Trong file root/bash_history ta thấy chương trình sử dụng : **binwalk**
<img width="1191" height="1009" alt="image" src="https://github.com/user-attachments/assets/c8d04a1e-10fd-4fe0-8dd6-de942400695b" />

Q6 : What is the third goal from the checklist Karen created?
- Ta có thể thấy mục tiêu của Karen trong root/Desktops/Checklist là : **Profit**
<img width="1203" height="521" alt="image" src="https://github.com/user-attachments/assets/955b8144-7bfe-40be-bd89-97a8842fc355" />

Q7 : How many times was Apache run?
- Ta kiểm tra trong var/log/apache2 : 
<img width="1203" height="396" alt="image" src="https://github.com/user-attachments/assets/fa139228-6c23-4757-b013-09376fff3c0c" />

- Cả 3 file đều có size = 0 nên không có dữ liệu nào được ghi lại nên **không có apache nào được sử dụng**

Q8 : This machine was used to launch an attack on another. Which file contains the evidence for this?
- Tìm kiếm trong root ta thấy ảnh **irZLAohL.jpeg** đã lưu lại quá trình khi tấn công vào C:\Users\Bob\AppData\Local\Temp
<img width="1914" height="1012" alt="image" src="https://github.com/user-attachments/assets/2a4dde78-d535-43ac-b43b-63fb4fd763ea" />

Q9 : It is believed that Karen was taunting a fellow computer expert through a bash script within the Documents directory. 
Who was the expert that Karen was taunting?
- Trong file /root/Documents/firstscript_fixed có đoạn lệnh in ra là **Young**
<img width="1204" height="628" alt="image" src="https://github.com/user-attachments/assets/b84a0bcc-d019-47f6-aac0-67bff79dc257" />

Q10 : A user executed the su command to gain root access multiple times at 11:26. Who was the user?
- Để tìm người đăng nhập vào root ta kiểm tra /var/log/auth.log : 
<img width="1362" height="984" alt="image" src="https://github.com/user-attachments/assets/0fcca39d-1745-453b-9964-8fdde587aa63" />

- Người đã đăng nhập và được cấp quyền root lúc 11:26 là user : **postgres**

Q11 : Based on the bash history, what is the current working directory?
<img width="1207" height="1010" alt="image" src="https://github.com/user-attachments/assets/ac77eb66-55a4-4bd6-b3f7-3a9d4770701b" />

- Thư mục hiện tại đang là /root/Documents/myfirsthack/
