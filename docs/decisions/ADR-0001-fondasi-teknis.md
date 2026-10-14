# ADR-0001 — Fondasi teknis lumbung-infra-devops

- Status: Diterima
- Tanggal: 2026-10-14

## Konteks

lumbung-infra-devops merakit dan merilis seluruh artefak Lumbung (MSIX gudang wajib hari-1, APK/IPA, backend Rust, web Bun) dan mengelola rahasia serta backup.

## Keputusan

1. CI memblokir rilis bila tes merah (SRS QA-002); tanpa skip tes.
2. Windows MSIX 1.0.0 dirakit di runner Windows `gudang`; kanal rilis MSIX/EXE; mobile Play Store + APK sideload + TestFlight/IPA; tanpa auto-update MSIX.
3. DB `lumbung` khusus (bukan gabungan divisi); `DATABASE_URL` hanya ke DB tersebut.
4. Rahasia sebagai GitHub Actions secrets: `DATABASE_URL`, `JWT_ED25519_PRIVATE`, `DEVICE_API_KEY_GUDANG`, `SERVICE_API_KEY`, `LUMBUNG_API_KEY`; rotasi 90 hari; pencabutan dalam 1 jam.
5. Backup dan uji restore dijadwalkan; runbook insiden dan rollback terdokumentasi.
6. Deploy per environment dengan jejak versi rilis.

## Konsekuensi

- Pipeline rilis backend/web/KMP harus lulus QA gate sebelum deploy.
- Kunci gudang lama diberi tenggang 7 hari saat rotasi (`docs/auth.md` backend).
