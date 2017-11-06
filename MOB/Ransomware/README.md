
## Soru İsmi: RANSOMWARE

## Soru Metni: 

Verilen Hesap makinası uygulamasına gizlenmiş olan Ransomware uygulaması telefon üzerindeki bütün verileri şifreleyip senden fidye talep etmekte. Fakat zararlı yazılımın kodlayıcıları bir hata yapmış ve sürekli aynı şifreleme anahtarını kullanmışlar. Bakalım uygulamayı analiz edip bu anahtarı bulabilecek misin. Not: Anahtarı bulduktan sonra SHA256 hash’ini al. Bu senin flag.zip dosyanın parolası olacaktır. 

## Çözüm: 

1.Verilen calculator.apk dosyası apktool aracı ile disassamble edilir. 
AndroidManifest.xml dosyası detaylı olarak incelenir.
a) Permissionlar incelenir. Bir hesap makinası uygulaması için çok sayıda ve gereksiz izin talep ettiği farkedilir. Özellikle RECEIVE_BOOT_COMPLETED izni şüphelidir:
b) Hangi BroadcastReceiverı aktive ettiği aranır ve tespit edilir:

2.Calculator.apk dosyası unzip edilir, classes.dex dosyasına ulaşılır.
3.Classes.dex dosyası sırasıyla dex2jar + JDGUI  araçlarıyla kaynak koda dönüştürülür. 
4.advransomReceiver sınıfının arka planda çalışan advransomService sınıfını aktive ettiği anlaşılır. Ayrıca bu çağrıdan hemen önce downloadMaliciousAPK() fonksyonun da çağrıldığı görülür. Fonkyonun isminden zararlı bir davranış sergilediği anlaşılır.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/Ransomware/ran1.png)

5.Bu noktada soru 2 şekilde de çözülebilir. Ya uygulama dinamik olarak çalıştırıp gerekli Broadcast ile tetiklenip zararlı yeni .apk uygulama dosyasının indirilmesi sağlanır veya herhangi bir obfuscation kullanılmadığından direkt olarak koda harcoded olarak gömülmüş URL adresine gidilir ve zararlı .apk download edilir.
6.Biz çözümünüzü direkt URL adresine gidip zararlı .apk’yı indirme üzerine yapacağız.
7. İndirilen .apk dosyasını yukarıdaki süreçlere benzer şekilde reverse ve disassamble ettiğimizde aşağıdaki kaynak kodla karşılaşırız. Kaynak kodu detaylı incelediğimizde renklendirilmiş URL adresinden bahsi geçen anahtar değerinin indirildiğini anlarız.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MOB/Ransomware/ran2.png)


8.URL adresine gittiğimizde aşağıdaki anahtar değerini bulmuş oluruz.

9.Elde edilen dizgeyi SHA256 hash fonksyonuna soktuğumuzda flag’i içeren zip dosyasının parolasını elde etmiş oluruz.

10.Bu parolayla flag.zip dosyasını açarız.

11.zip dosyasından çıkan flag değerimiz STMCTF{simdi_decryption_zamani} dir. Bu dizgenin de MD5 hash değeri alınarak panele girilir.
