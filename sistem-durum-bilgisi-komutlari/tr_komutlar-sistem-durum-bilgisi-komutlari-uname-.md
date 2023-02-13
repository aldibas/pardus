## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **uname** 


</br>

</br>

**uname** kurulu sistem bilgilerini görüntüler.

Bu bilgiler;

* Çekirdeğin ismi, **kernel name**
* Çekirdeğin derlenen sürümü, **kernel release**
* Çekirdek sürümü, **kernel versiyon**
* İşlemci türü, **processor**
* İşletim Sistemi, **Operatin System**
* Donanım platformu, **hardware platform** 
* anahtar, **keyword**


</br>


Komutun dizilimi;

```
uname [options] 
```

<br>


Komut seçenekleri : -**OPTIONS**- [-sanrvmpio]

| Seçenek | | Anlamı |
|--|:--:|--|
| -a, --all | » | Aşağıdaki tüm bilgileri listeler. |
| -s, --kernel-name | » | Çekirdek ismi. -varsayılan olarak görüntülenir- |
| -n, --nod-name | » | Cihazın hostname bilgisi. |
| -r, --kernel-release | » | Çekirdeğin derlenen sürümü. |
| -v, --kernel-version | » | Çekirdek sürümü. |
| -m, --machine | » | Makina donanım adı. |
| -p, --processor | » | İşlemci türü. / -unknown- |
| -i, --hardware-platform | » | Donanım platformu. / -unknown- |
| -o, --operating-system | » | İşletim sistemi. |
| --version | » | **uname** versiyon, lisans, yazın |


Bu seçenekler her Linux/Unix dağıtımda implemente edilmemiş olabilir.

</br>

**Örnekler:**

``` {.sh}
uname
```

Çıktı:

``` {echo}
Linux
```

---
</br>

``` {.sh}
uname -a
```

Çıktı:

``` {echo} 
Linux pardus 5.10.0-21-amd64 #1 SMP Debian 5.10.162-1 (2023-01-21) x86_64 GNU/Linux
```

---

</br>

``` {.sh}
uname -r
```

Çıktı:

``` {echo} 
5.10.0-21-amd64
```
---

</br>

``` {.sh}
uname -v
```

Çıktı:

``` {echo} 
#1 SMP Debian 5.10.162-1 (2023-01-21)
```

---



``` {.sh}
uname -m
```


``` {echo}
x86_64
```

---
</br>

``` {.sh}
uname -o
```

Çıktı:

``` {echo}
GNU/Linux
```
---
</br>

``` {.sh}
uname --version
```

Çıktı:

``` {echo}
uname (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Written by David MacKenzie.
```

---
</br>



</br>

 [Yardım alma komutları -type-](../yardim-alma-komutlari/tr_komutlar-yardim-alma-komutlari-type-.md) << Önceki / Sonraki >> [Sistem & durum bilgisi komutları -clear-](./tr_komutlar-sistem-durum-bilgisi-komutlari-clear-.md)

