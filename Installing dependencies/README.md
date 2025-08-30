Installing Dependencies

The first step in preparing your Azure DevOps pipeline is to ensure that all required dependencies are installed. These dependencies are necessary for running tasks and tools that will be used later in the project. For our setup, we need Docker, Azure CLI, and Terraform installed in the Linux agent.

Step 1: Add Tasks to the Pipeline
Begin by adding tasks in your Azure Pipeline that will handle the installation of the required dependencies. These tasks will automate the process of setting up the environment for your builds and deployments.

Step 2: Install Docker
Docker is required for creating, managing, and running containerized applications. Add a task to your pipeline to install Docker on the Linux agent. Once installed, Docker will allow you to build and run container images as part of your pipeline execution.

<img width="1920" height="1080" alt="Screenshot from 2025-08-23 13-59-16" src="https://github.com/user-attachments/assets/2cf3b7e9-4e77-4f7e-bca2-7703e9f6495d" />

Step 3: Install Azure CLI
Azure CLI is the command-line tool used to manage Azure resources directly from the Linux system. Add a task to install Azure CLI in your agent. After installation, you will need to run the login command once to provide the system with access to your Azure subscription. This step is crucial for enabling your pipeline to interact with Azure services.

Step 4: Install Terraform
Terraform is required for automating infrastructure deployment. In this step, add a task to install Terraform version 1.1.8 in the Linux agent. Terraform will allow you to define and provision infrastructure resources using configuration files.

<img width="1857" height="958" alt="Screenshot from 2025-08-30 20-51-01" src="https://github.com/user-attachments/assets/b94161fe-6125-425a-a350-b802e59bd622" />

Step 5: Pull Required Docker Images
Finally, add a task to pull all the necessary Docker images that will be used in subsequent stages of your pipeline. Examples include security scanning tools, linting tools, and cost analysis tools. By pulling these images in advance, your pipeline will be ready to execute tasks without delays caused by image downloads during runtime.


