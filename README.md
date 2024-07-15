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
  1. Download the installer from the [AWS CLI MSI Installer for Windows](https://awscli.amazonaws.com/AWSCLIV2.msi).
- **macOS:**
  1. Download the installer from the [AWS CLI pkg Installer for macOS](https://awscli.amazonaws.com/AWSCLIV2.pkg).

#### Step 3: Install the AWS CLI
- **Windows:**
  1. Run the downloaded MSI installer and follow the on-screen instructions.
- **macOS:**
  1. Run the downloaded pkg installer and follow the on-screen instructions.

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

