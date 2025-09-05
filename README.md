# ikatraev.github.io

This repository hosts my personal website, built with MkDocs and deployed via GitHub Pages.

- Site source lives in the `docs/` directory.
- GitHub Actions builds the site and deploys to the `gh-pages` branch.
- The site is available at: https://ikatraev.github.io

## Local development

Prerequisites:
* python CLI
  ```shell
  brew install python3
  brew install pipx
  ```
  
* mkdocs CLI 
  ```shell
  brew install mkdocs
  ```
  
* Create a virtual environment:
  ```shell
  python -m venv venv
  source venv/bin/activate 
  pip install mkdocs-material
  ```


Run the local server:
```shell
source venv/bin/activate
mkdocs serve
```

Then open http://127.0.0.1:8000

## Favicon generation

Convert the SVG favicon to ICO and place it into docs/assets/:
```shell
brew install inkscape imagemagick
mkdir -p docs/assets

# Rasterize to a large PNG first for fidelity
inkscape assets/favicon.svg --export-dpi=600 --export-type=png --export-filename=/tmp/favicon-512.png --export-width=512 --export-height=512

# Then create multi-resolution ICO (IMv7 uses `magick`)
magick /tmp/favicon-512.png -define icon:auto-resize=16,24,32,48,64,128,256 docs/assets/favicon.ico
```
