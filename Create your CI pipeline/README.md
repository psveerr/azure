Create Your CI Pipeline

Step 1: Navigate to Pipelines
In your Azure DevOps project, go to the Pipelines section and click on Create Pipeline. This is where you will define the process for building and testing your code.

Step 2: Use the Classic Editor
Select the option to use the Classic Editor. This editor provides a step-by-step interface to help you set up your pipeline without needing to write configuration files manually.

<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-17-51" src="https://github.com/user-attachments/assets/e9ef255e-5a4c-486b-9f74-28eacde72ccd" />

Step 3: Select Your Repository
Choose the Azure Repos repository that you have already configured. This repository will serve as the source of code for your pipeline. Once selected, continue to the next step.

Step 4: Start with an Empty Job
For your first pipeline, choose the option for an Empty Job. This gives you a blank pipeline where you can add tasks according to your needs.

Step 5: Select the Agent Pool
Choose the agent pool that you have already configured. This pool contains the agents that will run the jobs defined in your pipeline. Selecting the correct pool ensures that your pipeline has the required environment to execute.

<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-18-11" src="https://github.com/user-attachments/assets/7364dab4-f442-4e7e-aa3e-a4e462137ce3" />

Step 6: Choose the Default Branch and Options
Select the default branch of your repository that you want the pipeline to work on, typically the main or master branch. You can also configure additional options here, such as cleaning the workspace before each run.

Step 7: Add Tasks to Your Pipeline
Once the pipeline is created, you can begin adding tasks to it. Navigate to the Add Tasks option and select from the available list of tasks such as build, test, or deployment. These tasks can be customized to match the requirements of your project.

<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-28-06" src="https://github.com/user-attachments/assets/4aee5ac2-d9c9-4e8b-bd1f-3d19090ce3be" />

