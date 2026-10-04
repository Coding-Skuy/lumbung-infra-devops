# CI — Build KMP (MSIX / APK)

Alur CI untuk `lumbung-app-kmp`.

## APK Lapangan (`lapangan-mobile`)

1. Runner: `ubuntu-latest` + JDK 17 + Android SDK.
2. Perintah:
   ```bash
   ./gradlew :lapangan-mobile:assembleRelease
   ```
3. Artefak: `lapangan-mobile-*.apk` diunggah ke GitHub Releases.

## MSIX Gudang (`gudang-desktop`)

1. Runner: `windows-latest` (atau runner mandiri `gudang`) + JDK 17.
2. Perintah:
   ```bash
   ./gradlew :gudang-desktop:packageMsi
   ./gradlew :gudang-desktop:packageMsix
   ```
3. Artefak: paket `.msix` diunggah ke GitHub Releases.
4. Uji perangkat (hanya runner `gudang` fisik): baca serial timbangan sekali + cetak halaman uji thermal.

## Cache

- Cache direktori `~/.gradle` dan `build/` antar jalan agar build reproduksibel.
