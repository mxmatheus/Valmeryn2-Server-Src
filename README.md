# Valmeryn2 Server Source

Valmeryn2 server ve DB süreçlerinin C++ kaynak kodu ile CMake build yapılandırması.

## Gereksinimler

- CMake 3.20 veya üstü
- C++20 uyumlu derleyici
- MariaDB Connector/C ve depodaki diğer bağımlılıklar
- Windows için Visual Studio C++ araçları; hedef sunucu işletim sistemi için ayrıca uygun toolchain

## Derleme

```powershell
cmake -S . -B build
cmake --build build --config Release
```

Üretim sunucusu için hedef işletim sisteminde derleme ve bağımlılıkların o sistemle uyumunu ayrıca sağlayın. Windows build çıktısını FreeBSD çalışma sunucusuna kopyalamayın.

## Proje düzeni

- `src/`: game/DB kaynakları
- `include/`: ortak başlıklar
- `vendor/`: üçüncü taraf bağımlılıklar
- `buildtool/`: build yardımcıları

## Protokol ve veri tabanı

Client ile paylaşılan her paket değişikliğinde iki taraftaki struct boyutlarını, dispatcher kayıtlarını ve uzunluk kontrollerini beraber güncelleyin. Şema değişikliklerini sıralı migration olarak tutun; yeni Valmeryn DB'sinde yedek alıp doğrulamadan uygulamayın. Oyun içi kanıt olmadan özelliği tamamlandı olarak işaretlemeyin.

Önceki sistem kataloğu ve açık test maddeleri çalışma alanındaki `YENI_PROJE_DEVIR_RAPORU.md` dosyasındadır.
