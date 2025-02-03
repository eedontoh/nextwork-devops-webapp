# Connect a GitHub Repo with AWS
Git is a version control system for tracking code changes by taking snapshots of how files look like at specific moments, and each snapshot is considered a 'version.


## Features
1. GitHub serves as a centralized repository for managing various versions of projects that are tracked using Git. 
2. GitHub is a cloud-based service, enabling remote access to projects as well as collaborate with other developers through the internet.


## Technologies Used
1. Amazon EC2
2. VSCode
3. GitHub
  
Git using the commands sudo dnf update -y sudo dnf install git -y



We will:
 🐱 Set up Git and GitHub.
 🤝 Connect web app project to a GitHub repo.
 🤝 Make changes to the web app files and watch GitHub repo update too.

KEY TOOLS:
  
  
STEP #1
Set up your aws account and login in with your IAM user

STEP #2
Set Up Your Web App in the Cloud
-Launch an EC2 instance 
-Install VSCode

STEP #3
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
 
 
 


