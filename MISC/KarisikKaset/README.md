## Soru İsmi: Karışık Kaset

## Soru Metni: 

Şifreli görüşen iki casus arasındaki internet trafiğini kopyalamayı başardık. Ama PCAP dosyasından sadece bu dosya çıktı. Başta önemsemedik de bir mp3 dosyasında 35 tane şarkı olması bize biraz garip geldi. Hacker kulaklarını kullanarak şu dosyayı analiz eder misin?

## Çözüm: 

1. Bu soruda yaklasik 13 dakikalik bir MP3 dosyasi icerisinde flag bulunmaya calisildi. 
Sorudaki "Hacker kulaklarını kullan" ifadesi ve yarisma esnasinda "Mr. Robot'da Elliot'in yaptığı kadar karışık degil. Basit düşün." ipucu ile sorunun Steganografi sorunu olmadigini anliyoruz.

2. Ipuclari arasinda yer alan "Music Discovery, Charts & Song Lyrics", Google'da araninca ilk sirada Shazam cikiyor.
Bu ipucu verilmeden once de karisikkaset.mp3 dosyasi ffprobe ile incelendiginde bazi ipuclari karsimiza cikiyor.



3. Shazam ile her şarkı değişiminde şarkının adı bulunabiliyor. Sarkı isimlerinin baş harfleri sıralandığında FLAG ortaya çıkıyor. 
Gerisi şarkı isimlerinin baş harflerini yan yana yazmak.

```
S She and Her Darkness - Diary of Dreams
T T.N.T. - AC/DC
M Mjød - Kvelertak
C Crawling (Official Video) - Linkin Park
T Toy Yillar - TINI
F FaceSlap! - Antisilence
{ { - Stories In Red
S So Far Away - Dire Straits
T This Is the Life - Amy Macdonald
3 3000 - David Duchovny
G Göreceksin Kendini - Nilüfer
A Absolute Zero - Stone Sour 
N N'olur N'olur N'olur - Yasemin Mori
O One for the Road - Saints 'N' Sinners
_ _ - Nell 
Y Your Dreams Won't Die - Magnum
A Alagözlerini Sevdigim Dilber - Badem
L La Grange - ZZ Top
A Anatolia (Version 1) - Pentagram
N Nomad - Sepultura
+ + - Of Mice & Men
M Ma Baker - Boney M 
U Umrumda Değil - Sokak Köpekleri
2 2 Minutes To Midnight (1998 Remaster) - Iron Maiden
I ICH TU DIR WEH - Rammstein
K Killing Me Killing You - Sentenced
! ! - Batfoot!
S Song 2 - Blur 
A All of Me - John Legend
H Hatıralar - Mirkelam
A Angry Son - Radical Noise
N No Regrets - Edith Piaf
E Electric Worry - Clutch
.  . . . - Wolverine
} } - Stories In Red

```
STMCTF{ST3GANO_YALAN+MU2IK!SAHANE.}
