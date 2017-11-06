## Soru İsmi: encodingLoop

## Soru Metni: 
Biraz karıştırdık. Encode ettik, evirdik, çevirdik, rot'ladık, biraz da ipucu iliştirdik ve sana çözmen için bıraktık.

## Çözüm: 
1. 56eafb661da1f97918aa73d9e9461389.zip dosyasi icerisinden yaklasik 20 MB buyuklugunda flag.txt dosyasi cikiyor. Dosyanin icerigi incelendiginde BASE64 ile encode edildigi anlasiliyor.

2. flag.txt dosyasi base64 ile decode edildiginde base32 ifadesini takiben yeni bir encode edilmis text metin gozukuyor. Her decode sonrasinda bir sonraki encode isleminin ne olacagi dosyanin basinda belirtiliyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/encodeingLoop/encodeingLoop0.png)


