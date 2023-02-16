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

| Seçenek | | Çıktı | Açıklama |
|:--:|:--:|--|--|
| +%a | » |  Tue / Sal| Gün|
| +%A | » | Tuesday / Salı | Gün |
| +%b | » | Feb / Şub | Ay |
| +%B | » | February / Şubat | Ay |
| +%c | » | Tue 14 Feb 2023 01:27:22 AM +03 | Tarih ve saat- |
| +%C | » | 20 | Yüzyıl / century |
| +%d | » | 14 | Ayın günü  |
| +%D | » | 02/14/23 | Tarih |
| +%F | » | 2023-02-14 | Tarih |
| +%g | » | 23 | Yıl |
| +%G | » | 2023 | Yıl |
| +%H | » | 02 | Saat |
| +%k | » | 3 | Saat (0..23) |
| +%m | » | 02 | Ay |
| +%p | » | AM/PM | ÖÖ/ÖS |
| +%R | » | 03:00 | Zaman |
| .. | » | ... | ...|





</br>

---

 [Sistem&durum bilgisi komutları -uptime-](./tr_komutlar-sistem-durum-bilgisi-komutlari-uptime-.md) << Önceki / Sonraki >> [Sistem&durum bilgisi komutları -hostname-](./tr_komutlar-sistem-komutlari-hostname-.md)

