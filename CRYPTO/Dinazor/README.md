## Soru İsmi: Dinazor

## Soru Metni: 

Öz geçmişini çok beğendik. Seninle birlikte çalışmak isteriz. Bu soruyu çöz, gel işe başla. Ama vaktin kısıtlı, zaman kaybetme. 
```
Flag		: 7SSYSIK1_L8LLM_I}RBY8_TF6LM7J2Y_
Key Table : ZLABE2 STMOU7 CRYPD9 1854HG {_}60K FIN3JV
```

## Çözüm: 

1. 1854 yılında tanıtımı yapılan PlayFair Cipher kullanılmıştır. Soruda verilen KEY içerisinde yardımcı olması için bazı kelimeler var. Kelimeler başa gelecek şekilde KEY bölünmeye başlanınca 6x6 Key Table oluşmaya başlıyor. ZLAB, STM ve CRYP birer ipucu.

2. Flag'i 2'li gruplara boluyoruz.
```
Flag : 7SSYSIK1_L8LLM_I}RBY8_TF6LM7J2Y_
Flag Bolunmus : 7S SY SI K1 _L 8L LM _I }R BY 8_ TF 6L M7 J2 Y_
```

3. Key Table'i 6'li gruplara ayiriyoruz.
```
ZLABE2
STMOU7
CRYPD9
1854HG
{_}60K
FIN3JV
```

4. Sonra klasik PlayFair Cipher  çözümü ile flag çıkıyor.
```
7S SY SI K1 _L 8L LM _I }R BY 8_ TF 6L M7 J2 Y_
ST MC TF {G IT _T AT IL _Y AP _I SI _B OS VE R}
```
FLAG: STMCTF{GIT_TATIL_YAP_ISI_BOSVER}

