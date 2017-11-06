## Soru İsmi: cProjem

## Soru Metni: 
Brian Kernighan ve Dennis Ritchie'nin kitabini kurcalarken Bitwise Operators kısmını görünce gizli mesajlarımı C kodlarımın içerisinde saklayabileceğime o kadar emindim ki, kod yazdım, derledim ve şifrelemeye bile ihtiyacım yok. Sakladığım FLAG'ı bulabiliyorsan bul bakalım.

## Çözüm: 
1. 82b5f85851c228a1882ea18d22f2eb66.zip dosyasi icerisinden cProjem isimli dosya cikmaktadir. 64 bit ve Linux ELF dosyasi olmasi isleri biraz zorlastiriyor.

2. 400B93 adresinde XOR ile ilgili kısmın keşfedilmesi ilk adım. 

3. Daha sonra 34 karakterli {'_','W','Z','I','Q','[','|','g','f','a','a','s','w','t','^','+','D','N','g','n','g','c','H','k','j','t','u','n','Y','I','S','L','@','w'} degerlerin XOR'landığının bulunması ikinci adım oluyor. 

4. İki farklı XOR amacli kullanilan liste var. (Degerler decimal) 
<br>{12,2,23,9 ,5,6 ,7 ,8 ,9 ,1 ,20,12,19,14,1 ,16,17,16,1 ,2 ,6 ,12,23 ,24,5 ,16,7,28,6,30,31,24,7,9} ve 
<br>{34,3,2 ,10,3,29,28,20,23,15,10,29,11,21,21,19,18,17,13,2 ,13,4 ,21,15,10,19,8,27,6,15,24,13,8,10}. 
<br>Bunlarin bulunmasi üçüncü adım. 

5. Flag'in olusturulmasi icin sira ile iki farkli listenin kullanildigi anlasilmaktadir. CTF esnasinda asagidaki c kodu ipucu olarak da paylasilmistir. 
<br>for(z=0;z<34;z++){if((z%2)!=0){zz=(ks[z]^mask2[z]);}else{zz=(ks[z]^mask1[z]);}
<br>mask1[34] = {12,2,23,9 ,5,6 ,7 ,8 ,9 ,1 ,20,12,19,14,1 ,16,17,16,1 ,2 ,6 ,12,23 ,24,5 ,16,7,28,6,30,31,24,7,9};
<br>mask2[34] = {34,3,2 ,10,3,29,28,20,23,15,10,29,11,21,21,19,18,17,13,2 ,13,4 ,21,15,10,19,8,27,6,15,24,13,8,10};
<br>ks[34] = {'_','W','Z','I','Q','[','|','g','f','a','a','s','w','t','^','+','D','N','g','n','g','c','H','k','j','t','u','n','Y','I','S','L','@','w'};

6. Iki listenin birlestirilerek hazirlanan PYTHON kodu ve flag asagidaki sekildedir.
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/cProjem/cProjem.png)

