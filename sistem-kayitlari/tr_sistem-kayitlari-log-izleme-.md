# **Terminal & Kabuk -Shell- Komutları**

## Sistem Kayıtları

<br>
Genel olarak değişken (variable) veriler, dosyalar **/var** dizini altında **/log** klasörü içerisinde tutulur. Ayrıca log dizini içerisinde de belli başlı programlara ve servislere ait logları bulunduran başka alt dizinler bulunuyor. Örneğin sistem günlükleri, mail kuyruğu, gelen mailler, yazıcı kuyruğu, programların kilit dosyaları vb...

ls /var/log/ komutu ile klasörün içeriğini görebiliriz;

``` {.sh}
ls /var/log/
```

Komut çıktısı;

``` {.echo}
alternatives.log  bootstrap.log  dockerd.err.log  dpkg.log  lastlog     wtmp
apt               btmp           dockerd.out.log  faillog   supervisor
```

<br>

**Log dosyalarının içeriklerini listelerken kolaylık sağlayan komutlar;**

>**cat:** Dosyaların içeriklerini görüntülemek için kullanılan komuttur.

>**more:** Dosya içeriği sayfa sayfa açılır. Sayfalarda space tuşu ile ileri, Enter tuşu ile satır satır, b tuşu ileri geri gidirilir.

>**tail:** Dosyanın komutta belirtiğimiz kadar son satırlarını görüntülemek için kullanılır. Varsayılan olarak son on satırı listeler.

>**grep:** Dosya içerisinde sadece aradığımız kelimelerle ilgili satırları filtreleyerek listeler.

<br>

Örneğin dockerd.err.log dosyasının son 5 hareketini listelemek için;

``` {.sh}
tail -n 5 dockerd.err.log
```

Komut çıktısı;

``` {.echo}
time="2023-02-14T06:36:04.248049704Z" level=info msg="Default bridge (docker0) is assigned with an IP address 172.17.0.0/16. Daemon option --bip can be used to set a preferred IP address"
time="2023-02-14T06:36:04.284148672Z" level=info msg="Loading containers: done."
time="2023-02-14T06:36:04.299347738Z" level=info msg="Docker daemon" commit=e42327a graphdriver(s)=overlay2 version=20.10.18
time="2023-02-14T06:36:04.299536274Z" level=info msg="Daemon has completed initialization"
time="2023-02-14T06:36:04.332379503Z" level=info msg="API listen on /var/run/docker.sock"
```
Komutun uygulanmasıyla birlikte konsol bize son 5 işlemi listelemiş oldu.

<br>

### dmesg

Sistem açılışında yazan açılış notlarını dmesg komutu ile görüntüleyebiliriz. Sistem açılışında bildirilen problemlerin tespiti ve diğer sistem uyarılarını saptamak için başvurulur.

``` {.sh}
dmesg
```

Komut çıktısı;

``` {.echo}
[13110804.706332] docker_gwbridge: port 2(veth3a0d86d) entered blocking state
[13110804.706335] docker_gwbridge: port 2(veth3a0d86d) entered disabled state
[13110804.706366] device veth3a0d86d entered promiscuous mode
[13110804.706425] IPv6: ADDRCONF(NETDEV_UP): veth3a0d86d: link is not ready
[13110804.706427] docker_gwbridge: port 2(veth3a0d86d) entered blocking state
[13110804.706428] docker_gwbridge: port 2(veth3a0d86d) entered forwarding state
[13110804.939151] eth0: renamed from veth52f5679
[13110804.948205] docker_gwbridge: port 2(veth3a0d86d) entered disabled state
[13110804.948244] br0: port 4(veth2) entered blocking state
[13110804.948246] br0: port 4(veth2) entered forwarding state
[13110804.961928] eth1: renamed from veth5ff434c
[13110804.971091] IPv6: ADDRCONF(NETDEV_CHANGE): veth3a0d86d: link becomes ready
[13110804.971121] docker_gwbridge: port 2(veth3a0d86d) entered blocking state
[13110804.971123] docker_gwbridge: port 2(veth3a0d86d) entered forwarding state
```
Yukarıda bir kısmı verilen çıktı çok uzun olacaktır. Çıktıları filtrelemek istersen "grep" komutunu kullanarak filtreleme yapabiliriz. Örneğin yalnızca hataları görmek istiyorsak;

