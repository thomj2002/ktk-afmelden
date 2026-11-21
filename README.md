# KTK Kampen — GitHub Pages / Eigen Domein Hosting

Deze map (`github-pages/`) bevat de kant-en-klare bestanden om het **Bestuursdashboard** en de **Leden Afmeld-app** te hosten op **GitHub Pages** (of Cloudflare Pages / Netlify / eigen domein), zonder dat de bestaande Google Apps Script-links worden verstoord.

---

## Bestanden in deze map
- **`index.html`** — Het **Aanwezigheidsdashboard** (voor Bestuur & Sectiehoofden). Ondersteunt ook automatisch `?page=afmelden` doorsturing.
- **`afmelden.html`** — De **Leden Afmeld-app** (voor alle leden).
- **`assets/`** — Gebundelde CSS-, JavaScript- en logo-bestanden aangemaakt door `npm run build:pages`.
- **`manifest.json`** & **`manifest-dashboard.json`** — Web-app manifests zodat leden en bestuursleden de pagina als volwaardige app op hun telefoon-startscherm kunnen zetten.

---

## Hoe werkt de koppeling?
1. De **bestaande Google Apps Script-links** (`.../exec` en `.../exec?page=afmelden`) blijven **100% ongemoeid** in `Afmeldingen-app/`.
2. Daarnaast gebruikt deze GitHub Pages-versie exact dezelfde `doPost(e)` JSON-API en hetzelfde `localStorage`-sleutelformaat (`ktk_socie_member_session_v1`), zodat leden die eerder *"Onthoud mij"* hebben aangevinkt gewoon ingelogd blijven.
3. Alle API-aanroepen gaan via `fetch()` POST-verzoeken naar:
   `https://script.google.com/macros/s/AKfycbwhSIHa7asKuidwN5V31eK0GFrIV_zySqwW4AJsqw6pOmlAKLfaOLAcek_-uhy_qoFGGg/exec`

---

## Zo zet je een nieuwe build live op GitHub Pages (in 2 minuten)
1. Bouw vanuit de hoofdmap de nieuwste GitHub Pages-bundel met: `npm run build:pages`
2. Upload alle bestanden én mappen uit `github-pages/` (`index.html`, `afmelden.html`, `assets/`, `manifest.json`, `manifest-dashboard.json`) naar de hoofdmap van je GitHub Pages-repository (ook de `assets/`-map mee uploaden!).
3. Ga in GitHub naar **Settings** &rarr; **Pages**.
4. Kies onder **Build and deployment** bij *Source* voor **Deploy from a branch** en selecteer de **`main`** branch (`/(root)`).
5. Na circa 1 minuut zijn je live links actief:
   - **Dashboard:** `https://<jouw-gebruikersnaam>.github.io/<repo-naam>/`
   - **Leden Afmeld-app:** `https://<jouw-gebruikersnaam>.github.io/<repo-naam>/afmelden.html` (of `.../?page=afmelden`)

