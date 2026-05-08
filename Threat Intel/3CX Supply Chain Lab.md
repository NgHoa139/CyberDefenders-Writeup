# 3CX Supply Chain Lab

Q1 : Understanding the scope of the attack and identifying which versions exhibit malicious behavior is crucial for making informed decisions if these compromised versions are present in the organization. How many versions of 3CX running on Windows have been flagged as malware?
- Có 2 phiên bản được sử dụng trên Windows là **18.12.416** và **18.12.416**. Ta có thể tìm được thông tin về malware từ các nhà cung cấp bảo mật :
<img width="1523" height="634" alt="image" src="https://github.com/user-attachments/assets/aa4b76a3-10f1-471c-a61a-7bf5244d11b4" />


Q2 : Determining the age of the malware can help assess the extent of the compromise and track the evolution of malware families and variants. What's the UTC creation time of the .msi malware?
- Truy cập phền Details trong VirusTotal ta có thể tìm được thời gian tạo phần mềm là : **2023-03-13 06:33:26 UTC**
<img width="628" height="193" alt="image" src="https://github.com/user-attachments/assets/7a793e9b-fa24-450b-9c88-fe1fdf85e9b9" />


Q3 : Executable files (.exe) are frequently used as primary or secondary malware payloads, while dynamic link libraries (.dll) often load malicious code or enhance malware functionality. 
Analyzing files deposited by the Microsoft Software Installer (.msi) is crucial for identifying malicious files and investigating their full potential. Which malicious DLLs were dropped by the .msi file?
- Để tìm xem file .dll nào đã được cài vào máy ta kiểm tra Relations trên VirusTotal. Ta có thể thấy có 2 tệp dll là: **ffmpeg.dll, d3dcompiler_47.dll**
<img width="1084" height="720" alt="image" src="https://github.com/user-attachments/assets/ead5ca82-fa67-42b0-9107-ecd7debdc21f" />

Q4 : Recognizing the persistence techniques used in this incident is essential for current mitigation strategies and future defense improvements. What is the MITRE Technique ID employed by the .msi files to load the malicious DLL?
- Để kiểm tra MITRE của malware này ta có thể tìm thông tin trong Behavior của VirusTotal. Kĩ thuật MITRE để tải các file dll độc hại là : **T1574** 
<img width="1766" height="594" alt="image" src="https://github.com/user-attachments/assets/6627a274-4803-461e-b565-9b8671243b8c" />

Q5 : Recognizing the malware type (threat category) is essential to your investigation, as it can offer valuable insight into the possible malicious actions you'll be examining. What is the threat category of the two malicious DLLs?
- Ta có thể thấy 2 file dll là loại : **Trojan** 
<img width="1906" height="954" alt="image" src="https://github.com/user-attachments/assets/64274241-47d8-4d94-b4cd-5f957404d531" />

Q6 : As a threat intelligence analyst conducting dynamic analysis, it's vital to understand how malware can evade detection in virtualized environments or analysis systems. 
This knowledge will help you effectively mitigate or address these evasive tactics. What is the MITRE ID for the virtualization/sandbox evasion techniques used by the two malicious DLLs?
<img width="1768" height="600" alt="image" src="https://github.com/user-attachments/assets/246b3c03-7c7d-448d-8df3-5e8aaa37f58e" />

- Ta có thể thấy phần Virtualization/Sandbox Evasion của 2 file dll được sử dụng để tránh máy ảo là : **T1497**

Q7 : When conducting malware analysis and reverse engineering, understanding anti-analysis techniques is vital to avoid wasting time. Which hypervisor is targeted by the anti-analysis techniques in the ffmpeg.dll file?
- Kiểm tra kĩ file ffmpeg.dll ta thấy file có khả năng nhận biết và chống phân tích trên máy ảo : **VMware**
  <img width="515" height="303" alt="image" src="https://github.com/user-attachments/assets/79f11d00-d24b-408b-ad3f-9ba14ee8acd8" />

Q8 : Identifying the cryptographic method used in malware is crucial for understanding the techniques employed to bypass defense mechanisms and execute its functions fully. What encryption algorithm is used by the ffmpeg.dll file?
- Trong Behavior của file ffmpeg.dll ta thấy phần mã hóa file sử dụng : **RC4** 
<img width="432" height="210" alt="image" src="https://github.com/user-attachments/assets/bcab85ee-3104-4475-8e03-fa52c8110039" />

Q9 : As an analyst, you've recognized some TTPs involved in the incident, but identifying the APT group responsible will help you search for their usual TTPs and uncover other potential malicious activities. Which group is responsible for this attack?
- Về nhóm tội phạm tấn công ta có thể tra cứu trên Internet và nhóm đã thực hiện tấn công 3CX là : **Lazarus** 
<img width="670" height="446" alt="image" src="https://github.com/user-attachments/assets/a050a9b8-19d0-49c3-a4fd-40b5c4eff343" />
