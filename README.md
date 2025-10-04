# 🌿 EarthenCare — Carbon Tool Project

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE) [![Live Demo](https://img.shields.io/badge/demo-earthencare.gt.tc-brightgreen)](https://earthencare.gt.tc) ![Platform](https://img.shields.io/badge/platform-Web-lightgrey)

A compact, usable carbon-emission calculator and verified green‑products marketplace — built for quick local testing and easy FTP deployment (InfinityFree). Designed for clarity and action: calculate emissions, estimate electricity bills, discover verified products, and access green consultancy services.

---

## Demo
Live site: https://earthencare.gt.tc

---

## Key Features (at-a-glance)
- Appliance-level Electricity calculator (kWh → CO₂)  
- Water, Fuel and Green‑Building calculators (inputs-validated)  
- Electricity bill estimator (bracketed rate + FPPA + fixed charge)  
- Product marketplace with category filters and "View related products" links from tools  
- Protected Tools page (login required)  
- Save/load results to MySQL via PHP backend  
- Simple Playwright visual test scripts + TestSprite uploader

---

## Visual quick‑tour
- Hero: Tools (Electricity, Water, Green Building, Fuel)  
- Results view: detailed table + energy tips + "View related products" CTA  
- Product page: card grid with "Verified supplier" tag per card  
- Services: Carbon Calculator, Marketplace, Green Consultation

---

## Quick start (local)
1. Clone:
   ```
   git clone https://github.com/shrey-vyas-840/Carbon_Tool_Project.git
   cd Carbon_Tool_Project
   ```
2. Run (XAMPP):
   - Start Apache + MySQL
   - Import DB: phpMyAdmin → import provided SQL
3. Configure DB:
   - Edit `includes/db.php` with your DB host/name/user/password
4. Open:
   - http://localhost/<your-path>/tool.html
5. Test login:
   - Register / Login -> header shows Logout -> Tools access unlocked

---

## Usage notes
- Electricity bill rules implemented:
  - If units ≤ 50 → ₹3.20 / unit
  - If 51–100 → ₹3.95 / unit
  - If >100 → ₹5.00 / unit
  - FPPA charge: ₹3.81 / unit (added to subtotal)
  - Fixed charge: ₹50
  - Total = (units × rate) + (units × 3.81) + 50
- If user leaves units blank the estimator defaults to 1 unit (note displayed).
- Product filters:
  - Tools → after valid results a "View related products" button appears and links to `products.html?cat=<category>`
  - Products page has manual filter dropdown for direct visits

---

## Architecture (concise)
- Frontend: static HTML + CSS + vanilla JS (`main.js`)  
- Backend: PHP endpoints (auth, save results) + MySQL (users, products, results)  
- Tests: Playwright scripts in `tests/` (capture screenshots) + TestSprite uploader helper

---

// ...existing code...
## Tech stack
- HTML5, CSS3, JS (ES6)
- PHP 7/8 (server side)
- MySQL (phpMyAdmin)
- Playwright (visual captures)
- TestSprite (visual regression via API)
- Deployment: InfinityFree (FTP), alternative: Vercel with API migration

<!-- Visual tech stack bar -->
<div style="max-width:720px; margin:1rem 0; font-family:inherit;">
  <style>
    .tech-row { display:flex; align-items:center; gap:0.75rem; margin:0.5rem 0; }
    .tech-label { width:140px; font-weight:600; color:#0b5; }
    .bar { flex:1; height:14px; background:#e6f5ea; border-radius:8px; overflow:hidden; box-shadow:inset 0 -1px 0 rgba(0,0,0,0.03); }
    .bar > span { display:block; height:100%; border-radius:8px; }
    .html { background: linear-gradient(90deg,#ffdd57,#ffb347); width:95%; }
    .css { background: linear-gradient(90deg,#6dd5ed,#2193b0); width:90%; }
    .js { background: linear-gradient(90deg,#f7df1e,#f0c419); width:85%; }
    .php { background: linear-gradient(90deg,#8892BF,#6e5494); width:75%; }
    .mysql { background: linear-gradient(90deg,#4caf50,#2e7d32); width:80%; }
    .playwright { background: linear-gradient(90deg,#7f5af0,#5ad0a6); width:60%; }
    .testsprite { background: linear-gradient(90deg,#ff7eb3,#ff758c); width:50%; }
    .hosting { background: linear-gradient(90deg,#00c6ff,#0072ff); width:70%; }
    .tech-value { width:56px; text-align:right; font-size:0.85rem; color:#555; margin-left:0.6rem; }
  </style>

  <div class="tech-row"><div class="tech-label">HTML</div><div class="bar"><span class="html"></span></div><div class="tech-value">95%</div></div>
  <div class="tech-row"><div class="tech-label">CSS</div><div class="bar"><span class="css"></span></div><div class="tech-value">90%</div></div>
  <div class="tech-row"><div class="tech-label">JavaScript</div><div class="bar"><span class="js"></span></div><div class="tech-value">85%</div></div>
  <div class="tech-row"><div class="tech-label">PHP</div><div class="bar"><span class="php"></span></div><div class="tech-value">75%</div></div>
  <div class="tech-row"><div class="tech-label">MySQL</div><div class="bar"><span class="mysql"></span></div><div class="tech-value">80%</div></div>
  <div class="tech-row"><div class="tech-label">Playwright</div><div class="bar"><span class="playwright"></span></div><div class="tech-value">60%</div></div>
  <div class="tech-row"><div class="tech-label">TestSprite</div><div class="bar"><span class="testsprite"></span></div><div class="tech-value">50%</div></div>
  <div class="tech-row"><div class="tech-label">Hosting (InfinityFree)</div><div class="bar"><span class="hosting"></span></div><div class="tech-value">70%</div></div>
</div>
// ...existing code...

## Deployment (InfinityFree summary)
1. Create InfinityFree account and add site/subdomain.
2. Create MySQL DB in control panel and import SQL backup.
3. Use FTP (FileZilla) to upload project files to `/htdocs`.
4. Update `includes/db.php` with remote DB credentials.
5. Verify `https://<your-domain>/tool.html` works and remove any debug files.

---

## Troubleshooting (common)
- 500 / DB errors: check `includes/db.php` credentials and host.
- Missing assets: verify paths are relative (e.g., `./main.js`, `./style.css`).
- Tools blocked: ensure `greenshift_user` is created on login (localStorage) and `tool.html` checks it.
- Playwright: regenerate screenshots with `node tests/capture-and-compare.js`.

---

## Contributing
- Fork → feature branch → PR with focused changes
- Keep secrets out of the repo (do not commit `includes/db.php` with real credentials)
- Add tests for new calculator rules or product types

Suggested .gitignore (add before first commit):
```text
/node_modules/
/vendor/
/.env
includes/db.php
*.sql
/screenshots/
/.DS_Store
```

---

## Acceptance tests (examples)
- Electricity units 40 → subtotal 128.00; FPPA 152.40; fixed 50; total 330.40  
- Units 75 → subtotal 296.25; FPPA 285.75; fixed 50; total 632.00  
- Units 120 → subtotal 600.00; FPPA 457.20; fixed 50; total 1107.20

---

## License
MIT — see `LICENSE` file.

---

## Contact
Repo / owner: https://github.com/shrey-vyas-840  
Live demo: https://earthencare.gt.tc

