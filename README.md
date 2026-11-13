<div align="center">

<img src="snap/gui/betterleaks.png" alt="Betterleaks logo" width="128" />

# Betterleaks

**Find leaked secrets in Git, files, code hosts and S3 buckets.**

[![betterleaks](https://snapcraft.io/betterleaks/badge.svg)](https://snapcraft.io/betterleaks)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Betterleaks](https://github.com/betterleaks/betterleaks), a scanner that finds and validates secrets in Git history, files, GitHub, GitLab and S3.

</div>

---

## Getting Started

<a href="https://snapcraft.io/betterleaks"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install betterleaks
cd ~/my-project
betterleaks git -v
```

Scan a GitHub organization and check which findings are still live:

```bash
GITHUB_TOKEN=<token> betterleaks github https://github.com/my-org --validation
```

## Configure

This snap has no `snap set` options, and Betterleaks keeps no data of its own.
Tokens and S3 keys come from flags or environment variables such as `GITHUB_TOKEN`, `GITLAB_TOKEN`, `HF_TOKEN` and `AWS_ACCESS_KEY_ID`.
The Git included in the snap reads its configuration from `~/snap/betterleaks/current`, not from your own `~/.gitconfig`.

For repositories under `/media` or `/mnt`:

```bash
sudo snap connect betterleaks:removable-media
```

## Limitations

- Repositories, files and reports must be in a normal folder under your home directory or on connected removable storage. Hidden folders directly under your home directory are not accessible, but hidden files inside a project, such as `.env`, are scanned.
- Credential files such as `~/.aws/credentials` are not read; pass keys through flags or environment variables.
- Remote sources are cloned over HTTPS only. Git cannot run host programs that a repository's configuration calls, such as a textconv driver or the Git LFS filter.

## Build

```bash
git clone https://github.com/sidalit/betterleaks-snap.git
cd betterleaks-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/betterleaks-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/betterleaks/betterleaks/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/betterleaks-snap/blob/main/LICENSE).
