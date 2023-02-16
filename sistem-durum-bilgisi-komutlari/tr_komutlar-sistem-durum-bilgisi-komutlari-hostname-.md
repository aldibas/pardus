## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **hostname** 


</br>

**hostname** komutu; sitemdeki bilgisayar adını görüntülemek ve değiştirmek için kullanılır.

</br>



``` {.sh}
hostname
```

<br>

Çıktı:

``` {echo}
pardus
```

>hostname bilgisi için /etc/hostname dosyasının içeriğini de görüntüleyebiliriz.

``` {.sh}
cat /etc/hostname
```


**Komutun dizilimi;**

```
<command>  [OPTIONS] [Host_Name]
```

Komut seçenekleri : -**OPTIONS**- [--adfisyI1]

| Seçenek | | Açıklama |
|--|:--:|--|
| -a, --alias | » | Sistemdeki tüm kısayol adlarını -takmaAd/alias- görüntüler. |
| -d, --domain | » | Sistemdeki DNS alan adını görüntüler. |
| -f, --fqdn, --long| » | Sistemdeki tam olarak nitelendirilmiş alan adını (fully qualified domain name) görüntüler. |
| -i, --ip-address |»| Sistemdeki IP adresini görüntüler. |
| -s, --short |» | Sistemdeki kısa adı görüntüler. |
| -y, --yp |» | NIS (Network Information Service) alan adını görüntüler. |
| -I, --all-ip-addresses |» | Ana bilgisayar için tüm IP adreslerini listeler |

| Seçenek | | Çıktı | Açıklama |
|:--:|:--:|--|--|
| -i | » |  127.0.1.1 | IP |
| -a | » |  senol-pc | alias |
| -d | » |  pardus.net.tr | domain  |
| -f | » |  senol.pardus.net.tr | FQDN  |
| -s | » |  pardus |  sort name |
| -I | » | 172.17.0.1 10.1.52.4 172.19.0.3 | host IP |

HostName -bilgisayar adı- bilgisini "pardus" olarak değiştirmek için aşağıdaki komutu uygulayabilirsiniz.

 ``` {.sh}
hostname pardus
```

Kontrol etmek için :


 ``` {.sh}
hostname
```

>HostName bilgisini kalıcı olarak değiştirmek için **/etc/hostname** dosyası değiştirilmelidir.

</br>

Yukarıdaki işlem ile bu dosyanın değişip değişmediğine bakalım.

``` {.sh}
cat /etc/hostname
```


</br>

>Lokal IP -iç IP- adresinizi de **hostname -I** komutu ile görebilirsiniz.

 ``` {.sh}
hostname -I
```
Çıktı :

 ``` {echo}
172.17.0.1 10.1.52.4 172.19.0.3
```

</br>

Konu detayı için inceleme konuları:</br>
**hostnamectl, domainname, ypdomainname, nisdomainname, dnsdomainname,host**


</br>

---

 [Sistem&durum bilgisi komutları -date-](./tr_komutlar-sistem-durum-bilgisi-komutlari-date-.md) << Önceki / Sonraki >> [Sistem&durum bilgisi komutları -free-](./tr_komutlar-sistem-komutlari-free-.md)

