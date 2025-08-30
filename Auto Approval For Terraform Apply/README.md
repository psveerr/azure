Step 1: Pre-deployment conditions

Under Pre-deployment conditions, select After Release. This means the Apply pipeline will be triggered automatically as soon as the Release Artifact is generated.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-01-39" src="https://github.com/user-attachments/assets/ca192e0c-bced-4fe5-8537-c07b6ee19a27" />


Step 2: Deploy Pipeline

The deploy pipeline will contain the following steps.

Step 3: Install Terraform

In this step, Terraform (version 1.1.8) will be installed as a dependency.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-04-08" src="https://github.com/user-attachments/assets/dd9a7eae-e586-4311-8dc7-6da377252dfb" />


Step 4: Terraform INIT

This step will initialize the Terraform code in the system. It will also fetch information from the remote state file stored in Azure Blob Storage. For this, an active Azure Subscription ID is required.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-04-13" src="https://github.com/user-attachments/assets/e208bb1b-262e-4665-b1f1-75c99dca85bb" />


Step 5: Terraform APPLY

In the final step, Terraform will automatically apply all the desired configurations and deploy resources into the cloud.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 23-04-20" src="https://github.com/user-attachments/assets/dfa3ba43-6f0c-40c7-bdbe-f03b35486176" />
