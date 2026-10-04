# Runbook Operasional Lumbung

## Basis Data `lumbung` Terpisah

- Basis data `lumbung` adalah Postgres khusus divisi Lumbung; jangan gabung dengan basis data divisi lain.
- Nama basis data: `lumbung`. Pengguna aplikasi: `lumbung_app` dengan hak minimal (tanpa `SUPERUSER`).
- Cadangan harian penuh + WAL; uji restore tiap pekan.

## Tuning Pool Koneksi

- `sqlx` pool: `max_connections = 2 × jumlah vCPU API` (contoh: 4 vCPU → 8 koneksi per replika).
- `min_connections = 2`; `idle_timeout = 300s`; `max_lifetime = 1800s`.
- Batas koneksi Postgres (`max_connections`) wajib ≥ total pool seluruh replika + 10 cadangan admin.

## `sqlx prepare` (Offline Check)

- Wajib jalan sebelum commit yang mengubah query SQL:
  ```bash
  cargo sqlx prepare --database-url "$DATABASE_URL"
  ```
- Hasilnya (`sqlx-data.json`) di-commit agar `cargo test` lolos tanpa DB hidup.

## Insiden Umum

- `healthz` gagal cek DB: periksa `DATABASE_URL`, konektivitas, dan pool penuh.
- Timbangan USB tidak terbaca: ganti port, periksa driver serial, restart layanan `gudang-desktop`.
- Printer thermal diam: cetak halaman uji, periksa kertas 58mm, pastikan status cetak tidak menggantung di backend.
