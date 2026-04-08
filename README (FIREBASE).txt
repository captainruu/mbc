# 🔥 PANDUAN SETUP FIREBASE — Muscle Beach Club
## Database Online Terpusat (Gratis)

---

## ⚡ LANGKAH SETUP (±10 menit, sekali saja)

### STEP 1 — Buat Project Firebase
1. Buka **https://console.firebase.google.com**
2. Login dengan Google Account
3. Klik **"Add project"** → beri nama: `muscle-beach-club`
4. Disable Google Analytics (opsional) → **Create project**

---

### STEP 2 — Aktifkan Firestore Database
1. Di sidebar kiri, klik **"Firestore Database"**
2. Klik **"Create database"**
3. Pilih **"Start in test mode"** → Next
4. Pilih region terdekat: **`asia-southeast1 (Singapore)`** → Enable

---

### STEP 3 — Ambil Config Website
1. Klik ikon **⚙️ (gear)** → **Project settings**
2. Scroll ke bawah → bagian **"Your apps"**
3. Klik ikon **`</>`** (Web)
4. Register app: nama bebas, klik **"Register app"**
5. Copy **firebaseConfig** yang muncul:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "muscle-beach-club.firebaseapp.com",
  projectId: "muscle-beach-club",
  storageBucket: "muscle-beach-club.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

---

### STEP 4 — Paste ke index.html

Buka `index.html`, cari baris ini (sekitar baris 899):

```javascript
const firebaseConfig = {
  apiKey:            "PASTE_YOUR_apiKey_HERE",
  authDomain:        "PASTE_YOUR_authDomain_HERE",
  projectId:         "PASTE_YOUR_projectId_HERE",
  storageBucket:     "PASTE_YOUR_storageBucket_HERE",
  messagingSenderId: "PASTE_YOUR_messagingSenderId_HERE",
  appId:             "PASTE_YOUR_appId_HERE"
};
```

**Ganti** nilai `"PASTE_YOUR_..."` dengan nilai dari Firebase Anda.

---

### STEP 5 — Atur Firestore Rules (Keamanan)

1. Di Firestore → klik tab **"Rules"**
2. Ganti rules dengan ini (untuk production):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Members: read & write (admin manages via admin panel)
    match /members/{doc} {
      allow read, write: if true;
    }
    // Packages: anyone can read, write allowed
    match /packages/{doc} {
      allow read, write: if true;
    }
    // Promos: anyone can read, write allowed
    match /promos/{doc} {
      allow read, write: if true;
    }
  }
}
```

3. Klik **Publish**

---

### STEP 6 — Deploy ke GitHub Pages

1. Buat repository baru di GitHub: `muscle-beach-club`
2. Upload `index.html` ke root repository
3. Settings → Pages → Source: `main` / `root`
4. Live di: `https://username.github.io/muscle-beach-club/`

---

## ✅ HASIL SETELAH SETUP

| Fitur | Status |
|-------|--------|
| Database terpusat | ✅ Semua device sync |
| Data member | ✅ Tersimpan di Firestore |
| Paket & harga | ✅ Edit dari admin, langsung update |
| Promo & event | ✅ Upload dari admin, langsung tampil |
| Login admin | ✅ Kode: `#admin0#` |
| Login member | ✅ Kode unik (e.g. `MBC-2025-AB3X7K`) |
| Export CSV | ✅ Download dari admin panel |
| Scan QR | ✅ Kamera real-time |

---

## 🆓 KUOTA GRATIS FIREBASE (Spark Plan)

| | Limit Gratis |
|--|--|
| Firestore reads | 50,000/hari |
| Firestore writes | 20,000/hari |
| Storage | 1 GB |
| Bandwidth | 10 GB/bulan |

→ **Lebih dari cukup** untuk gym kecil-menengah.

---

## 🔑 LOGIN CREDENTIALS

| Role | Kode |
|------|------|
| **Admin** | `#admin0#` |
| **Member** | Kode unik yang di-generate saat registrasi (contoh: `MBC-2025-AB3X7K`) |

---

*© 2024 Muscle Beach Club – Uluwatu, Bali*