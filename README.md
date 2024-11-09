# base_environment
troubleshooting my base_env

## New steps in installing docker 27.1.2
### Step 1: Download Docker Engine Version 27.1.2 Packages
1. Create a directory to store the .deb files:
```bash
mkdir -p ~/docker-install && cd ~/docker-install
```

2. Download the specific .deb files:
```bash
curl -O https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-ce_5%3A27.1.2~3-0~ubuntu-focal_amd64.deb
curl -O https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/docker-ce-cli_5%3A27.1.2~3-0~ubuntu-focal_amd64.deb
curl -O https://download.docker.com/linux/ubuntu/dists/focal/pool/stable/amd64/containerd.io_1.6.21-1_amd64.deb
```

### Step 2: Install Docker Packages
Once the .deb files are downloaded, you can install them in the following order:
```bash
sudo apt-get install ./containerd.io_1.6.21-1_amd64.deb
sudo apt-get install ./docker-ce-cli_5:27.1.2~3-0~ubuntu-focal_amd64.deb
sudo apt-get install ./docker-ce_5:27.1.2~3-0~ubuntu-focal_amd64.deb
```

### Step 3: Verify the Installation
To confirm Docker Engine 27.1.2 is installed, check the Docker version:
```bash
docker --version
```

### Step 4: Clean Up
```bash
rm -rf ~/docker-install
```

## Updated Steps for Installing Docker Compose 1.29.2 on WSL Ubuntu 20.04

1. Download Docker Compose: Use curl to download the binary into your user’s home directory first, which avoids permission issues.
 ```bash
 curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o ~/docker-compose
 ```

2. Move and Grant Permissions: Move the downloaded binary to /usr/local/bin and make it executable:
```bash
sudo mv ~/docker-compose /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
    
3. Verify the Installation: Confirm Docker Compose was installed by checking its version:
```bash
docker-compose --version
```

4. Alternative Installation Using Python (if needed):
 - If direct download still doesn’t work, you can install Docker Compose via pip (Python’s package manager):
  ```bash
  sudo apt-get install -y python3-pip
  sudo pip3 install docker-compose==1.29.2
  ```

<hr>

## Request Dependecy warning
Upgrade or Downgrade requests, urllib3, and chardet: First, try to upgrade the requests package along with urllib3 and chardet to compatible versions by running:

```bash
pip install --upgrade requests urllib3 chardet
```
This should ensure that all dependencies are aligned with compatible versions.

Install Specific Compatible Versions: If upgrading doesn’t work, try installing specific versions that are known to work together. For example, as of recent updates, the following versions are often compatible:

```bash
pip install requests==2.31.0 urllib3==1.26.16 chardet==3.0.4
````
Use requests with charset_normalizer Instead of chardet: Since requests has shifted to use charset_normalizer by default instead of chardet, you might avoid the issue by uninstalling chardet:

```bash
pip uninstall chardet
```
Verify the Installation: After making these changes, verify the installed versions to confirm compatibility:

```bash
pip show requests urllib3 chardet charset_normalizer
```


## From stackOverflow About Hypervisor
[solution](https://stackoverflow.com/questions/39684974/docker-for-windows-error-hardware-assisted-virtualization-and-data-execution-p#39989990)





   


    
