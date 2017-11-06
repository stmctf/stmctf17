## Soru İsmi: Beni Çalıştırma

## Soru Metni: 
"Uçarım Kaçarım" firması çalışanları firmanın giriş kapısında bir USB bellek bulmuş. Firmanın sistem yöneticisi USB bellek içerisinde "beniCalistirma.exe" isimli bir dosya oldugunu tespit etmiş, bazı analizler yapmış ama hiçbir sonuç alamamış. Bu sabah da STM Zararlı Yazılım Analizi Laboratuvarı zLab'a analiz edilmesi icin exe dosyası getirildi. Dostum; analizi yapalım ama hepimiz şu anda CTF yarışmasında görevliyiz.  Bize yardimci olur musunuz? Dosyayı bizim için analiz ediver.

## Çözüm: 
1. ac78fc90b6fb7e17ec2d35e09e7b008d.zip dosyasi icerisinden beniCalistirma.exe dosyasi cikiyor. Dosya, IDA Pro veya IDA Demo ile açıldığında assembly kodlarının anlamsız olduğu görülüyor. 

2. Yarisma boyunca verilen ipuclari ve sorunun adindan da anlisilacagi gibi exe dosyasi calisabilir bir dosya degil. 

3. IDA Pro veya IDA Demo ile soz konusu dosya acildiginda Graph Overview ekranında dogrudan flag gözüküyor. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/BeniCalistirma/beniCalistirma_0.png)

3.  Graph Overview ekranında STMCTF{_Hold_the_DOOR__} flag okunabiliyor. 

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/BeniCalistirma/beniCalistirma_1.png)

4. DEF CON 23, "Chris Domas - Repsych: Psychological Warfare in Reverse Engineering" sunumunu izleyerek keyifli dakikalar gecirebilirsiniz.

