## WordPress installation 
To complement the custom-built NBA Fan Page, WordPress was manually installed on the same Azure-hosted Ubuntu server to show a level of capability with content management systems (CMS) and enhance server functionality. This installation was completed through secure shell (SSH) access, without the use of pre-configured Azure images.

### Installation guide:
#### Step 1: Make sure the Virtual Machine on Azure is running.
-	Log in or sign up with Microsoft Azure.
-	This is the link: https://azure.microsoft.com/en-au
-	Click start VM.

#### Step 2: Connect to you Azure VM through SSH
-	Open terminal 
-	Now SSH into your VM:
- To SSH into your virtual machine, enter in the terminal:
```bash
ssh -i “Key pair name”key.pem Username@PublicIPAddress
```
- So for the NBA fan page project, this is how the terminal would look:
```bash
ssh -i NBAFanPageVM_key.pem azureuser@4.254.74.158
```
- Make sure when you do this, the private key is in the right directory. 
-	If this is your first time connecting, you will be asked to accept the fingerprint. Type “yes” to proceed.

#### Step 3: Update Package Index and Install Dependencies
-	Now, enter in your terminal:
```bash
sudo apt update
sudo apt install apache2 mysql-server php php-mysql libapache2-mod-php php-cli php-cgi php-gd unzip curl -y
```

#### Step 4: Download and Extract WordPress
-	After installing dependencies, enter in your terminal:
```bash
cd /tmp
curl -O https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz
```

#### Step 5: Move WordPress Files to Web Directory
-	Once you’ve entered the temporary directory and extracted WordPress, enter in your terminal:
```bash
sudo cp -R wordpress /var/www/html/
sudo chown -R www-data:www-data /var/www/html/wordpress
sudo chmod -R 755 /var/www/html/wordpress
```
-	Now your web files have been moved to the web directory.

#### Step 6: Create a MySQL Database for WordPress
-	Now, enter in your terminal:
```bash
sudo mysql -u root
```
-	Next, inside MySQL, type whatever to show it exists:

#### Step 7: Restart Apache
-	Now, restart Apache by entering:
```bash
sudo systemctl restart apache2
Step 8: Accessing WordPress
```
-	Once completed, WordPress can now be accessed through either:
[http://<your-public-ip>/wordpress](http://<your-public-ip>/wordpress)
example: [http://4.254.74.158/wordpress](http://4.254.74.158/wordpress)
- Or through domain
[http://nbafanpage.australiaeast.cloudapp.azure.com/wordpress](http://nbafanpage.australiaeast.cloudapp.azure.com/wordpress)

### Purpose and Value
Installing WordPress from scratch shows:
-	Manual server configuration and CMS deployment.
-	Experience beyond static HTML/CSS websites.
-	Ability to host dynamic, content-driven platforms.
-	Preparation for real-world hosting and web management scenarios.
This complements the HTML-based NBA fan page by enabling potential future features like blog posts, fan comments, news updates, or CMS-managed photo galleries.

