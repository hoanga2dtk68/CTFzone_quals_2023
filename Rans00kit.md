`Description`

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/e040057a-705c-46b8-a3d7-7a2ad75db5c0)

`Unintended solution`
![meme](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/6fcd614e-d8ae-4f63-835f-e8a62fcd9ad0)
![unitened-solution](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/f06532a4-4d43-4465-b2a3-23d429874f95)

`Intended solution`

Đầu tiên chúng ta import machine và dùng kvrt quét để tìm rootkit và xóa

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/0ac95fd4-4576-4dbb-87ca-8f95e08a3f88)


Sau khi quét tiếp thì nhận thấy có một file ransomware mã hóa file và thêm vào đuôi file * -> *.config xem qua thì có thể thấy .NET vì thế dùng dnspy để dịch ngược chương trình để decrypt

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/f624d5b2-10df-456b-9f1b-d700ba35ccf5)

Có thể xem qua hàm main và có thể thấy chương trình gen chuỗi text ngẫu nhiên và set vào key theo path trên hình và tiếp theo tạo key và iv để mã hóa aes cbc file trong folder

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/b3d2c58f-19ba-4d3e-ad7b-a559704845cb)

Đầu tiên chúng ta vào đường dẫn HKCU như hình để lấy chuỗi text được gen random có thể bị ẩn nhưng chúng ta có thể làm hiện bằng cách vào control panel bật hiện các file ẩn là có thể thấy hoặc có thể dùng ntuser.dat để lấy chuỗi text được gen ra

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/236a6061-3aa5-45e6-9d58-58f56eda30e5)

Sau đó theo code để lấy key và iv 

[Code ở đây](https://ideone.com/aJtGVC)

`Key: 3C-01-8C-F3-C8-0F-10-D8-D6-5F-78-88-39-24-F7-33-4B-D6-76-C8-A8-21-8B-90-58-09-80-42-C8-72-FC-25
 IV: 57-12-97-70-81-70-3C-B3-B7-2E-6A-7F-99-12-18-47`

được rồi có key và iv ta đi giải mã và nhận flag thôi

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/9312dbde-42e8-4bd5-b9f8-883b3178ffcd)

yeah! có vẻ đã đúng key và iv khi decrypt ra MZ 

Định phân tích file này tiếp nhưng nghĩ có thể chèn flag vào nên em find thửu và ra flag

![image](https://github.com/hoanga2dtk68/CTFzone_quals_2023/assets/110059218/8fd9155a-5409-4d78-ae31-4a91d542b41e)

`flag: ctfzone{!R1nG0_r00Tk1T_Ea$Y_byPa$$!}`
