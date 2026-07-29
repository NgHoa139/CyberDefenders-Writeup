# Silent Breach Lab

Q1 : What is the MD5 hash of the potentially malicious EXE file the user downloaded? 
- Sử dụng công cụ Exterro FTK Imager ta truy cập vài file .ad1
- Ở phần Dowload ta thấy có file .exe được tải là : IMF-Info.pdf.exe
<img width="304" height="334" alt="image" src="https://github.com/user-attachments/assets/900867d7-99b3-4eeb-be26-5bbcc3cc73a3" />

- Xuất file ra mã MD5 ta được : ```336a7cf476ebc7548c93507339196abb```

Q2 : What is the URL from which the file was downloaded?
- Để tìm ứng đã được sử dụng để tải về ta sử dụng FTK Image để tìm kiếm lịch sử của các ứng dụng web
<img width="1429" height="746" alt="image" src="https://github.com/user-attachments/assets/cb53466f-e6e6-4948-8c4e-74bb6c5d94c2" />

- Xuất file ra và kiểm tra file History thấy tệp độc hại được tải về từ : ```http://192.168.16.128:8000/IMF-Info.pdf.exe```

<img width="1095" height="82" alt="image" src="https://github.com/user-attachments/assets/e6976d85-44dc-4e69-a7c8-92237976b1cc" />

Q3 : What application did the user use to download this file?
- Từ phần trước phân tích ta biết được ứng dụng được sử dụng để tải về là : **Microsoft Edge**

Q4 : By examining Windows Mail artifacts, we found an email address mentioning three IP addresses of servers that are at risk or compromised. What are the IP addresses?
- Về cơ bản, tệp HxStore.hxd đóng vai trò như một cơ sở dữ liệu chứa các tin nhắn email, tệp đính kèm và siêu dữ liệu, tất cả được lưu trữ ở định dạng nhị phân, đòi hỏi các công cụ hoặc kỹ thuật chuyên dụng để truy cập.
- Ta tìm kiếm, xuất file và kiểm tra :
<img width="1430" height="749" alt="image" src="https://github.com/user-attachments/assets/07ee2661-b62f-4506-9894-5b116e21f74f" />

- Sử dụng strings và grep để bắt các địa chỉ IPv4 ta có : 145.67.29.88, 212.33.10.112, 192.168.16.128
<img width="1083" height="384" alt="image" src="https://github.com/user-attachments/assets/c19c83d7-f427-46dc-b073-f9aa1780fedf" />

Q5 : By examining the malicious executable, we found that it uses an obfuscated PowerShell script to decrypt specific files. What predefined password does the script use for encryption?
- Ta xuất file qua dạng .txt và tìm kiếm *powershell* :
<img width="1893" height="319" alt="image" src="https://github.com/user-attachments/assets/0a3594ef-ab21-42d8-9e59-aac3bf9bf9ec" />

- Trước khi mở lệnh ```powershell.exe``` ta có thể thấy trước đấy là 1 dãy kí tự được mã hóa Base64. Ta chạy thử đoạn mã trên :
<img width="1508" height="806" alt="image" src="https://github.com/user-attachments/assets/959898cf-8b3a-48ed-b4a3-cff77fdbfc07" />

- Ta có được : $password = "Imf!nfo#2025Sec$"

Q6 : After identifying how the script works, decrypt the files and submit the secret string.
