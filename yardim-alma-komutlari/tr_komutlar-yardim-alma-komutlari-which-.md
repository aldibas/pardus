## **Terminal & Kabuk -Shell- Komutları**

### Yardım Alma Komutları 

#### **whereis** 


</br>

Komutların çalıştırılabilir ve kaynak dosyaları ile kılavuz sayfalarının konumlarını görüntüler.





Komutun dizilimi;
```
whereis [options] <name>
```


<br>

Komut seçenekleri : -**OPTIONS**- [b,m,s,u,B,M,S,f,l,h,v...]

| Desen | | Anlamı |
|--|:--:|--|
| -b | » |  |
| -m | » |  |
| -s | » |  |
| -h, --help | » | Kullanımı ile ilgili yardım görüntüler. |
| -V, --version | » | Versiyon -sürüm- bilgisini görüntüler. |

<br>


**Örnekler:**


ls komutu ve klavuz dosyalarının konumunu görüntülemek için:

``` {.sh}
whereis ls
```


Çıktı:

```
senol@pardus:~$ whereis ls
ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz
```

---
<br>

**ls** komutunun sadece konumu için:

``` {.sh}
whereis -b ls
```

<br>
Çıktı:

```
senol@pardus:~$ whereis -b ls
ls: /usr/bin/ls
```

---

<br>

**ls** komutunun kılavuz -manual- dosyasının konumu için: için: 

``` {.sh}
whereis -m ls
```


```
senol@pardus:~$ whereis -m ls
ls: /usr/share/man/man1/ls.1.gz
```



<div style="color:red;"> 

.

</div>

---


</br>

 [Yardım alma komutları -whatis-](./tr_komutlar-yardim-alma-komutlari-whatis-.md) << Önceki / Sonraki >> [Yardım alma komutları -which-](./tr_komutlar-yardim-alma-komutlari-which-.md)

