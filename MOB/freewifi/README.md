
## Soru İsmi: Free WiFi

## Soru Metni: 
Evdeki eski Pentium 1.3 GHz dizüstü bilgisayarı elden çıkardıktan sonra kablosuz modem ayarlarını tekrar ayarladım. Güvensiz kablosuz bağlantım artık daha güvenli. Komşunun hacker kuzeni de sözde bana not bırakmış, imkanı yok şifremi kırmış olamaz, şifrem 10 karakterden fazla. 


## Çözüm: 
1. bbc0482305844d0c031df0c082cc5d2e.zip icerisinden l ve n isimli iki adet dosya cikiyor.

2. Dosyaların sıkıştırılmış olduğu görülüyor. 
```
l: 7-zip archive data, version 0.4
n: gzip compressed data, last modified: Sun Sep 10 13:21:15 2017, max compression, from Unix
```

3. 7-zip için 
```
7za e l
```
içerisinden evimKat1.tiff isimli dosya çıkıyor.

gzip için 
```
tar zxvf n
```
içerisinden evimKat1.jpg isimli dosya çıkıyor.

4. evimKat1 isimli dosya tipleri kontrol edildiğinde pcap dosyası olduğu görülüyor.
```
evimKat1.png:  tcpdump capture file (little-endian) - version 2.4 (802.11, capture length 65535)
evimKat1.tiff: tcpdump capture file (little-endian) - version 2.4 (802.11, capture length 65535)
```

5. Soru WiFi dediği için zaman kaybetmeden aircrack ile her iki dosyayi deniyoruz.

```
> aircrack-ng evimKat1.png
Opening evimKat1.png
Read 1609958 packets.

   #  BSSID              ESSID                     Encryption

   1  00:12:BF:5A:F7:B7  evimKat1                  WEP (766940 IVs)

Choosing first network as target.
Opening evimKat1.png
Attack will be restarted every 5000 captured ivs.
Starting PTW attack with 766940 ivs.

                                             Aircrack-ng 1.2 rc4
                             [00:00:04] Tested 1009515 keys (got 766940 IVs)
   KB    depth   byte(vote)
    0    0/  1   38(1056768) DD(806912) 01(802048) A5(799744) 42(799488) B0(794624) 37(793088) 
    1    0/  1   75(1029120) 53(805888) EB(805888) D6(801792) 49(799744) AA(797696) 92(795392) 
    2    0/  1   2A(1014528) E2(803584) 67(800256) 64(799488) 1A(797696) A2(796160) E5(793088) 
    3    0/  1   46(1039616) CF(798976) 84(797184) E6(795136) CA(793856) 6E(792832) D1(792576) 
    4    0/  1   31(1004544) 3F(806400) 8D(805888) FD(799488) A1(798208) 1E(794368) 43(792320) 
    5    0/  1   34(1029632) 6E(803072) B5(797184) 49(796928) D7(795904) A9(795392) AD(794112) 
    6    0/  1   67(1009408) FB(810240) B8(805376) 13(803328) B2(801024) 8A(800768) D8(797440) 
    7    0/  1   2A(1017600) 5D(807680) E6(796160) 6F(792320) B3(791808) 12(789248) 38(788736) 
    8    0/  1   44(960768) 85(802304) 19(798464) 97(798464) 94(796928) 81(796672) 0E(795392) 
    9    0/  1   65(973568) 08(794880) 37(794880) 0A(794624) C5(794624) 7E(793600) 40(790528) 
   10    0/  1   F2(803584) 20(802816) 2F(799232) FC(797184) 6B(796928) CE(796928) 2D(796672) 
   11    0/  1   6F(805632) 1E(797184) 58(795648) 6B(795136) 28(794880) 45(794368) 72(793856) 
   12    0/ 16   7E(812748) B8(810680) 8D(809696) 9D(798488) 08(795428) F9(792180) F2(790904) 

     KEY FOUND! [ 38:75:2A:46:31:34:67:2A:44:65:67:69:6C ] (ASCII: 8u*F14g*Degil )
	Decrypted correctly: 100%

> aircrack-ng evimKat1.tiff
Opening evimKat1.tiff
Read 1790738 packets.

   #  BSSID              ESSID                     Encryption

   1  00:12:BF:5A:F7:B7  evimKat1                  WPA (1 handshake)

Choosing first network as target.

Opening evimKat1.tiff
Please specify a dictionary (option -w).
Quitting aircrack-ng...
```

6. Soruda kişinin ağ ayarlarında sıkılaştırma yaptığı anlaşılıyor. yani WEP den WPA ya geçmiş. Belki aynı şifreyi kullanıyordur. Bir dosya içerisine bulduğumuz 8u*F14g*Degil şifreyi yazıp WPA kırma işlemini tekrar yapıyoruz. NOT: Yarışmacı burada ele geçirdiği evimKat1.png isimli WEP trafiğini inceleyebilir. Burada bulabileceği bir başka ipucu bulunmamaktadır. 

```
> cat dictionary 
8u*F14g*Degil

> aircrack-ng -w dictionary evimKat1.tiff
Opening evimKat1.tiff
Read 1790738 packets.

   #  BSSID              ESSID                     Encryption

   1  00:12:BF:5A:F7:B7  evimKat1                  WPA (1 handshake)

Choosing first network as target.

Opening evimKat1.tiff
Reading packets, please wait...

                                 Aircrack-ng 1.2 rc4

      [00:00:00] 1/1 keys tested (142.03 k/s) 

      Time left: 0 seconds                                     100.00%

                         KEY FOUND! [ 8u*F14g*Degil ]


      Master Key     : DD 80 65 C9 F5 F9 C5 51 6F 57 72 0E D3 6D 57 B1 
                       47 AF CC 8D DD 56 CF 28 E5 AD 7F 49 6C 40 CD A3 

      Transient Key  : 91 45 D7 CE E3 C7 71 5E A9 3F 3F A5 34 F1 16 1D 
                       61 4A 96 5C 8B 16 72 06 1C 50 22 F2 74 C4 40 26 
                       E6 F5 4C 2C A6 6B AD 8F 4F A0 41 34 36 B1 F2 73 
                       A8 3D BD 02 72 35 E3 9E 34 DC 71 AF E8 BA CB 0A 

      EAPOL HMAC     : FA 34 26 9F 44 84 BF 42 C6 38 24 92 7D 7D 0D 08  

```

7. Wireshark ile evimKat1.tiff dosyasını açıyoruz.  IEEE 802.11 WPA için elde ettiğimiz şifreyi giriyoruz. Daha sonra wireshark trafiği decode edilmesini bekliyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/freewifi/freewifi0.tiff)

8. Ağ trafiğini incelediğimizde çok fazla gürültü olduğunu görüyoruz. Yarışmacı burada DNS paketleri üzerine yoğunlaşabilir. STMCTF kelimesi geçen sorgular bulunmakta. Gürültü olması için koyulan ping istekleri, farklı portlara açılan TCP istekleri görülmektedir. DNS paketleri incelendiğinde veya STMCTF{ kelimesi string olarak paketler içerisinde arandığında flag bulunabiliyor.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/freewifi/freewifi1.tiff)


```
306088	1058.626222	192.168.2.100	192.168.2.1	DNS	141 Standard query 0x7fe1 A STMCTF{Kulland1g1n_S1frey1_Tekrar_Kullanma}
```
