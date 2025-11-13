sd-decals/
├── generate_site.py
├── templates/
│   └── index_template.html
├── data/
│   └── products.json
├── static/
│   ├── style.css
│   └── logo.svg
└── README.md
import json
from pathlib import Path

# Load product data
with open("data/products.json", "r") as f:
    products = json.load(f)

# Load HTML template
template = Path("templates/index_template.html").read_text()

# Build product cards
product_html = ""
for p in products:
    product_html += f"""
    <div class='product-card'>
        <img src='{p['image']}' alt='{p['name']}'>
        <h3>{p['name']}</h3>
        <p>{p['price']}</p>
    </div>
    """

# Insert products into template
final_html = template.replace("{{ products }}", product_html)

# Create site folder and write HTML
Path("site").mkdir(exist_ok=True)
Path("site/static").mkdir(exist_ok=True)
(Path("site") / "index.html").write_text(final_html)

# Copy assets
for asset in Path("static").glob("*"):
    (Path("site/static") / asset.name).write_bytes(asset.read_bytes())

print("✅ Site generated in /site folder! Ready for GitHub Pages.")
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SD Sports Decals</title>
  <link rel="stylesheet" href="static/style.css">
</head>
<body>
  <header>
    <img src="static/logo.svg" alt="SD Sports Decals Logo" class="logo">
    <h1>SD Sports Decals</h1>
    <p>Your one-stop shop for custom sports helmet decals!</p>
  </header>

  <section class="products">
    <h2>Our Decals</h2>
    <div class="product-grid">
      {{ products }}
    </div>
  </section>

  <footer>
    <p>© 2025 SD Sports Decals | Contact: <a href="mailto:orders@sdsportsdecals.com">orders@sdsportsdecals.com</a></p>
  </footer>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background: #f8f9fc;
  color: #111;
  text-align: center;
}

header {
  background: linear-gradient(135deg, #002b5b, #0b66ff);
  color: white;
  padding: 2rem 1rem;
}

.logo {
  width: 100px;
  height: auto;
}

.products {
  padding: 2rem;
}

.product-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
}

.product-card {
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  padding: 1rem;
  width: 200px;
}

.product-card img {
  width: 100%;
  border-radius: 6px;
}

footer {
  background: #002b5b;
  color: white;
  padding: 1rem;
  font-size: 0.9rem;
}
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 240 240">
  <defs>
    <linearGradient id="grad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#002B5B"/>
      <stop offset="100%" stop-color="#0B66FF"/>
    </linearGradient>
  </defs>
  <rect width="240" height="240" rx="24" fill="white"/>
  <path d="M50 70 C50 45, 110 45, 110 65 C110 85, 80 85, 65 95 C50 105, 90 110, 110 130 C130 150, 80 165, 50 150 C35 142, 35 130, 55 125 C80 120, 100 115, 85 105 C70 95, 50 95, 50 70Z" fill="url(#grad)"/>
  <path d="M140 60 L140 160 L170 160 C205 160, 215 130, 215 110 C215 85, 205 60, 170 60 Z" fill="url(#grad)"/>
  <text x="120" y="215" text-anchor="middle" font-family="Arial Black" font-size="26" fill="#0B66FF">SPORTS DECALS</text>
</svg>
[
  {"name": "Football Helmet Decal", "price": "$8.99", "image": "static/football.png"},
  {"name": "Hockey Team Sticker", "price": "$6.99", "image": "static/hockey.png"},
  {"name": "Baseball Cap Logo", "price": "$5.49", "image": "static/baseball.png"}
]
# 🏈 SD Sports Decals

A simple, Python-generated website for selling custom **sports decals**.  
This site is built with a Python script that creates static HTML files for easy hosting on **GitHub Pages**.

---

## 🚀 How to Run

1. Clone or download this repo:
   ```bash
   git clone https://github.com/<your-username>/sd-decals.git
   cd sd-decals
python generate_site.py
