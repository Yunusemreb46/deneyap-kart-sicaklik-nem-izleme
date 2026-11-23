# deneyap-kart-sicaklik-nem-izleme
Deneyap Kart, DHT22 sensörü ve I2C LCD ekran kullanarak ortam sıcaklığı ile nemini ölçen, verileri seri haberleşme (UART) üzerinden C# Windows Forms arayüzüne anlık aktaran izleme sistemi.



# Deneyap Kart ve C# ile Gerçek Zamanlı Sıcaklık-Nem İzleme Sistemi

## Projenin Amacı
Bu projenin amacı, **Deneyap Kart**, **DHT22** sensörü ve **16x2 I2C LCD ekran** kullanarak ortamın sıcaklık ve nem verilerini ölçmek, bu verileri hem yerel LCD ekranda hem de **C# Windows Forms** masaüstü arayüzünde anlık olarak görüntülemektir. Deneyap Kart, topladığı verileri seri haberleşme (UART) üzerinden **115200 baud** hızıyla ve `TEMP:xx.x,HUM:xx.x` formatında bilgisayara gönderir; C# arayüzü de bu verileri okuyarak ekrana yansıtır.

## Donanım ve Bağlantılar
* **DHT22 Sensörü:** Veri ucu **D4** pinine, güç uçları uygun besleme (`3V3` / `GND`) hatlarına bağlanır.
* **16x2 I2C LCD Ekran:** `SDA` ve `SCL` hatları Deneyap Kart'ın ilgili pinlerine, güç uçları (`5V` / `GND`) besleme hattına bağlanır.
* **Bilgisayar Bağlantısı:** Deneyap Kart, USB kablosu ile bilgisayara bağlanır.

## Kurulum Adımları

1. **Arşiv / Klasör Yapısı:**
   * Proje dosyalarını (`.ino` mikrodenetleyici kodu ve `IsiNemArayuz` C# proje dosyaları) çıkartın veya ilgili klasörlere ayırın.

2. **Deneyap Kart Kodunun Yüklenmesi:**
   * **Arduino IDE**'yi açın ve Deneyap Kart kütüphanesi ile `DHT` ve `LiquidCrystal_I2C` kütüphanelerinin kurulu olduğundan emin olun.
   * `.ino` dosyasını açın, doğru Deneyap Kart modelini ve COM portunu seçip kodu karta yükleyin.
   * Yükleme sonrası C# arayüzünü açmadan önce seri monitörün kapalı ve portun boşta olduğundan emin olun.

3. **C# Arayüzünün Hazırlanması ve Çalıştırılması:**
   * `IsiNemArayuz` klasörünü VS Code veya Visual Studio ile açın.
   * Terminalde proje klasörüne girip `System.IO.Ports` paketini yükleyin:
     ```bash
     dotnet add package System.IO.Ports
     ```
   * **Aygıt Yöneticisi** üzerinden Deneyap Kart'ın bağlı olduğu COM portunu kontrol edin ve arayüzde doğru portu seçip bağlanın.
   * Sıcaklık ve nem değerlerinin arayüzde ve I2C ekranda güncellendiğini doğrulayın.
