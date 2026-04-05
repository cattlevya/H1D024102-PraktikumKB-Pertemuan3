# H1D024102-PraktikumKB-Pertemuan3

Pengumpulan tugas praktikum Kecerdasan Buatan pertemuan 3.

## Pengimplementasian Logika Fuzzy Menggunakan Library scikit-fuzzy

Program ini mengimplementasikan sistem inferensi fuzzy (Fuzzy Inference System) menggunakan metode Mamdani untuk dua studi kasus yang berbeda.

---

### 1. Studi Kasus 1 - Penentuan Stok Makanan (`main.py`)

Program ini menentukan jumlah stok makanan yang direkomendasikan berdasarkan 4 variabel input menggunakan logika fuzzy.

#### a. Variabel Input (Antecedent)
- **Barang Terjual** `[0 - 100]` → Himpunan: Rendah, Sedang, Tinggi (baris ke-16 sampai 18)
- **Permintaan** `[0 - 300]` → Himpunan: Rendah, Sedang, Tinggi (baris ke-21 sampai 23)
- **Harga per Item** `[0 - 100.000]` → Himpunan: Murah, Sedang, Mahal (baris ke-26 sampai 28)
- **Profit** `[0 - 4.000.000]` → Himpunan: Rendah, Sedang, Banyak (baris ke-31 sampai 33)

#### b. Variabel Output (Consequent)
- **Stok Makanan** `[0 - 1000]` → Himpunan: Sedang, Banyak (baris ke-36 sampai 37)

#### c. Aturan Fuzzy (Rules)
Terdapat 6 aturan fuzzy IF-THEN yang didefinisikan pada baris ke-40 sampai 45.

#### d. Nilai Input yang Diuji
- Barang Terjual = 80
- Permintaan = 255
- Harga per Item = Rp 25.000
- Profit = Rp 3.500.000

#### e. Membership Function
- Menggunakan fungsi segitiga (`trimf`) untuk sebagian besar himpunan fuzzy.
- Menggunakan fungsi trapesium (`trapmf`) pada himpunan Profit "Banyak" (baris ke-33).

---

### 2. Studi Kasus 2 - Kepuasan Pelayanan Masyarakat (`studi2.py`)

Program ini menentukan tingkat kepuasan pelayanan masyarakat berdasarkan 4 variabel input menggunakan logika fuzzy.

#### a. Variabel Input (Antecedent)
- **Kejelasan Informasi** `[0 - 100]` → Himpunan: Tidak, Cukup, Memuaskan (baris ke-16 sampai 18)
- **Kejelasan Persyaratan** `[0 - 100]` → Himpunan: Tidak, Cukup, Memuaskan (baris ke-21 sampai 23)
- **Kemampuan Petugas** `[0 - 100]` → Himpunan: Tidak, Cukup, Memuaskan (baris ke-26 sampai 28)
- **Ketersediaan Sarpas** `[0 - 100]` → Himpunan: Tidak, Cukup, Memuaskan (baris ke-31 sampai 33)

#### b. Variabel Output (Consequent)
- **Kepuasan Pelayanan** `[0 - 400]` → Himpunan: Tidak, Kurang, Cukup, Memuaskan, Sangat (baris ke-36 sampai 40)

#### c. Aturan Fuzzy (Rules)
Terdapat 81 aturan fuzzy IF-THEN yang mendefinisikan seluruh kombinasi dari 4 variabel input × 3 himpunan = 3⁴ = 81 aturan (baris ke-44 sampai 124).

#### d. Nilai Input yang Diuji
- Kejelasan Informasi = 80
- Kejelasan Persyaratan = 60
- Kemampuan Petugas = 50
- Ketersediaan Sarpas = 90

#### e. Membership Function
- Menggunakan fungsi trapesium (`trapmf`) untuk himpunan "Tidak" dan "Memuaskan" pada setiap variabel input.
- Menggunakan fungsi segitiga (`trimf`) untuk himpunan "Cukup" pada setiap variabel input.
- Menggunakan fungsi trapesium (`trapmf`) untuk seluruh himpunan output.

---

### 3. Library yang Digunakan

#### a. numpy
Digunakan untuk membuat array numerik sebagai semesta pembicaraan (universe of discourse) pada setiap variabel fuzzy.

#### b. matplotlib
Digunakan untuk menampilkan visualisasi grafik membership function dari setiap variabel fuzzy dan hasil defuzzifikasi.

#### c. scikit-fuzzy (skfuzzy)
Library utama yang digunakan untuk membangun sistem inferensi fuzzy, meliputi:
- Definisi variabel input (`Antecedent`) dan output (`Consequent`)
- Pembuatan membership function (`trimf`, `trapmf`)
- Pendefinisian aturan fuzzy (`Rule`)
- Pembangunan sistem kontrol (`ControlSystem`) dan simulasi (`ControlSystemSimulation`)
- Perhitungan output menggunakan metode defuzzifikasi

---

### 4. Cara Menjalankan Program

```bash
# Install dependencies
pip install numpy matplotlib scikit-fuzzy

# Jalankan Studi Kasus 1
python main.py

# Jalankan Studi Kasus 2
python studi2.py
```
