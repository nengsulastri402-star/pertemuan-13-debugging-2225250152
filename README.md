# Pertemuan 13 - Debugging dan Testing

**Nama:** [SULASTRI]  
**NIM:** [ 2225250152]  
**Kelas:** [B] 
**Prodi:** [Pendidikan Matematika]  

## Kasus
Pengujian dan perbaikan program pemrosesan data nilai mahasiswa yang memiliki masalah logical bug pada kalkulasi rata-rata, penentuan kelulusan nilai batas, dan ekstraksi nilai tertinggi.

## Test Case
| ID | Input | Expected | Actual Awal | Status Awal |
|---|---|---|---|---|
| T1 | `[80, 60, 90, 70]` | 75.0 | 60.0 | FAIL |
| T2 | `[100, 80]` | 90.0 | 36.0 | FAIL |
| T3 | `60` | Lulus | Tidak lulus | FAIL |
| T4 | `59` | Tidak lulus | Tidak lulus | PASS |
| T5 | `[80, 60, 90, 70]` | 90 | 0 | FAIL |

## Bug Report
* **B01 (Rata-rata):** 
  - *Gejala:* Nilai rata-rata salah ketika panjang list bukan 5.
  - *Lokasi:* Fungsi `hitung_rata_rata`.
  - *Akar Penyebab:* Pembagi di-hardcode angka 5.
  - *Perbaikan:* Mengganti pembagi dengan `len(nilai)`.
* **B02 (Status Batas):**
  - *Gejala:* Nilai 60 dinyatakan "Tidak lulus".
  - *Lokasi:* Fungsi `status`.
  - *Akar Penyebab:* Operator perbandingan `>` tidak mencakup nilai 60.
  - *Perbaikan:* Mengubah operator menjadi `>=`.
* **B03 (Nilai Tertinggi):**
  - *Gejala:* Output selalu 0 untuk angka positif.
  - *Lokasi:* Fungsi `nilai_tertinggi`.
  - *Akar Penyebab:* Kondisi perbandingan terbalik (`<`) dan inisialisasi awal 0.
  - *Perbaikan:* Inisialisasi dengan `nilai[0]` dan ubah kondisi menjadi `>`.

## Retest
| ID | Input | Expected | Actual Akhir | Status Retest |
|---|---|---|---|---|
| T1 | `[80, 60, 90, 70]` | 75.0 | 75.0 | PASS |
| T2 | `[100, 80]` | 90.0 | 90.0 | PASS |
| T3 | `60` | Lulus | Lulus | PASS |
| T4 | `59` | Tidak lulus | Tidak lulus | PASS |
| T5 | `[80, 60, 90, 70]` | 90 | 90 | PASS |

## Cara Menjalankan
```bash
python3 praktik/praktik_4_debugging.py
