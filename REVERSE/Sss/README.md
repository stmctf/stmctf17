
## Soru İsmi: Şşş

## Soru Metni: 
Aslında çok kolay olan soruyu birazcık zorlaştırdık.
7605274185f215e181254aeab3837cb4.zip

## Çözüm: 

1. Yarışmacı strings komutuyla resme baktığında flagin sadece bir parçasını görebiliyor.

```strings Şşş.jpg```

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/Sss/sss1.png)

2. Unicode karakterler olduğu için flagi tam olarak görmesi için encodingi ayarlaması lazım.
(s = single-7-bit-byte characters (ASCII, ISO 8859, etc., default), S = single-8-bit-byte characters)

```strings -e S Şşş.jpg```

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/Sss/sss2.png)

FLAG = STMCTF{Ş3KİL_Y4pm4K_İÇİn_N3_K4Dar_uĞr4ştığımı_GöRÜy0rsUn_DEğİl_mİ?}
