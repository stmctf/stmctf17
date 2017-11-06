
## Soru İsmi: ŞA the DARKNIGHT

## Soru Metni: Alfred Batman’e ulaştırmak istediği dosyaları ziplerek saklıyormuş. Ama kendisi akıllı olduğu için flag.zip parolasını en az 60 karakter falan vermiş. Verilen .mpeg dosyasının içindeki bilgiler bilmediğimiz bir şifreleme yöntemiyle kriptolanmış ve/veya içinde bilgi kodlanmıştır. Pes etme ve içerdiği mesajı bul. 
439eec60a5ce2520a4078dac350c6e4b.zip
flag.zip

## Çözüm: 

1.Verilen darknight.mpeg dosyası strings komutu ile incelenir.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/SAtheDarknight/dk1.png)

2.Elde edilen  binary code text haline dönüştürülür. Çıkan text aşağıda gösterilmiştir.Yapısından bir Base64 kodu olduğu anlaşılır.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/SAtheDarknight/dk2.png)

3. Elde edilen bu çıktı decode edildiğinde bu kez aşağıdaki gibi bir metinle karşılaşılır.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/SAtheDarknight/dk3.png)

4. Bu aşamada elde edilen metin anahtarsız CEASER-13(ROT13) şifreleme algoritmasıyla decrypt edilir ve aşağıdaki açık metne kavuşulur.
![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/SAtheDarknight/dk4.png)

5.Bu noktada BatmanveRobin sha256 hash değeri alınarak flag’i içeren zip dosyasının parolası bulunur.

$ echo -n "BatmanveRobin" | sha256sum
4e490270fa48fb14365e0a326711f158814d8e634e624f172c7ba0b146fe76b0

6.Flag.txt açıldığında nihai flagin aşağıda gösterilen değer olduğu bulunur.

STMCTF{Gotham_artik_daha_guvenli!}

EEF1795A3A93F66AEBC067880783B1FB

