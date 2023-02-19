## **Terminal & Kabuk -Shell- Komutları**

### Dosya Yönetimi -Listeleme-

#### **ls** -LiSt-


</br>

**ls** dosya listeleme komutudur. Belirtilen konum ya da çalışma dizini içeriklerini alfabetik olarak listeler. Listelemeyi **boyut, tarih** gibi alanlara göre sıralanacak şekilde değiştirebiliriz.


``` {.sh}
ls
```

Bu kullanım var ise çalışma dizinindeki -**pwd**- dosyaları listeler. Dizinleri de "dosya" ile ifade edebilir ya da tanımı, "dosya ve dizinleri listeler" şeklinde belirtebiliriz.


</br>

**Komutun dizilimi;**


```
ls [OPTIONS] [FILE] ...
```

<br>

Komut seçenekleri : -**OPTIONS**- [-aAbBcCdDfFgGhHiIklLmnNopqQrRsStTuUvwxXz1] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -a, --all | » | "**.**" ile başlayan dosyaları gizlemez. |
| -b, --escape | » | Basılamayan karakterler öncesi **"\\"** karekteri ile gösterim. -space- |
| -B, --ignore-backups | » |  "**~**" ile biten dosyaları listelemez.  |
| --color[=koşul] | » | Dosya türüne göre renklendirme. **auto, never, always** |
| **-d, --directory** | » | dizinlerin içeriklerini değil kendisini listeler. |
| -F, --classify | » | Sınıfa göre isimlerin sonuna ***/=@\|** karakterlerinden birini ekleyerek listeler. |
| --file-type | » | Türe göre isimlerin sonuna **/=@\|** karakterlerinden birini ekleyerek listeler. Çalıştırılabilir -**\***- dosyaları işaretlemez |
| -h, --human-readable | » | Boyut bilgisini birimlere dönüştürerek -**kolay okunablir**-  görüntüler. **16G, 20M, 10K**  |
| -i, --inode | » | Her bir dosyayı index numarası ile listeler. |
| -l, -- | » | Uzun -detaylı- biçiminde listeleme yapar. |
| -r, --reverse | » | Sıralamayı tersine çevirir. |
| -R, --recursive | » | Alt dizinlerin içeriklerinşi de listeler. |
| --sort=sözcük | » | Sözcüğe göre sıralama yapılır. **size, time, extension, version** |
| -S | » | Boyuta göre sıralama yapar. |
| -t,  | » |  |
|-Z, --context |  » | Dosyaların **SELinux** güvenlik bağlamını listeler. |





**ls** çıktı Örnekleri:


``` {.sh}
ls --all
```

"**.**" ile başlayan dosyalar da listeye dahil ediliyor.

``` {echo}

```


---

``` {.sh}
ls
```

**ls** komutu ile alacağımız çıktıda görüntü şu şekilde olacaktır:

```
```
---


``` {.sh}
ls -
```


```

```

---



``` {.sh}
ls -
```


``` {echo}
```

---


``` {.sh}
ls -
```


``` {echo}
```

---

---


``` {.sh}
ls -
```


``` {echo}
```

---

---


``` {.sh}
ls -
```


``` {echo}
```

---

---


``` {.sh}
ls -
```


``` {echo}
```

---

---


``` {.sh}
ls -
```


``` {echo}
```


---



---

Tüm; 

``` {.sh}
ls
```

``` {echo}
---

</br>

>**ls** komutu ile aldığımız listeyi bir dosyaya yazdırabiliriz. 

---


``` {.sh}
ls -
```


``` {echo}
```

---

---


>**ls** komutu ile aldığımız çıktıya başka bir komuta giriş -input- olarak gönderebiliriz.

listede **root** ifadesi geçen satırlar:

```
ls -l | grep root
```


</br>

---

 [Dosya Sistemi Hiyerarşisi](../unix-gnu-linux-dosya-sistemi-yapisi/tr_unix-gnu-linux-dosya-sistemi-yapisi.md) << Önceki / Sonraki >> [Dosya Yönetimi -Kopyalama- -cp-](./tr_dosya-yonetimi-dosya-kopyalama-cp-.md)

