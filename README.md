# www
[![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Enabled-24292F?style=plastic&logo=github&logoColor=white)](https://github.com/features/copilot)

Personal website

## Setup

This repository uses a Git submodule to include the Festival canvas application from the [festival2](https://github.com/jphinspace/festival2) repository.

### For Cloudflare Pages

Cloudflare Pages automatically initializes and updates submodules during deployment. No additional configuration is needed - just connect your repository and deploy.

### For local development

To clone this repository with the submodule:

```bash
git clone --recurse-submodules https://github.com/jphinspace/www.git
```

Or if you've already cloned the repository:

```bash
git submodule init
git submodule update
```

### Updating the festival2 submodule

To update the festival2 submodule to the latest version:

```bash
cd festival2
git pull origin main
cd ..
git add festival2
git commit -m "Update festival2 submodule"
```
