# HawkEye Lab

Q1 : How many packets does the capture have?
- Mở file .pcap bằng Wireshark ta có : 4003 packets

Q2 : At what time was the first packet captured (UTC)?
- Ta có thể thấy packet đầu tiên vào lúc : 2019-04-10 20:37
<img width="560" height="120" alt="image" src="https://github.com/user-attachments/assets/a4c3cf2c-9fde-4007-827f-b16db51e2b7a" />

Q3 : What is the duration of the capture?
- Mở phần Properties của file pcap ta có thời gian là : 01:03:41
<img width="339" height="95" alt="image" src="https://github.com/user-attachments/assets/085205f0-6631-42d7-a3cc-9662e9fa01f8" />

Q4 : What is the most active computer at the link level?
- Ta vào phần Ethernet của Converstations ta có thể thấy máy hoạt động nhiều ở : 00:08:02:1c:47:ae
<img width="1051" height="152" alt="image" src="https://github.com/user-attachments/assets/fb0ff9ab-49c1-421f-ae69-f3d581fae5f9" />

Q5 : Manufacturer of the NIC of the most active system at the link level?
- Ta tra địa chỉ MAC của nhà cung cấp ta có : **Hewlett-Packard**
<img width="857" height="534" alt="image" src="https://github.com/user-attachments/assets/a26b6fa3-e86c-4c1d-ae60-17e35d0f12d0" />

Q6 : Where is the headquarter of the company that manufactured the NIC of the most active computer at the link level?
- Trụ ở chính ở :  Palo Alto

Q7 : The organization works with private addressing and netmask /24. How many computers in the organization are involved in the capture?
- Có 3 máy có địa chỉ IP riêng là : 10.4.10.2, 10.4.10.4, 10.4.10.132
<img width="582" height="248" alt="image" src="https://github.com/user-attachments/assets/bce98dec-8f5c-4285-b895-47b2b809fde7" />

Q8 : What is the name of the most active computer at the network level?
- Sử dụng filter để tìm DHCP của 10.4.10.132 ta có tên PC là : Beijing-5cd1-PC 
<img width="368" height="142" alt="image" src="https://github.com/user-attachments/assets/63f69091-4253-4e49-a3b4-c50471111d75" />

Q9 : What is the IP of the organization's DNS server?
- IP của nhà tổ chức là : 10.4.10.4
<img width="536" height="120" alt="image" src="https://github.com/user-attachments/assets/e27c22b8-a294-4304-8c7e-71cbee51e346" />

Q10 : What domain is the victim asking about in packet 204?
- Domain được tìm kiếm trong packet 204 là : proforma-invoices.com

Q11 : What is the IP of the domain in the previous question?
- Ta tìm kiếm phần response của trang web proforma-invoices.com và ta có IP của tên miền trước đấy là : 217.182.138.150
<img width="507" height="124" alt="image" src="https://github.com/user-attachments/assets/a183e989-e0ad-433c-85bd-b9a1c23d56f3" />

Q12 : Indicate the country to which the IP in the previous section belongs.
- Tra cứu thông tin IP 217.182.138.150 ta biết được IP được tìm thấy ở : France

Q13 : What operating system does the victim's computer run?
- Kiểm tra User-Agent của máy nạn nhân bằng cách tìm các packet HTTP : **Windows NT 6.1**
<img width="814" height="245" alt="image" src="https://github.com/user-attachments/assets/9bd94672-3965-4bcb-a2b5-4a173b68644c" />

Q14 : What is the name of the malicious file downloaded by the accountant?
- Ta Export HTTP ta sẽ tìm được file tải về là : ```tkraw_Protected99.exe```
<img width="754" height="554" alt="image" src="https://github.com/user-attachments/assets/6cb1abac-cb8c-48a3-8cd0-ecd4230a8727" />

Q15 : What is the md5 hash of the downloaded file?
- Sau khi Export file ```tkraw_Protected99.exe``` ta tính toán MD5 : 71826BA081E303866CE2A2534491A2F7

Q16 : What software runs the webserver that hosts the malware?
- Ta tìm kiếm thông tin ở Header của gói tin download malware : **LiteSpeed**
<img width="626" height="301" alt="image" src="https://github.com/user-attachments/assets/717186b6-ac9c-4491-91a3-8f6aacabd79f" />

Q17 : What is the public IP of the victim's computer?
- Sau khi tải xuống malware máy nạn nhân đã thực hiện giao tiếp với máy chủ của kẻ tấn công và trả về : 173.66.146.112
<img width="764" height="127" alt="image" src="https://github.com/user-attachments/assets/6442d574-c9f4-4782-abf7-0e7afb6817b6" />

Q18 : In which country is the email server to which the stolen information is sent?
- Lọc các gói SMTP ta có thể thấy các gói tin email được gửi đến IP : 23.229.162.69. Ta tra thông tin là ở **United States**

Q19 : Analyzing the first extraction of information. What software runs the email server to which the stolen data is sent?
- Từ response của máy chủ ta có thể thấy máy chủ đang sử dụng : Exim 4.91
<img width="845" height="163" alt="image" src="https://github.com/user-attachments/assets/0e3057e6-4c72-4ee4-a051-81b9270bf833" />

Q20 : What is the password used by the malware to send the email?
- Ta kiểm tra trong gói SMTP thì thấy thông tin được gửi đến địa chỉ : ```sales.del@macwinlogistics.in```

Q21 : What is the password used by the malware to send the email?
- Ta follow TCP gói tin ta thấy được các chuỗi mã hóa Base64 : Sales@23
<img width="371" height="121" alt="image" src="https://github.com/user-attachments/assets/d6199e59-cd49-45fe-bd91-63403ba45f42" />

Q22 : Which malware variant exfiltrated the data?
- Follow gói tin email ta có thể thấy được phần mềm : Reborn v9

Q23 : What are the bankofamerica access credentials? (username:password)
- Decode toàn bộ ta sẽ được thông tin : roman.mcguire:P@ssw0rd$
<img width="628" height="222" alt="image" src="https://github.com/user-attachments/assets/25c9de55-0cea-4048-9935-d63d7e261d0d" />

Q24 : Every how many minutes does the collected data get exfiltrated?
- Ta có thể thấy thời gian giữa 2 email được gửi là : 10 phút
