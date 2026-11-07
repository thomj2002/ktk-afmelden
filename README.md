# KTK Kampen — GitHub Pages / Eigen Domein Hosting

Deze map (`github-pages/`) bevat de kant-en-klare bestanden om het **Bestuursdashboard** en de **Leden Afmeld-app** te hosten op **GitHub Pages** (of Cloudflare Pages / Netlify / eigen domein), zonder dat de bestaande Google Apps Script-links worden verstoord.

---

## Bestanden in deze map
- **`index.html`** — Het **Afmeldingen Dashboard** (voor Bestuur & Sectiehoofden). Ondersteunt ook automatisch `?page=afmelden` doorsturing.
- **`afmelden.html`** — De **Leden Afmeld-app** (voor alle leden).
- **`manifest.json`** & **`manifest-dashboard.json`** — Web-app manifests zodat leden en bestuursleden de pagina als volwaardige app op hun telefoon-startscherm kunnen zetten.

---

## Hoe werkt de koppeling?
1. De **bestaande Google Apps Script-links** (`.../exec` en `.../exec?page=afmelden`) blijven **100% ongewijzigd doorwerken** via `doGet(e)`.
2. Daarnaast heeft `Code.js` nu een `doPost(e)` JSON-ontvanger.
3. Wanneer `index.html` of `afmelden.html` buiten Google Apps Script wordt geopend (bijv. via GitHub Pages of lokaal in je browser), zet de ingebouwde API-bridge alle `google.script.run` aanroepen automatisch om naar veilige `fetch()` POST-verzoeken naar:
   `https://script.google.com/macros/s/AKfycbwhSIHa7asKuidwN5V31eK0GFrIV_zySqwW4AJsqw6pOmlAKLfaOLAcek_-uhy_qoFGGg/exec`

---

## Zo zet je het live op GitHub Pages (in 2 minuten)
1. Maak op [github.com](https://github.com) een nieuwe repository aan (bijv. `ktk-afmelden`).
2. Upload de bestanden uit deze map (`index.html`, `afmelden.html`, `manifest.json`, `manifest-dashboard.json`) naar de hoofdmap van die repository.
3. Ga in GitHub naar **Settings** &rarr; **Pages**.
4. Kies onder **Build and deployment** bij *Source* voor **Deploy from a branch** en selecteer de **`main`** branch (`/(root)`).
5. Na circa 1 minuut zijn je nieuwe links actief:
   - **Dashboard:** `https://<jouw-gebruikersnaam>.github.io/<repo-naam>/`
   - **Leden Afmeld-app:** `https://<jouw-gebruikersnaam>.github.io/<repo-naam>/afmelden.html` (of `.../?page=afmelden`)

