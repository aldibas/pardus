# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### Dosya ve Dizin Silme -rm- / -rmdir-

</br>

#### **rmdir** -ReMove DIRectory-

"**rmdir**" komutu boş dizinleri silmek için kullanılır. 

</br>

**Komutun dizilimi;**

``` {echo}
rmdir [OPTIONS] SOURCE 
```

<br>

Seçenekler: -**OPTIONS**- [-pv --help ] 

| Seçenek | | Açıklama |
|--|:--:|:--|
| -p, --parents | » | İç içe olan boş dizinleri siler |
| -v, --verbose | » | İşlem yapılan dizinleri çıktı olarak listeler. |
||

</br>

Çalışma dizinimizdeki yapıyı "**tree**" komutu ile ağaç yapısı şeklinde görüntüleyelim:

``` {.sh}
tree
```

Bir önceki konuda çalışma dizinimizde dosya ve dizinller aşağıdaki gibiydi.


``` {echo}
.
└── debian
    ├── GNU-Linux
    ├── GNU-Linux.SNL
    ├── pardus.txt
    └── Pardus.txt

1 directory, 4 files
```

Buradaki "debian" dizinini rmdir komutu ile kaldırmayı deneyelim.

``` {.sh}
rmdir debian
```

Bu durumda kabuk standart hataya -**stderr**- şu mesajı dönecektir.

``` {echo}
rmdir: failed to remove 'debian': Directory not empty
```

rmdir komutunu örneklemek için "**mkdir**" komutu ile çalışma dizinimizde "pardus" isminde bir dizin olşturalım.


``` {.sh}
mkdir pardus
```


``` {.sh}
tree
```

``` {echo}
.
├── debian
│   ├── GNU-Linux
│   ├── GNU-Linux.SNL
│   ├── pardus.txt
│   └── Pardus.txt
└── pardus

2 directories, 4 files
```

"**pardus**" dizinini **rmdir** komutu ile silelim.

``` {.sh}
rmdir pardus
```


``` {.sh}
tree
```

Çıktı

```
.
└── debian
    ├── GNU-Linux
    ├── GNU-Linux.SNL
    ├── pardus.txt
    └── Pardus.txt

1 directory, 4 files
```
</br>

>Dizin oluşturmak imin kullandığımız "**mkdir**" komutunda "**-p / --parents**" parametresi ile iç içe aynı anda dizin oluşturmak mümkün olduğu gibi, dizin silme işleminde "**--parents**" parametresi ile iç içe olan boş dizinler tek bir "**rmdir**" komutu ile silinebilir. 

</br>

Örnek:

``` {.sh}
mkdir -p pardus/senol/06
```

"**tree**" komutu çıktısı:

```
.
├── debian
│   ├── GNU-Linux
│   ├── GNU-Linux.SNL
│   ├── pardus.txt
│   └── Pardus.txt
└── pardus
    └── senol
        └── 06

4 directories, 4 files
```

</br>

**pardus, senol** ve **06** dizinlerini silelim:

``` {.sh}
rmdir -p pardus/senol/06
```
"**tree**" komutu çıktısı:

```
.
└── debian
    ├── GNU-Linux
    ├── GNU-Linux.SNL
    ├── pardus.txt
    └── Pardus.txt

1 directories, 4 files
```

<br>

---

</br>



#### **rm** (ReMove)

</br>

"**rm**" komutu dosya ve dizinleri silmek için kullanılır.


</br>

**Komutun dizilimi;**

``` {echo}
mv [OPTIONS] SOURCE DEST
```

<br>

Seçenekler: -**OPTIONS**- [-fiIrRdv --backup --help ] 

| Seçenek | | Açıklama |
|--|:--:|:--|
| -f, --force | » | Silme onayı istemez ve olmayan doyalar için "dosya yok" uyarısı vermez. |
| -r, -R, --recursive | » | Dizinleri de siler. |
| --dir | » | Boş dizinleri siler. |
| -i | » | Her bir dosya için silmeden önce sorar. |
| -I | » | Silme işlemi 3 ten fazla dosyayı ilgilendiriyorsa 1 defa onay ister. |
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

**Örnekler:**

Çalışma dizinimizdeki yapıyı hatırlayalım :

``` {.sh}
tree
```

Bir önceki konuda çalışma dizinimizde dosya ve dizinller aşağıdaki gibiydi.


``` {echo}
.
└── debian
    ├── GNU-Linux
    ├── GNU-Linux.SNL
    ├── pardus.txt
    └── Pardus.txt

1 directory, 4 files
```

"**debian**" klasöründeki dosyalardan 1 tanesi hariç diğerlerini silelim ve silmeden atlayacağımız dosyaya silme işlemi esnasında karar verelim.

``` {.sh}
rm -i debian/*
```

[Yes/No] onayında sadece bir dosyayı "**no"" / ""n"" olarak geçtikten sonra çıktı:

``` {echo}
.
└── debian
    └── Pardus.txt

1 directory, 1 file
```

"**debian**" dizinini silelim:

``` {.sh}
rm  debian
```

Yukarıdaki **rm** komutunda "**debian**" dizini içinde dosya olduğundan değil, bir dizin oladuğundan dolayı silinmeyecek ve standart hata olarak aşağıdaki çıktıyı dönecektir.

``` {echo}
rm: cannot remove 'debian': Is a directory
```

"**debian**" dizinini **--recursive** opsiyonu/seçeneği ile silebiliriz.


``` {.sh}
rm -R debian
```

</br>

>Dosya özellikle de **dizin** silme çok dikkatli yapılması gereken bir işlemdir.

</br>

---
 [Dosya Yönetimi / Dosya Taşıma -mv- ](tr_dosya-tasima-mv-.md) << Önceki 
