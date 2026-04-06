# RedLine Lab
As a member of the Security Blue team, your assignment is to analyze a memory dump using Redline and Volatility tools. Your goal is to trace the steps taken by the attacker on the compromised machine and determine how they managed to bypass the Network Intrusion Detection System (NIDS). Your investigation will identify the specific malware family employed in the attack and its characteristics. Additionally, your task is to identify and mitigate any traces or footprints left by the attacker.

Q1 : What is the name of the suspicious process?
- Ta sử dụng cung cụ volatility3 để liệt kê ra các quá trình có trong ổ đĩa :
<img width="1908" height="968" alt="image" src="https://github.com/user-attachments/assets/f1dead15-c15b-48af-8813-1675fbb5e99b" />
- Ta có thể thấy **oneetx.exe** là quá trình bất thường mới được chạy

Q2 : What is the child process name of the suspicious process?
- Sau khi chạy oneetx.exe thì quá trình đã sản sinh ra quá trình con là : **rundll32.exe**
<img width="1911" height="972" alt="image" src="https://github.com/user-attachments/assets/1c38f2e4-8bde-472a-9539-14e1030ae7cd" />

Q3 : What is the memory protection applied to the suspicious process memory region?
- Để tìm tính năng bảo vệ ta kiểm tra vùng bộ nhớ của tiến trình bằng : **vadinfor**
<img width="1917" height="956" alt="image" src="https://github.com/user-attachments/assets/74b89bb4-96ef-4ae5-a0c8-edfd36072c73" />

-  Ta thấy tệp có quyền : **PAGE_EXECUTE_READWRITE**

Q4 : What is the name of the process responsible for the VPN connection? 
- Để tìm quá trình kết nối VPN ta sử dụng psscan của volatility :
<img width="1915" height="974" alt="image" src="https://github.com/user-attachments/assets/6ed455c3-5b7d-487b-b639-1210e682d6e6" />

- Ta thấy quá trình sử dụng : **Outline.exe** để kết nối VPN

Q5 : What is the attacker's IP address?
- Để tìm IP của kẻ tấn công ta sử dụng : netscan
<img width="1899" height="142" alt="image" src="https://github.com/user-attachments/assets/09157d50-f587-4411-933c-3cefda9929a3" />

- Ta thấy : **77.91.124.20** chính là địa chỉ IP của kẻ tấn công

Q6 : What is the full URL of the PHP file that the attacker visited?
- Ta sử dụng strings để trích xuất các đường dẫn và để tìm nơi kẻ tấn công đã đến ta lọc Ip của kẻ tấn công : **http://77.91.124.20/store/games/index.php**
<img width="1325" height="629" alt="image" src="https://github.com/user-attachments/assets/c160ac41-f146-454b-aaf5-8ed66c9c5c61" />

Q7 : What is the full path of the malicious executable?
- Tệp nghi ngờ được ta phát hiện oneetx.exe có đường dẫn là : **C:\Users\Tammam\AppData\Local\Temp\c3912af058\oneetx.exe**
<img width="1897" height="123" alt="image" src="https://github.com/user-attachments/assets/9f8743b7-d3f3-4118-8adf-0293ac56f7df" />
