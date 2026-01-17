# WebStrike Lab

Q1 : Identifying the geographical origin of the attack facilitates the implementation of geo-blocking measures and the analysis of threat intelligence. From which city did the attack originate?
- Mở file WebStrike.pcap và lọc các gói GET bằng : http.request.method == GET. Ta có thể thấy hàng loạt request từ địa chỉ IP: 117.11.88.124
<img width="824" height="422" alt="image" src="https://github.com/user-attachments/assets/0c90e2b1-359e-4027-835e-6344b0020146" />

- Địa chỉ IP là ở : **Tianjin-China**

Q2 : Knowing the attacker's User-Agent assists in creating robust filtering rules. What's the attacker's Full User-Agent?

- Follow một gói tin bất kì ta có thể tìm thấy User-Agent : **Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0**
<img width="626" height="586" alt="image" src="https://github.com/user-attachments/assets/b26c17f2-c7ed-47a6-a47c-39ef9385c87c" />

Q3 : We need to determine if any vulnerabilities were exploited. What is the name of the malicious web shell that was successfully uploaded?

- Để tìm gói mà tin tặc đã upload thành công lên máy chủ ta lọc toàn bộ gói POST bằng : http.request.method == POST
<img width="880" height="510" alt="image" src="https://github.com/user-attachments/assets/a7e0db3f-2f44-4de5-a377-7c63e2ad6eac" />

- Ta thấy tin tặc đã upload 2 file nhưng kiểm tra sâu hơn thì có 1 file upload không thành công do sai định dạng. Sau đó tin tặc đã upload lần 2 với filename là: **image.jpg.php**
<img width="550" height="514" alt="image" src="https://github.com/user-attachments/assets/d1456a7c-cd79-4c9b-ba34-01706f0ac23c" />

Q4 : Identifying the directory where uploaded files are stored is crucial for locating the vulnerable page and removing any malicious files. Which directory is used by the website to store the uploaded files?

- Ngay trong gói POST đã có địa chỉ mà tin tặc đã tải lên : **/reviews/uploads/** 
<img width="843" height="519" alt="image" src="https://github.com/user-attachments/assets/9270b156-969a-4fd3-bd7c-ab014ce2fe07" />

Q5 : Which port, opened on the attacker's machine, was targeted by the malicious web shell for establishing unauthorized outbound communication?

- Trong gói POST tin tặc đã chèn lệnh PHP và giao tiếp ra ngoài nhờ cổng **8080**
- <img width="549" height="512" alt="image" src="https://github.com/user-attachments/assets/aeef3786-6313-4f8b-a208-04b1490ab881" />

Q6 : Recognizing the significance of compromised data helps prioritize incident response actions. Which file was the attacker attempting to exfiltrate?

- Bắt giữ lưu lượng truy cập đi ra từ máy chủ nạn nhân **24.49.63.79** đến máy của kẻ tấn công trên cổng **8080** bằng cách filter : (tcp.port==8080) && (ip.src==24.49.63.79)
<img width="552" height="512" alt="image" src="https://github.com/user-attachments/assets/48954731-ebcf-490b-82fd-af7cee21bb95" />

- Ta có thể thấy kẻ tấn công đang lấy cắp tệp tin : **passwd**
