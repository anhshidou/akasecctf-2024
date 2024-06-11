Ở bài này, mình phải kết hợp giữa networking và endpoint hoặc malware. Mở file pcapng lên và filter thử bằng protocol, mình thấy rằng

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/c6f48acc-a512-4c6f-9a8d-c5f5cdd5c2b9)

Nhìn đoạn này có vẻ khá ảo ma. Thế nên mình thử xem website này có gì

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/ea5f7bf9-15ef-4158-a84a-a48fb1721b02)

Có một nút bấm download, không ngần ngại, mình bấm nút download

Lúc này sẽ có 1 file tên là FREE_Ram.exe. Như bài trước mình sử dụng công cụ để xem con malware này. Sau đó mình phát hiện rằng file này thực thi một số lệnh powershell

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/0f4ffcc9-efd6-4d60-abc8-dc8504006b9b)

Sau khi vào sslkey.log mình thấy có rất nhiều traffic secret. Tiếp tục quay về file pcapng. Sau đó add masterkey log file của sslkey bằng: Edit -> Preferences -> Protocols -> TLS -> Pre Masterkey logfile

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/0c57e260-adcf-4af5-9131-a3f561c749c5)

Sau khi upload file sslkey xong, mình thấy rằng có một protocol mới là http2. Lúc này thì chỉ cần tìm là sẽ thấy flag

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/ae6f2aff-c849-4037-ba54-130b34740763)

**Flag: AKASEC{B4s1c_M4lw4r3_4nd_PC4P_4n4lys1s}**
