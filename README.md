# deneyap-kart-sicaklik-nem-izleme
Deneyap Kart, DHT22 sensörü ve I2C LCD ekran kullanarak ortam sıcaklığı ile nemini ölçen, verileri seri haberleşme (UART) üzerinden C# Windows Forms arayüzüne anlık aktaran izleme sistemi.



# Deneyap Kart ve C# ile Gerçek Zamanlı Sıcaklık-Nem İzleme Sistemi

## Projenin Amacı
Bu proje; **Deneyap Kart**, **DHT22** sıcaklık/nem sensörü ve **16x2 I2C LCD ekran** kullanarak ortamın sıcaklık ve nem değerlerini ölçen, bu verileri hem yerel LCD ekranda hem de **C# Windows Forms** masaüstü arayüzünde anlık olarak görüntüleyen bir izleme sistemidir. Deneyap Kart, topladığı verileri seri haberleşme (UART) üzerinden **115200 baud** hızıyla `TEMP:xx.x,HUM:xx.x` formatında bilgisayara aktarır.

## Donanım ve Pin Bağlantıları

| Bileşen | Deneyap Kart Pini | Açıklama |
| :--- | :---: | :--- |
| **DHT22 (DAT)** | `D4` | Dijital veri hattı |
| **DHT22 (VCC / GND)** | `3V3` / `GND` | Sensör güç beslemesi |
| **16x2 I2C LCD (SDA / SCL)** | `SDA` / `SCL` | I2C veri ve saat hatları (çapraz bağlanmamalıdır) |
| **16x2 I2C LCD (VCC / GND)** | `5V` / `GND` | Ekran güç beslemesi |

## Kurulum ve Çalıştırma Adımları

1. Bu depodaki `.zip` uzantılı proje arşivini bilgisayarınıza indirin.
2. İndirdiğiniz ZIP dosyasına sağ tıklayıp **"Tümünü Ayıkla" (Extract All)** seçeneği ile dosyaları boş bir klasöre çıkartın (klasör içinde `.ino` dosyası ve `IsiNemArayuz` klasörü yer alacaktır).
3. Bilgisayarınızda **Arduino IDE** uygulamasını açın.
4. **Araçlar > Kart > Kart Yöneticisi** menüsünden **Deneyap Kart** paketinin kurulu olduğundan emin olun.
5. **Taslak > Library Ekle > Kütüphaneleri Yönet** menüsünden `DHT sensor library` (Adafruit) ve `LiquidCrystal I2C` kütüphanelerini aratıp kurun.
6. Ayıkladığınız klasördeki `.ino` uzantılı kodu Arduino IDE ile açın.
7. Deneyap Kart'ı USB kablosu ile bilgisayara bağlayın; **Araçlar** menüsünden doğru kart modelini ve **COM portunu** seçip **Yükle (Upload)** butonuna basın.
8. Yükleme tamamlandıktan sonra portun kilitlenmemesi için **Seri Monitör'ün kapalı olduğundan** emin olun.
9. Ayıkladığınız klasör içerisindeki **`IsiNemArayuz`** klasörünü **Visual Studio** ile açın.
10. Terminali açıp proje dizinine (`IsiNemArayuz`) girin ve seri haberleşme paketini yükleyin:
    ```bash
    dotnet add package System.IO.Ports
    ```
11. Windows **Aygıt Yöneticisi > Bağlantı Noktaları (COM ve LPT)** sekmesinden Deneyap Kart'ın bağlı olduğu COM port numarasını kontrol edin ve gerekirse `Program.cs` içerisindeki port bilgisini güncelleyin.
12. Uygulamanın ana giriş dosyası olan **`Program.cs`** dosyasını çalıştırın VS Code üzerinden **Run / F5** tuşuyla veya terminalde `dotnet run` komutu ile).
13. Masaüstü arayüz penceresi açılacak ve karttan gelen sıcaklık ile nem değerleri ekranda anlık olarak görüntülenmeye başlayacaktır. **Tüm bu adımlar tamamlandığında kurulum bitmiş ve sistem sorunsuz bir şekilde çalışmış olur.**
