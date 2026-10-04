# Deploy Produksi Lumbung

## Topologi

- API: `lumbung-backend-service` (kontainer, 2 replika) di depan penyeimbang beban.
- Web: `lumbung-web` (statis/Node) di CDN.
- DB: Postgres khusus `lumbung` (terpisah dari divisi lain).

## Langkah Rilis

1. Terapkan migrasi: `sqlx migrate run --database-url "$DATABASE_URL"`.
2. Gulirkan kontainer API ke citra baru; tunggu `GET /healthz` menjawab `ok`.
3. Sebarkan web; verifikasi halaman `/ops`, `/rute`, `/papan-harga`.
4. Putar balik bila `healthz` gagal 3 kali beruntun.

## Pasca-rilis

- Periksa log error 15 menit pertama.
- Pastikan pipeline `ingest-timbangan` tetap menulis ke DB `lumbung`.
