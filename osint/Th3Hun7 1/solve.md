![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/b2376865-c5d0-42cd-9709-211fa81e6e6b)

Ở challenge này, họ yêu cầu ta phải đi tìm Former member của team akasec. Hint ở đây là đáp án không nhất thiết phải ở ctftime.org.

Bước đầu tiên, mình vào trang ctftime.org để xem team này có gì không ?

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/9cea893b-46e8-41ff-8e65-cda77a59e81e)

Mình thấy 3 link là website của ctf, website chính thức và twitter. Lúc này mình vào website chính thức

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/b21902f9-fa29-4c63-85be-e5d5e191bf36)

Mình thấy nó khá bình thường. Vì vậy nên mình vào twitter của team này

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/6ad5f9c9-c2c3-4bdb-b31c-b108b32342bc)

Lúc này, mình biết được rằng đây là website mới deploy. Mình đoán là ở trong website này sẽ có gì đó mà tác giải cài cắm, vì thế nên mình xem thử source code của trang web này.

Ở đây mình thấy 1 link twitter, 1 link github và 

``` <img alt="l3ar4nda5" loading="lazy" decoding="async" data-nimg="fill" class="object-cover" style="position:absolute;height:100%;width:100%;left:0;top:0;right:0;bottom:0;color:transparent" sizes="100vw" src="/_next/static/media/l3rnds.bbe6448d.jpeg"> ```

Ở đây, rõ ràng đây là phần sus nhất. Vì thế nên mình thử xem src ảnh kia có gì

![image](https://github.com/anhshidou/akasecctf-2024/assets/120787381/f8f0093b-fc87-4eef-8e30-aafb98fbe5e5)

**Flag: AKASEC{Wh4T_a_PfP_:3}**
