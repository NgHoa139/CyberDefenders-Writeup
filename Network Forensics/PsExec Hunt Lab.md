# PsExec Hunt Lab

Q1 : To effectively trace the attacker's activities within our network, can you identify the IP address of the machine from which the attacker initially gained access?
- Ta có thể thấy IP của kẻ tấn công là **10.0.0.130** vì lượng truy cập nhiều và thường xuyên
<img width="1031" height="238" alt="image" src="https://github.com/user-attachments/assets/d66fbef3-74ca-4742-a94b-0c4521f8e617" />

Q2 : To fully understand the extent of the breach, can you determine the machine's hostname to which the attacker first pivoted?
- Ta sử dụng bộ lọc để tìm các giao thức SMB2
<img width="1913" height="915" alt="image" src="https://github.com/user-attachments/assets/953b7f92-6ecd-4ef0-a3c6-9156db279228" />

- Ta có thể thấy Targer Name là : **SALES-PC**

Q3 : Knowing the username of the account the attacker used for authentication will give us insights into the extent of the breach. What is the username utilized by the attacker for authentication?
- Trong giao thức SMB2 ta có thể tìm thấy username là : **ssales**
<img width="1913" height="939" alt="image" src="https://github.com/user-attachments/assets/ba96c1c0-263b-4640-90b7-d2bc60d3b3a6" />

Q4 : After figuring out how the attacker moved within our network, we need to know what they did on the target machine. What's the name of the service executable the attacker set up on the target?
- Ta tìm các giao thức SMB đã được thực hiện :
<img width="751" height="550" alt="image" src="https://github.com/user-attachments/assets/72459448-c790-4a32-badd-c9578d72f69e" />

- Có thể thấy rằng tên của dịch vụ thực thi là : **psexesvc**

Q5 : We need to know how the attacker installed the service on the compromised machine to understand the attacker's lateral movement tactics. This can help identify other affected systems. 
Which network share was used by PsExec to install the service on the target machine?
- Sử dụng bộ lọc smb2.tree, tập trung vào thư mục chia sẻ quản trị mặc định thường được sử dụng để truy cập từ xa vào thư mục hệ thống Windows:
<img width="954" height="439" alt="image" src="https://github.com/user-attachments/assets/5a56a27f-0799-4f73-b8e5-c650bd63c4f1" />

Q6 : We must identify the network share used to communicate between the two machines. Which network share did PsExec use for communication?
- Kiểm tra hoạt động giao tiếp SMB trên các thư mục chia sẻ này và xem có tên tệp nào bao gồm stdout, stdin hoặc stderr hay không.
<img width="949" height="438" alt="image" src="https://github.com/user-attachments/assets/6e2be289-437d-477e-8968-e4b414592e65" />

Q7 :Now that we have a clearer picture of the attacker's activities on the compromised machine, it's important to identify any further lateral movement. 
What is the hostname of the second machine the attacker targeted to pivot within our network? 
- Sử dụng bộ lọc ntlmssp.challenge.target_name để xác định máy thứ hai mà kẻ tấn công nhắm mục tiêu :
<img width="1915" height="939" alt="image" src="https://github.com/user-attachments/assets/9394c2cf-53d7-4665-9402-8676608c9cfe" />

- Ta có thể thấy máy thứ 2 tấn công là: **Marketing-PC**
