# Dataset Program Studi Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![API Status](https://img.shields.io/badge/api-live-green)](https://api.ibnuhabib.web.id/api/majors)
[![Records](https://img.shields.io/badge/records-4.971-orange)](program-studi-indonesia.csv)

Data seluruh program studi perguruan tinggi di Indonesia, dilengkapi kuota, peminat, keketatan, dan passing grade dari SNPMB.

## Data

| File | Records | Size | Delimiter |
|------|---------|------|-----------|
| `program-studi-indonesia.csv` | 4.971 | ~1 MB | `;` (titik koma) |

## Kolom

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `id` | UUID prodi | `a83673a9-...` |
| `university_id` | UUID perguruan tinggi | `3557957e-...` |
| `code` | Kode prodi SNPMB | `24743030` |
| `name` | Nama program studi | `TEKNIK INFORMATIKA` |
| `degree` | Jenjang | `Sarjana`, `Sarjana Terapan`, `Diploma Tiga` |
| `quota` | Daya tampung | `120` |
| `applicants` | Jumlah peminat | `2450` |
| `category` | Kategori | `SAINTEK`, `SOSHUM` |
| `sub_category` | Sub-kategori | |
| `competition_ratio` | Rasio keketatan (peminat/kuota) | `20.42` |
| `passing_grade` | Passing grade estimasi | `720` |
| `classification` | Klasifikasi | |
| `min_score` | Skor minimum (data 2024) | `689` |
| `max_score` | Skor maksimum (data 2024) | `756` |
| `university_name` | Nama perguruan tinggi | `Universitas Indonesia` |
| `university_code` | Kode singkat PT | `UI` |
| `university_region` | Provinsi PT | `Jawa Barat` |
| `university_type` | Tipe PT | `Negeri`, `Swasta`, `Kedinasan` |

## Contoh Data

```csv
id;university_id;code;name;degree;quota;applicants;category;sub_category;competition_ratio;passing_grade;classification;min_score;max_score;university_name;university_code;university_region;university_type
a83673a9-...;3557957e-...;24743030;TEKNIK INFORMATIKA;Sarjana;120;2450;SAINTEK;;20.42;720;;689;756;Universitas Indonesia;UI;Jawa Barat;Negeri
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses REST API.

**Base URL:** `https://api.ibnuhabib.web.id`

```bash
# Cari program studi
curl "https://api.ibnuhabib.web.id/api/majors?search=informatika&limit=5"

# Prodi di PT tertentu
curl "https://api.ibnuhabib.web.id/api/majors?university=ui"

# Filter kategori + jenjang
curl "https://api.ibnuhabib.web.id/api/majors?category=saintek&degree=sarjana&limit=10"

# Prodi kedokteran di PTN
curl "https://api.ibnuhabib.web.id/api/majors?search=kedokteran&type=negeri"

# Detail prodi
curl "https://api.ibnuhabib.web.id/api/majors/a83673a9-..."

# Download CSV
curl -O "https://api.ibnuhabib.web.id/download/majors.csv"
```

**Parameter search:**

| Param | Deskripsi |
|-------|-----------|
| `search` | Nama program studi |
| `university` | Nama atau kode PT |
| `category` | `SAINTEK` atau `SOSHUM` |
| `degree` | `Sarjana`, `Sarjana Terapan`, `Diploma Tiga` |
| `region` | Provinsi PT |
| `type` | `Negeri`, `Swasta`, `Kedinasan` |
| `page` | Halaman (default 1) |
| `limit` | Per halaman (max 500, default 50) |

## Dataset Terkait

- [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) — REST API
- [dataset-perguruan-tinggi-indonesia](https://github.com/prodhokter/dataset-perguruan-tinggi-indonesia)
- [dataset-sekolah-indonesia](https://github.com/prodhokter/dataset-sekolah-indonesia)
- [dataset-kbbi-indonesia](https://github.com/prodhokter/dataset-kbbi-indonesia)
- [dataset-wilayah-indonesia](https://github.com/prodhokter/dataset-wilayah-indonesia)

## Sumber

SNPMB / LTMPT — data resmi seleksi nasional perguruan tinggi.

## Lisensi

MIT — © 2025 [Ibnul Habib](https://github.com/prodhokter). Data bersumber dari institusi pemerintah Indonesia.
