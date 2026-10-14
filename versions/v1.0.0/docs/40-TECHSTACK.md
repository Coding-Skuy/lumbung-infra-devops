> Versi: v1.0.0 | Status: disetujui | Menggantikan: -
> Sumber: Lumbung-TownHall `platform/versions/v1.0.0/` pada commit `673a467` ([platform/versions/v1.0.0](https://github.com/Coding-Skuy/Lumbung-TownHall/blob/673a467126e195ffd67c9d3ff21d108193a6c3ec/platform/versions/v1.0.0))

# 40 — Tech Stack lumbung-infra-devops

Matriks CI/deploy v1.0.0.

## Matriks

| Artefak | Runner | Perintah inti | Kanal rilis |
|---|---|---|---|
| MSIX `:gudang-desktop` 1.0.0 | Windows `gudang` | Gradle package MSIX (x64) | MSIX/EXE di PC gudang |
| APK `:lapangan-mobile` | Linux | Gradle assemble | Play Store + APK sideload |
| IPA iOS | macOS | Xcode archive | TestFlight |
| Backend Rust | Linux | `cargo test --locked` + build | deploy per env |
| Web Bun | Linux | `bun install` + `bun run build` | VPS (SSR) |

## Rahasia

| Rahasia | Dipakai oleh | Rotasi |
|---|---|---|
| `DATABASE_URL` | backend | saat insiden |
| `JWT_ED25519_PRIVATE` | backend | sesuai ADR keamanan |
| `DEVICE_API_KEY_GUDANG` | perangkat gudang | 90 hari (tenggang 7 hari) |
| `SERVICE_API_KEY` | pipeline, ai-models | sesuai ADR keamanan |
| `LUMBUNG_API_KEY` | web (server) | 90 hari; cabut 1 jam bila bocor |
