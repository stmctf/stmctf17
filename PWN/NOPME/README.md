## Soru İsmi: REVERSE ME OR NOP ME

## Soru Metni: 
Eğer yeterince beklersen gelecek FLAG'ı bulabilirsin.

[1c8f8fd399da56cf95f64ada316b84be.zip](https://github.com/stmctf/stmctf17/blob/master/PWN/NOPME/NOPME)


## Çözüm: 

Soruda verilen binary dosyasini acinca sleepler ile bilinmeyen bir zaman bekliyor. Ya reverse edip, printflag fonksiyonlarinin input/outputlari incelenmeli veya binary patching yapilarak sleepler nop'a cevirilmelidir.


0. ```cp NOPME NOPME_patched``` komutu ile binary patching yapacagimiz dosyayi kopyalayarak cozume hazirlaniyoruz.

1. Radare ile dosyayi yazilabilir bir sekilde aciyoruz.
```radare2 -Aw NOPME_patched``` 

```s main``` komutu ile main fonksiyonuna gidiyoruz.


```pdf``` komutu ile fonksiyonu disassemble edilmis sekilde ekrana bastiriyoruz.

```
[0x00400470]> s main
[0x00400566]> pdf
            ;-- main:
/ (fcn) sym.main 613
|   sym.main ();
|           ; var int local_30h @ rbp-0x30
|           ; var int local_28h @ rbp-0x28
|           ; var int local_20h @ rbp-0x20
|           ; var int local_18h @ rbp-0x18
|           ; var int local_10h @ rbp-0x10
|           ; var int local_8h @ rbp-0x8
|              ; DATA XREF from 0x0040048d (entry0)
|           0x00400566      55             push rbp
|           0x00400567      4889e5         mov rbp, rsp
|           0x0040056a      4883ec30       sub rsp, 0x30               ; '0'
|           0x0040056e      48c745d00409.  mov qword [local_30h], str.__no
|           0x00400576      48c745d80909.  mov qword [local_28h], str.__this
|           0x0040057e      48c745e01009.  mov qword [local_20h], str.__is
|           0x00400586      48c745e81509.  mov qword [local_18h], str.__not
|           0x0040058e      48c745f01b09.  mov qword [local_10h], str.___a
|           0x00400596      48c745f82009.  mov qword [local_8h], str.__flag
|           0x0040059e      bf12000000     mov edi, 0x12
|           0x004005a3      e85d020000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004005a8      bf01000000     mov edi, 1
|           0x004005ad      e89efeffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004005b2      bf13000000     mov edi, 0x13
|           0x004005b7      e849020000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004005bc      bf0a000000     mov edi, 0xa
|           0x004005c1      e88afeffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004005c6      bf0c000000     mov edi, 0xc
|           0x004005cb      e835020000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004005d0      bf64000000     mov edi, 0x64               ; 'd'
|           0x004005d5      e876feffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004005da      bf02000000     mov edi, 2
|           0x004005df      e821020000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004005e4      bfe8030000     mov edi, 0x3e8
|           0x004005e9      e862feffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004005ee      bf13000000     mov edi, 0x13
|           0x004005f3      e80d020000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004005f8      bf10270000     mov edi, 0x2710
|           0x004005fd      e84efeffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400602      bf05000000     mov edi, 5
|           0x00400607      e8f9010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x0040060c      bf10270000     mov edi, 0x2710
|           0x00400611      e83afeffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400616      bf00000000     mov edi, 0
|           0x0040061b      e81f020000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400620      bf10270000     mov edi, 0x2710
|           0x00400625      e826feffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040062a      bf0d000000     mov edi, 0xd
|           0x0040062f      e8d1010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400634      bf40420f00     mov edi, 0xf4240
|           0x00400639      e812feffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040063e      bf0e000000     mov edi, 0xe
|           0x00400643      e8bd010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400648      bf40420f00     mov edi, 0xf4240
|           0x0040064d      e8fefdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400652      bf0f000000     mov edi, 0xf
|           0x00400657      e8a9010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x0040065c      bf40420f00     mov edi, 0xf4240
|           0x00400661      e8eafdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400666      bf0d000000     mov edi, 0xd
|           0x0040066b      e895010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400670      bf40420f00     mov edi, 0xf4240
|           0x00400675      e8d6fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040067a      bf0e000000     mov edi, 0xe
|           0x0040067f      e881010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400684      bf40420f00     mov edi, 0xf4240
|           0x00400689      e8c2fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040068e      bf0f000000     mov edi, 0xf
|           0x00400693      e86d010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400698      bf40420f00     mov edi, 0xf4240
|           0x0040069d      e8aefdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004006a2      bf0d000000     mov edi, 0xd
|           0x004006a7      e859010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004006ac      bf40420f00     mov edi, 0xf4240
|           0x004006b1      e89afdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004006b6      bf0e000000     mov edi, 0xe
|           0x004006bb      e845010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004006c0      bf40420f00     mov edi, 0xf4240
|           0x004006c5      e886fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004006ca      bf0f000000     mov edi, 0xf
|           0x004006cf      e831010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004006d4      bf40420f00     mov edi, 0xf4240
|           0x004006d9      e872fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004006de      bf0d000000     mov edi, 0xd
|           0x004006e3      e81d010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004006e8      bf40420f00     mov edi, 0xf4240
|           0x004006ed      e85efdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004006f2      bf0e000000     mov edi, 0xe
|           0x004006f7      e809010000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x004006fc      bf40420f00     mov edi, 0xf4240
|           0x00400701      e84afdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400706      bf0f000000     mov edi, 0xf
|           0x0040070b      e8f5000000     call sym.printFlag2         ; floating_point rint(arithmetic x)
|           0x00400710      bf40420f00     mov edi, 0xf4240
|           0x00400715      e836fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040071a      bf0b000000     mov edi, 0xb
|           0x0040071f      e81b010000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400724      bf40420f00     mov edi, 0xf4240
|           0x00400729      e822fdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040072e      bf02000000     mov edi, 2
|           0x00400733      e807010000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400738      bf40420f00     mov edi, 0xf4240
|           0x0040073d      e80efdffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400742      bf0b000000     mov edi, 0xb
|           0x00400747      e8f3000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x0040074c      bf40420f00     mov edi, 0xf4240
|           0x00400751      e8fafcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400756      bf02000000     mov edi, 2
|           0x0040075b      e8df000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400760      bf40420f00     mov edi, 0xf4240
|           0x00400765      e8e6fcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040076a      bf0b000000     mov edi, 0xb
|           0x0040076f      e8cb000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400774      bf40420f00     mov edi, 0xf4240
|           0x00400779      e8d2fcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x0040077e      bf02000000     mov edi, 2
|           0x00400783      e8b7000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x00400788      bf40420f00     mov edi, 0xf4240
|           0x0040078d      e8befcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x00400792      bf0b000000     mov edi, 0xb
|           0x00400797      e8a3000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x0040079c      bf40420f00     mov edi, 0xf4240
|           0x004007a1      e8aafcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004007a6      bf02000000     mov edi, 2
|           0x004007ab      e88f000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x004007b0      bf40420f00     mov edi, 0xf4240
|           0x004007b5      e896fcffff     call sym.imp.sleep          ; int sleep(int s)
|           0x004007ba      bf01000000     mov edi, 1
|           0x004007bf      e87b000000     call sym.printFlag3         ; floating_point rint(arithmetic x)
|           0x004007c4      b800000000     mov eax, 0
|           0x004007c9      c9             leave
\           0x004007ca      c3             ret
```

2. Gorundugu uzere oldukca fazla sleep fonksiyonu var. Dilerseniz tek tek butun sleep instructionlarinin uzerine NOP yazabilirsiniz ancak uzun surecegi icin daha kisa bir cozum aramakta fayda var. Biz bu soruyu asagidaki yol ile cozmek istedik.  Daha kolay cozumler olmasina ragmen bu yontem ile yine 2-3 dakika icerisinde cozulebilmektedir.

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/NOPME/nop1.png)



