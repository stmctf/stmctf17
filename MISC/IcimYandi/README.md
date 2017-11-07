

## Soru İsmi: {içim yandı}

## Soru Metni: 

Sadece resim. Sana verebileceğim tek şey bu.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/IcimYandi/b6d4575a18de06e94ae0b06c0b4115b7.jpg)

## Çözüm: 


1. Fotoğrafın contrast ayarlarıyla oynadıktan sonra aşağıdaki gibi binary formatta ipucu saklanmıştı.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/IcimYandi/ic1.png)

2. Binary decode ettiğimizde “Siz hala su icmediniz mi? :)” mesajı ile karşılaşıyoruz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/IcimYandi/ic2.png)


3. Daha sonra masaya dağıtılan su şişesini incediğimizde jelatinin arkasında “STEG PASS: 552-745” yazılı stickerı farketmemiz bekleniyordu. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/IcimYandi/ic3.png)

4. Steghide aracını kullanarak  flagimizi bulabilirdik.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/IcimYandi/ic4.png)
