# Pardus & GNU / Linux Sistem Yönetimi 

[![N|Solid](https://www.pardus.org.tr/wp-content/uploads/2019/12/parduslogo.png)](https://pardus.org.tr)
## Pardus Hakkında...

**Anadolu Parsı  -Panthera Pardus Tulliana-**

|    Tanım     | Açık Kaynak kodlu GNU/Linux işletim sistemi dağıtımı.    |
|--------------|------------------|
|**Başlangıç**    | 2003   |
|**İlk sürüm**    | 04.02.2005 ( Pardus Live CD 1.0  -Gentoo )  |
|**Kurulabilir Sürüm** | 27.12.2005 ( Pardus Linux 1.0  -PiSi ) |
|**Diğer Versiyonlar**|PiSi: 2007, 2008, 2009, 2011 Debian: Pardus 2013, Pardus K. 5, Pardus 17, 19,21|
||
|**Çekirdek**|Linux|
|**Paket Sistemi** | Debian|
|**Grafik Arayüz** |Xfce, GNOME, KDE|
|**Lisans**        |GPLv3 -Genel Kamu Lisansı-|
|**Lisans Bedeli** |Ücretsiz|
||
|**_Pardus Projeleri_**|
|**ETAP**| Etkileşimli Tahta Arayüz Projesi|
|**LiderAhenk**|Merkezi Yönetim Sistemi|
|**Ahtapot**| Tümleşik Siber Güvenlik Sistemi|
|**Engerek** |Kimlik Yönetim Sistemi|
||
|**İndirme**  | pardus.org.tr|
|**Belgeler** |pardus.org.tr/belgeler|
|**Forum**    |forum.pardus.org.tr|
|**Bilgi Bankası**|belge.pardus.org.tr|
|**Topluluk**     |gonullu.pardus.org.tr|
|**Diğer**        |etap.org.tr|

Pardus, _**Debian GNU/Linux**_ temelli Özgür ve Açık Kaynak kodlu bir işletim sistemidir. İnternet üzerinden ücretsiz olarak indirilebilmekte ve kurulabilmektedir. Kişisel veya kurumsal kullanımlar için Pardus’un rekabet edebilir ve sürdürülebilir bir işletim sistemi haline getirilmesi için TÜBİTAK ULAKBİM bünyesinde geliştirme ve idame çalışmaları devam ettirilmektedir.

Pardus’un, kamu kurum ve kuruluşları ile KOBİ’lerde kolay yaygınlaştırılabilmesi için kurumsal ihtiyaçları karşılayan Açık Kaynak kodlu alt projeleri bulunmaktadır. Lider Ahenk Merkezi Yönetim Sistemi, Engerek Kimlik Yönetim Sistemi, Ahtapot Bütünleşik Siber Güvenlik Sistemi, Etkileşimli Tahta Arayüz Projesi (ETAP) bunların başlıcalarıdır.

Pardus ekibi ülkemizde yaygınlaştırılması, destekleyici bir ekosistemin gelişmesi için çalışmalar yapmaktadır. Özgür Yazılımlar konusunda konferans, çalıştaylar ve eğitimler düzenlemekte; **Mustafa Akgül Özgür Yazılım Yaz Kampı, Mustafa Akgül Özgür Yazılım Kış Kampı (Akademik Bilişim), Pardus ve Açık Kaynak Günleri** gibi organizasyonlara destek vermekte; Teknofest, Özgür Yazılım ve Linux Günleri gibi organizasyonlara katılım sağlamaktadır. Ayrıca kamuoyunu bilgilendirmek için **Açık Belge Biçimi (ODF)** portalı, Özgür Yazılım faaliyetlerini özendirmek için **Açık Kaynak Kod Platformu** gibi projeleri başlatmıştır.
<p align="right">
Özgürlük içn Pardus!
</p>

Pardus versiyonunuz hakkında bilgi almak için **os-release** dosyasını görüntüleyebilirsiniz.

``` {.sh}
cat /etc/*release
```

``` {echo}
PRETTY_NAME="Pardus GNU/Linux 21 (yirmibir)"
NAME="Pardus GNU/Linux"
VERSION_ID="21.2"
VERSION="21.2 (yirmibir)"
VERSION_CODENAME=yirmibir
ID=pardus
HOME_URL="https://www.pardus.org.tr/"
SUPPORT_URL="https://forum.pardus.org.tr/"
BUG_REPORT_URL="https://talep.pardus.org.tr/"
ID_LIKE=debian
PARDUS_CODENAME=yirmibir
```

Bu bilgileri veren **screenfetch** komutunu da deneyebilirsiniz.

**screenfetch** komutunu kurman için :

``` {.sh}
apt install screenfetch 
```


``` {.sh}
screenfetch 
```

Çıktı:

``` {echo}

   .smNdy+-    `.:/osyyso+:.`    -+ydmNs.    senol@pardus
  /Md- -/ymMdmNNdhso/::/oshdNNmdMmy/. :dM/   OS: Pardus 21.4 yirmibir
  mN.     oMdyy- -y          `-dMo     .Nm   Kernel: x86_64 Linux 5.10.0-21-amd64
  .mN+`  sMy hN+ -:             yMs  `+Nm.   Uptime: 5h 27m
   `yMMddMs.dy `+`               sMddMMy`    Packages: Unknown
     +MMMo  .`  .                 oMMM+      Shell: bash 5.1.4
     `NM/    `````.`    `.`````    +MN`      Resolution: 5760x1080
     yM+   `.-:yhomy    ymohy:-.`   +My      DE: Xfce
     yM:          yo    oy          :My      WM: Xfwm4
     +Ms         .N`    `N.      +h sM+      WM Theme: pardus-default
     `MN      -   -::::::-   : :o:+`NM`      GTK Theme: pardus [GTK2]
      yM/    sh   -dMMMMd-   ho  +y+My       Icon Theme: pardus
      .dNhsohMh-//: /mm/ ://-yMyoshNd`       Font: Ubuntu 12
        `-ommNMm+:/. oo ./:+mMNmmo:`         Disk: 506G / 832G (65%)
       `/o+.-somNh- :yy: -hNmos-.+o/`        CPU: Intel Core i7-10750H @ 12x 5GHz [49.0°C]
      ./` .s/`s+sMdd+``+ddMs+s`/s. `/.       GPU: Quadro P620
          : -y.  -hNmddmNy.  .y- :           RAM: 5396MiB / 31900MiB
           -+       `..`       +-           


```

</br>

Sonraki  >>  [Özgür Yazılım -freesoftware-](../hakkinda/tr_free-software.md)