# QR Kod Oluşturucu

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![License](https://img.shields.io/badge/license-MIT-orange.svg)
![GitHub](https://img.shields.io/github/stars/serialprint/QR_Code?style=social)

**Python ile QR Kod Oluşturma Uygulaması**

Tkinter arayüzü ile girilen metinden QR kod oluşturan ve belirtilen konuma kaydeden Python uygulaması.

</div>

---

## 📋 İçindekiler

- [Özellikler](#-özellikler)
- [Gereksinimler](#-gereksinimler)
- [Kurulum](#-kurulum)
- [Kullanım](#-kullanım)
- [Ekran Görüntüsü](#-ekran-görüntüsü)

---

## ✨ Özellikler

- ✅ **Kolay Kullanım**: Basit ve kullanıcı dostu arayüz
- ✅ **Farklı Kalite Seçenekleri**: Düşük, Normal, Yüksek kalite
- ✅ **Özelleştirilebilir Kayıt Yeri**: İstediğiniz klasöre kaydedin
- ✅ **Türkçe Arayüz**: Tamamen Türkçe kullanım

---

## 🔧 Gereksinimler

- Python 3.x
- qrcode kütüphanesi
- tkinter (Python ile birlikte gelir)
- Pillow (PIL)

---

## 📦 Kurulum

### 1. Gerekli Kütüphaneleri Yükleyin

```bash
pip install qrcode[pil]
pip install pillow
```

### 2. Uygulamayı Çalıştırın

```bash
python "QR Code.py"
```

---

## 🚀 Kullanım

1. Uygulamayı başlatın
2. QR koda dönüştürmek istediğiniz metni girin
3. Kalite seçeneğini belirleyin:
   - **Düşük Kalite**: 150x150 piksel
   - **Normal Kalite**: 300x300 piksel
   - **Yüksek Kalite**: 600x600 piksel
4. Kayıt dizinini seçin (varsayılan: Masaüstü)
5. "QR Kodu Oluştur ve Kaydet" butonuna tıklayın
6. QR kod `qrcode.png` olarak kaydedilir

---

## 🖼️ Ekran Görüntüsü

```
┌─────────────────────────────┐
│     QR Kodu Oluşturucu      │
├─────────────────────────────┤
│  Metin:                     │
│  [___________________]      │
│                             │
│  Boyut:                     │
│  ○ Düşük Kalite             │
│  ● Normal Kalite            │
│  ○ Yüksek Kalite            │
│                             │
│  Kayıt Dizini: ~/Masaüstü   │
│  [  Kayıt Dizini Seç  ]     │
│                             │
│  [QR Kodu Oluştur ve Kaydet]│
│                             │
│  QR kodu oluşturuldu!       │
└─────────────────────────────┘
```

---

## 💻 Kod Yapısı

### Ana Sınıf

```python
class QRCodeUygulamasi:
    def __init__(self, ana_pencere):
        # Pencere ayarları
        # Arayüz oluşturma
    
    def kayit_dizini_sec(self):
        # Kayıt dizini seçimi
    
    def kaydet(self):
        # QR kod oluşturma ve kaydetme
```

### QR Kod Oluşturma

```python
qr = qrcode.QRCode(
    version=1,
    error_correction=qrcode.constants.ERROR_CORRECT_L,
    box_size=10,
    border=4,
)
qr.add_data(metin)
qr.make(fit=True)
qr_goruntu = qr.make_image(fill_color="black", back_color="white")
```

---

## 🐛 Sorun Giderme

### ModuleNotFoundError: No module named 'qrcode'

```bash
pip install qrcode[pil]
```

### Tkinter Hatası

Tkinter genellikle Python ile birlikte gelir. Eğer hata alıyorsanız:

**Windows:**
Python'u yeniden yüklerken "tcl/tk and IDLE" seçeneğini işaretleyin.

**Linux:**
```bash
sudo apt-get install python3-tk
```

---

## 📝 Versiyon Geçmişi

### v1.0.0
- İlk sürüm
- Temel QR kod oluşturma
- Kalite seçenekleri
- Kayıt dizini seçimi

---

## 📄 Lisans

Bu proje MIT lisansı altında lisanslanmıştır.

---

## 👤 Yazar

**serialprint**
- GitHub: [@serialprint](https://github.com/serialprint)

---

<div align="center">

**⭐ Beğendiyseniz yıldız vermeyi unutmayın! ⭐**

Made with ❤️ by serialprint

</div>
