Azure Application Gateway with Certbot and Path-Based Routing
This documentation outlines the process of configuring a GitHub-hosted application with path-based routing and HTTPS, leveraging an Azure Application Gateway for TLS/SSL termination. The process uses Certbot to generate certificates, which are then integrated into the Azure environment.

1. Prerequisites
Before you begin, ensure you have the following:

An active Azure subscription.

An Azure Application Gateway instance already deployed.

Multiple backend web servers (e.g., NGINX on VMs) hosted behind the Application Gateway.

A custom domain name (e.g., yourdomain.com) with a DNS record pointing to the Application Gateway's public IP address.

SSH access to at least one of your backend NGINX servers for the Certbot process.

2. Generate and Configure SSL Certificates with Certbot
The key is to use Certbot to generate a certificate for your domain on a VM, and then export it for use with the Azure Application Gateway.

Step 2.1: SSH into a Backend Server
Connect to one of your NGINX backend servers. This is where you will run the Certbot command.

ssh azureuser@your-nginx-vm-ip-address

<img width="1451" height="582" alt="Screenshot 2025-09-11 212727" src="https://github.com/user-attachments/assets/72011ea7-9a01-4bcf-addb-5a0ceaee4b86" />


Step 2.2: Stop NGINX Temporarily
Certbot's standalone authenticator needs to bind to port 80 to prove domain ownership. Stop your NGINX service to free up the port.

sudo systemctl stop nginx

<img width="1117" height="846" alt="Screenshot 2025-09-11 212746" src="https://github.com/user-attachments/assets/0ca27701-4094-4321-854d-caef30980eac" />


Step 2.3: Run Certbot to Get the Certificate
Execute the Certbot command using the standalone authenticator. Replace yourdomain.com with your actual custom domain.

sudo certbot certonly --standalone -d yourdomain.com

Follow the on-screen prompts to enter your email address and agree to the terms of service. Certbot will perform an HTTP-01 challenge, using the Application Gateway's public IP and your DNS entry to validate your domain. Upon success, the certificate files will be stored in /etc/letsencrypt/live/yourdomain.com/.

Step 2.4: Export the Certificate as a PFX File
Azure Application Gateway requires certificates in the Personal Information Exchange (.pfx) format, which bundles the private key and public certificate.

sudo openssl pkcs12 -export -out yourdomain.com.pfx -inkey /etc/letsencrypt/live/[yourdomain.com/privkey.pem](https://yourdomain.com/privkey.pem) -in /etc/letsencrypt/live/[yourdomain.com/fullchain.pem](https://yourdomain.com/fullchain.pem) -passout pass:yourpassword

Replace yourpassword with a secure password for the PFX file. This command will create yourdomain.com.pfx.

<img width="1058" height="306" alt="Screenshot 2025-09-11 212809" src="https://github.com/user-attachments/assets/5f755b97-2fb9-4826-ba0f-db3d410552d1" />


3. Upload the Certificate to Azure Key Vault
For a secure and manageable solution, store your PFX certificate in Azure Key Vault.

Step 3.1: Create an Azure Key Vault (If You Don't Have One)
In the Azure Portal, create a new Key Vault. Ensure it's in the same resource group and region as your Application Gateway for easy management.

<img width="1280" height="611" alt="Screenshot 2025-09-11 212907" src="https://github.com/user-attachments/assets/1c3c2aee-540c-4e1b-acd5-4f05ba6d797a" />


Step 3.2: Upload the Certificate
Navigate to your Key Vault instance in the Azure Portal.

In the left-hand menu, select Certificates and then Generate/Import.

Choose Import as the method.

Give the certificate a name (e.g., certbot-ssl-certificate).

Upload the yourdomain.com.pfx file and enter the password you set in the previous step.

4. Configure Application Gateway for TLS Termination and Path-Based Routing
This is the final step, where you configure the Application Gateway to use the certificate and route traffic.

Step 4.1: Create a Listener with the New Certificate
In the Azure Portal, navigate to your Application Gateway.

<img width="1919" height="937" alt="Screenshot 2025-09-11 213106" src="https://github.com/user-attachments/assets/138ae92b-60b7-4bbc-8dee-17cf2091467b" />


Go to the Listeners section and select + Add listener.

Fill in the details:

Listener name: https-listener

Frontend IP: Choose Public

Protocol: HTTPS

Port: 443

Choose a certificate: Select From Key Vault.

Link the Key Vault to your Application Gateway. Once linked, select the certificate you uploaded (certbot-ssl-certificate).

Step 4.2: Create a URL Path Map
A URL path map allows you to define routing rules based on the URL path.

In your Application Gateway, go to Rules and select + Add a routing rule.

Rule name: path-based-rule

Listener: Select the https-listener you just created.

Under the Backend targets tab, select Path based routing.

Add a path rule for each of your backend applications. For example:

Path: /app1/*

Target name: app1-backend

Backend settings: http-backend-setting (or create a new one)

Backend pool: Select the backend pool for app1.

Repeat for other applications (/app2/*, etc.), and set a Default backend target for unmatched paths.

Step 4.3: Automate Certificate Renewal
Certbot certificates are valid for 90 days. You must automate the renewal process. A common approach is to use an Azure Automation account with a PowerShell runbook or a simple cron job on your VM that runs Certbot with the --renew-hook flag to automatically export and upload the renewed certificate to Key Vault.
