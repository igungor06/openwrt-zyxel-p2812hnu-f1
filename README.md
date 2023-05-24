# ZyXEL P-2812HNU-F1 için OpenWRT Kurulum Rehberi!

![thumbnail](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/e9e57423-b580-4933-87d5-ae3af7da1861)

Bu yöntem ile Windows üzerinde ZyXEL P-2812HNU-F1 modeminize OpenWRT kurabileceksiniz.  

**OpenWRT kurulumunda oluşabilecek tüm komplikasyonlar sizin sorumluluğunuzdadır.**  

**Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.** 🙏

<p align="left">
  <a href="https://youtu.be/3NRZ06BoXCM"><img src="https://img.shields.io/badge/Youtube-Kurulum Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
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

- Kuruluma başlamadan önce [OpenWRT.zip](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/openwrt.rar) dosyamızı indirelim ve masaüstüne çıkartalım.

- <details>
  <summary>Dosyalara ait resim</summary>

  ![openwrt](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/b251ffba-178d-464a-a11b-5e2d86a56a0f)

</details>

- <details>
  <summary>Windows Ağ ayarlarından Ethernet'imize statik ip atayalım</summary>

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

- <details>
  <summary>Son hali resimdeki gibi olmalıdır</summary>

  ![image](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/ee98bafc-9268-4dd5-8a06-f61ab950f455)

</details>

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
- Şimdi cihaz UART modunda iken TeraTerm programından **"File" "Send File"** kısmından **u-boot.asc** dosyasını seçin.

- U-Boot yüklemesi bittiğinde aşağıdaki komutu girin

  ```
  nand erase.chip
  ```

- <details>
  <summary>Tftp programını açın aşağıdaki gibi ayarlayın uygulama altta beklesin</summary>

  ![tftpd64](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/8175e7b2-9fd0-48ae-9770-8917cadd3a97)

</details>

- TeraTerm programına aşağıdaki komutları sırayla girin:
  ```
  tftpboot openwrt-lantiq-p2812hnufx_nandtpl-u-boot-16M-patch.img

  nand write 0x81000000 0x0 0x38985
  ```

- Modemi kapatın. Modem kapandıktan sonra tekrar açalım ve **TeraTerm** programında görünen **autoboot** işlemini herhangi bir tuşa basarak durdurun.

- Aşağıdaki komutları TeraTerm programına girelim. 

  <details>
  <summary>XX:XX:XX:XX:XX:XX yazan yere modemin arka yüzündeki etikette yazan MAC adresini yazınız</summary>

  ![p-2812_stickerr](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/b38c7965-e307-4e51-bec3-f5982fb38d76)

  </details>

  ```
  mtdparts add nand0 256k uboot

  mtdparts add nand0 128k uboot-env

  mtdparts add nand0 3m kernel

  mtdparts add nand0 - ubi

  setenv ethaddr XX:XX:XX:XX:XX:XX

  setenv nboot 'nand read 0x80800000 0x60000 0x300000; bootm 0x80800000'

  setenv bootcmd 'run nboot'

  saveenv

  tftpboot openwrt-22.03.0-rc1-lantiq-xrx200-zyxel_p-2812hnu-f1-initramfs-kernel.bin

  bootm $fileaddr
  ```

- Modem yeniden başlayacak. Akan yazılar durduğunda "Enter" tuşuna basalım. OPENWRT diye yazı göreceksiniz.

- Modemin arayüzüne [192.168.1.1](https://192.168.1.1) adresinden giriş yapalım. 

  **username: root ve şifresi yoktur**. Direkt **Login** butonuna tıklayalım.

- Arayüze girdikten sonra üst panelden **System > Backup / Flash Firmware** kısmına girelim.

  En aşağıdaki **Flash image..** butonuna tıklayalım. Açılan pencereden **Browse** butonuna tıklayarak **openwrt-22.03.0-rc1-lantiq-xrx200-zyxel_p-2812hnu-f1-squashfs-sysupgrade.bin** doyasını seçelim.

  **Keep Settings** tikini kaldıralım ve dosyayı kuralım. Kurulum bittiğinde cihaz yeniden başlayacak.

- Modeme OpenWRT kurduk ama wifi driverı olmadığı için şuan modemin wifisi çalışmamaktadır.

  <details>
  <summary>WinSCP programı ile modemin ana dizinine giriş yapalım.</summary>

  ![winscplogin](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/64be1765-8ff1-46e8-9cf7-b3a42852d69f)

  </details>

  <details>
  <summary>/lib/firmware klasörünün içine RT3062.eeprom dosyasını sürükleyerek atalım</summary>

  ![winscpfirmware](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/d581ca08-9914-4339-99e0-d8d12eedb1b1)

  </details>

- **VDSL** bağlantısı WinSCP programınan aynı şekilde **/etc/config/network** dosyasını açın. Aşağıda verdiğim satırdaki **dsl0** yazan satırı bulup **dsl0.35** olarak düzenleyin (diğer kısımlara dokunmayın):

  ```
  config interface 'wan'
    option ifname 'dsl0'
    option proto 'pppoe'
    option username 'XXXXXXXXX@XXXXXXXX.net'
    option password 'XXXXXXXX'
    option ipv6 '1'
  ```

  Düzenledikten sonraki hali:
  ```
  config interface 'wan'
    option ifname 'dsl0.35'
    option proto 'pppoe'
    option username 'XXXXXXXXX@XXXXXXXX.net'
    option password 'XXXXXXXX'
    option ipv6 '1'
  ```

- Modem yeniden başladığında **wifi açılmama sorununu** çözmek için modem arayüzünden **System > Startup** kısmına ve oradan da **Local Startup** kısmına girelim. 

  Çıkan ekrandaki yazıların hepsini aşağıdaki gibi düzenleyelim ve **Save** butonuna basarak kaydedilim:

  ```
  # Put your custom commands here that should be executed once
  # the system init finished. By default this file does nothing.
  echo 1 > /sys/bus/pci/rescan
  exit 0
  ```

- Modem bir kere yeniden başlatalım ve istediğiniz diğer ayarları yapınız. 

- **Tebrikler OpenWRT kurulumunu tamamladınız.** 👏👏

# 💖 Özel Teşekkürler
Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.  

# 🗃️ Kaynaklar
- [OpenWRT Wiki](https://openwrt.org/toh/zyxel/p-2812hnu-f1)
- [Zyxel P-2812HNUL-F1 Modeme Openwrt Kurma Rehberi - Donanım Haber Forum](https://forum.donanimhaber.com/zyxel-p-2812hnul-f1-modeme-openwrt-kurma-rehberi--134393534)

-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
