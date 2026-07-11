# BlueSky Ransomware Lab

Q1 : Knowing the source IP of the attack allows security teams to respond to potential threats quickly. Can you identify the source IP responsible for potential port scanning activity?
- Truy cập phần Endpoint ta có thể thấy IP : 87.96.21.84 thực hiện gửi nhiều packets mà không hoàn thành bắt tay 3 bước SYN nên IP : 87.96.21.84 là kẻ khả nghi nhất cho việc rà soát các cổng

Q2 : During the investigation, it's essential to determine the account targeted by the attacker. Can you identify the targeted account username?
- Sử dụng bộ lọc các gói tin TDS(Tabular Data Stream) để tìm kiếm thông tin đăng nhập. Ta có thể tìm thấy username được sử dụng để đăng nhập là : sa
<img width="393" height="322" alt="image" src="https://github.com/user-attachments/assets/e7fffda4-1ccc-4bf9-b42d-1ea41ec487a0" />

Q3 : We need to determine if the attacker succeeded in gaining access. Can you provide the correct password discovered by the attacker?
- Ở phần trên ta có thể thấy kẻ tấn công đã đăng nhập bằng cách sử dụng username : sa với password là : cyb3rd3f3nd3r$

Q4 : Attackers often change some settings to facilitate lateral movement within a network. What setting did the attacker enable to control the target host further and execute further commands?
- Sau khi đăng nhập kẻ tấn công đã sử dụng : xp_cmdshell để mở CMD 
<img width="712" height="322" alt="image" src="https://github.com/user-attachments/assets/ad22f60f-e58d-4ea0-96bd-7caac7827141" />

Q5 : Process injection is often used by attackers to escalate privileges within a system. What process did the attacker inject the C2 into to gain administrative privileges?
- Theo dõi các Event của máy chủ và lọc ra các Envent sử dụng PowerShell(400,600) ta có thể thấy kẻ tấn công đã cài đặt phần mềm khả nghi là : winlogon.exe
<img width="573" height="402" alt="image" src="https://github.com/user-attachments/assets/60a0817b-ea26-4a09-8bbf-e550c0e718bf" />

Q6 : Following privilege escalation, the attacker attempted to download a file. Can you identify the URL of this file downloaded?
- Lọc các gói giao thức HTTP ta follow theo gói .checkingps1 ta có thể biết được rằng URL : http://87.96.21.84/checking.ps1
<img width="229" height="52" alt="image" src="https://github.com/user-attachments/assets/fecca06d-eab9-4e34-8fbe-c9671b3f1612" />

Q7 : Understanding which group Security Identifier (SID) the malicious script checks to verify the current user's privileges can provide insights into the attacker's intentions. Can you provide the specific Group SID that is being checked?
- Trong gói giao thức trước ta có thể thấy kể tấn công đã kiểm tra group : S-1-5-32-544
<img width="915" height="374" alt="image" src="https://github.com/user-attachments/assets/6123b974-9eec-465c-ad39-a19aeee1ebe6" />

Q8 : Windows Defender plays a critical role in defending against cyber threats. If an attacker disables it, the system becomes more vulnerable to further attacks. What are the registry keys used by the attacker to disable Windows Defender functionalities? Provide them in the same order found.
- Vẫn trong gói giao thức trên ta có thể thấy rằng kẻ tấn công đã lần lượt vô hiệu hóa các tính năng của Windows Defender : DisableAntiSpyware,DisableRoutinelyTakingAction,DisableRealtimeMonitoring,SubmitSamplesConsent,SpynetReporting 
<img width="637" height="131" alt="image" src="https://github.com/user-attachments/assets/c8f23f1d-8342-442a-9a4a-5d811cd7b74e" />

Q9 : Can you determine the URL of the second file downloaded by the attacker?
- Trong giao thức trên kéo xuống dưới sẽ có thêm thông tin về file thứ 2 được tải xuống bởi kẻ tấn công là : http://87.96.21.84/del.ps1
<img width="805" height="132" alt="image" src="https://github.com/user-attachments/assets/11055a20-9ecd-4628-a6c9-fb9cbc1da21b" />

Q10 : Identifying malicious tasks and understanding how they were used for persistence helps in fortifying defenses against future attacks. What's the full name of the task created by the attacker to maintain persistence?
- Sau khi cài đặt file thứ 2 để tìm xem kẻ tấn công đã cài gì để duy trì sự hiện diện trên máy nạn nhân ta dùng bộ lọc : http contains "schtasks" để lọc các quá trình lặp lại : \Microsoft\Windows\MUI\LPUpdate
<img width="1089" height="214" alt="image" src="https://github.com/user-attachments/assets/3c8e4749-f3a1-45f9-b087-6ab8dc259a5c" />

Q11 : According to your analysis of the second malicious file, what is the MITRE ID of the tactic the file aims to achieve?
- 
