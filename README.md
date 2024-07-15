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

#### Step 5: Configure the AWS CLI
- Before you can use the AWS CLI, you need to configure it with your AWS credentials.
- In the terminal or command prompt, type:
  ```sh
  aws configure
  ```
  - You will be prompted to enter your AWS Access Key ID, Secret Access Key, default region name, and default output format. If you don't have an Access Key ID and Secret Access Key, you can create them in the AWS Management Console.

#### Additional Tips
- **AWS Documentation:** For more detailed information and troubleshooting, refer to the [AWS CLI User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).
- **AWS IAM:** Ensure your AWS IAM user has the necessary permissions to perform actions with the AWS CLI.

By following these steps, you should be able to install and configure the AWS CLI on your computer successfully.

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
     - `AmazonS3ReadOnlyAccess`: Grants read-only access to S3 buckets.
     - `AmazonEC2ReadOnlyAccess`: Grants read-only access to EC2 instances.
     - `IAMUserChangePassword`: Allows the user to change their own password.
   - For more comprehensive access, you might use `AdministratorAccess`, but be cautious as it grants full access to all AWS resources.
3. **Click Next:**
   - Click "Next: Tags" (optional to add tags).
4. **Review:**
   - Review the user details and attached policies. Click "Create user."

#### Step 5: Download Credentials
- After creating the user, you will see a success message with the user's Access Key ID and Secret Access Key.
  - **Important:** Download the `.csv` file containing the credentials or copy the Access Key ID and Secret Access Key to a secure location. **You won't be able to see the Secret Access Key again.**

#### Step 6: Configure the AWS CLI with New User Credentials
1. **Open Terminal or Command Prompt:**
   - On your computer, open a terminal or command prompt.
2. **Configure AWS CLI:**
   - Type the following command and press Enter:
     ```sh
     aws configure
     ```
   - Copy and Paste in the Access Key ID and press enter. Copy and paste the Secret Access Key and press enter. Enter in default region name of your choice (e.g., `us-west-1`), and default output format (e.g., `json`) when prompted.

By following these steps, you can create an IAM user with the necessary permissions to use the AWS CLI.
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
1. **Open Terminal or Command Prompt:**
   - On your local machine, open a terminal or command prompt.
2. **Run Authentication Command:**
   - Run the following AWS CLI command to authenticate Docker to your ECR registry:
     ```sh
     aws ecr get-login-password --region <your-region> | docker login -u AWS -p $(aws ecr get-login-password --region <region>)<account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app
     ```
   - Replace `<your-region>` with your AWS region (e.g., `us-west-1`).
   - Replace `<account-id>` with your AWS account ID.
   - Replace `<my-app>` with your preferred image name.

#### Step 3: Build Your Docker Image
1. **Navigate to Your App Directory:**
   - In your terminal or command prompt, navigate to the directory containing your Dockerized app (where the `Dockerfile` is located).
2. **Build the Docker Image:**
   - Run the following command to build your Docker image:
     ```sh
     docker build -t my-app .
     ```
   - Replace `my-app` with your preferred image name.

#### Step 4: Tag Your Docker Image
- Tag your Docker image with the ECR repository URI:
  ```sh
  docker tag my-app:latest <account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app:latest
  ```
  - Replace `my-app` with your image name.
  - Replace `<account-id>` with your AWS account ID.
  - Replace `<your-region>` with your AWS region.
  - Replace `latest` with your preferred tag (e.g., a version number).

#### Step 5: Push Your Docker Image to ECR
- Push the tagged image to your ECR repository:
  ```sh
  docker push <account-id>.dkr.ecr.<your-region>.amazonaws.com/my-app:latest
  ```
  - Replace `my-app` with your image name.
  - Replace `<account-id>` with your AWS account ID.
  - Replace `<your-region>` with your AWS region.
  - Replace `latest` with your tag.

By following these steps, you should be able to upload your Dockerized app to AWS ECR, making it accessible for deployment in AWS services like ECS or Kubernetes.

</details>

<details open>
<br>
<summary> Creating a Cluster in AWS ECS Using the AWS Management Console </summary>

Amazon Elastic Container Service (ECS) is a highly scalable container management service that makes it easy to run, stop, and manage Docker containers on a cluster. This guide will walk you through the steps to create an ECS cluster using the AWS Management Console.

#### Step 1: Navigate to Amazon ECS
- In the AWS Management Console, search for "ECS" in the search bar and select "Elastic Container Service" to open the ECS Dashboard.

#### Step 2: Create a New Cluster
1. **Open the Clusters Page:**
   - Click on "Clusters" in the left-hand sidebar.
   - Click the "Create Cluster" button.

2. **Select a Cluster Template:**

  - **EC2 Linux + Networking:** we will manage our own EC2 instances for running containers.

3. **Configure Cluster:**

##### For EC2 Linux + Networking
1. **Cluster Name:**
   - Enter a name for your cluster (e.g., `my-ec2-cluster`).
2. **Provisioning Model:**
   - Select the provisioning model (e.g., On-Demand or Spot Instances).
3. **EC2 Instance Type:**
   - Select the EC2 instance type (e.g., `t2.micro`). (this is free tier eligible) 
4. **Number of Instances:**
   - Select 1
     - This specifies the number of instances for your cluster.
6. **Networking:**
   - Choose the default VPC and subnets.
7. **Enable Auto-Assign IP**
9. **Create:**
   - Click the "Create" button to create the cluster.

#### Step 3: View Your Cluster
- After the cluster is created, you’ll be redirected to the cluster’s detail page where you can see information about your cluster, including cluster name, status, and other configurations.

By following these steps, you should be able to create a cluster in AWS ECS using the AWS Management Console, ready to run and manage your Docker containers.</summary>
