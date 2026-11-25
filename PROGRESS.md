# Progress Log

## 2026-11-25 — Tambah projek "Personal Training Log Dashboard" ke Selected work

User (hafizz) tanya boleh tambah showcase projek GitHub terbaru dia dalam portfolio. Dicari guna `gh repo list brodyn-dev` — jumpa `hafizz-training-log` (public). Check `gh api repos/.../commits` dan repo metadata dulu sebelum tulis apa-apa copy: repo ni **fork** dari `dreeveapp/dreeve` (projek open-source self-hosted fitness dashboard, dulu nama "Statistics for Strava"), **bukan** app yang dibina dari kosong oleh hafizz. Kerja sebenar hafizz: deploy Docker + Cloudflare Tunnel (`metrain.brodynhq.com`), import backlog Strava (876 aktiviti), retheme penuh (warna moss, font, logo), beberapa bug fix UI (theme toggle sync, OG image dashboard, table width widget).

**Keputusan (confirm dengan user guna AskUserQuestion):** (1) link live dashboard terus (`https://metrain.brodynhq.com`) dalam card, walaupun dashboard tu papar data fitness peribadi sebenar (nama, rupa lokasi lari/basikal) — user dah confirm ok; (2) copy explicitly declare ia "self-hosted & customized open-source app", bukan claim "built from scratch" — supaya jujur, sebab semua card lain dalam Selected work describe app yang dibina sendiri (React/Power BI/dsb).

Card baru letak dalam `index.html` (lepas MeBooks Reading Tracker), guna pattern sedia ada (tech tags, `<details>` overview, status, `.actions` dengan button + project-link macam card Malaysia Labour Market Intelligence). Link GitHub pun ditambah (`https://github.com/brodyn-dev/hafizz-training-log`). Footer "Selected projects" list pun ditambah entry sama untuk konsisten dengan projek live lain. Verified kat browser (local `static-preview` server, sebab file:// terus tak load CSS betul dalam preview pane).

Branch `portfolio/add-training-log-dashboard`, PR #15, user confirm merge terus (`gh pr merge --merge`, commit `8615590`) — site live brodynhq.com kini ada card ni. Local `main` disync (fast-forward), branch kerja dipadam (local + remote) lepas merge.

## 2026-11-25 — Tukar Blueprint ke sheet "whiteprint" (PR #14 merged) — site kini terang semula

User rasa tema "cyanotype" (dark, round sebelum ni) terlalu berat/"ringan kepala", dan tanya sama ada ni memang betul ikut skill Hallmark. Check punca: tema Blueprint sendiri ada **3 sheet variant** dalam dokumentasi dia (cyanotype/dark, whiteprint/light, brownline/sepia) — fork guna default (cyanotype) je tanpa declare pilihan lain ada. Bukan salah skill, salah pilihan variant.

Tukar ke **whiteprint**: kekal semua ciri Blueprint (radius 0, keyline bukan shadow, uppercase drafted type), tapi page jadi terang. Dua "band" gelap (hero data card + contact band) dikekalkan sebagai aksen — pattern yang sama macam design round pertama (sebelum Blueprint).

**Bug dijumpai & dibaiki sekali (bukan sekadar swap token):** beberapa heading dalam band gelap guna token yang jadi gelap lepas swap (nyaris tak nampak, gelap-atas-gelap) — dibetulkan. Hover nav link "mati" sebab accent token = ink token (same value) — accent kini warna biru lebih tegas, berbeza dari ink. Contrast diukur betul (canvas sRGB, bukan andaian): body ~5.1:1, heading ~10.6:1, aksen ~5.7:1 — semua lepas AA.

Branch `restyle/whiteprint-sheet`, PR #14, merged ke `main` (`1049ad0`). Nota: push direct ke main kali ni **di-block** oleh auto-mode classifier (perubahan visual besar) — kena guna branch+PR walaupun ni "pembetulan" kepada restyle yang baru je di-merge.

## 2026-11-25 — Restyle tema warna (PR #13 merged) — site kini "Blueprint" dark theme

User rasa tema navy/blue-on-white (dari redesign awal) generic/tak ada vibe. Jalankan Hallmark **restyle** depth (bukan full redesign — layout/content kekal, cuma sistem visual berubah): deal 3 tema, pilih **Blueprint** — seluruh page dark navy sheet, putih sebagai satu-satunya aksen/ink, radius 0, takde shadow, card guna keyline nipis. Masih ada benang biru ke identity lama, tapi jauh lebih distinctive.

Contrast diukur betul guna canvas-based sRGB conversion dalam browser (bukan andaian): body text ~6.2:1, heading ~10.5:1, button ~11.3:1 — semua lepas AA, kebanyakan lepas AAA. Semua fix alignment sesi ni (card divider, grid gap kosong, about/contact centering) di-reverify kat 1600px & mobile, semua masih hold.

Branch `restyle/theme-refresh`, PR #13, merged ke `main` (fast-forward, `e7dbd2d`). Site live brodynhq.com kini guna tema Blueprint ni.

## 2026-11-25 — Isu sama jumpa di "Selected work" grid, dah dibaiki

User jumpa isu sama (slot kosong) di section "Selected work": card terakhir (Malaysia Labour Market Intelligence) di-set `grid-column:1/-1` (full-width, side-by-side image+text) semasa redesign — ini BUKAN dari CSS asal, memang diperkenalkan semasa redesign sebagai "featured card" style. 6 project card dalam grid 3-lajur: 2 card biasa tak boleh share baris dengan satu card full-width, so dia terpaksa jatuh baris baru, tinggalkan slot kosong. Dibetulkan dengan kembalikan card tu jadi width biasa (gambar di atas, macam design asal sebelum redesign) — 6 card kini isi genap 2 baris × 3 lajur. Commit `814033c`.

**Patut saya dah check dari awal:** lepas fix grid pertama (services), saya patut terus check grid "Selected work" juga sebab guna struktur serupa (grid 3-lajur + card khas) — tak tunggu user jumpa sendiri.

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
