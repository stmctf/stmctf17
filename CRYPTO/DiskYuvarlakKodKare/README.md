

## Soru İsmi: Disk Yuvarlak - Kod Kare

## Soru Metni: 
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DiskYuvarlakKodKare/d02f7fa78908987a9460a4decbb1a927.png)

![f93f75f8cae4a51cdd9b491a7c11c69d.zip](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DiskYuvarlakKodKare/f93f75f8cae4a51cdd9b491a7c11c69d.zip)


## Çözüm: 

1.Karekod herhangi bir okuyucu ile okutulduğunda Alberti Leon Battista adına kayıtlı telefon no ve mail adresi çıkmaktadır. Alberti Leon Battista (Alberti Disk) adıyla bilinen şifreleme aygıtının mucididir. 
 
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DiskYuvarlakKodKare/disk1.png)

2.Telefon numarası olan 85836977657376 değeri ASCII karakterlerine oldukça benzemektedir ve http://www.asciitohex.com/ benzeri bir siteden ASCII’ye çevrildiğinde karakter karşılığının USEMAIL olduğu görülür.
3.Bu ipucu disk.rar dosyasının şifresinin kare koddan çıkan mail adresi olduğunu gösterir (battista1467@decifris.org). 
4.Rar dosyasının içeriğinde aşağıdaki metin  ve disk.jpg dosyası vardır. 

“mqzkqp{lnonenltptkeqxote}”
 
 ![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DiskYuvarlakKodKare/disk2.png)
 
5.Resimde bir Alberti Diski örneği vardır ve A harfi E ile, B harfi G ile yer değiştiği görülür. Elle ya da şu adresten rahatlıkla çözülebilir http://goto.pachanka.org/crypto/alberti-cipher-disk/
 ![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/DiskYuvarlakKodKare/disk3.png)
 
6.Çözüldükten sonra çıkan metin şu şekildedir  “STMCTF{DEREAEDIFICATORIA}”. 

7.De Re Aedificatori, Alberti Leon Battista tarafından yazılan ve Rönesans dönemi mimarisinin en önemli kitaplarından biridir. 

8.Dolayısıyla panele girilmesi gereken flag değeri MD5(STMCTF{DEREAEDIFICATORIA}) = 0d6c1aea74d30fdb5fb488f08d3e3375 ‘dir. 
