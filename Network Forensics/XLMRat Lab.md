# XLMRat Lab

Q1 : The attacker successfully executed a command to download the first stage of the malware. What is the URL from which the first malware stage was installed?
- File đàu tiên được tải xuống là : mdm.jpg (http://45.126.209.4:222/mdm.jpg)
  <img width="753" height="553" alt="image" src="https://github.com/user-attachments/assets/5bfb10c7-2a49-428c-826a-41ffeb7bff8f" />

Q2 : Which hosting provider owns the associated IP address?
- Kiểm tra IP của máy kẻ tấn công trên whois ta có : **reliablesite.net**
<img width="748" height="254" alt="image" src="https://github.com/user-attachments/assets/67a64e2c-96f7-411d-8577-193f30b1aefc" />

Q3 : By analyzing the malicious scripts, two payloads were identified: a loader and a secondary executable. What is the SHA256 of the malware executable?
- Trích xuất giá trị của biến $hexString_bbb và tính qua mã SHA-256 : 1eb7b02e18f67420f42b1d94e74f3b6289d92672a0fb1786c30c03d68e81d798

Q4 : What is the malware family label based on Alibaba?
- Từ mã SHA-256 ta đưa malware lên VirusTotal
<img width="1308" height="852" alt="image" src="https://github.com/user-attachments/assets/ec72886c-f74f-4d25-a351-0b8bd7f4bac0" />

- Nhãn phân loại phần mềm độc hại dựa trên Alibaba là : **AsyncRat**

Q5 : What is the timestamp of the malware's creation?
- Thời gian tạo là : 2023-10-30 15:08
<img width="475" height="172" alt="image" src="https://github.com/user-attachments/assets/baf64445-a069-4ed0-b47a-f0951d4e438c" />

Q6 : Which LOLBin is leveraged for stealthy process execution in this script? Provide the full path.
- C:\Windows\Microsoft.NET\Framework\v4.0.30319\RegSvcs.exe

Q7 : The script is designed to drop several files. List the names of the files dropped by the script.
- 3 files bị bỏ qua là : Conted.bat, Conted.ps1, Conted.vbs
<img width="742" height="484" alt="image" src="https://github.com/user-attachments/assets/79cd2dd3-5f77-428d-8ae6-0924809dc26b" />
