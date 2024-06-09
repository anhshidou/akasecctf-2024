![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/2fdc9bb2-74a1-470d-ab0b-6c6c98ef1306)

Ở bài này, họ cho mình một file memdump. Lúc này mình đã xác định được hướng đi là memory analysis và tool mình sẽ dùng ở đây là volatility3

Đầu tiên, mình sử dụng để câu lệnh: ``` python3 vol.py -f /mnt/e/CTF/akasecctf/forensics/Portugal/memdump1.mem windows.pslist.PsList ``` để list ra các process

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/132a59b1-bee5-43e1-a398-ab7bf277a370)

Lúc này, mình thấy chrome.exe là process nhiều nhất, vì vậy nên mình có thể chắc chắn rằng pid 1240 là pid mấu chốt để tìm ra

Thế nên, mình sử dụng câu lệnh: ```python3 vol.py -f /mnt/e/CTF/akasecctf/forensics/Portugal/memdump1.mem -o /mnt/e/CTF/akasecctf/forensics/Portugal/ windows.memmap.Memmap --pid 1240 --dump``` để dump pid này ra 1 file

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/403bdff6-e9d1-48c7-91d6-e583636d074c)

Sau khi đã có thì mình xem thử file và filter google search, sau khi filter và lọc ra, mình thu được như sau:

``` https://www.google.com/search?q=8-+1t&sourceid=chrome&ie=UTF-88- 1t\
https://www.google.com/search?q=8-+1t&sourceid=chrome&ie=UTF-88- 1t\
https://www.google.com/search?q=7-+1l&sourceid=chrome&ie=UTF-87- 1l\
https://www.google.com/search?q=7-+1l&sourceid=chrome&ie=UTF-87- 1l\
https://www.google.com/search?q=6-+4t&sourceid=chrome&ie=UTF-86- 4t\
https://www.google.com/search?q=6-+4t&sourceid=chrome&ie=UTF-86- 4t
https://www.google.com/search?q=5-+0l&sourceid=chrome&ie=UTF-85- 0l\
https://www.google.com/search?q=5-+0l&sourceid=chrome&ie=UTF-85- 0l^
https://www.google.com/search?q=4-+%7Bv&sourceid=chrome&ie=UTF-84- {v^
https://www.google.com/search?q=4-+%7Bv&sourceid=chrome&ie=UTF-84- {v\
https://www.google.com/search?q=3-+ec&sourceid=chrome&ie=UTF-83- ec\
https://www.google.com/search?q=3-+ec&sourceid=chrome&ie=UTF-83- ec
https://www.google.com/search?q=2-+as&sourceid=chrome&ie=UTF-82- as\
https://www.google.com/search?q=2-+as&sourceid=chrome&ie=UTF-82- as\
https://www.google.com/search?q=1-+ak&sourceid=chrome&ie=UTF-81- ak
https://www.google.com/search?q=1-+ak&sourceid=chrome&ie=UTF-81- ak
https://www.google.com/search?q=18-+h_&sourceid=chrome&ie=UTF-818- h_^Q
https://www.google.com/search?q=18-+h_&sourceid=chrome&ie=UTF-818- h_^P
https://www.google.com/search?q=21-+0r&sourceid=chrome&ie=UTF-821- 0r^O
https://www.google.com/search?q=21-+0r&sourceid=chrome&ie=UTF-821- 0r^N
https://www.google.com/search?q=19-+h1&sourceid=chrome&ie=UTF-819- h1^M
https://www.google.com/search?q=19-+h1&sourceid=chrome&ie=UTF-819- h1^L
https://www.google.com/search?q=20-+st&sourceid=chrome&ie=UTF-820- st^K
https://www.google.com/search?q=20-+st&sourceid=chrome&ie=UTF-820- st`J
https://www.google.com/search?q=22-+y%7D&sourceid=chrome&ie=UTF-822- y}`I
https://www.google.com/search?q=22-+y%7D&sourceid=chrome&ie=UTF-822- y}^H
https://www.google.com/search?q=17-+rc&sourceid=chrome&ie=UTF-817- rc^G
https://www.google.com/search?q=17-+rc&sourceid=chrome&ie=UTF-817- rc^;
https://www.google.com/search?q=16-+34&sourceid=chrome&ie=UTF-816- 34^:
https://www.google.com/search?q=15-+_s&sourceid=chrome&ie=UTF-815- _s^9
https://www.google.com/search?q=15-+_s&sourceid=chrome&ie=UTF-815- _s^8
https://www.google.com/search?q=14-+m3&sourceid=chrome&ie=UTF-814- m3^7
https://www.google.com/search?q=14-+m3&sourceid=chrome&ie=UTF-814- m3^6
https://www.google.com/search?q=13-+r0&sourceid=chrome&ie=UTF-813- r0^5
https://www.google.com/search?q=13-+r0&sourceid=chrome&ie=UTF-813- r0
https://www.google.com/search?q=look+!!+its+here+yay&rlz=1C1FHFK_enMA1112MA1112&sourceid=chrome&ie=UTF-8look !! its here yay
https://www.google.com/search?q=look+!!+its+here+yay&rlz=1C1FHFK_enMA1112MA1112&sourceid=chrome&ie=UTF-8look !! its here yay^0
https://www.google.com/search?q=12-+ch&sourceid=chrome&ie=UTF-812- ch^/
https://www.google.com/search?q=12-+ch&sourceid=chrome&ie=UTF-812- ch^.
https://www.google.com/search?q=11-+r_&sourceid=chrome&ie=UTF-811- r_^-
https://www.google.com/search?q=11-+r_&sourceid=chrome&ie=UTF-811- r_^,
https://www.google.com/search?q=10-+f0&sourceid=chrome&ie=UTF-810- f0^+
https://www.google.com/search?q=10-+f0&sourceid=chrome&ie=UTF-810- f0\)
https://www.google.com/search?q=9-+y_&sourceid=chrome&ie=UTF-89- y_\*
https://www.google.com/search?q=9-+y_&sourceid=chrome&ie=UTF-89- y_
https://www.google.com/search?q=16-+34&sourceid=chrome&ie=UTF-816- 34
```

Khi để ý kĩ, mình thấy rằng giờ chỉ cần ghép tất cả chỗ này thành flag theo đúng order đã được cho:

**Flag: AKASEC{V0L4T1L1TY_f0r_chr0m3_s34rch_h1st0ry}**
