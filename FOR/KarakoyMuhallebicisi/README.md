## Soru İsmi: Karakoy Muhallebicisi

## Soru Metni: 
Sisteme sızan bir saldırganın veri kaçırdığını farkettik. Ekteki ağ trafik kaydını inceleyerek, kaçırılan veriyi bulmakta bize yardımcı olur musun?
41795a29a6d369da13d9bbc086008ca1.zip

## Çözüm: 

1. Wireshark ile inceledigimiz zaman dns trafigini olusturan subdomainlerin anlam ifade etmeyen karakterler olustugunu tespit ediyoruz.

2. Bu DNS paketlerindeki 213.74.41.50 ile olan trafigin yapisi XXX.YYY seklinde oldugu anlasilir.

```“5140 56.127685403 172.16.196.137 → 172.16.196.138 DNS 92 Standard query 0x6971 A AYLEMRUXI2.LPNYQHI3ZA OPT”```

3. Tshark ile DNS trafigi filtrelenerek text dosyasina aktarilir.

```tshark -n -r karakoy.pcapng -Y 'dns' > dns.txt```

4. 213.74.41.50 IP adresi ile iletisim filtrelenerek supheli kisim ayri bir text dosyasina aktarilir.

```cat dns.txt | grep '213.74.41.50' | cut -d' ' -f14 > dns2.txt```


5. Text dosyasindaki “.” karakterleri cikarilir.

```tr -d '.' < dns2.txt > dns3.txt```

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/KarakoyMuhallebicisi/kar1.png)


6. Text dosyasindaki “.” karakterleri cikarilir.

```tr -d '\n' < dns3.txt > dns4.txt```

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/KarakoyMuhallebicisi/kar2.png)



#Cikan karakterler analiz edildiginde. Base32 encode edildigi ortaya cikmaktadir.
#base32 -d komutu ile decode edilmektedir.

```base32 -d dns4.txt | grep STMCTF```
![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/KarakoyMuhallebicisi/kar3.png)
