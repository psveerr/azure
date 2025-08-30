Branching policies are required to protect the main/master branch from unwanted commits.
Any changes to the main/master branch can only be done through a Pull Request.

It is also important to note that the Terraform-CD (Release) pipeline will only be triggered if the Terraform-CI (Build) pipeline was triggered from the main branch.

Step 1

Navigate to Project Settings → Repositories and select the repository where your code is stored.
<img width="1865" height="963" alt="Screenshot from 2025-08-30 23-18-07" src="https://github.com/user-attachments/assets/3b7a92d5-6043-43d1-905f-574b79e72aba" />


Step 2: Branching Policy

After selecting the repository, go to the Policies section and scroll down.
<img width="1256" height="963" alt="Screenshot from 2025-08-30 23-19-13" src="https://github.com/user-attachments/assets/5020b33a-e28d-453c-81bb-2d1be62b47e2" />


Step 3: Configuring Branching Policy

Apply the required branching policies (such as restricting direct commits and enforcing pull requests). Once these changes are made, your branching policy will be active.
<img width="1579" height="963" alt="Screenshot from 2025-08-30 23-20-04" src="https://github.com/user-attachments/assets/9cd11888-0a66-4b33-8c9c-606e1ba9cd08" />
