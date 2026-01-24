# Yellow RAT Lab

Q1 : Understanding the adversary helps defend against attacks. What is the name of the malware family that causes abnormal network traffic?
- Tìm kiếm thông tin về malware Yellow RAT ta có thể thấy tên đầy đủ của malware này là : **Yellow Cockatoo RAT**

Q2 : As part of our incident response, knowing common filenames the malware uses can help scan other workstations for potential infection. 
What is the common filename associated with the malware discovered on our workstations?
- Truy cập phần Details của VirusTotal để tìm kiếm ta có thể thấy tên tệp là : **111bc461-1ca8-43c6-97ed-911e0e69fdf8.dll**
  <img width="640" height="285" alt="image" src="https://github.com/user-attachments/assets/f320243c-280d-4dcf-ac7b-54f1a91a00ff" />

Q3 : Determining the compilation timestamp of malware can reveal insights into its development and deployment timeline. What is the compilation timestamp of the malware that infected our network?
- Thời điểm báo cáo đầu tiên của báo cáo về malware này là : **2020-09-24 18:26**
<img width="476" height="168" alt="image" src="https://github.com/user-attachments/assets/9029f498-4820-4072-b6c3-a8f420ee3981" />

Q4 : Understanding when the broader cybersecurity community first identified the malware could help determine 
how long the malware might have been in the environment before detection. When was the malware first submitted to VirusTotal?

- Từ phần History ở trên ta có thể biết lần đầu tiên malware được phát hiện là : **2020-10-15 02:47**

Q5 : To completely eradicate the threat from Industries' systems, we need to identify all components dropped by the malware.
What is the name of the .dat file that the malware dropped in the AppData folder?
- Tìm kiếm thông tin trên internet ta có được : **solarmarker.dat**
 <img width="772" height="364" alt="image" src="https://github.com/user-attachments/assets/14b17f7f-bc78-47ad-a06a-d36a55bcf4ae" />

Q6 : It is crucial to identify the C2 servers with which the malware communicates to block its communication and prevent further data exfiltration. 
What is the C2 server that the malware is communicating with?
- Vào phần Behavior trên VirusTotal và tìm kiếm phần Network Communications để tìm kiếm xem máy đã kết nối với máy chủ C2 nào
  <img width="773" height="613" alt="image" src="https://github.com/user-attachments/assets/29d1dc2a-131e-421e-8b35-0e3af53d61f5" />

- Ta có thể thấy phần mềm độc hại đang liên lạc với máy chủ : **https://gogohid.com**
