# OverTheWire Wargames Solutions & Documentation

<p align="center">
  <img src="https://img.shields.io/badge/Security-Wargames-red?style=for-the-badge" alt="Security">
  <img src="https://img.shields.io/badge/Linux-Bash-Personal?style=for-the-badge&color=black" alt="Linux">
  <img src="https://img.shields.io/badge/Language-EN%20%7C%20TR-blue?style=for-the-badge" alt="Languages">
</p>

---

## English Description

Welcome to my **OverTheWire Wargames** repository! This project serves as my personal cyber security log where I document my solutions, methodologies, and core findings while progressing through various security challenges hosted by OverTheWire.

The primary goal of this repository is to track my development in command-line proficiency, server administration, network protocols, and ethical hacking principles, creating a structured professional portfolio.

### 📂 Repository Structure
```text
├── Bandit/              # Linux command line fundamentals
│   ├── bandit1.md       # Detailed methodology for levels 1 to 2
│   ├── bandit6.md       # Detailed methodology for levels 6 to 7
│   └── README.md        # Bandit series overview & core learning objectives
├── Natas/               # Web application security concepts (Future)
└── README.md            # Main entry point (This file)
```
📝 Write-up Content Policy & Spoiler Alert
⚠️ Strict Anti-Spoiler Policy: To respect the OverTheWire community guidelines and encourage genuine problem-solving, this repository does not contain plaintext flags or level passwords. It focuses strictly on commands, concepts, and analytical logic.

🛠️ Sample Write-up Format
Each milestone markdown file utilizes a standardized template for structural consistency:
### Level 03 ➔ Level 04
- **Objective:** Locate the hidden file hidden inside the `inhere` directory.
- **Commands Utilized:** `ls -la`, `cd`, `cat`
- **Core Concept:** In Linux environments, files prefixed with a dot (`.`) are hidden by default. Standard directory listings omit them; thus, the `-a` (all) flag must be appended to the list command.

  
## Türkçe Açıklama

OverTheWire Wargames çözüm ve dokümantasyon repoma hoş geldiniz! Bu proje, OverTheWire platformunda yer alan siber güvenlik laboratuvarlarını çözerken edindiğim bilgileri, kullandığım yöntemleri ve teknik yaklaşımları kayıt altında tuttuğum kişisel siber güvenlik günlüğüm ve portfolyomdur.

Bu reponun temel amacı; Linux komut satırı hakimiyeti, sunucu yönetimi, ağ protokolleri ve temel sızma testi mantığı konularındaki pratik gelişimimi yapılandırılmış bir düzende takip etmektir.
```text
├── Bandit/              # Temel Linux komut satırı pratikleri
│   ├── bandit1.md       # 1. seviyeden 2'ye geçerken izlenilen yol
│   ├── bandit6.md       # 6. seviyeden 7'ye geçerken izlenilen yol
│   └── README.md        # Bandit serisi özeti ve öğrenim çıktıları
├── Natas/               # Web uygulamaları güvenliği konseptleri (Yakında)
└── README.md            # Ana giriş sayfası (Bu dosya)
```

📝 Çözüm Politikası ve Spoiler Uyarısı
⚠️ Etik Kurallar ve Gizlilik: OverTheWire topluluk kurallarına saygı duymak ve öğrenme sürecini baltalamamak adına, bu repoda bölüm şifreleri (flag değerleri) açık metin olarak paylaşılmamaktadır. Dokümantasyonlar tamamen çözüm mantığına ve komut analizlerine odaklıdır.

🛠️ Örnek Çözüm Şablonu
İçerik kalitesini ve okunabilirliği korumak adına tüm seviyeler şu şablona göre dökümante edilmektedir:
### Seviye 03 ➔ Seviye 04
- **Amaç:** `inhere` dizini içerisindeki gizli dosyayı tespit etmek ve okumak.
- **Kullanılan Komutlar:** `ls -la`, `cd`, `cat`
- **Temel Konsept:** Linux işletim sistemlerinde ismi nokta (`.`) ile başlayan dosyalar gizli dosya statüsündedir. Düz bir `ls` komutu ile listelenmezler; bu sebeple tüm dosyaları görmek için `-a` (all) parametresi eklenmelidir.