3. Disassemble edilmis main fonksiyonuna baktigimiz zaman goruyoruz ki sleep icin yapilan sistem cagrilari ```e8 (call) + ****ffff (adres)``` seklinde. ```/x e8....ffff``` komutu ile opcode aramasi yaparak binary icerisindeki butun cagrilari ekrana dokuyoruz ve bunlardan main adres alani icerisindeki satirlari kopyalayarak sleeps.txt’ye kaydediyoruz.


```
#sleeps.txt icerigi 

0x004005ad hit0_2 e89efeffff
0x004005c1 hit5_2 e88afeffff
0x004005d5 hit5_3 e876feffff
0x004005e9 hit5_4 e862feffff
0x004005fd hit5_5 e84efeffff
0x00400611 hit5_6 e83afeffff
0x00400625 hit5_7 e826feffff
0x00400639 hit5_8 e812feffff
0x0040064d hit5_9 e8fefdffff
0x00400661 hit5_10 e8eafdffff
0x00400675 hit5_11 e8d6fdffff
0x00400689 hit5_12 e8c2fdffff
0x0040069d hit5_13 e8aefdffff
0x004006b1 hit5_14 e89afdffff
0x004006c5 hit5_15 e886fdffff
0x004006d9 hit5_16 e872fdffff
0x004006ed hit5_17 e85efdffff
0x00400701 hit5_18 e84afdffff
0x00400715 hit5_19 e836fdffff
0x00400729 hit5_20 e822fdffff
0x0040073d hit5_21 e80efdffff
0x00400751 hit5_22 e8fafcffff
0x00400765 hit5_23 e8e6fcffff
0x00400779 hit5_24 e8d2fcffff
0x0040078d hit5_25 e8befcffff
0x004007a1 hit5_26 e8aafcffff
0x004007b5 hit5_27 e896fcffff
```


