# Oski Lab


Q1 : Determining the creation time of the malware can provide insights into its origin. What was the time of malware creation?
- Truy cập VirusTotal và tìm kiếm mã độc : 12c1842c3ccafe7408c23ebf292ee3d9
- Truy cập phần Detail ta có thể thấy mã độc được tạo ra vào lúc : **2022-09-28 17:40**
  <img width="608" height="136" alt="image" src="https://github.com/user-attachments/assets/4baaca59-b538-4422-bceb-b6bf58d902a8" />

Q2 : Identifying the command and control (C2) server that the malware communicates with can help trace back to the attacker. Which C2 server does the malware in the PPT file communicate with?
- Vào phần Relation để tìm máy chủ C2 mà phần mềm kết nối đến : **http://171.22.28.221/5c06c05b7b34e8e6.php**
  <img width="824" height="142" alt="image" src="https://github.com/user-attachments/assets/4ae3a5ff-453b-410b-a261-bc89618fe82d" />

Q3 : Identifying the initial actions of the malware post-infection can provide insights into its primary objectives. What is the first library that the malware requests post-infection?
- Để tìm thư viện đầu tiên mà phần mềm độc hại yêu cầu sau khi lây nhiễm ta truy cập vào Behavior :  
<img width="525" height="360" alt="image" src="https://github.com/user-attachments/assets/fee465d7-b100-4b26-956d-9daf1404b7bd" />

- Vậy là file : **sqlite3.dll**

Q4 : By examining the provided Any.run report, what RC4 key is used by the malware to decrypt its base64-encoded string?
- Truy cập Any.run và kiểm tra phần Malware Configuration : **5329514621441247975720749009**
<img width="612" height="449" alt="image" src="https://github.com/user-attachments/assets/770e00d1-9c83-4c3e-8679-571c9d1aa02b" />

Q5 : By examining the MITRE ATT&CK techniques displayed in the Any.run sandbox report, identify the main MITRE technique (not sub-techniques) the malware uses to steal the user’s password.
- Truy cập phần ATT&CK để tìm Credentials from Password Stores và kiểm tra xem MITRE chính là gì : **T1555**
  <img width="717" height="504" alt="image" src="https://github.com/user-attachments/assets/541771bb-492b-46aa-83ca-682986ddced6" />

Q6 : By examining the child processes displayed in the Any.run sandbox report, which directory does the malware target for the deletion of all DLL files?
- Ta tìm câu lệnh CMD mà kẻ tấn công đã thực hiện và thấy kẻ tấn công đã xóa : **C:\ProgramData**
- <img width="1394" height="580" alt="image" src="https://github.com/user-attachments/assets/72c24b95-f557-4854-91a2-80fefcef5a10" />

Q7 : Understanding the malware's behavior post-data exfiltration can give insights into its evasion techniques. By analyzing the child processes, after successfully exfiltrating the user's data, how many seconds does it take for the malware to self-delete?
- Ta có thể dễ dàng thấy được kẻ tấn công đã delay máy chủ **5 giây**
<img width="592" height="206" alt="image" src="https://github.com/user-attachments/assets/d5582d21-3808-4255-a60e-1611c034f5b8" />
