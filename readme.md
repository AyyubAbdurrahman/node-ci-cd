## Decision coveraeg and Multiple coverage

## Konsep

Decision coverage adalah teknik pengujian yang digunakan untuk memastikan setiap jalur logis dalam kode program telah diuji setidaknya sekali. Fokusnya adalah pada titik keputusan dalam kode, seperti pernyataan if, switch, atau loop bersyarat. Tujuanya untuk memastikan semua cabang logika berjalan dan teruji. teknik penjian ini sangat cocok digunakan untuk pengujian dengan tingkat kopleksitas rendah ataupun sedang

Multi-Decision coverage adalah pengembangan dari decision testing yang melibatkan lebih dari satu keputusan dalam satu skenario. Fokusnya adalah memastikan kombinasi berbagai keputusan telah diuji secara menyeluruh. Hal ini penting dalam sistem yang memiliki banyak kondisi yang saling tergantung. Tujuanya untuk memastikan semua kemungkinan kombinasi hasil dari kondisi dalam keputusan diuji. Multiple covergae memberikan cakupan yang sangat komphrensif dn juga dapat mengidentifikasi kesalahan logika yang berjalan secara kompleks.

### Gambar Ilustrasi

![image.png](images/ilustrasi.jpeg)

### Penjelasan

decision Point 1 (Username Valid)

Ini adalah titik keputusan pertama yang memeriksa validitas username.
Jika valid, jalur dilanjutkan ke Decision Point 2.
Jika tidak valid, jalur menuju ke hasil "Username Tidak Valid".

Decision Point 2 (Password Valid)
Jika password valid, jalur menuju ke hasil "Login Sukses".
Jika tidak valid, jalur menuju ke hasil "Password Salah".

Multi Decision Path
Ini menunjukkan jalur kombinasi kondisi yang diperiksa secara simultan antara validitas username dan validitas password.
Outcome

Berdasarkan hasil dari pengambilan keputusan, akan dihasilkan satu dari tiga jalur:
Login Sukses (Username dan Password valid)
Password Salah (Username valid tetapi password salah)
Username Tidak Valid (Username tidak ditemukan di database)

## Langkah-langkah Pengujian

berdasarkan gambar berikut penjelasanya

Berikut adalah langkah-langkah pengujian berdasarkan alur flowchart pada gambar:

## Pemahaman Komponen Flowchart

Decision Point 1 (Username Valid): Memeriksa apakah username yang dimasukkan valid atau tidak.
Decision Point 2 (Password Valid): Memeriksa apakah password yang dimasukkan valid atau tidak.
Multi-Decision Path (Kombinasi Kondisi): Menggabungkan hasil dari dua keputusan sebelumnya untuk menentukan jalur hasil akhir.
Outcome: Hasil akhir yang mungkin:
Login Sukses
Password Salah
Username Tidak Valid

##Langkah-Langkah Pengujian
Langkah 1: Pengujian Validasi Username
Masukkan username valid:
Pastikan sistem menganggap username benar.
Masukkan username tidak valid:
Pastikan sistem memberikan respons yang benar (contoh: pesan error "Username Tidak Valid").
Langkah 2: Pengujian Validasi Password
Masukkan password valid:
Pastikan sistem menganggap password benar.
Masukkan password tidak valid:
Pastikan sistem memberikan respons yang sesuai (contoh: pesan error "Password Salah").
Langkah 3: Kombinasi Pengujian (Multi-Decision Path)
Lakukan pengujian terhadap semua kemungkinan kombinasi dari username dan password:

Username valid + Password valid:
Hasil: Login Sukses.
Username valid + Password tidak valid:
Hasil: Password Salah.
Username tidak valid + Password valid:
Hasil: Username Tidak Valid.
Username tidak valid + Password tidak valid:
Hasil: Username Tidak Valid.
Langkah 4: Verifikasi Outcome
Untuk setiap kombinasi di langkah 3, pastikan sistem memberikan hasil sesuai dengan logika berikut:

Jika kedua kondisi benar, hasilnya adalah "Login Sukses".
Jika salah satu atau kedua kondisi salah, sistem memberikan respons error yang tepat.

## Contoh Kasus

# Decision Coverage

