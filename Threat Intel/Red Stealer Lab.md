# Red Stealer Lab 

Q1 : Categorizing malware enables a quicker and clearer understanding of its unique behaviors and attack vectors. What category has Microsoft identified for that malware in VirusTotal?
- Ta có thể thấy mối đe dọa này được phân loại vào : **Trojan**
<img width="1311" height="846" alt="image" src="https://github.com/user-attachments/assets/b8af04ea-34f9-48ab-bd32-5b9f4dd5d76f" />

Q2 : Clearly identifying the name of the malware file improves communication among the SOC team. What is the file name associated with this malware?
- Tệp tin được liên kết với phần mềm độc hại này là : **Wextract**
<img width="561" height="520" alt="image" src="https://github.com/user-attachments/assets/22c85055-e557-430a-9a4b-adaaa15618d5" />

Q3 : Knowing the exact timestamp of when the malware was first observed can help prioritize response actions.
Newly detected malware may require urgent containment and eradication compared to older, well-documented threats. What is the UTC timestamp of the malware's first submission to VirusTotal?
- Lần đầu tiên mối đe dọa được phát hiện là : **2023-10-06 04:41**
<img width="493" height="174" alt="image" src="https://github.com/user-attachments/assets/f58e5637-65fe-477a-a09b-64bf735144c0" />

Q4 : Understanding the techniques used by malware helps in strategic security planning. What is the MITRE ATT&CK technique ID for the malware's data collection from the system before exfiltration?
- Mã định danh (ID) cho quá trình thu thập dữ liệu của phần mềm độc hại từ hệ thống trước khi đánh cắp là : **T1005**
<img width="1255" height="602" alt="image" src="https://github.com/user-attachments/assets/958558a3-226f-440d-a88c-a99ab58dff29" />

Q5 : Following execution, which social media-related domain names did the malware resolve via DNS queries?
- Sau khi thực thi, phần mềm độc hại sẽ tiến hành phân giải tên miền cho một số tên miền, bao gồm cả **facebook.com.**
- Các đối tượng tấn công thường sử dụng các tên miền hợp pháp như facebook.com vì những tên miền này thường được người dùng truy cập và sự hiện diện của chúng trong lưu lượng mạng khó có thể gây nghi ngờ.
<img width="1090" height="851" alt="image" src="https://github.com/user-attachments/assets/00e77c92-f8cd-4988-831c-8c9c65504a99" />

Q6 : Once the malicious IP addresses are identified, network security devices such as firewalls can be configured to block traffic to and from these addresses. 
Can you provide the IP address and destination port the malware communicates with?
- Tìm trong phần IP Traffic ta có thể thấy được ip mà phần mềm độc hại đã liên lạc : **77.91.124.55:19071**
<img width="842" height="633" alt="image" src="https://github.com/user-attachments/assets/644a48b4-f916-44ac-b72d-12e8e568cc6a" />

Q7 : YARA rules are designed to identify specific malware patterns and behaviors. Using MalwareBazaar, what's the name of the YARA rule created by "Varp0s" that detects the identified malware?
- Quy tắc YARA do "Varp0s" tạo ra để phát hiện phần mềm độc hại đã được xác định có tên là **detect_Redline_Stealer**.
<img width="1288" height="427" alt="image" src="https://github.com/user-attachments/assets/991cdbb7-7547-4663-8a67-e56b44a733fc" />

Q8 :  Understanding which malware families are targeting the organization helps in strategic security planning for the future and prioritizing resources based on the threat. 
Can you provide the different malware alias associated with the malicious IP address?
- Sử dụng Malpedia để tìm bí danh của phần mềm được liên kết : **RECORDSTEALER**
<img width="1108" height="663" alt="image" src="https://github.com/user-attachments/assets/e0640281-ad3c-48e0-b298-6120393a8dc3" />

Q9 : By identifying the malware's imported DLLs, we can configure security tools to monitor for the loading or unusual usage of these specific DLLs. 
Can you provide the DLL utilized by the malware for privilege escalation?
- File DDL dùng để leo thang đặc quyền là : **ADVAPI32.dll**
<img width="1081" height="881" alt="image" src="https://github.com/user-attachments/assets/8998887b-25f9-4a67-ac79-2b0bbae828c5" />

