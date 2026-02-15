# Docker Git Auto-Pusher

> [!CAUTION]
> This tool uses `git push --force` and automated merge strategies. 
> **Always maintain your own backups.** Use at your own risk.** Read the full [Disclaimer](https://github.com/AlexHolly/docker-git-auto-pusher/blob/main/DISCLAIMER.md).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Docker](https://img.shields.io/badge/docker-ready-blue.svg)](https://www.docker.com/)
[![Git](https://img.shields.io/badge/git-automated-orange.svg)](https://git-scm.com/)

Automated Git backups with intelligent merge conflict resolution for file-based projects (e.g., Obsidian vaults).

## Features

- 🔄 **Automatic daily backups** to GitHub (customizable schedule)
- 🛡️ **Smart merge conflict resolution** - preserves both versions when conflicts occur
- 🔑 **Automatic SSH key generation** with clear instructions
- 💾 **Persistent storage** - your data stays on your host
- ⚡ **Runs on any system with Docker** (Synology, NAS, Linux, etc.)
- 📁 **Works with any folder** - not just Obsidian vaults

## Quick Start
   
1. **Host Directories Configuration**

    **Set Path in docker-compose**

    ```docker-compose
        volumes:
          - /volume1/docker/obsidian/repo:/repo
          - /volume1/docker/obsidian/ssh:/root/.ssh
    ```
    
    **Create directories on your host**
   
    ```bash
    mkdir -p /volume1/docker/obsidian/repo
    mkdir -p /volume1/docker/obsidian/ssh
    ```

1. **Set Repo Configuration**

    ```docker-compose
    environment:
      - GIT_EMAIL="your.email@example.com"
      - GIT_NAME="Your Name"
      - GIT_REPO=git@github.com:username/repo.git
      - CRON_SCHEDULE=0 3 * * *
      - TZ=Europe/Berlin
    ```

2. **Start Docker Container**

   ```sh
   docker-compose up -d
   ```

3. Copy SSH Key from docker protocol to GitHub (`Account -> Settings -> SSH and GPG keys -> New SSH Key`)

### Obsidian Vault
1. Choose SMB (Server Message Block) `/volume1/docker/obsidian/reporepo` folder as obsidian vault
2. By default it will push to GitHub once a day
   
