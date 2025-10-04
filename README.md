# 🌿 Carbon Tool Project

![License](https://img.shields.io/badge/license-MIT-green) ![Platform](https://img.shields.io/badge/platform-Web-lightgrey)

A lightweight, user-friendly Carbon Emission Calculator and green products marketplace. Helps users estimate emissions (electricity, water, fuel, green-building), view recommended products and approximate electricity bills, and access green consulting services.

## Features
- Multi-category carbon emission calculator:
  - Electricity (appliance-based kWh and emissions)
  - Water usage emissions
  - Green building impact calculator
  - Fuel consumption emissions
- Electricity bill estimator with configurable modes and FPPA + fixed charge breakdown
- Product catalog with category filters (electricity, water, building, etc.)
- Protected tools page — requires login
- Save results to backend (MySQL / PHP)
- Responsive, accessible UI and simple deployment ready

## Screenshots
Place your screenshots in `/assets/screenshots` and reference them here.

## Quick Start (local)
1. Clone repository:
   git clone https://github.com/shrey-vyas-840/Carbon_Tool_Project.git
2. Move into project:
   cd Carbon_Tool_Project
3. Start local PHP + MySQL (XAMPP):
   - Ensure Apache and MySQL are running.
4. Import database dump (phpMyAdmin or mysqldump).
5. Update DB config:
   - Edit `includes/db.php` with remote/local DB credentials.
6. Open in browser:
   http://localhost/your_path/tool.html

## Deploy to InfinityFree (summary)
1. Export your local DB (phpMyAdmin → Export).
2. In InfinityFree control panel create MySQL DB and import SQL.
3. Upload project files to `/htdocs` via FTP (FileZilla).
4. Update `includes/db.php` with InfinityFree DB credentials.
5. Test live site and remove any debug files.

## Usage
- Register / Login (creates `greenshift_user` in localStorage)
- Open Tools → Electricity → pick appliances → Calculate Emissions
- After results: view energy-saving tips, then View Related Products or Estimate Bill

## Architecture
- Frontend: Static HTML, CSS, vanilla JS (main.js)
- Backend: PHP endpoints + MySQL (for auth and saving results)
- Pages:
  - tool.html — main calculators
  - products.html — product listing & filters
  - services.html — service descriptions
- DB: MySQL (users, saved_results, products)

## Tech Stack
- HTML5, CSS3, JavaScript (ES6)
- PHP 7.x/8.x (server-side)
- MySQL / phpMyAdmin
- Optional dev: Playwright for visual tests

## Development & Tests
- Playwright scripts located in `/tests` capture screenshots for visual tests.
- TestSprite integration: upload screenshots for visual regression.

## Contributing
- Fork → branch → PR
- Keep secrets out of repo (DB credentials in includes/db.php should be local-only)

## License
MIT — see LICENSE file.

## Contact
Project owner: shrey-vyas-840  
GitHub: https://github.com/shrey-vyas-840/Carbon_Tool_Project
