## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları / Text Manipulation

#### **more** 



</br>

**more** komutu; uzun metin dosyalarını okumak ve dosya içeriğinde gezinmek için kullanılır. Dosya içeriğini sayfalar halinde -ekran- görüntüleyerek uzun dosyalar için kullanıcıya okuma kolaylığı sağlar. 

</br>


>**more** ile alınan çıktıca sayfa sayfa -ekran- ilerlemek için **boşluk -space-**, satır satır ilerlemek için **giriş -enter-** tuşları kullanılır. Ekran ekran yukarı aşağı yönlü hareket için yön tuşları da kullanılabilir. Sayfa sayfa alınan çıktıda sayfa satır sayısı değiştirilebilir. **-n, --lines**

</br>

**Komutun dizilimi;**

```
more [OPTIONS] FILE
```

Komut seçenekleri : -**OPTIONS**- [-dlfpcsun]

| Seçenek | | Açıklama |
|:--:|:--:|--|
| -n, --lines | » | Sayfa boyutunu belirtilen satır sayısına göre ayarlayarak görüntüler. |
| -c, --clean-print | » | Kaydırma -scroll- yapmadan  her sayfayı en üstten yazarak görüntüler.Bu seçenek, daha temiz bir görünüm elde etmek istediğinizde kullanışlıdır. |
| -f | » | Alt satıra taşan satırlar listelenecek satır sayısını etkilemez. |
| -l | » | Alt satıra taşan uzun satırlar ayrı tatırmış gibi işlem görür -sayılır-.  |
|||

<br>

>**Örnekler:**

<br>

Kullanıcı dosyasını her terminal ekran ekran görüntüsünde -scroll- 5 satır olacak şekilde görüntüleyelim.


``` {.sh}
more -n 5 /etc/passwd
```


``` {.sh}
more -5 /etc/passwd
```

``` {.sh}
more --lines=5 /etc/passwd
```

---

</br>

>**more** komutunda belirli bir sayfadan itibaren görüntüleme işlemi yapılabilir. 


``` {.sh}
more +2 /etc/passwd
```

>**more** komutu çıktı ekranında  **/** karakterinden sonra desen -patern- girilerek düzenli ifadeye -regex- göre arama yapılabilir. -**/\<patern>**- 

>**more** komutu çıktı ekranında  **?** ile kullanılabilecek tuş ve işlevleri listelenebilir. Bu işlevler:


| Tuş | | İşlev |
|:--|:--:|--|
| q / Q | » | Çıkış |
| \<return> | » | Sonraki satır. |
| \<space> | » | Sonraki sayfa. |
| /\<patern> | » | Belirtilen deseni -**patern**- arar. |
| !\<command> | » | Belirtilen kabuk komutunun çıktısını görüntüler. |
| :n | » | Sonraki dosyaya geçer. -**n**ext- |
| :p | » | Önceki dosyaya geçer. -**p**revious- |
| :f | » | Görüntülenen dosyanın adı ve aktif satır numarasını yazar.  |
|||


<br>
Daha fazlası için yardım belgesini görüntüleyebilirsiniz:

```
more --help
```
Bu komut, "more" komutu için yardım belgesini görüntüler ve kullanım örnekleri sunar.

>"**more**" komutu, sayfa sayfa görüntüleme işlemini gerçekleştirir ve özellikle büyük dosyaların yönetimi için faydalıdır. Ancak, kullanıcıların büyük dosyaları işlerken "less" komutunu kullanmaları daha verimli olabilir.

</br>

---
 [Metin İşleme Komutları/Text Manipulation -cat-](./tr_komutlar-metin-isleme-komutlari-cat-.md) << Önceki / Sonraki >> [Metin İşleme Komutları/Text Manipulation -less-](./tr_komutlar-metin-isleme-komutlari-less-.md)

