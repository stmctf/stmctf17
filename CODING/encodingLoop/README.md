## Soru İsmi: encodingLoop

## Soru Metni: 
Biraz karıştırdık. Encode ettik, evirdik, çevirdik, rot'ladık, biraz da ipucu iliştirdik ve sana çözmen için bıraktık.

## Çözüm: 
1. 56eafb661da1f97918aa73d9e9461389.zip dosyasi icerisinden yaklasik 20 MB buyuklugunda flag.txt dosyasi cikiyor. Dosyanin icerigi incelendiginde BASE64 ile encode edildigi anlasiliyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop4.png)

2. flag.txt dosyasi base64 ile decode edildiginde base32 ifadesini takiben yeni bir encode edilmis text metin gozukuyor. 
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop5.png)

3. Her decode sonrasinda bir sonraki encode isleminin ne olacagi dosyanin basinda belirtiliyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop0.png)

4. base64, base32, rot_13, bz2_codec, zlib_codec ve xor islemlerinin oldugu ve rastgele tekrar ettigi anlasiliyor. xor formatinda digerlerinden farkli olarak hangi karakter ile xor edildigi de belirtiliyor. xor_y ifadesi y ile xor edildigini gosteriyor.

5. Toplanan bu bilgiler ile decode python kodunu su sekilde olur.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop1.png)

6. Python kodunu calistirdigimizda 227 decode isleminden sonra flag karsimiza cikiyor.    
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop2.png)
![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/encodingLoop/encodingLoop3.png)

FLAG: STMCTF{3ll3_0lacak_Gibi_Degildi!}
