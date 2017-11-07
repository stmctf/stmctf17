

## Soru İsmi: HackOpssVol5465

## Soru Metni: 

Teknoloji firmasının web developer'ı prod uygulama üzerinde geliştirmeler yapmaya başlamış ve mesai bitimine doğru elektriğin kesilmesi ile birlikte çalışmanın diğer kısmını ertesi güne ertelemişlerdir. 

İki hacker bu firmanın uygulama geliştiricisinin yaptığı bir hata nedeni ile şirketin ağına yetkisiz erişim sağlamışlardır. Bunu fark eden IT güvenlik birimi ağ iz kayıtlarından durumu detaylı incelemeye başladılar. Onlara yardımcı olabilir misin ?

http://192.168.MASANO.5:9999

## Çözüm: 

1. Soruda verilen web sayfasına girdiğimizde “config not found” hatası alınmaktaydı. 
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa1.png)

2. Soru açıldıkdan 5 dakika sonra developer’ın vi kullandığı ipucu olarak verildikten sonra aşağıdaki adrese gitmemiz gerekiyordu. Sebebi ise vi aracının recovery özelliği sayesinde swp dosyasına ulaşabilir olması. Kaynak kodunu görüntülediğimizde pcapFile dosyası göze çarpıyordu.

![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa2.png)

3. Dosyayi ilgili adresten indiriyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa3.png)

4. Pcap dosyasını incelemeye başladıktan sonra 2 adet dosyayının sunucuya yüklendiğini görmekteyiz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa4.png)

5. İlk dosyamız “k01” adında rar formatıyla yüklendiğini görmekteyiz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa5.png)

6. Dosyamızı Raw formatta görütüledikten sonra aşağıdaki ekran görüntüsündeki gibi kayediyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa6.png)

7. Dosyayı açmaya çalıştığımızda sıkıştırılmış dosyanın parolası olduğunu görüyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa7.png)

8. İşe yarar ipucu bulmak için 2. dosyamıza yöneliyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa8.png)

9. 2. dosya bir ses dosyasıydı.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa9.png)

10. Dosyamızı Raw formatta görüntüledikten sonra mp3 olarak kaydediyoruz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa10.png)

11. Ses dosyasını dinlediğimizde bize “Parola : 583406” olduğunu söylüyordu.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa11.png)

12. Word dosyamızı açtığımızda  “/k-o-a/stmAdmin.php?flag=” adresine gitmemiz bekleniyordu.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa12.png)

13. Adrese erişmeye ve flag parametresine bişeyler yazmaya çalıştığımızda aşağıdaki ekran görüntüsündeki web sayfası aşağıdaki gibi gif ile geliyordu.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa13.png)

14. Bu soruyla alakalı 5 er dakika arayla 2 adet ipucu açıldı. İlk ipucunda pcap dosyasında 2 hackerın konuşmasının olduğundan bahsediyordu.Strings aracı ile “Hacker” olarak greplediğimizde encode  çeşitleriyle konuşmaları görebiliyorduk. Burada fark etmemiz gereken, konuşma “Hacker1 Hacker2” olarak giderken son 2 satırda “Hacker2 Hacker2” olarak gitmişti. 2. ipucunda ise “grep’i hack edin” deniyordu. Grep hack olarak değiştirdiğimizde “Hack ers1” konuşmasında sezar algoritması ile encode edilmiş bir cümle vardı.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa14.png)

15. Sezar algoritmasını 17 harf ileriye kaydırdığımızda aşağıdaki ipucu karşımıza geliyordu.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa15.png)

16. Sezarda çıkan “EDPXT===” base32 yaptığımızda herhangi bir sonuç dönmeyecekti. Satırda gördüğümüz şekilde Base32 decode edildiğinde artık uygulamanın paneline “k0a” olarak giriş yapabilirdik.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa16.png)

17. Flag parametresine “k0a” yazdığımızda flagi yakalayabilirdik.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/HackOpssVol5465/koa17.png)