``` {.sh}
dmesg | grep "ERROR"
```

Komut çıktısı;
``` {.echo}
[8360918.462843] [drm:drm_crtc_commit_wait [drm]] *ERROR* flip_done timed out
[8360918.462915] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:38:crtc-0] commit wait timed out
[8360928.702591] [drm:drm_crtc_commit_wait [drm]] *ERROR* flip_done timed out
[8360928.702653] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:34:plane-0] commit wait timed out
[11101650.937709] [drm:drm_crtc_commit_wait [drm]] *ERROR* flip_done timed out
[11101650.937785] [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:38:crtc-0] commit wait timed out
```
Görüldüğü gibi "ERROR" ifadesinin geçtiği, hataların belirtildiği iletiler ekrana gelmiş oldu.

<br>

### /var/log/syslog dosyası

Açılış sorunlarının çözümü, araştırma imkanları sınırlı olduğundan bazı durumlarda zor olabilmektedir. Linux sistemler açılırken çekirdek ekrana bir takım mesajlar basar. Bazen bu mesajlar, açılışta kullanılan bir grafiğin arkasında kalmaktadır. **ESC** tuşuna basarak bu grafik kaldırılıp alttaki mesajlar görülebilir.

Çekirdek logları açılışta özel bir tampon alana yazılır ve daha sonra **‘dmesg’** komutu ile görüntülenir. Sistem günlüğünü tutan syslogd hizmeti devreye girdikten sonra ise bu loglar syslogd üzerinden günlük dosyalarına yazılır. Başlangıç mesajları da dahil, bu günlükler **/var/log/syslog** dosyasında bulunur.

<br>

``` {.sh}
tail /var/log/syslog
```
Komut çıktısı;
``` {.echo}
Feb 17 09:38:39 pardus dbus-daemon[1552]: [session uid=1000 pid=1552] Successfully activated service 'org.gnome.evince.Daemon'
Feb 17 09:38:43 pardus dbus-daemon[877]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.100' (uid=1000 pid=9209 comm="/opt/google/chrome/chrome ")
Feb 17 09:38:43 pardus systemd[1]: Condition check resulted in Bluetooth service being skipped.
Feb 17 09:39:01 pardus CRON[9450]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb 17 09:39:01 pardus systemd[1]: Starting Clean php session files...
Feb 17 09:39:02 pardus systemd[1]: phpsessionclean.service: Succeeded.
Feb 17 09:39:02 pardus systemd[1]: Finished Clean php session files.
Feb 17 09:43:11 pardus kernel: [ 4488.785104] audit: type=1400 audit(1676616191.671:73): apparmor="DENIED" operation="open" profile="/usr/bin/evince" name="/usr/local/lib/libfreetype.so.6.18.3" pid=9587 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Feb 17 09:47:39 pardus Thunar[9700]: Oturum yöneticisine bağlanılamadı: Oturum yöneticisine bağlanırken hata oluştu: SESSION_MANAGER environment variable not defined
Feb 17 09:47:39 pardus systemd[1532]: Started VTE child process 9705 launched by xfce4-terminal process 9700.
```
<br>



### /var/log/faillog dosyası

</br>

Başarısız oturum açma girişimleri hakkında bilgileri içerir. 
Kullanıcı adı,şifre kırma saldırılarını ve güvenlik ihlali teşebbüslerini bulmak için kullanılan günlük dosyasıdır.

İçeriğini görüntülemek için;

