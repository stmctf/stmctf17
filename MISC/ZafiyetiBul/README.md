
## Soru İsmi: Zafiyeti Bul

## Soru Metni: @areyouaresearcher’daki exploit kodu dünya çapında etki yaratan hangi güvenlik açığının kodudur?

## Çözüm: 

1. @areyouaresearcher’daki exploit kodunun hangi güvenlik açığının kodu olduğu soruluyordu. Burada ilk olarak @areyouaresearcher hesabını internet üzerinden bulmak gerekiyordu. Hesap kod paylaşım platformu olan Github’da bulunmaktaydı.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/ZafiyetiBul/zaf1.png)

2. Github üzerinde bulunan @areyouaresearcher hesabında ctf17.py kodunu okuyarak exploit kodunun hangi güvenlik açığına karşı yazıldığını bulmak gerekmekteydi.

![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/ZafiyetiBul/zaf2.png)

3. Kod Google üzerinde de araştırıldığı taktirde MS17-010 kodlu zafiyet için yazıldığı bulunabilirdi.
![Preview](https://github.com/stmctf/stmctf17/blob/master/MISC/ZafiyetiBul/zaf2.png)

Bulunan zafiyet STMCTF bayrak formatına göre md5 değeri bulunur.

$echo -n 'STMCTF{MS17-010}' | md5sum

aa69084aa15efe4cfc5d8053ec918a3f

