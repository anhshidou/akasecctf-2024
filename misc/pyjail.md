# Pyjail

![image](https://github.com/anhshidou/akasecctf-2024/assets/81132394/c41d95ac-a711-427e-97c4-3954cc5975af)

Trước tiên mình tải source code về và xem

![image](https://github.com/anhshidou/akasecctf-2024/assets/81132394/1828a844-2804-436d-9c1f-47875d99cece)

Source code:
```
from string import printable

print('''
#################################################################
#                                                               #
#   Welcome to pyJail!                                          #
#                                                               #
#   You have been jailed for using too many characters.         #
#                                                               #
#   You are only allowed to use 16 characters of printable      #
#   ascii.                                                      #
#                                                               #
#   If you manage to break free, you will get the flag.         #
#                                                               #
#################################################################\n''')

code = input('> ')

sys.stdin = None

len = sum(1 for char in code if char in printable)

if len >= 17:
    print('Too long!')
    exit()

eval(code)

```
Tại bài này, mình cũng thử các cái để spawn ra shell mới nhưng vì ta có dòng `sys.stdin = None` nên tất cả đều không được.

Sau khi đọc qua 1 vài tài liệu, mình thấy cái này ở trên [github](https://github.com/salvatore-abello/python-ctf-cheatsheet)

![image](https://github.com/anhshidou/akasecctf-2024/assets/81132394/1c8d59a6-0d6d-4f24-bd25-281e716a3ed7)

Mình nghĩ tới việc thay đổi các function của python về các kí tự thuộc unicode nhưng không thuộc ASCII. Mình sử dụng trang [này](https://instafonts.io/font/math-sans-font)

Sau đó mình đổi code như sau: `𝗉𝗋𝗂𝗇𝗍(__𝗂𝗆𝗉𝗈𝗋𝗍__("os").𝗅𝗂𝗌𝗍𝖽𝗂𝗋())`

![image](https://github.com/anhshidou/akasecctf-2024/assets/81132394/9d473ca9-69ae-43bc-9ef8-84010ee9a426)

Và cuối cùng mình thử open nó sau khi exit python `𝖾𝗑𝗂𝗍(𝗌𝖾𝗍(𝗈𝗉𝖾𝗇("flag.txt")))`

![image](https://github.com/anhshidou/akasecctf-2024/assets/81132394/57bd2773-f151-43ce-ad7f-1204274c882a)

Flag: `AKASEC{1t5_4ll_4b0ut_3sc4p1ng_4nd_3v4lu4T1ng}`

**--END--**
