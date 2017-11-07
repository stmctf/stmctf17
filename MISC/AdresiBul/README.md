
## Soru İsmi: Adresi Bul

## Soru Metni: 

Bir hacker dünya çapında web ve mobil uygulamalarını daha güvenli hale getirmek için çalışan ve top 10 zafiyetleri yayınlayan organizasyonun sitesini ele geçiriyor. Yetkililer sunucunun nasıl ele geçirildiğini tespit edemiyor ve atağın zero day olabileceğini söylüyor. Tüm güvenlik araştırmacıları yeni bir yöntem olduğunu ve bunu acilen bilinmesi gerektiğini belirtiyor. Zafiyet tespiti için de sunucunun fiziksel adresine erişmek gerekiyor Size düşen ise sunucudan dönen fiziksel adresin olduğu bulvarın ismini bulmak. Bayrak için ipucu STMCTF{\*_*_Blvd}

Soruyu hazırlayan: [Ş]


## Çözüm: 

1. Dünya çapında web ve mobil uygulama güvenliğini arttırmak için çalışan ve top 10 zafiyetleri yayınlayan organizasyon www.owasp.org olarak düşünülür. 



2. nslookup www.owasp.org sorgusu yapılır. IP 104.130.219.202 olarak bulunur.
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/AdresiBul/adr1.png)

3. Burada istenen fiziksel adres sunucudan dönen ‘loc’ bilgisidir. İstenilen IP’den dönen fiziksel adresi bulabilmek için çeşitli yöntemlerden biri uygulanır. Loc ekran görüntüsündeki gibi bulunur.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/AdresiBul/adr2.png)


4. Bulunan koordinat bilgisi Google maps’te aranarak hedef bulunmaya çalışılır.
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/AdresiBul/adr3.png)

5. Hedefe ulaşılır. Soruda da ipucu olarak verilen {*_*_Blvd} şekilde adres bulunur.  Center Park Blvd
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/AdresiBul/adr4.png)

Bulunan adres STMCTF bayrak formatına göre md5 değeri bulunur.

$echo -n 'STMCTF{Center_Park_Blvd}' | md5sum

2a14c77547e08e867c98af69465c62e7

