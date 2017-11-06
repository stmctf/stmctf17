
## Soru İsmi: RENGARENK

## Soru Metni: 

Bana sayıyı 5 saniye içinde söyle FLAG'i kap!

nc 192.168.$MASANO.5 6666

## Çözüm: 

Sunucuda belirlenen portta çalışan servis yarışmacıya base64 değer dönmektedir. 
Yarışmacıdan beklenen sunucuya belli bir süre içinde istenen sayıyı doğru olarak yollaması.

![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/RENGARENK/ren1.png)

1. Yarışmacı base64 değerini decode ettiği zaman 20 karakterli bir sayı olan PNG dosyası elde etmektedir.

2. Her rakamın yer aldığı kutu farklı renktedir. Aşağıdaki gibi color code vardır:
color = {"1":"red", "2":"blue", "3":"white", "4":"yellow", "5":"green", "6":"pink", "7":"orange", "8":"purple", "9":"magenta", "0":"gray"}

![Preview](https://github.com/stmctf/stmctf17/blob/master/CODING/RENGARENK/code.png)


3. Resim boyutu 400x30 şeklindedir. Her rakamın kutusu 20x30 luktur.

4. Yarışmacıdan beklenen color code u keşfedip her kutunun ilk pixelindeki yani, [0,0],[20,0],[40,0]....[380,0] pixellerindeki RGB değeriyle rakamı eşleştirip sunucuya yollayacak bir kod yazmasıdır.

5. Aşağıdaki python scripti sorulan soruyu cevaplayarak flag i alabilecektir:

```python
#!/usr/bin/python

from random import *
from pwn import *
from PIL import Image, ImageFont, ImageDraw, ImageEnhance
import socket

host = "X.X.X.X"
port = 6666

conn = remote(host,port)
# sunucudaki base64 degeri al.
data=conn.recvuntil("\n")

# sorulan soruyu base64 decode ederek png dosyasina yazarak resmi olustur.
fo = open("question.png", "wb")
fo.write(data.decode('base64'))
fo.close()

# sayinin oldugu png dosyasini ac.
im= Image.open("question.png")
pix = im.load()
size = im.size

# sayilarla RGB degerlerini eslestir.
number=""
colorcode = {\
(128, 128, 128):"0",\
(255, 0, 0):"1",\
(0, 0, 255):"2",\
(255, 255, 255):"3",\
(255, 255, 0):"4",\
(0, 128, 0):"5",\
(255, 192, 203):"6",\
(255, 165, 0):"7",\
(128, 0, 128):"8",\
(255, 0, 255):"9"}

x=0
number=""

# her kutu icin ilk pixelin (sol ust kose) RGB degerini oku. [0,0], [20,0],[40,0]....[380,0] lardaki RGB degerleri. ve bu degerleri rakamlarla eslestir. 
while x<20:
	rgb=pix[20*x,0]
	number += colorcode[rgb]
	x += 1

print "number: "+number

# hesaplanan sayiyi sunucuya gonderek sunucudan donen flag i al.
conn.send(number+"\n")
print conn.recvline()+"\n"
print "flag = "+conn.recvline()

conn.close()
```






