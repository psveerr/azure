Step 1 involves adding the necessary steps in the Azure Pipeline to define how files and logs will be copied and stored as artifacts.

Step 2 focuses on copying files into the release directory. All Terraform configuration files with .tf and .tfvars extensions are moved to this directory so that they are grouped together and made available as part of the release artifact.

<img width="1602" height="862" alt="Screenshot from 2025-08-30 20-07-32" src="https://github.com/user-attachments/assets/6c8b52de-d5eb-4de2-963a-1ba048814735" />

Step 3 involves copying files into the report directory. This step collects all the generated log files, such as compliance logs and cost estimation reports, and places them in a separate location for easy reference and publishing.

<img width="1602" height="862" alt="Screenshot from 2025-08-30 20-07-32" src="https://github.com/user-attachments/assets/a09c973e-d006-4d5b-b8a9-88eba5d56cce" />

Step 4 is about publishing the release artifact. Once the files are gathered in the release directory, this directory is published as an artifact named release. This artifact is important because it will trigger the Terraform CD (Continuous Deployment) pipeline. If the pipeline fails, the release artifact is not created, and as a result, the deployment pipeline will not run. This ensures that only successful builds move forward to deployment.

<img width="1605" height="913" alt="Screenshot from 2025-08-30 20-11-51" src="https://github.com/user-attachments/assets/4d90fbfd-349e-46da-b327-3d594a8bc4fa" />

Step 5 is about publishing the report artifact. The report directory, which contains the logs generated during the pipeline run, is published as an artifact named report. Unlike the release artifact, the report artifact is created even if the pipeline fails, ensuring that the logs are always available for debugging, auditing, or analysis.

<img width="1605" height="913" alt="Screenshot from 2025-08-30 20-11-51" src="https://github.com/user-attachments/assets/f4f8972d-abf0-442e-96a7-389d5e6a8512" />
