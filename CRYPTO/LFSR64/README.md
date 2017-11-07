
## Soru İsmi: LFSR64

## Soru Metni: 
Düşman hatlarından gelen son mesajı bir türlü çözemiyoruz. Açık mesaj anahtarla XOR’lanmış ve anahtar olarak da 64 bitlik bir LFSR çıktısı kullanılmış. Ancak ne polinomu ne de LFSR’ın ilk değerini (seed) biliyoruz. Bildiğimiz tek şey açık mesajın ilk 16 karakterin “bugunhavagunesli” olduğu. Mesajın geri kalanını da çözmemiz lazım!
1368bcdb1fd305416757edbe85a35843.zip

## Çözüm: 

1.Bu soru derin bir kriptografi bilgisi gerektirdiğinden kripto bölümündeki zor gözüken ve pek dokunulmayan sorulardan bir tanesiydi.

2.Soruda anahtar üreteci olarak 64 bitlik LFSR (Linear Feedbach Shift Register) kullanıldığı belirtilmekte. Bu üreteç doğrusal olduğundan üretecin ilk değeri ve polinomu bilinmese de 128 bitlik ardışık çıktısı biliniyorsa Berlekamp-Massey algoritması ile aynı diziyi üreten en küçük LFSR bulunabilir. Yarışmanın ilerleyen bölümlerinde bu algoritma bu ipucu olarak verildi.

3.Açık mesajın ilk 16 karakteri (128 bit) hali hazırda verilmiş. Bu durumda açık mesajın ilk 128 biti;

m(0,128) = bugunhavagunesli = 01100010011101010110011101110101011011100110100001100001011101100110000101100111011101010110111001100101011100110110110001101001

olur. Dolayısıyla cipher’ın ilk 128 biti ile xorlanırsa, LFSR’ın ilk 128 bitlik çıktısı şu şekilde bulunur.

anahtar(0,128) = m(0,128) ^cipher(0,128) = 
01100000101010100110101011100101010100010010010101010000101010100110010010000010001010001111000100111001101100111000011000000110

4.Bu diziyi üreten polinom Berlekamp-Massey algoritması ile x^64 + x^55 + x^30 + x^3 + 1 olarak bulunur.

![Preview](https://github.com/stmctf/stmctf17/blob/master/CRYPTO/LFSR64/lsfr1.png)

Polinom yardımıyla dizinin tamamı üretilerek açık mesaj bulunur.
m = 01100010011101010110011101110101011011100110100001100001011101100110000101100111011101010110111001100101011100110110110001101001010100110101010001001101010000110101010001000110011110110100001101010100010001100101111101101001011000110110100101101110010111110110111001100101010111110110011101110101011110100110010101101100010111110110001001101001011100100101111101100111011101010110111001111101

m = bugunhavagunesliSTMCTF{CTF_icin_ne_guzel_bir_gun}

MD5(STMCTF{CTF_icin_ne_guzel_bir_gun})=6B86E64B15DA1CB9BE2369355DBCB222
