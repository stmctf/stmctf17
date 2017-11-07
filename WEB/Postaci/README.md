
## Soru İsmi: Postacı

## Soru Metni: 

http://192.168.$MASANO.5:5555/troll.php sayfasına git bakalım FLAG orada mı acaba? 

## Çözüm: 

0. Tatil Firsati sorusunun aksine bu sefer /flag.txt yazanlar bir youtube linkine yonlendirilmekteydi. Ancak bu link gercek flagi icermiyor ( https://www.youtube.com/watch?v=o1eHKf-dMwo ).
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po0.png)

1. Çıkan sayfada yazan “POSTacı geldi hanııım!” cümlesinden ilgili sayfaya POST isteği yapmamız gerektiğini anlıyoruz.
2. Burp aracıyla intercept ederek GET isteği yerine POST isteği gönderdiğimizde aşağıdaki mesaj çıkıyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po1.png)
3. Mesajdaki değeri ekliyoruz:
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po2.png)
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po3.png)

4.  Dönen cevapta POST isteğiyle bir de data yollamamız gerektiğini anlıyoruz. POST datası olarak flag dışında bir şey yollarsak "yanlış parametre" cevabını alıyoruz:
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po4.png)
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po5.png)

5. POST datası olarak flag yollarsak bizi troll.php?page=sanayardimicinburadayim.php sayfasına yönlendiriyor.



![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po7.png)

6. page parametresini kullanarak LFI deneyebiliriz fakat denediğimizde aşağıdaki sayfa geliyor:
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po8.png)

7. Yönlendirildiğimiz troll.php?page=sanayardimicinburadayim.php sayfasında flag parametresine verdiğimiz değerin yanlış olduğunu söylüyor. Doğru parametre verirsek flagi elde edebiliriz. Parametrenin değerini bulmak için yine URL’deki page parametresinden yararlanabiliriz. Bu parametrenin değeri troll.php sayfasında yazmaktadır. Amacımız troll.php sayfasının kodunu bir şekilde LFI yaparak okumak.

8. PHP filtrelerini kullanarak /troll.php?page=php://filter/convert.base64-encode/resource=troll.php ile troll.php sayfasının kodu base64 olarak okunabiliyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po9.png)


9. Yarışmacı base64 değerini decode ettiğinde troll.php'nin kodunu görebiliyor ve flag parametresine vermesi gereken değeri görüyor.
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po10.png)

10. Flagin olduğu dosyayı direk olarak /hanimisflagburadaymisflag.php şeklinde çağıramıyor. Ancak POST requestiyle doğru parametreyi vererek okuması gerekiyor. 
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po11.png)

11. Decode edilen base64 degerinde (sayfanin kaynak kodunda) "Hanimis benim flag im?" gorulmektedir. Dogru parametre, dogru sayfa ve dogru http method birlestirilerek asagidaki istek olusturuluyor ve STMCTF{MuK-KemMEL_1_POST_Istegi} flag bulunuyor. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/Postaci/po12.png)

```
Alternatif istek:
$ curl -X POST -d "flag=Hanimis benim flag im?" http://192.168.X.5:5555/troll.php
STMCTF{MuK-KemMEL_1_POST_Istegi}
```



