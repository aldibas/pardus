## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları 

#### **tail** 


</br>

</br>

**tail** komutu; bir dosyanın sonundan belirli bir sayıda satırı görüntülemek için kullanılır. Bu, özellikle büyük dosyaları okurken çok faydalı olabilir. 

</br>



Temel kullanımı şu şekildedir:
``` {.sh}
tail file_name
```

_**tail**_ komutu, temel kullanımında bir dosyanın son 10 satırını ekrana yazdırır. Aşağıdaki komutu kullanarak bir dosyanın son 10 satırını görüntüleyebilirsiniz:

<br>

**Komutun dizilimi;**

```
tail [OPTIONS] FILE
```

Komut seçenekleri : -**OPTIONS**- [-cfFnqsvz --pid --max-unchanged-sats]

| Seçenek | | Açıklama |
|:--:|:--:|--|
| -n --lines | » |  -n seçeneği, belirli bir sayıda satırın görüntülenmesini sağlar. Örneğin, yandaki komutla bir dosyanın sondan, girilen sayı kadar satırını görüntüleyebilirsiniz.|
| -f | » | Bir dosyanın sonundan itibaren yeni eklenen satırları gerçek zamanlı olarak ekrana yazdırır. Bu seçenek genellikle log dosyaları gibi sürekli olarak güncellenen dosyalar için kullanılır.|
| -c --bytes | » | belirli bir sayıda byte'ın görüntülenmesini sağlar. Aşağıdaki komutla bir dosyanın sondan, girilen byte değeri kadar byte'ını görüntüleyebilirsiniz. |
| -q | » | birden fazla dosya görüntülendiğinde her dosyanın başlıklarını görmezden gelir. Aşağıdaki komutla dosya1 ve dosya2 dosyalarının son 10 satırını, başlıklarını görmezden gelerek görüntüleyebilirsiniz.|
|||

<br>

>**Bazı Örnekler:**

<br>

 Aşağıdaki komut example.log dosyasının son 10 satırını görüntüler ve dosya güncellendiğinde otomatik olarak eklenen satırları da gösterir:

```
tail -f example.log
```
Bu komut, example.log dosyasının son 10 satırını standart çıktıya yazdırır ve dosya güncellendikçe yeni satırları da görüntüler. tail -f komutu, log dosyalarının takibi gibi birçok senaryoda yararlıdır. Eğer Ctrl + C tuşlarına basarsanız, tail -f komutundan çıkabilirsiniz.

<br>

Belirli Bir Sayıda Satır Görüntüleme:

```
tail -n 2 /etc/ucf.conf 
```
-n seçeneği, belirli bir sayıda satırın görüntülenmesini sağlar. Örneğin, yukarıdaki komutla bir dosyanın son 2 satırını görüntüleyebilirsiniz. 

<br>

>Ayrıca -n komutu kullanmadan da yalnızca sayı değeri girerek komutu 
çalıştırabilirsiniz : 

```
tail -2 /etc/ucf.conf 
```

<br>

Uçbirim çıktısı şu şekilde olacaktır.
```
# Please note that only one of conf_force_conffold and
# conf_force_conffnew should be set.
```

</br>

---

 [Metin işleme komutları -head-](./tr_komutlar-metin-isleme-komutlari-head-.md) << Önceki / Sonraki >> [Metin işleme komutları -multitail-](./tr_komutlar-metin-isleme-komutlari-multitail-.md)

