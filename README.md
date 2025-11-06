# RE-JOIN Portal Documentation

This repository hosts the official documentation for the **RE-JOIN Portal**, including user guides, tutorials, and developer references for the RE-JOIN multimodal imaging platform.

---

## Live Documentation

The documentation is automatically built and deployed with GitHub Pages:

**https://Cai-Lab-at-University-of-Michigan.github.io/RE_JOIN_PORTAL_WIKI/**

---

## Contributing

We welcome contributions! Please take a look at our [guide](CONTRIBUTING.md). 
If you would like to improve tutorials, add examples, fix broken links, or enhance layout and accessibility, feel free to open a pull request.

---

## Local Development & Preview

To build and preview the documentation locally:

### 0. Set Up Python Virtual Environment (Recommended)

```bash
python3 -m venv .venv
source .venv/bin/activate    # macOS / Linux
# OR
.\.venv\Scripts\activate     # Windows PowerShell
```

### 1. Install Dependencies

```bash
pip install mkdocs-material \
           mkdocs-minify-plugin \
           mkdocs-redirects \
           mkdocs-git-revision-date-localized-plugin \
           mkdocs-glightbox
```