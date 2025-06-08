# NBA Fan Page Server

This project involved the creation and deployment of a cloud-hosted NBA fan page website that shows iconic NBA moments, NBA teams and their players and related multimedia content. By doing this, I will show my proficiency and ability to demonstrate my understanding of infrastructure as a service (IaaS) by manually configuring and managing a Linux-based web server using command-line tools and showcasing web development. 
The server hosts a basic HTML/CSS website made to appeal to NBA fans. To host the website, I used Microsoft Azure as the cloud provider and created a Linux-based virtual machine (VM) using Ubuntu Server. The VM was configured manually through SSH (Secure Shell) access from my local machine. After utilising the VM, I installed and configured the Apache web server to serve the web content from the directory.
A custom DNS entry was also set up using Azure’s DNS service to point to the public IP address of my server. 

# WebSite
- Domain: [http://nbafanpage.australiaeast.cloudapp.azure.com/](http://nbafanpage.australiaeast.cloudapp.azure.com/)
- Public IP: [http://4.254.74.158](http://4.254.74.158)

# Project Goals
- Demonstrate understanding of Infrastructure as a Service (IaaS).
- Manually configure a cloud-based Linux server using SSH.
- Install and configure Apache to serve a basic HTML/CSS website.
- Set up a custom DNS entry to map domain to server IP.
- Install and configure WordPress manually on the same server.
- Implement SSL/TLS using Certbot to enable HTTPS for secure connections.
- Implement a script onto the server providing a service.

# Technologies Used
- Cloud Provider: Microsoft Azure
- Operating System: Ubuntu Server (Linux)
- Web Server: Apache2
- Access Protocol: SSH
- CMS: WordPress
- Development: HTML/CSS
- SSL/TLS: Let's Encrypt with Certbot

# Setup Overview
- Created a Linux-based Virtual Machine on Microsoft Azure.
- Connected through SSH from local machine.
- Installed and configured Apache web server to host both static HTML and WordPress.
- Uploaded HTML/CSS files to /var/www/html/ for the custom NBA fan page.
- Created a DNS entry using Azure DNS to point a domain to the public IP.
- Installed and configured WordPress manually in /var/www/html/wordpress/ with MySQL. For a full breakdown, check out [WordPress Installation](docs/wordpress-config.md).
- Installed a free SSL certificate using Certbot to enable secure HTTPS access.
- Verified accessibility through both public IP and domain (HTTP and HTTPS).
- Created a bash script that outputs a welcome message for NBA fans and displays the current date. For a full breakdown, check out [Bash Script Guide](scripts/helloNBA-script.md). 
- For a full breakdown of all the other set-ups, check out [Server Configuration](docs/server-config.md).

# Repository Structure 
- README.md                # Overview of the project
    - docs/
        - server-config.md       # Detailed documentation of server configuration in md.
        - wordPress-config.md    # Detailed documentation of wordPress installation and configuration in md.
    - scripts/
        - helloNBA-script.md     # Detailed documention of script used in server.
                   

# Video Explainer
-  A walkthrough video of the server setup and site creation (need to add link) 




