To install LiveKit on Amazon Linux 2023, follow these steps:

### Step 1: Update the System
Start by updating your system packages:

```bash
sudo dnf update -y
```

### Step 2: Install Docker
Amazon Linux 2023 uses `dnf` as the package manager. Install Docker with the following command:

```bash
sudo dnf install docker -y
```

### Step 3: Start Docker Service
Once Docker is installed, start and enable the Docker service to run on boot:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 4: Add User to Docker Group
Add your user to the `docker` group to allow running Docker commands without `sudo`:

```bash
sudo usermod -aG docker $USER
```

Log out and back in to apply the group changes.

### Step 5: Install Docker Compose
Docker Compose is necessary to run LiveKit. Install Docker Compose by downloading it directly:

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

Verify the installation:

```bash
docker-compose --version
```

### Step 6: Download the LiveKit Docker Compose File
Fetch the `docker-compose.yml` file for LiveKit:

```bash
curl -O https://raw.githubusercontent.com/livekit/livekit/main/docker-compose.yml
```

### Step 7: Start the LiveKit Server
Use Docker Compose to start LiveKit:

```bash
sudo docker-compose up -d
```

This command pulls the necessary Docker images and starts the LiveKit server.

### Step 8: Verify the Installation
Check the status of the running Docker containers to ensure LiveKit is running:

```bash
sudo docker ps
```

You should see LiveKit listed among the running containers.

### Step 9: Access LiveKit
LiveKit should be accessible via your server's public IP address on port 7880:

```
http://your-server-ip:7880
```

Replace `your-server-ip` with the actual public IP address of your EC2 instance.
