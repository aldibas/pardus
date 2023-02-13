## **Terminal & Kabuk -Shell- Komutları**

### Yardım Alma Komutları 

#### **which** 


</br>

**PATH** değişkeninde tanımlı konumlardaki ikili -**binary**- dosyalarda arama yapar. 


Komutun dizilimi;

```
which [options] <argüman>
```


<br>

Komut seçenekleri : -**OPTIONS**- [a]

| Seçenek | | Anlamı |
|--|:--:|--|
| -a | » | **PATH** değişkeninde tanımlanan adreslerdeki eşlenen binary -ikili- dosyaların tamamının konumunu listeler. |


<br>


**Örnekler:**


ls komutu ve klavuz dosyalarının konumunu görüntülemek için:

``` {.sh}
which ls
```


Çıktı:

```
senol@pardus:~$ which ls
/usr/bin/ls
```

---
<br>

PATH değişkeninde tanımlı yollardaki tüm **ls** konumları için:

``` {.sh}
which -a ls
```

<br>
Çıktı:

```
senol@pardus:~$ which -a ls
/usr/bin/ls
/bin/ls
```

---

<br>


</br>

 [Yardım alma komutları -whereis-](./tr_komutlar-yardim-alma-komutlari-whereis-.md) << Önceki / Sonraki >> [Basit sistem komutları --](./tr_komutlar-yardim-alma-komutlari-which-.md)

