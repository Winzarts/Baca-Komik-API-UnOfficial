# 🕸️ Komiku API (Unofficial)

API sederhana berbasis **Flask** untuk melakukan **scraping data manga dari Komiku.org**.  
Proyek ini bertujuan untuk menyediakan endpoint API yang dapat digunakan untuk mendapatkan daftar manga, detail, chapter, genre, pencarian, dan manga terbaru.

> ⚠️ **Disclaimer:**  
> API ini *tidak resmi* (Unofficial) dan hanya dibuat untuk keperluan pembelajaran / pengembangan pribadi.  
> Semua data diambil dari situs [Komiku.org](https://komiku.org).

---

## 🚀 Fitur

- 📚 **Daftar Manga per Genre**  
- 🔍 **Pencarian Manga**  
- 🆕 **Manga Terbaru (Latest Update)**  
- 📖 **Detail Manga (sinopsis, genre, status, chapter, dll)**  
- 📜 **Daftar Chapter (awal & terbaru)**  
- 🔗 **Endpoint API konsisten menggunakan struktur URL lokal**

---

## ⚙️ Teknologi yang Digunakan

- **Python 3.10+**
- **Flask**
- **BeautifulSoup (bs4)**
- **Selenium (Chromedriver)**
- **Requests**

---

## 📂 Struktur Proyek

```
komiku_api/
│
├── app.py                 # File utama Flask API
├── config.py              # Konfigurasi global (BASE_URL, API_BASE, HEADERS, TIMEOUT)
├── requirements.txt       # Dependensi Python
├── README.md              # Dokumentasi proyek
└── utils/
    └── scraper.py         # Fungsi scraping & parser HTML
```

---

## 🧩 Contoh Endpoint

### 🔹 1. Manga Terbaru
```
GET /latest
```
**Contoh Response:**
```json
{
  "count": 20,
  "results": [
    {
      "title": "My Disciples Are All Big Villains",
      "slug": "my-disciples-are-all-big-villains",
      "thumbnail": "https://cdn.komiku.org/cover.jpg",
      "chapter_awal": "http://127.0.0.1:3080/manga/my-disciples-are-all-big-villains/my-disciples-are-all-big-villains-chapter-01/",
      "chapter_terbaru": "http://127.0.0.1:3080/manga/my-disciples-are-all-big-villains/my-disciples-are-all-big-villains-chapter-428/"
    }
  ]
}
```

---

### 🔹 2. Detail Manga
```
GET /manga/<slug>/
```
**Contoh:**
```
GET /manga/my-disciples-are-all-big-villains/
```

---

### 🔹 3. Daftar Chapter
```
GET /manga/<slug>/<chapter_slug>/
```

---

### 🔹 4. Pencarian
```
GET /search?q=Shut+Up
```

**Contoh Response:**
```json
{
  "query": "Shut Up",
  "count": 2,
  "results": [
    {
      "title": "Shut Up and Run!",
      "genre": "Drama, Romance",
      "description": "Kisah cinta penuh tantangan...",
      "thumbnail": "https://komiku.org/wp-content/uploads/...jpg",
      "link": "http://127.0.0.1:3080/manga/shut-up-and-run/"
    }
  ]
}
```

---

## 🧠 Cara Menjalankan

### 1. Clone Repository
```bash
git clone https://github.com/username/komiku-api.git
cd komiku-api
```

### 2. Install Dependensi
```bash
pip install -r requirements.txt
```

### 3. Jalankan Server
```bash
python app.py
```

Local server akan berjalan di:
```
http://127.0.0.1:3080
```

---

## 🧾 Contoh Konfigurasi `config.py`
```python
BASE_URL = "https://example.com"
API_BASE = "http://127.0.0.1:3080"
HEADERS = {"User-Agent": "Mozilla/5.0"}
TIMEOUT = 15
```

---

## 💡 Catatan
- Sebagian halaman di Komiku menggunakan **HTMX** dan memerlukan **Selenium** karena kontennya dimuat secara dinamis.
- Pastikan **ChromeDriver** sudah terpasang dan sesuai dengan versi browser kamu.
- Untuk performa lebih cepat, kamu bisa menggunakan sistem caching sederhana (misalnya dengan `functools.lru_cache` atau Redis).

---

## 🧑‍💻 Author

**Bluenight**  
🔗 *Project belajar scraping & API sederhana berbasis Flask*  
🖥️ Dibuat dengan semangat belajar dan secangkir kopi ☕  
