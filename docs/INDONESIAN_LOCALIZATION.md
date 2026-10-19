# Indonesian Localization Integration Guide (Durango: Renewal v3.2.x)

> **Bahasa Indonesia** · [English](#english) · [ภาษาไทย](#ภาษาไทย)

Mod Lokalisasi Bahasa Indonesia untuk **Durango: Reborn / Renewal Client** (v3.2.0 – v3.2.4+).

Repository Resmi Mod: [https://github.com/my-aicustom/durango-indonesia-mod](https://github.com/my-aicustom/durango-indonesia-mod)  
Author / Maintainer: **Ddos-spec** ([@Ddos-spec](https://github.com/Ddos-spec) · `setgraph69@gmail.com`)

---

## Bahasa Indonesia

### 1. Deskripsi Mod
Mod ini memungkinkan pemain menikmati Durango: Renewal secara penuh dalam Bahasa Indonesia tanpa memodifikasi file asli game (`resources.assets`). 
Sistem bekerja secara dinamis saat runtime (*zero-asset patch*) menggunakan **Unity Doorstop** dan **HarmonyLib** untuk mencegat pemanggilan teks NGUI / LocalizeSystem.

### 2. Fitur & Keunggulan
- **Non-Destructive**: 100% aman dari kerusakan arsip game.
- **Kamus Lengkap**: 
  - `thai-id.tsv` (~6.8 MB) — Translasi dialog, item, crafting, skill.
  - `korean-id.tsv` (~4.1 MB) — Fallback kamus Korea original.
  - `indonesia-overrides.tsv` — Override nama pulau, bioma, faksi, dan event.
- **Support BBCode & Icon**: Menjaga tag warna, format `{0}`, dan icon sprite bawaan game tetap utuh.

### 3. Struktur File Distribusi Client (PC)
```text
Durango_Game_Directory/
├── DurangoV2.exe
├── winhttp.dll                  (Unity Doorstop Proxy)
├── doorstop_config.ini          (Konfigurasi target assembly)
├── thai-id.tsv                  (Kamus Thai -> ID)
├── korean-id.tsv                (Kamus Korean -> ID)
├── indonesia-overrides.tsv      (Override istilah khusus)
└── DurangoV2_Data/
    └── Managed/
        ├── 0Harmony.dll         (Harmony v2 runtime)
        └── Durango.ThaiToId.dll (Compiled Assembly Mod)
```

### 4. Konfigurasi `doorstop_config.ini`
```ini
[General]
enabled=true
target_assembly=DurangoV2_Data\Managed\Durango.ThaiToId.dll
redirect_output_log=false
```

---

## English

### 1. Overview
This mod provides comprehensive Indonesian localization for **Durango: Renewal PC Client** (v3.2.x) using runtime injection via **Unity Doorstop** and **HarmonyLib**. 
It translates Thai, Korean, and English UI text and quest dialogues dynamically on the fly without touching the original `resources.assets`.

### 2. Key Highlights
- **Zero-Asset Modification**: Clean drop-in/drop-out installation.
- **Massive Terminology Database**: Tens of thousands of precompiled exact-match entries (`thai-id.tsv`, `korean-id.tsv`).
- **Safe Tag Preservation**: Automatically preserves NGUI BBCode, placeholder tokens, and sprite tags.

### 3. Proposal for Upstream Integration (SoloCode228 / ShuuuuShi)
Maintainers can bundle this mod as an optional language pack for Indonesian community members:
1. Include `Durango.ThaiToId.dll` and `0Harmony.dll` inside `DurangoV2_Data/Managed/`.
2. Provide a toggle in the launcher or a `.bat` switcher (`Play_Indonesian.bat` vs `Play_Default.bat`) that activates/deactivates `winhttp.dll` or `doorstop_config.ini`.
3. Source code & dictionary updates are hosted at [https://github.com/my-aicustom/durango-indonesia-mod](https://github.com/my-aicustom/durango-indonesia-mod).

---

## ภาษาไทย

### คำแนะนำสำหรับผู้พัฒนา (SoloCode228)
ม็อดนี้เป็นม็อดแปลภาษาอินโดนีเซียสำหรับ Durango: Renewal (PC) โดยใช้ **Unity Doorstop** และ **HarmonyLib** ดักจับข้อความตอนรันเกม โดยไม่ต้องแก้ไขไฟล์ `resources.assets` ดั้งเดิมของผู้พัฒนา

ผู้พัฒนาสามารถรวมม็อดนี้ไว้เป็นตัวเลือกภาษาเสริม (Language Pack) ให้กับผู้เล่นชาวอินโดนีเซียได้ทันที โดยเปิด/ปิดผ่าน `doorstop_config.ini` (enabled=true / false).
