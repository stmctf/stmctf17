## Soru İsmi: Odie

## Soru Metni: 
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/odie/odie0.jpeg)


## Çözüm: 
1. 6b51d5a125cf6c0eca3d1df3545b7d25.zip icerisinden odie.html isimli dosya cikiyor.odie.html sayfasi acildiginda soruda bizi karsilayan Odie isimli kedi resmi tekrar cikiyor. 
![Preview](https://github.com/stmctf/stmctf17/blob/master/WEB/odie/odie2.png)

2. odie.html dosyasina vi ile bakildiginda ise goruntu su sekilde oluyor.

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<meta name="description" content="@odie.the.cat @odiethecat" />
<meta name="keywords" content="instagram,facebook" />
<meta name="author" content="Odie" />
<title>Odie the Cat</title>
</head>
<body style="background-color:#ff9900;">
<img src="data:image/png;base64,

/9j/4AAQSkZJRgABAQAASABIAAD/4QC8RXhpZgAATU0AKgAAAAgABQESAAMAAAABAAEAAAEaAAUA
AAABAAAASgEbAAUAAAABAAAAUgEoAAMAAAABAAIAAIdpAAQAAAABAAAAWgAAAAAAAABIAAAAAQAA
AEgAAAABAAeQAAAHAAAABDAyMjGRAQAHAAAABAECAwCgAAAHAAAABDAxMDCgAQADAAAAAQABAACg
AgAEAAAAAQAAAwCgAwAEAAAAAQAAA8CkBgADAAAAAQAAAAAAAAAA/+0AOFBob3Rvc2hvcCAzLjAA
...
...
...
```

3. Header bilgilerine bakarak Instagram'da @odie.the.cat veya Facebook'da @odiethecat sayfalarini ziyaret etmeniz guzel kedi fotograflari gormenizden baska bir ise yaramiyor. [Odie sizlere tesekkur ediyor.]

4. odie.html dosyasina cat ile bakildiginda ise goruntu su sekilde oluyor.
```


<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<meta name="description" content="@odie.the.cat @odiethecat" />
<meta name="keywords" content="instagram,facebook" />
<meta name="author" content="Odie" />
<title>Odie the Cat</title>
</head>

<body>
<img src="data:image/png;base64,
/9j/4AAQSkZJRgABAQAASABIAAD/4QC8RXhpZgAATU0AKgAAAAgABQESAAMAAAABAAEAAAEaAAUA
AAABAAAASgEbAAUAAAABAAAAUgEoAAMAAAABAAIAAIdpAAQAAAABAAAAWgAAAAAAAABIAAAAAQAA
AEgAAAABAAeQAAAHAAAABDAyMjGRAQAHAAAABAECAwCgAAAHAAAABDAxMDCgAQADAAAAAQABAACg
AgAEAAAAAQAAAwCgAwAEAAAAAQAAA8CkBgADAAAAAQAAAAAAAAAA/+0AOFBob3Rvc2hvcCAzLjAA
OEJJTQQEAAAAAAAAOEJJTQQlAAAAAAAQ1B2M2Y8AsgTpgAmY7PhCfv/AABEIA8ADAAMBIgACEQED
EQH/xAAfAAABBQEBAQEBAQAAAAAAAAAAAQIDBAUGBwgJCgv/xAC1EAACAQMDAgQDBQUEBAAAAX0B
AgMABBEFEiExQQYTUWEHInEUMoGRoQgjQrHBFVLR8CQzYnKCCQoWFxgZGiUmJygpKjQ1Njc4OTpD
REVGR0hJSlNUVVZXWFlaY2RlZmdoaWpzdHV2d3h5eoOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmq
srO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4eLj5OXm5+jp6vHy8/T19vf4+fr/xAAfAQADAQEB
AQEBAQEBAAAAAAAAAQIDBAUGBwgJCgv/xAC1EQACAQIEBAMEBwUEBAABAncAAQIDEQQFITEGEkFR
B2FxEyIygQgUQpGhscEJIzNS8BVictEKFiQ04SXxFxgZGiYnKCkqNTY3ODk6Q0RFRkdISUpTVFVW
V1hZWmNkZWZnaGlqc3R1dnd4eXqCg4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrC
w8TFxsfIycrS09TV1tfY2dri4+Tl5ufo6ery8/T19vf4+fr/2wBDAAICAgICAgMCAgMFAwMDBQYF
BQUFBggGBgYGBggKCAgICAgICgoKCgoKCgoMDAwMDAwODg4ODg8PDw8PDw8PDw//2wBDAQICAgQE
BAcEBAcQCwkLEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEB">
</body>
</html>
```

5. Dosyanin satir sayisina baktigimizda ise icerigin sadece ekranda gozukenden olusmadigini goruyoruz.
```
wc odie.html 
   19672    2545  207452 odie.html
```

6. Dosyanin iceriginde STM kelimesini aratinca flag dogrudan cikiyor.
```
cat odie.html | grep STM
<STMCTF{YARI_Kor_Kedi_ODIE_nin_HAYATI}></STMCTF{YARI_Kor_Kedi_ODIE_nin_HAYATI}>
```

FLAG: STMCTF{YARI_Kor_Kedi_ODIE_nin_HAYATI}
