
# Server Configuration Steps

## Setting up the Cloud Server: Azure, SSH and Linux Setup
The cloud provider chosen for this project is Microsoft Azure. Azure was selected because:
*	It's a reliable host for Linux virtual machines.
*	Supports SSH access for manual configuration.
*	Provides custom domain support.
*	Offers strong security and scalability.

### Step 1: Go to the Azure Website
*	Log in or sign up at: [https://azure.microsoft.com/en-au](https://azure.microsoft.com/en-au) 

### Step 2: Create a Virtual Machine (VM)
1.	Use the Azure portal to search for and select "Virtual Machine".
2.	Click Create, then fill in the required fields:
*	**Subscription**: Azure for Students (or your preferred plan).
*	**Resource Group**: NBAFanPageGroup (created for this project).
*	**VM Name**: nbafanpage-vm.
*	**Region**: Australia East.
*	**Image**: Ubuntu 22.04 LTS (search manually if not listed).
*	**Size**: Standard B2as v2 (2 vCPUs, 8 GiB memory).
*	**Authentication Type**: SSH Public Key.
  - Generate a new key pair.
  - Key Type: RSA
  - Format: SSH-RSA
  - Key Name: NBAFanPageVM_Key
*	**Public IP**: Create a new static IP, such as NBAfanPage.
*	**Inbound Ports**:
  - Allow SSH (22)
  - Allow HTTP (80)
	- Manually add HTTPS (443)
*	**NIC Network Security Group**: Basic
*	**Routing Preference**: Microsoft Network
*	**OS Disk Type**: Standard SSD
*	**Defender for Cloud**: Enable Basic Plan (free)
*	**Security Type**: Standard
*	**Username**: Choose any username or use the default azureuser.
 
### Step 3: Create and Deploy
*	Click Create to finalise the VM setup.
*	Start the VM after creation.
*	Download and safely store the private key (used for SSH access).

## DNS Configuration
During VM setup, a domain was configured to point to the public IP address.
### Steps:
1.	In the VM Networking tab, under NIC Network Interface, locate Public IP.
2.	Create a new DNS name label, nbafanpage.
This automatically maps the IP to:
*	[http://nbafanpage.australiaeast.cloudapp.azure.com](http://nbafanpage.australiaeast.cloudapp.azure.com)  
Azure handles internal DNS routing, no need for manual CNAME records.

## Web Server Setup: Apache Install/Config
### Step 1: SSH Into VM
```bash 
ssh -i NBAFanPageVM_key.pem azureuser@4.254.74.158
``` 
*	Ensure the .pem key is in your working directory.
*	Accept the fingerprint when prompted.

### Step 2: Install Apache
```bash 
sudo apt update
```
```bash 
sudo apt install apache2 -y
```
*	Verify Apache is running by visiting:
 - [http://4.254.74.158](http://4.254.74.158)  
 - [http://nbafanpage.australiaeast.cloudapp.azure.com](http://nbafanpage.australiaeast.cloudapp.azure.com) 

## Website Content Creation: NBA Fan Page
### Step 1: Edit the Apache Default Page
```bash
sudo nano /var/www/html/index.html 
``` 
*	Insert HTML for NBA content such as moments, players and images.
*	Save changes with: Ctrl + X, then Y, then Enter

### Step 2: View Your Changes
Visit your website to confirm it’s updated and live:
*	[http://4.254.74.158](http://4.254.74.158)  
*	[http://nbafanpage.australiaeast.cloudapp.azure.com](http://nbafanpage.australiaeast.cloudapp.azure.com) 