4. Daha sonra sleeps.txt dosyasindaki her adrese NOP yazmak icin gerekli komut listesini awk ile olusturuyoruz (her nop yazimi icin iki satir gerekiyor: ```s 0xAdres``` komutu ile istenilen adrese gidiyoruz ve ```“wa nop;nop;nop;nop;nop;”``` komutu ile 5 byte NOP yaziyoruz).

```awk '{print "s " $1 "\n\"wa nop;nop;nop;nop;nop;\""}' sleeps.txt```

![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/NOPME/nop2.png)


```
#Olusan komut listesi:

s 0x004005ad
"wa nop;nop;nop;nop;nop;"
s 0x004005c1
"wa nop;nop;nop;nop;nop;"
s 0x004005d5
"wa nop;nop;nop;nop;nop;"
s 0x004005e9
"wa nop;nop;nop;nop;nop;"
s 0x004005fd
"wa nop;nop;nop;nop;nop;"
s 0x00400611
"wa nop;nop;nop;nop;nop;"
s 0x00400625
"wa nop;nop;nop;nop;nop;"
s 0x00400639
"wa nop;nop;nop;nop;nop;"
s 0x0040064d
"wa nop;nop;nop;nop;nop;"
s 0x00400661
"wa nop;nop;nop;nop;nop;"
s 0x00400675
"wa nop;nop;nop;nop;nop;"
s 0x00400689
"wa nop;nop;nop;nop;nop;"
s 0x0040069d
"wa nop;nop;nop;nop;nop;"
s 0x004006b1
"wa nop;nop;nop;nop;nop;"
s 0x004006c5
"wa nop;nop;nop;nop;nop;"
s 0x004006d9
"wa nop;nop;nop;nop;nop;"
s 0x004006ed
"wa nop;nop;nop;nop;nop;"
s 0x00400701
"wa nop;nop;nop;nop;nop;"
s 0x00400715
"wa nop;nop;nop;nop;nop;"
s 0x00400729
"wa nop;nop;nop;nop;nop;"
s 0x0040073d
"wa nop;nop;nop;nop;nop;"
s 0x00400751
"wa nop;nop;nop;nop;nop;"
s 0x00400765
"wa nop;nop;nop;nop;nop;"
s 0x00400779
"wa nop;nop;nop;nop;nop;"
s 0x0040078d
"wa nop;nop;nop;nop;nop;"
s 0x004007a1
"wa nop;nop;nop;nop;nop;"
s 0x004007b5
"wa nop;nop;nop;nop;nop;"
```

5. Cikan sonucu radare2 konsolumuza yapistirip, q ile cikiyoruz.

[NOPME_patched](https://github.com/stmctf/stmctf17/blob/master/PWN/NOPME/NOPME_patched) dosyasini calistirdigimiz zaman flagi  **STMCTF{NOPNOPNOPNOP90909090}** olarak buluyoruz.


![Preview](https://github.com/stmctf/stmctf17/blob/master/PWN/NOPME/nop3.png)


