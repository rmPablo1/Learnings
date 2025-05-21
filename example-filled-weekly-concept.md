
# 📚 Weekly Coding Concept – GitHub Actions CI/CD

## 📅 Week: 2025-05-20 to 2025-05-26
## 🧩 Topic: Automating Testing and Deployment with GitHub Actions

---

## 🎯 Goal
Set up a basic GitHub Actions pipeline that runs tests on every push to the `main` branch and automatically deploys a static site to GitHub Pages.

---

## 📚 Resources Used
- [x] [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [x] [GitHub Actions – FreeCodeCamp Video](https://www.youtube.com/watch?v=R8_veQiYBjI)
- [x] [actions/starter-workflows](https://github.com/actions/starter-workflows)

---

## 📁 Project Structure
```bash
.
├── .github/
│   └── workflows/
│       └── ci.yml
├── app/
│   ├── index.html
│   └── styles.css
├── README.md
```

---

## 🛠️ Hands-on Activity
Set up GitHub Actions CI pipeline:
- Triggered on push to `main`
- Installs dependencies
- Runs basic test script
- Deploys to GitHub Pages on successful build

```yaml
name: CI/CD

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '18'
      - run: npm install
      - run: npm run test

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./app
```

---

## ✍️ What I Learned
- GitHub Actions workflows are written in YAML and stored in `.github/workflows`
- Actions are reusable blocks to handle tasks like checking out code, setting up Node, etc.
- CI/CD automation saves time and ensures consistency

---

## 📦 Output
- ✅ CI pipeline runs on each push
- ✅ Static site deployed to GitHub Pages
- 💡 Could add Slack notification for failed builds next

---

## 🔁 Reflection
- **What went well:** Setup was simple using documentation and examples
- **Challenges faced:** YAML indentation errors; learning the GitHub Actions syntax
- **Confidence level (1–5):** ⭐️⭐️⭐️⭐️

---

## 🔜 Next Topic
> Terraform – Launch an EC2 instance with infrastructure as code
