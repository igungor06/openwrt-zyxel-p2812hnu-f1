# ZyXEL P-2812HNU-F1 için OpenWRT Kurulum Rehberi!

![thumbnail](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/e9e57423-b580-4933-87d5-ae3af7da1861)

Bu yöntem ile Windows üzerinde ZyXEL P-2812HNU-F1 modeminize çok kısa sürede OpenWRT kurabileceksiniz.  

*OpenWRT kurulumunda oluşabilecek tüm komplikasyonlar sizin sorumluluğunuzdadır.*  
*Konu ile ilgili hiçbir sorumluluk kabul etmiyoruz. Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.* 🙏

<p align="left">
  <a href=""><img src="https://img.shields.io/badge/Youtube-Kurulum Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
</p>
  

# ⚙️ Cihaz Özellikleri

- CPU: 500 Mhz Lantiq XWAY VRX288 (PSB 80920)
- DSL: Lantiq (PSB 80190)
- RAM: 128 MB (Samsung veya ProMOS V59C1G01168QBJ25)
- FLASH: 128 MB (Samsung K9F1G08U0D-SCB0)
- WI-FI: RaLink RT3062f 300 Mbps b/g/n
- PORT: 4 adet Gigabit LAN, 1 adet Gigabit WAN, 2 adet USB 2.0

# 🧰 Gerekli Malzemeler
- <details>
  <summary>ZyXEL P-2812HNU-F1</summary>

  ![p2812](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/0931a4ed-dd4c-4f5b-9109-5bc66cb36a4e)

</details>

- <details>
  <summary>Ethernet Kablosu</summary>

  ![ethernet-kablosu](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/460a8350-1cfc-4860-9db7-bfbdddb72b97)

</details>

- <details>
  <summary>PL2303 USB TO TTL Kablo</summary>

  ![PL2303](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/0bdf35a7-1b48-43cd-be08-568e10f4cb1b)

</details>

# 💻 Gerekli Programlar
Aşağıdaki programları önceden kuralım.

- P2303 Driver - [İndir](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/1-PL2303_Driver.exe)

- TeraTerm - [İndir](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/2-teraterm-4.106.exe)

- Tftpd64 - [İndir](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/3-Tftpd64-4.64.exe)

- WinSCP - [İndir](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/4-WinSCP-5.21.7.exe)

# ✨ Başlarken

- <details>
  <summary>Kuruluma başlamadan önce Windows Ağ ayarlarından Ethernet'imize statik ip atayalım.</summary>

  > Denetim Masası\Ağ ve Internet\Ağ Bağlantıları

  ![ethernet-settings](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/e97236c7-922c-4dc0-847c-ebe92348f898)

</details>

- <details>
  <summary>Modemin içini açalım ve anten kablolarını dikkatlice çıkartıp kartı elimize alalım</summary>

  ![p-2812hnu-f1_board_bottom](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/ad81e23f-3d04-4412-ae5d-7bf7ceeac850)

</details>

- <details>
  <summary>Kartın arka yüzündeki serial kablolarına PL2303 kablomuzu şekildeki gibi bağlayalım</summary>

  ![p-2812hnu-f1_board_top](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/5e012f3a-6c66-44a0-a943-01b989452f08)
  
  (Tekli : Siyah) - Yeşil - Beyaz - (Kırmızıyı bağlama)

  ![p-2812hnu-f1_serial](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/02581033-f8a0-4444-9ee8-7b15371abe32)
</details>

- Son olarak modemi ethernet kablosu ile LAN portundan bilgisayarımıza bağlayalım ve güç kablomuzu modeme takalım. **Ama modem kapalı durumda olsun.**

# 🚀 OpenWRT Kurulumu

- <details>
  <summary>İlk olarak "TeraTerm" programını açın Serial portunuzu seçin, "Setup / SerialPort" kısmından "speed'i 115200" ayarlayın</summary>

  ![teratermport](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/a5978332-4d17-43b5-b641-641278d9c186)

  ![teratermspeed](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/71125a0f-27d5-462e-83ac-8464cbf2668b)

</details>

- <details>
  <summary>Şimdi iletken bir madde ile R17 yazan lehimli yeri kısa devre yaptırırken modemi güç tuşuna basarak çalıştıralım</summary>

  ![p-2812hnu-f1_nand](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/239edf62-3143-4c76-a8a5-b4d8817619f8)

</details>

- Modemi açtığımızda TeraTerm programında modemin UART moduna girdiğini gösteren alttaki yazıyı göreceğiz

  ```
  ROM VER: 1.0.5
  CFG 02
  UART
  ```
- Şimdi cihaz UART modunda iken TeraTerm programından **"File" "Send File"** kısmından [u-boot.asc](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/u-boot.asc) dosyasını seçin.

- U-Boot yüklemesi bittiğinde aşağıdaki komutu girin

  ```
  nand erase.chip
  ```

- <details>
  <summary>Tftp programını açın aşağıdaki gibi ayarlayın uygulama altta beklesin</summary>

  ![tftpd64](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/8175e7b2-9fd0-48ae-9770-8917cadd3a97)

</details>


# 😎 Merhaba OpenWRT!
Tebrikler! Artık doğruca [192.168.1.1](http://192.168.1.1/) adresine giderek OpenWRT'ye merhaba diyebilirsiniz! \*alkış efekti\*  

# 💖 Özel Teşekkürler
Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.  

# 🗃️ Kaynaklar
- [OpenWRT Wiki](https://openwrt.org/toh/zyxel/p-2812hnu-f1)
- [Zyxel P-2812HNUL-F1 Modeme Openwrt Kurma Rehberi - Donanım Haber Forum](https://forum.donanimhaber.com/zyxel-p-2812hnul-f1-modeme-openwrt-kurma-rehberi--134393534)

-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  