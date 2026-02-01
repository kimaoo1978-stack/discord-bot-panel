# 🌐 Discord Bot Web Panel

Modern ve kullanıcı dostu Discord bot yönetim paneli!

## 📋 Özellikler

✅ Discord OAuth2 ile güvenli giriş  
✅ Gerçek zamanlı başvuru yönetimi  
✅ Detaylı istatistikler  
✅ Responsive tasarım  
✅ Koyu tema  
✅ Hızlı işlem butonları  

---

## 🚀 Kurulum

### 1. Gerekli Paketleri Yükle

```bash
npm install
```

### 2. Discord Developer Portal Ayarları

1. [Discord Developer Portal](https://discord.com/developers/applications) 'a git
2. Botunu seç (veya yeni oluştur)
3. **OAuth2** sekmesine git
4. **Redirects** kısmına ekle:
   ```
   http://localhost:3000/callback
   ```
   (Canlıya aldığında domain'inle değiştir: https://siteadi.com/callback)

5. **OAuth2 URL Generator** kısmında:
   - Scopes: `identify`, `guilds`
   - Redirect URL'i seç

6. **General Information** sekmesinden:
   - `CLIENT ID` kopyala
   - `CLIENT SECRET` kopyala

### 3. Config Ayarla

`webpanel.js` dosyasını aç ve şunları değiştir:

```javascript
const config = {
  clientID: 'BURAYA_CLIENT_ID',
  clientSecret: 'BURAYA_CLIENT_SECRET',
  callbackURL: 'http://localhost:3000/callback',
  scope: ['identify', 'guilds']
};
```

### 4. Çalıştır

```bash
npm start
```

Tarayıcıda aç: **http://localhost:3000**

---

## 🌍 Canlıya Alma (Hosting)

### Ücretsiz Seçenekler:

#### 1. **Railway** (Önerilen) ⭐
- [Railway.app](https://railway.app) 'a git
- GitHub ile giriş yap
- "New Project" → "Deploy from GitHub"
- Repo'nu seç → Otomatik deploy olur
- Environment Variables ekle:
  ```
  CLIENT_ID=...
  CLIENT_SECRET=...
  CALLBACK_URL=https://yourapp.railway.app/callback
  ```

#### 2. **Render**
- [Render.com](https://render.com) 'a git
- "New Web Service"
- GitHub repo'nu bağla
- Otomatik deploy

#### 3. **Glitch**
- [Glitch.com](https://glitch.com)
- "New Project" → "Import from GitHub"
- `.env` dosyasına secret'ları ekle

---

## 📁 Dosya Yapısı

```
discord-bot-webpanel/
├── webpanel.js           # Ana server dosyası
├── package.json          # Bağımlılıklar
├── views/                # HTML sayfaları
│   ├── index.ejs         # Ana sayfa
│   ├── dashboard.ejs     # Dashboard
│   ├── applications.ejs  # Başvurular
│   └── settings.ejs      # Ayarlar
└── public/               # Statik dosyalar
    └── css/
        └── style.css     # Stil dosyası
```

---

## 🔧 Özelleştirme

### Renkleri Değiştir

`public/css/style.css` dosyasındaki `:root` kısmını düzenle:

```css
:root {
  --primary: #5865F2;     /* Ana renk */
  --success: #3BA55D;     /* Başarı rengi */
  --danger: #ED4245;      /* Hata rengi */
  /* ... */
}
```

### Yeni Sayfa Ekle

1. `views/yenisayfa.ejs` oluştur
2. `webpanel.js` 'e route ekle:

```javascript
app.get('/yenisayfa', checkAuth, (req, res) => {
  res.render('yenisayfa', { user: req.user });
});
```

---

## 🔗 Domain Bağlama

### Ücretsiz Domain:

1. **Freenom** veya **dot.tk** 'den ücretsiz domain al
2. Hosting'inin IP adresini domain'e yönlendir
3. `callbackURL` 'i güncelle:

```javascript
callbackURL: 'https://senindomain.com/callback'
```

### Cloudflare (SSL için):

1. [Cloudflare.com](https://cloudflare.com) 'a kayıt ol
2. Domain'ini ekle
3. SSL/TLS → Full
4. Otomatik HTTPS aktif

---

## 📊 Database Ekleme (İsteğe Bağlı)

Başvuruları saklamak için MongoDB ekle:

```bash
npm install mongoose
```

`webpanel.js` 'e ekle:

```javascript
const mongoose = require('mongoose');
mongoose.connect('MONGODB_URL');
```

---

## ❓ Sorun Giderme

### "Cannot find module" hatası:
```bash
npm install
```

### Port zaten kullanılıyor:
`webpanel.js` 'te portu değiştir:
```javascript
const PORT = 8080; // veya başka bir port
```

### OAuth2 hatası:
- Discord Developer Portal'da redirect URL'i kontrol et
- CLIENT_ID ve SECRET doğru mu kontrol et

---

## 📝 Yapılacaklar (Gelecek)

- [ ] Database entegrasyonu
- [ ] Gerçek zamanlı bildirimler (WebSocket)
- [ ] Gelişmiş istatistik grafikleri
- [ ] Multi-language desteği
- [ ] Dark/Light tema switcher
- [ ] Export raporlar (PDF/Excel)

---

## 🤝 Katkıda Bulun

Pull request'ler kabul edilir! 

---

## 📞 Destek

Sorun yaşıyorsan Discord sunucumuza katıl: [Link]

---

## ⭐ Beğendiysen Yıldız Ver!

Bu projeyi kullanıyorsan GitHub'da yıldız vermeyi unutma 😊

---

**Made with ❤️ for Discord Bot Developers**
