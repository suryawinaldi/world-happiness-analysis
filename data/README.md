# Sumber data

Notebook revisi menggunakan workbook resmi:
https://files.worldhappiness.report/WHR26_Data_Figure_2.1.xlsx

Letakkan file asli di `data/raw/WHR26_Data_Figure_2.1.xlsx` atau di akar proyek. Jika tidak tersedia, notebook mencoba mengunduhnya. Jangan mengganti XLSX dengan CSV lama yang diganti ekstensi.

- Sheet: `Data for Figure 2.1 (2011–2025)`
- SHA-256 yang diperiksa notebook: `576e382655cec3ae704a0b41cd2c04465b87cd84b7f131a0c4fa26d41f6d8028`
- Cakupan yang diharapkan: 2.116 baris, 168 negara/teritori, 14 label tahun; label 2013 tidak tersedia.
- Workbook belum disertakan dalam pembaruan ini. Unduhan dari lingkungan pemeriksaan ditolak proxy (HTTP 403). Hasil eksekusi ulang belum diverifikasi di lingkungan ini.
- CSV dalam `raw/` adalah input versi awal, dipertahankan untuk audit, bukan input notebook revisi.
- Sumber dan ketentuan penggunaan: https://www.worldhappiness.report/data-sharing/ . Data tetap milik penyedia sumber; repository ini tidak memberikan lisensi ulang atas data tersebut.

## Kamus kolom keluaran

| Kolom | Makna |
|---|---|
| country | Negara atau teritori menurut sumber |
| year | Label akhir jendela survei; 2025 mewakili 2023–2025 |
| rank | Peringkat publikasi pada label terkait |
| score | Skor evaluasi hidup, skala 0–10 |
| ci_lower, ci_upper | Batas IK 95% skor; NA jika tidak tersedia |
| c_gdp, c_support, c_health | Kontribusi dekomposisi PDB, dukungan sosial, dan kesehatan, dalam poin skor |
| c_freedom, c_generosity, c_corruption | Kontribusi dekomposisi kebebasan, kedermawanan, dan persepsi korupsi, dalam poin skor |
| dystopia_residual | Prediksi tolok ukur Dystopia ditambah residual negara |
| complete_decomposition | Semua tujuh komponen tersedia |

Kontribusi merupakan keluaran model WHR, bukan indikator mentah atau efek kausal. Nilai hilang tidak diubah menjadi nol. Tabel analisis baru ditulis ke `outputs/` saat notebook dijalankan.
