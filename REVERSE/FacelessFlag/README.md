

## Soru İsmi: Faceless Flag

## Soru Metni: 
Faceless flag 300 puanını katletmeden gerçek yüzünü bulmalısın.

32ada5b75430c524df16bf3b1428e65e.zip

## Çözüm: 

1. asm uzantılı dosyayı indirdikten sonra 32 bit ve nasm syntaxı ile yazıldığı anlaşılır ve buna göre assemble ve link işlemleri resimdeki gibi yapılır.Assemble işlemi yaparken daha rahat debug edebilmek için -F parametresi ile debug bilgisi formatını belirliyoruz. 

```
sudo nasm -f elf32 -F dwarf -g xor.asm
ld -m elf_i386 -o xor xor.o
```
2. gdb ile programı debug etmeye başlıyoruz.
```
gdb xor
```
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa4.png)

3. Kodun akış mantığına baktığımız zaman _start’ın başında stack’e  data pushlayıp 7 sefer dönen  ilk loop’un (loop)   mov ecx,[esp+28-(7-ecx)*4] satırında bu pushlanan dataları geri alıp bswap ve not(Reverse Byte Order)  işlemine taabi tutarak    [R_B_Order] değişkenine atıyor.

4. ilk loopun sonuna breakpoint koyup [R_B_Order]  değişkeninin sonucuna bakarsak; STMCTF{but_not_real_flag!!!} olarak atandığını görüyor olacağız.
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa5.png)
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa6.png)

5. ikinci loopa (loop2) baktığımız zaman msg(STMCTF{Yes_i_am_the_flag!!!})  ve R_B_Order(STMCTF{but_not_real_flag!!!}) değşkenlerini alıp xorlayıp GCC__Version değişkene atadağını görüyoruz. 

6. üçüncü loopda (loop3)  stack’e  data pushlayıp 7 sefer dönen  loopun mov ecx,[esp+28-(7-ecx)*4] satırında bu pushlanan dataları geri alıp bswap ve not(Reverse Byte Order)  işlemine taabi tutarak    [NASM__Version] değişkenine atıyor.
call printf satırına breakpoint atıp NASM__Version değerine baktığımız zaman;

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa7.png)
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa8.png)

7. call printf satırında loop4’ün altında printf kısmına bakarsak bir sytemcall çağrıldığını görüyoruz.Burda eax’e atadığı değere baktığımıza(1) çağırdığı systemcall’un print yerine exit systemcall’u olduğu anlayıp programımızın düzgün şekilde devam etmesi için call printf kısmını etkisiz hale getirmemiz gerekiyor.(İsterseniz gdb’de nop işlemi ile değiştirebilir , instruction pointer’ı call printf’in altına gösterebilir isterseniz assembly kodunu  değiştirip tekrardan assemble ve link edebilirsiniz.) Ben burda instruction pointerı editleyerek devam ettim.

8. loop4'e baktığımız zaman loop2’ye çok benzdeğini göreceksiniz fakat burda kodun akış şemasında bir bozukluk olduğunu fark etmek gerek.

loop2'de loopun başında 
```
  mov ecx,[msg+ebx]
  mov edx,[R_B_ORDER+ebx] 
```

değişkenlerden dataları alıp ecx ve edx attığını sonrasında ikisini xorladığını görüyoruz.

loop4'de ise:
```
  mov ecx,[GCC__Version+eax]
  mov ebx,[GDBObj__Version+eax]
```

değişkenlerden dataları alıp ecx ve ebx attığını sonrasında ise ecx ve edx xorladığını göreceksiniz fakat biz edx’e hiç değer atamıyoruz.


Burdan anlaşılacağı üzere 

  mov ebx,[GDBObj__Version+eax] satırındaki ebx’i  edx ile değiştirmemiz gerek.


Kodun akışındaki bir diğer bozukluk ise loop2’de xor işlemine tabi tutulan değer bir önceki loopdan(loop) elde edilen değer(R_B_ORDER). Fakat loop4 ‘de GDBObj__Version kullanılıyor.GDBObj__Version değişkenini decode ettiğiniz zaman “nerderhardergeekerstronger” şeklinde bir string göreceksiniz xorlarda kullanılan karakter sayısının tutmaması NASM__Version değişkeninin anlamlı olup kullanılmaması ve loop2-loop4 arasındaki benzerliğin yakalanmasından   bu değişkenin yanlış olduğuna karar vermenizi bekledik.

mov ebx,[GDBObj__Version+eax] satırındaki GDBObj__Version değişkeninin 
NASM__Version değişkeni ile değiştirmemiz gerek.

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa1.png)

8. adımın sonunda  “mov ebx,[GDBObj__Version+eax]” satırının son hali 
mov edx,[NASM__Version+eax] oluyor.

9. Bir onceki adımda bulduğumuz hatalı satırı isterseniz assembly kodunda tekrar yazıp derleyip ve link edip çalıştırabilirsiniz isterseniz de direk debug işlemi sırasında instruction olarak editleyebilirsiniz.
(Ben instruction editlemeyi gösteriyor olacağım.)
![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa2.png)

0x0804814e ve  0x0804814+4  adresleri 
mov ebx,[GDBObj__Version+eax]  instructionı ve datanın  olduğu adreslerdir.
biz bu adresleri  mov edx,[NASM__Version+eax] şeklinde değiştirmiş olduk.

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa9.png)

10. Değiştirdikten sonra loop4’ün sonuna breakpoint koyup stack’e bakarsanız;

![Preview](https://github.com/stmctf/stmctf17/blob/master/REVERSE/FacelessFlag/fa10.png)

STMCTF{Flag_is_Eldad_Eilam} olan doğru flagi buldunuz demektir.
md5 değerini alarak submit ediyoruz.

