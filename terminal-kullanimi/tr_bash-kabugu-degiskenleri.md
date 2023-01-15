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

HOME, USER, SHELL, PWD, LANG, LOGNAME ve PATH değişkenlerini içeriklerin yazdırınız.

Konunun daha iyi anlaşılması için PATH değişkenini detay örnek ile inceleyelim.

``` {.sh}
echo $PATH
```
Çıktı:

```
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
```

Yukarıdaki çıktıda da gördüğünüz gibi **harici** çalıştırılabilir komutların bulundukları konumlara **-bin-** bir yol tanımı yapılmış. Dolayısı ile **ls** yazdığımızda çalışma dizinimizde olamayan uygulamaları çalıştırabiliyoruz. Bu nasıl mümkün oluyor? 

Eğer **PATH** değişkeni ile **bir yol** tanımı yapılmamış olsaydı çalıştırmak istediğimiz bir komutun tam adresini -yolunu- yazmak zorunda kalacaktık. 


>**Yerleşik komutlar**, kabuğun kendisinde bulunup başka bir program çağırmadan doğrudan kabuk tarafından yürütülen komutlardır. 


Şimdi PATH değişkeninin içeriğini sıfırlayalım. Ancak **PATH** değişkenin tekrar eski değerine **hızlıca** döndürmek için **YOL** isminde bir değişkene aktaralım. 

``` {.sh}
YOL=$PATH
```

Artık **YOL** değişkeni ile **PATH** değişkenlerinin içerikleri aynı.

**PATH** değişkenin içeriğini "**unset**" komutu ya da aşağıdaki şekilde sıfırlayabiliriz. -**unset PATH**-

``` {.sh}
PATH=""
```

Şimdi örnek birkaç harici komut çalıştırmayı deneyelim...

``` {.sh}
whoami
```

Çıktı:

```
-bash: whoami: No such file or directory
```

---

``` {.sh}
ls
```

Çıktı:
```
-bash: ls: No such file or directory
```

---

Artık bu **harici** komutları adreslerini yazarak çalıştırabiliriz.

``` {.sh}
/usr/bin/whoami
```

``` {.sh}
/usr/bin/ls
```

</br>

Ancak, **yerleşik** -dahili- komutların kullanımında bir değişiklik yok.

``` {.sh}
echo "echo, kabuğun kendisinde olan yerleşik bir komuttur."
```

</br>

>Bir komutun yerleşik ya da harici bir komut olup olamdığına "**type**" komutu ile bakabiliriz. Örneğin; **type echo**

</br>

``` {.sh}
type echo
```

Çıktı:

```
echo is a shell builtin
```

---

``` {.sh}
type whoami
```

Çıktı:

```
whoami is /usr/bin/whoami
```

---

``` {.sh}
type ls
```

Çıktı:

```
ls is hashed (/usr/bin/ls)
```
ya da

