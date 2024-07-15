<details open>
  <summary> How to Run a Docker Container on Your Computer </summary>


### Step 1: Install Docker
1. **Download Docker:**
   - Go to the [Docker website](https://www.docker.com/products/docker-desktop) and download Docker Desktop for your operating system (Windows, macOS, or Linux).

2. **Install Docker:**
   - Follow the installation instructions provided for your operating system. For most systems, this involves running the downloaded installer and following the prompts.

3. **Start Docker:**
   - Once installed, open Docker Desktop. It may take a few moments to initialize.

### Step 2: Open a Terminal or Command Prompt
- On Windows, you can use Command Prompt or PowerShell.
- On macOS and Linux, use the Terminal.

### Step 3: Verify Docker Installation
- Type the following command and press Enter to ensure Docker is installed correctly:
  ```sh
  docker --version
  ```
  - You should see the Docker version information if it’s installed correctly.

### Step 4: Pull a Docker Image
- Choose a Docker image to run. For this example, we’ll use the official `hello-world` image, which is a simple image to test Docker.
- Type the following command and press Enter:
  ```sh
  docker pull hello-world
  ```
  - This command downloads the `hello-world` image from the Docker repository.

### Step 5: Run a Docker Container
- Once the image is downloaded, you can run it in a container.
- Type the following command and press Enter:
  ```sh
  docker run hello-world
  ```
  - This command starts a new container from the `hello-world` image. If everything is set up correctly, you’ll see a message saying "Hello from Docker!" followed by some informational text.

### Step 6: Check Running Containers
- To see the list of currently running containers, type:
  ```sh
  docker ps
  ```
  - If there are no running containers, the list will be empty.

### Step 7: Stop and Remove Containers
- If you have running containers and you want to stop one, you can use:
  ```sh
  docker stop [container_id]
  ```
  - Replace `[container_id]` with the actual container ID, which you can get from the `docker ps` command.
  
- To remove a stopped container, use:
  ```sh
  docker rm [container_id]
  ```
  - Replace `[container_id]` with the actual container ID.

### Step 8: Remove Docker Image
- To clean up and remove the Docker image you downloaded, use:
  ```sh
  docker rmi hello-world
  ```

### Additional Tips
- **Docker Hub:** Explore other images on [Docker Hub](https://hub.docker.com/), where you can find official images for various applications.
- **Docker Documentation:** For more detailed information, refer to the [Docker documentation](https://docs.docker.com/).

By following these steps, you should be able to run a Docker container on your computer successfully.
<br>
</details>

# Using ECS to deploy a Docker app to AWS



