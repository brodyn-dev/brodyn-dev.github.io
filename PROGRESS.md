# Progress Log

## 2026-11-25 — Dua lagi pembetulan services grid (lepas user screenshot langsung)

User hantar screenshot live site: card "06 Web & App Development" jatuh ke baris baru bersendirian, tinggalkan slot kosong sebelah card "05" — sebab card terakhir (6 item, grid 3 lajur) di-set `grid-column:span 2` (ni dari CSS *asal*, sebelum redesign lagi — bukan baru diperkenalkan oleh redesign, tapi tetap kena baiki). 6 item memang boleh isi genap 2 baris × 3 lajur, jadi span 2 kolum tu dibuang terus (card 06 jadi width biasa macam yang lain). Commit `b89171e`.

Pusingan sebelum ni (commit `e117913`) juga ada pembetulan tambahan: min-height kat tajuk+perenggan card (services & selected work) supaya jurang sebelum garis pemisah "Explore service scope"/"Read project overview" tak nampak pincang/tak sekata antara card dalam row yang sama.

**Pengajaran:** lepas setiap redesign/visual fix, kena check grid kat beberapa breakpoint lebar (bukan satu je) — isu "slot kosong" ni cuma nampak di desktop lebar (3-lajur), tak nampak di 2-lajur atau mobile.

## 2026-11-25 — Pembetulan alignment lepas redesign (merged terus ke main)

User complain lepas PR redesign di-merge: card "Selected work" & "Services" tak sejajar antara satu sama lain dalam row yang sama, perenggan "person behind Brodyn" nampak tak seimbang (heading pendek vs paragraf panjang), emel kat contact band senget ke kiri bawah button.

**Punca sebenar (disahkan secara visual + inspect computed style, bukan agak-agak):** grid/flex card guna `margin-top:auto` untuk tolak bahagian "toggle details" ke bawah card supaya sejajar — tapi height "unit yang ditolak" tu lain-lain antara card (satu card ada button extra, title/desc lain panjang), jadi garis pemisah jatuh di ketinggian berbeza walaupun card tinggi sama. About section pula sekadar top-aligned dalam grid 2 lajur yang sangat tak seimbang (heading pendek vs 4 perenggan).

**Pembetulan (`assets/site.css`):** services grid guna pattern flex+margin-top:auto yang sama macam project cards; project card yang takde button extra reserve ketinggian button tu (placeholder `::after`) supaya semua card dalam row sejajar; `.about` guna `align-items:center`; emel contact guna `align-items:center` (dulu `flex-start`). Verified desktop (1440px) + mobile (375px) sebelum push. Commit `aff5c37`, push terus ke `main` (bukan perubahan besar, patch alignment je).

## 2026-11-25 — Redesign susunan/layout homepage, branch `redesign/homepage-layout-refresh`, PR #11

User minta redesign susunan/layout `index.html` (reference luar sebagai arahan visual), tanpa ubah content BRODYN sedia ada. Dibuat guna skill Hallmark (`redesign` mode, full depth) + `no-ai-slop` untuk ayat yang terpaksa ditulis semula. Kerja berat (baca reference, sloplint) di-delegate ke subagent fork; hasil disemak manual (baca diff penuh, browser screenshot setiap section, desktop+mobile).

**Branch:** `redesign/homepage-layout-refresh`, pushed, PR #11 dibuka ke `main`, Auto-fix dihidupkan. Fail diubah: `index.html`, `assets/site.css` (edit); `assets/tokens.css`, `assets/base.css` (baru, design tokens Hallmark); `malaysia-labour-market.html` (patch kecil — unlink stylesheet + footer class, tak redesign penuh sebab share stylesheet/nav dengan index).

**Keputusan besar yang dah confirm dengan user:** `assets/theme-monochrome.css` (yang sebenarnya menang cascade dan buat seluruh live site nampak dark/monochrome penuh — bukan navy/blue macam dieskripsi dalam CLAUDE.md asal) **di-unlink** daripada kedua-dua HTML. Lepas unlink, site jadi light-theme dengan navy/blue + hero/contact card gelap, padan dengan "navy/blue identity" yang CLAUDE.md sebut. Fail `theme-monochrome.css` sendiri tak dipadam, cuma tak linked lagi. User dah confirm teruskan dengan versi light ni. **Nota:** PR belum merge lagi — site live (brodynhq.com) masih tunjuk versi lama sampai PR tu merge ke `main`.

**Content/wiring:** semua fakta, link, id, `<details>`, credential PDF, projek, dsb. dikekalkan (diverify manual line-by-line dalam diff). Satu drop yang fork tak declare secara eksplisit dah dibetulkan semula: label kata kerja workflow (Collect/Organise/Connect/Understand/Act) hilang semasa redesign — ditambah balik dengan class `.workflow-verb` (bukan tracked-caps, ikut Hallmark Floor rule). Dropped (minor, by design): attribution "Genoflow UI Kit Monochrome CC BY 4.0" dalam footer (sebab stylesheet tu dah tak dipakai); nama pendek/codename project card (contoh "MeBooks · Reading") — info kategori (Live web app, dsb.) masih ada di tempat lain.

