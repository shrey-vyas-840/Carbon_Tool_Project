# 🌿 EarthenCare - Carbon Tool Project

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Live Demo](https://img.shields.io/badge/demo-earthencare.gt.tc-brightgreen)](https://earthencare.gt.tc)
![Platform](https://img.shields.io/badge/platform-Web-lightgrey)
![Built with](https://img.shields.io/badge/Built%20with-HTML%2C%20CSS%2C%20JS%2C%20PHP-blue)
![Status](https://img.shields.io/badge/status-Active-success)

---

### 🪴 Overview

**EarthenCare** is a compact carbon-emission calculator and verified green-products marketplace — designed for clarity, action, and simple FTP deployment.  
It helps users **calculate emissions**, **estimate electricity bills**, and **discover verified eco-products** with ease.

🌐 **Live Demo:** [https://earthencare.gt.tc](https://earthencare.gt.tc)

---

## ⚡ Key Features
✅ Appliance-level Electricity calculator (kWh → CO₂)  
✅ Water, Fuel & Green-Building calculators (validated inputs)  
✅ Electricity bill estimator (bracketed rate + FPPA + fixed charge)  
✅ Product marketplace with filters + related product linking  
✅ Protected Tools page (login required)  
✅ MySQL data persistence (save/load results)  
✅ Playwright visual tests + TestSprite visual regression tool  

---

## 🧩 Architecture Overview

    U[User Browser 🌐] --> A[Frontend (HTML, CSS, JS)]
    A -->|HTTP Requests| B[PHP Backend (Auth & Logic)]
    B --> C[(MySQL Database)]
    B --> D[Playwright Visual Tests]
    D --> E[TestSprite Visual Regression]
    B --> F[InfinityFree Hosting / FTP]


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

## Tech stack
- HTML5, CSS3, JS (ES6)
- PHP 7/8 (server side)
- MySQL (phpMyAdmin)
- Playwright (visual captures)
- TestSprite (visual regression via API)
- Deployment: InfinityFree (FTP), alternative: Vercel with API migration


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
- Tools blocked: ensure `users` is created on login (localStorage) and `tool.html` checks it.
- Playwright: regenerate screenshots with `node tests/capture-and-compare.js`.

---

## Contributing
- Fork → feature branch → PR with focused changes
- Keep secrets out of the repo (do not commit `includes/db.php` with real credentials)
- Add tests for new calculator rules or product types


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

