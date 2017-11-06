
## Soru İsmi: ATBAŞI gidiyorlardı...

## Soru Metni: Xlp lmvnor lowftfmf wfhfmwftfnfa yri plmfhnzbr gvohraov pzbwvggrp znz rhrm rxrmwvm xrpznrblifa. Fx ilgliof yri nzprmvwvm yzshvwrbliozi. Rop ilgli klarhblmoziı hrizhrboz W Z ev X. Yriyrirmv yztor sziuovi wv ZY ev IF. Bzpzozwrtrnra nvhzq rhv SYXDFQ{GTSAACELFTEKNEBILMJCS}

## Çözüm: 
1.ATBASH kripto sistemi M.Ö 1000 civarlarında kullanılan tarihteki ilk kripto sistemlerinden birisidir. A-Z, B-Y, C-X  olacak şekilde devam eder ve aynalama sistemi olarak da bilinir. ENIGMA ise bilindiği gibi 2. Dünya savaşında Alman ordusu tarafından kullanılmış ve kırılması ile savaşın seyri değişmiştir.

2.Başlıktan ATBASH şifrelemesi kullanıldığı anlaşılmakta, yarışmanın ilerleyen bölümlerinde de ipucu olarak verilmişti. http://www.dcode.fr/atbash-mirror-cipher sitesinden çözüldüğünde ise şöyle bir metin çıkmakta. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/ATBASIgidiyorlardi/atbash1.png)

Cok onemli oldugunu dusundugumuz bir konusmayi telsizle kaydettik ama isin icinden cikamiyoruz. Uc rotorlu bir makineden bahsediyorlar. Ilk rotor pozisyonları sirasiyla D A ve C. Birbirine bagli harfler de AB ve RU. Yakaladigimiz mesaj ise HBCWUJ{TGHZZXVOUGVPMVYRONQXH}. 

3.Verilen rotor vb. kelimelerden şifreleme makinesinin ENIGMA olduğu anlaşılmakta. 
http://enigmaco.de/enigma/enigma.html ya da http://enigma.louisedade.co.uk/enigma.html siteleri kullanılarak verilen parametreler girildiğinde HBCWUJ{TGHZZXVOUGVPMVYRONQXH}. 
metninin çözümü STMCTF{ENIGMAYIDAKIRDINBRAVO} çıkmakta.

![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/ATBASIgidiyorlardi/atbash2.png)

4.Dolayısıyla doğru cevap MD5(STMCTF{ENIGMAYIDAKIRDINBRAVO}) = A59F8B06DD35EAB52C8A90998AD4C7D7

