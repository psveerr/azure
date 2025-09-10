Path-Based Routing with Azure Application Gateway and Custom Domain
Overview

This project demonstrates how to deploy two backend applications on Azure Virtual Machines, configure path-based routing using Azure Application Gateway, and host the applications on a custom domain purchased via Namecheap.

Infrastructure Setup
Virtual Machine Instances

Two Linux virtual machines were created in Azure. Each VM was configured with a web server and served different content:

VM1 was set up to serve application content for the /path1 route.

VM2 was set up to serve application content for the /path2 route.
<img width="1538" height="958" alt="Screenshot from 2025-09-10 17-52-51" src="https://github.com/user-attachments/assets/0ba8ecec-109a-404d-98e3-74e942cf5895" />
<img width="1810" height="1006" alt="Screenshot from 2025-09-10 17-55-34" src="https://github.com/user-attachments/assets/73769b57-5915-40c9-9432-fad08105e32b" />
<img width="1412" height="426" alt="Screenshot from 2025-09-10 18-08-54" src="https://github.com/user-attachments/assets/a859de74-5b52-448a-ad62-1b00119d4031" />
<img width="1371" height="452" alt="Screenshot from 2025-09-10 18-10-10" src="https://github.com/user-attachments/assets/e0671248-39de-411d-ad09-ebf99fd2baea" />

Application Gateway

An Azure Application Gateway was created with the following configuration:

A frontend IP was assigned using a public IP address.

Two backend pools were created, one pointing to VM1 and the other to VM2.

HTTP settings were configured for port 80 communication.

A listener was created to receive incoming HTTP traffic.
<img width="1798" height="965" alt="Screenshot from 2025-09-10 18-20-10" src="https://github.com/user-attachments/assets/f53a8a59-498c-4b11-b12a-10f833d49432" />
<img width="1815" height="1004" alt="Screenshot from 2025-09-10 18-35-21" src="https://github.com/user-attachments/assets/be02e417-a601-432c-b9a0-0e3770002fbe" />


Path-Based Routing Rules

A request routing rule was configured to direct traffic based on the requested path:

Requests to /path1/* were routed to the backend pool associated with VM1.

Requests to /path2/* were routed to the backend pool associated with VM2.
<img width="1798" height="965" alt="Screenshot from 2025-09-10 18-29-48" src="https://github.com/user-attachments/assets/20efc7c6-14b6-4f11-805e-a3e97a09c65d" />


After deployment, the setup was tested by accessing the Application Gateway’s public IP. The routing worked correctly, directing users to the respective backend servers depending on the path entered.

Custom Domain Integration
Domain Setup

A domain was purchased from Namecheap. The name servers of the domain were updated to point to Azure DNS.
<img width="1815" height="1004" alt="Screenshot from 2025-09-10 18-34-52" src="https://github.com/user-attachments/assets/076fd819-83ae-4ac8-872e-2e3fd3bb768f" />


Azure DNS Zone

A DNS zone was created in Azure corresponding to the custom domain. Within the DNS zone, records were configured as follows:

An A record was created to map the root domain to the Application Gateway’s public IP.
<img width="1815" height="1004" alt="Screenshot from 2025-09-10 18-37-28" src="https://github.com/user-attachments/assets/9ce5784b-ed51-4f67-9e1f-bc1472977ca8" />


Application Gateway Listener

The listener on the Application Gateway was updated to accept requests for the custom domain. This ensured that traffic sent to the domain name would be processed and routed correctly.
<img width="1815" height="1004" alt="Screenshot from 2025-09-10 18-42-30" src="https://github.com/user-attachments/assets/11fd1e08-7408-400e-aeac-59a8026f3c17" />


Validation

The backend health status in the Application Gateway was verified to ensure both VMs were healthy.

DNS propagation was checked to confirm that the domain resolved to the Application Gateway’s public IP.

The applications were successfully accessible using the custom domain with the correct path-based routing.
