# Day 01 - Lab Preparation & Environment Setup

## Objective

Prepare the lab environment for building the Wazuh Blue Team Detection Platform.

---

## Host Machine

- Operating System: Windows 11
- Laptop: Dell Inspiron 15 3511
- RAM: 16 GB

---

## Virtual Machines

### Ubuntu (Wazuh Server)

- Ubuntu 26.04 LTS
- RAM: 6 GB
- CPU: 2 vCPUs
- Disk: 60 GB
- Network: NAT

### Kali Linux (Attacker)

- RAM: 3 GB
- CPU: 2 vCPUs
- Disk: 50 GB
- Network: NAT

---

## Tasks Completed

### 1. Verified Ubuntu Installation

Commands used:

```bash
lsb_release -a
free -h
df -h
lsblk
```

Result:

- Verified Ubuntu installation.
- Confirmed memory allocation.
- Confirmed storage layout.
- Verified virtual disk expansion.

---

### 2. Expanded Ubuntu Storage

Commands used:

```bash
sudo growpart /dev/sda 2
sudo resize2fs /dev/sda2
```

Result:

- Expanded the root partition.
- Increased the filesystem from approximately 19 GB to 58 GB.

---

### 3. Created Project Structure

Created folders:

- architecture
- attack-simulation
- diagrams
- docs
- reports
- rules
- screenshots
- scripts

Created files:

- README.md
- docs/Day01.md
- docs/Day02.md

---

### 4. Git & GitHub Setup

Completed:

- Installed Git.
- Configured Git username and email.
- Initialized local Git repository.
- Created GitHub repository.
- Connected local repository to GitHub.
- Created first commit.
- Successfully pushed project to GitHub.

Commands learned:

```bash
git init
git status
git add .
git commit -m "Initialize Wazuh Blue Team Detection Lab project structure"
git remote add origin <repository-url>
git remote -v
git push -u origin main
```

---

## Key Concepts Learned

### Linux

- Virtual disks
- Partitions
- Filesystems
- Storage expansion
- System verification commands

### Git

- Repository initialization
- Staging changes
- Creating commits
- Remote repositories
- Pushing code to GitHub

### GitHub

- Creating repositories
- Authentication using Git Credential Manager
- Connecting local and remote repositories

### Project Organization

- Professional folder structure
- Daily documentation
- Version control workflow

---

## Challenges Faced

- Ubuntu storage remained at 19 GB after increasing the VMware virtual disk.
- Learned that expanding a virtual disk does not automatically expand the Linux partition or filesystem.
- Corrected documentation file locations in VS Code.
- Successfully authenticated Git with GitHub.

---

## Outcome

- Ubuntu server is ready for Docker installation.
- GitHub repository has been initialized.
- Project documentation structure has been created.
- Development environment is fully prepared.

---

## Next Steps (Day 02)

- Update Ubuntu
- Install Docker Engine
- Install Docker Compose
- Verify Docker installation
- Deploy the Wazuh stack