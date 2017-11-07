
## Soru İsmi: Retro

## Soru Metni:

```nc 192.168.$MASANO.5 8888```

## On bilgi:
Kendi ortaminizda dosyayi binary dosyasini 8888 portundan servis etmek icin asagidaki komutu kullanabilirsiniz. Ancak unutmayin ki, sorunun calistigi isletim sistemi ile sizin isletim sisteminiz farkli oldugu icin, yarisma platformu tam olarak simule edilemeyecektir. Flag /home/ctf/flag dosyasinda yer almaktadir.
socat TCP-LISTEN:8888,reuseaddr,fork EXEC:"./retro"

## Çözüm: 

1. Bu soruda brute force saldirilarinin engellenmesi icin mesajlar arasina sleep konulmustur ve kullanicidan bu sure sonunda bir parola istenmektedir. Yanlis parola girildigi taktirde /bin/ls komutunun calistigi belirtilmektedir. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/Retro/r1.png)

2. Bellekte bir sekilde tasirma yaparak system(/bin/ls); komutu calistirilmak istenilen komut ile degistirilebilir. Muhtemel buffer boyutlarini (512, 1024, 2048 vb.) tasirmaya yonelik payload gonderdigimiz zaman (ornegin 1024+2 byte) tasirma oldugunu fark ediyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/Retro/r2.png)

3. Bu durumda, hedef sisteme “1024”*A+”/bin/sh” seklinde bir payload gonderdigimiz zaman shell alabiliyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/Retro/r3.png)


