<!-- PROJECT LOGO -->
<br><br>
<p align="center">
  <a href="https://bulutbilisimciler.com/">
    <img src="md_images/bb-slogan.png" alt="Logo" width="250">
  </a>
  <p align="center">
    İfadeyi, öğrenmeyi ve uygulamayı ilerleten türden yaratıcı keşiflere ilham vermek ve bunları çoğaltmak istiyoruz. Bulut Bilişimciler, yaratıcı ve meraklı insanlar için frontend, backend, bulut teknolojileri ve daha fazlasını içeren senaryolarla kavramları ve araçları kendiniz test ederek öğrenebileceğiniz interaktif bir çevrimiçi öğrenme topluluğudur.
  <br>
    <a href="https://github.com/YunusEmreAlps/bb-scenario-template/archive/refs/heads/master.zip">Download</a>
    ·
    <a href="https://github.com/YunusEmreAlps/bb-scenario-template/issues">Report Bug</a>
    ·
    <a href="https://github.com/YunusEmreAlps/bb-scenario-template/issues">Request Feature</a>
  </p>
</p>

---

*Başlamadan önce: Tüm senaryolara https://gitlab.bulutbilisimciler.com/bb-public/scenarios bu link üzerinden ulaşabilirsiniz.* 🎉⭐

---

## Bulut Bilişimciler Kaynaklar 

Örnek Senaryolara bu Linkler üzerinden ulaşabilirsiniz:

1. <https://github.com/katacoda/scenario-examples>
2. <https://github.com/BenHall/katacoda-scenarios>
3. <https://github.com/Leverege/kubernetes-book>
4. <https://github.com/enkidevs/curriculum>
5. <https://github.com/TheOdinProject/curriculum>

***1 ve 2 numaralı linkler ile BB platformunda kullandığımız yapı aynıdır. Bu linkler üzerinden örnek senaryolara bakabilirsiniz. Geri kalan linkler ise senaryo yazımına yardımcı olmak için paylaşılmıştır.***

---

## Senaryo Oluşturma Adımları

**1. Adım** —— Senaryo yazacağımız teknolojinin adı ile bir dosya oluşturuyoruz. (Örn: Git, Go veya Linux gibi...)

![Create Base File](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/create_base_file.png?raw=true)

Bu dosyaları, kök dizin olarak düşünebiliriz.

---

**2. Adım** —— 1. Adımı tamamladıktan sonra konu başlıklarına göre dosyalar oluşturuyoruz. (bash-basics-1, basics-1, gibi bir isim verebilirsiniz.). Bu dosyaları ise ağacın dalları gibi düşünebiliriz.

![Create Base File](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/create_scenario_file.png?raw=true)

---

**3. Adım** —— Oluşturduğumuz her konu başlık dosyasının içerisinde aşağıda belirtilen dosyaları oluşturuyoruz.

- en_finish.md
- en_intro.md
- en_step1.md
- index.json
- tr_finish.md
- tr_intro.md
- tr_step1.md

<pre>
  Kurs Adı (Linux, Go, Ubuntu, vs...)
    |__Konu 1
       |__en_finish.md
       |__en_intro.md
       |__en_step1.md
       |__index.json
       |__tr_finish.md
       |__tr_intro.md
       |__tr_step1.md
    |__Konu 2
       |__en_finish.md
       |__en_intro.md
       |__en_step1.md
       |__index.json
       |__tr_finish.md
       |__tr_intro.md
       |__tr_step1.md
    |__Konu 3
       |__en_finish.md
       |__en_intro.md
       |__en_step1.md
       |__index.json
       |__tr_finish.md
       |__tr_intro.md
       |__tr_step1.md
    |__Konu 4
       |__en_finish.md
       |__en_intro.md
       |__en_step1.md
       |__index.json
       |__tr_finish.md
       |__tr_intro.md
       |__tr_step1.md
</pre>

***Senaryoları tek adımda bitirebilirsiniz ama bu öğrenimi uzun ve karmaşık bir hale getirecektir. Bu yüzden adımlara ayırmanız öğrenim sürecini daha kolay ve akıcı bir hale getirecektir. Adım sayısına göre en_step1.md ve tr_step1.md dosyalarını en_stepx.md ve tr_stepx.md şeklinde arttırabilirsiniz.***

***Dünya'nın her yerinde ulaşılabilir olmak istiyoruz. Bu yüzden yazılan senaryoları bu aşamada iki dili destekleyecek şekilde istiyoruz. Tr ile başlayan markdown (.md) dosyaları Türkçe, en ile başlayan markdown (.md) dosyaları ise İngilizce olmalıdır.***

![Create MD Files](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/md_files.png?raw=true)

---

**4. Adım** —— Son adımda ise oluşturduğumuz dosyaları **index.json** dosyasına tanımlıyoruz. Adımları, kullanılacak image adını ve video linkini aşağıdaki gibi girmemiz gerekiyor.

```sh
{
    "scenario": {
      "steps": [
        {
          "text": "step1.md" // Adım 1
        }
        {
          "text": "step2.md" // Adım 2
        }
        {
          "text": "step3.md" // Adım 3
        }
      ],
      "intro": {
        "text": "intro.md" // Dersin içeriği ile ilgili girizgâh yapılan dosya
      },
      "finish": {
        "text": "finish.md" // Dersin sonunda elde edilen yetkinliklerin anlatıldığı dosya
      },
      "video": {
        "text": {
          "en": "https://youtube.com/embed/zRiZZwGSl0M", // İngilizce Video
          "tr": "https://youtube.com/embed/zRiZZwGSl0M"  // Türkçe Video
        }
      }
    },
    "environment": {
      "uilayout": "editor-terminal"
    },
    "backend": {
      "imageid": "alpine" // Kullanılacak Image Adı
    }
  }
```

![Index.json](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/index.json.png?raw=true)

---

### Dosyaların Platformda Görünümü

- Eğitimler
![Scenarios](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/lesson.png?raw=true)
- Senaryoların Gösterilmesi
![Scenarios](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/scenario_list.png?raw=true)
- Senaryo'nun Çalıştırılması
![Specific Scenario](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/scenario_tab.png?raw=true)
- Senaryo Başlangıç (tr_intro.md)
![tr_intro.md](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/tr_intro.md.png?raw=true)
- Senaryo Adımları (tr_step1.md)
![tr_step1.md](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/tr_step1_top.png?raw=true)

![tr_step1.md](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/tr_step1_bottom.png?raw=true)

- Senaryo Bitirme Kısmı (tr_finish.md)
![tr_finish.md](https://github.com/YunusEmreAlps/bb-scenario-template/blob/master/md_images/tr_finish.md.png?raw=true)
