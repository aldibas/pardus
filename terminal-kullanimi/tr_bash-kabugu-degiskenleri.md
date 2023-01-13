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
senol@pardus:~$ AD="Pardus" && echo Merhaba ${AD:1:4}
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


</br>

Sonraki : [Bash komut yapısı -syntax-](tr_komut-yapisi-.md)


