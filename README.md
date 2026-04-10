# Green Computing Workshop Site

Static Hugo website for the workshop:

**A (very) brief introduction to green computing practices**

## Local development

1. Start the local server:
   ```bash
   hugo server
   ```
2. Open the URL shown in your terminal (usually `http://localhost:1313/`).

## Build

```bash
hugo --gc --minify
```

## GitHub Pages deployment

This repository includes a GitHub Actions workflow at `.github/workflows/hugo.yml`.

After you push to the `main` branch and enable **GitHub Pages -> Source: GitHub Actions**, the site will publish as a project site.

Set `baseURL` in `hugo.toml` to:

`https://<YOUR_GITHUB_USERNAME>.github.io/green-computing-workshop/`
