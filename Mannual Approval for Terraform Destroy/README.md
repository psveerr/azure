Step 1: Pre-deployment conditions

Under pre-deployment conditions, permissions will be granted only to a small set of trusted individuals who can provide manual approval for Terraform Destroy.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-11-01" src="https://github.com/user-attachments/assets/0cecc9b4-6ba9-4cf7-a05e-ecd20f616d9e" />


Step 2: Pipeline steps

The destroy pipeline will include the following tasks.

Step 3: Install Terraform

Terraform version 1.1.8 will be installed as a dependency.

Step 4: Terraform INIT

This step initializes the Terraform code. It also retrieves information from the remote state file stored in Azure Blob Storage. For this step, an active Azure Subscription ID is required.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-14-22" src="https://github.com/user-attachments/assets/aa5754af-5e3d-4cd4-8d63-5e7f8387d63b" />



Step 5: Terraform DESTROY

In the final step, Terraform will automatically destroy all existing configurations and remove infrastructure from the cloud.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-14-26" src="https://github.com/user-attachments/assets/54a0ca23-521c-44bc-988e-9e06193a5c4b" />
