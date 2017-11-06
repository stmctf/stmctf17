
## Soru İsmi: Farkı Bul

## Soru Metni: Flag resmin içinde. Kendi kendine kilitlenip açılan killit buldum.
c214364ee8d366a4170337c5216f498c.zip

## Çözüm: 
1.lock-a ve lock-b png dosyalarının piksel olarak farkını aldığımızda decryption için işimize yarayacak olan anahtarı görüyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/FarkiBul/fark1.png)


2.Aynı resim dosyalarının meta bilgilerinden part_1 ve part_2 olarak ciphertext elde ediliyor. Örnek komut: “exiftool lock-a.png”
![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/FarkiBul/fark2.png)


3.Şu ana kadar elde ettiğimiz bilgileri ve lock.png’de açık olarak görünen IV değerini kullanarak decryption işlemini gerçekleştirip flag’i elde ediyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/FarkiBul/fark3.png)




