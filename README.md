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
![Home](https://cdn.discordapp.com/attachments/1015405908223860836/1118692592599703642/image.png)
![Bank](https://cdn.discordapp.com/attachments/1015405908223860836/1118692973790625952/image.png)
![Advert](https://media.discordapp.net/attachments/1015405908223860836/1118693103864381510/image.png)
![Mail](https://cdn.discordapp.com/attachments/1015405908223860836/1118693230163279912/image.png)
![Garage](https://cdn.discordapp.com/attachments/1015405908223860836/1118693339315851314/image.png)
![Garage Detail](https://cdn.discordapp.com/attachments/1015405908223860836/1118693498602922125/image.png)
![services](https://cdn.discordapp.com/attachments/1015405908223860836/1118693612079808522/image.png)
![Houses](https://cdn.discordapp.com/attachments/1015405908223860836/1118693754388353124/image.png)
![Racing](https://cdn.discordapp.com/attachments/1015405908223860836/1118693849204801666/image.png)
![Crypto](https://cdn.discordapp.com/attachments/1015405908223860836/1118694029148819588/image.png)
![Gallery](https://cdn.discordapp.com/attachments/1015405908223860836/1118694118877573140/image.png)
![Twitter](https://cdn.discordapp.com/attachments/1015405908223860836/1118694277334179910/image.png)
![Settings](https://cdn.discordapp.com/attachments/1015405908223860836/1118694445873889330/image.png)
![Whatsapp](https://cdn.discordapp.com/attachments/1015405908223860836/1118694602258530364/image.png)
![Phone](https://cdn.discordapp.com/attachments/1015405908223860836/1118694686903783444/image.png)

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
