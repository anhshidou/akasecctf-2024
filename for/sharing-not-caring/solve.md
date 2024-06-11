Ở bài này, mình phải kết hợp giữa networking và endpoint hoặc malware. Mở file pcapng lên và filter thử bằng protocol, mình thấy rằng

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/c6f48acc-a512-4c6f-9a8d-c5f5cdd5c2b9)

Nhìn đoạn này có vẻ khá ảo ma. Thế nên mình thử xem website này có gì

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/ea5f7bf9-15ef-4158-a84a-a48fb1721b02)

Có một nút bấm download, không ngần ngại, mình bấm nút download

Lúc này sẽ có 1 file tên là FREE_Ram.exe. Như bài trước mình sử dụng công cụ để xem con malware này. Sau đó mình phát hiện rằng file này thực thi một số lệnh powershell

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/0f4ffcc9-efd6-4d60-abc8-dc8504006b9b)

Sau khi vào sslkey.log mình thấy có rất nhiều traffic secret. Tiếp tục quay về file pcapng
