## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **date** 


</br>

</br>

>**date** komutu; sistem zamanını görüntüler ve değiştirme imkanı sunar.

</br>



``` {.sh}
date
```

<br>

Çıktı:

``` {echo}
Tue 14 Feb 2023 01:15:25 AM +03
```

**Komutun dizilimi;**

```
<command>  [OPTIONS] [+FORMAT]
```

Komut seçenekleri : -**OPTIONS**- [-dfIRrsu --debug] [%a %A %b %B...]

| Seçenek | | Açıklama |
|--|:--:|--|
| -u, --utc | » |  Zamanı evrensel koordinata göre göster/ayarla |
| -s, --set=STRING | » | Saati belirtilen dizgeye göre ayarlar. |
| -r, --reference=FILE| » | Dosyanın son düzenlenme zamanını gösterir. |
|||

| Seçenek | | Çıktı |
|:--:|:--:|--|
| +%a | » |  Tue / Sal|
| +%A | » | Tuesday / Salı |
| +%b | » | Feb / Şub |
| +%B | » | February / Şubat |
| +%c | » | Tue 14 Feb 2023 01:27:22 AM +03 -tarih ve saat- |
| +%C | » | 20 -Yüzyıl / century- |
| +%d | » | 14 -Ayın günü / century- |
| +%D | » | 02/14/23 -Tarih- |
| +%F | » | 2023-02-14 |
| +%g | » | 23 -yıl- |
| +%G | » | 2023 -yıl- |
| +%H | » | 02 -saat- |
| +%k | » | 3 -saat (0..23)- |
| +%m | » | 02 -ay- |
| +%p | » | AM/PM -ÖÖ/ÖS- |
| +%R | » | 03:00 -zaman- |
| .. | » | ... |




</br>

---

 [Sistem&durum bilgisi komutları -uptime-](./tr_komutlar-sistem-durum-bilgisi-komutlari-uptime-.md) << Önceki / Sonraki >> [Sistem&durum bilgisi komutları -date-](./tr_komutlar-sistem-komutlari-date-.md)

