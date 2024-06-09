# Đề bài:

![Screenshot (579)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/3b41d3f7-cf8e-482b-b852-75b4e8af0fb3)

# Khai thác:
- Tài liệu: https://pkg.go.dev/net/http/pprof
- Để ý suộc, ta thấy ```import _ "net/http/pprof"```
- Để ý dockerfile, ta thấy vị trí của flag ```CMD ["./main", "--FLAG=AKASEC{REDACTED}"]```
- Tiếp theo, trong tài liệu ta thấy: ```Cmdline responds with the running program's command line, with arguments separated by NUL bytes. The package initialization registers it as /debug/pprof/cmdline.```
- Vậy nên bài này ta chỉ cần đơn giản sử dụng path /debug/pprof/cmdline (tất nhiên là chỉ biết được khi giải kết thúc, haizz)

# Exploit:
- Giao diện trang web:

![Screenshot (580)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/85823f0d-a6c9-4478-9008-0400e46e1cf6)

- Flag is here:

![Screenshot (581)](https://github.com/anhshidou/akasecctf-2024/assets/152991010/0b0aee76-d6fb-4322-b691-8308972b8ad5)

# Flag:
AKASEC{r0t4t3d_p20x1n9_f002_11f3_15n7_92347_4f732_411____}
