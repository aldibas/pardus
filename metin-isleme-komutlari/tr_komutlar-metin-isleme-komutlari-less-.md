## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları  / Text Manipulation

#### **less** 


</br>

</br>

**less** komutu; metin dosyalarını sayfalara bölerek terminal penceresinde görüntülemek için kullanılır. **less** komutu büyük metin dosyalarını kolayca okumayı sağlar ve arama, kaydırma ve metin içerisinde gezinme gibi işlevleri de destekler.

</br>



kullanımı şu şekildedir:
``` {.echo}
less file_name
```

<br>

Daha sonra, dosyayı okumak için "Enter" tuşuna basarak sayfalar arasında gezinebilirsiniz. Çıkış yapmak için "q" tuşunu kullanabilirsiniz. Ayrıca, daha fazla seçenek ve komut satırı seçeneği de mevcuttur, bunları "less --help" komutuyla görüntüleyebilirsiniz.

**Komutun dizilimi;**

```
less [OPTIONS] FILE
```

Komut seçenekleri : -**OPTIONS**- [-aABcCdeEfFgGiIJKLmMnNqQrRsSuUVwWX]

| Seçenek | | Açıklama |
|:--:|:--:|--|
| -/arama_kelimesi' | » |  Metin dosyasında belirli bir kelime veya ifade arar ve sonuçları listeler. |
| -F | » | Metin dosyasında yapılan değişiklikleri otomatik olarak takip eder. |
| -n | » | Arama sonuçları arasında gezinir ve bir sonraki eşleşmeyi gösterir. |
| -N | » | Dosyanın içerisindeki her satırın satır numarasını görüntüler. |
| -p | » | Arama sonuçları arasında gezinir ve bir önceki eşleşmeyi gösterir. |
| -g | » | Belirli bir sayfaya atlamak için kullanılır. |
| -q | » | Less'ten çıkmak için kullanılır. |
| -h | » | Yardım menüsünü gösterir ve mevcut tüm komutları listeler. |
|||

Bu parametreleri kullanarak ***_less_*** komutu ile dosyaları görüntüleyebilir, arama yapabilir, sayfalar arasında gezinebilir, belirli bir sayfaya atlayabilir, dosya hakkında bilgi alabilir ve belirli bir satıra gitmek için kullanabilirsiniz.

<br>

>less -N: Uçbirimde bir metin dosyası görüntülemek için kullanılan "less" komutunun bir seçeneğidir. Bu seçenek, dosyanın başındaki her satırın numarasını görüntüler.
Nasıl kullanıldığına dair örnek verilmiştir:

<br>

```
less -N /etc/updatedb.conf
```

bu komutla birlikte çıktıdaki 3.satır şu şekilde olacaktır: 

```{echo}
3 PRUNEPATHS="/tmp /var/spool /media /var/lib/os-prober /var/lib/ceph"
```

</br>

---
 [Metin İşleme Komutları/Text Manipulation -more-](./tr_komutlar-metin-isleme-komutlari-more-.md) << Önceki / Sonraki >> [Metin İşleme Komutları/Text Manipulation -head-](./tr_komutlar-metin-isleme-komutlari-head-.md)

