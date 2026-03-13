# GrabThePhisher Lab

Analyze a cryptocurrency phishing kit to identify exfiltration methods, extract critical IOCs, and gather threat actor intelligence using local logs and Telegram APIs.

Q1 : Which wallet is used for asking the seed phrase?
- Ta có thể tìm thấy 1 loại ví là : **metamask**

Q2 : What is the file name that has the code for the phishing kit? 
- Do sử dụng ví metamask nên kẻ tấn công đã lợi dụng điều đó để tạo ra : **metamask.php** để không bị nghi ngờ
<img width="937" height="210" alt="image" src="https://github.com/user-attachments/assets/926bdf27-d19f-49ce-a904-aebe563d4c64" />

Q3 : In which language was the kit written?
- PHP

Q4 : What service does the kit use to retrieve the victim's machine information?
- Kẻ tấn công đã sử dụng **sypex geo** để gửi địa chỉ IP của nạn nhân được lấy động thông qua các biến máy chủ đến điểm cuối Sypex Geo.
  <img width="1011" height="205" alt="image" src="https://github.com/user-attachments/assets/4af9788c-88c9-4b2e-9ef7-3ce5d00f19fe" />

Q5 : How many seed phrases were already collected?
- Cụm từ "seed" là một thành phần bảo mật quan trọng đối với ví tiền điện tử, bao gồm 12 hoặc 24 từ cho phép người dùng khôi phục quyền truy cập vào ví và tài sản của họ.
- Kiểm tra file log.txt ta thấy có 3 mục điều đó có nghĩa là 3 nạn nhân đã mắc bẫy
<img width="968" height="301" alt="image" src="https://github.com/user-attachments/assets/7339c2ff-02c6-48ad-bec8-a83fb44b1bcf" />

Q6 : Could you please provide the seed phrase associated with the most recent phishing incident? 
- Các hạt giống liên quan đến sự cố gần nhất là : **father also recycle embody balance concert mechanic believe owner pair muffin hockey**

Q7 : Which medium had been used for credential dumping?
- Trang được sử dụng để bán thông tin người dùng là : **Telegram**
<img width="1482" height="254" alt="image" src="https://github.com/user-attachments/assets/12cd046a-9c50-4982-aeb7-392fe8d98c35" />

Q8 : What is the token for the channel? 
- Token của kênh telegram là : **5457463144:AAG8t4k7e2ew3tTi0IBShcWbSia0Irvxm10**
<img width="1394" height="264" alt="image" src="https://github.com/user-attachments/assets/048c6544-4353-4ee4-934c-f436130e871a" />

Q9 : What is the Chat ID for the phisher's channel?
- Chat ID của kẻ lừa đảo là : **5442785564**
<img width="1391" height="253" alt="image" src="https://github.com/user-attachments/assets/25796bf9-6f95-430f-8b30-7ad18c20f80f" />

Q10 : What are the allies of the phish kit developer?
- Trong đoạn code ta thấy có phần comment : **j1j1b1s@m3r0**
<img width="650" height="231" alt="image" src="https://github.com/user-attachments/assets/807622e5-e3e3-4964-811b-f73f397cd418" />
