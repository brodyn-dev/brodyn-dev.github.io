# BRODYN ENTERPRISE

Business Intelligence & Digital Solutions — https://brodynhq.com

Independent business website by Hafizz. Static HTML and CSS, hosted through the existing GitHub Pages configuration. No build step, JavaScript framework or external runtime dependency.

## October 2026 strategic update

- Evolve the hero and metadata around data, business processes and digital solutions.
- Expand services into BI & analytics, automation, business systems, websites and research/reporting. Retain data collection, preparation, Power BI, monthly reporting and website setup.
- Preserve the three original projects; add ongoing labour-market research and the internal BMS.
- Preserve the founder's research, Learning & Development, employment services, compliance and programme-monitoring background; connect it to practical digital solutions.
- Group existing and new skills. Python, SQL and Git remain foundational; Power Apps is developing.
- Add seven verified course/learning-path completions in a compact expandable section; privacy-edited PDFs are linked with the user’s approval. These do not assert PL-300, MOS or PMP certification or Microsoft partnership.
- Identify vending work as a family-business practice project, not an independently verified paid client engagement.

## Preservation checklist

- [x] Original Malaysia Labour Market Intelligence case-study text, findings, caveats and attributions.
- [x] Both original dashboard screenshots, unchanged.
- [x] All original external dashboard and email URLs.
- [x] Seven privacy-edited certificate PDFs included and linked; only Mohammad Hafizz remains visible.
- [x] Financial Sample description, sample-data disclaimer and in-development status.
- [x] Vending scope and privacy protection; no private dashboard added.
- [x] All existing relevant skills, including HTML/CSS, Cloudflare and Search Console.
- [x] Existing navy/blue identity, accessibility skip link and reduced-motion support.
- [x] Existing section anchors, including #work and #skills.
- [x] CNAME, robots.txt and sitemap.xml unchanged. No new public HTML page requires a sitemap addition.

## Files

Modified:
- `index.html`: expanded content and navigation, credentials, project statuses and metadata.
- `malaysia-labour-market.html`: shared stylesheet and navigation only; case-study content unchanged.
- `README.md`: current positioning, preservation and publishing instructions.

Added:
- `assets/site.css`: original inline CSS extracted into one shared stylesheet, with responsive expansion styles.

Seven privacy-edited PDFs are included under `assets/credentials/`. The surname was permanently redacted, metadata removed and copies labelled as privacy-edited. Original certificates remain unchanged and are not published.

## Verification and remaining review

Checked local links, fragment targets, original external-link preservation, sitemap XML, unchanged domain/configuration/image files, and redacted certificate text. Certificate titles/dates were extracted and visually reviewed against the PDFs.

A local Chromium download failed in this environment, so desktop/mobile browser rendering has NOT been verified. Before merging, preview at desktop and phone widths, open the credential and service accordions, and click the case-study and PDF links. All seven privacy-edited certificate links resolve locally. Financial Sample is still in development; BMS has no public demo or private records attached, intentionally. Add new evidence only as modules are completed.

## Preview on Windows (PowerShell)

Run these commands from the parent folder where you keep projects. If this repository is already cloned, use its existing folder and skip the clone command.

```powershell
git clone https://github.com/brodyn-dev/brodyn-dev.github.io.git
cd brodyn-dev.github.io
git fetch origin
git switch update/business-intelligence-digital-solutions
git pull --ff-only
py -m http.server 8000
```

Open http://localhost:8000 in a browser. Use Ctrl+C in the terminal to stop the preview. A local server does not publish the site.

## Commit further edits to the review branch

The prepared update is already committed when delivered as a pull request. Use the following only after making additional local edits:

```powershell
git status
git add index.html malaysia-labour-market.html assets README.md
git commit -m "Refine Brodyn digital solutions website"
git push origin update/business-intelligence-digital-solutions
```

## Publish after review

Either mark the draft pull request ready and merge it into `main` on GitHub, OR use the commands below. Do not do both. These commands require a clean working tree and publish the reviewed update to the existing Pages source branch:

```powershell
git fetch origin
git switch main
git pull --ff-only origin main
git merge --no-edit origin/update/business-intelligence-digital-solutions
git push origin main
```

If Git reports a merge conflict, resolve it before pushing; never force-push. The existing GitHub Pages workflow then builds and deploys. Check the latest successful run in Actions before refreshing https://brodynhq.com with Ctrl+F5. Keep `CNAME` unchanged. No Cloudflare or DNS changes are needed for this content update.
