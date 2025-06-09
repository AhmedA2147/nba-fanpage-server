
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

## SSL/TLS setup
Secure Sockets Layer (SSL) and Transport Layer Security (TLS) are protocols that:
- Encrypt data between the user and your web server.
- Protect against data interference, such as using passwords and forms.
- Show a padlock icon in the browser.
- Changes your site URL from “http://” to “https://”.

### Why it’s necessary: 
- It's required for user trust for modern browsers.
- Helps increase your site’s Google SEO ranking.
- Secure data transmission, especially important for login pages, forms and CMS such as WordPress.
- Gives your site a sense of professionalism that should always be expected.

### Guide to have SSL and TSL:
### Step 1: Confirmation
- Make sure your server is up and running. Follow the guide on **“Setting up the cloud server: Azure, SSH and Linux setup"**
- Make sure Apache is installed. Follow the guide on **“Web Server Setup: Apache install/config”**
- Make sure Port 80 and Port 443 are open in Azure. Follow the guide on **“Setting up the cloud server: Azure, SSH and Linux setup”**

### Step 2: If not, make sure the Virtual Machine on Azure is running.
- Log in or sign up with Microsoft Azure.
- This is the link: [https://azure.microsoft.com/en-au](https://azure.microsoft.com/en-au)
- Click Start VM.

### Step 3: Connect to you Azure VM through SSH.
- Open terminal 
- Now SSH into your VM:
- To SSH into your virtual machine, enter in the terminal:
```bash
ssh -i “Key pair name”key.pem Username@PublicIPAddress
```
So, for the NBA fan page project, this is how the terminal would look:
```bash
ssh -i NBAFanPageVM_key.pem azureuser@4.254.74.158
```
Make sure when you do this, the private key is in the right directory. 
- If this is your first time connecting, you will be asked to accept the fingerprint. Type “yes” to proceed.

### Step 4: Install Certbot & Apache plugin.
- Inside the terminal, type:
```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
```

### Step 5: Run Certbot to obtain and install the SSL certificate.
-	Inside the terminal type:
```bash
sudo certbot --apache
```
- Follow the questions the command asks you, such as entering your email, domain name and accepting terms and services.
- Now Certbot will directly configure Apache, download and install Apache then reload it.

### Step 6: Check if HTTPS is working.
- Go to your browser now and type your domain name, but this time lead it with https://:
Example: [https://nbafanpage.australiaeast.cloudapp.azure.com](https://nbafanpage.australiaeast.cloudapp.azure.com)
- Now your website should come up, but this time https:// is in the address bar and there's a padlock in the browser.
- To check if the certificate is installed, click on the padlock logo on the search browser of your now secured site, and it should tell you where it's issued by and how long till expires or if the certificate is still valid.

## Website content: NBA Fan Page
The NBA Fan Page website was built entirely using custom HTML and CSS, and deployed through the Apache web server on a Linux virtual machine hosted on Microsoft Azure. This site was made to attract NBA fans by showing them relevant and engaging basketball content in a structured and visually appealing layout.

### Key Features
The website was organised into adequate sections, demonstrating an understanding of layout and front-end structure. These include:

**Recent NBA Moments**: Displays iconic images from recent games, each with captions and their sources.

**Famous NBA Players**: Presents headshots of top players with their names labeled on each image for easy recognition.

**Latest News & Interviews**: Highlights key headlines using bullet points to summarise recent interviews and news.

**Rankings & Predictions**: Features updated playoff rankings and some predicted outcomes.

**NBA Highlights**: Implemented YouTube videos using <iframe> elements to bring dynamic multimedia to the page.

### Design Considerations 
All multimedia components are accompanied by proper captions using proper HTML tags like "figure" and "figcaption", ensuring content is accessible and well-structured. A footer includes a Creative Commons license to clarify content usage rights.

### Skills Demonstrated
This section of the project reflects on the understanding gained from front-end web development. They including:
- Proper HTML structuring.
- CSS styling for layout and look.
- Media implemented such as images and YouTube videos.
- User-focused visual design.
It also shows the ability to work with raw code and not relying on website builders. being able to manually deploy content in a cloud-hosted Linux environment helping meet key requirements for Infrastructure as a Service (IaaS).

## Conclusion and Learning Outcomes
Creating the NBA Fan Page website provides a hands-on experience with deploying a fully functional website using Infrastructure as a Service (IaaS) through Microsoft Azure. The project required configuring a Linux virtual machine then connecting through SSH and then manually installing and managing the Apache web server. The site was made entirely from scratch using custom HTML and CSS, with emphasis on structured layout, multimedia implementation and clean visual presentation.

### Key Learning Outcomes
- Gaining experience in the end-to-end deployment of a cloud-hosted web server.
- Developed practical understanding with Linux terminal tools like apt, nano, and sudo.
- Learned to configure networking, DNS labels, and static public IP mapping using Azure.
- Practiced web development fundamentals using HTML and CSS, including correct tags and proper design principles.
- Updating content through SSH-based editing.

### Challenges Faced
**SSH Key Errors**: Encountering errors when trying to log in due to missing or misdirected private key location (.pem). Just need to make sure when you SSH into your VM, the private key is in the right directory, and it exists. 

**Apache Configuration Problems**: Apache initially showed a blank page due to editing the wrong file. The correct file (/var/www/html/index.html) was later identified and updated.

**HTML Layout Issues**:  Initially, content lacked alignment and consistency, which is easily resolvable through CSS styling and structured tag use, such as <figure> and <figcaption>.

### Potential Improvements
To extend the project in the future:
- Integrate dynamic content using some server-side. That way, even live game updates can be implemented.
- Convert the fan page into a fully usable website using a Content Management System (CMS) like WordPress for easier content updates.
- Implement user interaction features, such as comment sections and fan polls.
- Add SSL/TLS security to enable HTTPS for encrypted connections and better trust.

## References 
- [Microsoft. (n.d.). Microsoft Learn. Retrieved June 5, 2025,](https://learn.microsoft.com)
- [Canonical Ltd. (n.d.). Ubuntu. Retrieved June 5, 2025,](https://ubuntu.com)
- [National Basketball Association. (n.d.). NBA.com. Retrieved June 5, 2025,](https://www.nba.com) 

**[Images used on Website:](http://nbafanpage.australiaeast.cloudapp.azure.com/)**
- [Imagn. (2025). Shai Gilgeous-Alexander playoff photo (Photograph). Sports Illustrated via Minute Media](https://images2.minutemediacdn.com/image/upload/c_crop,w_3212,h_1806,x_181,y_331/c_fill,w_2160,ar_16:9,f_auto,q_auto,g_auto/images%2FImagnImages%2Fmmsport%2Fsi%2F01jw7xfe23dtr0nr84v4.jpg)  
- [News Corp Australia. (2025). NBA game image [Photograph](https://content.api.news/v3/images/bin/63744d75080ea1b4f197a1404fd3631a?width=768)
- [Motorcycle Sports. (2025, May). NBA-themed image [Photograph](https://motorcyclesports.net/wp-content/smush-webp/2025/05/image-19596-1140x570.jpg.webp) 
- [National Basketball Association. (2025). Anthony Edwards headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/1630162.png)
- [National Basketball Association. (2025). Jalen Brunson headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/1628973.png) 
- [National Basketball Association. (2025). Kevin Durant headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/201142.png)
- [National Basketball Association. (2025). Giannis Antetokounmpo headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/203507.png) 
- [National Basketball Association. (2025). Nikola Jokić headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/203999.png) 
- [National Basketball Association. (2025). Shai Gilgeous-Alexander headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/1628983.png) 
- [National Basketball Association. (2025). LeBron James headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/2544.png) 
- [National Basketball Association. (2025). Stephen Curry headshot [Photograph](https://cdn.nba.com/headshots/nba/latest/1040x760/201939.png) 
  
**[Videos used on Website:](http://nbafanpage.australiaeast.cloudapp.azure.com/)**
- [Golden Hoops. (2024, May 6). Stephen Curry’s clutch performance (Video). YouTube.](https://www.youtube.com/watch?v=0DGrPNUyPfg) 
- [Golden Hoops. (2024, May 4). NBA Playoffs Moments - Clutch Highlights (Video). YouTube.](https://www.youtube.com/watch?v=elxT_VoPqSo)




