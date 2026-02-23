# JSON Resume - Romain KOENIG

Professional resume built with [JSON Resume](https://jsonresume.org/), an open-source standard for creating machine-readable resumes.

## 📋 About

This repository contains my professional resume in JSON format, following the [JSON Resume Schema v1.0.0](https://github.com/jsonresume/resume-schema). The resume data is stored in `resume.json` and can be exported to various formats (HTML, PDF, etc.) using the resume-cli tool.

**Theme**: [Elegant](https://github.com/mudassir0909/jsonresume-theme-elegant)

## 🚀 Quick Start

### Prerequisites

- Node.js (v20 or higher recommended)
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/romain-koenig/json-resume.git
cd json-resume

# Install dependencies
npm ci
```

## 🔄 Deployment

This project uses **GitHub Actions** for automated deployment to an FTP server.

### Automatic Deployment

The resume is automatically built and deployed when:
- Code is pushed to the `main` branch
- Workflow is manually triggered from GitHub Actions tab

### Deployment Workflow

The CI/CD pipeline (`.github/workflows/deploy-ftp.yml`) performs:

1. ✅ Validates `resume.json` against JSON Resume schema
2. 🔨 Builds the HTML resume using the Elegant theme
3. 📤 Deploys `index.html` to the FTP server root

### Required GitHub Secrets

To enable FTP deployment, configure these secrets in your repository settings:

| Secret | Description |
|--------|-------------|
| `FTP_HOST` | FTP server hostname |
| `FTP_USER` | FTP username |
| `FTP_PASS` | FTP password |

**Setup**: Go to `Settings` → `Secrets and variables` → `Actions` → `New repository secret`

### Manual Deployment

You can also deploy manually:

1. Build the resume: `npm run build`
2. Upload `dist/index.html` to your web server via FTP/SFTP

## 📝 Usage

### Validate the resume

Ensure your `resume.json` follows the JSON Resume schema:

```bash
npm run validate
```

### Build HTML version

Generate a static HTML version of the resume:

```bash
npm run build
```

The generated file will be available at: `dist/index.html`

### Preview in browser

One can open the generated HTML file directly:

```bash
# Linux
xdg-open dist/index.html

# macOS
open dist/index.html

# Windows
start dist/index.html
```

## 📁 Project Structure

```
json-resume/
├── .github/
│   └── workflows/
│       └── deploy-ftp.yml  # GitHub Actions CI/CD pipeline
├── resume.json          # Resume data (JSON Resume format)
├── package.json         # Project dependencies and scripts
├── dist/               # Generated files (HTML, PDF, etc.)
│   └── index.html      # Built HTML resume
└── README.md           # This file
```

## 🛠️ Available Scripts

| Command | Description |
|---------|-------------|
| `npm run validate` | Validates `resume.json` against JSON Resume schema |
| `npm run build` | Exports resume to HTML using the Elegant theme |

## 📚 JSON Resume Resources

- [JSON Resume Official Website](https://jsonresume.org/)
- [Schema Documentation](https://github.com/jsonresume/resume-schema)
- [Theme Gallery](https://jsonresume.org/themes/)
- [Resume CLI Documentation](https://github.com/jsonresume/resume-cli)

## 🎨 Themes

This project uses the **Elegant** theme. To use a different theme:

1. Install the theme package:
   ```bash
   npm install jsonresume-theme-[theme-name]
   ```

2. Update the build script in `package.json`:
   ```json
   "build": "mkdir -p dist && resume export dist/index.html --resume resume.json --theme [theme-name]"
   ```

Browse available themes at: https://jsonresume.org/themes/

## 🔄 Updating the Resume

1. Edit `resume.json` with updated information
2. Validate changes: `npm run validate`
3. Rebuild the HTML: `npm run build`
4. Commit and push the changes
5. CI/CD will deploy to [romainkoenig.com](https://romainkoenig.com)

---

*This resume is maintained using [JSON Resume](https://jsonresume.org/) - An open source initiative to create a JSON-based standard for resumes.*