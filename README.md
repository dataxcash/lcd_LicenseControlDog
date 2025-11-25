# LCD – License Control Dog

This repository hosts:

- **`release/`** – platform-specific LCD binaries ready for distribution.
- **`docs/`** – the static website for LCD, intended to be served via GitHub Pages.

> Note: The implementation details of LCD itself are **not** part of this repository and remain closed-source. This repo only contains release artifacts and public documentation.

---

## Overview

LCD (License Control Dog) is a lightweight, cross‑platform license enforcement agent designed to run close to your applications. It integrates with:

- **LCC – License Control Center** for local license management and observability.
- **LMF – License Management Framework / Server** for upstream license provisioning and activation.

At a high level, LCD focuses on:

- Enforcing license terms on the client side.
- Providing a secure, minimal interface to check license status.
- Working in both **online** and **intermittent/offline** scenarios (depending on how it is configured together with LCC/LMF).

This repository gives you:

- Downloadable LCD binaries for different operating systems.
- A public website that introduces LCD and explains how to obtain, deploy, and operate it without exposing internal implementation details.

---

## Repository structure

```text
lcd_website/
├── release/        # Platform-specific executables (filled by release process)
├── docs/           # Static website (served by GitHub Pages)
└── README.md       # This file
```

### `release/`

The `release/` directory is the canonical place to store packaged executables for:

- Linux (various architectures)
- Windows
- macOS

Typical layout (subject to change depending on your release process):

```text
release/
├── linux-amd64/
├── linux-arm64/
├── windows-amd64/
└── darwin-arm64/
```

Binaries in this folder are usually produced by the internal build/release pipeline and then pushed to this repository (or attached to GitHub Releases) for convenient distribution.

> Security note: If you distribute production binaries here, you should also consider publishing checksums (e.g. SHA256) and, if applicable, signatures.

### `docs/`

The `docs/` directory contains a static website for LCD. It is intended to be published via **GitHub Pages** using the `docs/` folder as the Pages root.

The website focuses on:

- High-level product description.
- Supported platforms and basic deployment topologies.
- How LCD relates to LCC and LMF.
- User‑oriented guides (installation, upgrade, troubleshooting at a conceptual level).

It **intentionally avoids** describing:

- Internal algorithms or protocols.
- Source code structure or implementation details of LCD.
- Any information that would expose the inner workings of the protection mechanisms.

---

## Using this repository

### 1. Downloading LCD binaries

1. Navigate to the `release/` folder in this repository (or the corresponding GitHub Release).
2. Choose the subdirectory that matches your target platform.
3. Download the appropriate archive or executable.
4. Verify the checksum/signature if your release process provides them.

> The concrete file naming conventions and verification instructions should be documented by your internal release process.

### 2. Running the web docs locally

The `docs/` site is pure static HTML/CSS/JS, so you can:

- Open `docs/index.html` directly in a browser, or
- Serve it via any static HTTP server (such as `python -m http.server`, Nginx, Caddy, etc.).

Example (from the repo root):

```bash
python -m http.server --directory docs 8080
```

Then open `http://localhost:8080` in your browser.

### 3. Publishing via GitHub Pages

For a typical GitHub Pages setup using this repo:

1. Go to the repository settings in GitHub.
2. Navigate to **Pages**.
3. Select the branch you want to publish from (e.g. `master`/`main`).
4. Set the **source folder** to `/docs`.
5. Save and wait for GitHub Pages to deploy.

Once published, the LCD website will be available at your GitHub Pages URL and will serve the content from `docs/`.

---

## Development notes

This repository is intentionally minimal. Common customizations include:

- Updating the visual style and content of `docs/` to match your brand.
- Automating binary uploads into `release/` using CI/CD.
- Adding more end‑user‑oriented documentation pages under `docs/`.

When updating documentation, make sure you:

- Keep explanations high‑level and product‑focused.
- Do not disclose internal implementation details of LCD or any security‑sensitive mechanisms.

---

## License

The licensing of LCD binaries and related materials is governed by your organization’s licensing terms.

If you plan to publish this repository publicly, add an appropriate `LICENSE` file that reflects how the documentation and any public assets may be used.