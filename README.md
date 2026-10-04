# lumbung-infra-devops

Infrastruktur dan DevOps Lumbung: CI, deploy, dan runbook operasional gudang.

## Cakupan CI

- KMP: rakit APK (`lapangan-mobile`) dan paket MSIX (`gudang-desktop`) — lihat `ci/build-kmp.md`.
- Rust dan Web: `cargo test` untuk backend, `bun install` + build untuk web — lihat `ci/build-rust-web.md`.
- Deploy produksi: lihat `deploy/prod/README.md`.
- Runbook insiden: lihat `docs/runbook.md`.

## Runner Gudang

- Runner `gudang` (Windows) untuk build MSIX dan uji perangkat USB/serial + printer thermal.
- Runner `linux` untuk backend Rust dan web.

## Rahasia (Secrets)

- `DATABASE_URL` — string koneksi basis data `lumbung` (wajib basis data khusus lumbung, bukan gabungan divisi).
- `JWT_ED25519_PRIVATE` — kunci privat ed25519 untuk menandatangani JWT akses.
- `DEVICE_API_KEY_GUDANG` — kunci API perangkat gudang (timbangan/cetak).
- `SERVICE_API_KEY` — kunci API antar-layanan (pipeline, AI serving).

Jangan pernah commit nilai rahasia; simpan sebagai GitHub Actions secrets atau berkas `.env` lokal yang diabaikan git.
