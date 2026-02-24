### FreeFlowCI 🚀

Automate deploying your website or project to InfinityFree using LFTP.
Works for simple PHP sites, Node projects, and Python apps. Build your project in GitHub Actions and deploy automatically whenever you push code.

## Simple PHP website (no Composer)
```
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Frost-bit-star/FreeFlowCI@v1
        with:
          ftp_username: ${{ secrets.FTP_USER }}
          ftp_password: ${{ secrets.FTP_PASS }}
```
- This will deploy your plain PHP/HTML website to htdocs.

## PHP project with Composer
```
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Frost-bit-star/FreeFlowCI@v1
        with:
          ftp_username: ${{ secrets.FTP_USER }}
          ftp_password: ${{ secrets.FTP_PASS }}
          deploy_php: "true"
```
# FreeFlowCI will run composer install before uploading files.

### Node.js / Frontend project
```
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Frost-bit-star/FreeFlowCI@v1
        with:
          ftp_username: ${{ secrets.FTP_USER }}
          ftp_password: ${{ secrets.FTP_PASS }}
          deploy_node: "true"
```
FreeFlowCI will run npm install and npm run build (if a build script exists) before deploying.

## Python project
```
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Frost-bit-star/FreeFlowCI@v1
        with:
          ftp_username: ${{ secrets.FTP_USER }}
          ftp_password: ${{ secrets.FTP_PASS }}
          deploy_python: "true"
```
FreeFlowCI will run pip install -r requirements.txt before deploying.

# Setup

- Go to your Repository → Settings → Secrets → Actions

- Add your FTP credentials:

- FTP_USER → your InfinityFree FTP username

- FTP_PASS → your InfinityFree FTP password

Push to the main branch → FreeFlowCI will deploy automatically.

## Inputs / Options
# Input	Description	Default
- ftp_username	InfinityFree FTP username	Required
- ftp_password	InfinityFree FTP password	Required
- ftp_directory	Remote directory	htdocs
- deploy_php	Run composer install	"false"
- deploy_node	Run npm install & build	"false"
- deploy_python	Run pip install	"false"

**Optional flags allow advanced users to build projects before deployment. Defaults are safe for beginners.**

## Security

- Uses GitHub encrypted secrets

- Credentials never leave GitHub runner

Server is hardcoded: ftpupload.net