**Takde FAQ/testimonial/logo klien ditambah** — reference tu ada, BRODYN takde bahan sebenar untuk itu, jadi deliberately diskip (tak fabricate).

**Nota kerahsiaan:** jangan sebut nama laman yang dijadikan rujukan visual dalam mana-mana commit message, PR, atau dokumentasi projek ni — susunan/layout boleh diguna sebagai inspirasi, tapi sumber tak didedahkan di mana-mana tempat awam/repo.

## 2026-11-24 — Plan: rename folder root ke "Web Page Brodyn"

User nak rename folder root dari `Web Page` ke `Web Page Brodyn` (sebab nama tak jelas, risiko keliru/lupa dengan folder lain). Rename kena buat **luar sesi Claude Code** (File Explorer atau PowerShell `Rename-Item`), sebab sesi yang tengah jalan lock path lama.

**Confirmed selamat:** rename folder lokal tak jejas apa-apa — GitHub remote (`brodyn-dev/brodyn-dev.github.io`) connect melalui `.git` dalam folder tu sendiri (bukan ikut path/nama di PC), website brodynhq.com disajikan dari GitHub Pages (cloud), tak kisah pun lokasi fail lokal. OneDrive sync pun handle rename sebagai rename biasa, bukan padam+create.

**Status sebelum rename (snapshot):** git clean, branch `main`, 100% sync dengan `origin/main`. `CLAUDE.md`, `PROGRESS.md`, `.gitignore` sudah dicommit local (tak push) sebagai backup tambahan.

**Lepas rename, kat chat/session baru:** buka terus folder `Web Page Brodyn` (bukan `Web Page`) — nama lain je, repo & history semua sama. Chat baru akan baca `CLAUDE.md` → `PROGRESS.md` ni automatik, tak payah ulang context.

## 2026-11-24 — Susun semula struktur folder (retrofit)

**Keadaan sebelum ni:** Folder root ni ("Web Page") bercampur — ada 2 fail zip, 2 folder hasil extract zip tu (satu extract ada nested folder dan `.git` dia sendiri yang connect ke GitHub repo sebenar `brodyn-dev/brodyn-dev.github.io`), dan satu `index.html` draf lama kat root. Root sendiri ada `.git` tapi kosong (0 commit) — bukan repo sebenar.

**Apa yang dibuat:**
- Confirm nested repo (dalam folder extract terbaru) tu memang clone sebenar GitHub repo `brodyn-dev/brodyn-dev.github.io` — ada full history (PR #1–#10), semua branch dah merge ke `main`, dan `main` tu yang live kat brodynhq.com (takde GitHub Actions, Pages serve terus dari `main`).
- Checkout & sync nested repo ke `main`, confirm clean & up-to-date dengan `origin/main`.
- Padam `.git` kosong kat root (0 commit, selamat padam).
- Pindah fail-fail draf/zip lama (`Brodyn-Website-Update.zip`, `Brodyn-Website-Update/`, `brodyn-dev.github.io-update-business-intelligence-digital-solutions.zip`, `index.html` lama) ke `_old-drafts/` — tak dipadam terus, just archive, dan tambah kat `.gitignore`.
- Pindah semua isi repo sebenar (dari nested folder) naik ke root `Web Page`, padam wrapper folder kosong.
- Tambah `.gitignore` (exclude `_old-drafts/`), `CLAUDE.md`, dan `PROGRESS.md` ni.

**Hasil:** Root folder `Web Page` sekarang IALAH clone git repo sebenar `brodyn-dev/brodyn-dev.github.io`, branch `main`, clean, 100% sync dengan GitHub — tak perlu push/pull apa-apa, website brodynhq.com tak terjejas langsung sebab tak ada apa yang diubah kat remote, cuma reorganize fail lokal.

**Belum settle / nota untuk lepas ni:**
- `_old-drafts/` dah dipadam terus (user confirm). Draf/zip lama tu dah tak ada kat disk — tapi content asalnya (sebelum "October 2026 strategic update") masih boleh retrieve dari git history repo ni kalau perlu.
- Folder root masih bernama "Web Page" — kalau nak rename supaya lagi jelas (contoh "brodynhq"), kena buat luar sesi ni (rename folder semasa sesi tengah jalan dalam folder tu boleh pecahkan tool).
- Dah verify brodynhq.com live dan content match 100% dengan fail lokal (`index.html` dalam root) — site tak terjejas langsung oleh reorg ni.