```
ls is aliased to `ls --color=auto'
```

---
</br>

Üst satırdaki "**aliased**" kelimesinin nereden geldiğine bakalım:

</br>

### Takma Adlar -**alias**- 
</br>

Yerleşik ya da dış komutları kullanırken kabu üzerinde sık kullandığımız komutların yine sık kullandığımız parametreleri var ise bunları sürekli yazmak zaman alacağı gibi parametrenin ne olduğunu da hatırlamamızı ya da kılavuz dosyalarına -man pages- bakmamızı gerektirir. İşte tam da bu noktada **alias** komutu bizi bu durumdan kurtaracaktır.

>alias komutu ile bir veya daha fazla komutu bir isim ile ifade edebiliriz. Çoğu kabukta sık kullanılan komutlar **rc dosyalarında**
tanımlı gelebilir. Örneğin BaSH kabuğu için (.bashrc) dosyasında  alias içeren satırları ***grep alias ~/.bashrc** ile listeleyebiliriz.


Konuyu basit bir örnek ile ele alalım:

**USB** aygıtlarımız için **lsusb**, PCI aygıtlarımız için **lspci**
komutlarını kullanabileceğimizden bahsetmiştik. Bu komutların her ikisini yazmak yerine sadece **aygit** yazarak aynı çıktıyı almak için aşağıdaki tanımlamayı yapabiliriz.


``` {.sh}
alias aygit='lsusb; lspci'
```

Artık oturumumuz süresince aşağıdaki gibi **aygit** ifadesini kullanabilşiriz.

``` {.sh}
aygit
```

>Yukarıdaki bu taımlamayı kalıcı yapmak istersek kabuk rc dosyasına -bash kabuğu için **.bashrc** yazmak yeterlidir.-

Diğer takma adları -**alias**- görmek için **alias** komutunu kullanabiliriz.

``` {.sh}
alias
```

```
alias aygit='lsusb; lspci'
alias grep='grep --color=auto'
alias ll='ls -l'
alias ls='ls --color=auto'
alias pardus='cowsay -f pardus'
```


>Bir **alias** tanımını kaldırmak için **unalias** komutunu kullanabiliriz.

``` {.sh}
unalias aygit
```



Tekrar **alias** komutunu kullanrak aygit isimli tanımlamanın kalktığını görebiliriz.


```
alias grep='grep --color=auto'
alias ll='ls -l'
alias ls='ls --color=auto'
alias pardus='cowsay -f pardus'
```

Üstteki listede **ls** için de bir tanımlama yapıldığını görüyoruz. Buradaki **color=auto** parametresini sürekli yazmamak için bu tanımlamanın yapıldığı açık. Şimdi **ls** komutunu kullanarak aldığımız çıktıyı inceleyelim. -Sizde bu tanımlama yok ise ekleyebilirsiniz.-

``` {.sh}
ls
```

Aldığınız çıktıda kısayol, dosya ve dizinlerin farklı renklendiğini görüyoruz. Çünkü **ls** yazdığımızda sistem ilk olarak **alias** listesine ardından **PATH** değişkeninde tanımlı konumlara bakmaktadır.

>**type** komutu ile bir komutun yerleşik ya da dış komut olup olmadığına bakabileceğimizden bahsetmiştik. Aynı durum alias tanımları için de geçerlidir.

``` {.sh}
type ls
```

```
senol@pardus:~$ type ls
ls is aliased to `ls --color=auto'
```

Bir takma ismi kaldırmadan komutun adresini yazarak alias tanımını pas geçebiliriz.

``` {.sh}
/usr/bin/ls
```

Yukarıdaki komut ile aldığımız çıktıda **color=auto** parametresi kullanılmamış olacağından çıktı tek renkli gelecektir.

>Bir komutun konumuna **which** komutu ile bakabiliriz.

``` {.sh}
which ls
```

>Bir takma ismi pas geçmek için "**\\**" karakterini de kullanabiliriz.

``` {.sh}
\ls
```
</br>
Örnekler:

Daha sonra detaylı inceleyeceğimiz **man** -manual- komutu ile komutlar hakkında yardım alabiliriz. Aldığımız yardım çıktısının istediğimiz bir dilde görüntülenmesi için **manpath** parametresine istediğimiz dilin kılavuz dosyalarının konumunu girmeliyiz. Sürekli bu bir konumu belirtmek zaman alacağından aşağıdaki **alias** tanımınıyapabiliriz.

``` {.sh}
alias mantr='man --manpath=/usr/share/man/tr'
```

Üstteki tanımlamayı yaptıktan sonra Türkçe yardım almak için **man** yerine **mantr** yazabiliriz.


``` {.sh}
mantr ls
```

Tanımlı takma ad listesi için **alias** komutunu kullandığımızda,

``` {.sh}
alias
```



aşağıdaki çıktı listelenecektir.


```
alias grep='grep --color=auto'
alias ll='ls -l'
alias ls='ls --color=auto'
alias mantr='man --manpath=/usr/share/man/tr'
alias pardus='cowsay -f pardus'
```


>Tanımlı tüm takma ad listesini kaldırmak için **unalias** komutunda **a** parametresini kullanabiliriz.

``` {.sh}
unalias -a
```

</br>
Sonraki : [Bash komut yapısı -syntax-](tr_komut-yapisi-.md)


