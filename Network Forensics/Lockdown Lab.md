# Lockdown Lab

Q1 : After flooding the IIS host with rapid-fire probes, the attacker reveals their origin. Which IP address generated this reconnaissance traffic?
- Sử dụng Converstation để kiểm tra các kết nối ta thấy địa chỉ IP : **10.0.2.4** đã gửi hành loạt packets đến máy chủ 
<img width="1292" height="866" alt="image" src="https://github.com/user-attachments/assets/9166a79c-3521-475a-ae0b-0ed185ef9a75" />

Q2 : Zeroing in on a single open service to gain a foothold, the attacker carries out targeted enumeration. Which MITRE ATT&CK technique ID covers this activity?
- Kẻ tấn công lợi dụng tấn công qua network nên là ID của MITRE là : **T1046**
<img width="656" height="341" alt="image" src="https://github.com/user-attachments/assets/41954ec4-ee05-4547-ac39-e20936128ba1" />

Q3 : While reviewing the SMB traffic, you observe two consecutive Tree Connect requests that expose the first shares the intruder probes on the IIS host. Which two full UNC paths are accessed?
- Để kiểm tra ta lọc các gói SMB2 để kiểm tra và ta tìm được 2 đường dẫn UNC của kẻ xâm nhập đã truy cập : **\\10.0.2.15\Documents, \\10.0.2.15\IPC$**
<img width="615" height="68" alt="image" src="https://github.com/user-attachments/assets/d0731574-9a36-48fa-923b-8df269a33475" />

Q4 : Inside the share, the attacker plants a web-accessible payload that will grant remote code execution. What is the filename of the malicious file they uploaded, and what byte length is specified in the corresponding SMB2 Write Request?
- Vẫn kiểm tra các gói SMB2 ta có thể tìm thấy file được tải ;lên là : **shell.aspx** với độ dài : **1015024**
<img width="773" height="955" alt="image" src="https://github.com/user-attachments/assets/767b3c23-9961-4881-aee4-5f65e89a32cd" />

Q5 : The newly planted shell calls back to the attacker over an uncommon but firewall-friendly port. Which listening port did the attacker use for the reverse shell?
- Ta phân tích file : shell.aspx và dịch ngược thì ta biết được là cổng được kết nối là : 4443
<img width="1278" height="1027" alt="image" src="https://github.com/user-attachments/assets/47fc2a0f-9fb9-4cd0-b8d9-21f49662b3ea" />

Q6 : 
<img width="1099" height="61" alt="image" src="https://github.com/user-attachments/assets/9710c4d2-08aa-4643-bac7-a386c22843a9" />

Q7 : 
<img width="1109" height="589" alt="image" src="https://github.com/user-attachments/assets/87a56139-5846-4633-8f5b-cf275a7c8995" />

Q8 : 
<img width="1106" height="557" alt="image" src="https://github.com/user-attachments/assets/7f6166e8-bac3-47c6-8d2d-356802b67632" />

