

## Soru İsmi: NURELLA

## Soru Metni: 67b99362ffe51662399a5c2bad15e284.jpg

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/NURELLA/67b99362ffe51662399a5c2bad15e284.jpg)

## Çözüm: 
1. Yarışmacı verilen resmin metadatsına exiftool ile baktığında comment bölümünde yazan hex stringi buluyor:
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/NURELLA/nur1.png)

2. Sorunun ismi NURELLA ve resimde yazan da ÇAREniz NURELLA şeklinde algılanabilir. 
3. Bulunan hexadecimal string “NURELLA” ile XORlandığında flag bulunuyor.
4. NURELLA yı hexadecimale çeviriyoruz: 4e5552454c4c41
5. Bulunan hexadecimal değer 70 karakterli NURELLA nın hexadecimali ise 14 karakter. Bu nedenle NURELLA nın hexadecimal değerini 5 kere yazıyoruz ve bu şekilde XOR luyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/NURELLA/nur2.png)

6. Bulunan hexadecimal değeri (53544d4354467b41795f6e655f4b344434725f5933725f79416e6469213f213f213f7d) ASCII ye çevirdiğimizde flag i elde ediyoruz:

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/NURELLA/nur3.png)

Flag = STMCTF{Ay_ne_K4D4r_Y3r_yAndi!?!?!?} = 8FBDA0AAC22A1602DF86FBC761E56AA0
