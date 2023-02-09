## **Terminal & Kabuk -Shell- Komutları**

### Yardım Alma Komutları 

#### **whatis** 


</br>

Komutların kılavuz sayfalarındaki  **NAME** kısmında geçen kısa açıklamalarını görüntüler.





Komutun dizilimi;
```
whatis [options] <name>
```


<br>

Komut seçenekleri : -**OPTIONS**- [c,d,l,L,m,M,,v,w,...]

| Desen | | Anlamı |
|--|:--:|--|
| -r, --regex | » | Bu seçenek ile "düzenli ifadeler" **regular expression** kullanılabilir. |
| -w, --wildcard | » | Bu seçenek ile joker karakterler kullanılabilir. |
| -M, --manpath | » | Kılavuz dosyası konumunu belirler. Farklı dillerde yardım almak için kullanılabilir. |
| -?, --help | » | Kullanımı ile ilgili yardım görüntüler. |
| --usage | » | Komut dizilimini görüntüler. |
| -V | » | Versiyon -sürüm- bilgisini görüntüler. |

<br>


**Örnekler:**


ls komutunun kısa açıklaması için;

``` {.sh}
whatis ls
```


Çıktı:

```
senol@pardus:~$ whatis ls
LS (6)  - display animations aimed to correct users who accidentally enter LS instead of ls .
ls (1)  - list directory contents
```

---
<br>
Türkçe yardım almak için:

``` {.sh}
whatis --manpath=/usr/share/man/tr/ ls
```

<br>
Çıktı:

```
senol@pardus:~$ whatis --manpath=/usr/share/man/tr/ ls
ls (1)    - dizinlerin içindekileri listeler
```

---

<br>
Listeleme komutları -"ls" ile başlayan- ile ilgili yardım almak için: 

``` {.sh}
man --wildcard "ls*"
```

Sonraki komut için Ctrl+D, iptal etmek için Ctrl+C tuşlarını kullanabilirsiniz.


---


</br>

 [Yardım alma komutları -man-](./tr_komutlar-yardim-alma-komutlari-man-.md) << Önceki / Sonraki >> [Yardım alma komutları -whereis-](./tr_komutlar-yardim-alma-komutlari-whereis-.md)

