# Dataset Program Studi Indonesia

Data seluruh program studi perguruan tinggi di Indonesia, dilengkapi kuota, peminat, keketatan, dan passing grade.

## Data

**File:** `program-studi-indonesia.csv`  
**Records:** 4.971 program studi  
**Size:** ~1 MB  
**Delimiter:** titik koma (`;`)

## Kolom

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `id` | UUID prodi | `a83673a9-...` |
| `university_id` | UUID perguruan tinggi | `3557957e-...` |
| `code` | Kode prodi SNPMB | `24743030` |
| `name` | Nama program studi | `TEKNIK INFORMATIKA` |
| `degree` | Jenjang | `Sarjana`, `Sarjana Terapan`, `Diploma Tiga` |
| `quota` | Daya tampung | `120` |
| `applicants` | Jumlah peminat | `2.450` |
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

## Contoh

```csv
id;university_id;code;name;degree;quota;applicants;category;sub_category;competition_ratio;passing_grade;classification;min_score;max_score;university_name;university_code;university_region;university_type
a83673a9-...;3557957e-...;24743030;TEKNIK INFORMATIKA;Sarjana;120;2450;SAINTEK;;20.42;720;;689;756;Universitas Indonesia;UI;Jawa Barat;Negeri
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses via REST API:

```
GET /api/majors?search=informatika&university=ui&category=saintek&degree=sarjana&page=1&limit=50
GET /api/majors/:id
```

## Sumber

SNPMB / LTMPT — data resmi seleksi nasional perguruan tinggi.

## Lisensi

Data bersumber dari institusi pemerintah Indonesia. Gunakan sesuai ketentuan yang berlaku.
