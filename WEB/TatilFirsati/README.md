
## Soru İsmi: Tatil Fırsatı

## Soru Metni: 

En büyük tur acentelerinden birinde kritik açık bulundu. Kendine ve arkadaşlarına bedava tatil fırsatını kaçırma!

![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/TatilFirsati/tatilsoru.png)

## Çözüm: 

Ilk ve en basit olarak /flag.txt'yi tahmin ederek cozulebilir.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/TatilFirsati/tatil0.png)


Flag.txt'nin varliginin tahmin edilemedigi durumlarda command injection denemesi yapilarak, grep komutuyla dizinde icinde STM kelimesi gecen dosyalar ekrana bastirilabilir.

```
Ankara;grep -R STM&
```
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/TatilFirsati/tatil1.png)


