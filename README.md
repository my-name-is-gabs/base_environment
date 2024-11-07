# base_environment
troubleshooting my base_env

## Installation

Installing docker engine 27.1.2

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

   


    
