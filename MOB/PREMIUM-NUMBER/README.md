

## Soru İsmi: PREMIUM-NUMBER

## Soru Metni: Verilen Satranç programının aslında Premium numaralara sürekli SMS atan bir
Dialer tipi zararlı olduğu ay sonu gelen kabarık faturadan anlaşılmakta.
Senin görevin bu numarayı bulmak. Bu sayede yetkili mercilere gerekli şikayeti
yapabileceğiz.

Flag'in ise soruda verilen Flag.zip dosyasının içinde saklı. Boşuna Brute force yapmaya çalışma zaman yetmiyor biz denedik :) Bunun yerine uygulama içinden tespit ettiğin telefon numarasının SHA256 hashini al. İşte burdan elde edeceğin sonuç seni flagine kavuşturacak parolan olacak.
6c7235643de4bebd2a10820a3b7853f6.zip


## Çözüm: 
1. Chess.apk dosyası verilmiş, içinde zararlı kod barındırdığı belirtilmiştir. Öncelikte uygulama dosyasının unzip edilip binary kodları barındıran classes.dex dosyasına erişilmesi gerekir. Classes.dex dosyasını daha sonra kullanmak üzere kenarda tutalım.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem1.png)

2. Bu aşamada Chess.apk dosyası apktool aracı’nın d opsyonu ile disassemle edilir ve okunabilir AndroidManifest dosyasına erişilir.


apktool d chess.apk


![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem2.png)

3. AndoidManifest.xml dosyası incelenir.Dikkat edilmesi gereken noktalar izinler, aktiviteler, receiverlar ve intentlerdir.Bu noktada izinler incelendiğinde RECEIVE_BOOT_COMPLETED izninin oldukça şüpheli olduğu görülür.Aşağıya inip Receiverlar incelendiğinde bu broadcasti zlab.stm.com.premiumnor1.chessReceiver isimli sınıfının dinlediği anlaşılır. Bir diğer şüpheli sınıfımız da hemen alttında yer alan zlab.stm.com.premiumnor1.chessService isimli service bileşenidir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem3.png)

4. Sıra ilk aşamada extract ettiğimiz classes.dex dosyasını tersine mühendislik yöntemiyle kaynak koduna döndürme aşamasına gelmiştir.Bu amaç için dex2jar+JDGUI ikilisi açık kaynak çözümler olarak tercih edilebilir.


sh d2j-dex2jar.sh classes.dex


5. Kaynak kodu incelediğimizde chessReceiver sınıfının BOOT_COMPLETED Broadcastini alır almaz arka planda çalışacak olan chessService sınıfını çağırdını anlarız. Bu durumda ilgi odağımızı chessService sınıfına çeviririz.



6. ChessService sınıfını incelediğimizde şüpheli bir reflection çağrısıyla karşılaşırız.Reflection yapısını detaylı incelediğimizde ismi maskelenmiş bir sınıfın ve ismi maskelenmiş bir methodunun çağrıldığını görürüz.
![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem4.png)


7. Bu noktada Runtime’da kullanılan class’ın isminin str2, bu classa ait methodun isminin ise str3 olduğunu gözlemleriz. Ayrıca bu methodun str1 argümanıyla çağrıldığını anlarız. Bu noktadan itibaren sıra bu dizgelerin ne olduğunu çözmeye gelir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem5.png)

 str2 ve str3 dizgelerinin çalışma zamanında functionFoo isimli fonkyonun çalıştırılması sonucunda elde edildiği anlaşılmaktadır. FunctionFoo() fonkyonunu gidip incelemeye alırız.
 Kaynak kodu inceleyip anladığımızda aslında fonksyonun bir Ceaser Cipher olduğu anlaşılmaktadır.Cipher’ın girdilerini decipher ettiğimizde karşımıza çıkan 2 değer;
android.telephony.SmsManager
sendTextMessage
dizgeleridir. Bu sınıf ve metodun SMS text message atmak için kullanılan sınıf ve o sınıfa ait method olduklarını anlarız. Methodun imzasını incelediğimizde aldığı argümanlardan birinin SMS göndereceği telefon numarası olduğu anlaşılmaktadır.O halde str1 dizgesi aradığımız gizli bilgi olan premium number değerinin kendisi olduğu anlaşılmaktadır.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem6.png)

8. str1 dizgesinin nasıl elde edildiğine döndüğümüzde aşağıdaki reklendirilmiş satırla karşılaşırız;
Sırasıyla “” içinde verilen dizgenin get() fonksyonundan gelen değerle Encrption fonkyonuna sokulduğu, çıkan değerin de Base64Decoder fonkyonuna girdi olarak girdiğini görürüz.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem7.png)

9. get()fonksyonuna gidip baktığımızda assets folderından .txt uzantılı bir dosyayı okuduğunu anlarız.Dosyayı gidip okuduğumuzda bu değerin EncryptionFunc() dosyasının anahtar değeri olduğu anlaşılır. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem8.png)

Anahtar değer;
17 adet sıfır değerinin ardından da STM harfleridir

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem8.png)

10. Sıra bu anahtar değerin ve anlamsızlaştırılmış dizgenin EncrptionFunc() fonksyonu içinde nasıl işlendiğini anlamaya gelir. Aşağıdaki fonkyon detaylı incelendiğinde basit bir XOR işlemi yapıldığı anlaşılır. Fonksyon bilinen 2 değerle çalıştırılır, çıktı elde edilir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem10.png)

11. Elde edilen çıktı son olarak da aşağı da gösterilen Base64Decoder() fonkyonuna gönderilir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/PREMIUM-NUMBER/prem11.png)

12. Fonkyon sembolik veya gerçek olarak çalıştırıp bakıldığında;
3805052939136 numaralı telefona ulaşılır ki SMS gönderilen telefon numarasının bu olduğu anlaşılır.

13. Bu değerin 256 Hash değeri alındığında flagi içeren dosyanın parolası bulunur.

echo -n "3805052939136" | sha256sum
bab8773e366b559fcf2053403b92b67c1465ed0fe6cca529786c95ba61ed4deb

14. Elde edilen parola ile .zip dosyası açılır.

15. zip dosyasının içinden ulaşılan STMCTF{Tisikkirler_superman} flag değerinin MD5 hash değeri alınarak nihai sonuç elde edilir.
