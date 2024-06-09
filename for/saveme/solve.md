![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/34b40ab4-d578-4ff9-890c-ae015e95e067)

Ồ, vậy là malware. Ở đây mình có vài file ảnh bị lỗi và 1 file docm. Theo lẽ thường thì mình sẽ dùng olevba, nhưng mà lần này thi mình không dùng. Thay vào đó thì mình vào file docm và sử dụng tổ hợp ctrl + A để select all

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/73092674-089c-42ba-b415-ec691990001f)

Lúc này, sẽ xuất hiện đoạn nhìn có vẻ là hexa và được ngăn cách bởi &H. Mình sử dụng đoạn code nhỏ

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/8ce0b323-65f2-4245-8506-a58142ec20fe)

Vậy đây là 1 file Executable, chắc chắn đây sẽ là điểm mấu chốt. Lúc này vì mình không có máy ảo là windows nên mình sử dụng app.any.run để kiểm tra nó hoạt động như nào

``` https://app.any.run/tasks/3b474515-dc8e-4019-985a-152bfbc518df/ ```

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/f1794b20-dae3-4239-91d5-5d6b113aa141)

Vậy ở đây mình thấy 1 đường link HTTP còn active. Vì vậy nên mình thử tải file này về

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/907d3ade-c5ab-4d9a-92e3-c416eda1ab7b)

Mình thấy rằng đây là 1 file .NET, vì vậy nên mình thử cho nó vào ide để xem có gì không. Sau khi disassemble file bằng jetbrains dotPeek. Mình tìm thấy cách mã hóa của nó

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/7e383744-fae0-4fea-a3dd-639c65dd7211)

```
string path1 = str2;
          global::a.b = (object) flag2;
          byte[] numArray3 = File.ReadAllBytes(path1);
          \u003CModule\u003E.g = (object) null;
          global::a.b = (object) "185ee01d-8c67-459c-9586-6804417e592ce434881f-7f35-4ffd-bdf6-4a1f244e25084e41b92d-afec-";
          \u003CModule\u003E.d = (object) null;
          byte[] numArray4 = numArray3;
          \u003CModule\u003E.h = 1308380089;
          cryptoServiceProvider1 = new TripleDESCryptoServiceProvider();
          TripleDESCryptoServiceProvider cryptoServiceProvider2 = cryptoServiceProvider1;
          Encoding ascii = Encoding.ASCII;
          string s = str1;
          \u003CModule\u003E.k = 401140706;
          byte[] bytes1 = ascii.GetBytes(s);
          cryptoServiceProvider2.Key = bytes1;
          \u003CModule\u003E.o = 1203310366;
          TripleDESCryptoServiceProvider cryptoServiceProvider3 = cryptoServiceProvider1;
          byte[] numArray5 = numArray2;
          c.b = (object) str1;
          cryptoServiceProvider3.IV = numArray5;
          byte[] numArray6 = global::b.b(numArray4, cryptoServiceProvider1);
          string path2 = str2;
          byte[] bytes2 = numArray6;
          \u003CModule\u003E.n = -1749758540;
          File.WriteAllBytes(path2, bytes2);
          global::a.b = (object) "102abfb4-ec8b-4922-9b54-2f17b2c5b52d6d";
          string str3 = str2;
          \u003CModule\u003E.a = (object) exception1;
          Console.WriteLine("Encrypted: " + str3);
          c.b = (object) 1876936332;
```

Ở đoạn này, mình biết được rằng: Key của TripleDES là str1, mà str1 ở đây là Lp3jXluuW799rnu4, và IV là gồm các byte từ 0 - 7. Vậy là mình đã có được cả key lẫn IV. Thế còn decrypt thì mình có thể đoán được ngay là decrypt các ảnh bị hỏng kia.

Ở đây mình chọn ảnh 144 vì nó là cái lạ nhất. Sau khi decrypt thì ta có bức ảnh

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/d996e365-0ff4-4427-b87f-72d45d08cae3)

**Flag: AKASEC{F_MiCRoSft_7733}**
