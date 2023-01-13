## Bash Kullanımı

### **BaSH Kabuğu değişkenleri**

**Değişken** için, "geçici hafızata tutulan ve her an değişebilen verileri  saklayan tanımlardır." diyebiliriz.

Kabukta **AD=Pardus** yazdığımızda **AD** isimli değişkende **Pardus** ifadesini saklamış -atamış- oluruz.

``` {.sh}
AD="Pardus" 
```

**AD** değişkeninin içeriğini bir görüntülemek istersek aşağıdaki gibi bir komut yazabiliriz.

``` {.sh}
echo Merhaba ${AD}
```

Bu komut aşağıdaki gibi bir çıktı üretecektir.

```
senol@pardus:~$ echo Merhaba ${AD}
Merhaba Pardus
```

Aşağıdaki çıktılardaki farkları inceleyiniz...

```
senol@pardus:~$ AD="PARDUS" && echo Merhaba ${AD,}
Merhaba pARDUS
```

```
senol@pardus:~$ AD="PARDUS" && echo Merhaba ${AD,,}
Merhaba pardus
```

```
senol@pardus:~$ AD="pardus" && echo Merhaba ${AD^}
Merhaba Pardus
```

```
senol@pardus:~$ AD="pardus" && echo Merhaba ${AD^^}
Merhaba PARDUS
```
</br>



>Değişkenin bellirli bir noktasından -**offset**- istediğimiz kadar karakterini de -**length**- yazdırabiliriz. **{parameter:offset:lenght}**

``` {.sh}
AD="Pardus" && echo Merhaba ${AD:0:3}
```

Bu kullanımda çıktı aşağıdaki gibi "Merhaba Par" olacaktır.
```
senol@pardus:~$ AD="Pardus" && echo Merhaba ${AD:0:3}
Merhaba Par
```

Aşağıdaki çıktılardaki farkları inceleyiniz...

```
senol@pardus:~$ ad="Pardus" && echo Merhaba ${ad:1:4}
Merhaba ardu
```

```
senol@pardus:~$ AD="Pardus" && echo Merhaba ${AD:1:}
Merhaba
```
```
senol@pardus:~$ AD="Pardus" && echo Merhaba ${AD: -3:2}
Merhaba du
```

```
senol@pardus:~$ AD="Pardus" && echo Merhaba ${AD: -3}
Merhaba dus
```

```
senol@pardus:~$ AD="Pardus" && echo " Pardus isminde ${#AD} karakter var"
Pardus isminde 6 karakter var
```
</br>

Şimdi, BaSH kabuğu başlarken tanımlanan çevre değişkenlerine bakalım. Bu değişkenler tüm kullanıcılar için ortak tanımlanıyor olabileceği gibi oturum açan kullanıcı için, kullanıcının ev dizinindeki yapılandırma dosyaları ile kendisine özel de tanımlanabilir.

Bu dosyalardan birkaçı:
```
/etc/profile

~/.profile
~/.bashrc
```

Kullanıcının ev "**~**" dizinindeki "**.profile** ve **.bashrc** dosyaları "**ls**" komutunda parametre kullanmadan görüntülenmeyecektir. **ls** komutunda "-a" parametresi "**.**" ile başlayan dosyaların da dosya listesine dahil olamsını sağlayacaktır.

``` {.sh}
ls -a
```

Kolay akılda kalması için, tam karşılığı olmasa da;
>"**.**" ile başlayan dosyalar gizli dosyalardır."

diyebiliriz.

</br>

Daha önce PS1 değişkeninden bahsetmiştik. **PS1** değişkenine atanan verileri görmek için ev dizinimizde iken **cat** komutu ile **.bashrc** dosyasını görüntüleyelim.

``` {.sh}
cat .bashrc
```

>Sadece **PS1** geçen satırları görmek için daha sonra değineceğimiz **grep** komutunu da kullanabilirdik.


``` {.sh}
cat .bashrc | grep PS1
```

>Bu şekilde oturum başlatılırken atanan çevre değişkenlerini **printenv** ya da **env** komutları listeleyebiliriz.

``` {.sh}
env
```

>Bir değişkenin içeriğini "**echo**" komutu ile yazdırabiliriz.

``` {.sh}
echo $USER
```

HOME, USER, SHELL, PWD, LANG, LOGNAME ve PATH değişkenlerinin içeriklerin yazdırınız.



### alias 


</br>
Sonraki : [Bash komut yapısı -syntax-](tr_komut-yapisi-.md)


