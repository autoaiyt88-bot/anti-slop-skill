# anti-slop

Skill untuk Claude yang mencegah output generik dan "terasa buatan AI" (slop) di lima bidang: desain, kode, tulisan, media (motion graphic, video, slide), serta riset dan klaim faktual.

Cara kerjanya: Claude menangkap konteks, memilih arah yang spesifik, mengerjakan dengan isi nyata, lalu mengaudit hasilnya memakai daftar tanda slop per bidang dan memperbaikinya.

## Isi

```
anti-slop/
├── SKILL.md                      alur kerja, prinsip, peta referensi
├── references/
│   ├── design.md                 UI, web, grafis
│   ├── code.md                   kode dan review kode
│   ├── writing.md                tulisan (Indonesia dan Inggris)
│   ├── media.md                  motion graphic, video, VO, slide, gambar AI
│   └── facts-and-claims.md       riset, analisis, laporan kerja jujur
└── scripts/
    └── slop_scan.py              pemindai pola slop permukaan (opsional)
```

## Instalasi

**Claude.ai:** unduh `anti-slop.skill` (atau zip folder `anti-slop/` dengan folder itu di root zip), lalu unggah di Settings, bagian Skills.

**Claude Code:**

```bash
git clone https://github.com/USERNAME/anti-slop-skill.git
cp -r anti-slop-skill/anti-slop ~/.claude/skills/
```

Untuk satu proyek saja, salin ke `.claude/skills/` di dalam proyek.

## Pemakaian

Skill terpanggil otomatis saat kamu meminta Claude membuat atau memperbaiki sesuatu, atau menyebut hal seperti "jangan generik", "anti slop", "lebih natural". Contoh:

- "Buatkan landing page untuk kedai kopi, jangan kelihatan buatan AI."
- "Review kode ini, cari yang slop."
- "Tulis ulang caption ini supaya lebih manusiawi."

Pemindai manual:

```bash
python3 anti-slop/scripts/slop_scan.py artikel.md styles.css app.js
```

## Kontribusi

Tambahkan pola slop baru di `references/` atau di daftar `RULES` pada `slop_scan.py`. Sertakan alasan mengapa pola itu slop dan cara menggantinya.

## Lisensi

MIT. Lihat `LICENSE`.
