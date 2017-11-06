

## Soru İsmi: Balküpü

## Soru Metni: 8192 bitlik öyle bir modulus kullanmışlar ki kırmaya değil bakmaya bile cesaret edemiyoruz. Bir şekilde kırılmalı bu metin, vazgeçmek yok!
f0fc1bc65d283fc5c065a364de26ebaa.zip

## Çözüm: 
1.Standart dışı RSA gerçeklemelerinde (bu soruyu oluşturmak için kullanılan kullanılan Python Crypto modülü dahil) mesaj bloğuna dolgulama (padding) yapılmayıp küçük bir exponent (e=3 gibi) kullanıldığında şifreli metnin uzunluğunun modulusun (8192 bit) uzunluğunu geçmeme ihtimali vardır. Soru metnine bakıldığında şifreli mesajın (c) boyunun modulustan (n) çok daha küçük olduğu görülmekte.

2.Bu durumda çok basit bir şekilde şifreli metnin küp kökü alındığında açık mesaja ulaşılabilir! 

3.Gerek sorunun başlığında gerekse yarışma boyunca verilen ipuçlarıyla (I: Mesaj boyu oldukça küçük ve dolgulama (padding) yapılmamış. II: Küp kök mü alsak? )  bu durum anlatıldı ancak ne yazık ki çözüme ulaşan olmadı. 

4.Aşağıdaki python kodundan faydalanabiliriz.

https://github.com/stmctf/stmctf17/blob/master/CRYPTO/Balkupu/cuberoot.py


![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/Balkupu/balkupu1.png)

5.Metni_oyle_bir_yazdik_ki_kupunu_alsak_da_modulusun_boyunu_gecmiyor. Yani_STMCTF{Padding_yoksa_RSA_8192_bile_kirilabiliyor}

Dolayısıyla MD5 özet değerimiz = MD5(STMCTF{Padding_yoksa_RSA_8192_bile_kirilabiliyor} ) = 4A66DA3D0266044A3004C2E8816A14C1


