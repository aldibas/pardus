## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **uname** 


</br>

</br>

>**type** komutu, bir Linux/Unix kabuğunda belirtilen komutun türü ile ilgili aşağıdaki bilgileri verir.

* yerleşik, **built-in**
* harici komut, **file**
* takma ad, **alias**
* fonksiyon, **function** 
* anahtar, **keyword**


</br>
Özetle "**type**" komutu, kullanıcıların belirtilen komutun ne olduğunu anlamasına ve yapılandırılmış komutların standart komutlardan ayırt edilmesine yardımcı olur. Ayrıca, bir komutun çalışması sırasında olası hataları veya yanlış yapılan yol göstermelerini önler.

Komutun dizilimi;

```
type [options] <name> [name]
```

<br>


Komut seçenekleri : -**OPTIONS**- [-afpPt]

| Seçenek | | Anlamı |
|--|:--:|--|
| -a, --all | » | Eşleşen tüm tip bilgileri listeler. |
| -p, --path | » | komutun yolunu görüntüler. |
| -P | » | Türe bakmaksızın komut dosyasını arar ve yolunu listeler. |
| -t, --type | » | Tipini görüntüler. -**alias/file/keyword/bulitin**- |


Bu seçenekler her Linux/Unix dağıtımda implemente edilmemiş olabilir.

</br>

**Örnekler:**

``` {.sh}
type type
```

Çıktı:

``` {echo}
type is a shell builtin
```

---
</br>

``` {.sh}
type cp
```

Çıktı:

``` {echo} 
cp is hashed (/usr/bin/cp)
```

---

</br>

``` {.sh}
type firefox
```

Çıktı:

``` {echo} 
firefox is /usr/bin/firefox
```
---

</br>

``` {.sh}
type while
```

Çıktı:

``` {echo} 
while is a shell keyword
```

---



``` {.sh}
type ls
```


``` {echo}
ls is aliased to `ls --color=auto'
```

---
</br>

``` {.sh}
type -a ls
```

Çıktı:

``` {echo}
ls is aliased to `ls --color=auto'
ls is /usr/bin/ls
ls is /bin/ls
```

---
</br>

``` {.sh}
type -P ls
```

Çıktı:

``` {echo}
/usr/bin/ls
```

---
</br>

``` {.sh}
type -t ls
```

Çıktı:

``` {echo}
alias
```



</br>

 [Yardım alma komutları -type-](../yardim-alma-komutlari/tr_komutlar-yardim-alma-komutlari-type-.md) << Önceki / Sonraki >> [Sistem&durum bilgisi komutları --](./tr_komutlar-sistem-komutlari-which-.md)

