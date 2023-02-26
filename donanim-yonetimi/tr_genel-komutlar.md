# **Terminal & Kabuk -Shell- Komutları**


## Donanım Yönetimi

### Genel Bilgi Alma Komutları

#### **lsusb** 


</br>

**`lsusb`** GNU/Linux işletim sistemi üzerinde bağlı olan **USB** aygıtlarını listelemek için kullanılan bir komuttur. lsusb komutunu kullanarak, bağlı USB aygıtlarının üreticilerini, model numaralarını ve diğer özelliklerini görüntüleyebilirsiniz.


``` {.sh}
lsusb
```

Bu komutu çalıştırdığınızda, sistemde bağlı olan tüm USB aygıtları hakkında bilgi görüntülenecektir. 

``` {echo}
Bus 001 Device 006: ID 8087:0026 Intel Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
...
```

Bu çıktıda, her bir USB aygıtı için bir satır bulunmaktadır.
* "**Bus**", aygıtın bağlı olduğu USB veri yolunun numarasını gösterir.
* "**Device**", bağlı olan aygıtın numarasını gösterir.
* "**ID**", aygıtın üretici ve model numarasını gösterir.

</br>

**Komutun dizilimi;**

``` {echo}
lsusb  [OPTIONS] 
```

Komut seçenekleri: -**OPTIONS**- [-vsdDtV ]

| Seçenek | | Açıklama |
|--|:--:|--|
| -v, --verbose | » | Aygıt ayrıntılarını -**Device Descriptor**- gösterir. |
| -s [[bus]:][devnum] | » | Belirtilen USB aygıtının ayrıntılarını gösterir.  |
| -d [[bus]:][devnum] | » | Belirtilen üretici ve ürün kimliğine sahip USB aygıtlarını listeler. |
| -D device | » | Belirtilen aygıt dosyası varsa, bu aygıta ait bilgileri görüntüler. | 
| -t --tree | » | USB topolojisini ağaç yapısında gösterir. | 
|||

</br>

**Örnekler:**

</br>

Tüm aygıt detaylarını görüntüleme...

 ``` {.sh}
lsusb -v
```

``` {echo}
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.10
...
```
---
</br>

Sadece belirtilen aygıt için bilgi görüntülemek için veri yolu ve aygıt numarası "**1:2**" şeklinde ya da "**001:002** girilmelidir. Örneği uygularken bu bilgileri `lsusb` komutunda aldığınız çıktıya göre girin.


 ``` {.sh}
lsusb -s 001:002
```

``` {echo}
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
``` 

Aygıtın detaylı bilgileri için "**-v**" parametresi kullanılabilir.

 ``` {.sh}
lsusb -vs 001:002
```

---

</br>

Aygıtların USB topolojisini görüntülemek için "**-t** / **--tree**" opsiyonu kullanılabilir.

 ``` {.sh}
lsusb -ts 001:002
```

``` {echo}
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/16p, 480M
    |__ Port 9: Dev 5, If 0, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 14: Dev 6, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 14: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
...
``` 

---

 ``` {.sh}
lsusb -D /dev/bus/usb/001/002
```

``` {echo}
Device: ID 046d:c52b Logitech, Inc. Unifying Receiver
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
...
``` 
---
</br>



>Diğer kullanışlı USB aygıtı yönetimi komutlarından bazıları : **lsblk, mount, umount, dmesg, lsmod**

lsblk: Bağlı blok aygıtlarını listeler. Bu komutu kullanarak, harici bir sabit disk veya USB bellek gibi USB depolama aygıtlarınızı görüntüleyebilirsiniz.

mount: Sisteme bağlı olan dosya sistemlerini listeler. Bu komutu kullanarak, bağlı olan USB depolama aygıtlarınızı görüntüleyebilir ve sisteme bunları bağlayabilirsiniz.

umount: Bağlı olan dosya sistemlerini çıkarır. Bu komutu kullanarak, USB depolama aygıtlarınızı sistemden güvenli bir şekilde çıkarabilirsiniz.

dmesg: Sisteme son bağlı olan aygıtlar hakkında ayrıntılı bilgi sağlar. Bu komutu kullanarak, aygıtın neden tanınmadığını veya sorunlar yaşanıp yaşanmadığını tespit edebilirsiniz.

