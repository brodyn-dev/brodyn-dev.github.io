# BRODYN website (brodynhq.com)

Baca [PROGRESS.md](PROGRESS.md) dulu sebelum mula kerja, dan update dia lepas keputusan/pembetulan penting.

## Apa projek ni

Website personal/business untuk BRODYN (Hafizz) — Business Intelligence & Digital Solutions.
Static HTML/CSS, takde build step, takde JS framework, takde dependency luar.
Host kat GitHub Pages, repo `brodyn-dev/brodyn-dev.github.io`, custom domain `brodynhq.com` (fail `CNAME`).
GitHub Pages serve terus dari branch `main` (takde GitHub Actions workflow) — commit/merge ke `main` = live terus.

## Struktur fail

- `index.html` — homepage (hero, services, portfolio/work, skills, about, credentials, contact)
- `malaysia-labour-market.html` — case study page (kongsi stylesheet + nav dengan index)
- `assets/site.css` — shared stylesheet (navy/blue identity, accessibility skip link, reduced-motion support)
- `assets/theme-monochrome.css` — theme tambahan
- `assets/credentials/*.pdf` — sijil yang privacy-edited (surname redacted) — jangan upload sijil asli/belum redacted
- `CNAME`, `robots.txt`, `sitemap.xml` — jangan tukar melainkan diminta
- `README.md` — dokumentasi asal projek (preview/publish workflow)
- `_old-drafts/` — arkib draf/export lama (zip & folder extract versi sebelum ni), **tak ditrack git** (.gitignore). Boleh padam bila dah confirm tak perlu.

## Peraturan kerja

- Ni live production website — jangan push terus ke `main` untuk perubahan besar. Guna branch + PR macam workflow sedia ada (lihat git log untuk contoh nama branch & commit message).
- Jangan ubah `CNAME` kecuali diminta — ubah ni boleh rosakkan domain brodynhq.com.
- Sijil dalam `assets/credentials/` mesti kekal privacy-edited (surname redacted, metadata dibuang). Jangan replace dengan versi asal.
- Commit message boleh guna Bahasa Melayu (ikut history sedia ada) atau English — tengok konteks.
