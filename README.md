# base_environment
troubleshooting my base_env

## Installing docker engine 27.1.2

1. Uninstall any older Docker versions (if installed):
```bash
  npm install my-project
  cd my-project
```

2. Update the apt package index and install prerequisites:
```bash
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

3. Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Set up the stable Docker repository:
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Update the apt package index again:
```bash
sudo apt-get update
```

6. Install a specific version of Docker Engine:
 - List available Docker versions to verify that 27.1.2 is available:
   ```bash
   apt-cache madison docker-ce
   ```
 - You should see a list of Docker versions. Look for 27.1.2~3-0~ubuntu-focal (or a similar tag).
   ```bash
   apt-cache madison docker-ce
   ```
 - Install version 27.1.2:
   ```bash
   sudo apt-get install docker-ce=27.1.2~3-0~ubuntu-focal docker-ce-cli=27.1.2~3-0~ubuntu-focal containerd.io
   ```

7. Verify the installation:
```bash
docker --version
```

8. Configure Docker to start on WSL boot (optional):
```bash
sudo systemctl enable docker
```

## Solving issues in installing docker-compose version 1.29.2

1. Check for Download and Permissions Errors:
   - Make sure the download command was successful. Run:
    ```bash
    ls -l /usr/local/bin/docker-compose
    ```
   - You should see the file docker-compose in /usr/local/bin with executable permissions (-rwxr-xr-x). If it’s not there, the download might have failed or permissions weren’t set correctly.

2. Re-run the Download and Permission Commands:
  - Retry downloading the binary and setting permissions in case there was a network issue or a typo:
    ```bash
    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    ```

3. Check the PATH:
  - If docker-compose is not found after installation, the path might not include /usr/local/bin. Add it to your PATH:
    ```bash
    echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
    source ~/.bashrc
    ```

4. Verify with Correct Command:
 - Double-check with this command to confirm installation:
   ```bash
   docker-compose --version
   ```

5. Alternative Installation Using Python (if needed):
 - If direct download still doesn’t work, you can install Docker Compose via pip (Python’s package manager):
  ```bash
  sudo apt-get install -y python3-pip
  sudo pip3 install docker-compose==1.29.2
  ```

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


## From stackOverflow
[solution](https://stackoverflow.com/questions/39684974/docker-for-windows-error-hardware-assisted-virtualization-and-data-execution-p#39989990)










   


    