lsmod: Yüklü modülleri listeler. Bu komutu kullanarak, sisteme bağlı olan USB aygıt modülleri listelenir.

---

</br>



#### **lspci** 


</br>

**`lspci`** komutu, PCI (Peripheral Component Interconnect) veri yoluna bağlı aygıtların listesini gösterir. Bu komut, sistem yöneticilerine, hangi PCI cihazlarının sisteme bağlandığını, bunların özelliklerini, özellikle donanım kimliklerini ve hangi sürücülerin bunları desteklediğini anlamalarına yardımcı olur.


``` {.sh}
lspci
```

Bu komutu çalıştırdığınızda, sistemde bağlı olan tüm PCI aygıtları hakkında bilgi görüntülenecektir. 

``` {echo}
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host ..
00:01.0 PCI bridge: Intel Corporation 6th-10th Gen Core PCIe ...
00:02.0 VGA compatible controller: Intel Corporation CometLake-H ...
...
```

Bu çıktıda, her bir USB aygıtı için bir satır bulunmaktadır.
* "**Bus**", aygıtın bağlı olduğu USB veri yolunun numarasını gösterir.
* "**Device**", bağlı olan aygıtın numarasını gösterir.
* "**ID**", aygıtın üretici ve model numarasını gösterir.

</br>

**Komutun dizilimi;**

``` {echo}
lspci  [OPTIONS] 
```

Komut seçenekleri: -**OPTIONS**- [-vsknt ]

| Seçenek | | Açıklama |
|--|:--:|--|
| -v | » | Aygıt ayrıntılarını -**Device Descriptor**- gösterir. |
| -vv | » | Daha ayrıntılı aygıt bilgileri sağlar. |
| -vvv | » | Tüm aygıt ayrıntılarını gösterir. |
| -k | » | Ayğıta yüklü olan sürücü ismini gösterir. |
| -n  | » | Aygıt kimliğini gösterir. |
| -s  | » | Belirtilen kaynak aygıtının ayrıntılarını gösterir. . | 
| -t --tree | » | Aygıtlar ağaç yapısında gösterilir. | 
|||

</br>

**Örnekler:**

</br>

Tüm aygıt detaylarını görüntüleme...

 ``` {.sh}
lspci -vvv
```

``` {echo}
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host ..
	Subsystem: Lenovo 10th Gen Core Processor Host Bridge/DRAM ...
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ... 
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast ...
	Latency: 0
	IOMMU group: 0
	Capabilities: <access denied>
	Kernel driver in use: skl_uncore
...
```
---
</br>

 ``` {.sh}
lspci -n
```


``` {echo}
00:00.0 0600: 8086:9b54 (rev 02)
00:01.0 0604: 8086:1901 (rev 02)
00:02.0 0300: 8086:9bc4 (rev 05)
...
```

---
</br>

 ``` {.sh}
lspci -k
```

``` {echo}
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host..
	Subsystem: Lenovo 10th Gen Core Processor Host Bridge/DRAM....
00:01.0 PCI bridge: Intel Corporation 6th-10th Gen Core Processor...
	Kernel driver in use: pcieport
00:02.0 VGA compatible controller: Intel Corporation CometLake-H...
	Subsystem: Lenovo UHD Graphics
	Kernel driver in use: i915
	Kernel modules: i915
...
```




---

</br>

Sadece belirtilen aygıt için bilgi görüntülemek için adresi girilebilir. Örneği uygularken bu bilgileri `lspci` komutunda aldığınız çıktıya göre girin.


 ``` {.sh}
lspci -s 00:00.0 
```

``` {echo}
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host...
``` 

Aygıtın detaylı bilgileri için "**-v**" parametresi kullanılabilir.

 ``` {.sh}
lsusb -v -s 00:00.0
```

``` {echo}
00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host...
	Subsystem: Lenovo 10th Gen Core Processor Host Bridge/DRAM...
	Flags: bus master, fast devsel, latency 0, IOMMU group 0
	Capabilities: <access denied>
	Kernel driver in use: skl_uncore
``` 

---

</br>

Aygıtları ağaç yapısı biçiminde görüntülemek için "**-t**  opsiyonu kullanılabilir.

 ``` {.sh}
lspci -t
```

``` {echo}
-[0000:00]-+-00.0
           +-01.0-[01]----00.0
           +-02.0
           +-04.0
...
``` 



</br>

---



