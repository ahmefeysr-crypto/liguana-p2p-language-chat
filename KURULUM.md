# 🦎 Liguana P2P Dil Öğrenme Chat - Kurulum Rehberi

## 📋 Gereksinimler

- **Node.js 18+** ve npm
- **Gmail hesabı** (e-posta bildirimleri için) veya başka SMTP servisi
- **Modern web tarayıcısı** (WebRTC ve WebCrypto desteği ile)

## 🚀 Hızlı Kurulum

### 1. Projeyi İndirin ve Açın
```bash
# ZIP dosyasını açın ve klasöre girin
cd liguana-p2p-chat

# Bağımlılıkları yükleyin
npm install
```

### 2. E-posta Ayarlarını Yapın
```bash
# .env.local dosyası oluşturun
cp .env.example .env.local
```

`.env.local` dosyasını düzenleyin:
```env
EMAIL_USER=sizin-email@gmail.com
EMAIL_PASS=uygulama-sifreniz
NEXT_PUBLIC_BASE_URL=http://localhost:3000
NODE_ENV=development
```

### 3. Gmail Uygulama Şifresi Oluşturun
1. Gmail hesabınızda 2 faktörlü doğrulamayı açın
2. Google Hesap Ayarları > Güvenlik > Uygulama şifreleri
3. "Mail" için yeni uygulama şifresi oluşturun
4. Bu şifreyi `EMAIL_PASS` olarak kullanın

### 4. Uygulamayı Başlatın
```bash
npm run dev
```

### 5. Tarayıcıda Açın
```
http://localhost:3000/Liguana1.2/chat.html
```

## 🎯 Nasıl Kullanılır

1. **Dil ve Seviye Seçin**: Öğrenmek istediğiniz dil ve seviyenizi seçin
2. **E-posta Girin**: Eşleşme bildirimleri için e-posta adresinizi girin
3. **Sohbet Başlat**: "Sohbet Başlat" butonuna tıklayın
4. **RSA Anahtarını İndirin**: Güvenlik anahtarınızı kaydedin
5. **Eşleşme Bekleyin**: Uygun partner bulunduğunda e-posta alacaksınız
6. **Sohbet Edin**: Güvenli P2P bağlantı ile dil pratiği yapın

## 🔧 Özelleştirme

### Tema Değiştirme
- Sağ üst köşedeki tema değiştirici ile 4 farklı tema arasında geçiş yapın

### Yeni Dil Ekleme
1. `public/Liguana1.2/chat.html` - dil seçeneklerini güncelleyin
2. `public/Liguana1.2/p2p.js` - `getLanguageName()` fonksiyonunu güncelleyin
3. `src/app/api/sendEmail/route.js` - e-posta şablonlarını güncelleyin

### SMTP Ayarları
Farklı e-posta sağlayıcısı kullanmak için `src/app/api/sendEmail/route.js` dosyasındaki transporter ayarlarını değiştirin.

## 🛠️ Geliştirme

### Proje Yapısı
```
├── public/Liguana1.2/     # Frontend uygulaması
│   ├── chat.html          # Ana sohbet arayüzü
│   ├── style.css          # Stil ve temalar
│   ├── js.js             # Ana JavaScript
│   ├── rsa.js            # RSA şifreleme modülü
│   └── p2p.js            # WebRTC P2P iletişim
├── src/app/api/          # Next.js API rotaları
│   ├── matchmaking/      # Kullanıcı eşleştirme
│   ├── sendEmail/        # E-posta bildirimleri
│   └── signaling/        # WebRTC sinyalleşme
└── README.md             # Detaylı dokümantasyon
```

### API Endpoints
- `POST /api/matchmaking` - Eşleşme için kayıt
- `GET /api/matchmaking` - Eşleşme kontrolü
- `POST /api/sendEmail` - E-posta gönderimi
- `POST /api/signaling` - WebRTC sinyalleri

## 🔒 Güvenlik

- **RSA-OAEP Şifreleme**: 2048-bit RSA anahtarları
- **P2P İletişim**: Mesajlar sunucuda saklanmaz
- **Geçici Oturumlar**: Sohbet geçmişi kalıcı değil
- **E-posta Güvenliği**: Uygulama şifreleri kullanın

## 🚀 Prodüksiyon Dağıtımı

### Vercel'de Dağıtım
```bash
npm install -g vercel
vercel
```

### Çevre Değişkenleri
Prodüksiyon ortamında şu değişkenleri ayarlayın:
```env
EMAIL_USER=production-email@gmail.com
EMAIL_PASS=production-app-password
NEXT_PUBLIC_BASE_URL=https://yourdomain.com
NODE_ENV=production
```

### Veritabanı Entegrasyonu
Prodüksiyon için in-memory storage yerine Redis veya PostgreSQL kullanın.

## 🆘 Sorun Giderme

### Yaygın Sorunlar

**E-posta gönderilmiyor:**
- Gmail uygulama şifresini kontrol edin
- 2 faktörlü doğrulamanın açık olduğundan emin olun

**WebRTC bağlantı sorunu:**
- Tarayıcının WebRTC desteğini kontrol edin
- HTTPS kullanın (prodüksiyon için)

**RSA anahtar hatası:**
- Tarayıcının WebCrypto API desteğini kontrol edin
- HTTPS bağlantısı gerekebilir

### Log Kontrolü
```bash
# Geliştirme logları
npm run dev

# Tarayıcı konsolunu kontrol edin
F12 > Console
```

## 📞 Destek

- **GitHub Issues**: Hata raporları ve özellik istekleri
- **Dokümantasyon**: README.md dosyasını inceleyin
- **Kod İnceleme**: Satır içi yorumları okuyun

## 🎉 Başarılı Kurulum!

Artık Liguana P2P Dil Öğrenme Chat uygulamanız hazır! Güvenli ve anonim bir şekilde dil pratiği yapmaya başlayabilirsiniz.

**İyi sohbetler! 🌟**
