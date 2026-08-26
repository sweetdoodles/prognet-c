# Laporan Take-Home Assignment — Student Hub & Code Defense

**Nama :** Ida Ayu Putu Audrey Tara Cahyarani
**NIM :** 2505551128
**Program Studi :** Teknologi Informasi, Fakultas Teknik, Universitas Udayana
**Bidang Minat (Kurikulum 2026) :** Artificial Intelligence

---

## 1. Langkah-Langkah (Step-by-Step)

Berikut runtutan perintah terminal dari awal setup proyek hingga menjalankan `npm run dev`:

```bash
# 1. Membuat proyek Vite + React baru
npm create vite@latest student-hub -- --template react

# 2. Masuk ke folder proyek & install dependency dasar
cd student-hub
npm install

# 3. Install Tailwind CSS beserta plugin Vite-nya
npm install -D tailwindcss @tailwindcss/vite

# 4. Install lucide-react untuk ikon (opsional, dipakai di komponen ini)
npm install lucide-react

# 5. Menjalankan development server
npm run dev
```

  **Dokumentasi:**
![image alt](https://github.com/sweetdoodles/prognet-c/blob/0b8fd03ec724fe417d7751262902d06cfa629a02/Screenshot%202026-08-26%20191016.png)

Setelah `npm run dev` dijalankan, aplikasi dapat diakses di `http://localhost:5173`. Seluruh tampilan Student Hub ditulis dalam satu file `src/App.jsx` (Single-File Component), tanpa membuat file atau folder tambahan di luar file tersebut.

---

## 2. AI Prompt Log

Berikut prompt persis yang digunakan untuk men-generate komponen `src/App.jsx` melalui AI coding assistant (Antigravity/Copilot):

```
Buatkan Web Student Hub Personal Mahasiswa TI Unud di file src/App.jsx menggunakan
React dan Tailwind CSS. Sertakan:

1. Header & Navbar Semantik: Nama "Ida Ayu Putu Audrey Tara Cahyarani", NIM
   "2505551128", dan Bidang Minat Kurikulum 2026 "Artificial Intelligence". Navbar
   berisi link Home, Profile, Projects.

2. Hero Profile: Judul sapaan "Hi, saya Ida Ayu Putu Audrey Tara Cahyarani", bio
   ringkas mahasiswa TI Unud yang tertarik pada AI dan solusi digital, serta target
   Profil Lulusan PL-01 "Pengembang Teknologi Informasi" beserta deskripsinya.

3. Interactive Counter (useState): Stat Card dengan label "Project Selesai", nilai
   awal 3, dan tombol "+ Tambah Project" yang menambah nilai counter setiap diklik.

4. Showcase 3 Card Project: Balinese Culture Digital Archive (React, Database,
   UI/UX), Smart Waste Management (IoT, ESP32, Sensor, Web Dashboard), dan AI
   Academic Assistant (Artificial Intelligence, React, API), masing-masing dengan
   deskripsi singkat dan badge teknologi.

PENTING: Tulis seluruh kodenya langsung di file src/App.jsx saja (Single-File
Component) menggunakan tag HTML5 semantik (header, nav, main, section, footer).
JANGAN membuat file/folder baru di luar file ini!
```

**Catatan constraint:** instruksi *"Single-File Component di src/App.jsx saja menggunakan tag HTML5 semantik"* selalu disertakan agar AI tetap fokus mengubah satu file dan tidak menghasilkan struktur folder acak.

---

## 3. Trace Alur Eksekusi (`index.html` ➔ `main.jsx` ➔ `App.jsx`)

Aplikasi React yang dibuka di browser sebenarnya melalui 3 tahap berantai:

**Tahap 1 — `index.html` (Entry Point Browser)**
Browser pertama kali membuka `index.html`. File ini sebenarnya sangat sepi: ia hanya berisi sebuah `<div id="root"></div>` yang masih kosong, ditambah satu tag `<script type="module" src="/src/main.jsx">` yang memanggil script React. Tidak ada tampilan UI sama sekali di tahap ini — `index.html` hanyalah wadah kosong.

**Tahap 2 — `src/main.jsx` (Bridge Script)**
Script ini bertindak sebagai jembatan (bridge) antara `index.html` dan React. `main.jsx` mengambil elemen `#root` dari `index.html` menggunakan `document.getElementById('root')`, lalu memanggil `ReactDOM.createRoot(...).render(<App />)` untuk menyuntikkan komponen `<App />` ke dalam wadah kosong tersebut.

**Tahap 3 — `src/App.jsx` (Root Component)**
Setelah disuntikkan oleh `main.jsx`, `App.jsx` mengambil alih. Di sinilah seluruh logika berada:
- **State** (`useState`) menyimpan data hidup seperti nilai `projectSelesai`.
- **Event handler** (`handleTambahProject`) menangani klik tombol "Tambah Project".
- **Return JSX** merender tampilan UI (Navbar, Hero Profile, Stat Card, Project Showcase, Footer) menggunakan HTML5 semantik + Tailwind CSS.

Ketika tombol "Tambah Project" diklik, `setProjectSelesai` mengubah nilai state, React mendeteksi perubahan tersebut, lalu secara otomatis me-render ulang (*re-render*) bagian `<p>{projectSelesai}</p>` di layar — inilah yang membuat angka pada Stat Card bertambah tanpa perlu me-refresh halaman secara manual.

**Ringkasan alur:**
```
index.html (wadah kosong #root)
     ↓ memanggil
src/main.jsx (bridge, render <App /> ke #root)
     ↓ menyuntikkan
src/App.jsx (logika State + tampilan JSX yang muncul di browser)
```

---

## 4. Bedah & HTML5 Semantik pada `App.jsx`

Meskipun kode ini dihasilkan dengan bantuan AI, struktur `return JSX` tetap disusun menggunakan tag HTML5 bermakna, bukan sekadar tumpukan `<div>` ("Div Soup"). Berikut alasan pemilihan tiap tag semantik:

| Tag | Digunakan untuk | Alasan Pemilihan |
|---|---|---|
| `<header>` | Bagian atas berisi identitas (Nama, NIM) dan `<nav>` | Menandai secara eksplisit bahwa bagian ini adalah kepala halaman, bukan sekadar konten biasa — memudahkan screen reader melompat langsung ke navigasi. |
| `<nav>` | Daftar link Home, Profile, Projects | Memberi tahu browser dan teknologi assistive bahwa elemen ini adalah kumpulan navigasi, bukan daftar teks biasa. |
| `<main>` | Pembungkus seluruh konten inti (Hero, Counter, Projects) | Hanya boleh ada satu `<main>` per halaman; menandai konten utama yang membedakannya dari header/footer/navigasi. |
| `<section>` | Hero Profile dan Project Showcase | Mengelompokkan konten yang punya tema/topik sendiri (profil vs daftar proyek), masing-masing diberi `aria-labelledby` agar terbaca jelas oleh screen reader. |
| `<article>` | Setiap card project | Setiap card berisi konten yang berdiri sendiri dan bisa dipahami terlepas dari konteks di sekitarnya — cocok dengan definisi `<article>`. |
| `<footer>` | Bagian penutup halaman | Menandai informasi penutup (identitas & program studi) secara semantik, terpisah dari `<main>`. |
| `<h1>` – `<h3>` | Judul sapaan, judul section, judul card | Menjaga hierarki heading yang benar (satu `<h1>` per halaman) sehingga struktur dokumen tetap logis untuk SEO dan navigasi screen reader. |

**Manfaat penggunaan tag semantik ini:**
1. **SEO** — mesin pencari seperti Google lebih mudah memahami struktur dan kepentingan tiap bagian halaman.
2. **Accessibility (a11y)** — pengguna screen reader dapat melompat antar bagian (navigasi, konten utama, footer) tanpa harus membaca seluruh halaman secara linear.
3. **Keterbacaan kode** — developer lain (atau dosen penguji saat *code defense*) dapat langsung memahami struktur halaman hanya dari nama tag, tanpa perlu membaca seluruh `className`.

---

## Lampiran: Fitur Web yang Diimplementasikan

- Header & Navbar semantik (Nama, NIM, Bidang Minat)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/1a58f5dda1798982afde9e8f4607b5dd216fe6fa/Student%20Hub%20Preview.png)
- ✅ Hero Profile (Bio + Target Profil Lulusan PL-01)
- ✅ Interactive Counter dengan `useState` (Stat Card "Project Selesai")
- ✅ Showcase 3 Card Project (Balinese Culture Digital Archive, Smart Waste Management, AI Academic Assistant)
- ✅ Single-File Component — seluruh kode berada di `src/App.jsx`
