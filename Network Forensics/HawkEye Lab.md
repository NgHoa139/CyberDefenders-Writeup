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
- 
