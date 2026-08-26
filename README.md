# Laporan Take-Home Assignment — Student Hub & Code Defense

**Nama :** Ida Ayu Putu Audrey Tara Cahyarani
**NIM :** 2505551128
**Program Studi :** Teknologi Informasi, Fakultas Teknik, Universitas Udayana
**Bidang Minat (Kurikulum 2026) :** Artificial Intelligence

---

## 1. Langkah-Langkah

Berikut urutan perintah terminal dari awal setup proyek hingga menjalankan `npm run dev`:

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
![image alt](https://github.com/sweetdoodles/prognet-c/blob/1b063debb1c4a4e755834dd2afa329d391a06e3d/Screenshot%202026-08-26%20191027.png)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/3d4c6f71ddab7b4acc667aaac52cc17976f90035/Screenshot%202026-08-26%20191154.png)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/63a6ed3e9a8bba6f4e9104a0d9f33169ccf2f499/Screenshot%202026-08-26%20191159.png)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/03bbf8b3f409f891003a51a08104b465fce8a7c7/Screenshot%202026-08-26%20193431.png)

Setelah `npm run dev` dijalankan, aplikasi dapat diakses di `http://localhost:5173`. Seluruh tampilan Student Hub ditulis dalam satu file `src/App.jsx` (Single-File Component), tanpa membuat file atau folder tambahan di luar file tersebut.

---

## 2. AI Prompt Log

Berikut prompt persis yang digunakan untuk men-generate komponen `src/App.jsx` melalui AI coding assistant (Copilot):

```
Buatkan sebuah Web Student Hub Personal Mahasiswa Teknologi Informasi Universitas Udayana menggunakan **React + Tailwind CSS**.
1. Ketentuan Utama
Seluruh kode website WAJIB berada dalam satu file `src/App.jsx` saja.
JANGAN membuat file atau folder tambahan, termasuk:
  * `Navbar.jsx`
  * `Hero.jsx`
  * `ProjectCard.jsx`
  * `Footer.jsx`
  * file CSS tambahan
  * folder components
  * folder assets
* Gunakan React Functional Component.
* Gunakan React Hooks, terutama `useState`, dan `useEffect` jika memang diperlukan.
* Jangan menggunakan backend atau database eksternal.
* Semua data project, skill, profil, dan target dapat dibuat sebagai data statis di dalam `App.jsx`.
* Gunakan Tailwind CSS untuk styling.
* Jika membutuhkan icon, gunakan icon library yang sudah tersedia pada project. Jika tidak tersedia, gunakan emoji atau inline SVG sederhana. **Jangan membuat file icon tambahan.**
* Pastikan kode dapat langsung dijalankan pada project React yang sudah memiliki Tailwind CSS.
* Jangan memberikan pseudo-code. Berikan **kode lengkap dan runnable**.

2. Tujuan Website
Website ini merupakan **personal dashboard mahasiswa TI** yang berfungsi sebagai Student Hub untuk menampilkan:
* Identitas mahasiswa
* Profil dan bio
* Bidang minat
* Target profil lulusan
* Statistik project
* Project impian selama kuliah
* Skill
* Goals
* Project favorit
Website harus terlihat seperti **personal portfolio/dashboard mahasiswa modern**, bukan seperti website administrasi kampus.

3. Identitas Mahasiswa
Gunakan data dummy yang mudah diganti, misalnya:
* Nama: `Ida Ayu Putu Audrey Tara Cahyarani`
* NIM: `2505551128`
* Program Studi: `Teknologi Informasi`
* Universitas: `Universitas Udayana`
* Bidang Minat: salah satu dari 4 Bidang Minat Kurikulum 2026
Buat bagian identitas tersebut menggunakan variabel/data sehingga mudah diubah tanpa harus mencari banyak bagian kode.
Jika informasi 4 Bidang Minat Kurikulum 2026 tidak tersedia secara pasti, buat array placeholder yang jelas dan mudah diganti:
const bidangMinat = [
  "Bidang Minat 1",
  "Bidang Minat 2",
  "Bidang Minat 3",
  "Bidang Minat 4"
];
Jangan mengarang nama resmi bidang minat jika tidak diberikan.

4. Struktur HTML Semantic
Gunakan HTML5 Semantic Tags secara nyata, bukan hanya sebagai dekorasi.
Pastikan setiap section memiliki `id` yang sesuai agar dapat digunakan untuk navigasi.

5. Header & Navbar
Buat navbar modern dan responsive.
Navbar minimal berisi:
* Logo/inisial mahasiswa
* Nama mahasiswa
* NIM
* Program Studi
* Bidang Minat
* Menu:
  * Home
  * Profile
  * Projects
  * Skills
  * Goals
* Tombol Dark/Light Mode

Ketentuan navbar:
* Navbar dapat diklik.
* Klik menu harus melakukan smooth scrolling menuju section terkait.
* Gunakan `scroll-behavior: smooth` atau mekanisme yang sesuai.
* Pada mobile, ubah navbar menjadi menu hamburger.
* Hamburger menu harus benar-benar berfungsi menggunakan `useState`.
* Navbar memiliki efek hover dan transition.
* Navbar tetap mudah digunakan pada layar kecil.

6. Hero Section
Buat Hero Section yang menjadi bagian utama halaman Home.
Tampilkan:
* Greeting seperti:
  `Hello, I'm`
* Nama mahasiswa
* Program studi
* Bio singkat
* Bidang minat
* Target Profil Lulusan
* Avatar/foto placeholder
* CTA button:
  * `View My Projects`
  * `Explore Profile`
Tambahkan visual seperti:
* gradient background
* decorative blur/blob sederhana
* card modern
* subtle animation
Namun jangan membuat desain terlalu ramai.
Avatar dapat menggunakan placeholder berbentuk lingkaran jika tidak tersedia foto asli.

7. Target Profil Lulusan Interaktif
Buat pilihan Target Profil Lulusan menggunakan `useState`.
Pilihan:
* `PL-01 — Pengembang Sistem TI`
* `PL-02 — Entrepreneur Digital`
* `PL-03 — Akademisi/Peneliti`
Tampilkan dalam bentuk button/card.
Ketika mahasiswa memilih salah satu:
* pilihan aktif berubah secara visual
* deskripsi target berubah
* Stat Card Target Profil Lulusan ikut berubah

8. Dark Mode & Light Mode
Implementasikan Dark Mode menggunakan React `useState`.
Ketentuan:
* Terdapat tombol toggle.
* Klik toggle mengubah seluruh tampilan website.
* Light mode dan dark mode harus memiliki kontras yang baik.
* Text tetap mudah dibaca.
* Card, background, border, navbar, button, dan section ikut berubah.
* Gunakan Tailwind dark classes jika konfigurasi project mendukungnya.
* Jika perlu, implementasikan class `dark` pada root element menggunakan `useEffect`.
Tambahkan icon atau indikator:
* ☀️ Light Mode
* 🌙 Dark Mode
Pastikan toggle benar-benar bekerja, bukan hanya mengubah icon.

9. Interactive Project Counter
Buat Stat Card:
**Project Selesai**
Gunakan:
``js
useState()
``
untuk menyimpan jumlah project.
Sediakan tombol:
* `+ Tambah Project`
* `Reset`
Ketentuan:
* Tombol Tambah Project meningkatkan jumlah project sebanyak 1.
* Tombol Reset mengembalikan jumlah ke nilai awal.
* Nilai tidak boleh menjadi negatif.
* Perubahan angka harus langsung terlihat pada UI.
Tambahkan progress bar berdasarkan jumlah project.
Contoh:
Project Selesai
8
Progress Kuliah
80%
████████████████░░░░
Gunakan batas maksimum yang masuk akal, misalnya target `10 project`.
Progress harus dihitung secara dinamis berdasarkan state, bukan angka hard-code.

10. Stat Dashboard
Buat beberapa Stat Card modern:
1. `Project Selesai`
2. `Total Project`
3. `Project Favorit`
4. `Target Profil Lulusan`
Stat Card harus menggunakan data/state yang sebenarnya.
Khusus:
* Total Project = jumlah project pada data project.
* Project Favorit = jumlah project yang sedang difavoritkan.
* Target Profil = pilihan PL yang sedang aktif.

11. Showcase Projects
Buat section:
**My Dream Projects**
Berisi minimal **3 project impian selama kuliah**.
Setiap project memiliki:
``js
{
  id,
  title,
  category,
  description,
  technologies,
  status,
  fullDescription,
  goal,
  targetUser
}
``
Contoh kategori:
* Web Development
* Artificial Intelligence
* IoT
* Data
* Mobile Development
* Sustainability Technology
Gunakan project yang relevan dengan mahasiswa TI.
Setiap Project Card menampilkan:
* Nama project
* Category badge
* Deskripsi singkat
* Teknologi
* Status
* Favorite button
* `View Details`

12. Project Detail Interaktif
Ketika Project Card atau tombol `View Details` diklik:
Tampilkan detail project secara interaktif.
Boleh menggunakan:
* Modal
* Expandable card
* Detail panel
Detail minimal:
* Nama project
* Deskripsi lengkap
* Tujuan
* Teknologi
* Target pengguna
* Status project
Jika menggunakan modal:
* klik tombol Close menutup modal
* klik area luar modal boleh menutup modal
* tombol Escape boleh digunakan jika mudah diimplementasikan

13. Favorite Project
Setiap project harus memiliki tombol Favorite.
Gunakan `useState` untuk menyimpan project favorit.
Ketika tombol favorite diklik:
* project berubah menjadi favorit
* icon berubah
* tampilan visual berubah
* jumlah `Project Favorit` pada Stat Card ikut berubah

14. My Skills
Buat section:
**My Skills**
Skill minimal:
* React
* JavaScript
* HTML
* CSS / Tailwind CSS
* Database
* Networking
Tampilkan dalam bentuk:
* badge
* progress bar
* skill card

15. My Goals
Buat section:
**My Goals**
Berisi target mahasiswa selama kuliah, misalnya:
* Menyelesaikan berbagai project TI
* Mengikuti kompetisi
* Meningkatkan kemampuan programming
* Membuat project yang bermanfaat bagi masyarakat
* Mengembangkan kemampuan teamwork
* Membangun portfolio profesional
Tampilkan dalam bentuk card/checklist.
Tambahkan hover interaction pada setiap goal.

16. Design System
Gunakan desain yang:
* modern
* profesional
* clean
* minimalis
* student-friendly
* cocok untuk mahasiswa Teknologi Informasi
* tidak terlalu corporate
* tidak terlalu ramai
Gunakan:
* gradient
* rounded-xl / rounded-2xl
* shadow
* border
* backdrop blur jika sesuai
* spacing yang konsisten
* typography hierarchy
* badge
* icon
* subtle animation
Gunakan maksimal sekitar **2–3 warna utama** agar desain tidak berlebihan.
Pastikan warna dark mode berbeda secara tepat dari light mode.

17. Animation & Micro Interaction
Tambahkan animasi sederhana seperti:
* hover scale pada card
* hover shadow
* button transition
* fade-in sederhana
* icon transition
* progress bar transition
* favorite animation
* modal transition
* navbar transition
Gunakan animasi yang halus.
**Jangan menggunakan animasi berlebihan** yang mengganggu readability.

18. Responsive Design
Website wajib responsive pada:
* Desktop
* Laptop
* Tablet
* Mobile

Gunakan Tailwind responsive classes seperti:
```text
sm:
md:
lg:
xl:
``
Perhatikan:
* navbar mobile
* grid project
* stat cards
* hero layout
* typography
* padding
* modal
* button
* skill cards
Pada mobile, jangan sampai terjadi horizontal scrolling.

19. Output yang Saya Inginkan
Berikan hasil akhir berupa:
1. Penjelasan singkat mengenai konsep website.
2. **Kode lengkap `src/App.jsx`**.
3. Tidak membuat file tambahan.
4. Pastikan kode dapat langsung digunakan.
5. Jelaskan bagian-bagian penting kode secara singkat setelah kode agar mudah digunakan untuk **Code Defense**.
6. Sertakan penjelasan:
   * penggunaan `useState`
   * cara kerja Dark Mode
   * cara kerja Project Counter
   * cara kerja Favorite
   * cara kerja Target Profil Lulusan
   * cara kerja Project Detail
   * penggunaan `.map()`
   * penggunaan semantic HTML
   * responsive design Tailwind CSS

20. Acceptance Criteria
Anggap website **BELUM SELESAI** jika:
* hanya terlihat bagus tetapi tombol tidak berfungsi
* Dark Mode hanya berupa icon tanpa mengubah tema
* Favorite tidak mengubah state
* Counter tidak berubah
* Reset tidak berfungsi
* Project Detail tidak dapat dibuka
* Navbar tidak dapat berpindah section
* mobile menu tidak berfungsi
* progress bar tidak mengikuti jumlah project
* terdapat file tambahan di luar `src/App.jsx`
* terdapat error React
* terdapat undefined component/variable
* layout rusak pada mobile
Prioritaskan dalam urutan:
**1. Functionality → 2. Code correctness → 3. Responsive → 4. UI/UX → 5. Animation**
```

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

## Fitur Web yang Diimplementasikan

- Header & Navbar semantik (Nama, NIM, Bidang Minat)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/1a58f5dda1798982afde9e8f4607b5dd216fe6fa/Student%20Hub%20Preview.png)
- Hero Profile (Bio + Target Profil Lulusan)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/368c5a584a7e4ce3c7fd7de699c479514e4c5630/Hero%20Profile.png)
- Interactive Counter dengan `useState`
 ![image alt](https://github.com/sweetdoodles/prognet-c/blob/dca6f46eca6c20f88a1c87035468514f62c2b4d9/Interactive%20Counter.png)
- Showcase 3 Card Project (Balinese Culture Digital Archive, Smart Waste Management, AI Academic Assistant)
![image alt](https://github.com/sweetdoodles/prognet-c/blob/99ddca04735e72551696b3e1ff2f5213f8ae9078/Showcase%203%20Card%20Project.png)
- Single-File Component
![image alt]()
