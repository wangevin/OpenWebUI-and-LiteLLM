# Install Docker on Ubuntu 24.04

## Useful URL's
- [Docker Docs: Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
- [How to Install Docker on Ubuntu 24.04: Step-by-Step Guide](https://www.cherryservers.com/blog/install-docker-ubuntu)

## Step 1: Update the system and install dependencies
- In the terminal, enter the following
    ```bash
    sudo apt update
    sudo apt install curl apt-transport-https ca-certificates software-properties-common
    ```

## Step 2: Add the Docker APT repository to your system
To install the most current version of Docker, we need to install it from the official Docker repository.  So we need to add that repo to our system
- Sownload the Docker GPG key using the `curl` command
    ```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```
- Next, add the Docker APT repository to your system. The command creates a docker.list repository file in the /etc/apt/sources.list.d directory
    ```bash
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```
- Update the package index
    ```bash
    sudo apt update
    ```


## Step 3: Install Docker Community Edition
- Run the command
    ```bash
    sudo apt install docker-ce -y
    ```
- See if it's working
    ```bash
    sudo systemctl status docker
    ```

## Step 4: Add user to Docker group
- By default, only the root or sudo user can run Docker commands. To add the currently logged-in user, use the usermod command
    ```bash
    sudo usermod -aG docker $USER
    ```
- Next, run the `newgrp` command
    ```bash
    newgrp
    ```
- Verify
    ```bash
    groups $USER
    ```
- Log out and log back in, or reboot your system, to apply the group changes

## Step 4: Log back in and Test
- Verify the Docker Version
```bash
docker version
```
