# Dataset Program Studi Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Records](https://img.shields.io/badge/records-4.971-orange)](program-studi-indonesia.csv)

Data 4.971 program studi pada perguruan tinggi peserta SNPMB, lengkap dengan daya tampung, jumlah peminat, rasio keketatan, passing grade, dan rentang nilai, **untuk tahun data 2024**.

## Data

| File | Baris | Ukuran | Delimiter |
|------|-------|--------|-----------|
| `program-studi-indonesia.csv` | 4.971 | ~1 MB | `;` (titik koma) |

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `id` | UUID prodi | `0d47b35d-f7e8-4b1c-a283-cb8870bafaeb` |
| `university_id` | UUID PT (relasi ke dataset perguruan tinggi) | `08ebcbab-3307-4a61-93b1-9c58222723ea` |
| `code` | Kode prodi SNPMB | `13321021` |
| `name` | Nama program studi (huruf besar) | `SEKOLAH TEKNIK ELEKTRO DAN INFORMATIKA - KOMPUTASI (STEI-K)` |
| `degree` | Jenjang | `Sarjana`, `Sarjana Terapan`, `Diploma Tiga` |
| `quota` | Daya tampung | `90` |
| `applicants` | Jumlah peminat | `3454` |
| `category` | Kategori | `SAINTEK`, `SOSHUM` |
| `sub_category` | Sub-kategori (banyak yang kosong) | (kosong) |
| `competition_ratio` | Rasio keketatan (peminat dibagi kuota) | `38.38` |
| `passing_grade` | Passing grade estimasi, rentang data 371 sampai 790 | `790` |
| `classification` | Klasifikasi level | `Level 9` |
| `min_score` | Nilai minimum | `677` |
| `max_score` | Nilai maksimum | `697` |
| `university_name` | Nama PT (denormalisasi, memudahkan pemakaian) | `Institut Teknologi Bandung` |
| `university_code` | Kode PT | `ITB` |
| `university_region` | Provinsi PT | `Jawa Barat` |
| `university_type` | Tipe PT | `Negeri` |

Sebaran data: jenjang Sarjana 3.668, Sarjana Terapan 749, Diploma Tiga 554. Kategori SAINTEK 3.464, SOSHUM 1.507.

Catatan penting: **statistik tahunan melekat pada baris ini dan berasal dari tahun 2024**. Di platform SNBTKU, statistik dipisah ke tabel per tahun sehingga tahun berikutnya bisa ditambahkan tanpa mengubah struktur prodi.

## Contoh data

```csv
id;university_id;code;name;degree;quota;applicants;category;sub_category;competition_ratio;passing_grade;classification;min_score;max_score;university_name;university_code;university_region;university_type
0d47b35d-f7e8-4b1c-a283-cb8870bafaeb;08ebcbab-3307-4a61-93b1-9c58222723ea;13321021;SEKOLAH TEKNIK ELEKTRO DAN INFORMATIKA - KOMPUTASI (STEI-K);Sarjana;90;3454;SAINTEK;;38.38;790;Level 9;677;697;Institut Teknologi Bandung;ITB;Jawa Barat;Negeri
```

## Cara pakai

### 1. Unduh langsung

```bash
curl -O https://raw.githubusercontent.com/prodhokter/dataset-program-studi-indonesia/master/program-studi-indonesia.csv
```

### 2. Lewat API publik

Base URL: `https://datasets.snbtku.com` (hostname kedua: `https://api.ibnuhabib.web.id`)

```bash
# Cari prodi
curl "https://datasets.snbtku.com/api/v1/majors?q=informatika&limit=5"

# Filter kategori dan PT
curl "https://datasets.snbtku.com/api/v1/majors?category=SAINTEK&university_id=08ebcbab-3307-4a61-93b1-9c58222723ea&limit=10"

# Rekomendasi prodi untuk skor tertentu (passing grade kurang dari atau sama dengan skor)
curl "https://datasets.snbtku.com/api/v1/majors/smart-recommendations?score=700&category=SAINTEK&count=5"
```

Contoh respons nyata:

```json
// GET /api/v1/majors?q=informatika&limit=1
{
  "items": [
    {
      "id": "0d47b35d-f7e8-4b1c-a283-cb8870bafaeb",
      "university_id": "08ebcbab-3307-4a61-93b1-9c58222723ea",
      "university_name": "Institut Teknologi Bandung",
      "university_code": "ITB",
      "university_region": "Jawa Barat",
      "university_type": "Negeri",
      "name": "SEKOLAH TEKNIK ELEKTRO DAN INFORMATIKA - KOMPUTASI (STEI-K)",
      "degree": "Sarjana",
      "code": "13321021",
      "category": "SAINTEK",
      "stat_year": 2024,
      "quota": 90,
      "applicants": 3454
    }
  ],
  "total": 58,
  "limit": 1,
  "offset": 0
}
```

```json
// GET /api/v1/majors/smart-recommendations?score=700&count=1
{
  "count": 1,
  "items": [
    {
      "name": "TEKNIK GEOLOGI",
      "university_name": "Universitas Sriwijaya",
      "university_code": "UNSRI",
      "university_region": "Sumatera Selatan",
      "category": "SAINTEK",
      "stat_year": 2024,
      "quota": 42,
      "applicants": 596,
      "competition_ratio": 14.19,
      "passing_grade": 690
    }
  ]
}
```

Rate limit 120 permintaan per menit per IP, CORS terbuka, respons di-cache 5 menit.

## Sumber & lisensi

- Sumber: data SNPMB (kuota, peminat, dan statistik nilai) tahun 2024.
- Repo ini (kompilasi dan pembersihan): MIT, Copyright (c) 2025 Ibnul Habib.

## Changelog

Lihat [CHANGELOG.md](CHANGELOG.md).
