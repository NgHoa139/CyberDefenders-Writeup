# Ramnit Lab

Analyze a memory dump using Volatility to identify a malicious process, extract network IOCs, file hash, and compilation timestamp, correlating with external threat intelligence.

Q1 : What is the name of the process responsible for the suspicious activity?
- Sử dụng Volatility3 để quét pstree của file dump
- Hành động đáng nghi ngờ nhất là tải file **ChromeSetup.exe** và thực thi nó 
<img width="1474" height="709" alt="image" src="https://github.com/user-attachments/assets/ee390677-e84e-48f0-ad1b-3e9a8314d143" />

Q2 : What is the exact path of the executable for the malicious process?
- Địa chỉ của file nằm ở : **C:\Users\alex\Downloads\ChromeSetup.exe**
<img width="625" height="740" alt="image" src="https://github.com/user-attachments/assets/35783ea3-1a01-49ae-9196-e3cf54fb0e67" />

Q3 : Identifying network connections is crucial for understanding the malware's communication strategy. What IP address did the malware attempt to connect to?
- Để tìm kiếm địa chỉ IP mà máy kết nối đến ta sử dụng windows.netscan của Volatility : **58.64.204.181**
<img width="777" height="278" alt="image" src="https://github.com/user-attachments/assets/a084d746-9abb-4123-b6df-07cc80cf6495" />

Q4 : To determine the specific geographical origin of the attack, Which city is associated with the IP address the malware communicated with?
- Sử dụng IP Location để tìm kiếm địa chỉ IP : 58.64.204.181 ta có được kết quả là ở **Hong Kong** :
<img width="1051" height="372" alt="image" src="https://github.com/user-attachments/assets/424aa35e-2bf3-4fbe-a625-80bc1401a413" />

Q5 : Hashes serve as unique identifiers for files, assisting in the detection of similar threats across different machines. What is the SHA1 hash of the malware executable?
- Để tìm được mã SHA1 của file ta phải tìm kiếm địa chỉ của file bằng windows.filescan : \Users\alex\Downloads\ChromeSetup.exe
- Tiến hành dump file bằng windows.dumpfiles 
- Tính mã SHA1 từ file đã được dump trước đó : **280c9d36039f9432433893dee6126d72b9112ad2**
<img width="1890" height="312" alt="image" src="https://github.com/user-attachments/assets/caec1670-cae9-435e-9fd7-5beb3a51f3e7" />

Q6 : Examining the malware's development timeline can provide insights into its deployment. What is the compilation timestamp for the malware?
- Sử dụng exiftool để tìm kiếm Time Stamp nhưng phải trừ đi 7 tiếng để chuẩn giờ quốc tế : **2019-12-01 08:36**
<img width="1898" height="101" alt="image" src="https://github.com/user-attachments/assets/c64918d3-8698-43c9-8327-8f008005bd26" />

Q7 : Identifying the domains associated with this malware is crucial for blocking future malicious communications and detecting any ongoing interactions with those domains within our network.
Can you provide the domain connected to the malware?
- Dùng mã SHA1 đã tính được gửi lên VirusTotal để tra cứu. Trong phần Relations ta có thể thấy phần mềm kết nối với : **dnsnb8.net**
<img width="740" height="168" alt="image" src="https://github.com/user-attachments/assets/1c4c8777-c2c8-4fd7-9899-a2f3d2baa31a" />

