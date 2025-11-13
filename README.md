# SD Decals — Static Site for GitHub Pages

This project creates a clean, one-page website to sell **sports decals** using a Python static site generator. The website includes a custom **SD logo**, sample products, and ready-to-publish HTML/CSS files.

---

## 🚀 Getting Started

Follow these steps to build and host your site live on **GitHub Pages**.

---

### 🧰 1. Requirements

You’ll need:
- A [GitHub account](https://github.com)
- **Python 3.8+** installed → check:
  ```bash
  python --version
  ```
- **Git** installed → [https://git-scm.com](https://git-scm.com)

---

### ⚙️ 2. Set Up the Project

1. **Create a folder** for your project:
   ```bash
   mkdir sd-decals
   cd sd-decals
   ```

2. **Add the project files**:
   - `generate_site.py`
   - `templates/index_template.html`
   - `data/products.json`
   - `static/style.css`
   - `static/logo.svg`
   - (Optional) `static/placeholder.png`

3. **Generate your site**:
   ```bash
   python generate_site.py
   ```

   ✅ This creates a folder named `site/` that contains your complete website.

---

### 🧩 3. Create a GitHub Repository

1. Go to [https://github.com/new](https://github.com/new)
2. Name it **sd-decals** (or any name you like)
3. Choose **Public**
4. Leave README and .gitignore unchecked
5. Click **Create Repository**

---

### 🪶 4. Upload Your Site

In your terminal, from inside the generated `site/` folder:

```bash
cd site
git init
git add .
git commit -m "Initial commit — SD Decals site"
git branch -M main
git remote add origin https://github.com/<your-username>/sd-decals.git
git push -u origin main
```

*(Replace `<your-username>` with your actual GitHub username.)*

---

### 🌐 5. Enable GitHub Pages

1. On your GitHub repo, go to **Settings → Pages**
2. Under **Source**, choose:
   - Branch: `main`
   - Folder: `/ (root)`
3. Click **Save**

Wait 1–2 minutes — then your site will be live at:

```
https://<your-username>.github.io/sd-decals/
```

---

### 🧩 6. Customize Your Site

- **Add your own decals** → edit `data/products.json`
- **Replace logo** → edit `static/logo.svg`
- **Change colors and layout** → modify `static/style.css`
- **Update text or sections** → edit `templates/index_template.html`

To apply changes, re-run:
```bash
python generate_site.py
```
and re-push the new `site/` folder.

---

### 💡 Tips
- Keep product images under `static/`
- Use descriptive filenames like `helmet-decal.png`
- Commit and push regularly to save your work

---

**Author:** SD Decals Project  
**License:** MIT  
**Live Demo (after setup):** `https://<your-username>.github.io/sd-decals/`

