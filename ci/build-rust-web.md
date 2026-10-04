# CI — Build Rust dan Web

## Backend Rust (`lumbung-backend-service`)

1. Runner: `ubuntu-latest` + toolchain Rust stabil.
2. Perintah:
   ```bash
   cargo test --locked
   cargo build --release --locked
   ```
3. Migrasi diperiksa dengan `sqlx migrate lint` bila tersedia; jalankan `cargo sqlx prepare` sebelum commit yang mengubah query.

## Web (`lumbung-web`)

1. Runner: `ubuntu-latest` + Bun `1.4.x`.
2. Perintah:
   ```bash
   bun install --frozen-lockfile
   bun run check
   bun run build
   ```
3. Artefak: direktori `build/` SvelteKit untuk deploy statis/Node.
