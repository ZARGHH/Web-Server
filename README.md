# Web-Server
Deploying a Web SStep 1: Prerequisites

Before you begin, you need the following:

An Azure account
Azure CLI installed on your local machine
Step 2: Create a Virtual Machine

Open your terminal or command prompt.

Use the Azure CLI to create a new virtual machine:

bash
Copy code
az vm create \
  --resource-group myResourceGroup \
  --name myVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
Replace myResourceGroup with the name of your Azure resource group.
Replace myVM with your desired VM name.
We're using the "UbuntuLTS" image, which is a popular choice for running web servers on Linux. You can choose a different image if needed.
Once the VM is created, note down its public IP address.
Step 3: Connect to the Virtual Machine

Use SSH to connect to your VM:
bash
Copy code
ssh azureuser@your-vm-public-ip
You're now connected to your VM.
Step 4: Install Nginx

Update the package list:
bash
Copy code
sudo apt update
Install Nginx:
bash
Copy code
sudo apt install nginx
Start Nginx:
bash
Copy code
sudo systemctl start nginx
Enable Nginx to start on boot:
bash
Copy code
sudo systemctl enable nginx
Step 5: Test Your Web Server

Open a web browser and enter your VM's public IP address or hostname. You should see the default Nginx welcome page.
Step 6: Deploy Your Website

Copy your website files to the VM. You can use scp or tools like rsync to transfer your website files to the VM.

Configure Nginx to serve your website. Typically, you'd create a new Nginx server block in /etc/nginx/sites-available/ and link it to /etc/nginx/sites-enabled/. Don't forget to test the Nginx configuration and reload Nginx:

bash
Copy code
sudo nginx -t
sudo systemctl reload nginx
Your website should now be accessible using your VM's public IP or domain.
This example deploys a basic web server on an Azure VM. Depending on your specific requirements, you might need to perform additional configurations like setting up domain names, SSL certificates, and securing your server. Additionally, consider automating the deployment process using configuration management tools like Ansible or using Azure DevOps pipelines for continuous deployment.erver
