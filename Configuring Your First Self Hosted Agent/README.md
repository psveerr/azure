Configuring Your First Self-Hosted Agent

Step 1: Open Project Settings
In your Azure DevOps project, go to the bottom-left corner and click on Project Settings. This section allows you to manage configurations for pipelines, repositories, permissions, and agent pools.

Step 2: Navigate to Agent Pools
Inside Project Settings, locate the Pipelines section and click on Agent Pools. Agent pools are collections of agents that can be shared and used to run pipeline jobs.

Step 3: Create a New Pool for Self-Hosted Agents
Click on Add Pool and select the option for a Self-Hosted Agent. Creating a new pool allows you to organize and dedicate self-hosted agents for your builds and deployments.

Step 4: Add a New Agent to the Pool
Open the newly created pool and click on New Agent. You will be asked to select the operating system of the machine you want to configure. Choose the correct operating system and proceed with the instructions provided on screen.

Step 5: Configure Your Agent
After downloading and setting up the agent, you need to configure it. The configuration process will ask for your Azure DevOps organization details and requires a Personal Access Token (PAT). To generate this token, go to User Settings in the top-right corner of your Azure DevOps page and select Personal Access Tokens. Create a new token, give it a meaningful name, and assign the necessary permissions. Copy this token as it will not be visible again. If it is lost, a new one must be generated. During configuration, you will be prompted to provide the Azure DevOps URL, the PAT, the agent pool name, the agent name, and the work folder. Default values can be used if preferred.

Step 6: Start the Agent
Once the configuration is complete, start the agent to bring it online. The status of the agent will change from Offline to Online. At this point, your self-hosted agent is ready and can be used in your pipelines.

<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-22-05" src="https://github.com/user-attachments/assets/b930b3bb-a5ff-4475-bda4-e2a71dc3f95a" />
<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-22-39" src="https://github.com/user-attachments/assets/6b98830a-5586-4e2c-9219-9304b423dee1" />
<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-22-45" src="https://github.com/user-attachments/assets/f02fb2fc-2cec-47b6-9608-5a33b00f64ce" />
<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-23-23" src="https://github.com/user-attachments/assets/080a71a6-4bab-4483-ad5f-d1205f53b5b0" />
<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-25-11" src="https://github.com/user-attachments/assets/4b74feef-3730-48ad-97fa-35de733e784d" />
<img width="1920" height="1080" alt="Screenshot from 2025-08-23 12-25-49" src="https://github.com/user-attachments/assets/e3aa5e80-97b6-45a1-be2a-650f4f7e61b6" />
