

## Soru İsmi: Tombul Kuş

## Soru Metni: 

Biz yükledik, oynadık; çok eğlendik. Ama ne kadar zıplarsan zıpla, bulamayacaksın. 

## Çözüm: 
1. Apk’yı decompile edip kodu incelediğimizde flag’in 200 parça halinde png dosyalarından oluştuğu anlaşılıyor.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/TombulKus/tombul1.png)

2. Assets/flag dizininde png dosyalarını görüyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/TombulKus/tombul2.png)


3. Resimleri yatay olarak birleştirince flag elde ediliyor. Bu işlem için convert komutu +append parametresi ile kullanılabilir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/TombulKus/tombul3.png)
