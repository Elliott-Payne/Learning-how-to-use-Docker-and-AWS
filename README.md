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

<br>
</details>

# [Using ECS to deploy a Docker app to AWS](https://www.youtube.com/watch?v=zs3tyVgiBQQ)

<details open>
<summary> How to install AWS CLI </summary>
<br>
The AWS Command Line Interface (CLI) is a tool that lets you manage AWS services and resources through a command line. Here's a step-by-step guide to install the AWS CLI on your computer.

#### Step 1: Check System Requirements

- Ensure your system meets the minimum requirements for installing the AWS CLI. The AWS CLI is compatible with Windows and macOS.

#### Step 2: Download the Installer

- **Windows:**
  - Download the installer from the [AWS CLI MSI Installer for Windows](https://awscli.amazonaws.com/AWSCLIV2.msi).
- **macOS:**
  - Download the installer from the [AWS CLI pkg Installer for macOS](https://awscli.amazonaws.com/AWSCLIV2.pkg).

#### Step 3: Install the AWS CLI

- **Windows:**
  - Run the downloaded MSI installer and follow the on-screen instructions.
- **macOS:**
  - Run the downloaded pkg installer and follow the on-screen instructions.

#### Step 4: Verify the Installation

- After installation, verify that the AWS CLI is installed correctly by opening a terminal or command prompt and typing:
  ```sh
  aws --version
  ```
  - You should see the version of the AWS CLI that you have installed.


#### Additional Tips

- **AWS Documentation:** For more detailed information and troubleshooting, refer to the [AWS CLI User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).
- **AWS IAM:** Ensure your AWS IAM user has the necessary permissions to perform actions with the AWS CLI. This will be explained in a later section.

</details>

<details open> 
<summary> Creating an IAM User and Granting Permissions for AWS CLI </summary>
<br>

Creating a user in AWS Identity and Access Management (IAM) and granting it the necessary permissions to use AWS CLI is essential for secure and efficient management of AWS resources. Follow these steps to set up an IAM user with the appropriate permissions.

#### Step 1: Sign in to AWS Management Console

- Go to the [AWS Management Console](https://aws.amazon.com/console/) and sign in with your root account or an existing IAM user with administrative permissions.

#### Step 2: Navigate to IAM

- In the AWS Management Console, search for "IAM" in the search bar and select "IAM" to open the IAM Dashboard.

#### Step 3: Create a New IAM User

1. **Click on Users:**
   - In the left-hand sidebar, click on "Users."
2. **Add User:**
   - Click the "Add user" button at the top of the page.
3. **Set User Details:**
   - **User Name:** Enter a username for the new user (e.g., `cli-user`).
   - **Access Type:** Check the box for "Access key - Programmatic access" to enable the user to use the AWS CLI, SDK, and API.

#### Step 4: Set Permissions

1. **Attach Policies Directly:**
   - Select "Attach existing policies directly."
2. **Choose Policies:**
   - For basic CLI usage, you can attach the following policies:
     - use `AdministratorAccess`, but be cautious as it grants full access to all AWS resources.
3. **Click Next:**
   - Click "Next: Tags" (optional to add tags).
4. **Review:**
   - Review the user details and attached policies. Click "Create user."

#### Step 5: Download Credentials

- After creating the user, you will see a success message with the user's
- Click `create access key`
  - **Important:** Download the `.csv` file containing the credentials or copy the Access Key ID and Secret Access Key to a secure location. `You won't be able to see the Secret Access Key again.`
   </details>

<details open>
  <summary> Uploading a Dockerized app to AWS ECR </summary>
<br>

AWS Elastic Container Registry (ECR) is a managed container image registry service. This guide will walk you through the steps to upload a Dockerized app to AWS ECR.

#### Prerequisites

- An AWS account
- Docker installed on your local machine
- AWS CLI installed and configured on your local machine
- Your Dockerized application

#### Step 1: Create an ECR Repository

1. **Sign in to AWS Management Console:**
   - Go to the [AWS Management Console](https://aws.amazon.com/console/) and sign in.
2. **Navigate to ECR:**
   - In the AWS Management Console, search for "ECR" in the search bar and select "Elastic Container Registry."
3. **Create a Repository:**
   - Click on "Repositories" in the left-hand sidebar.
   - Click the "Create repository" button.
   - **Repository Name:** Enter a name for your repository (e.g., `my-app`).
   - Click "Create repository."

#### Step 2: Authenticate Docker to Your ECR Registry

You have created a IAM User, gave it the correct permissions, created a repo, now it is time to login to your accounts using the terminal and use the given commands to build the app inside the cluster.

1. **Navigate to your ECR repositories:**
   - click on the name of your repo
   - click on `View push commands`
   - **These are the commands you are going to use to login, and build your app. Copy and paste them into your terminal**
     
2. **Run the push commands:**
   - Run the following AWS CLI command to authenticate Docker to your ECR registry:
     ```sh
     aws ecr get-login-password --region <your-region> | docker login -u AWS -p $(aws ecr get-login-password --region <region>)<account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app
     ```

#### Step 3: Navigate to Your App Directory

1.  In your terminal or command prompt, navigate to the directory containing your Dockerized app (where the `Dockerfile` is located).
2.  **Build the Docker Image:**
    - Run the following command to build your Docker image:
      ```sh
      docker build -t my-app .
      ```
    

#### Step 4: Tag Your Docker Image

- Tag your Docker image with the ECR repository URI:
  ```sh
  docker tag my-app:latest <account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app:latest
  ```

#### Step 5: Push Your Docker Image to ECR

- Push the tagged image to your ECR repository:
  ```sh
  docker push <account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app:latest
  ```
  
### Step 6: Copy the image URL and save it somewhere for later.

- `It will be used in a later step.`

</details>

<details open>
<br>
<summary> Creating a Cluster in AWS ECS </summary>

Amazon Elastic Container Service (ECS) is a highly scalable container management service that makes it easy to run, stop, and manage Docker containers on a cluster. This guide will walk you through the steps to create an ECS cluster using the AWS Management Console.

#### Step 1: Navigate to Amazon ECS

- In the AWS Management Console, search for "ECS" in the search bar and select "Elastic Container Service" to open the ECS Dashboard.

#### Step 2: Create a New Cluster

1. **Open the Clusters Page:**

   - Click on "Clusters" in the left-hand sidebar.
   - Click the "Create Cluster" button.

2. **Name the Cluster:**
3. **Leave Everything else Default**
4. **Adding a tag is optional**
5. **Click `create` at the bottom right of the screen**

#### Step 3: Add Capacity Provider
- After the cluster is created, you’ll be redirected to the cluster’s detail page where you can see information about your cluster, including cluster name, status, and other configurations.
  1. Click the name of your cluster
  2. Click `Update Cluster` in the top right
  3. Click `Add Capacity Provider`
  4. Select `Fargate` under Capactiy Provider
  5. Click `Update` on the bottom right
</details>

<details open>
<summary> Using EventBridge </summary>
<br>

</details>
