# Lab 5 - Kalkulator Nilai Mahasiswa

Aplikasi web sederhana interaktif berbasis JavaScript untuk menghitung nilai akhir mahasiswa berdasarkan komponen nilai Tugas, UTS, dan UAS. Aplikasi ini secara otomatis menentukan predikat nilai ($A, B, C, D, E$) serta status kelulusan mahasiswa berdasarkan standar kriteria penilai.

---

## 📁 Struktur Proyek

```text
Lab5_javascript/
├── .vscode/
│   └── settings.json
├── index.html
├── script.js
└── README.md
```

- **`index.html`**: Halaman utama yang memuat formulir input, tata letak antarmuka (CSS), dan elemen penampung hasil perhitungan.
- **`script.js`**: Berkas logika JavaScript yang menangani pengolahan event form, fungsi perhitungan, validasi rentang input, dan penentuan predikat/status.
- **`.vscode/settings.json`**: Konfigurasi lingkungan pengembangan editor VS Code.

---

## ✨ Fitur Utama

1. **Input Interaktif**: Formulir pengisian angka untuk **Nilai Tugas** (bobot 30%), **Nilai UTS** (bobot 30%), dan **Nilai UAS** (bobot 40%).
2. **Validasi Input**: Memastikan input berada dalam rentang valid $0$ hingga $100$. Jika input di luar batas atau tidak valid, pesan kesalahan (*error message*) akan ditampilkan.
3. **Pemisahan Modular Logika**:
   - Fungsi terpisah untuk kalkulasi nilai akhir (`hitungNilaiAkhir`).
   - Fungsi terpisah untuk evaluasi grade/predikat (`tentukanPredikat`).
4. **Tampilan Hasil Dinamis**: Menampilkan Nilai Akhir (dibulatkan 2 desimal), Predikat, dan Status Kelulusan secara langsung pada halaman HTML tanpa perlu berpindah halaman atau hanya melihat melalui *Console*.

---

## 🧮 Rumus Perhitungan & Aturan Evaluasi

### 1. Nilai Akhir
$$\text{Nilai Akhir} = (\text{Tugas} \times 0.30) + (\text{UTS} \times 0.30) + (\text{UAS} \times 0.40)$$

### 2. Aturan Predikat
| Rentang Nilai Akhir | Predikat |
| :--- | :---: |
| $\text{Nilai} \ge 85$ | **A** |
| $75 \le \text{Nilai} < 85$ | **B** |
| $60 \le \text{Nilai} < 75$ | **C** |
| $50 \le \text{Nilai} < 60$ | **D** |
| $\text{Nilai} < 50$ | **E** |

### 3. Status Kelulusan
- **Lulus**: Nilai Akhir $\ge 60$
- **Belum Lulus**: Nilai Akhir $< 60$

---

## 💻 Struktur Kode & Penjelasan

### 1. Struktur HTML (`index.html`)
Elemen utama terdiri dari form `<form id="gradeForm">` yang memuat input angka untuk ketiga komponen nilai, tombol submit, serta kontainer `<div id="resultBox">` untuk menampilkan output hasil perhitungan.

### 2. Logika JavaScript (`script.js`)

```javascript
// Fungsi memisahkan proses perhitungan nilai akhir
function hitungNilaiAkhir(tugas, uts, uas) {
    return (tugas * 0.30) + (uts * 0.30) + (uas * 0.40);
}

// Fungsi memisahkan penentuan predikat berdasarkan nilai
function tentukanPredikat(nilai) {
    if (nilai >= 85) return "A";
    if (nilai >= 75) return "B";
    if (nilai >= 60) return "C";
    if (nilai >= 50) return "D";
    return "E";
}
```

- **Validasi Data**:
  ```javascript
  if (tugas < 0 || tugas > 100 || uts < 0 || uts > 100 || uas < 0 || uas > 100) {
      // Menampilkan peringatan pesan error jika input di luar rentang 0 - 100
  }
  ```

---

## 🧪 Skenario Pengujian (Test Cases)

Berikut adalah 3 skenario pengujian nilai yang direkomendasikan untuk memastikan fungsi berjalan secara benar:

| Skenario | Nilai Tugas | Nilai UTS | Nilai UAS | Nilai Akhir | Predikat | Status Kelulusan |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Skenario 1 (Tinggi)** | 85 | 78 | 88 | **83.90** | **B** | **Lulus** |
| **Skenario 2 (Sedang)** | 60 | 65 | 70 | **65.50** | **C** | **Lulus** |
| **Skenario 3 (Rendah)** | 40 | 45 | 50 | **45.50** | **E** | **Belum lulus** |

---

## 🚀 Cara Menjalankan Aplikasi

1. **Melalui File System**:
   - Buka folder `Lab5_javascript`.
   - Klik dua kali pada file `index.html` untuk membuanya langsung di peramban web (Chrome, Firefox, Edge, dll).
2. **Melalui Visual Studio Code**:
   - Buka folder `Lab5_javascript` di VS Code.
   - Gunakan ekstensi **Live Server** (jika terpasang), lalu klik kanan pada file `index.html` dan pilih **Open with Live Server**.