

## Soru İsmi: Destek istiyorum Sizden

## Soru Metni: Elimde key var, script var bi de şifreli dosya var. Napçam ben bunları? Bi destek atıverin!
c460e1ea3455bbf5b4253a8a7d5f55a5.zip

## Çözüm: 
1. decrypt.py içerisindecipherolarakDESkullanıldığınıgörüyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DestekIstiyorumSizden/destek1.png)

2. keys.txt dosyasında uygun uzunlukta bir tane key bulunuyor.

![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DestekIstiyorumSizden/destek2.png)

3. decryptme dosyasının içinde byte’ların 1 ve 0’lardan oluşan string representation’ı görünüyor. Ufak bir script yardımıyla tekrar byte’a çevirip dosyaya yazıyoruz. Örnek kod:
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DestekIstiyorumSizden/destek3.png)

4. decrypt.py içinde gerekli değişiklikleri yapıp çalıştırdığımızda flag’i elde ediyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DestekIstiyorumSizden/destek4.png)
