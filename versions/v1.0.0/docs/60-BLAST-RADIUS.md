> Versi: v1.0.0 | Status: disetujui | Menggantikan: -
> Sumber: Lumbung-TownHall `platform/versions/v1.0.0/` pada commit `673a467`; [townhall-roadmap.md §2](https://github.com/Coding-Skuy/ChefGenie-TownHall/blob/main/townhall-roadmap.md); [KONTEKS §8/§9](https://github.com/Coding-Skuy/ChefGenie-TownHall/blob/main/KONTEKS-LINTAS-DIVISI.md)

# 60 — Blast Radius lumbung-infra-devops

Batas context v1.0.0 Lumbung (townhall-roadmap §2): 3 komoditas pilot, fee Rp1.500/kg dekat dan Rp2.500/kg jauh, radius 25 km; point of concern titik impas 18.000 kg/bulan dan susut <5%.

## Boleh disentuh

- Workflow CI, skrip deploy, konfigurasi environment, runbook, backup/restore.
- Mengelola secrets repo/organisasi Lumbung.

## Dilarang

- Menyentuh DB logis divisi lain (`pasaree`, `titipo`, `pedaree`, `pawonee`, `titeny`).
- Menambah `event_type` di luar registry KONTEKS §3 tanpa bump versi + 30 hari dual-read.
- Menambah komoditas keempat atau melayani di luar radius 25 km (non-goal PRD/30).
- Menyimpan nilai rahasia di repo atau log CI.
- Menggabungkan DB `lumbung` dengan DB divisi lain.
- Merilis dengan tes merah atau melewati QA gate.
- Mengaktifkan auto-update MSIX (non-goal v1.0.0).

## Kontrak diproduksi

- Artefak rilis: MSIX, APK, IPA, image/artefak backend dan web.
- Runbook insiden dan jadwal rotasi kunci.

## Kontrak dikonsumsi

- Repo kode: `lumbung-app-kmp`, `lumbung-backend-service`, `lumbung-web`, `lumbung-data-pipeline`, `lumbung-ai-models`.
- Persyaratan keamanan dari SRS/30 dan `docs/auth.md` backend.

## Aturan perubahan

Perubahan di luar batas ini = PR requirement di Lumbung-TownHall lebih dulu, lalu ADR baru di repo ini. Perubahan angka lintas-divisi wajib memperbarui KONTEKS §terkait + dokumen divisi + CHANGELOG versi dalam PR yang sama (KONTEKS §9).
