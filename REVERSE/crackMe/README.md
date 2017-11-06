## Soru İsmi: Crack Me

## Soru Metni: 
Lisans anahtarımı kaybettim, hükümsüzdür. Artık bu ürüne destek de verilmiyor. Satın aldığım firmayı telefonla aradım, yazılım firması emlakçılık yapmaya karar vermiş. Şu programın lisans sorgusu bölümünü geçebilmem için bi el atıver...

## Çözüm: 
1. b756d6413e4bbcd7ba46f210e345cad2.zip dosyasi icerisinden crackme.exe dosyasi cikiyor.  

2. Dosya calistirildiginda bizden bir lisans anahtari isteniyor.

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/crackMe/crackMe0.png)

3. 00402985 adresinde kurulumun baslamasi ile ilgili text bilgilerini goruluyor. 0040297F adresindeki  "JNZ  402AD7" opcodu dogru anahtar girilmez ise kuruluma baslanmasini engelledigi anlasiliyor.

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/crackMe/crackMe1.png)

4. 0040297F adresindeki  "JNZ  402AD7" opcodu  "JE 402AD7" olarak değiştirmek yeterli oluyor. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/crackMe/crackMe3.png)

5. Programi tekrar calistirip rastgele bir anahtar girmemiz durumunda flag karsimiza cikiyor. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/crackMe/crackMe4.png)

6. STMCTF{JNE_JE_NOP_NE_KADAR_kolay_CRACK_oldu.} ulasmak bu kadar kolay :p
