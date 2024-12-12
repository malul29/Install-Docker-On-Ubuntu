# Install-Docker-On-Ubuntu
![image](https://github.com/user-attachments/assets/4b0b72a5-b1c1-48d3-a32a-55f1540d4b3a)

# Install Docker on Ubuntu

Follow these steps to install Docker on an Ubuntu system.

## Prerequisites

- An Ubuntu system (20.04 or later is recommended).
- A user account with `sudo` privileges.

## Steps to Install Docker

1. **Update the Package Index**
   ```bash
   sudo apt update
   ```

2. **Install Required Packages - let apt use packages over HTTPS:**
   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add the GPG key for the official Docker repository to your system:**
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. **Set Up the Docker Repository**
   This will also update our package database with the Docker packages from the newly added repo.
   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
   ```

6. **Install Docker Engine**
   ```bash
   sudo apt update
   sudo apt install docker-ce
   ```

7. **Verify the Installation**
   ```bash
   sudo docker --version
   sudo docker run hello-world
   ```

   If Docker is installed successfully, the `hello-world` container will print a confirmation message.

## Optional: Manage Docker as a Non-root User

1. **Create a Docker Group**
   ```bash
   sudo groupadd docker
   ```

2. **Add Your User to the Docker Group**
   ```bash
   sudo usermod -aG docker $USER
   ```

3. **Apply Group Changes**
   Log out and log back in, or run:
   ```bash
   newgrp docker
   ```

4. **Test Non-root Access**
   ```bash
   docker run hello-world
   ```

## Uninstallation (if needed)

To remove Docker from your system, run:
```bash
sudo apt remove -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

## References

- [Docker Documentation](https://docs.docker.com/engine/install/ubuntu/)
- [Digital Ocean - How To Install and Use Docker on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
