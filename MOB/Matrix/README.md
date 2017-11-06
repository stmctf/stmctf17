

## Soru İsmi: Matrix

## Soru Metni: Gerçek sandığın spotify uygulaması aslında bir zararlı ve senin rehberine senden habersiz hiç tanımadığın bir ajanın numarasını kaydediyor. Ajanın ismini bul SHA256 ile hashle bulduğun değer flag.zip dosyasının parolası. Hadi durma flag seni bekliyor.

## Çözüm: 

Verilen calculator.apk dosyası apktool aracı ile disassamble edilir. AndroidManifest.xml dosyası detaylı olarak incelenir.
Permissionlar incelenir. Bir hesap makinası uygulaması için çok sayıda ve gereksiz izin talep ettiği farkedilir. Özellikle RECEIVE_BOOT_COMPLETED izni şüphelidir. Hangi BroadcastReceiverı aktive ettiği aranır ve tespit edilir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/Matrix/mat1.png)

BOOT_COMPLETED ile tetiklenen Receiver sınıfının com.spotfy.music.songReceiver
olduğu anlaşılır.

2. Calculator.apk dosyası unzip edilir, classes.dex dosyasına ulaşılır.


3. Classes.dex dosyası sırasıyla dex2jar + JDGUI  araçlarıyla kaynak koda dönüştürülür.

4. sonReceiver sınıfının kaynak kodu detaylı incelendiğinde şunlar farkedilir.
getString() fonksyonu kullanılmıştır. Bu fonksyon Strings.xml dosyasından bir değer okumak için kullanılan bir fonksyondur. Ayrıca daha sonra String.xml dosyasından elde edilen değerin bir DownloadManager sınıfı objesinin Request() fonksyonuna parametre olarak gönderildiği anlaşılır. ki Uri.parse(….) kullanımı da göz önüne alındığında girilen argümanın bir URL adresi olduğu anlaşılır.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/Matrix/mat2.png)

5. Bu noktadan sonra String.xml dosyasında anlamlı bir URL adresi aranmaya başlanır.
Aramaların çoğunda zararlı repackage edildiğinden çeşitli resmi spotify subdomain adresleriyle karşılaşılır ancak son noktada;
http://dpaste.com/3QMJVWN.txt adresi bulunmuş olur. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/Matrix/mat3.png)

6. Bahsi geçen adrese gidildiğinde aranan değerin Smith olduğu bulunur.

7. Smith değerinin SHA256 değeri alınıp flag.zip dosyasının parolası bulunur.

8. Flag değerinin STMCTF{what_is_matrix} olduğu anlaşılır



