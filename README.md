# qb-phone
Advanced Phone for QB-Core Framework :iphone:

#qb-iPhone-TR
- Türkçeleştirilmiş qb-phone. Ekstra olarak iPhone görüntüsü verildi.
- Turkish localized qb-phone. In addition frame changed to iPhone.
- [QB-Core](https://github.com/qbcore-framework)
- ![screenshot](https://cdn.discordapp.com/attachments/1071872069115072604/1117991460340518962/image.png)

# License

    QBCore Framework
    Copyright (C) 2021 Joshua Eger

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>

## Gereksinimler
- [qb-core](https://github.com/qbcore-framework/qb-core)
- [qb-policejob](https://github.com/qbcore-framework/qb-policejob) - MEOS, kelepçe kontrolü vb..
- [qb-crypto](https://github.com/qbcore-framework/qb-crypto) - kripto para ticareti
- [qb-lapraces](https://github.com/qbcore-framework/qb-lapraces) - Rota oluşturma ve yarış
- [qb-houses](https://github.com/qbcore-framework/qb-houses) - Ev ve Anahtar Yönetim Uygulaması
- [qb-garages](https://github.com/qbcore-framework/qb-garages) - Garaj Uygulaması için
- [qb-banking](https://github.com/qbcore-framework/qb-banking) - Bankacılık Uygulaması için
- [screenshot-basic](https://github.com/citizenfx/screenshot-basic) - Fotoğraf Çekmek İçin
- Telefonda fotoğrafları çekebilmek için bir WebHook'a ihtiyacınız var.(Discord veya Imgur bunu sağlayabilir)


## Screenshots
![Home](https://cdn.discordapp.com/attachments/921675245360922625/921675439783673897/home.jpg)
![Bank](https://cdn.discordapp.com/attachments/921675245360922625/921675441142644756/bank.jpg)
![Advert](https://cdn.discordapp.com/attachments/921675245360922625/921675440878415872/advert.jpg)
![Mail](https://cdn.discordapp.com/attachments/921675245360922625/921675440278614068/mail.jpg)
![Garage](https://cdn.discordapp.com/attachments/921675245360922625/921675439590760528/garage.jpg)
![Garage Detail](https://cdn.discordapp.com/attachments/921675245360922625/921675441591422986/garage_in.jpg)
![services](https://cdn.discordapp.com/attachments/921675245360922625/921675458670641152/services.jpg)
![Houses](https://cdn.discordapp.com/attachments/921675245360922625/921675440005988362/house.jpg)
![Racing](https://cdn.discordapp.com/attachments/921675245360922625/921675458423173140/race.jpg)
![Crypto](https://cdn.discordapp.com/attachments/921675245360922625/921675457718517820/qbit.jpg)
![Gallery](https://cdn.discordapp.com/attachments/921675245360922625/921675441381736448/gallery.jpg)
![MEOS](https://cdn.discordapp.com/attachments/921675245360922625/921675440488341534/meos.jpg)
![Twitter](https://cdn.discordapp.com/attachments/921675245360922625/921675459270438922/twitter.jpg)
![Settings](https://cdn.discordapp.com/attachments/921675245360922625/921675458905513984/setting.jpg)
![Whatsapp](https://cdn.discordapp.com/attachments/921675245360922625/921675459517906944/whatsapp.jpg)
![Phone](https://cdn.discordapp.com/attachments/921675245360922625/921675440677064745/phone.jpg)

## Özellikler
- Araç ayrıntılarını görmek için garaj uygulaması
- Oyuncuyu bilgilendirmek için posta uygulaması
- Bakiye görüntüleme ve para transferi için bankacılık uygulaması
- Yarışlar oluşturmak için yarış uygulaması
- Uygulama Mağazası'ndan uygulama indirme
- Polisler için MEOS uygulaması
- Ev ayrıntıları ve yönetimi için evler uygulaması

## Installation
### Manuel
Komut dosyasını indirin ve `[qb]` dizinine yerleştirin.
Veritabanında `qb-phone.sql` dosyasını içe aktarın.
server.cfg/resouces.cfg dosyasına aşağıdaki kodu ekleyin:
```
ensure qb-core
ensure screenshot-basic
ensure qb-phone
ensure qb-policejob
ensure qb-crypto
ensure qb-lapraces
ensure qb-houses
ensure qb-garages
ensure qb-banking
```

## Yapılandırma
```

Config = Config or {}

Config.RepeatTimeout = 2000 -- Yanıtlanmamış arama bildirimi için zaman aşımı
Config.CallRepeats = 10 -- Yanıtlanmamış arama bildirimi tekrarları
Config.OpenPhone = 244 -- Telefona erişmek için tuş kodu
Config.PhoneApplications = {
    ["phone"] = { -- Benzersiz olmalı
        app = "phone", -- Uygulama rotası
        color = "#04b543", -- Uygulama simgesi rengi
        icon = "fa fa-phone-alt", -- Uygulama simgesi
        tooltipText = "Telefon", -- Uygulama adı
        tooltipPos = "top",
        job = false, -- İş gereksinimi
        blockedjobs = {}, -- Bu uygulamayı kullanamayan işler
        slot = 1, -- Uygulama konumu
        Alerts = 0, -- Bildirim sayısı
    },
}
```
## Fotoğraflar için server/main.lua dosyasında Webhook ayarlama
Aşağıdaki değişkeni Webhook'unuza ayarlayın (Örneğin, bir Discord kanalı veya Imgur webhook'u)

# Discord kullanmak için:
- Fotoğraflar için ayrılmış bir kanala sağ tıklayın
- Kanalı Düzenle seçeneğini tıklayın
- Entegrasyonlar seçeneğini tıklayın
- Webhookları Görüntüle seçeneğini tıklayın
- Yeni Webhook seçeneğini tıklayın
- Kanalı onaylayın
- Webhook URL'sini kopyalayın
- `server/main.lua` dosyasındaki `WebHook` değişkenine yapıştırın
```
local WebHook = ""
```
