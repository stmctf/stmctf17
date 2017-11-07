
## Soru İsmi: 6 Ustu Karakter

## Soru Metni: 

Bana en az 6 karakterli oyle bir x degeri ver ki ben de sana FLAG'i vereyim.

nc 192.168.$MASANO.5 3333

## Çözüm: 

Sunucuda belirlenen portta çalışan servis yarışmacıya random ürettiği 6 karakterli bir sayının sha1(md5(x)) değerinin ilk 6 karakterini vermektedir.
Yarışmacıdan 6 karakterli bu sayıyı 5 saniye içerisinde hesaplayıp sunucuya göndermesi beklenmektedir.

Yarışmacı 5 saniyeden az bir surede sorulan soruyu cevaplayacak bir script hazırlamalıdır. Aşağıdaki python scripti sorulan soruyu cevaplayarak flagi alabilecektir:

```python
#!/usr/bin/python

import hashlib
from pwn import *
import sys

host = "X.X.X.X"
port = 3333

conn = remote(host,port)
data = conn.recvuntil("\n")

#6 karakterli sayi
candidate = 100000

#sunucudaki soruyu parse ederek sha1(md5(x)) değerini aliyor.
target=(data.split(" ")[16])
print "question: "+data
print "sha1(md5(x)): "+target

#6 karakterli butun sayilari deneyerek hepsinin sha1(md5(sayi)) degerini hesapliyor.
while candidate<1000000:
	md5hash_object = hashlib.md5(str(candidate))
    md5 = md5hash_object.hexdigest()

	sha1hash_object = hashlib.sha1(md5)
	sha1 = sha1hash_object.hexdigest()[:6]

	#deger sorulan sorudaki degere esitse sunucuya göndererek sunucudan donen cevabi aliyor.
	if (sha1 == target):
		print "x: "+str(candidate)
		conn.send(str(candidate)+"\n")
		print "flag = "+conn.recvline()
		break
	candidate = candidate + 1

conn.close()
```

