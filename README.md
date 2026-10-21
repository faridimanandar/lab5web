# Lab5Web — Praktikum 5: JavaScript Dasar dan Manipulasi HTML

**Mata Kuliah:** Pemrograman Web
**Pertemuan:** 6
**Program Studi:** Teknik Informatika

| | |
|---|---|
| **Nama** | _(isi nama Anda)_ |
| **NIM** | _(isi NIM Anda)_ |
| **Kelas** | _(isi kelas Anda)_ |

---

## Daftar Isi

1. [Tujuan Praktikum](#tujuan-praktikum)
2. [Struktur Folder](#struktur-folder)
3. [Persiapan dan Cara Menjalankan](#persiapan-dan-cara-menjalankan)
4. [Langkah Kerja dan Hasil Latihan](#langkah-kerja-dan-hasil-latihan)
5. [Mini Project — Kalkulator Nilai Mahasiswa](#mini-project--kalkulator-nilai-mahasiswa)
6. [Eksperimen Mandiri](#eksperimen-mandiri)
7. [Jawaban Pertanyaan](#jawaban-pertanyaan)
8. [Kesimpulan](#kesimpulan)
9. [Referensi](#referensi)

---

## Tujuan Praktikum

1. Memahami sintaks dasar JavaScript dan cara menyisipkan JavaScript pada HTML.
2. Menggunakan variabel, tipe data, operator, percabangan, perulangan, dan function.
3. Menampilkan informasi melalui `console`, `alert`, `prompt`, dan elemen HTML.
4. Memanipulasi konten serta gaya elemen HTML menggunakan JavaScript.
5. Membuat interaksi sederhana pada form dan melakukan validasi input.
6. Mendokumentasikan pekerjaan praktikum beserta hasil pengujiannya.

---

```

> Catatan: karena seluruh latihan memakai satu `index.html` dan satu `script.js`, kerjakan dan uji latihan secara berurutan. Beri komentar (`//`) pada kode latihan sebelumnya jika dialog `prompt` mengganggu pengujian latihan berikutnya.

---

## Persiapan dan Cara Menjalankan

### Persiapan

1. Buat folder kerja `lab5_javascript` (atau clone repository `Lab5Web`).
2. Buat file `index.html` dan `script.js` di dalam folder tersebut.
3. Salin kerangka HTML berikut ke `index.html`:

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Praktikum JavaScript</title>
</head>
<body>
  <h1>Pengenalan JavaScript</h1>
  <p id="pesan">Konten awal.</p>

  <!-- Tambahkan elemen untuk Latihan 6, 7, dan 8 di sini -->

  <script src="script.js"></script>
</body>
</html>
```

### Cara Menjalankan

1. Buka folder proyek di **Visual Studio Code**.
2. Buka `index.html` dengan browser modern (Chrome, Firefox, atau Edge), atau gunakan ekstensi **Live Server**.
3. Buka **Inspect/Periksa → Console** untuk melihat output `console.log`.
4. Ikuti setiap latihan secara berurutan dan simpan screenshot hasilnya ke folder `screenshots/`.

---

## Langkah Kerja dan Hasil Latihan

### Latihan 1 — Menampilkan Output

**Tujuan:** mengenali cara menampilkan output di halaman dan Console.

**Kode (`script.js`):**

```javascript
document.getElementById("pesan").textContent = "Hello World";
console.log("Hello World");
```

**Langkah:**
1. Jalankan halaman di browser.
2. Pastikan teks pada halaman berubah menjadi "Hello World".
3. Pastikan pesan "Hello World" tampil di Console.

**Hasil:**

![Latihan 1](screenshots/latihan1.png)

**Pengamatan:** `textContent` mengubah tampilan di dalam halaman (terlihat oleh pengguna), sedangkan `console.log` hanya tampil di Console browser (terlihat oleh developer).

---

### Latihan 2 — Alert dan Prompt

**Kode (`script.js`):**

```javascript
const namaPengguna = prompt("Masukkan nama Anda:", "");

if (namaPengguna && namaPengguna.trim() !== "") {
  alert("Halo, " + namaPengguna + "!");
  document.getElementById("pesan").textContent = "Selamat datang, " + namaPengguna + ".";
} else {
  alert("Nama belum diisi.");
}
```

**Hasil pengujian:**

| Skenario | Perilaku Program |
|---|---|
| Memasukkan nama (mis. "Rani") | Muncul alert "Halo, Rani!" dan teks halaman menjadi "Selamat datang, Rani." |
| Menekan **Cancel** | `prompt` mengembalikan `null` → muncul alert "Nama belum diisi." |
| Input dikosongkan lalu **OK** | String kosong dianggap tidak valid → muncul alert "Nama belum diisi." |

![Latihan 2](screenshots/latihan2.png)

---

### Latihan 3 — Function dan Operasi Aritmetika

**Kode (`script.js`):**

```javascript
function operasiDasar(a, b) {
  console.log("Penjumlahan:", a + b);
  console.log("Pengurangan:", a - b);
  console.log("Perkalian:", a * b);
  console.log("Pembagian:", b !== 0 ? a / b : "Tidak dapat dibagi nol");
  console.log("Modulus:", a % b);
}

operasiDasar(9, 4);
```

**Hasil di Console untuk `operasiDasar(9, 4)`:**

```
Penjumlahan: 13
Pengurangan: 5
Perkalian: 36
Pembagian: 2.25
Modulus: 1
```

![Latihan 3](screenshots/latihan3.png)

**Pengamatan:** pembagian sudah dilindungi dari pembagi nol, tetapi `a % 0` menghasilkan `NaN`. Jika diperlukan, baris modulus dapat diberi pengecekan `b !== 0` yang sama.

---

### Latihan 4 — Seleksi Kondisi if–else

**Kode (`script.js`):**

```javascript
const inputNilai = prompt("Masukkan nilai (0–100):");
const nilaiMahasiswa = Number(inputNilai);

if (inputNilai === null || inputNilai.trim() === "" ||
    Number.isNaN(nilaiMahasiswa) || nilaiMahasiswa < 0 || nilaiMahasiswa > 100) {
  alert("Input nilai tidak valid.");
} else if (nilaiMahasiswa >= 60) {
  alert("Lulus");
} else {
  alert("Belum lulus");
}
```

**Hasil pengujian:**

| Input | Hasil |
|---|---|
| `76` | Lulus |
| `60` | Lulus |
| `45` | Belum lulus |
| `150` | Input nilai tidak valid |
| `abc` | Input nilai tidak valid |
| _(kosong)_ / Cancel | Input nilai tidak valid |

![Latihan 4](screenshots/latihan4.png)

**Pengamatan:** `prompt` selalu mengembalikan string, sehingga input harus dikonversi dengan `Number()` sebelum dibandingkan.

---

### Latihan 5 — Seleksi Kondisi switch

**Kode (`script.js`):**

```javascript
const inputPilihan = prompt("Masukkan angka 1–5:");

switch (inputPilihan) {
  case "1": alert("Bilangan satu"); break;
  case "2": alert("Bilangan dua"); break;
  case "3": alert("Bilangan tiga"); break;
  case "4": alert("Bilangan empat"); break;
  case "5": alert("Bilangan lima"); break;
  default: alert("Pilihan tidak tersedia");
}
```

**Hasil pengujian:**

| Input | Hasil |
|---|---|
| `1` – `5` | Menampilkan nama bilangan sesuai angka (satu sampai lima) |
| `9`, `abc`, kosong | "Pilihan tidak tersedia" |

![Latihan 5](screenshots/latihan5.png)

---

### Latihan 6 — Form Bilangan Genap atau Ganjil

**HTML (`index.html`):**

```html
<label for="bilangan">Masukkan bilangan bulat:</label>
<input type="number" id="bilangan" step="1">
<button type="button" onclick="cekBilangan()">Periksa</button>
<p id="hasilBilangan"></p>
```

**JavaScript (`script.js`):**

```javascript
function cekBilangan() {
  const input = document.getElementById("bilangan").value;
  const angka = Number(input);
  const hasil = document.getElementById("hasilBilangan");

  if (input.trim() === "" || !Number.isInteger(angka)) {
    hasil.textContent = "Masukkan bilangan bulat yang valid.";
  } else if (angka % 2 === 0) {
    hasil.textContent = "Bilangan genap";
  } else {
    hasil.textContent = "Bilangan ganjil";
  }
}
```

**Hasil pengujian:**

| Input | Hasil |
|---|---|
| `8` (positif genap) | Bilangan genap |
| `7` (positif ganjil) | Bilangan ganjil |
| `-4` (negatif) | Bilangan genap |
| `-3` (negatif) | Bilangan ganjil |
| `0` | Bilangan genap |
| `3.5` (desimal) | Masukkan bilangan bulat yang valid. |
| _(kosong)_ | Masukkan bilangan bulat yang valid. |

![Latihan 6](screenshots/latihan6.png)

---

### Latihan 7 — Mengubah Warna Halaman

**HTML (`index.html`):**

```html
<button type="button" onclick="ubahWarnaLatar('lightgreen')">Latar Hijau</button>
<button type="button" onclick="ubahWarnaLatar('white')">Latar Putih</button>
<button type="button" onclick="ubahWarnaLatar('lightyellow')">Latar Kuning</button>
```

**JavaScript (`script.js`):**

```javascript
function ubahWarnaLatar(warna) {
  document.body.style.backgroundColor = warna;
}
```

**Hasil:** setiap tombol mengubah warna latar halaman sesuai nilai parameter yang dikirim. Satu function dengan parameter digunakan untuk ketiga tombol sehingga kode tidak berulang.

![Latihan 7](screenshots/latihan7.png)

---

### Latihan 8 — DOM dan Checkbox Menu Makanan

**HTML (`index.html`):**

```html
<h3>Daftar Menu Makanan</h3>
<label><input type="checkbox" class="menu" value="5000"> Ayam Goreng — Rp5.000</label><br>
<label><input type="checkbox" class="menu" value="500"> Tempe — Rp500</label><br>
<label><input type="checkbox" class="menu" value="2500"> Telur Dadar — Rp2.500</label><br>
<p>Total: Rp<span id="total">0</span></p>
```

**JavaScript (`script.js`):**

```javascript
const daftarMenu = document.querySelectorAll(".menu");

daftarMenu.forEach((item) => {
  item.addEventListener("change", hitungTotal);
});

function hitungTotal() {
  let total = 0;
  daftarMenu.forEach((item) => {
    if (item.checked) total += Number(item.value);
  });
  document.getElementById("total").textContent = total.toLocaleString("id-ID");
}
```

**Hasil pengujian:**

| Menu yang dicentang | Total |
|---|---|
| Tidak ada | Rp0 |
| Ayam Goreng | Rp5.000 |
| Ayam Goreng + Tempe | Rp5.500 |
| Semua menu | Rp8.000 |
| Semua dicentang, lalu Tempe dilepas | Rp7.500 |

![Latihan 8](screenshots/latihan8.png)

**Catatan:** `<script src="script.js"></script>` diletakkan di akhir `<body>` agar seluruh elemen HTML sudah tersedia saat script dijalankan.

---

## Mini Project — Kalkulator Nilai Mahasiswa

**Deskripsi:** program menerima nilai tugas, UTS, dan UAS, menghitung nilai akhir, menentukan predikat, serta menampilkan status kelulusan pada halaman HTML.

**Rumus nilai akhir:** `Tugas × 30% + UTS × 30% + UAS × 40%`

**Ketentuan predikat:**

| Nilai Akhir | Predikat |
|---|---|
| ≥ 85 | A |
| ≥ 75 | B |
| ≥ 60 | C |
| ≥ 50 | D |
| < 50 | E |

Status **Lulus** jika nilai akhir ≥ 60, selain itu **Belum lulus**.

**HTML (`index.html`):**

```html
<h2>Kalkulator Nilai Mahasiswa</h2>

<label for="tugas">Nilai Tugas:</label>
<input type="number" id="tugas" min="0" max="100"><br>

<label for="uts">Nilai UTS:</label>
<input type="number" id="uts" min="0" max="100"><br>

<label for="uas">Nilai UAS:</label>
<input type="number" id="uas" min="0" max="100"><br>

<button type="button" onclick="prosesNilai()">Hitung</button>

<div id="hasilNilai"></div>
```

**JavaScript (`script.js`):**

```javascript
// --- Fungsi perhitungan (logika) ---
function hitungNilaiAkhir(tugas, uts, uas) {
  return tugas * 0.30 + uts * 0.30 + uas * 0.40;
}

function tentukanPredikat(nilai) {
  if (nilai >= 85) return "A";
  if (nilai >= 75) return "B";
  if (nilai >= 60) return "C";
  if (nilai >= 50) return "D";
  return "E";
}

// --- Fungsi validasi ---
function nilaiValid(teks) {
  const angka = Number(teks);
  return teks.trim() !== "" && !Number.isNaN(angka) && angka >= 0 && angka <= 100;
}

// --- Fungsi tampilan (hasil ke halaman) ---
function prosesNilai() {
  const tugasInput = document.getElementById("tugas").value;
  const utsInput = document.getElementById("uts").value;
  const uasInput = document.getElementById("uas").value;
  const hasil = document.getElementById("hasilNilai");

  if (!nilaiValid(tugasInput) || !nilaiValid(utsInput) || !nilaiValid(uasInput)) {
    hasil.textContent = "Semua nilai harus diisi dengan angka 0–100.";
    return;
  }

  const akhir = hitungNilaiAkhir(Number(tugasInput), Number(utsInput), Number(uasInput));
  const predikat = tentukanPredikat(akhir);
  const status = akhir >= 60 ? "Lulus" : "Belum lulus";

  hasil.innerHTML =
    "Nilai akhir: <strong>" + akhir.toFixed(2) + "</strong><br>" +
    "Predikat: <strong>" + predikat + "</strong><br>" +
    "Status: <strong>" + status + "</strong>";
}
```

**Skenario pengujian:**

| Skenario | Tugas | UTS | UAS | Nilai Akhir | Predikat | Status |
|---|---|---|---|---|---|---|
| 1 | 85 | 78 | 88 | 84.10 | B | Lulus |
| 2 | 90 | 95 | 92 | 92.30 | A | Lulus |
| 3 | 40 | 35 | 45 | 40.50 | E | Belum lulus |
| 4 | 110 | 80 | 80 | — | — | Ditolak (di luar rentang 0–100) |
| 5 | _(kosong)_ | 80 | 80 | — | — | Ditolak (kolom kosong) |

![Mini Project](screenshots/miniproject.png)

---

## Eksperimen Mandiri

Kode eksperimen dapat ditambahkan ke `script.js` atau file terpisah.

**1. Latihan 3 dengan input `prompt` (dikonversi ke number):**

```javascript
const x = Number(prompt("Masukkan bilangan pertama:"));
const y = Number(prompt("Masukkan bilangan kedua:"));
operasiDasar(x, y);
```

**2. Tabel perkalian angka 7 (1–10):**

```javascript
for (let i = 1; i <= 10; i++) {
  console.log("7 x " + i + " = " + (7 * i));
}
```

**3. Function `cekGenap(angka)`:**

```javascript
function cekGenap(angka) {
  return angka % 2 === 0;
}
console.log(cekGenap(10)); // true
console.log(cekGenap(7));  // false
```

**4. Validasi form agar kolom tidak boleh kosong:**

```javascript
function validasiKolom(idInput, idPesan) {
  const nilai = document.getElementById(idInput).value.trim();
  const pesan = document.getElementById(idPesan);
  if (nilai === "") {
    pesan.textContent = "Kolom tidak boleh kosong.";
    return false;
  }
  pesan.textContent = "";
  return true;
}
```

**5. Latihan 8 dengan tambahan menu** — contoh menambah dua pilihan pada HTML:

```html
<label><input type="checkbox" class="menu" value="3000"> Nasi Putih — Rp3.000</label><br>
<label><input type="checkbox" class="menu" value="2000"> Es Teh — Rp2.000</label><br>
```

**6. Tombol sembunyikan/tampilkan elemen:**

```html
<button type="button" onclick="toggleElemen()">Sembunyikan / Tampilkan</button>
```

```javascript
function toggleElemen() {
  const elemen = document.getElementById("pesan");
  elemen.style.display = (elemen.style.display === "none") ? "block" : "none";
}
```

---

## Jawaban Pertanyaan

**1. Perbedaan `console.log()`, `alert()`, `prompt()`, dan `textContent`/`innerHTML`.**

- `console.log()` menulis pesan ke Console browser; dipakai developer untuk debugging dan tidak terlihat di halaman.
- `alert()` menampilkan kotak dialog berisi pesan dan menghentikan eksekusi sampai pengguna menekan OK.
- `prompt()` menampilkan kotak dialog untuk meminta masukan; hasilnya berupa string, atau `null` jika dibatalkan.
- `textContent` mengubah isi teks elemen HTML secara aman (tanpa menafsirkan tag), sedangkan `innerHTML` mengubah isi elemen dan menafsirkan teks sebagai HTML.

**2. Perbedaan `let` dan `const`.**

`let` untuk variabel yang nilainya dapat ditetapkan ulang, sedangkan `const` untuk variabel yang tidak boleh ditetapkan ulang.

```javascript
let umur = 20;
umur = 21;        // boleh

const nama = "Rani";
nama = "Dina";    // error: Assignment to constant variable
```

**3. Perbedaan `==` dan `===`.**

`==` membandingkan nilai setelah melakukan konversi tipe otomatis, sedangkan `===` membandingkan nilai **dan** tipe tanpa konversi. Disarankan memakai `===`.

```javascript
console.log(5 == "5");   // true
console.log(5 === "5");  // false
```

**4. Fungsi `if–else` dan `switch`.**

`if–else` dipakai untuk menguji kondisi logis, terutama rentang nilai atau kondisi majemuk (mis. `nilai >= 60`). `switch` dipakai untuk memilih satu tindakan dari sejumlah nilai tertentu yang pasti (mis. pilihan menu "1" sampai "5"). `break` pada `switch` mencegah eksekusi berlanjut ke `case` berikutnya.

**5. Fungsi parameter dan `return` dalam function.**

Parameter menerima data masukan sehingga function dapat dipakai ulang dengan nilai berbeda. `return` mengembalikan hasil proses ke pemanggil function agar dapat disimpan atau diproses lebih lanjut.

**6. Cara `document.getElementById()` memilih elemen HTML.**

Method ini mencari elemen di dokumen berdasarkan nilai atribut `id` dan mengembalikan objek elemen tersebut (atau `null` jika tidak ditemukan). Objek itu kemudian dapat diubah isi, atribut, atau gayanya.

```javascript
const elemen = document.getElementById("pesan");
elemen.textContent = "Halo, JavaScript!";
```

**7. Script validasi form: nama tidak kosong dan nilai 0–100.**

```html
<label for="nama">Nama:</label>
<input type="text" id="nama"><br>

<label for="nilai">Nilai (0–100):</label>
<input type="number" id="nilai"><br>

<button type="button" onclick="validasiForm()">Kirim</button>
<p id="pesanValidasi"></p>
```

```javascript
function validasiForm() {
  const nama = document.getElementById("nama").value.trim();
  const nilaiTeks = document.getElementById("nilai").value;
  const nilai = Number(nilaiTeks);
  const pesan = document.getElementById("pesanValidasi");

  if (nama === "") {
    pesan.textContent = "Nama tidak boleh kosong.";
  } else if (nilaiTeks.trim() === "" || Number.isNaN(nilai) || nilai < 0 || nilai > 100) {
    pesan.textContent = "Nilai harus berupa angka 0–100.";
  } else {
    pesan.textContent = "Data valid. Nama: " + nama + ", Nilai: " + nilai;
  }
}
```

---

## Kesimpulan

Melalui praktikum ini, dipelajari cara menyisipkan JavaScript eksternal ke HTML, menggunakan variabel, tipe data, operator, percabangan, perulangan, dan function, serta menampilkan output melalui Console, dialog, dan elemen HTML. Selain itu, DOM digunakan untuk mengubah konten dan gaya elemen, membuat interaksi pada form dan checkbox, serta melakukan validasi input sebelum diproses.

---

## Referensi

1. Flanagan, D. (2020). _JavaScript: The Definitive Guide_ (7th ed.). O'Reilly Media.
2. MDN Web Docs. _JavaScript Guide_. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
3. Modul Praktikum Pemrograman Web — Praktikum 5: JavaScript Dasar dan Manipulasi HTML.