```python
def akses_layanan(usia, anggota):
if usia >= 18 and anggota == True:
return "Akses diberikan"
else:
return "Akses ditolak"

## penjelasan :

Kondisi Keputusan
Usia >= 18
Anggota == True
Pengujian
Untuk memastikan cakupan keputusan:

Test Case 1: usia = 20, anggota = True
Hasil: "Akses diberikan" (Cabang True dari kedua kondisi).

Test Case 2: usia = 16, anggota = False
Hasil: "Akses ditolak" (Cabang False dari kedua kondisi).

Hasil: Semua cabang logis diuji (True dan False).
```

# multiple decision coverage

```python
    def akses_layanan(usia, anggota):
            if usia >= 18 and anggota == True:
                return "Akses diberikan"
            else:
                return "Akses ditolak"


## Penjelasan :

Kombinasi Keputusan
Dua kondisi menghasilkan 4 kombinasi (2^2):

usia >= 18 = True, anggota == True = True

usia >= 18 = True, anggota == True = False

usia >= 18 = False, anggota == True = True

usia >= 18 = False, anggota == True = False

Pengujian
Test Case 1: usia = 20, anggota = True
Kombinasi: (True, True). Hasil: "Akses diberikan".

Test Case 2: usia = 20, anggota = False
Kombinasi: (True, False). Hasil: "Akses ditolak".

Test Case 3: usia = 16, anggota = True
Kombinasi: (False, True). Hasil: "Akses ditolak".

Test Case 4: usia = 16, anggota = False
Kombinasi: (False, False). Hasil: "Akses ditolak".

Hasil: Semua kombinasi kondisi diuji.
```

# Perbedaan :

| **Aspek**            | **Decision Coverage**                                       | **Multiple Decision Coverage**                  |
| -------------------- | ----------------------------------------------------------- | ----------------------------------------------- |
| **Jumlah Kombinasi** | Minimal, True/False untuk setiap kondisi secara individual. | Semua kombinasi True/False untuk semua kondisi. |
| **Tingkat Uji**      | Cukup memastikan setiap cabang diuji.                       | Lebih mendalam, mencakup kombinasi logika.      |

# Kesimpulan :

Decision Coverage memberikan cakupan dasar dengan fokus pada hasil individual setiap kondisi.
Multiple Decision Coverage memberikan cakupan yang lebih lengkap, memastikan semua kombinasi logika diuji untuk mengurangi risiko bug pada situasi kompleks.
Pemilihan metode bergantung pada kebutuhan pengujian dan kompleksitas sistem.

# Contoh penggunaan

```python
    def akses_layanan(usia, anggota):
            if usia >= 18 and anggota == True:
                return "Akses diberikan"
            else:
                return "Akses ditolak"
```

# Decision coverage

Test Case 1: usia = 20, anggota = True
Hasil: "Akses diberikan"
Cabang yang diuji:
usia >= 18 adalah True
anggota adalah True

Test Case 2: usia = 16, anggota = False
Hasil: "Akses ditolak"
Cabang yang diuji:
usia >= 18 adalah False
anggota adalah False

Cakupan:
Semua keputusan (True dan False) untuk masing-masing kondisi diuji setidaknya sekali

# Multiple decision coverage

```python
    def akses_layanan(usia, anggota):
            if usia >= 18 and anggota == True:
                return "Akses diberikan"
            else:
                return "Akses ditolak"
```

Pada Multiple Decision Coverage, kita menguji semua kombinasi kondisi yang ada. Karena ada dua kondisi (usia dan status anggota), kita memiliki 4 kombinasi kemungkinan:

usia >= 18 True, anggota True
usia >= 18 True, anggota False
usia >= 18 False, anggota True
usia >= 18 False, anggota False
Pengujian untuk Multiple Decision Coverage:
Test Case 1: usia = 20, anggota = True

Hasil: "Akses diberikan"
Kombinasi yang diuji: (True, True)
Test Case 2: usia = 20, anggota = False

Hasil: "Akses ditolak"
Kombinasi yang diuji: (True, False)
Test Case 3: usia = 16, anggota = True

Hasil: "Akses ditolak"
Kombinasi yang diuji: (False, True)
Test Case 4: usia = 16, anggota = False

Hasil: "Akses ditolak"
Kombinasi yang diuji: (False, False)

Cakupan:
Semua kombinasi keputusan (True dan False) diuji untuk setiap kondisi.

## Kontributor

Ayyub abdurahman 2200016092 (konsep)[https://github.com/AyyubAbdurrahman]
M.rizkiansyah 22000016008
Adam zalfa
[Tulis daftar kontributor (anggota kelompok) beserta link github]

```

```

```

```
