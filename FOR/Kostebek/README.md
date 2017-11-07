
## Soru İsmi: Köstebek

## Soru Metni: 

Şirketimizde önemli veri sızıntıları yaşandı. Ağ paketlerini inceleyerek kaçırılan veriyi bulmanı istiyoruz! 
ac6b6864c2dc3978c0a6a8cdba239dcd.zip

## Çözüm: 

1. network_analysis.pcapng dosyası wireshark vasıtasıyla açılır. Objeler seçeneğinden HTTP objeleri içerisinde yer alan confidential.zip dosyası kaydedilir.  Dosyanın şifreli olduğu anlaşılır.

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/Kostebek/kostebek1.png)

2. Ağ paketleri içerisinde XMPP ağ paketleri içerisinde yer alan mesajlaşmalar dikkatli incelenerek, şifre bulunur. Mesajlaşmalarda geçen ‘’ işaretlerinde yer alan kelimeler peşi sıra eklenir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/Kostebek/kostebek2.png)

3. Şifre girildikten sonra confidential.txt dosyası içerisinde bayrak bulunur.

![Preview](https://github.com/stmctf/stmctf17/blob/master/FOR/Kostebek/kostebek3.png)
