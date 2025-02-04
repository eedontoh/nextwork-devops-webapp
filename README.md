# Connect a GitHub Repo with AWS
Git is a version control system for tracking code changes by taking snapshots of how files look like at specific moments, and each snapshot is considered a 'version.


## Features
1. GitHub serves as a centralized repository for managing various versions of projects that are tracked using Git. 
2. GitHub is a cloud-based service, enabling remote access to projects as well as collaborate with other developers through the internet.


## Technologies Used
1. Amazon EC2
2. VSCode
3. GitHub
  

## Program Structure
├── web.xml & index.jsp # web application files

├── pom.xml # Maven Project Object Model file

└── README.md # Documentation for the project


## Setup & Installation
Follow these steps to set up and run the project:

### 1. Set up an IAM user
### 2. Set Up Your Web App in the Cloud
  * Launch an EC2 instance and save the private key-pair file in .pem format in DevOps folder on Desktop 
  
  * Install VSCode  
  
  * In the terminal, run the following command to change directory and allow access to your .pem file.  
     `cd ~/Desktop/DevOps`  
     `chmod 400 nextwork-keypair.pem`  
    
  * Use the following command to connect to your EC2 instance:   
     `ssh -i [PATH TO YOUR .PEM FILE] ec2-user@[YOUR PUBLIC IPV4 DNS]`  
  
  * Install Apache Maven to set up all the necessary web files to create  web app structure and its dependencies using the commands below:
      ```
     wget https://archive.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz

     sudo tar -xzf apache-maven-3.5.2-bin.tar.gz -C /opt

     echo "export PATH=/opt/apache-maven-3.5.2/bin:$PATH" >> ~/.bashrc

     source ~/.bashrc
  
  *  To verify that Maven is installed correctly, run:
     `mvn -v` 
 
  * Install Java 8, more specifically, Amazon Correto 8 to enable maven build the webapp.  
     ```
     sudo amazon-linux-extras enable corretto8

     sudo yum install java-1.8.0-amazon-corretto-devel

     export JAVA_HOME=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64

     export PATH=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64/jre/bin/:$PATH
  
  *  To verify that java 8 correctly installed, run:
     `java -version`
  *  Use mvn to generate a Java web app. To do this, use these commands
      ```
     mvn archetype:generate \
         -DgroupId=com.nextwork.app \
         -DartifactId=nextwork-web-project \
         -DarchetypeArtifactId=maven-archetype-webapp \
         -DinteractiveMode=false
   
   ### 3. Use Remote - SSH to connect VSCode with your EC2 instance.
   * Connect VSCode with your EC2 Instance.  
   * Select the Extensions icon at the side of your VSCode window.
   * Search for Remote - SSH and click Install for the extension.  
   * Click on the double arrow icon at the bottom left corner of your VSCode window.
   * Select Configure SSH Hosts..., and clear everything in your config file (which should look like /Users/username/.ssh/config).
   * Save your changes, and select Remote-SSH: Connect to Host... again.
   * Select + Add New SSH Host...
   * Enter the SSH command you used to connect to your EC2 instance: ssh -i [PATH TO YOUR .PEM FILE] ec2-user@[YOUR PUBLIC IPV4 DNS]
   * Select the configuration file at the top of your window. It should look similar to /Users/username/.ssh/config
   * Select the blue Open Config button on that popup.
   * Confirm that all the details in your configuration file are correct.
   * Click on the double arrow button on the bottom left corner and select Connect to Host again
   * Select the EC2 instance
   * From VSCode's left hand navigation bar, select the Explorer icon.
   * Select Open folder.
   * Enter /home/ec2-user/nextwork-web-project.
   * Press OK
   * If you see this popup, select Yes, I trust the authors  

  ### 4. Install Git 
   *  Run the following command in the terminal to install Git
      ```
        sudo dnf update -y  
        sudo dnf install git -y  
   *  Verifiy the installation:
        `git --version`  
   
      
  ### 5. Set up GitHub  
   *  Head to GitHub's signup page.[GitHub Signup Page](https://github.com/join) to create account  
   *  Select New repository afterwards  
   *  Select Create repository.

This loads up a new page where you can create a repository.

Under Owner, click on the Choose an owner dropdown and select your GitHub username.
Under Repository name, enter nextwork-devops-webapp
For the Description, enter Java web app set up on an EC2 instance.
Choose your visibility settings. We'd recommend selecting Public to make your repository available for the world to see.




  
  



Install Git
-Launch an EC2 instance.
-Set up VSCode on your local computer.
-Use Remote - SSH to connect VSCode with your EC2 instance

 	
Connect a GitHub Repo with AWS
 
Introducing Today's Project!
What is GitHub?
Github is an online site for hosting repos tracked by git. I used it to host the content of my local repos include my web application source code, files and folders.

One thing I didn't expect...
I didn't expect ssh on vscode to work but it worked perfectly. I had to ensure my security group inbound rules allowed ssh traffic on port 22 over my ip.

This project took me...
About an hour

Git and GitHub
Git is a version control system for tracking code changes by taking snapshots of how my files look like at specific moments, and each snapshot is considered a 'version. I installed Git using the commands sudo dnf update -y sudo dnf install git -y
GitHub as a storage space for different version of my project that Git tracks. I'm using GitHub because its is a cloud service that lets me access my work from anywehere and collaborate with other developers over the internet.

![image](https://github.com/user-attachments/assets/e63732cd-8a37-40af-a66d-1737ac4eb57a)
 
My local repository
A Git repository (aka 'repo') is a folders which contains all my project files and their entire version history
Git init is a command to create a local repository on my computer. I run git init inside a directory, to sets up the a local Git repository which means changes are now tracked for version control
After running git init, the response from the terminal was some yellow texts. Git suggests different branch names like 'main' or 'development' instead of 'master'. 
A branch in Git is a parallel version or 'alternate universe' of the same project
 
 **To push local changes to GitHub, I ran three commands**

################The first command I ran to connect my local project folder to my git repo was;############## 
git remote add origin https://github.com/eedontoh/nextwork-devopswebapp.

################ To stage changes ############################################
git add .

The second command I ran was; git commit -m "Updated index.jsp with new content" to commit changes to my git repo Using '-m' provides a message to describe the commit action
git push

The third command I ran was; git push -u origin master to save my local project online on github. Using '-u' means i am setting an 'upstream' for my local branch, which means i am telling Git to remember to push to master by default.
Authentication
When I commit changes to GitHub, Git asks for my credentials because Git needs to double check that i have the right to push any changes to the remote origin my local repo is connected with
Local Git identity
Git needs my name and email because Git needs author information for commits to track who made what change
Running git log showed me the my history of commits, which also mentions the commit author's name
 
GitHub tokens
GitHub authentication failed when I entered my password because GitHub phased out password authentication to connect with repositories over HTTPS there are too many security risks and passwords can get intercepted over the internet.
A GitHub token is a unique string of characters that looks like a random password. I'm using one in this project because they are great for security since they're unique and very hard to guess
I could set up a GitHub token by: Heading back into my browser with GitHub open. Select my profile icon and select Settings. Select Developer settings Select Personal access tokens. Select Tokens (classic). Select Generate new token
 
Making changes again
I wanted to see Git working in action, so I updated the index.jsp file but I couldn't see the changes in my GitHub repo initially because the changes on my local repo has not been pushed to git hub yet.
I finally saw the changes in my GitHub repo after i run the commands: git add .
git commit -m "Add a new line to index.jsp" git push
 
 
 


