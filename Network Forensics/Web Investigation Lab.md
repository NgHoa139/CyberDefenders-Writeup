# Web Investigation Lab

Q1 : By knowing the attacker's IP, we can analyze all logs and actions related to that IP and determine the extent of the attack, the duration of the attack, and the techniques used. 
Can you provide the attacker's IP?
- Kiểm tra phần Conversations để xác định những IP đã giao tiếp với máy chủ. Ta có thể thấy IP : ```111.224.250.131``` đã gửi tới 88,484 packets nên ta có thể biết được địa chỉ IP của kẻ tấn công 
<img width="1913" height="783" alt="image" src="https://github.com/user-attachments/assets/d348e939-00b2-403d-b8be-b37a79278b88" />

Q2 : If the geographical origin of an IP address is known to be from a region that has no business or expected traffic with our network, this can be an indicator of a targeted attack.
Can you determine the origin city of the attacker?
- Ta kiểm tra IP của kẻ tấn công trên IP Location ta có thể thấy rằng kẻ tấn công đến từ : ```Shijiazhuang```
<img width="1061" height="296" alt="image" src="https://github.com/user-attachments/assets/6dc62501-7ead-44ff-8b21-13c2dd786f42" />

Q3 : Identifying the exploited script allows security teams to understand exactly which vulnerability was used in the attack. This knowledge is critical for finding the appropriate patch or workaround to close the security gap and prevent future exploitation.
Can you provide the vulnerable PHP script name?
- Khi sử dụng WireShark để phân tích gói .pcap ta có thể tìm thấy hàng loạt tên của file : ```search.php```
<img width="1899" height="745" alt="image" src="https://github.com/user-attachments/assets/1a528dd5-0500-41ef-8691-6d8e7bc381f9" />

Q4 : Establishing the timeline of an attack, starting from the initial exploitation attempt, what is the complete request URI of the first SQLi attempt by the attacker?
- Ta có thể dễ dàng tìm kiếm từ những thông tin ta có được ở trên. Ta thấy ở gói tin 357 kẻ tấn công đã sử dụng :```/search.php?search=book%20and%201=1;%20--%20-``` Decode ra ta sẽ được :```/search.php?search=book and 1=1; -- -```
<img width="1868" height="721" alt="image" src="https://github.com/user-attachments/assets/5c9532fc-f379-45a5-9b11-69a854776c15" />

Q5 : Can you provide the complete request URI that was used to read the web server's available databases?
- Ta lưu toàn bộ các gói tin liên quan đến search.php về dưới dạng plain text là bắt đầu decode toàn bộ file để tìm :
<img width="1438" height="217" alt="image" src="https://github.com/user-attachments/assets/edcba769-d7f2-4b73-b91d-6c5c0637e7f2" />

- Ta có thể tìm thấy dòng lệnh : ```/search.php?search=book' UNION ALL SELECT NULL,CONCAT(0x7178766271,JSON_ARRAYAGG(CONCAT_WS(0x7a76676a636b,schema_name)),0x7176706a71) FROM INFORMATION_SCHEMA.SCHEMATA-- -```

Q6 : Assessing the impact of the breach and data access is crucial, including the potential harm to the organization's reputation. What's the table name containing the website users data?
- Kiểm tra câu lệnh SQL(packet: 1525) đã bị tấn công ta có thể thấy dữ liệu được trả về là tên của các bảng :
<img width="1283" height="547" alt="image" src="https://github.com/user-attachments/assets/4fd755c8-50f0-441d-b890-71cf77910132" />

- Tiếp tục tìm các câu lệnh đã tấn công vào các bảng. Ta có thể thấy trong câu lệnh tên công vào bảng :
<img width="1282" height="651" alt="image" src="https://github.com/user-attachments/assets/1d79c71a-8bdc-47f7-8828-3f6440c421b0" />

- Ta có thể thấy bảng dữ liệu : ```customers``` đã trả về toàn bộ dữ liệu của người dùng

Q7 : The website directories hidden from the public could serve as an unauthorized access point or contain sensitive functionalities not intended for public access. 
Can you provide the name of the directory discovered by the attacker?
- Để tìm tên thư mục bị lợi dụng để tấn công ta sử dụng Filter để lọc ra các gói POST : ```http.request.method == POST```
- Tiếp đó ta có thể thấy phần Referer có đường dẫn : ```/admin/```
  <img width="1903" height="861" alt="image" src="https://github.com/user-attachments/assets/0a24505b-8057-4e0e-843e-bfc50bd864b0" />

Q8 : Knowing which credentials were used allows us to determine the extent of account compromise. What are the credentials used by the attacker for logging in?
- Kiểm tra phần login thì ta có thể biết được username và password là : ```admin:admin123!```
<img width="971" height="826" alt="image" src="https://github.com/user-attachments/assets/d8a6aacc-0b11-4853-8c40-9d8eaa5d5ac8" />

Q9 : We need to determine if the attacker gained further access or control on our web server. What's the name of the malicious script uploaded by the attacker?
- Kiểm tra gói tin sau khi kẻ tấn công đã truy cập được vào máy chủ. Ta có thể thấy file mà kẻ tấn công đã tải lên là : ```NVri2vhp.php```
<img width="728" height="645" alt="image" src="https://github.com/user-attachments/assets/02780427-590e-4843-9b4a-f60bc6fbb0a6" />
 
