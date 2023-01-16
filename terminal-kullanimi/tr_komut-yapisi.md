## **Bash Kullanımı**

### **Komut Yapısı -Syntax-**

</br>

Bir komutun;
* işlevine,
* dizilimine,
* parametrelerinin işlevlerine,
* yazarına,
* lisansına
**man** komutu ile bakabiliriz.

``` {.sh}
man echo
```

Biz aşağıda genel anlamda bir komutun diziliminin nasıl olduğuna bakacağız.

Bir komutun genel olarak kullanım biçimi, 

```
<command>  [--OPTION]  [PATH]  [PATH]
```

şeklindedir. 

Köşeli parantezler ( [ , ] ) komutun kullanımında zorunlu olmayan kısımları ifade etmek için kullanılmıştır. Buradan parametrelerin ve adreslerin (path=yol) her zaman ya da her komutta kullanılma zorunluluğunun olmadığı sonucunu çıkartabiliriz. Örneğin “clear” komutu uçbirim ekranını temizler ve dosya sistemi üzerinde işlem yapmadığından kullanımında herhangi yol tanımı yapılmaz.

#### Parmetre / Opsiyon / Anahtar

Seçenekler -**option**- ise komutların ana işlevlerinin ekstra özellikleriyle kullanılmasını sağlar.  Örneğin detaylı dosya listesini görüntülemek istiyorsanız dosya listeleme komutu olan “**ls**” komutunu “**-l**” opsiyonu ile “**ls -l**” şeklinde kullanmanız gerekir. Bu opsiyonlar -option-, parametre ya da anahtar adıyla da belirtilebilirler. Ancak parametre deha geniş bir tanımdır ve komuta gönderilen değerleri de kapsayabilir.

>**Opsiyonlar** ise genellikle, tek karakter kısaca ya da açık hali ile kullanılabilirler. Tek karakter ile gösterimlerde “**-**” işareti ile kullanılırken açık hali ile kullanırken “**--**” karakterleri ile yazılır. Çoğu durumlarda opsiyonu kullandığımız noktada bir yol tanımı -dosya/dizin adı- beklenmiyorsa "**-**" ya da "**--**" işaretleri kullanılmayabilir. 

Bu kısmı örneklemek gerekirse "**.**" ile başlalay dosyaları listelemek için aşağıdaki her iki yazım şekli de kullanılabilir.

``` {.sh}
ls -a
```

``` {.sh}
ls --all
```

>Opsiyonları kullanırken tek "**-**" işaretine birden fazla seçenek girebileceğimiz gibi ayrı ayrı da belirtebiliriz.

Aşağıdaki yazım şekilleri aynıdır.


Tüm dosyaları -**a:all**- detaylı biçimde -**l:long**- boyuta -**S:size**- göre ters -**r:reverse**- sırada listele.


``` {.sh}
ls -a -l -S -r
```

``` {.sh}
ls -alSr
```

``` {.sh}
ls -alS --reverse
```

#### PATH/Yol Tanımı






</br>
Sonraki: []()

