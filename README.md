# NBA Fan Page Server

This project involved the creation and deployment of a cloud-hosted NBA fan page website that shows iconic NBA moments, NBA teams and their players and related multimedia content.

# WebSite
- Domain: [http://nbafanpage.australiaeast.cloudapp.azure.com/](http://nbafanpage.australiaeast.cloudapp.azure.com/)
- Public IP: [http://4.254.74.158](http://4.254.74.158)

# Project Goals
- Demonstrate understanding of Infrastructure as a Service (IaaS).
- Manually configure a cloud-based Linux server using SSH.
- Install and configure Apache to serve a basic HTML/CSS website.
- Set up a custom DNS entry to map domain to server IP.
- Practice using GitHub for version control and documentation.
  
# Technologies Used
- Cloud Provider: Microsoft Azure
- Operating System: Ubuntu Server (Linux)
- Web Server: Apache2
- Access Protocol: SSH
- Development: HTML/CSS
- Version Control and Docs: GitHub

# Setup Overview
- Created a Linux-based Virtual Machine on Microsoft Azure.
- Connected via SSH from local machine.
- Installed and configured Apache web server to host the website.
- Uploaded HTML/CSS files to /var/www/html/.
- Created a DNS entry pointing to the public IP using Azure DNS.
- Verified accessibility using both domain and IP address.
- For a full breakdown, check-out [docs/server-setup.md](docs/server-setup.md) 

# Repository Structure (still need to add other docs, scripts)
- README.md                # Overview of the project
    - docs/                    # Detailed documentation in md
    - scripts/                 # scripts used in the server
    - website/                 # HTML/CSS content hosted on the server
      - index.html
      - assets                  # Screenshots or video assets (if any)

# Video Explainer
-  A walkthrough video of the server setup and site creation (need to add link) 




