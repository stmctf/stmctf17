

## Soru İsmi: Derin Araştırma

## Soru Metni: 

Kaynağı belirsiz bir yazılımın indirilmesi sonucu makinelerin birinde zararlı aktivite ile karşılaşılmıştır. Derin bir araştırma sonucu dosya sisteminden zararlı aktiviteye sebep olan yazılımı bulup bayrağı yakalayabilecek misin?
0d4b03de6ec80c61b2e90213b6d4ce8e.zip

## Çözüm: 

1.Strings komutuyla disk.dump dosyasın raw formatlı olduğunu bulduktan sonra. Dosya sistemi analiz araçları kullanılarak, sırasıyla dos formatı, block-size 512-byte sektör olduğu bulunur. İncelenmek istenen disk alanının NTFS formatlı ve başlangıç değerinin 63 olduğu anlaşılır.

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/DerinArastirma/der1.png)

2.Fls komutu vasıtasıyla dosya tablolarının timeline’ı oluşturulur. Mactime ile dosya düzeni bulunur. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/DerinArastirma/der2.png)

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/DerinArastirma/der3.png)

3.Aranan dosyanın Kullanıcı klasörü içerisinde yer alan tftpd.zip dosyası olduğu anlaşılır. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/DerinArastirma/der4.png)

4.Tam adresi alındıktan sonra raw formatlı dosya içerisinden icat vasıtasıyla çıkartılır.

icat disk.dump -o 63 -i raw -f ntfs -b 512 11515-128-3 > tftpd.zip

5.Sıkıştırılmış dosya açıldıktan sonra strings komutu ile bayrak bulunur.

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/DerinArastirma/der5.png)
