Now it’s time to deploy our Terraform code.
The Release (Terraform-CD) pipeline will only be triggered once the CI pipeline has successfully passed all checks. After the CI pipeline finishes, it generates a Release Artifact which auto-triggers the CD pipeline.

Step 1: Go to Release Pipeline under the Pipeline section and choose the latest artifact from the Terraform-CI pipeline.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 22-58-15" src="https://github.com/user-attachments/assets/982455af-2fc3-4a50-b92c-e975d654f7b2" />


Step 2: Configure the Continuous Deployment Trigger. Enable the CD trigger and set it to use the Main branch as the build branch.
<img width="1607" height="920" alt="Screenshot from 2025-08-30 22-57-38" src="https://github.com/user-attachments/assets/0c003152-d011-4b1f-b31d-ac696ac1b784" />
