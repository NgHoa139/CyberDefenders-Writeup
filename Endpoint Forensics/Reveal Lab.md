# Reveal Lab 

Q1 : Identifying the name of the malicious process helps in understanding the nature of the attack. What is the name of the malicious process?
- Sử dụng Volatility3 để liệt kê các danh sách tiến trình đã được chạy ta được :
<img width="1639" height="283" alt="image" src="https://github.com/user-attachments/assets/27aa54bf-43a0-44e5-933f-913c454ed7ad" />

- Ta có thể thấy rõ ràng tiến trình **powershell.exe** là tiến trình đáng nghi ngờ

Q2 : Knowing the parent process ID (PPID) of the malicious process aids in tracing the process hierarchy and understanding the attack flow. What is the parent PID of the malicious process?
- Từ phần PsList ở trên ta có thể thấy PPID của quá trình đáng ngờ là : **4120**

Q3 : Determining the file name used by the malware for executing the second-stage payload is crucial for identifying subsequent malicious activities. 
What is the file name that the malware uses to execute the second-stage payload?
- Để kiểm tra câu lệnh được sử dụng sau khi chạy quá trình powershell.exe thì ta dùng cmdline của Volatility3 : **3435.dll**
<img width="1859" height="194" alt="image" src="https://github.com/user-attachments/assets/f7c07642-d784-4910-b39b-a74a9ef7da05" />

Q4 : Identifying the shared directory on the remote server helps trace the resources targeted by the attacker. What is the name of the shared directory being accessed on the remote server?
- Ta có thể thấy quá trình net.exe đã truy cập vào thư mục : **davwwwroot**
<img width="1860" height="192" alt="image" src="https://github.com/user-attachments/assets/bee7224d-3f02-4eab-8621-adbfdf354254" />

Q5 : What is the MITRE ATT&CK sub-technique ID that describes the execution of a second-stage payload using a Windows utility to run the malicious file?
- Hành vi của kẻ tấn công là chạy lệnh trên : rundll32 ta có thể tra cứu MITRE ID của nó là : **T1218.011**
<img width="1355" height="576" alt="image" src="https://github.com/user-attachments/assets/d87d36a7-de90-4313-b6cd-7a6b69430bbe" />

Q6 : Identifying the username under which the malicious process runs helps in assessing the compromised account and its potential impact.
What is the username that the malicious process runs under?
- Để tìm tên người dùng mà bị tấn công ta sử dụng getsid và lọc các id liên quan đến 3692. Ta có thể thấy người dùng là : **Elon**
<img width="1216" height="391" alt="image" src="https://github.com/user-attachments/assets/27cff2cf-2011-4632-a03a-38e8eabfb9c2" />

Q7 : Knowing the name of the malware family is essential for correlating the attack with known threats and developing appropriate defenses. What is the name of the malware family?
- Ta đưa địa chỉ IP của kẻ tấn công lên VirusTotal ta có thể thấy : **StrelaStealer**
<img width="844" height="636" alt="image" src="https://github.com/user-attachments/assets/6d5c5fe9-a702-41e2-9c29-87f393ebb9bd" />
