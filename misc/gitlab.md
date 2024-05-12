# GitLab Docker Server Windows Setup

Before you start, make sure you have Administrator access and either Windows Enterprise or Pro version. You may also need BIOS access.

---

## Enable Hyper-V

 - Use the Windows Search to find `Turn Windows features on or off`
 - Enable Hyper-V
 - Restart your computer

---

## Download & Install Required Applications
**Required**:

**Ubuntu** from Windows Store
**Windows Terminal** from Windows Store
**Docker Desktop Installer**
**WSL2 Linux Kernel Update Package for x64 Machines**

---

## WSL Setup

Run Powershell as administrator:

```sh
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
# Reboot after WSL installs
wsl --install
```

Ensure you have installed the `WSL Linux Kernel Update` before proceeding. Then run:

```sh
wsl --install -d Ubuntu
# Close the window that opens
wsl --set-version Ubuntu 2
```

Ensure you have installed `Docker Desktop` before proceeding. Then run:

```sh
net localgroup docker-users $env:username /add
```

Helpful commands:

```sh
# View installed distros
wsl -l -o
# View WSL versions
wsl -l -v
```

---

## Ubuntu Setup & Mounting NAS

Open the Ubuntu terminal & setup your user profile (username/password)

```sh
sudo apt update && sudo apt upgrade
sudo apt install nfs-common
sudo mkdir /nfs
sudo mkdir /nfs/syn
sudo chmod -R 755 /nfs/syn
sudo usermod -aG docker username
sudo chown -R :docker /nfs/syn
sudo chmod -R g+rwx /nfs/syn
sudo mount -t nfs <nas-ip-address>:/volume1/gitlabhome /nfs/syn
```

---

## Install the GitLab EE Image

> The GitLab Enterprise Edition software does not actually require you to have a license to use it. If you do not supply a license after installation, it will automatically show you the GitLab Community Edition feature set instead.

> The primary reason someone might download the Community Edition is if they prefer to only download open source software. For more information on GitLab’s licensing, review the GitLab article on this subject. To download the GitLab CE Docker image, run this command:

```sh
sudo docker pull gitlab/gitlab-ce:<latest || version-tag>
```

It may take a few minutes to download the image. When the download is complete, you can view a list of all installed Docker images with the images command:

```sh
sudo docker images
```

---

## GitLab Setup

```sh
# Pull GitLab Image 16.1.2
sudo docker pull gitlab/gitlab-ee:16.1.2-ee.0
```

**Docker-Compose Configuration**
```yml
version: '3.8'

services:
  gitlab:
    image: 'gitlab/gitlab-ee:16.1.2-ee.0'
    restart: always
    hostname: 'serveripgoeshere'
    ports:
      - '80:80'
      - '443:443'
      - '22:22'
    volumes:
      - /nfs/syn/config:/etc/gitlab
      - /nfs/syn/logs:/var/log/gitlab
      - /nfs/syn/data:/var/opt/gitlab
    shm_size: '256m'
```

```sh
sudo docker exec -it <container-id> grep 'Password:' /etc/gitlab/initial_root_password
```


```sh
# Inject Backup into Container
docker cp YYYY_MM_DD_VERSION_gitlab_backup.tar <container-id>:/var/opt/gitlab/backups/YYYY_MM_DD_VERSION_gitlab_backup.tar
```

```sh
# Issue GitLab Restore
docker exec -it <container-id> gitlab-backup restore BACKUP=YYYY_MM_DD_VERSION
```

---

## GitLab Backup Creation & Export

```sh
# Backup Create
sudo docker exec -it <container-id> gitlab-backup create
```

```sh
# Backup Export
sudo docker cp <container-id>:/var/opt/gitlab/backups/LATEST_VERS-ee_gitlab_backup.tar YYYYMMDD_gitlab_backup.tar
```

```sh
# Minor Upgrade Container 
sudo docker exec -it <container-id> apt
sudo docker exec -it <container-id> apt install gitlab-ee=15.11.11-ee.0
sudo docker exec -it <container-id> gitlab-ctl reconfigure
sudo docker exec -it <container-id> gitlab-ctl restart
```

---

```sh
# Major Upgrade Container (must be latest minor version)
sudo docker exec -it <container-id> apt update && apt install gitlab-ee
```

---

```sh
# Check Version
sudo docker exec -it <container-id> gitlab-rake gitlab:env:info
```