``` {.sh}
cat /var/log/faillog 
```
komutunu kullanabilirsiniz.

<br>

### /var/log/cron dosyası

Cron işlemleri bu dosyaya yazılır. Cron servisinde oluşan bir hata ya da servisin yeniden başlatılması işlemlerini bu dosyadan görebilirsiniz.

Dosya içeriğini görmek için; 

``` {.sh}
cat /var/log/cron 
```
komutunu çalıştırabilirsiniz.

<br>

## /var/log/auth.log

Kimlik doğrulama işlemleri bu dosyada görülebilir.
Sistemdeki bir kullanıcının (root ya da normal kullanıcı) terminal üzerinden başarılı ya da başarısız oturum açma girişimleri bu dosyada incelenebilir.

Dosya içeriğini görmek için; 

``` {.sh}
cat /var/log/auth.log
```
komutunu çalıştırabilirsiniz.

<br>

## /var/log/boot.log

Yanlış ve beklenmeyen kapanmalar, yeniden başlatmalar veya önyükleme hataları ile ilgili bu günlük dosyasından takip edilebilir.

Dosya içeriğini görmek için; 

``` {.sh}
cat /var/log/boot.log
```
komutunu çalıştırabilirsiniz.

<br>

## /var/log/messages

Bilgi amaçlı ve kritik olmayan sistem etkinlik mesajlarını saklamak için kullanılır.
Kernel dışı önyükleme hataları, uygulama ile ilgili servis hataları ve sistem başlangıcında kaydedilen mesajlar takip edilebilir. Sistem yöneticilerinin bir sorun olup olmadığını kontrol edebilemeleri için gerekli ilk log dosyasıdır.
Örneğin herhangi bir donanımınızla ilgili bazı sorunlarla karşılaşıyorsanız bu dosyada bulunan mesajlara göz atabilirsiniz.

Dosya içeriğini görmek için; 

``` {.sh}
cat /var/log/messages
```
komutunu çalıştırabilirsiniz.

<br>

## /var/log/kern.log

Çekirdek ile ilgili hataları ve uyarıları gidermek için kullanılır. Çekirdek tarafından kaydedilen bilgileri barındırdığından çok önemli bir günlük dosyasıdır. Donanın ve bağlantı sorunlarında da incelenmesi kullanışlıdır.

Dosya içeriğini görmek için; 

``` {.sh}
cat /var/logkern.log
```
komutunu çalıştırabilirsiniz.

<br>

## Systemd ve journalctl

Kısaca, systemd bir sistemin süreçlerinin yönetimi için kullanılır.

Systemd tarafından toplanan log olaylarını yönetmek ve görüntülemek için journalctl programı journalctl komutuyla kullanılır.

>Docker imajında systemd kurulu olmadığından burada journalctl komutunu kullanamıyorsuz. Log analizi için journalctl komutunu inceleyiniz.

<br>

## last

Son oturum açan kullanıcıların kayıtlarını listeler;


``` {.sh}
last
```
Komut çıktısı;

``` {.echo}
pardus   tty7         :0               Tue Jan  3 08:27 - 19:02  (10:35)
reboot   system boot  5.10.0-20-amd64  Tue Jan  3 08:26 - 19:03  (10:36)
pardus   tty7         :0               Mon Jan  2 09:06 - 20:49  (11:42)
reboot   system boot  5.10.0-20-amd64  Mon Jan  2 09:06 - 20:49  (11:42)
pardus   tty7         :0               Mon Jan  2 08:55 - 09:05  (00:10)
reboot   system boot  5.10.0-20-amd64  Mon Jan  2 08:54 - 09:05  (00:11)
pardus   tty7         :0               Mon Jan  2 08:21 - 08:53  (00:32)

wtmp begins Mon Jan  2 08:20:38 2023
```
>Burada benzer çıktıyı göremeyebilirsiniz. Yüklü sisteminizde görebilirsiniz.

<br>

---

