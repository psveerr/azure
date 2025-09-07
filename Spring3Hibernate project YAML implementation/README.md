I recently worked on setting up a CI pipeline in Azure DevOps for the Spring3Hibernate project (https://github.com/opstree/spring3hibernate).

The project was originally configured with a MySQL dependency, but instead of provisioning a database, I focused on ensuring a smooth build and artifact generation process.

Here’s what I implemented:

-Pipeline Setup

Configured a YAML pipeline in Azure DevOps

Used a self-hosted agent pool (veer-meow) with Java 8 and Maven pre-installed. Ensured compatibility with the existing project without modifying the source repo.

<img width="1565" height="925" alt="Screenshot from 2025-09-07 21-44-45" src="https://github.com/user-attachments/assets/5fdd101a-8ea5-469b-9b5b-9a418f7bab5f" />



-Build Process

Maven was used to compile and package the project

Successfully generated files in the target directory

<img width="1565" height="925" alt="Screenshot from 2025-09-07 21-44-45" src="https://github.com/user-attachments/assets/95457938-480b-48a2-a114-8bb6cdeb7730" />


Artifacts Management

Published the packaged files as Azure Pipeline Artifacts

This makes the output reusable across environments and further pipeline stages, while keeping the build process lightweight


-Verdict

 Even without a dedicated database service, pipelines can still deliver reliable, portable artifacts by adjusting build strategies. Leveraging Azure DevOps YAML pipelines and self-hosted agents provided flexibility and control over the build process.

 
