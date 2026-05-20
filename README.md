# JavaScript ile Masaüstü Uygulama Geliştirme: Electron.js ve Tauri

* Bu çalışma, Bartın Üniversitesi bünyesinde modern web teknolojilerinin masaüstü uygulama geliştirme ekosistemindeki rolünü, mimari yapılarını ve sektörel uygulamalarını incelemek amacıyla hazırlanmış bir akademik araştırma raporudur.

## 📌 Özet ve Giriş
Günümüzde JavaScript; tarayıcı sınırlarını aşarak sunucu taraflı geliştirmeden nesnelerin internetine ve masaüstü uygulama süreçlerine kadar geniş bir alana yayılmıştır.C++, C# veya Java gibi geleneksel dillerin aksine HTML, CSS ve JavaScript kullanarak tek bir kod tabanı üzerinden Windows, macOS ve Linux uyumlu çapraz platform uygulamalar geliştirmek, modern yazılım ekosisteminde hem maliyetleri düşürmekte hem de zengin UI/UX olanakları sunmaktadır

---

## 🏗️ Mimari İnceleme ve Teknolojiler

### 1. Electron.js ve Çok İşlemli Mimarisi
Electron.js; Chromium ve Node.js tabanlı çalıştırılabilir dosyalar üzerinden çapraz platform uygulama geliştirmeyi sağlar.JavaScript'in tarayıcı içi kısıtlı "sandbox" yapısını Node.js ile aşarak doğrudan işletim sisteminin dosya ve ağ yapılandırmalarına erişim imkanı tanır.

Kullanıcı arayüzünü yüksek performansla ekrana yansıtmak için **Chromium Çok İşlemli (Multi-Process) Mimarisini** kullanır:

![Chromium Mimarisi](assets)
* **Browser Process (Ana Süreç):** Uygulamanın çekirdeğidir. `RenderProcessHost` ve `RenderViewHost` yapıları üzerinden alt süreçlerin yönetimini ve pencerelerin ana yaşam döngüsünü kontrol eder.
* **Renderer Process (Oluşturucu Süreç):** Her pencere veya sekme için ayrı bir `RenderProcess` nesnesi ayağa kaldırılır. `WebKit` motorunu kullanarak HTML/CSS ve JavaScript kodlarını işler ve görsel arayüzü oluşturur.
* **IPC (Inter-Process Communication):** Ana süreç ile oluşturucu süreçler birbirlerinin bellek alanlarına doğrudan erişemezler. Güvenliğin ve kararlılığın korunması adına, süreçler arası tüm veri alışverişi görseldeki kesikli hatlarla belirtilen **IPC kanalları** üzerinden asenkron olarak gerçekleştirilir.

### 2. Tauri Framework
Electron'a modern ve performans odaklı bir alternatif olan Tauri, Rust dili üzerine inşa edilmiştir.Her uygulama için gömülü bir Chromium motoru paketlemek yerine, işletim sisteminin yerel "webview" altyapısını (WRY/TAO) kullanır.Bu sayede paket boyutunu muazzam ölçüde küçülterek (600 KB'a kadar) bellek (RAM) tüketimini optimize eder.

---

## 📊 Teknik Karşılaştırma

Aşağıdaki tablo, araştırmada ele alınan iki büyük framework'ün teknik parametreler doğrultusunda kıyaslanmasını göstermektedir:

| Özellik | Electron.js | Tauri |
| :--- | :--- | :--- |
| **Paket Boyutu** | Yüksek (100MB+) |Çok Düşük (-10MB)  |
| **Bellek (RAM) Kullanımı** | Yüksek  | Düşük  |
| **Güvenlik** | Orta  | Yüksek (Rust Tabanlı)  |
| **Öğrenme Eğrisi** | Kolay (Sadece JS) | Orta (Rust Bilgisi Gerekebilir)  |
| **Tarayıcı Motoru** | Gömülü Chromium  | Sistem Webview (Yerel) |

---

## 🏢 Gerçek Dünya Örnekleri Analizi

* **Visual Studio Code (VS Code):** Arka planda çalışan Node.js altyapısı sayesinde kodları gerçek zamanlı analiz eden (IntelliSense) ve HTML/CSS esnekliği ile tamamen özelleştirilebilen, Electron tabanlı lider bir kod editörüdür.
* **Discord:** Kullanıcı arayüzünü JavaScript/React ile sunarken, sesli iletişim gibi yüksek performans ve düşük gecikme gerektiren işlemler için C++ ile yazılmış yerel modülleri (Native Modules) sisteme bağlayan hibrit bir Electron mimarisidir.

---

📂 Klasör Yapısı

├── dokuman/
│   └── desktop-app-research-report.pdf     # Akademik Araştırma Raporu (Tam Metin)
└── assets/
    └── chromium-multi-process-architecture.png # Chromium Mimari Şeması
    
