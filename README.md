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

          
   ![git version](https://github.com/user-attachments/assets/3decc08c-2141-46ff-9ec7-5bd401cbee3d)

      
  ### 5. Set up GitHub  
   *  Head to GitHub's signup page.[GitHub Signup Page](https://github.com/join) to create account  
   *  Select New repository afterwards  
   *  Run the command below to creat a local repository on your local device  
       `Git init`  

      ![git init responds](https://github.com/user-attachments/assets/4a784bf1-3de4-4ad0-8232-0c1e10315dcd)  

 
### 6. Push local changes to GitHub
* Ran the command to connect the local project folder to the git repo  
    `git remote add origin https://github.com/eedontoh/nextwork-devopswebapp.`
  
![nextwork-java-web-app-repo](https://github.com/user-attachments/assets/97022b1b-b198-40c9-867b-1ef974e1c43c)  

  
* To stage changes
  `git add .`
* Run the command below to commit changes to the git repo. Using '-m' provides a message to describe the commit action  
   `git commit -m "Updated index.jsp with new content"` 
* Run the command below to save the local project online on github. Using '-u' means i am setting an 'upstream' for my local branch, which means i am telling Git to remember to push to 
  master by default.  
     `git push -u origin master`


### 6. Authetication and Local Identity
* Authenticate via tokens to connect to your online repo.  

  ![token setup](https://github.com/user-attachments/assets/82de6908-dbcb-4c52-a2ec-c737c3286df6)  
  

* Set up local Git identity by entering your name and email as Git needs to double check that you have the right to push any changes to the remote origin the local repo is connected with
*  Log History - shows the history of commits, which also mentions the commit author's name
  Run `git log` 
  
### 7. Making changes again
* To see Git working in action, update the index.jsp file  and run the following commands  
  `git add .`  
  `git commit -m "Add a new line to index.jsp"`    
  `git push`    

 ![second git push](https://github.com/user-attachments/assets/7ce3b7b7-5aee-467e-9f0f-0a2273fd7627)

 
 


