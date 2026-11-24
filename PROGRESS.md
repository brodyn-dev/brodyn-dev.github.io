# Progress Log

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
