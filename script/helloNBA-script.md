## Script: Code and Explanation 

**Name of script:** helloNBA.sh
This bash script, called helloNBA.sh, is a custom message that is placed on the server, and when executed, it outputs a welcome message for NBA fans and displays the current date using “echo” and the “date” command. It's one of the few ways to demonstrate scripting skills and terminal output on a live server. 

**Skills gained:**
•	Writing and executing a Bash script.
•	Using basic system commands.
•	Deploying and running scripts on a cloud server through SSH.

### Guide to create and run script:
**Step 1: Make sure the Virtual Machine on Azure is running.**
-	Log in or sign up with Microsoft Azure.
-	This is the link: https://azure.microsoft.com/en-au
-	Click start VM.

**Step 2: Connect to you Azure VM through SSH**
- Open terminal 
-	Now SSH into your VM:
- To SSH into your virtual machine, enter in the terminal: ssh -i “Key pair name”key.pem Username@PublicIPAddress
- So for the NBA fan page project, this is how the terminal would look:
```bash
ssh -i NBAFanPageVM_key.pem azureuser@4.254.74.158
```
- Make sure when you do this, the private key is in the right directory. If this is your first time connecting, you will be asked to accept the fingerprint. Type “yes” to proceed.

**Step 3: Create the script file**
-	Create a file using: Nano “nameofyourfile”.sh
- Example:
```bash
nano helloNBA.sh
```
-	Now you should be in the terminal text editor.

**Step 4: Implement the script**
-	Inside the nano text editor, type:
- example: 
```bash
#!/bin/bash
echo "Hello NBA fans!"
echo "Today's date is: $(date)"
```
-	This is the bash script that will output the message you want and show the current date and time.
-	After typing up the script, save and exit in nano by entering:
Ctrl + O: This saves the script 
Ctrl + X: Exits the text editor nano

**Step 5: Make the script computable**
-	After saving and exiting Nano, enter in the terminal:
```bash
chmod +x hello_nba.sh
```
-	This will make the script executable now.

**Step 6: Compute the script**
-	To execute the script enter: ./ “name of file” 
- Example:
```bash 
./helloNBA.sh
```
-	Now the script is executed and should show the message you entered, date and time.
-Example output:
Hello, NBA fans!
Today's date is Wed May 21 17:45:21 AWST 2025

**Screenshots of process**
- ![image](https://github.com/user-attachments/assets/b5244b7b-8cc6-45ac-b8c5-283490e00d1b)
- ![image](https://github.com/user-attachments/assets/de369f68-f77f-4425-b146-974bb99298da)






