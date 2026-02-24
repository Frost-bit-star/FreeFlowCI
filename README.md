# FreeFlowCI 🚀

Automated deploy to InfinityFree using LFTP.

### Usage

Add this workflow in your repo:

```yaml
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

### Setup

Go to Repository → Settings → Secrets → Actions

### Add:

- FTP_USER

- FTP_PASS

Push to main and deploy automatically.

## Security

- Uses GitHub encrypted secrets

- Credentials never leave GitHub runner

- Server is hardcoded: ftpupload.net
