# PoisonedCredentials Lab

Q1 : In the context of the incident described in the scenario, the attacker initiated their actions by taking advantage of benign network traffic from legitimate machines. 
Can you identify the specific mistyped query made by the machine with the IP address 192.168.232.162?
- Sử dụng bộ lọc hiển thị của Wireshark để phân lập lưu lượng LLMNR từ địa chỉ IP 192.168.232.162.
<img width="1134" height="352" alt="image" src="https://github.com/user-attachments/assets/792cf5e5-04d6-41d6-9727-b6e011b12bfa" />
- Ta thấy câu truy vấn bị sai là : **fileshaare**

Q2 : We are investigating a network security incident. To conduct a thorough investigation, We need to determine the IP address of the rogue machine.
What is the IP address of the machine acting as the rogue entity?
- Ta tìm các giao tiếp với địa chỉ IP: 192.168.232.162 để xác định đâu là máy đóng vai trò giả mạo : **192.168.232.215**
<img width="1726" height="638" alt="image" src="https://github.com/user-attachments/assets/5fe8342b-d6df-4b8c-8b93-d4a8766e2d41" />

Q3 : As part of our investigation, identifying all affected machines is essential. What is the IP 
address of the second machine that received poisoned responses from the rogue machine?
- Ta sử dụng filler : nbns.addr==192.168.232.215 để lọc các gói tin NBNS (NetBIOS Name Service) có liên quan đến địa chỉ IP 192.168.232.215
<img width="1739" height="605" alt="image" src="https://github.com/user-attachments/assets/0c881784-a40c-42e7-982f-ce74fc0bdf0d" />
- Ta xác định được IP : **192.168.232.176**

Q4 : We suspect that user accounts may have been compromised. To assess this, we must determine the username associated with the compromised account. 
What is the username of the account that the attacker compromised?
- Để xác định tên người dùng liên kết với tài khoản bị xâm phạm ta bắt đầu bằng cách phân tích lưu lượng mạng hướng đến máy tính độc hại.
- Bộ lọc Wireshark ip.dst==192.168.232.215 được áp dụng để cô lập tất cả lưu lượng truy cập có địa chỉ IP đích tương ứng với máy tính độc hại, 192.168.232.215. 
