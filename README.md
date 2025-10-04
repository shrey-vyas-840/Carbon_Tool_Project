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

## Tech stack
- HTML5, CSS3, JS (ES6)
- PHP 7/8 (server side)
- MySQL (phpMyAdmin)
- Playwright (visual captures)
- TestSprite (visual regression via API)
- Deployment: InfinityFree (FTP), alternative: Vercel with API migration

---

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

