## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları 

#### **grep** 


</br>

**`grep`** komutu, metin dosyalarında belirli bir kelimeyi ya da bir deseni -pattern- arar. Elbette buradaki "dosya" ifadesi, aynı zamanda bir uygulamanın çıktısıdır. "**|**" karakteri ile yönlerndirme konusunda benzer uygulamalar yapmıştık.

<br>

Temel kullanım örnekleri;



``` {echo}
grep aranacak-kelime/desen file-name 
```

"**grep**" komutunun "**stdin**" (standart giriş) üzerinden de veri alması durumunda kullanım şekli:

``` {echo}
<command> |  grep aranacak-kelime/desen
```

</br>

**Komutun dizilimi;**


```
GREP [OPTIONS] PATTERNS [FILE] [FILE] ...
```

<br>

Komut seçenekleri : -**OPTIONS**- [-AbsentTEuv --help --version] 

Düzenli ifade "**regex**" stili seçme seçenekleri; 
| Seçenek | | Açıklama |
|--|:--:|--|
| -E, --extended-regexp | » | Gelişmiş düzenli ifadeler -**regex**- |
| -F, --fixed-strings | » | **tab** karakterlerini **^I** olarak görüntüler  |
| -G, --basic-regexp | » | BRE -Basic regular expression- Temel düzenli ifade dili.|
| -P, --perl-regexp | » |  PCRE -Perl-compatible regular expressions- **Perl** dili. |

"**Desen**" eşitleme/kontrol seçenekleri; 
| Seçenek | | Açıklama |
|--|:--:|--|
| -i, --ignore-case | » | Arama işlemini **büyük/küçük** harf duyarlılığı olmadan yapar. |
| -w, --word-regexp | » | Yalnızca kelimenin **tamamıyla** eşleşen satırları yazdırır. |
| -v, --invert-match | » | Belirtilen desene **uymayan** satırları yazdırır. |
| -x, --line-regexp | » | Belirtilen desenin **tüm satır** ile eşlenmesini gerektirir. |

"Genel çıktı **output**" kontrol seçenekleri; 
| Seçenek | | Açıklama |
|--|:--:|--|
| -c --count | » | Desene uyan satırların sayısını ekrana yazdırır. |
| --color | » | Çıktıda belirtilen desen renklendirme ile vurgulanır. |
| -l, --files-with-match | » | Desene uyan dosya adlarını ekrana yazdırır. |
| -L, --files-without-match | » | Desene uymayan dosya adlarını ekrana yazdırır. |
| -o, --only-matching | » | Tüm satır yerine sadece desen eşlemesini yazar. |
| -q, --quiet, --silent | » | Çıktı üretmez, işlem durumunu -exit code- tutar. $? =0/1 |
| -s, --no-messages | » | Kaynak dosya yoksa hata mesajını yazmaz.  |

"Çıktı satırları **Line**" kontrol seçenekleri; 
| Seçenek | | Açıklama |
|--|:--:|--|
| -A NUM, --after-context=NUM | » | Desen ile birlikte alttaki N satır. |
| -BNUM, --before-context=NUM | » |Desen ile birlikte üstteki N satır.  |
| -C NUM, --context=NUM | » | Desen ile birlikte alt ve üstteki N satır. Ayıraç: "--" |

"Dosya"/"dizin" seçimi; 
| Seçenek | | Açıklama |
|--|:--:|--|
| -a --text | » | Binary dosyayı metin dosyası gibi işler. |
| -r, --recursive | » | Deseni alt dizinlerde de arar. |
| -R, --dereference-recursive | » | Deseni konumdaki linklerde de arar. |
|||


</br>




**grep** örnekleri:

</br>

"linux.txt" dosyasında ilk harfi büyük "Pardus" ifadesini içeren satırları listeleyelim.

``` {.sh}
grep Pardus linux.txt
```


``` {.sh}
cat linux.txt | grep Pardus 
```


---
</br>

"file.txt" dosyasında BÜYÜK/küçük harf ayrımı yapmadan "hello" ifadesini içeren satırları listeleyelim.

``` {.sh}
grep -i hello file.txt
```

---
</br>

Bir ifadeyi bir konumdaki tüm dosyalarda arayalım...

