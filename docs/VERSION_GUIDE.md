# Version Update Guide

This document lists all the locations where the application version number needs to be updated when releasing a new version.

## Configuration Files

| File Path | Location / Key | Description |
|-----------|---------------|-------------|
| `package.json` | `version` | Main Node.js project version. |
| `src-tauri/tauri.conf.json` | `version` | Tauri application version (used for build artifacts). |
| `src-tauri/Cargo.toml` | `version` | Rust crate version. |
| `bucket/health-reminder.json` | `version` | Scoop bucket manifest version. |

## Lock Files (Auto-generated)

| File Path | Command to Update | Description |
|-----------|-------------------|-------------|
| `package-lock.json` | `npm install` | Updates after `package.json` change. |
| `src-tauri/Cargo.lock` | `cargo check` (in `src-tauri/`) | Updates after `Cargo.toml` change. |

## UI & Localization (Source Code)

| File Path | Keys to Update | Description |
|-----------|---------------|-------------|
| `src/i18n/zh-CN.js` | `app.footer`<br>`settings.currentVersion`<br>`settings.newVersion` | Display text in Chinese UI (Footer & Settings). |
| `src/i18n/en-US.js` | `app.footer`<br>`settings.currentVersion`<br>`settings.newVersion` | Display text in English UI (Footer & Settings). |

## Documentation

| File Path | Location | Description |
|-----------|----------|-------------|
| `README.md` | Badge URL (`shields.io`)<br>`## 版本记录` (Changelog) | Chinese README version badge and history. |
| `README.en.md` | Badge URL (`shields.io`)<br>`## Version History` (Changelog) | English README version badge and history. |
| `docs/screenshots/` | Feature screenshots used by README files | Add or refresh screenshots for user-facing changes. |

## Update Checklist

1. [ ] Update `package.json`.
2. [ ] Update `src-tauri/tauri.conf.json`.
3. [ ] Update `src-tauri/Cargo.toml`.
4. [ ] Update `bucket/health-reminder.json` (use `hash: "skip"` only before the release asset exists; the release workflow replaces it with the real SHA256).
5. [ ] Update localization files (`src/i18n/*.js`).
6. [ ] Update `README.md` and `README.en.md` (Badge, screenshots & Changelog).
7. [ ] Run `npm install` to update `package-lock.json`.
8. [ ] Run `cd src-tauri && cargo check` to update `Cargo.lock`.
9. [ ] Run `npm run build` to verify the build.
