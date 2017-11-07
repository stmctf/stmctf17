## Soru İsmi: Satır - Sütun

## Soru Metni: 
27.08.2011 tarihli Old School Emulation Center (TOSEC) Naming Convention PDF dosyasının Dördüncü sayfanın, yedinci satırının, onbirinci kelimesinin, ikinci harfi O'dur.  O zaman bu nedir?
```
STMCTF{12010101120202022501010301020203010202021901020126010402250201011701040222020204010101032001010425020403260301091705050425031104}
```
## Çözüm: 

1. PDF dokümandan sorudaki O harfini bulabildiyseniz, rakamları ayrabilmek gerekiyor. 

2. Sayfa - Satır - Kelime - Harf olarak düzenlenmiş. PDF kitap 26 sayfa olunca her bir bölümün 2 rakam ile ifade edileceği düşünülebilir. 

3. Sayfa (2) - Satır (2) - Kelime (2) - Harf (2) = 8 rakam . Elimizde bulunan sayı grubunu 8'li sayı gruplarına bölelim.

```
12010101
12020202
25010103
01020203
01020202
19010201
26010402
25020101
17010402
22020204
01010103
20010104
25020403
26030109
17050504
25031104
```

4. Bu grubu da 2'li sayı gruplarına bölelim.
```
12 	01 	01 	01
12 	02 	02 	02
25 	01 	01 	03
01 	02 	02 	03
01 	02 	02 	02
19 	01 	02 	01
26 	01 	04 	02
25 	02 	01 	01
17 	01 	04 	02
22 	02 	02 	04
01 	01 	01 	03
20 	01 	01 	04
25 	02 	04 	03
26 	03 	01 	09
17 	05 	05 	04
25 	03 	11 	04
```

5. 12'nci Sayfanın, 01'inci Satırının, 01'inci Kelimesinin, 01'inci harfi B'dir. 

```
12 	01 	01 	01 	B
12	02	02	02	u
25	01	01	03	l
01	02	02	03	m
01	02	02	02	a
19	01	02	01	c
26	01	04	02	a
25	02	01	01	T
17	01	04	02	a
22	02	02	04	m
01	01	01	03	S
20	01	01	04	e
25	02	04	03	n
26	03	01	09	l
17	05	05	04	i
25	03	11	04	k
```

6. Tüm harfler çıkınca flag BulmacaTamSenlik olarak çıkıyor. Soruda da STMCTF{} arasına rakamlar koyulduğu için flag STMCTF{BulmacaTamSenlik} olarak bulunur.