``` {.sh}
grep -r 127.0.0.1 /etc
```

---
</br>

Sonuçları dosyaya yazdırma:

"/etc/passwd" dosyasında "bash" ifadesini içeren satırları ev dizinimizdeki shell.txt dosyasına yazalım...

``` {.sh}
grep bash /etc/passwd > ~/shell.txt 
```


---
</br>

Birden fazla ifadeyi arama:

"/etc/passwd" dosyasında "root" **veya** "senol" ifadesini içeren satırları yazdıralım...

``` {.sh}
grep -e root -e senol /etc/passwd 
```

---
</br>


Arama sonuçlarını satır numaraları ile yazdırma:

"group" dosyasında "sudo" ve "lpadmin" gruplarının bulundukları satırları **satır numaraları** ile yazdıralım...

``` {.sh}
grep -ne sudo -e lpadmin /etc/group 
```

---
</br>
Belirli uzantıya sahip dosyalarda arama yapmak/yapmamak:

Çalışma dizininde sadece "**.sh**" uzantılı dosyalarda "hello" kelimesini arayalım...

``` {.sh}
grep -r --include=*.sh hello .
```


Çalışma dizininde "**.sh**" uzantılı dosyalar **haricindeki** dosyalarda "hello" kelimesini arayalım...

``` {.sh}
grep -r --exclude=*.sh hello .
```

---

</br>

Düzenli ifadeleri (regular expressions) kullanarak arama yapmak:

"/etc" konumundaki dosyalaeda "**host**" ifadesini arayalım.

``` {.sh}
grep -r '\shost\s' /etc/
```

>bu önekte "**\s**" boşluk karakterini gösterir ve bu kollanımda "hostname" / "localhost" gibi ifadeler arama sonuçlarında listelenmemiş sadece host içeren satırlar listelenmiştir. Elbette "-w" seçeneği ile de buradaki sonuç alınabilir ancak düzenli ifadelere göre arama yapmak çok daha detaylandırılabilecek bir konudur.

</br>

#### **pgrep** -Process grep-

</br>

`pgrep` komutu, çalışan bir işlemin süreç numarasını  -**process ID**- bulmak için kullanılır.


`pgrep firefox` komutu uygulandığında Firefox tarayıcısının süreç numarası -**PID**- yazdırılacaktır.

</br>

>Genel olarak, bir komutun başındaki "**p**" karakteri "**process**", "**n**" katakteri **network**, "**x**" karakteri grafik arabirim -**GUI**-, "**z**" karakteri "**zip**" anlamına gelir. 
</br> **Örnek komutlar:** `pkill` , `ngrep` , `nstat` , `xmessage` , `xclock` , `xcowsay` , `xkill` , `xrdp` , `xmore` , `xless` , `zcat` , `zmore` , `zless` , `zdiff` 

</br>

#### **ngrep** -Network grep-
</br>

Ngrep komutu, ağ trafiğini dinleyerek belirli bir deseni filtrelemek için kullanılır. Kullanımı grep komutuna benzer. 



**Komut dizilimi:**

```echo
ngrep [seçenekler] pattern [capture]
```

</br>
Örnekler:

```sh
ngrep -q example.com tcp
```



TCP paketlerinde "example.com" adresinin geçtiği tüm paketleri gösterir:



---



```sh
ngrep -q -d any 'GET /' 'port 80'
```

Bu komut, ağ trafiğini dinleyerek, HTTP portu 80'e gelen tüm paketleri filtreleyerek "GET /" kalıbını içeren paketleri yakalar. "q" seçeneği, çıktının sadece yakalanan paketlerin içeriğini -istek URL'i- gösterir.

Bu örnekte "**any**" kısmında dinlenmek istenen **ağ arayüz aygıtı** -NIC- belirtilebilir.

</br>

---

 [Sistem & Durum Bilgisi Komutları -df-](../sistem-durum-bilgisi-komutlari/tr_komutlar-sistem-durum-bilgisi-komutlari-df-.md) << Önceki / Sonraki >> [Metin İşleme Komutları/Text Manipulation -more-](./tr_komutlar-metin-isleme-komutlari-more-.md)

